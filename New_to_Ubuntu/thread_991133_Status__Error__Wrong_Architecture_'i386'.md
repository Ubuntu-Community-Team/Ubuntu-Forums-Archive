---
title: "Status : Error : Wrong Architecture 'i386'"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by FunkyBluffMan on 2008-11-23
Hi,

I've just installed ubuntu 8.10 using WUBI. I'm trying to install skype on it. I downloaded the "Ubuntu 7.04-8.04" option on Skypes download page and when I try and install it I get the following error message

Status : Error : Wrong Architecture 'i386'. 

I know I have a intel processor which is not 64bit though I think my motherboard may support 64bit. 

I'm new to linux/ubuntu and really like it except I need to try and figure out how to compile/install programs.

How can I get skype installed. I'm also looking for yahoo messenger or another program to use to chat to people on Windows but it must be able to use a webcam.

---

### Post by beno1990 on 2008-11-23
Navigate to the folder you have the .deb file for Skype in (using the cd command), and then do the following:

```

sudo dpkg <filename>.deb

```

---

### Post by Paqman on 2008-11-23
Actually, you probably do have a 64-bit processor, because it seems like Wubi has installed 64-bit Ubuntu.

what does it say if you put this into a terminal:
```
uname -m
```

---

### Post by FunkyBluffMan on 2008-11-23
when I run uname it says x86_64. I only have a old P4 3.0GHZ any originally Dell Dimension 3100.

---

### Post by Paqman on 2008-11-23
> **FunkyBluffMan said:**
> when I run uname it says x86_64. I only have a old P4 3.0GHZ any originally Dell Dimension 3100.

Congratulations, you are running 64-bit Ubuntu!

There doesn't seem to be a 64-bit version of Skype available, which is very slack of them. If you really want Skype and aren't bothered about reinstalling then you can force Wubi to install 32-bit, as mentioned on the Wubi site:
> 
*Can I force Wubi to download and install a 32 bit version of Ubuntu?*

Yes, either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument.


---

### Post by FunkyBluffMan on 2008-11-23
Just found these two links quiet useful
[http://packages.medibuntu.org/intrepid/skype-common.html](http://packages.medibuntu.org/intrepid/skype-common.html)
[http://packages.medibuntu.org/intrepid/skype.html](http://packages.medibuntu.org/intrepid/skype.html)

It does have 64bit versions there. Is it hard to get 32bit software working on 64bit? I just want a webcam chat that I can use on my distro and that would allow my windows contacts to use so that we can see each other when we chating. I manged to log into kype though I dont know if I can webcam chat yet.

---

