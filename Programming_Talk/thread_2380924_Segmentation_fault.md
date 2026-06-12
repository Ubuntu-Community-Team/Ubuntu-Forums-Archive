---
title: "Segmentation fault"
date: 2017-12-23
forum: Programming Talk
---

### Post by kelve17 on 2017-12-23
Hi guys, 

Im new here , and sorry if im doing anything wrong :).
I'm creating a game based on server-client project on linux with c programing.
On the server side i have 1 thread to control the AI but at some point of the code when i try to access members of my global variable that represents a struct , i get segmentation fault error.
I used GDB to see where but it doesnt give me any error , just when i run the program i get the error. Can u give me some suggestions to avoid the error ? 
PS:When i run the program on MAC OS , its perfect no errors.
The global variable resp is initialized on the main aswell as the threads creation.

```

#include "header.h"
RESPONSE resp;
void *moveInimigo(void *arg) { //nota : tornar os inimigos mais inteligentes depois


    srand((unsigned) time(NULL));
    int continua, n, a, b;
    char namepipe[MAX];
    int x, y, xOrig, yOrig;
    ENEMY *inimigo = (ENEMY*) arg;


    x = xOrig = inimigo->posX;
    y = yOrig = inimigo->posY;
    while (!ENDTHREAD) {
        pthread_mutex_lock(&mutex);
        printf("NEW\n");
        fflush(stdout);
        sleep(5);




        //verifica vizinhanca ... neighbors 32 
        continua = 1;
        for (int i = x - 2; i < x + 2 && continua; i++) {
            printf("cheguei i\n");
            sleep(2);
            if (i < 0)
                a = 0;
            if (i >= resp.width)
                a = resp.width - 1;
            for (int j = y - 2; j < y + 2 && continua; j++) {
                printf("cheguei j\n");
                fflush(stdout);
                usleep(400);
                if (j < 0)
                    b = 0;
                if (j >= resp.height)
                    b = resp.height - 1;
                if (resp.maze[a][b].type == player) {


                    if (a < x) {
                        x--;
                    } else if (a > x) {
                        x++;
                    }
                    if (b < y) {
                        y--;
                    } else if (b > y) {
                        y++;
                    }


                    if (resp.maze[x][y].type == emptyBlock)
                        continua = 0;
                    else {
                        x = xOrig;
                        y = yOrig;
                    }
                }
            }
        }




        printf("Terminou ciclo\n");
        if (continua) {
            printf("Entrou no random\n");
            fflush(stdout);
            usleep(400);
            while (continua) {
                n = rand() % 3;


                switch (n) {
                    case 0://up
                        printf("CIMA\n");
                        fflush(stdout);
                        if (x - 1 >= 0 && resp.maze[x - 1][y].type == emptyBlock) {
                            printf("ERRO AQUI\n");
                            fflush(stdout);
                            x--;
                            continua = 0;
                        }
                        break;
                    case 1://down
                        printf("BAIXO\n");
                        fflush(stdout);
                        if (x + 1 < resp.width && resp.maze[x + 1][y].type == emptyBlock) {
                            printf("ERRO AQUI\n");
                            fflush(stdout);


                            x++;
                            continua = 0;
                        }
                        break;
                    case 2://left
                        printf("ESQUERDA\n");
                        fflush(stdout);
                        if (y - 1 >= 0 && resp.maze[x][y - 1].type == emptyBlock) {
                            printf("ERRO AQUI\n");
                            fflush(stdout);
                            y--;
                            continua = 0;
                        }
                        break;
                    case 3://right
                        printf("DIREITA\n");
                        fflush(stdout);
                        if (y + 1 < resp.height && resp.maze[x][y + 1].type == emptyBlock) {
                            printf("ERRO AQUI\n");
                            fflush(stdout);
                            y++;
                            continua = 0;
                        }
                        break;
                }
            }
            printf("SAIU DO RANDOM\n");
            fflush(stdout);


            //atualizar mapa e enviar aos clientes logados
            continua = 1;
            for (int i = 0; i < resp.width && continua; i++)
                for (int j = 0; j < resp.height && continua; j++)
                    if (resp.maze[i][j].idEnemy == inimigo->id) {
                        resp.maze[x][y].idEnemy = resp.maze[i][j].idEnemy;
                        printf("AQUI\n");
                        fflush(stdout);
                        resp.maze[x][y].type = enemy;
                        resp.maze[i][j].type = emptyBlock;
                        resp.maze[i][j].idEnemy = 0;
                        continua = 0;
                    }
            //mostrar aos clientes


            printf("SAIU\n");
            fflush(stdout);
            for (int i = 0; i < Players; i++) {
                if (clientes[i].pid != -1) {
                    sprintf(namepipe, CLIENT_FIFO, clientes[i].pid);
                    fd_res = open(namepipe, O_WRONLY);
                    res = write(fd_res, &resp, sizeof (resp));
                    close(fd_res);
                }
            }


        } //random movement


        printf("Im done , i leave to another\n");
        fflush(stdout);
        pthread_mutex_unlock(&mutex);
    }
    return NULL;
}

```

header.h : 
```

typedef enum {
    player = 0, emptyBlock = 1, destrutiveBlock = 2, indestrutiveBlock = 3, firebal = 4, skeleton = 5, spider = 6, enemy = 7, object = 8
} Element;


typedef enum {
    empty = 0, bombinha = 1, megabomba = 2, life = 3, money = 4, colector = 5, points = 6, fire = 7, shield = 8, shoe = 9
} Drop;


//Estrutura dos Objectos no Mapa


typedef struct {
    Element type;
    Drop drop;
    char idLetraJogador;
    int idEnemy;


} MAP;


//Estrutura Info. Acerca dos Jogadores


typedef struct {
    int pid;
    char user[MAX];
    int life;
    int points;
    int bombinha;
    int megaBomba;
    char letraID; //letra do jogador no jogo


} CLIENT;


//Estrutura de Pedido


typedef struct {
    int pid;
    int command; // 1 - Login, 2 - Registro
    char username[MAX];
    char password[MAX];
    int tecla;


} REQUEST;


//Estrutura de Resposta


typedef struct {
    int command; //1 - Login, 2 - Registro, 3 - MSG de Aviso(Ex: cliente X fez logout), 4 - LogOut, 5 - Sair (Shutdown)
    int message; //1 - Confirmado / Efectuado, 0 -Nao confirmado / Nao efectuado
    char notice[MAX]; //Mensagem Predefina Enviada aos Clientes
    int width;
    int height;
    MAP maze[MAX_LINE][MAX_COL];


} RESPONSE;






typedef struct{
    int id;
    int posX;
    int posY;
}ENEMY;


const int minLine = 20;
const int minCol = 30;


int fd, res, fd_res, NOBJECT, NENEMY, NMAXPLAY;
bool CHECK = false;
bool VALIDATE = false;
bool QUIT = false;
bool EXIT = false;
bool SHUTDOWN = false;
bool firstClient = true;
bool ENDTHREAD = false;


WINDOW *menu_win, *form_win, *info_win, *game_win;
static char id = 96;

```

---

### Post by dwhitney67 on 2017-12-28
A few comments:

1.  The statement srand((unsigned) time(NULL)) should only be called once in your application (preferably outside of the thread).

2.  You should check to verify that the argument that is passed to the thread is non-NULL before you attempt to access data from it.  For example:
```

    ...
    if (inimigo == NULL)
    {
        fprintf(stderr, "Argument is NULL");
        return NULL;
    }
    x = xOrig = inimigo->posX;
    y = yOrig = inimigo->posY;
    ...

```

3.  Your code does not work *perfect*, otherwise you would not have posted here on UF.  Your claims regarding your success on a Mac OS X are dubious, and perhaps is most likely due to luck.  You did not indicate how you ran 'gdb', and since you stated it did not point out the error, perhaps you did not invoke it correctly.  Follow these instructions:

    a.  Include symbolic/debugging information within your application by compiling it with the -g option, and by disabling optimization (-O0).

    b.  Enable core file generation within your terminal using this command:  ulimit -c unlimited

    c.  Execute your program from the terminal; for example:  ./yourprogram

    d.  Run GDB, with a command like:  gdb ./yourprogram core

    e.  As soon as you see the gdb prompt, enter "bt", or "backtrace".

    f.  Using GDB, examine the variables in your thread.  I suspect that an index is out of bounds.  You can use the 'print' command for this.


Final notes:  Use your header file to declare data structures.  Avoid declaring non-constant variables, for this implies that you are using global variables, which is a bad/evil practice.  You should also follow the standard convention when defining enumeration variables (e.g. player, emptyBlock, etc.); these should be in all uppercase letters (e.g. PLAYER, EMPTY_BLOCK, etc.) for they denote fixed constants.  Your use of all uppercase letters for your structure names adds confusion to this practice.  I would recommend that you choose better names (e.g. UserRequest, UserResponse, EnemyPosition, etc.).

---

