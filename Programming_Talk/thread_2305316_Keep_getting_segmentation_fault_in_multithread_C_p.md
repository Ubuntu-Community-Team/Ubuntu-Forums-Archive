---
title: "Keep getting segmentation fault in multithread C program"
date: 2015-12-04
forum: Programming Talk
---

### Post by shaylen on 2015-12-04
Hello everyone, I am writing a multithread C program for my OS class, however every time I enter an number of threads higher than 1, I get a segmentation fault of 11. 
Thanks in advance for any help. 

Here is my code:

```
#include <stdio.h>
#include <pthread.h>
#include <stdlib.h>




struct thread_data{
    FILE *fp;
    long int offset;
    int start;
    int blockSize;
}


int words=0;  


void *countFrequency(void* data){


    struct thread_data* td=data;
    char *buffer = malloc(td->blockSize);


    int i,c;
    i=0;c=0;
    enum states { WHITESPACE, WORD };
    int state = WHITESPACE;


    fseek(td->fp, td->offset, td->start);


        char last = ' '; 
        while ((fread(buffer, td->blockSize, 1, td->fp))==1){


            if ( buffer[0]== ' ' || buffer[0] == '\t'  ){
            state = WHITESPACE;
            }
            else if (buffer[0]=='\n'){
            //newLine++;
                state = WHITESPACE;
            }
            else {
                if ( state == WHITESPACE ){
                    words++;
                }
                state = WORD;
            }
            last = buffer[0];
    }
    free(buffer);


    pthread_exit(NULL);


    return NULL;
}


int main(int argc, char **argv){


    int nthreads, x, id, blockSize,len;
    //void *state;
    FILE *fp;
    pthread_t *threads;


    struct thread_data data[nthreads];


    if (argc < 2){
        fprintf(stderr, "Usage: ./a.out <file_path>");
        exit(-1);
    }


    if((fp=fopen(argv[1],"r"))==NULL){
        printf("Error opening file");
        exit(-1);
    }  


    printf("Enter the number of threads: ");
    scanf("%d",&nthreads);
    threads = malloc(nthreads*sizeof(pthread_t));


    fseek(fp, 0, SEEK_END);
    len = ftell(fp);  
    printf("len= %d\n",len);


    blockSize=(len+nthreads-1)/nthreads;
    printf("size= %d\n",blockSize);


    for(id = 0; id < nthreads; id++){


        data[id].fp=fp;
        data[id].offset = blockSize;
        data[id].start = id*blockSize+1;


        }
        //LAST THREAD
        data[nthreads-1].start=(nthreads-1)*blockSize+1;


        for(id = 0; id < nthreads; id++)
            pthread_create(&threads[id], NULL, &countFrequency,&data[id]);


    for(id = 0; id < nthreads; id++)
        pthread_join(threads[id],NULL);


    fclose(fp);
    //free(threads);


    //pthread_exit(NULL);


    printf("%d\n",words); 
    return 0;  
}








}

```

---

### Post by spjackson on 2015-12-04
Consider this carefully:
> 
    struct thread_data data[nthreads];


---

### Post by shaylen on 2015-12-04
bro I have tried asking on other forums and I still can not figure this out. I tried using a mutex lock, but that still did not help.

---

### Post by sisco311 on 2015-12-04
Welcome to the forums, shaylen!

From the [thread=2158945]Posting Guidelines[/thread]:
> 
8. While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

 

spjackson already pointed out a very obvious error in your code. If that wasn't helpful for you, then I'm afraid that all we can suggest for you is to re-read your learning material.

---

### Post by QIII on 2015-12-04
The first post was great and the answer was spot on.  That is what we hope to see in the "hints and minor sticking points" homework questions.

Unfortunately, we may have stepped past that now.

Closed.

---

