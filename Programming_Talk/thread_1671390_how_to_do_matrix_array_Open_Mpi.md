---
title: "how to do matrix array Open Mpi"
date: 2011-01-19
forum: Programming Talk
---

### Post by arepisa on 2011-01-19
Hello,

Suppose I have A[100,100] Matrix.I want to send every Sub matrix SM[10,10] to the 10 worker PC using Open MPI, to do the operation (SM[i,j] -= 5) and return the edited SM[10,10] to the Master PC. Could any one suggest me how can I do this. Tq

---

### Post by talonmies on 2011-01-20
If the operation is "embarassingly parallel" (so there are no inbuilt ordering relationships between MPI rank and the data), then using [MPI_Scatter]("http://www.open-mpi.org/doc/v1.5/man3/MPI_Scatter.3.php") and [MPI_Gather]("http://www.open-mpi.org/doc/v1.5/man3/MPI_Gather.3.php") is probably the most efficient and simplest method.

---

### Post by arepisa on 2011-01-20
Im sorry, but i am very beginner using this Open MPI thing. Could u provide me some example using this MPI_Scatter & MPI_Gather. I need to read the matrix array from file and then divide the array between 10 working computer to do some operation on each value and then send the result back to master computer to combine the result matrix array back and print to output file. TQ very much for your help.

---

### Post by talonmies on 2011-01-20
No sorry, I will not provide you with an working example (you haven't even said what language you are planning to write this in, MPI natively supports bindings in C, C++ and Fortran 90/95). I will, however,  provide you with this [link]("http://tinyurl.com/4cu2jsy"), which is a very useful starting point, if you have never tried it before.

---

### Post by arepisa on 2011-01-21
Im plannning to do it in C. Thanks for your guide.

---

### Post by arepisa on 2011-03-01
I have to distributed arrays in pgm image file format P2 using Open MPI. I have problem to compile the code. It says segmentation fault. Could someone please see what wrong with may code? TQ



```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <mpi.h>

#define SIZE_X 640
#define SIZE_Y 480



  
 int main(int argc, char **argv) 
{
    FILE *FR,*FW;
    int ierr;
    int rank, size;
    int ncells;
    int greys[SIZE_X][SIZE_Y];
    int rows,cols, maxval;
    
    int mystart, myend, myncells;
    const int IONODE=0;
    int *disps, *counts, *mydata;
    int *data;
    int i,j,temp1;
    char dummy[50]="";
    
    



    ierr = MPI_Init(&argc, &argv);
    if (argc != 3) {
        fprintf(stderr,"Usage: %s infile outfile\n",argv[0]);
        fprintf(stderr,"outputs the negative of the input file.\n");
        return -1;
    }            

    ierr  = MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    ierr |= MPI_Comm_size(MPI_COMM_WORLD, &size);
    if (ierr) {
        fprintf(stderr,"Catastrophic MPI problem; exiting\n");
        MPI_Abort(MPI_COMM_WORLD,1);
    }

    if (rank == IONODE) {
         
         rows=SIZE_X;
         cols=SIZE_Y;
         maxval=255;
         FR=fopen(argv[4], "r+");
        
         fgets(dummy,50,FR);
         do{  fgets(dummy,50,FR); } while(dummy[0]=='#');
         fgets(dummy,50,FR);

         for (j = 0; j <cols; j++)
         {
           for (i = 0; i <rows; i++)
           {
               fscanf(FR,"%d",&temp1);
             greys[i][j] = temp1;
           }
         }
    }

        ncells = rows*cols;
        disps = (int *)malloc(size * sizeof(int));
        counts= (int *)malloc(size * sizeof(int));
        data = &(greys[0][0]); /* we know all the data is contiguous */
        
    /* everyone calculate their number of cells */
    ierr = MPI_Bcast(&ncells, 1, MPI_INT, IONODE, MPI_COMM_WORLD);
    myncells = ncells/size;
    mystart = rank*myncells;
    myend   = mystart + myncells - 1;
    if (rank == size-1) myend = ncells-1;
    myncells = (myend-mystart)+1;
    mydata = (int *)malloc(myncells * sizeof(int));

    /* assemble the list of counts.  Might not be equal if don't divide evenly. */
    ierr = MPI_Gather(&myncells, 1, MPI_INT, counts, 1, MPI_INT, IONODE, MPI_COMM_WORLD);
    if (rank == IONODE) {
        disps[0] = 0;
        for (i=1; i<size; i++) {
            disps[i] = disps[i-1] + counts[i-1];
        }
    }

    /* scatter the data */
    ierr = MPI_Scatterv(data, counts, disps, MPI_INT, mydata, myncells, 
                        MPI_INT, IONODE, MPI_COMM_WORLD);

    /* everyone has to know maxval */
    ierr = MPI_Bcast(&maxval, 1, MPI_INT, IONODE, MPI_COMM_WORLD);

    for (i=0; i<myncells; i++)
        mydata[i] = maxval-mydata[i];

    /* Gather the data */
    ierr = MPI_Gatherv(mydata, myncells, MPI_INT, data, counts, disps, 
                        MPI_INT, IONODE, MPI_COMM_WORLD);

    if (rank == IONODE) 
    {

      FW=fopen(argv[5], "w");
      fprintf(FW,"P2\n%d %d\n255\n",rows,cols);    
      for(j=0;j<cols;j++)
        for(i=0;i<rows;i++) 
       fprintf(FW,"%d ", greys[i][j]);
    }

    free(mydata);
    if (rank == IONODE) {
        free(counts);
        free(disps);
        free(&(greys[0][0]));
        free(greys);
                
    }
    fclose(FR);
    fclose(FW);
    MPI_Finalize();
    return 0;
}


```

---

### Post by Arndt on 2011-03-01
> **arepisa said:**
> I have to distributed arrays in pgm image file format P2 using Open MPI. I have problem to compile the code. It says segmentation fault. Could someone please see what wrong with may code? TQ



```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <mpi.h>

#define SIZE_X 640
#define SIZE_Y 480



  
 int main(int argc, char **argv) 
{
    FILE *FR,*FW;
    int ierr;
    int rank, size;
    int ncells;
    int greys[SIZE_X][SIZE_Y];
    int rows,cols, maxval;
    
    int mystart, myend, myncells;
    const int IONODE=0;
    int *disps, *counts, *mydata;
    int *data;
    int i,j,temp1;
    char dummy[50]="";
    
    



    ierr = MPI_Init(&argc, &argv);
    if (argc != 3) {
        fprintf(stderr,"Usage: %s infile outfile\n",argv[0]);
        fprintf(stderr,"outputs the negative of the input file.\n");
        return -1;
    }            

    ierr  = MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    ierr |= MPI_Comm_size(MPI_COMM_WORLD, &size);
    if (ierr) {
        fprintf(stderr,"Catastrophic MPI problem; exiting\n");
        MPI_Abort(MPI_COMM_WORLD,1);
    }

    if (rank == IONODE) {
         
         rows=SIZE_X;
         cols=SIZE_Y;
         maxval=255;
         FR=fopen(argv[4], "r+");
        
         fgets(dummy,50,FR);
         do{  fgets(dummy,50,FR); } while(dummy[0]=='#');
         fgets(dummy,50,FR);

         for (j = 0; j <cols; j++)
         {
           for (i = 0; i <rows; i++)
           {
               fscanf(FR,"%d",&temp1);
             greys[i][j] = temp1;
           }
         }
    }

        ncells = rows*cols;
        disps = (int *)malloc(size * sizeof(int));
        counts= (int *)malloc(size * sizeof(int));
        data = &(greys[0][0]); /* we know all the data is contiguous */
        
    /* everyone calculate their number of cells */
    ierr = MPI_Bcast(&ncells, 1, MPI_INT, IONODE, MPI_COMM_WORLD);
    myncells = ncells/size;
    mystart = rank*myncells;
    myend   = mystart + myncells - 1;
    if (rank == size-1) myend = ncells-1;
    myncells = (myend-mystart)+1;
    mydata = (int *)malloc(myncells * sizeof(int));

    /* assemble the list of counts.  Might not be equal if don't divide evenly. */
    ierr = MPI_Gather(&myncells, 1, MPI_INT, counts, 1, MPI_INT, IONODE, MPI_COMM_WORLD);
    if (rank == IONODE) {
        disps[0] = 0;
        for (i=1; i<size; i++) {
            disps[i] = disps[i-1] + counts[i-1];
        }
    }

    /* scatter the data */
    ierr = MPI_Scatterv(data, counts, disps, MPI_INT, mydata, myncells, 
                        MPI_INT, IONODE, MPI_COMM_WORLD);

    /* everyone has to know maxval */
    ierr = MPI_Bcast(&maxval, 1, MPI_INT, IONODE, MPI_COMM_WORLD);

    for (i=0; i<myncells; i++)
        mydata[i] = maxval-mydata[i];

    /* Gather the data */
    ierr = MPI_Gatherv(mydata, myncells, MPI_INT, data, counts, disps, 
                        MPI_INT, IONODE, MPI_COMM_WORLD);

    if (rank == IONODE) 
    {

      FW=fopen(argv[5], "w");
      fprintf(FW,"P2\n%d %d\n255\n",rows,cols);    
      for(j=0;j<cols;j++)
        for(i=0;i<rows;i++) 
       fprintf(FW,"%d ", greys[i][j]);
    }

    free(mydata);
    if (rank == IONODE) {
        free(counts);
        free(disps);
        free(&(greys[0][0]));
        free(greys);
                
    }
    fclose(FR);
    fclose(FW);
    MPI_Finalize();
    return 0;
}


```

1) I suggest you run the program with the debugger, gdb. Then it will point out exactly where it crashes.
2) Language detail: if the program gives you a segmentation fault, it's not the compilation that's a problem, but the execution.

---

### Post by arepisa on 2011-03-04
Could u explain in detail how to find the problem. This is the error when i try to run using mpirun -np 10 ./exmpi_2 2.pgm 10.pgm




[ubuntu:02995] *** Process received signal ***
[ubuntu:02995] Signal: Segmentation fault (11)
[ubuntu:02995] Signal code: Address not mapped (1)
[ubuntu:02995] Failing at address: (nil)
[ubuntu:02995] [ 0] [0x73d410]
[ubuntu:02995] [ 1] ./exmpi_2(main+0x1f6) [0x8048d2a]
[ubuntu:02995] [ 2] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x409bd6]
[ubuntu:02995] [ 3] ./exmpi_2() [0x8048aa1]
[ubuntu:02995] *** End of error message ***
--------------------------------------------------------------------------
mpirun noticed that process rank 0 with PID 2995 on node ubuntu exited on signal 11 (Segmentation fault).
[/QUOTE]

---

