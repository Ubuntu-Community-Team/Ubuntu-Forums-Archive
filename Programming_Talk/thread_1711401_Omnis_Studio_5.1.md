---
title: "Omnis Studio 5.1"
date: 2011-03-21
forum: Programming Talk
---

### Post by johnaaronrose on 2011-03-21
I'm trying to install Omnis Studio 5.1 under Ubuntu 10.04. I get "Cannot initialize: Error creating file Omnis.cfg". Any ideas?

PS Only thing that I can think of is that LD_LIBRARY_PATH is not used  any longer in 10.04 - procedure is to now create in /etc/ld.so.conf.d a  .conf file containing a path reference to the os51 directory (i.e. where  Omnis Studio is installed). Running sudo ldconfig & sudo ldconfig  --verbose shows that the Omnis Studio files have been 'picked up'.  Running ./omset is successful and creates the omnisI386 shell script.  This shell script contains:
#!/bin/sh
LD_LIBRARY_PATH=/opt/OmnisStudio/os51:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
/opt/OmnisStudio/os51/omnis $1 $2 $3 $4 $5 $6 $7 $8

However, echo $LD_LIBRARY_PATH and printenv LD_LIBRARY_PATH both show nothing.

I've tried executing (in terminal) /opt/OmnisStudio/os51/omnis but that gives 
"/opt/OmnisStudio/os51/omnis: error while loading shared libraries:  omnisxi.so: cannot open shared object file: No such file or directory"
However, omnisxi.so does exist in /opt/OmnisStudio/os51/.

In response to ikt on closed thread,
I've followed that guide i.e. [http://www.linuxuser.co.uk/tutorials...-omnis-studio/]("http://www.linuxuser.co.uk/tutorials/get-started-with-omnis-studio/") (except for using /opt rather than /usr/local). I haven't done the chown command but should that make a difference? Is this guide OK? I've also looked at [ftp://ftp.omnis.net/Studio42/Install.txt](ftp://ftp.omnis.net/Studio42/Install.txt) which talks about the LD_LIBRARY_PATH environment variable.

I've tried the omnisI386 script again and this time it setup the LD_LIBRARY_PATH env variable and started omnis with a moans about 2 icon files being old version and wanting a serial number (which TigerLogic have not yet provided). I started the tutorial and was following the steps until I couldn't see both the tutorial text and execute the steps in omnis due to omnis 'locking' its execution. So I saved the .lbs and exited omnis. When I restarted omnis, it refused to load the .lbs. I think that I'll reinstall omnis. Should I wait for TigerLogic to supply the serial number before trying again?

---

