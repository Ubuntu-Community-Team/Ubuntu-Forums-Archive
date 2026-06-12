---
title: "C Segmentation Fault Pthreads"
date: 2017-12-05
forum: Programming Talk
---

### Post by ljzb on 2017-12-05
I'm performing square matrix multiplications. The matrices are loaded from a text file named **matrices.datomly** For small matrices like 5x5 sometimes it works, sometimes it doesn't, this error appears randomly, but for larger files like 100x100 it always says segmentation fault 'core' dumped. Also tried mutexes but still the same error.

```

/*
USAGE:
./fine <numThreads>
*/

//Standard libraries for C
#include <stdio.h>
#include <stdlib.h>


//Thread library, to create and manipulate threads
#include <pthread.h>


//Time library, to use a method to calculate execution time
#include <sys/time.h>




//pthread_mutex_t mymutex;


int matrixSize;//All matrices will be square
int NUM_THREADS; //Number of threads to be created
int nmats;//Number of pairs of matrices
int myIndex;//Index for the array of structures
struct matrix{
    double **a,**b,**c;


};


struct matrix data[500];//The variable 'data' will contain the entire set of matrices in the text file


//************************************************************************************************//
/******************Function build to create dynamic memory for the matrices************************/
//************************************************************************************************//
double **allocateMatrix()
{
    int i;
    double *vals, **temp;


    // allocate space for values of a matrix
    vals = (double *) malloc (matrixSize * matrixSize * sizeof(double));


    // allocate vector of pointers to create the 2D array
    temp = (double **) malloc (matrixSize * sizeof(double*));


    for(i=0; i < matrixSize; i++)
        temp[i] = &(vals[i * matrixSize]);


    return temp;
}//End of Function


//************************************************************************************************//
/*************************************Multiplication function**************************************/
//************************************************************************************************//
void * mm(void *threadid) {
    int i,j,k;
    double sum;
    int portion=matrixSize/NUM_THREADS;
    int remain=matrixSize%NUM_THREADS;
    int final=0;
//    printf("\nThread #%ld\n",(long)threadid);
    for(myIndex=0;myIndex<nmats;myIndex++)
    {
        printf("\nPair #%d of %d\n",myIndex+1,nmats);
        if(matrixSize % NUM_THREADS != 0)
        {
            if(((long)threadid + 1) == NUM_THREADS)
            {
                final = matrixSize;
            }
            else
            {
                final= (portion*((long)threadid + 1));
            }
        }
        else
        {
            //Defining number of steps, according to the number of threads
            final=(portion*((long)threadid + 1));
        }
        for (i = (portion*(long)threadid); i < final; i++)
        {
            for (j = 0; j < matrixSize; j++)
            {
                sum = 0;
                //Dot product
                for (k = 0; k < matrixSize; k++)
                {
                    sum = sum + data[myIndex].a[i][k] * data[myIndex].b[k][j];
                }
                //pthread_mutex_lock (&mymutex);//Mutex lock
                data[myIndex].c[i][j] = sum;
                //pthread_mutex_unlock (&mymutex);//Mutex unlock                
                printf("%.0F ",data[myIndex].c[i][j]);


            }
            //Prints end of line after a single thread finishes its job
            printf("\n");
        }
    }
    putchar('\n');//Prints end of line after all the Threads are done
    pthread_exit(NULL);
}//End of Function




//************************************************************************************************//
/***********************************Printing Function**********************************************/
//************************************************************************************************//


void printResult(FILE *fres,char *results) //Once the threads are done, the C matrix will be stored in memory
{// as a double pointer variable
    int i, j;
    fres = fopen(results, "a");
    for(myIndex=0;myIndex<nmats;myIndex++)
    {
        printf("\nResult of Pair #%d:\n",myIndex+1);
        for (i = 0; i < matrixSize; ++i)
        {
            for (j = 0; j < matrixSize-1; ++j) //The last number will be printed without space after
            {
                printf( "%.0lf ", data[myIndex].c[i][j]);
                fprintf(fres, "%.0lf ", data[myIndex].c[i][j]);
            }
            fprintf(fres, "%.0lf", data[myIndex].c[i][j]);
            printf("%.0lf", data[myIndex].c[i][j]);
            printf("\n");
            fprintf(fres, "\n");
        }
    }
    fclose(fres);
}//End of Function


//************************************************************************************************//
/*************************************Main function************************************************/
//************************************************************************************************//
int main(int argc, char *argv[]) {


    struct timeval it,ft;//Inital time, final time
    double time;
    gettimeofday(&it, NULL);//Gets the initial time
    
    //pthread_attr_t attr; //Attribute for the threads
    //pthread_mutex_init(&mymutex, NULL);
    
    int rc,i,j;//i, j will be counters for loading matrices


    //    char *fname = "matrices_large.dat";
    char *fname = "matrices.dat"; //Change to matrices_large.dat for performance evaluation
    char *results="resFineGrain.txt";//Output file containing the results. It's created in order to compare
    //with the other version of the multiplication


    FILE *fh,*fres; //FILE type pointers, to manipulate the txt files


    //There should be 2 arguments to execute this script
    if (argc != 2) {
        printf("ERROR.\nHow to use: ./fine <NumberOfThreads>\n");
        exit(1);
    }
    //The number of threads will be converted from ascii to integer
    NUM_THREADS = atoi(argv[1]);


    //The text file is opened for reading
    fh = fopen(fname, "r");


    //Another txt file is created to store the results
    fres = fopen(results, "w");//Creates a txt file


    //First line indicates how many pairs of matrices there are and the matrix size
    fscanf(fh, "%d %d\n", &nmats, &matrixSize);


    //Creating an ID vector for threads
    pthread_t threads[NUM_THREADS];


    //'t' will be the thread id, and 'status' will be a pointer indicating if the thread has or hasn't finished its job
    long t;
    void *status;


    //Loading matrices from file
    printf("Loading %d pairs of square matrices of size %d from %s...\n", nmats, matrixSize, fname);


    for(myIndex=0;myIndex<nmats;myIndex++)
    {
        data[myIndex].a = allocateMatrix();
        data[myIndex].b = allocateMatrix();
        data[myIndex].c = allocateMatrix();


        for(i=0;i<matrixSize;i++)
        {
            for(j=0;j<matrixSize;j++)
            {
                fscanf(fh, "%lf", &data[myIndex].a[i][j]);
            }
        }


        for(i=0;i<matrixSize;i++)
        {
            for(j=0;j<matrixSize;j++)
            {
                fscanf(fh, "%lf", &data[myIndex].b[i][j]);
            }
        }
    }
    printf("Creating threads\n");
    //Creation of Threads
    for(t=0; t<NUM_THREADS; t++)
    {
        rc = pthread_create(&threads[t], NULL, mm, (void *)t);
        if (rc)
        {
            printf("ERROR; return code from pthread_create() is %d\n", rc);
            exit(-1);
        }
    }
    //pthread_attr_destroy(&attr);
    printf("Joining threads\n");
    for(t=0; t<NUM_THREADS; t++)
    {
        rc = pthread_join(threads[t], &status);
        if (rc)
        {
            printf("ERROR; return code from pthread_create() is %d\n", rc);
            exit(-1);
        }
    }
    printResult(fres,results);


    
    fclose(fh);
    //Free memory
    for(myIndex=0;myIndex<nmats;myIndex++)
    {
        free(*data[myIndex].a);
        free(data[myIndex].a);
        free(*data[myIndex].b);
        free(data[myIndex].b);
        free(*data[myIndex].c);
        free(data[myIndex].c);
    }


    //Execution time calculation
    gettimeofday(&ft, NULL);//Gets the final time
    time= (ft.tv_sec - it.tv_sec)*1000 + (ft.tv_usec - it.tv_usec)/1000.0;
    printf("Time (ms) = %g\n",time);
    //pthread_mutex_destroy(&mymutex);
    pthread_exit(NULL);
}



```

---

### Post by dwhitney67 on 2017-12-05
Compile your code with the -g option; this will include symbolic info within your executable so that you can determine where the code is crashing.

Next, set your core file size to unlimited before running your program.  To do this, run within a terminal console the following:  $ ulimit -c unlimited

Then from the same terminal console, run your program.

Finally, use the GNU Debugger (gdb) or the Data Display Debugger (ddd) to analyze the core file.  For example:  $ gdb ./yourprogram core.[pid-num]

Btw, I'm betting that the issue lies somewhere within allocateMatrix().  Also, I'm not convinced that you have properly thought about how to define the matrix structure.

---

