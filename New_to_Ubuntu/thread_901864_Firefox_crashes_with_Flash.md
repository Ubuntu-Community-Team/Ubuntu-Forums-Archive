---
title: "Firefox crashes with Flash"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by walawa on 2008-08-26
Hi,
I have Ubuntu 8.04 and the latest version of Firefox. When I visit some sites with flash content Firefox tends to crash. Firefox crashes every time I go onto Imeem's main page and occasionally ends up crashing when I switch videos through the sidebar on YouTube. The same thing happens on Songbird's browser. I've tried uninstalling the flashplugin-nonfree package and downloading and installing flash from Adobe. DefaultDepth was already set to 24 in xorg.conf. 

Should I try installing Gnash? , or is there something else that might work?

---

### Post by Crafty Kisses on 2008-08-26
When Firefox is open run the command > top, and post the results here.

---

### Post by sharks on 2008-08-26
open firefox through terminal using command:
firefox
and when it crashes post the error reports found in terminal

---

### Post by walawa on 2008-08-26
top: 

top - 20:34:53 up  9:26,  2 users,  load average: 0.16, 0.18, 0.11
Tasks: 153 total,   2 running, 150 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.3%us,  0.3%sy,  0.0%ni, 92.4%id,  5.8%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   2074592k total,  1233484k used,   841108k free,    46440k buffers
Swap:  6072528k total,    39564k used,  6032964k free,   790900k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
15465 tristan   20   0  215m  81m  24m R    2  4.0   0:06.82 firefox            
14643 root      20   0 63736  31m  11m S    1  1.6   0:21.48 Xorg               
14868 tristan   20   0 55636  31m   9m S    1  1.6   0:10.50 compiz.real        
14930 tristan   20   0 36180  19m  11m S    1  1.0   0:04.24 python             
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.48 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:03.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
   15 root      15  -5     0    0    0 S    0  0.0   0:00.28 events/0           
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   56 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/0          
   62 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   63 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  189 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod            
  239 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
  240 root      20   0     0    0    0 S    0  0.0   0:00.70 pdflush

---

### Post by walawa on 2008-08-26
Here's the error on Imeem:

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/bin/firefox: line 4: 15521 Segmentation fault      /usr/bin/firefox.org $1 $2 $3 $4 $5 $6 $7 $8 $9

I get the exact same thing when youtube crashes firefox.

I guess the 'segmentation fault' is the culprit?

Thanks for the quick replies.

---

### Post by wiseguyxp on 2008-08-26
This fixed this issue for me:

[http://kemal.bioeng-network.org/2008/06/08/how-to-get-rid-of-annoying-firefox-crashes-in-ubuntu-hardy-flashplugin-nonfree/](http://kemal.bioeng-network.org/2008/06/08/how-to-get-rid-of-annoying-firefox-crashes-in-ubuntu-hardy-flashplugin-nonfree/)

---

### Post by Rome.konig on 2008-08-26
nice... i had this same problem. w00T!

---

### Post by walawa on 2008-08-27
Thanks, YouTube stopped crashing. Imeem still does but if I find a fix I'll post it here.

---

### Post by Bloch on 2008-08-27
Flash for linux is buggy. Get used to it.

[http://linux.slashdot.org/linux/08/08/17/1649232.shtml](http://linux.slashdot.org/linux/08/08/17/1649232.shtml)

---

