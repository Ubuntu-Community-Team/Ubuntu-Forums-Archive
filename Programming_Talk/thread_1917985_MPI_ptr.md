---
title: "MPI ptr*"
date: 2012-01-31
forum: Programming Talk
---

### Post by vandorjw on 2012-01-31
Hey everyone, I am playing around with MPI and parrallel programming.
It compiles fine, but when I attempt to run the program, it segfaults on me. If anyone is able to see why and point out my mistake I would be gratefull :D

My intend is once each process has sorted their parts, they send their data to process 0 (Master) which adds it all up to make the histogram.

Its quite rough, but I am still learning.
The code in [COLOR="Red"]RED[/COLOR] is where problems come up. I am not yet a master of pointers..

```

[COLOR="DarkGreen"]#include "mpi.h"
#include <math.h>
#include <stdio.h>
#include <stdlib.h>[/COLOR]

const int SEED = 132941;

[COLOR="Blue"]/* Function Prototype */[/COLOR]
[COLOR="Blue"]//void histogram(int N, double m, double M, int nbins, int *bin_counts, double *bins);[/COLOR]

void histogram(int N, double m, double M, int nbins, int *bin_counts) {

    int comm_sz;    [COLOR="Blue"]/* Number of Processes. */[/COLOR]
    int my_rank;    [COLOR="Blue"]/* My process rank. */[/COLOR]

    int dest;
    int offset;
    int i;
    int j;
    int tag1;
    int tag2;

    double bin_width;                  [COLOR="Blue"] /* Sets Bin width. */[/COLOR]
    double bin_maxes[nbins];            [COLOR="Blue"]/* Hold max value of each bin. */[/COLOR]


    [COLOR="Blue"]/* Calculate the min-max value of each bin */[/COLOR]
    bin_width = (M-m)/nbins;
    for(j=0; j<nbins; j++)
        bin_maxes[j] = m + bin_width*(j+1);


    MPI_Status status;

    [COLOR="Blue"]/***** Initializations *****/[/COLOR]
    MPI_Init(NULL,NULL);
    MPI_Comm_size(MPI_COMM_WORLD, &comm_sz);
    MPI_Comm_rank(MPI_COMM_WORLD, &my_rank);

    printf ("MPI task %d has started...\n", my_rank);
[COLOR="Blue"]
    /*chunk sizes*/[/COLOR]
    int chunksize[comm_sz-1];
    int r, r_alocated = 0;
    for(r=0; r<(comm_sz-1); r++) {
        chunksize[r] = (int)ceil((N-r_alocated)/(comm_sz-1-r));
        r_alocated += chunksize[r];
    }

[COLOR="Blue"]    /* Declaring the array with all the data.
       Every single processor has this array.
       Waste of ram...but don't know how to fix as of yet.
     */[/COLOR]
    double *data = (double *)malloc(N* sizeof(double));
    if (data == NULL) {
        fprintf (stderr, "Insufficient memory Available!" );
        exit(1);
    }

    tag2 = 1;
    tag1 = 2;

 [COLOR="Blue"]   /***** Master task ******/[/COLOR]
    if (my_rank == 0){

      [COLOR="Blue"]  /* Fill the array */[/COLOR]

            srand(SEED);
            int i;
            for (i=0; i<N; i++){
               [COLOR="Blue"] //drand==0, then m              is smallest number
                //drand==1, then m + 1*(M-m)    is largest number[/COLOR]
                data[i] = m + drand48()*(M-m);
            }

        [COLOR="Blue"]/* Send each task its portion of the array */[/COLOR]
        offset = 0;
        for (dest=1; dest<comm_sz; dest++) {
            MPI_Send(&offset, 1, MPI_INT, dest, tag1, MPI_COMM_WORLD);
            MPI_Send(&data[offset], chunksize[dest-1], MPI_FLOAT, dest, tag2, MPI_COMM_WORLD);
            printf("Sent %d elements to task %d offset= %d\n",chunksize[dest-1],dest,offset);
            offset = offset + chunksize[dest-1];
        }
[COLOR="Blue"]
    /* Other Processes */[/COLOR]
    } else {
        offset = 0;
        for(dest=1; dest<comm_sz;dest++) {
            if(dest==my_rank) {
                MPI_Recv(&offset, 1, MPI_INT, 0, tag1, MPI_COMM_WORLD, &status);
                MPI_Recv(&data[offset], chunksize[dest-1], MPI_DOUBLE_PRECISION, 0, tag2, MPI_COMM_WORLD, &status);
                printf("Sup from %d::Received %d amount of data with offset %d!\n",my_rank,chunksize[dest-1],offset);

                [COLOR="Blue"]//Now that the process has the data, sort it into bins[/COLOR]

                for(i=offset; i < offset + chunksize[dest-1]; i++) {
                    [COLOR="Blue"]//Check in which bin data[i] belongs, using bin_maxes[/COLOR]
                    int ii;
                    for(ii=0; ii<nbins;ii++){
                        if(data[i]>(bin_maxes[i]-bin_width) && data[i]<bin_maxes[i]){
                            [COLOR="Red"]bin_counts[i]++;
                             **//This here is giving me the problem** 
[/COLOR]
                        }
                    }
                }
            }
            offset = offset + chunksize[dest-1];
        }
    }

    MPI_Finalize();
}

int main(int argc, char *argv[]){

    int N = 1000;
    double m = 5.23;
    double M = 27.64;
    int nbins = 10;
[COLOR="Blue"]//    double *bins = (double *)malloc((nbins+1) * sizeof(double));[/COLOR]
    [COLOR="Red"]int *bin_counts[/COLOR] = (int *)malloc(nbins * sizeof(int));

    int k;
    for(k=0; k<nbins; k++)
        bin_counts[k]=0;

    histogram(N,m,M,nbins, [COLOR="Red"]bin_counts[/COLOR]);

    return 0;
}

```

---

### Post by Bachstelze on 2012-01-31
my guess is that bin_counts[i] should be bin_counts[ii].

---

### Post by vandorjw on 2012-01-31
Bachstelze: Thank you. You are correct. It was going out of bounds of the array!

---

