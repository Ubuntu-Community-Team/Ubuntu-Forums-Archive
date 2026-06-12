---
title: "ERROR OPENING A FILE IN c"
date: 2012-11-01
forum: Programming Talk
---

### Post by xixzeroxix on 2012-11-01
hello everyone, im having a headache with this error im getting, im trying to read a number from a file but inside a Switch(case) statement but im getting alot of erros only inside the case and i cant figure out why if my open file code is correct (as far as i know) i need to read a number from the file and make a + with my (ac) variable

heres my code

```
#include <stdio.h>
#include <stdlib.h>



int main ()
{
   int pc;
   int ir;
   int cod;
   int ac=0;
   int i=0;
   int dir;
   int c=0;
   int num_datos;
   int dir_datos=0;
   int MAX=0;
   int x=0;


    int valor[1000];



        printf("Formato de los datos 0000\n\n");
  /*      printf("DATOS\n\n");
        printf("100\t0005\n")
        printf("101\t0002\n\n");   */
printf("\n");
        printf("Cuantas instrucciones vas a capturar?\n");
        scanf("%d",&dir);//5
printf("\n");
        printf("Escriba la direccion de la primer instruccion\n");
        scanf("%d",&pc);//100
printf("\n");
      //  printf("Escriba el valor de la direccion de memoria\n");
      //  scanf("%d",&ir);//1200
        printf("Escriba Cuantos datos van a haber\n");
        scanf("%d",&num_datos);//3
printf("\n");
        printf("Escriba la direccion de los datos\n");
        scanf("%d",&dir_datos);//200
        MAX=num_datos+dir_datos;
printf("\n");
                    for(i=dir_datos; i<MAX; i++)
                        {

                            printf("Escriba el valor del dato [%d]\n",dir_datos);
                            scanf("%d",&c);
                            valor[i]=c;
                            dir_datos++;
printf("\n");
                        }
               dir_datos=dir_datos-num_datos;
                       for(i=dir_datos; i<MAX; i++)
                        {
                            printf("%d \t %d\n",i,valor[i]);
                        }



        printf("\n");


              //  cod=ir/1000;
             //   dir=ir%1000;


           //for(i=0; i<dir; i++)

                while(x<dir)
                {

                printf("Escriba el valor de la direccion de memoria\n");
                scanf("%d",&ir);//1200


                cod=ir/1000;//este ya esta listo
             //   Mem=ir%1000;//el % significa el resto de la division
               dir_datos=ir%1000;


                    switch(cod)//esta correctamente evaluado
                    {
                        case 0:


                        printf("tomaste el caso 0\n");
                        printf("%d \t %d \t %d\n" ,pc,ir,ac);
                        pc++;
                        x++;

                        break;

                        case 1:

                        printf("tomaste el caso 1\n");
                            for(i=dir_datos; i<MAX; i++)
                            {
                                if(i==dir_datos)
                                {
                                printf("%d \t %d \t %d\n" ,pc,ir,ac);
                                ac=valor[dir_datos];
                                }
                            }

                        //Mem=ir%1000;
                       // printf("i=%d\n",i);
                       // ac=Mem[dir];
                        pc++;
                        x++;

                        break;

                        case 2:

                     printf("tomaste el caso 2\n");
                     for(i=dir_datos; i<MAX; i++)
                            {
                                if(i==dir_datos)
                                {
                                ac=valor[dir_datos];
                                printf("%d \t %d \t %d\n" ,pc,ir,ac);
                                }
                            }
                        pc++;
                        x++;

                        break;

                        case 3:

                    printf("tomaste el caso 3\n");
                    for(i=dir_datos; i<MAX; i++)
                            {
                                if(i==dir_datos)
                                {
                                ac=ac+valor[dir_datos];
                                printf("%d \t %d \t %d\n" ,pc,ir,ac);
                                }
                            }
                        pc++;
                        x++;

                        break;

                        case 4:

                    printf("tomaste el caso 4\n");
                    for(i=dir_datos; i<MAX; i++)
                            {
                                if(i==dir_datos)
                                {
                                ac=ac-valor[dir_datos];
                                printf("%d \t %d \t %d\n" ,pc,ir,ac);
                                }
                            }
                        pc++;
                        x++;

                        break;

                        case 5:

                    printf("tomaste el caso 5\n");
                    for(i=dir_datos; i<MAX; i++)
                            {
                                if(i==dir_datos)
                                {
                                ac=ac*valor[dir_datos];
                                printf("%d \t %d \t %d\n" ,pc,ir,ac);
                                }
                            }
                        pc++;
                        x++;

                        break;

                        case 6:

                    printf("tomaste el caso 6\n");
                    for(i=dir_datos; i<MAX; i++)
                            {
                                if(i==dir_datos)
                                {
                                ac=ac/valor[dir_datos];
                                printf("%d \t %d \t %d\n" ,pc,ir,ac);
                                }
                            }
                        pc++;
                        x++;

                        break;
///////////////////////////////////////////////////////////////////////////////////////////
                        case 7:


// int producto ( int argc, char **argv )
//{int c;
        FILE *archivo;

        //char buffer[100];
        int c;
       archivo = fopen ( "archivo.txt", "r" );
         while((c = fgetc(archivo)) != EOF) {
       ac=ac+c;
    }
       // fscanf(archivo, "%s" ,buffer);
        //buffer=atoi(buffer);
         //   ac=ac+buffer;
        printf("Convirtiendo la cadena  %s  en un numero: %d\n",buffer);

                                printf("%d \t %d \t %d\n" ,pc,ir,ac);
        fclose ( archivo );

        return 0;
//}


                                        pc++;
                                        x++;
                        break;
/////////////////////////////////////////////////////////////////////////////////////////////////
                        case 8:

                    printf("tomaste el caso 8\n");
                    printf("%d \t %d \t \n" ,pc,ir);
                            //8 Escribe AC en archivos.txt
                    pc++;
                    x++;

                        break;


                    }
            }
            return 0;

}
```

---

### Post by Bachstelze on 2012-11-01
This error:

```
test.c:182:13: error: a label can only be part of a statement and a declaration is not a statement
```

Is kinda tricky. Basically what it means is that when you have a label (either a case or a label to use with goto), it must be followed by a statement. In your code, you have

```
case 7:
    FILE *archive;
```

and this doesn't work because the second line here is a declaration, not a statement. A workaround is

```
case 7:
    ;
    FILE *archive;
```

---

### Post by satsujinka on 2012-11-01
Or do:
```
FILE *archive = fopen("archive.txt", "r");
```

---

