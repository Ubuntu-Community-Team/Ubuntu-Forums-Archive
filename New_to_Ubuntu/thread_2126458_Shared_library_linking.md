---
title: "Shared library linking"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by mathausj on 2013-03-17
Dear all, 
I am trying to run software (it's computational chemistry..) that someone else has compiled on the same supercomputer, but I am experiencing difficulties with shared libraries and as a beginner I've gotten clueless by now:

I got the user's binary and dynamically linked libs via cp -a so with links, but I keep getting
$ ldd ./bin/mpiexec
        linux-vdso.so.1 =>  (0x00007fff12a74000)
        libopen-rte.so.4 => not found
or 
$ ldd /storage/home/his-username/bin/mpiexec
        linux-vdso.so.1 =>  (0x00007fff2cdff000)
        libopen-rte.so.4 => not found


while he has at the same time
his-account$ ldd /home/his-username/storage/bin/mpiexec
        linux-vdso.so.1 =>  (0x00007fff57d33000)
        libopen-rte.so.4 => /home/his-username/CP2K/lib/libopen-rte.so.4 (0x00007fdb28ffd000)

So the software obviously didn't run because of this


I changed my script for PBS so that I added the red line
...
echo 'export LD_LIBRARY_PATH=/storage/home/$USER/lib' >> $go
echo 'export PATH=/storage/home/$USER/bin:'$PATH >> $go
echo 'echo "env:"; env' >> $go
echo 'echo "nodes:"; cat $PBS_NODEFILE; echo libs:; ls /storage/home/$USER/lib; echo bin:; ls /storage/home/$USER/bin' >> $go
[COLOR=#ff0000]echo 'export LD_LIBRARY_PATH=/storage/home/$USER/lib/libopen-rte.so.4' >> $go[/COLOR]
echo /storage/home/$USER/bin/'mpiexec --hostfile $PBS_NODEFILE -x LD_LIBRARY_PATH='$LD_LIBRARY_PATH' -x PATH='$PATH' cp2k.popt '$base'.in > '$base'.log 2>&1' >> $go
...


but in the logfile I keep getting
/storage/home/mathausj/bin/mpiexec: error while loading shared libraries: libopen-rte.so.4: cannot open shared object file: No such file or directory




though




$ ls lib
total 15936
-rwxr-xr-x 1 mathausj meta    20323 2013-03-14 09:59 libmpi_f90.so.3
-rwxr-xr-x 1 mathausj meta  2002819 2013-03-14 09:59 libmpi_f77.so.1
-rwxr-xr-x 1 mathausj meta 10282011 2013-03-14 09:59 libmpi.so.1
-rwxr-xr-x 1 mathausj meta  4006084 2013-03-14 16:52 libopen-rte.so.4


I also get stdout where all the other commands from PBS script seem to work, stderr is empty. 
The user who compiled it is not experiencing any difficulties with running the programme.

Please, could somebody help me with this?
Thanks

---

