---
title: "Index values get garbage"
date: 2010-10-23
forum: Programming Talk
---

### Post by -A- on 2010-10-23
Ok, so here's my code for a modified cigarette smokers problem. The thing is, when my threads are being created for the smokers, after the creation of the 4th one the index value o becomes some rubbish negative value...I have no clue why. Any help?

```
#include<stdio.h>
#include<stdlib.h>
#include<pthread.h>
#include<semaphore.h>
#include<sys/ipc.h>

typedef struct
{
    int id;
    int item;
}rec;

//Gobal variable declarations
sem_t table,agent,arrayMutex;
sem_t *smoker;
time_t endTime;
int exitFire=0;
rec *arr;
int N;

//Function declarations
void *agentf(void *param);
void *smokerf(void *param);

int main(void)
{
    pthread_t atid;
    pthread_t stid[3];
    endTime=time(NULL)+1;
    int status,o,i;
    N=10;

    arr=(rec *)calloc(N,sizeof(rec));
    smoker=(sem_t *)calloc(N,sizeof(sem_t));

    sem_init(&agent,0,0);
    for(o=0;o<N;o++)
    {
        sem_init(&smoker[o],0,0);
    }
    sem_init(&table,0,1);
    sem_init(&arrayMutex,0,1);


    for(o=0;o<N;o++)
    {
        printf("initial index = %d\n",o);
        status= pthread_create(&stid[o],NULL,smokerf,(void *)o);
        if(status!=0){printf("Smoker%d thread not created.\n\n",o);}
        printf("after index= %d\n",o);

    }

    status=pthread_create(&atid,NULL,agentf,NULL);
    if(status!=0){printf("Agent thread not created.\n\n");}

    pthread_join(atid,NULL);
    printf("Agent joined.\n\n");

    exitFire=1;

    for(i=0;i<N;i++)
    {
        sem_post(&smoker[i]);
    }
    //sem_post(&table);
        //sem_post(&table);
            //sem_post(&table);


    for(i=0;i<N;i++)
    {
        pthread_join(stid[i],NULL);
        printf("Smoker%d joined\n\n",i);
    }


    return(EXIT_SUCCESS);
}


void *agentf(void *param)
{
    int randNo;
    int i;
    while(time(NULL)<endTime)
    {
        sem_wait(&table);
        again:
        randNo=rand()%3;
        randNo+=1;
        printf("Random number %d.\n\n",randNo);

        if(randNo==1)
        {
            printf("Tobacco and matches on table\n\n");
            for(i=0;i<N;i++)
            {
                if(arr[i].item==randNo)
                {
                    sem_post(&smoker[arr[i].id]);
                    break;
                }
            }
            if(i==N){printf("Smoker type not there. Going back.\n\n");goto again;}
        }
        else if(randNo==2)
        {
            printf("Tobacco and paper on table\n\n");
                        for(i=0;i<N;i++)
            {
                if(arr[i].item==randNo)
                {
                    sem_post(&smoker[arr[i].id]);
                    break;
                }
            }
            if(i==N){printf("Smoker type not there. Going back.\n\n");goto again;}
        }
        else if(randNo==3)
        {
            printf("Paper and matches on table\n\n");
                        for(i=0;i<N;i++)
            {
                if(arr[i].item==randNo)
                {
                    sem_post(&smoker[arr[i].id]);
                    break;
                }
            }
            if(i==N){printf("Smoker type not there. Going back.\n\n");goto again;}
        }
        sem_post(&table);
        sem_wait(&agent);
    }
     pthread_exit(0);

}


void *smokerf(void *param)
{
    int choose,sindex,sitem,place;
    sindex=(int)param;
    sitem=rand()%3;
    sitem+=1;
    printf("Done till here.\n");
    sem_wait(&arrayMutex);
    arr[sindex].id=sindex;
    printf("Done here.\n");
    arr[sindex].item=sitem;
    sem_post(&arrayMutex);

    if(sitem==1)
    {
        printf("choosing 0 done,\n\n");
        int i;
        while(time(NULL)<endTime)
        {
            sem_wait(&smoker[sindex]);
            if(exitFire==1){pthread_exit(0);}
            sem_wait(&table);
            printf("paperSmoker got the stuff!\n\n");
            printf("paperSmoker on a high baby!\n\n");

            sem_wait(&arrayMutex);
            for(i=0;i<N;i++)
            {
                if(arr[i].id==sindex)
                {
                    place=i;
                    break;
                }
            }
            for(i=place+1;i<N+1;i++)
            {
                arr[i-1].id=arr[i].id;
                arr[i-1].item=arr[i].item;
            }
            arr[N].id=sindex;
            arr[N].item=sitem;
            sem_post(&arrayMutex);

            sem_post(&agent);
            sem_post(&table);

        }
        pthread_exit(0);
    }
    else if(sitem==2)
    {
                printf("choosing 1 done,\n\n");

        int j;
        while(time(NULL)<endTime)
        {
            sem_wait(&smoker[sindex]);
            if(exitFire==1){pthread_exit(0);}
            sem_wait(&table);
            printf("matchSmoker got the stuff!\n\n");
            printf("matchSmoker on a high baby!\n\n");

            sem_wait(&arrayMutex);
            for(j=0;j<N;j++)
            {
                if(arr[j].id==sindex)
                {
                    place=j;
                    break;
                }
            }
            for(j=place+1;j<N+1;j++)
            {
                arr[j-1].id=arr[j].id;
                arr[j-1].item=arr[j].item;
            }
            arr[N].id=sindex;
            arr[N].item=sitem;
            sem_post(&arrayMutex);
            sem_post(&agent);
            sem_post(&table);

        }
        pthread_exit(0);
    }
    else if(sitem==3)
    {
                printf("choosing 2 done,\n\n");
                int k;
        while(time(NULL)<endTime)
    {
        sem_wait(&smoker[sindex]);
        if(exitFire==1){pthread_exit(0);}
        sem_wait(&table);
        printf("tobacSmoker got the stuff!\n\n");
        printf("tobacSmoker on a high baby!\n\n");

                    sem_wait(&arrayMutex);
            for(k=0;k<N;k++)
            {
                if(arr[k].id==sindex)
                {
                    place=k;
                    break;
                }
            }
            for(k=place+1;k<N+1;k++)
            {
                arr[k-1].id=arr[k].id;
                arr[k-1].item=arr[k].item;
            }
            arr[N].id=sindex;
            arr[N].item=sitem;
            sem_post(&arrayMutex);

        sem_post(&agent);
        sem_post(&table);

    }
    pthread_exit(0);
    }
}

```

---

### Post by ibuclaw on 2010-10-23
Two questions:

[LIST=1]
[*]What is the size of the static array 'stid' ?
[*]What is the value of the global integer 'N' ?
[/LIST]

Realising this should solve your problem. :)

---

### Post by -A- on 2010-10-24
*feels so stupid* I just didn't notice that..I had hard coded the thing before, and forgot to remove it. 

Thank you so much!

---

### Post by Vox754 on 2010-10-24
> **-A- said:**
> Ok, so here's my code for a modified cigarette smokers problem. The thing is, when my threads are being created for the smokers, after the creation of the 4th one the index value o becomes some rubbish negative value...I have no clue why. Any help?

```

...
    for(o=0;o<N;o++)
    {
        printf("initial index = %d\n",o);
        status= pthread_create(&stid[o],NULL,smokerf,(void *)o);
        if(status!=0){printf("Smoker%d thread not created.\n\n",o);}
        printf("after index= %d\n",o);

    }
...
```
Lol. Don't use "o" (oh) as a variable. It's confusing, and may be mistaken as "0" (zero).

For a single program it's okay, but if you are going to program in a professional environment don't do it. It would be a nightmare to debug thousands of lines of source code with variables like that.

Experts recommend avoiding other letters such as "l" (ell), because it can be confused with "1" (one). Monospaced fonts make the distinction clear (when your eyes are not tired!), but that is not the case with other fonts, such as this very same paragraph!

You may use the plain old "i", or even "ii", "jj" or "kk" to make it more evident and avoid problems in the future.

---

