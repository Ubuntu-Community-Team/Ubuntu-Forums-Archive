---
title: "Ubuntu Login Loop and LibGL error"
date: 2015-07-25
forum: New to Ubuntu
---

### Post by akshay18 on 2015-07-25
Hi, 

After installing Octave and its dependencies on Ubuntu, I rebooted my system. Upon reboot it said that it could not configure the drivers. So I installed the nvidia 346.16 driver, as my Graphics card is a GT 755M. Upon rebooting again, I was able to get to the graphical login screen. However, after I enter the correct credentials the screen goes black and again the login screen pops up. I have tried the following stuff to take care of this login loop problem: 

1. ls -lah. And then chown username:username .Xuathority. 
2. ld -ld /tmp. It said drwxrwxrwt, which is what it should be. 
3. I even checked ~/.xsessions-error. There does not seem to be an issue with .profile. 
4. I also tried to delete the .Xuathority, and reboot but to no avail. 
5. I then did reinstall of lightdm, again to no avail. 

I have tried these methods, but no positive results. However in ~/.xsessions-error I get these error messages: 

libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

Hence, Kindly help me out, as I have run out of ideas and solutions. 

I really appreciate all the help. 

Thanks!

---

### Post by dino99 on 2015-07-25
use the ppa proposed with the link below (better to first purge the previous octave installation)

[http://wiki.octave.org/Octave_for_Debian_systems](http://wiki.octave.org/Octave_for_Debian_systems)

---

### Post by akshay18 on 2015-07-26
So, 

when I try and do a purge on octave it says that there is no package such as octave. Then I listed all the packages installed using : 

dpkg --get-selections | grep -v deinstall
and I couldn't find it there. I installed octave using the .tar.gz file that I downloaded off the web. The octave  version is 4.0.0. 

I don't know if it is octave that is causing the problem now, as I am stuck in the login loop. I could get to the Graphical login page. But then its stuck in a login loop. I am thinking about reinstalling ubuntu now, as it is taking too much time. 

Kindly let me know if anything else can be done. 

Thanks.

---

