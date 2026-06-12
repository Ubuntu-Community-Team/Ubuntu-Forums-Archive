---
title: "Segmentation faults on parallel program using Open MPI"
date: 2011-03-09
forum: Programming Talk
---

### Post by arepisa on 2011-03-09
I need to use Open MPI to distribute 2d-array in the PGM file among 10  working computers. Then I need to manipulate each value of the array to  get a negative image (255-i) and then print the output back. I'm  thinking of using mpi_scatterv and mpi_gatherv to distribute the data. 
I can compile my program but it got segmentation fault. I ran but nothing happen
```

mpirun -np 10 ./exmpi_2 balloons.pgm output.pgm

```The result is 
```

[ubuntu:04803] *** Process received signal ***
[ubuntu:04803] Signal: Segmentation fault (11)
[ubuntu:04803] Signal code: Address not mapped (1)
[ubuntu:04803] Failing at address: 0x7548d0c
[ubuntu:04803] [ 0] [0x86b410]
[ubuntu:04803] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x186b00]
[ubuntu:04803] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04803] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x141bd6]
[ubuntu:04803] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04803] *** End of error message ***
--------------------------------------------------------------------------
mpirun noticed that process rank 1 with PID 4803 on node ubuntu exited on signal 11 (Segmentation fault).
--------------------------------------------------------------------------

```Then i try run with valgrind to debug the program and the output.pgm is generated
```

valgrind mpirun -np 10 ./exmpi_2 balloons.pgm output.pgm
```The result is
```
==4632== Memcheck, a memory error detector
==4632== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==4632== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==4632== Command: mpirun -np 10 ./exmpi_2 2.pgm 10.pgm
==4632== 
==4632== Syscall param sched_setaffinity(mask) points to unaddressable byte(s)
==4632==    at 0x4215D37: syscall (syscall.S:31)
==4632==    by 0x402B335: opal_paffinity_linux_plpa_api_probe_init (plpa_api_probe.c:56)
==4632==    by 0x402B7CC: opal_paffinity_linux_plpa_init (plpa_runtime.c:37)
==4632==    by 0x402B93C: opal_paffinity_linux_plpa_have_topology_information (plpa_map.c:494)
==4632==    by 0x402B180: linux_module_init (paffinity_linux_module.c:119)
==4632==    by 0x40BE2C3: opal_paffinity_base_select (paffinity_base_select.c:64)
==4632==    by 0x40927AC: opal_init (opal_init.c:295)
==4632==    by 0x4046767: orte_init (orte_init.c:76)
==4632==    by 0x804A82E: orterun (orterun.c:540)
==4632==    by 0x804A3EE: main (main.c:13)
==4632==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==4632== 
[ubuntu:04638] *** Process received signal ***
[ubuntu:04639] *** Process received signal ***
[ubuntu:04639] Signal: Segmentation fault (11)
[ubuntu:04639] Signal code: Address not mapped (1)
[ubuntu:04639] Failing at address: 0x7548d0c
[ubuntu:04639] [ 0] [0xc50410]
[ubuntu:04639] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0xde4b00]
[ubuntu:04639] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04639] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xd9fbd6]
[ubuntu:04639] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04639] *** End of error message ***
[ubuntu:04640] *** Process received signal ***
[ubuntu:04640] Signal: Segmentation fault (11)
[ubuntu:04640] Signal code: Address not mapped (1)
[ubuntu:04640] Failing at address: 0x7548d0c
[ubuntu:04640] [ 0] [0xdad410]
[ubuntu:04640] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0xe76b00]
[ubuntu:04640] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04640] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xe31bd6]
[ubuntu:04640] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04640] *** End of error message ***
[ubuntu:04641] *** Process received signal ***
[ubuntu:04641] Signal: Segmentation fault (11)
[ubuntu:04641] Signal code: Address not mapped (1)
[ubuntu:04641] Failing at address: 0x7548d0c
[ubuntu:04641] [ 0] [0xe97410]
[ubuntu:04641] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x1e8b00]
[ubuntu:04641] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04641] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1a3bd6]
[ubuntu:04641] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04641] *** End of error message ***
[ubuntu:04642] *** Process received signal ***
[ubuntu:04642] Signal: Segmentation fault (11)
[ubuntu:04642] Signal code: Address not mapped (1)
[ubuntu:04642] Failing at address: 0x7548d0c
[ubuntu:04642] [ 0] [0x92d410]
[ubuntu:04642] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x216b00]
[ubuntu:04642] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04642] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1d1bd6]
[ubuntu:04642] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04642] *** End of error message ***
[ubuntu:04643] *** Process received signal ***
[ubuntu:04643] Signal: Segmentation fault (11)
[ubuntu:04643] Signal code: Address not mapped (1)
[ubuntu:04643] Failing at address: 0x7548d0c
[ubuntu:04643] [ 0] [0x8f4410]
[ubuntu:04643] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x16bb00]
[ubuntu:04643] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04643] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x126bd6]
[ubuntu:04643] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04643] *** End of error message ***
[ubuntu:04638] Signal: Segmentation fault (11)
[ubuntu:04638] Signal code: Address not mapped (1)
[ubuntu:04638] Failing at address: 0x7548d0c
[ubuntu:04638] [ 0] [0x4f6410]
[ubuntu:04638] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x222b00]
[ubuntu:04638] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04638] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1ddbd6]
[ubuntu:04638] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04638] *** End of error message ***
[ubuntu:04644] *** Process received signal ***
[ubuntu:04644] Signal: Segmentation fault (11)
[ubuntu:04644] Signal code: Address not mapped (1)
[ubuntu:04644] Failing at address: 0x7548d0c
[ubuntu:04644] [ 0] [0x61f410]
[ubuntu:04644] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x1a3b00]
[ubuntu:04644] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04644] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x15ebd6]
[ubuntu:04644] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04644] *** End of error message ***
[ubuntu:04645] *** Process received signal ***
[ubuntu:04645] Signal: Segmentation fault (11)
[ubuntu:04645] Signal code: Address not mapped (1)
[ubuntu:04645] Failing at address: 0x7548d0c
[ubuntu:04645] [ 0] [0x7a3410]
[ubuntu:04645] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x1d5b00]
[ubuntu:04645] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04645] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x190bd6]
[ubuntu:04645] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04645] *** End of error message ***
[ubuntu:04647] *** Process received signal ***
[ubuntu:04647] Signal: Segmentation fault (11)
[ubuntu:04647] Signal code: Address not mapped (1)
[ubuntu:04647] Failing at address: 0x7548d0c
[ubuntu:04647] [ 0] [0xf54410]
[ubuntu:04647] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x2bab00]
[ubuntu:04647] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04647] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x275bd6]
[ubuntu:04647] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04647] *** End of error message ***
--------------------------------------------------------------------------
mpirun noticed that process rank 2 with PID 4639 on node ubuntu exited on signal 11 (Segmentation fault).
--------------------------------------------------------------------------
6 total processes killed (some possibly by mpirun during cleanup)
==4632== 
==4632== HEAP SUMMARY:
==4632==     in use at exit: 158,751 bytes in 1,635 blocks
==4632==   total heap usage: 10,443 allocs, 8,808 frees, 15,854,537 bytes allocated
==4632== 
==4632== LEAK SUMMARY:
==4632==    definitely lost: 81,655 bytes in 112 blocks
==4632==    indirectly lost: 5,108 bytes in 91 blocks
==4632==      possibly lost: 1,043 bytes in 17 blocks
==4632==    still reachable: 70,945 bytes in 1,415 blocks
==4632==         suppressed: 0 bytes in 0 blocks
==4632== Rerun with --leak-check=full to see details of leaked memory
==4632== 
==4632== For counts of detected and suppressed errors, rerun with: -v
==4632== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 96 from 9)

```Could someone help me to solve this problem. This is my source code
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "mpi.h"
#include <syscall.h>

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
    ierr = MPI_Comm_size(MPI_COMM_WORLD, &size);
    if (ierr) {
        fprintf(stderr,"Catastrophic MPI problem; exiting\n");
        MPI_Abort(MPI_COMM_WORLD,1);
    }

    if (rank == IONODE) {
        //if (read_pgm(argv[1], &greys, &rows, &cols, &maxval)) {
         //   fprintf(stderr,"Could not read file; exiting\n");
         //   MPI_Abort(MPI_COMM_WORLD,2);
         
         rows=SIZE_X;
         cols=SIZE_Y;
         maxval=255;
         FR=fopen(argv[1], "r+");
        
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
    ierr = MPI_Scatterv(data, counts, disps, MPI_INT, mydata, myncells, MPI_INT, IONODE, MPI_COMM_WORLD);

    /* everyone has to know maxval */
    ierr = MPI_Bcast(&maxval, 1, MPI_INT, IONODE, MPI_COMM_WORLD);

    for (i=0; i<myncells; i++)
        mydata[i] = maxval-mydata[i];

    /* Gather the data */
    ierr = MPI_Gatherv(mydata, myncells, MPI_INT, data, counts, disps, MPI_INT, IONODE, MPI_COMM_WORLD);

    if (rank == IONODE) 
    {
//      write_pgm(argv[2], greys, rows, cols, maxval);
      FW=fopen(argv[2], "w");
      fprintf(FW,"P2\n%d %d\n255\n",rows,cols);    
      for(j=0;j<cols;j++)
        for(i=0;i<rows;i++) 
       fprintf(FW,"%d ", greys[i][j]);
    }

    free(mydata);
    if (rank == IONODE) {
        free(counts);
        free(disps);
        //free(&(greys[0][0]));
        //free(greys);
                
    }
    fclose(FR);
    fclose(FW);
    MPI_Finalize();
    return 0;
}


```This is the input image [HTML]http://orion.math.iastate.edu/burkardt/data/pgm/balloons.pgm[/HTML]TQ for your help.

---

### Post by Arndt on 2011-03-09
> **arepisa said:**
> I need to use Open MPI to distribute 2d-array in the PGM file among 10  working computers. Then I need to manipulate each value of the array to  get a negative image (255-i) and then print the output back. I'm  thinking of using mpi_scatterv and mpi_gatherv to distribute the data. 
I can compile my program but it got segmentation fault. I ran but nothing happen
```

mpirun -np 10 ./exmpi_2 balloons.pgm output.pgm

```The result is 
```

[ubuntu:04803] *** Process received signal ***
[ubuntu:04803] Signal: Segmentation fault (11)
[ubuntu:04803] Signal code: Address not mapped (1)
[ubuntu:04803] Failing at address: 0x7548d0c
[ubuntu:04803] [ 0] [0x86b410]
[ubuntu:04803] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x186b00]
[ubuntu:04803] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04803] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x141bd6]
[ubuntu:04803] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04803] *** End of error message ***
--------------------------------------------------------------------------
mpirun noticed that process rank 1 with PID 4803 on node ubuntu exited on signal 11 (Segmentation fault).
--------------------------------------------------------------------------

```Then i try run with valgrind to debug the program and the output.pgm is generated
```

valgrind mpirun -np 10 ./exmpi_2 balloons.pgm output.pgm
```The result is
```
==4632== Memcheck, a memory error detector
==4632== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==4632== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==4632== Command: mpirun -np 10 ./exmpi_2 2.pgm 10.pgm
==4632== 
==4632== Syscall param sched_setaffinity(mask) points to unaddressable byte(s)
==4632==    at 0x4215D37: syscall (syscall.S:31)
==4632==    by 0x402B335: opal_paffinity_linux_plpa_api_probe_init (plpa_api_probe.c:56)
==4632==    by 0x402B7CC: opal_paffinity_linux_plpa_init (plpa_runtime.c:37)
==4632==    by 0x402B93C: opal_paffinity_linux_plpa_have_topology_information (plpa_map.c:494)
==4632==    by 0x402B180: linux_module_init (paffinity_linux_module.c:119)
==4632==    by 0x40BE2C3: opal_paffinity_base_select (paffinity_base_select.c:64)
==4632==    by 0x40927AC: opal_init (opal_init.c:295)
==4632==    by 0x4046767: orte_init (orte_init.c:76)
==4632==    by 0x804A82E: orterun (orterun.c:540)
==4632==    by 0x804A3EE: main (main.c:13)
==4632==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==4632== 
[ubuntu:04638] *** Process received signal ***
[ubuntu:04639] *** Process received signal ***
[ubuntu:04639] Signal: Segmentation fault (11)
[ubuntu:04639] Signal code: Address not mapped (1)
[ubuntu:04639] Failing at address: 0x7548d0c
[ubuntu:04639] [ 0] [0xc50410]
[ubuntu:04639] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0xde4b00]
[ubuntu:04639] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04639] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xd9fbd6]
[ubuntu:04639] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04639] *** End of error message ***
[ubuntu:04640] *** Process received signal ***
[ubuntu:04640] Signal: Segmentation fault (11)
[ubuntu:04640] Signal code: Address not mapped (1)
[ubuntu:04640] Failing at address: 0x7548d0c
[ubuntu:04640] [ 0] [0xdad410]
[ubuntu:04640] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0xe76b00]
[ubuntu:04640] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04640] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xe31bd6]
[ubuntu:04640] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04640] *** End of error message ***
[ubuntu:04641] *** Process received signal ***
[ubuntu:04641] Signal: Segmentation fault (11)
[ubuntu:04641] Signal code: Address not mapped (1)
[ubuntu:04641] Failing at address: 0x7548d0c
[ubuntu:04641] [ 0] [0xe97410]
[ubuntu:04641] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x1e8b00]
[ubuntu:04641] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04641] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1a3bd6]
[ubuntu:04641] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04641] *** End of error message ***
[ubuntu:04642] *** Process received signal ***
[ubuntu:04642] Signal: Segmentation fault (11)
[ubuntu:04642] Signal code: Address not mapped (1)
[ubuntu:04642] Failing at address: 0x7548d0c
[ubuntu:04642] [ 0] [0x92d410]
[ubuntu:04642] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x216b00]
[ubuntu:04642] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04642] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1d1bd6]
[ubuntu:04642] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04642] *** End of error message ***
[ubuntu:04643] *** Process received signal ***
[ubuntu:04643] Signal: Segmentation fault (11)
[ubuntu:04643] Signal code: Address not mapped (1)
[ubuntu:04643] Failing at address: 0x7548d0c
[ubuntu:04643] [ 0] [0x8f4410]
[ubuntu:04643] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x16bb00]
[ubuntu:04643] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04643] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x126bd6]
[ubuntu:04643] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04643] *** End of error message ***
[ubuntu:04638] Signal: Segmentation fault (11)
[ubuntu:04638] Signal code: Address not mapped (1)
[ubuntu:04638] Failing at address: 0x7548d0c
[ubuntu:04638] [ 0] [0x4f6410]
[ubuntu:04638] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x222b00]
[ubuntu:04638] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04638] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1ddbd6]
[ubuntu:04638] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04638] *** End of error message ***
[ubuntu:04644] *** Process received signal ***
[ubuntu:04644] Signal: Segmentation fault (11)
[ubuntu:04644] Signal code: Address not mapped (1)
[ubuntu:04644] Failing at address: 0x7548d0c
[ubuntu:04644] [ 0] [0x61f410]
[ubuntu:04644] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x1a3b00]
[ubuntu:04644] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04644] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x15ebd6]
[ubuntu:04644] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04644] *** End of error message ***
[ubuntu:04645] *** Process received signal ***
[ubuntu:04645] Signal: Segmentation fault (11)
[ubuntu:04645] Signal code: Address not mapped (1)
[ubuntu:04645] Failing at address: 0x7548d0c
[ubuntu:04645] [ 0] [0x7a3410]
[ubuntu:04645] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x1d5b00]
[ubuntu:04645] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04645] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x190bd6]
[ubuntu:04645] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04645] *** End of error message ***
[ubuntu:04647] *** Process received signal ***
[ubuntu:04647] Signal: Segmentation fault (11)
[ubuntu:04647] Signal code: Address not mapped (1)
[ubuntu:04647] Failing at address: 0x7548d0c
[ubuntu:04647] [ 0] [0xf54410]
[ubuntu:04647] [ 1] /lib/tls/i686/cmov/libc.so.6(fclose+0x1a0) [0x2bab00]
[ubuntu:04647] [ 2] ./exmpi_2(main+0x78e) [0x80492c2]
[ubuntu:04647] [ 3] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x275bd6]
[ubuntu:04647] [ 4] ./exmpi_2() [0x8048aa1]
[ubuntu:04647] *** End of error message ***
--------------------------------------------------------------------------
mpirun noticed that process rank 2 with PID 4639 on node ubuntu exited on signal 11 (Segmentation fault).
--------------------------------------------------------------------------
6 total processes killed (some possibly by mpirun during cleanup)
==4632== 
==4632== HEAP SUMMARY:
==4632==     in use at exit: 158,751 bytes in 1,635 blocks
==4632==   total heap usage: 10,443 allocs, 8,808 frees, 15,854,537 bytes allocated
==4632== 
==4632== LEAK SUMMARY:
==4632==    definitely lost: 81,655 bytes in 112 blocks
==4632==    indirectly lost: 5,108 bytes in 91 blocks
==4632==      possibly lost: 1,043 bytes in 17 blocks
==4632==    still reachable: 70,945 bytes in 1,415 blocks
==4632==         suppressed: 0 bytes in 0 blocks
==4632== Rerun with --leak-check=full to see details of leaked memory
==4632== 
==4632== For counts of detected and suppressed errors, rerun with: -v
==4632== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 96 from 9)

```Could someone help me to solve this problem. This is my source code
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "mpi.h"
#include <syscall.h>

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
    ierr = MPI_Comm_size(MPI_COMM_WORLD, &size);
    if (ierr) {
        fprintf(stderr,"Catastrophic MPI problem; exiting\n");
        MPI_Abort(MPI_COMM_WORLD,1);
    }

    if (rank == IONODE) {
        //if (read_pgm(argv[1], &greys, &rows, &cols, &maxval)) {
         //   fprintf(stderr,"Could not read file; exiting\n");
         //   MPI_Abort(MPI_COMM_WORLD,2);
         
         rows=SIZE_X;
         cols=SIZE_Y;
         maxval=255;
         FR=fopen(argv[1], "r+");
        
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
    ierr = MPI_Scatterv(data, counts, disps, MPI_INT, mydata, myncells, MPI_INT, IONODE, MPI_COMM_WORLD);

    /* everyone has to know maxval */
    ierr = MPI_Bcast(&maxval, 1, MPI_INT, IONODE, MPI_COMM_WORLD);

    for (i=0; i<myncells; i++)
        mydata[i] = maxval-mydata[i];

    /* Gather the data */
    ierr = MPI_Gatherv(mydata, myncells, MPI_INT, data, counts, disps, MPI_INT, IONODE, MPI_COMM_WORLD);

    if (rank == IONODE) 
    {
//      write_pgm(argv[2], greys, rows, cols, maxval);
      FW=fopen(argv[2], "w");
      fprintf(FW,"P2\n%d %d\n255\n",rows,cols);    
      for(j=0;j<cols;j++)
        for(i=0;i<rows;i++) 
       fprintf(FW,"%d ", greys[i][j]);
    }

    free(mydata);
    if (rank == IONODE) {
        free(counts);
        free(disps);
        //free(&(greys[0][0]));
        //free(greys);
                
    }
    fclose(FR);
    fclose(FW);
    MPI_Finalize();
    return 0;
}


```This is the input image [HTML]http://orion.math.iastate.edu/burkardt/data/pgm/balloons.pgm[/HTML]TQ for your help.

The stack backtrace seems to be saying that the system call sched_setaffinity got a mask argument which pointed at undefined memory, and the question is where that parameter comes from. All the way from the main program? I can't tell, because the backtrace says that the call is made on line 13 in main.c, but on line 13 in your code, it's just the first line of the main function, so something is wrong.

Have you tried a debugger?

---

### Post by Arndt on 2011-03-09
I couldn't help myself, so I fetched the source code (version 1.4.3) of MPI and looked at it. The code actually calling sched_setaffinity (in plpa_api_probe.c) seems very relevant. It says:

```
#if PLPA_WANT_VALGRIND_SUPPORT
            /* Lie to Valgrind and say that this memory is addressible
               so that we don't get a false positive here -- we *know*
               that 0 is unaddressible; that's the whole point of this
               test (to see what error NR_sched_set_affinity will
               return).  So let's not see a warning from Valgrind from
               something that we know is wrong.  :-) */
            VALGRIND_MAKE_MEM_DEFINED(0, len);
#endif
            rc = syscall(__NR_sched_setaffinity, 0, tmp, NULL);
```

But I'm not sure what they are doing if the behaviour of the system call is to give a segmentation fault. Maybe you had better ask on the MPI support list, if there is one.

---

### Post by talonmies on 2011-03-09
You have two fclose() calls that will fail on any process other than the IONODE because the FILE handles will contain uninitialized values and no files were ever opened.

The actual MPI looks OK to my eyes.

---

### Post by Arndt on 2011-03-09
> **talonmies said:**
> You have two fclose() calls that will fail on any process other than the IONODE because the FILE handles will contain uninitialized values and no files were ever opened.

The actual MPI looks OK to my eyes.

Then the only thing wrong with valgrind is that it was not fooled into anything, but reported the sched_setaffinity call. Perhaps someone answered "no" when asked for valgrind support during configuration.

The other backtraces also mention fclose, so that is most likely the actual cause of the problem.

---

### Post by arepisa on 2011-03-09
I deleted the  two fclose() and my program works perfectly. Thanks for your help. It helps me a lot. Is there any command in mpi that can calculate the execution real time of the program?

---

### Post by talonmies on 2011-03-10
The fclose calls shouldn't be deleted, they should be made conditional so that only the process that opened tries to close them.

There is [MPI_Wtime]("http://www.mcs.anl.gov/research/projects/mpi/www/www3/MPI_Wtime.html") for wall clock timing against the local clock of any given process.

---

