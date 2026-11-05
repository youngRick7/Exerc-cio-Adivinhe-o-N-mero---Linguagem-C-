#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    srand(time(NULL));

    char continuar;

    do {
        int nivel, maximo, limite;
        int num, palpite;
        int tentativas = 0;
        int acertou = 0;

        // 1. Nível de dificuldade
        printf("\n=== ADVINHA NUMERO ===\n");
        printf("Escolha o nivel:\n");
        printf("1 - Facil (1 a 5)\n");
        printf("2 - Medio (1 a 20)\n");
        printf("3 - Dificil (1 a 100)\n");
        printf("Opcao: ");
        scanf("%d", &nivel);

        switch (nivel) {
            case 1: maximo = 5;   limite = 3; break;
            case 2: maximo = 20;  limite = 5; break;
            case 3: maximo = 100; limite = 7; break;
            default:
                printf("Opcao invalida! Usando nivel facil.\n");
                maximo = 5;
                limite = 3;
        }

        num = (rand() % maximo) + 1;

        printf("\nAdivinhe o numero de 1 a %d (voce tem %d tentativas)\n", maximo, limite);

        // 2 e 3. Contagem e limite de tentativas
        while (tentativas < limite && !acertou) {
            printf("Tentativa %d/%d: ", tentativas + 1, limite);
            scanf("%d", &palpite);
            tentativas++;

            if (palpite > num) {
                printf("Seu palpite e maior que o numero sorteado.\n");
            } else if (palpite < num) {
                printf("Seu palpite e menor que o numero sorteado.\n");
            } else {
                acertou = 1;
            }
        }

        if (acertou) {
            printf("\nParabens! Voce acertou em %d tentativa(s)!\n", tentativas);
        } else {
            printf("\nFim das tentativas! O numero sorteado era: %d\n", num);
        }

        // 4. Menu para continuar jogando
        printf("\nDeseja jogar novamente? (s/n): ");
        scanf(" %c", &continuar);

    } while (continuar == 's' || continuar == 'S');

    printf("Obrigado por jogar!\n");
    return 0;
}
