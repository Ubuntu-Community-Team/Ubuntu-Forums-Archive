---
title: "Windows 10 Alternative"
date: 2015-09-07
forum: New to Ubuntu
---

### Post by rbengr on 2015-09-07
Hi,

I am building a PC that will primarily run Windows 10.  Occasionally, I would like to run Ubuntu 14.04.  What is the best way to set up this flexibility?  Will I need additional hardware drivers?

Thanks

---

### Post by mastablasta on 2015-09-07
run windows 10 and install virtual box. inside the virtual box run Ubuntu occasionally.

---

### Post by ajgreeny on 2015-09-07
The answer to that will be entirely dependent on the hardware that you use to build the new machine.

Try to avoid very new cutting edge hardware and you may find that all the drivers needed are available in the kernel by default, and if you are using a separate graphic card it is probably best to look into nvidia rather than AMD-radeon, as nvidia drivers are generally better supported in my opinion, though I have not needed a separate graphic card for years.

Most Intel hardware other than very new versions of wifi cards and perhaps graphics, will be generally well supported, and will likely work with no further action needed on your part; AMD CPUs are also fine but the integrated graphics can, as far as I am aware, be a little more problematic, so search before you purchase is my main recommendation, using a custom search engine such as [www.googlubuntu.com](www.googlubuntu.com) or my own custom google-search at [https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao)

I've just seem mastablasta's answer, and depending on the spec of the new machine, VBox may be another good way to work; it depends what exactly you mean by "Occasionally, I would like to run Ubuntu 14.04".

---

### Post by chemist931 on 2015-09-07
I have dual-booted on several different systems, and again, as long as you don't get the absolute newest hardware out there, you should be fine.  It can be hard with Windows to dual boot on the same drive, so if possible, it would be easiest to use two hard drives and install the OS' separately.  This is all assuming you don't want to mess around with virtual machines.

---

### Post by Geoffrey_Arndt on 2015-09-07
Unless you're a "Gamer" . . . . why not do the opposite?   Run Ubuntu or Mint or OpenSuse and then Win10 as the guest0S in VirtualBox or VMWare.    

At least this way, you can still be in control of the system you just built (software and hardware).   Seems an awful waste of new hardware to have Win10 in "charge".

---

### Post by monkeybrain20122 on 2015-09-07
> **Geoffrey_Arndt said:**
> Unless you're a "Gamer" . . . . why not do the opposite?   Run Ubuntu or Mint or OpenSuse and then Win10 as the guest0S in VirtualBox or VMWare.    

At least this way, you can still be in control of the system you just built (software and hardware).   Seems an awful waste of new hardware to have Win10 in "charge".

+1.

BTW several posters made the qualification "if you don't have the absolute cutting edge hardware.." I just want to point out that this applies as well to Win10 if not more so. Driver (even for some less than absolute cutting edge hardware) availability often lags behind new Win releases. Experienced Win users usually don't upgrade at the first available moment, partly because of bugs, but also because of drivers.

---

### Post by Geoffrey_Arndt on 2015-09-07
Just one other thing . . . . . FYI

It's come to light recently that Windows 10 will by default settings . . convert your PC to a Win P2P network, and use your bandwith to help install Win10 and updates to other users PC's not on your network.

This is only one example of many of how Win10 is a remote control, hybrid cloud/client.    See:   [http://www.howtogeek.com/227827/windows-10-is-great-except-for-the-parts-that-are-terrible/](http://www.howtogeek.com/227827/windows-10-is-great-except-for-the-parts-that-are-terrible/)

---

