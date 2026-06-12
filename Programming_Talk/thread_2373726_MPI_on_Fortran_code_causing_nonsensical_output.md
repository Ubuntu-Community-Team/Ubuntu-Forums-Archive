---
title: "MPI on Fortran code causing nonsensical output"
date: 2017-10-09
forum: Programming Talk
---

### Post by thunderflash on 2017-10-09
Hey everyone, I have a Fortran code that runs some computational tasks, mainly a loop. The datasets(arrays X,Y,M_list and zeta_list) are created in Python, and then I import the data files, run the loop, write out the data.I'm trying to parallelise this code with MPI so that I can make use of many nodes/cores. I've tried two ways to parallelise a loop, one using MPI_Send/Recv, and another using MPI_Scatter/Gather. I've used for example, X and Y arrays which are 11 x 11, and 10 coordinate points(zeta_list) that the loop runs over. M_list is simply a list containing identical values, for example 1 or 0.1. 
The serial code without MPI is below : 

```
PROGRAM LensingTest1


IMPLICIT NONE 


DOUBLE PRECISION,DIMENSION(1,10)::M_list
DOUBLE PRECISION,DIMENSION(11,11)::X,Y,z_m_z_x,z_m_z_y,dist_z_m_z, alpha_x, alpha_y
DOUBLE PRECISION,DIMENSION(2,10)::zeta_list
INTEGER::i,j,t1,t2,clock_rate,clock_max




open(10,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/M_list.dat')
open(9,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/zeta_list.dat')
open(8,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/X.dat')
open(7,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/Y.dat')


read(10,*)M_list
read(9,*)zeta_list
read(8,*)X
read(7,*)Y




call system_clock ( t1, clock_rate, clock_max )
alpha_x = 0 
alpha_y = 0 


do i=1,size(zeta_list,2),1 
    z_m_z_x = X - zeta_list(1,i)
    z_m_z_y = Y - zeta_list(2,i)
    dist_z_m_z = z_m_z_x**2 + z_m_z_y**2
    alpha_x = alpha_x + (M_list(1,i)* z_m_z_x / dist_z_m_z)
    alpha_y = alpha_y + (M_list(1,i)* z_m_z_y / dist_z_m_z)
end do 


call system_clock ( t2, clock_rate, clock_max )
write ( *, * ) 'Elapsed real time = ', real ( t2 - t1 ) / real ( clock_rate ) ,'seconds'
write(*,*) alpha_x 
stop


END PROGRAM LensingTest1    



```
The one with MPI_Scatter/Gather is 

```
PROGRAM TEST_MPI



use mpi


IMPLICIT NONE 


!X and Y are coordinate grids, zeta_list contains a set of 10 random numbers in the form of (x,y)
!M_list is just a set of numbers to assign masses, they are identical values 
DOUBLE PRECISION,DIMENSION(1,10)::M_list
DOUBLE PRECISION,DIMENSION(11,11)::X,Y,z_m_z_x,z_m_z_y,dist_z_m_z,alpha_x, alpha_y, sub_alpha_x, sub_alpha_y
DOUBLE PRECISION,DIMENSION(2,10)::zeta_list
DOUBLE PRECISION,DIMENSION(2,1)::sub_zeta_list
INTEGER::i,t1,t2,clock_rate,clock_max,myid,ntasks,ierror






call MPI_INIT(ierror)
call MPI_COMM_RANK(MPI_COMM_WORLD, myid, ierror)
call MPI_COMM_SIZE(MPI_COMM_WORLD, ntasks, ierror)


!Open the input files, and read the input arrays 


if (myid == 0) then 
    open(10,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/M_list_10.dat')
    open(9,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/zeta_list_10.dat')
    open(8,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/X_10.dat')
    open(7,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/Y_10.dat')
    
    read(10,*)M_list
    read(9,*)zeta_list
    read(8,*)X
    read(7,*)Y
    !n = size(M_list,2)
    !n_per_proc = n/ntasks
    
    call system_clock ( t1, clock_rate, clock_max )


end if 
alpha_x = 0
alpha_y = 0 
sub_alpha_x = 0 
sub_alpha_y = 0 
sub_zeta_list = 0 


!Scatter the coordinates in zeta_list to each process, each coordinate is 2 elements 


if (myid == 0) then
    call MPI_Scatter(zeta_list,2,MPI_DOUBLE_PRECISION,sub_zeta_list,2,MPI_DOUBLE_PRECISION,0,MPI_COMM_WORLD)
end if 


!This is the loop that calculates the output arrays alpha_x and alpha_y
!I've created sub_zeta_list as the buffer array to hold in the coordinates for each process 


do i=1,10,1
    z_m_z_x = X - sub_zeta_list(1,i)
    z_m_z_y = Y - sub_zeta_list(2,i)
    dist_z_m_z = z_m_z_x**2 + z_m_z_y**2
    sub_alpha_x = sub_alpha_x + (M_list(1,i)* z_m_z_x / dist_z_m_z)
    sub_alpha_y = sub_alpha_y + (M_list(1,i)* z_m_z_y / dist_z_m_z)
end do


!To gather the outputs from each process into the master process
!Since sub_alpha_x and alpha_x are both 11 x 11 arrays, they contain 121 elements for output


if (myid == 0) then
    call MPI_Gather(sub_alpha_x,121,MPI_DOUBLE_PRECISION,alpha_x,121,MPI_DOUBLE_PRECISION,0,MPI_COMM_WORLD)
    call MPI_Gather(sub_alpha_y,121,MPI_DOUBLE_PRECISION,alpha_y,121,MPI_DOUBLE_PRECISION,0,MPI_COMM_WORLD)
end if 


if (myid == 0) then
    !write(*,*)sub_alpha_x
    !write(*,*)sub_zeta_list
    write(*,*)alpha_x
    call system_clock ( t2, clock_rate, clock_max )
    write ( *, * ) 'Elapsed real time = ', real ( t2 - t1 ) / real ( clock_rate ) ,'seconds'
end if 




call MPI_FINALIZE(ierror)


END PROGRAM TEST_MPI  
```

The example where I try to use MPI_Send/Recv:

```
PROGRAM TEST_MPI

use mpi 


IMPLICIT NONE 




DOUBLE PRECISION,DIMENSION(1,10)::M_list
DOUBLE PRECISION,DIMENSION(11,11)::X,Y,z_m_z_x,z_m_z_y,dist_z_m_z, alpha_x, alpha_y, real_alpha_x, real_alpha_y
DOUBLE PRECISION,DIMENSION(2,10)::zeta_list
INTEGER::i,j,t1,t2,clock_rate,clock_max,myid,ntasks,ierror,iworker
INTEGER,PARAMETER:: master=0, tag1=100,tag2=101
INTEGER,DIMENSION( MPI_STATUS_SIZE ) :: status
	


call MPI_INIT(ierror)
call mpi_comm_rank(MPI_COMM_WORLD, myid, ierror)
call mpi_comm_size(MPI_COMM_WORLD, ntasks, ierror)


if (myid == 0) then 
	open(10,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/M_list_10.dat')
	open(9,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/zeta_list_10.dat')
	open(8,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/X_10.dat')
	open(7,file='/home/amruth/Desktop/Coding/Fortran/Test_Programs/Lensing_Test/Y_10.dat')
	
	read(10,*)M_list
	read(9,*)zeta_list
	read(8,*)X
	read(7,*)Y
	
	
	call system_clock ( t1, clock_rate, clock_max )
	
	do iworker = 1, ntasks-1
		call MPI_Send(zeta_list,10,MPI_DOUBLE_PRECISION,iworker,tag1,MPI_COMM_WORLD,ierror)
	end do 
else
	call MPI_Recv(zeta_list,10,MPI_DOUBLE_PRECISION,master,tag1,MPI_COMM_WORLD,status,ierror)
end if 


alpha_x = 0 
alpha_y = 0
real_alpha_x = 0 
real_alpha_y = 0 


do i= myid+1,20,ntasks
	z_m_z_x = X - zeta_list(1,i)
	z_m_z_y = Y - zeta_list(2,i)
	dist_z_m_z = z_m_z_x**2 + z_m_z_y**2
	alpha_x = alpha_x + (M_list(1,i)* z_m_z_x / dist_z_m_z)
    alpha_y = alpha_y + (M_list(1,i)* z_m_z_y / dist_z_m_z)
end do 


if (myid /= 0 ) then
	call MPI_Send(alpha_x,121,MPI_DOUBLE_PRECISION,master,tag2,MPI_COMM_WORLD,ierror)
	call MPI_Send(alpha_y,121,MPI_DOUBLE_PRECISION,master,tag2,MPI_COMM_WORLD,ierror)
else
	real_alpha_x = alpha_x
	real_alpha_y = alpha_y 
	do iworker=1,ntasks-1
	    call MPI_Recv(alpha_x,121,MPI_DOUBLE_PRECISION,iworker,tag2,MPI_COMM_WORLD,status,ierror)
	    real_alpha_x = real_alpha_x + alpha_x
	    call MPI_Recv(alpha_y,121,MPI_DOUBLE_PRECISION,iworker,tag2,MPI_COMM_WORLD,status,ierror)
	    real_alpha_y = real_alpha_y + alpha_y
	end do 
end if 


if (myid == 0) then
	write(*,*)real_alpha_x
	write(*,*)size(M_list,2)
	call system_clock ( t2, clock_rate, clock_max )
	write(*,*) 'Elapsed real time = ', real ( t2 - t1 ) / real ( clock_rate ) ,'seconds'
end if








call MPI_FINALIZE(ierror)


END PROGRAM TEST_MPI  
```

When I run the codes using mpirun -np 1 a.out, they work fine. However, when I try to use more processes, like mpirun -np 2 a.out, they start printing out results like NaN and such. I have a feeling the error lies in the way I distribute the data chunks from the input arrays, or perhaps in the way I define my loop bounds. Would appreciate any help!!!

---

