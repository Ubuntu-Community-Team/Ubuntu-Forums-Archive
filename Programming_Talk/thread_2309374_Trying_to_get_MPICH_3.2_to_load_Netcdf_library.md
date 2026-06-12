---
title: "Trying to get MPICH 3.2 to load Netcdf library"
date: 2016-01-10
forum: Programming Talk
---

### Post by Chris_Laskaris on 2016-01-10
**Edit: Unfortunately, the problem is not solved, as I originally thought. I am re-opening the thread. Please ignore the first replies up to #5.**

I am using MPICH 3.2 to run a scientific simulation program which requires netcdf. The command I am using, which is given in the program's documentation, is:

```
mpirun -np 4 ./sim_program run_params
```

(run_params is a text file with options for the simulation. Basically, all the command does is tell MPICH to run the simulation program on four processors.)

Originally, this produced the following error message (one for each processor):

```
./sim_program: error while loading shared libraries: libnetcdf.so.7: cannot open shared object file: No such file or directory
./sim_program: error while loading shared libraries: libnetcdf.so.7: cannot open shared object file: No such file or directory
./sim_program: error while loading shared libraries: libnetcdf.so.7: cannot open shared object file: No such file or directory
./sim_program: error while loading shared libraries: libnetcdf.so.7: cannot open shared object file: No such file or directory
```

For some reason, mpirun does not find my netcdf libraries, which are at /opt/netcdf/4.3.3.1/lib. Using *LD_LIBRARY_PATH=/opt/netcdf/4.3.3.1/lib* before or with the mpirun command does not work. Eventually, I resorted to *ldconfig* to load netcdf. Now, I am getting a different error:

mpirun now terminates immediately, without an error message. The simulation program produces an error log, which starts with:

```
NetCDF: Unknown file format                                                    
 
NetCDF: Not a valid ID
```

So, obviously, netcdf is still not found. Maybe mpirun still does not find it, or maybe mpirun finds it but ./sim_program doesn't. I am not sure.

I have the feeling that I am missing something really easy, but I can't for the life of me figure it out. How can I run this program and make it recognise netcdf?

I'd be very grateful for any help.

---

### Post by spjackson on 2016-01-10
You could try
```

LD_LIBRARY_PATH=/opt/netcdf/4.3.3.1/lib mpirun -np 4 ./program run_params

```
or
```

export LD_LIBRARY_PATH=/opt/netcdf/4.3.3.1/lib
mpirun -np 4 ./program run_params

```
If neither of these works, you might need to re-link program or resort to ldconfig.

---

### Post by Chris_Laskaris on 2016-01-10
I solved the problem with a workaround.

I still haven't found a way to use a LD_LIBRARY_PATH option when running MPICH, but I have now simply added a new file called netcdf.conf to /etc/ld.so.conf.d, which contains the text /opt/netcdf/4.4.3.1/lib . This way, Ubuntu always looks for the netcdf libraries. It's not the most elegant solution, but it works.

---

### Post by Chris_Laskaris on 2016-01-10
@ spjackson: Thank you for your reply. I had tried the second solution (export then mpirun), but that didn't work for some reason. Maybe the first one would have worked. By now, I've just resorted to ldconfig, as you suggested.

---

### Post by Chris_Laskaris on 2016-01-11
Unfortuntately, the problem is not solved as I originally thought. I am merely getting a different error now. I am re-opening the thread and have re-written the opening post.

---

### Post by spjackson on 2016-01-12
> **Chris_Laskaris said:**
> 
For some reason, mpirun does not find my netcdf libraries, which are at /opt/netcdf/4.3.3.1/lib. Using *LD_LIBRARY_PATH=/opt/netcdf/4.3.3.1/lib* before or with the mpirun command does not work. Eventually, I resorted to *ldconfig* to load netcdf. Now, I am getting a different error:

mpirun now terminates immediately, without an error message. The simulation program produces an error log, which starts with:

```
NetCDF: Unknown file format                                                    
 
NetCDF: Not a valid ID
```

So, obviously, netcdf is still not found. Maybe mpirun still does not find it, or maybe mpirun finds it but ./sim_program doesn't. I am not sure.

I believe you are mistaken: netcdf **is** found and it is netcdf that is failing to open whatever file it is that your program is trying to open. I don't know anything about netcdf so I can't help there.

---

### Post by Chris_Laskaris on 2016-02-05
My apologies for the late reply - I forgot that I had not marked this issue as solved.

> **spjackson said:**
> I believe you are mistaken: netcdf **is** found and it is netcdf that is failing to open whatever file it is that your program is trying to open. I don't know anything about netcdf so I can't help there.

Yes, you are right, of course: MPICH did find netcdf, but could not open the necessary file because the path to that file was missing. I needed to enter the path first in a text file. That detail of how to run the program was pretty well hidden among various other instructions, so I had overlooked it.

Everything is working fine now. Thank you for your help!

---

