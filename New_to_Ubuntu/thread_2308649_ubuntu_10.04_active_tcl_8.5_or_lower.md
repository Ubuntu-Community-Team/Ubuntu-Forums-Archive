---
title: "ubuntu 10.04 active tcl 8.5 or lower"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by alfredo10 on 2016-01-04
Hi, absolute beginner here, well, in this forum at least. 
I tried searching for this in the forums but I get "Sorry - no matches".

I have a tcl file I need to run, should use activetcl 8.5 or lower. 

Doble-clicking on it does nothing. Right clicking and selecting "open with" I have no idea which program I should select (there doesn't seem to be any activetcl program or similar).

I read in another post about using this: sudo apt-get install tk8.5 tcl8.5; But I get this message: "tcl8.5 is already the newest version".

How do I check if activetcl is installed? And which version? If yes, how do I run the tcl file? If not, how do I install version 8.5? (can't find it in the activetcl site)

Not really familiar with tcl, so I don't know what info to include, if you need any more info, please let me know.

Any help in solving this issue is appreciated,

Alfredo

---

### Post by yancek on 2016-01-04
To check if an application is installed, you can try which activetcl or whereis activetcl or whatever the actual program name is.  You can also use Synaptic if you have that or the Software Manager.  Ubuntu 10.04 is no longer supported as you can see at the Ubuntu site below.  Did you read the info at the second link below on activetcl?  

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by steeldriver on 2016-01-04
I'm not sure if activetcl has any proprietary non-standard features, but you can try running it using the standard tcl shell via a terminal

```

tclsh path/to/your/file

```

If the file starts with a "shebang", you should be able to run it directly by making the file executable and then just calling it by name

---

### Post by alfredo10 on 2016-01-08
First of all, thanks for your answers. I really appreciate it.

-yancek: using whereis activetcl returns:
> ~$ whereis activetcl
activetcl:
alfredo@alfredo-cnc:~$
Not sure what that means :(

> Did you read the info at the second link below on activetcl?
Don't see a second link, only one about Ubuntu releases. I need to run this on 10.04 or maybe 12.04.

-steeldriver: using tclsh path/to/your/file returns:
> ~$ tclsh /home/alfredo/Desktop/rtstepperemc_win32-2.0.3-0/tkmini.tcl
couldn't load file "rtstepperemc.so": rtstepperemc.so: cannot open shared object file: No such file or directory
    while executing
"load rtstepperemc[info sharedlibextension]"
    (file "/home/alfredo/Desktop/rtstepperemc_win32-2.0.3-0/emc.tcl" line 45)
    invoked from within
"source [file join [file dirname [info script]]  emc.tcl]"
    (file "/home/alfredo/Desktop/rtstepperemc_win32-2.0.3-0/tkmini.tcl" line 31)
Seems to me there's some complement which is not being found?

Being  honest, I'm getting very slow and not to much support from the guy who  actually sells the product that uses this software, so I'm getting  second thoughts about buying it anyway, just a few tries to see if I can  get it to work.

Thanks again for your help,

Alfredo

---

### Post by steeldriver on 2016-01-08
Hmm... anything with _win32 in it doesn't sound too promising

Is this the software you are trying to run?

[http://www.ecklersoft.com/](http://www.ecklersoft.com/)

If so, did you read the part about

> 
March 2015, announcing the new PyMini software release. **PyMini replaces the old existing rt-stepper software.  This new release is python based and replaces TkMini which was written in TCL/TK.** PyMini takes advantage of newer  software components and provides an upgrade path with new OSs.  This release provides the following new features.


---

### Post by Bucky Ball on 2016-01-09
Again, 10.04 LTS is no longer supported. If the machine is online, better it isn't. You will not be able to update the machine, and that includes security updates. You may be able to fix this issue, may be not, but it won't change the fact the release is unsupported and as time goes on, things will get more difficult and support will be harder to find (and we don't officially support EOL releases here).

Good luck, whatever you do. :)

---

### Post by alfredo10 on 2016-01-09
-steeldriver: Yes! That's it! I did read and download the new pymini, but it looses a lot of important features (for me, but not for the developer :D) compared to the old rtstepper GUI. The developer says his USB dongle thing will work with either, but that's as far as his help will go, and the control software is open source anyway.

What I'm trying to accomplish: run a CNC machine. So far, I am using LinuxCNC, which only worked on Ubuntu 10.04. It is now available for 12.04 but I may run into real time delay issues, so, I'd like to control the CNC machine through USB instead of parallel port, my only option for Linux is the ecklersoft solution, but I have not been able to run either the old rtstepper or the new python (which again, I don't like anyway) in either 10.04 **OR** 12.04 on my cousins computer (Is 12.04 LTS still supported? I believe it is)

-Bucky Ball: that's another important reason why I'm trying to make this work, so I can upgrade to 12.04 or any higher. I'm already having issues with my printer and a few internet stuff (yes, it's online, but I'm a daredevil ;)) The only way I will continue to use Ubuntu is if I can make the rtstepper work, it's the only Linux solution that I like. Else, I 'll have to get one of the commercial Windows options that work through USB, which is a shame because I really like Ubuntu :(.

The problem I've had with Ubuntu so far, is that although it works fine when you only use stuff like firefox, word processors, watch movies, etc, special applications like what I use need to be tweaked/altered somehow, which takes time (which I don't have) and many times escapes my knowledge field.

I appreciate your help and your concerns A LOT anyway, thank you very much!!

---

