---
title: "&quot;gcc-arm-linux-gnueabihf is not avaliable&quot; problem"
date: 2014-03-30
forum: Packaging and Compiling Programs
---

### Post by Gang_Yang on 2014-03-30
Hi all,

I am doing a project on Panda board and the OS Ubuntu 12.04 (preinstalled desktop image). I want to recompile the kernel but got a problem.
After I entered "sudo apt-get install gcc-arm-gnueabihf" in terminal, the terminal proceeds a little bit but then showed "package gcc-arm-linux-gnueabihf is not avaliable, but is referred to by another package". I searched on google about this but can't find a solution.
I am still a rookie of Ubuntu so sorry if this question sounds silly. Could anyone explain why I have this error and how to solve it?
Thanks.

---

### Post by steeldriver on 2014-03-30
Hello and welcome to the forums

Did you add the 'universe' repository to your sources.list and then run 

```
sudo apt-get update
```

first? What does

```
apt-cache policy gcc-arm-linux-gnueabihf
```

say?

---

### Post by Gang_Yang on 2014-03-30
I didn't add the universe repository to my sources.list. Cound you tell me how to do it?

---

### Post by steeldriver on 2014-03-30
You can use any of these methods

[LIST=1]
[*]start Ubuntu Software Center; go to the 'Edit' menu and select 'Software Sources...' --> 'Ubuntu Software' and check the box beside *Community-maintained free and open-source software (universe)* 
[*]start Synaptic package manager; same as (1) but it's under 'Settings' --> 'Repositories' 
[*]edit your /etc/apt/sources.list file directly and add an entry like 
[/LIST]
[INDENT]```
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
```
[/INDENT]

(you can replace [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) with whatever mirror the rest of your sources are using).

---

### Post by Gang_Yang on 2014-03-30
Thank you.
I tried your method and the "sudo apt-get update" has an error
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-armhf/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-armhf/Packages) 404 Not Found [IP:2001:67c:1562::14 80]

The "gcc-arm-linux-gnueabihf" returns
Installed: (none)
Candidate: (none)
Version table:

Does it mean that this package is no longer available on Ubuntu server?

---

### Post by steeldriver on 2014-03-31
My apologies - I think I misunderstood what you are trying to do

AFAIK gcc-arm-linux-gnueabihf is a *cross-compiler* i.e. it is a package available for i386/x86_64 etc. architectures to let them build binaries for running on armhf

If you are actually building natively on an arm platform (as indicated by your *binary-armhf* repository URL) then I would think you just need the native gcc package for that architecture?

---

### Post by Gang_Yang on 2014-04-01
Oh, I didn't know that. Thank you.
The reason why I need to get a compiler is that I want to patch the kernel. I am trying to enable SPI on my Panda Board.
[http://www.omappedia.com/wiki/PandaBoard_SPI](http://www.omappedia.com/wiki/PandaBoard_SPI)
According to instruction in that link, I need to change arch/arm/mach-omap2/board-omap4panda.c file, but my /src folder is completely empty.
Do you know how to get native gcc package and compile the kernel?

---

