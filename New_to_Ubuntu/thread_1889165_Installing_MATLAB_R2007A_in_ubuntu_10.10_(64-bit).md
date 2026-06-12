---
title: "Installing MATLAB R2007A in ubuntu 10.10 (64-bit)"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by joga24 on 2011-11-30
In short, after I install this program from disc, the following text shows up in the terminal:

```
Installation 100% complete.


The MATLAB installer is finished.  This installation needs to be
activated prior to use.  The activation application will 
be launched now.
joga@joga:~$ ---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /home/joga/MATLAB/sys/java/jre/glnxa64/jre does not exist.
---------------------------------------------------------------------------

```This is a problem, because it is looking for
```
/home/joga/MATLAB/sys/java/jre/glnxa64/jre
```, but that directory does not exist.

The directory that was created during installation is 
```
/home/joga/MATLAB/sys/java/jre/glnx86/jre1.5.0
```Is there any way I can get it to go to the correct directory? Is it worth the fight, or should I relent and install it on Windows?

---

### Post by beew on 2011-11-30
Can you just create a symlink?


```
sudo ln -s /home/joga/MATLAB/sys/java/jre/glnx86/jre1.5.0  /home/joga/MATLAB/sys/java/jre/glnxa64/jre
```

---

