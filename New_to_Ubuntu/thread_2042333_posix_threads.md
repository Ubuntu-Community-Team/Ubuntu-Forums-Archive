---
title: "posix threads"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by catlakprofesormfb on 2012-08-14
Hello everybody!
First of all sorry for my bad english.
I started to learn c programming language and i am new.
First i made a program which calculates prime numbers smaller than a number and this program wrotes them on the screen. But then i noticed that may program can use only one of my cores. I have an i5 processor and  it has 4 cores. thats why i decided to make a multithreaded program. But i have problems. Can you correct my code?

#include <stdio.h>
#include <stdlib.h>
#include <windows.h>
#include <math.h>
#include <pthread.h>
#include <process.h>
#define PROCESSOR_NUMBER 4
void *asal_sayi_bulur (void *_pthread_create[5])
{
    int increment=PROCESSOR_NUMBER*2;
    long unsigned k,i,now_number1;
    long unsigned *now_number2;
    int *thread_number;
    int *lock;
    long unsigned *last_number;
    long unsigned *asallar[50000];
    now_number2=(long unsigned*)_pthread_create[4];
    last_number=(long unsigned*)_pthread_create[2];
    asallar[50000]=(long unsigned*)_pthread_create[3];
    thread_number=(int*)_pthread_create[0];
    lock=(int*)_pthread_create[1];
    now_number1=(*thread_number*2)+5;
    while(now_number1<=*last_number)
    {
        for(k=0;*asallar[k]**asallar[k]<=now_number1&&now_number1%*asallar[k]!=0&&*asallar[k]!=0;k++)
        {
            if(*asallar[k]**asallar[k]<=now_number1)
            {
                i=*asallar[k];
                while(now_number1%i!=0&&i*i<=now_number1)
                {
                    i+=2;
                }
            }
        }
        if(now_number1%i!=0&&now_number1%*asallar[k-1]!=0)
        {
            locked:
            if(*lock==1)
            {
                goto locked;
            }
            if(*lock==0)
            {
                *lock=1;
                *asallar[k]=now_number1;
                *now_number2=now_number1;
                *lock=0;
                now_number1+=increment;
            }
        }
    }
    return NULL;
}
int main(void)
{
    int main_lock;
    long unsigned *main_pthread_create[5];
    int main_thread_number;
    long unsigned main_last_number;
    long unsigned main_asallar[50000];
    long unsigned main_now_number2;
    long unsigned main_u;
    pthread_t pointer_of_threads[PROCESSOR_NUMBER];
    *main_pthread_create[0]=&main_thread_number+1;
    *main_pthread_create[1]=&main_lock;
    *main_pthread_create[2]=&main_last_number;
    *main_pthread_create[3]=main_asallar[50000];
    *main_pthread_create[4]=&main_now_number2;
    main_asallar[50000]=0;
    main_asallar[0]=2;
    main_asallar[1]=3;
    main_asallar[2]=5;
    main_lock=0;
    gel:
    printf("Lutfen hangi sayiya kadar asal sayilari gormek istediginizi yaziniz\n");
    scanf("%lu",&main_last_number);
    if(main_last_number<2){goto gel;}
    if(main_last_number>=2){printf("#2#");}
    if(main_last_number>=3){printf("3#");}
    if(main_last_number>=5){printf("5#");}
    if(main_last_number>=7)
    {
        for(main_thread_number=0;main_thread_number<PROCESSOR_NUMBER;main_thread_number++)
        {
            pthread_create(&pointer_of_threads[main_thread_number],NULL,asal_sayi_bulur,*main_pthread_create[5]);
        }
    }
    if(main_now_number2>=main_last_number)
    {
        Sleep(1000);
        for(main_u=3;main_asallar[main_u]!=0;main_u++)
            {
            printf("%lu#",main_asallar[main_u]);
            }
    }
    printf("\n");
    system("pause");
    return 0;
}

Thanks for Help
I didn't know which prefix i can use.
If it is not suited, sorry about that.

---

