---
title: "Unable to launch Firestorm"
date: 2014-03-27
forum: New to Ubuntu
---

### Post by maggie3 on 2014-03-27
I am having trouble launching Firestorm for Linix.  I am running Ubuntu 13.10, and I have run all the updates.  I downloaded Firestorm 64-bit, and followed the instructions below to "run" it:

3. INSTALLING & RUNNING
-=-=-=-=-=-=-=-=-=-=-=-
The Firestorm Linux client can entirely run from the directory you have
unpacked it into - no installation step is required.  If you wish to
perform a separate installation step anyway, you may run './install.sh'

Run './firestorm' from the installation directory to start Firestorm.

I downloaded it, and extracted it to a folder named "Firestorm" on my desktop.  I tried to run it in terminal following the instructions, and the results are posted below - 

---------------------------------------------
maggie@Pavilion-dv7:~/Desktop/Firestorm$ sudo ./firestorm
[sudo] password for maggie: 
64-bit Linux detected.
Running from /home/maggie/Desktop/Firestorm
./firestorm: line 99: ./etc/register_hopprotocol.sh: No such file or directory
./firestorm: line 100: ./etc/register_secondlifeprotocol.sh: Permission denied
./firestorm: line 160: bin/do-not-directly-run-firestorm-bin: Permission denied
*** Bad shutdown ($LL_RUN_ERR). ***

You are running the Firestorm Viewer on a x86_64 platform.  The
most common problems when launching the Viewer (particularly
'bin/do-not-directly-run-firestorm-bin: not found' and 'error while
loading shared libraries') may be solved by installing your Linux
distribution's 32-bit compatibility packages.
For example, on Ubuntu and other Debian-based Linuxes you might run:
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
maggie@Pavilion-dv7:~/Desktop/Firestorm$ 

-----------------------------

I searched for a 32-bit compatibilty package for Ubuntu 13.10, and I read that it one is not necessary with 13.10.   I tried installing ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl, and found that some of them were not found, and some had substitutes.

As a newbie to Ubuntu and Linix, I find the whole issue rather confusing.  Can you offer any advice?

Thanks

---

### Post by sandyd on 2014-04-03
Please do not post multiple threads on the same topic as it dilutes community effort.

Thanks.

Original Thread -> [http://ubuntuforums.org/showthread.php?t=2214755](http://ubuntuforums.org/showthread.php?t=2214755)

---

