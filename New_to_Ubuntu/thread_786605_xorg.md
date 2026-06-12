---
title: "xorg"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-08
my xorg version is 1.4.0.90
i am using Ubuntu 8.04
i am installing some drivers, and one of the steps is to copy some files to /usr/X11R6/lib/modules/input
the problem is, i dont have /lib/modules/input

is there something i need to download?
what is wrong?

thank you

---

### Post by glennric on 2008-05-08
What drivers are you installing?

Also, what do you mean your xorg is version 1.4.0.90?  Did you compile and install it yourself?  That is not the version of xorg in Ubuntu 8.04.

---

### Post by fmpfmpf on 2008-05-08
i am trying ot install elo drivers
[http://www.elotouch.com/Support/Downloads/dnld.asp#linux](http://www.elotouch.com/Support/Downloads/dnld.asp#linux)
(Linux with serial interface)

maybe i got my xorg version wrong
how can i check my xorg version?

---

### Post by glennric on 2008-05-08
Don't worry about the xorg version.  You should have the version that comes with 8.04 by default.  We don't need to know that.  Let me take a look at that page.  If drivers are released then there is a good chance Ubuntu already has them available and you don't need to install them yourself.

---

### Post by glennric on 2008-05-08
Have you seen the following link:
[Elo Touch Screen Intelli Touch (USB)]("http://ubuntuforums.org/showthread.php?t=579155&highlight=elo+touch")
Is that what you are talking about?

---

### Post by fmpfmpf on 2008-05-08
if you take a look at the readme file, there is this instruction


  d.) Copy and place the X display Elo component file in the proper
      location. Use "> X -version" command to check the X display
      version.


       For Xorg version 7.2 or later: (example: Fedora 7)
           
         > cp  /etc/opt/elo/elo_drv.so  /usr/lib/xorg/modules/input

       (or)

       For Xorg version 7.0 to 7.1.1: (example: Fedora Core 5)
           
         > cp  /etc/opt/elo/elo_drv.o  /usr/lib/xorg/modules/input

       (or)

       For other XFree86 or Xorg versions: 

         > cp  /etc/opt/elo/elo_drv.o  /usr/X11R6/lib/modules/input


i need to know my xorg version to proceed

thank you very much

---

### Post by glennric on 2008-05-08
Well the version of xorg in Hardy (8.04) is 7.3, and the directory /usr/lib/xorg/modules/input should exist (it does on mine).

---

### Post by fmpfmpf on 2008-05-08
how do you check the xorg version?

---

### Post by unutbu on 2008-05-08
```
dpkg --list xorg
```

The output should look something like
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name             Version          Description
+++-================-================-================================================
ii  xorg             1:7.2-5ubuntu13  X.Org X Window System
```

1:7.2-5ubuntu13 means version 7.2 is installed. Yours probably will say 7.3.

---

### Post by fmpfmpf on 2008-05-08
ok, i have got it
thank you very very much !!!!!

---

### Post by glennric on 2008-05-08
unutbu:  I think a nicer way to get version information for a specific package is to type
```
apt-cache policy xorg
```
This returns:
```
xorg:
  Installed: 1:7.3+10ubuntu10
  Candidate: 1:7.3+10ubuntu10
  Version table:
 *** 1:7.3+10ubuntu10 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
```
The problem with the "dpkg -l xorg" method is that if your terminal is not big enough you often get the information cut off.

---

