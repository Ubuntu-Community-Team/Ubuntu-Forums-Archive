---
title: "Wine Vs Virtual Box"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by nickelbox on 2012-01-28
Can someone kindly tell me the pros and cons to each and what they consider to be the better?

Thanks

---

### Post by wolfen69 on 2012-01-28
_Wine_

**Pros:** You can run some windows apps without needing windows.

**Cons:** Only *some* windows apps will work.

_Vbox_

**Pros:** You can run virtually any windows app.

**Cons:** You need a pretty beefy computer to run vbox effectively, and a full install of windows.

If the apps you need, run via wine, then I would say that is the best choice. If not, vbox is a good choice.

---

### Post by anewguy on 2012-01-28
If you have a copy of Windows with a valid license and if your hardware is powerful enough, then virtualbox would definitely be the way to go.

However, lacking a copy of Windows with a valid license or lacking sufficient hardware, then wine, playonlinux or crossover (I *think* that's what it is called) would probably be the better choice.

Dave ;)

EDIT:  You beat me to it!  ;)  Dave ;)

---

### Post by halitech on 2012-01-28
WINE:
Pros - no need to have a full OS installed
Con - doesn't support a lot of the latest software

Virtualbox:
Pro - will run almost anything a real install will run (3d support is still iffy though)
Con - need to have a legit install of windows
con - uses more hard drive space


edit, wow, question goes 2 hours without an answer and then gets 3 in 2 minutes  ~L~

---

### Post by nickelbox on 2012-01-28
I guess I am a bit confused on Virtual Box. If I need windows installed, what's the purpose of installing Virtual Box?

---

### Post by halitech on 2012-01-28
VirtualBox is exactly that, a virtual computer running as a program on another operating system. Personally I use Vbox over WINE because I find the programs I want to run (mostly IE to see how websites look as I'm designing them or keeping up to date on problems so I can support family and friends) work properly in Vbox where WINE is a pain in the butt to get alot of things running properly if you even can.

---

### Post by anewguy on 2012-01-28
> **halitech said:**
> ....edit, wow, question goes 2 hours without an answer and then gets 3 in 2 minutes  ~L~

We're slow readers ;) ;)

Dave ;)

---

### Post by halitech on 2012-01-29
> **anewguy said:**
> We're slow readers ;) ;)

Dave ;)

okay, I'll type slow from now on so you can keep up ;)

---

### Post by Dlambert on 2012-01-29
For me I have VB running OSx and Windows 7. What I do with my system is split the cores, so 3 are for the vb, and i split the ram to 8 and 8.

---

### Post by TheFu on 2012-01-29
The other answers are correct. I'll offer a slightly different point of view.

WINE provides a compatibility API layer between the win32 API of Microsoft and the native Linux calls. However, not every API has been implemented yet, so not every Windows program works.  Microsoft is constantly adding new interfaces, so the API is a constantly changing target.

VirtualBox provides a virtual hardware environment that you can run any multiitude of operating systems on top of.  This is PC virtual machine technology. The operating system doesn't know it isn't running on a real, physical PC.  So, if you need to run a non-FLOSS operating system, then you will need a valid license from the commercial company - like Microsoft Windows.  The overhead to run an entire OS is much greater than running just an API interface layer. More RAM, CPU, and disk space are needed. That's the downside with VirtualBox and other virtual machine solutions like QEMU, KVM, Xen, VMware Player, etc....  more overhead.  

Commonly available hardware these days can easily support this.  I've been using VirtualBox on a laptop to run Lubuntu as my primary desktop environment inside a VM for about 4 years. It is extremely stable and suitable for most "office productivity applications", but not so much for gaming or video work. I'm not saying it doesn't work, just that graphics performance uses virtual graphics drivers - not direct access to your GPU. This may or may not be an issue.

You can also run other versions of Linux or even the same version inside a VM. This is handy for testing or to isolate new software from your main desktop or server environment. Very handy.

Which is better? That depends.  For running MS-Windows programs, I always try WINE first - I try really hard. If I can't get it working well under WINE, then I'll use Windows running inside a virtual machine - either KVM or VirtualBox depending on which physical hardware I'd like it to run on.  I do not game very much, so running inside a VM on a server over the LAN is usually very acceptable to me.

---

### Post by varunendra on 2012-01-29
> **wolfen69 said:**
> 
If the apps you need, run via wine, then I would say that is the best choice. If not, vbox is a good choice.
+1
Perhaps the best criteria to make the decision.
And Crossover is nothing but a well-polished commercial version of wine,  which offers a much better installation and management interface than  wine does. It's trial version (14 days IIRC) is fully functional.

> **nickelbox said:**
> I guess I am a bit confused on Virtual Box. If I need windows installed, what's the purpose of installing Virtual Box?
It just offers you virtual machines. It's upto you what purpose you use them for, and the list of possible purposes and advantages (as well as a few disadvantages) is so long I'm afraid it'd be too large to put in one post.

The best way to figure out its usability for yourself is to just install and start using it (of course, if you have enough amount of RAM to suffice the minimum requirements of the host+guest Operating Systems).

---

### Post by underquark on 2012-01-29
I run both Wine and VirtualBox. If a program runs fine under Wine (I like Simple Sudoku, for example) then it launches quickly and I am happy. If I can't configure it easily to run under Wine then I use Win XP (I own a few legal copies) under VirtualBox for the few Windows programs that I run.

So - Wine works for some Windows programs and is quick to launch.
VirtualBox  requires a copy of Windows, needs a reasonably-specced machine (just don't expect quick graphics and effects on an older, slower machine, but it'll still run) but does  allow you to run more Windows programs.

---

### Post by nickelbox on 2012-01-29
Alright, things make sense now

I appreciate all the help

---

### Post by gradinaruvasile on 2012-01-29
Another thing - 3d-heavy directx games that run via wine usually will not work in virtualbox.
This is because the virtualbox video drivers, despite the fact that in theory they support 3d acceleration, do not translate many directx functions af of the current virtualbox versions (4.1.8). Opengl games may or may not run (half life base dones sem to run, but not that great).
Wine, on the other hand, translates directx functions to opengl thus enabling directx games to run. To a certain extent, of course, not all work but quite many do.

Another advantage of virtualbox is the possibility of using USB/serial peripherals by effectively passing the device directly to virtualbox. That means that even the device cannot be used in Linux, i twill work in virtualbox with its native Windows drivers (tested with usb gps units, usb dongles, digital signature pads etc).

---

