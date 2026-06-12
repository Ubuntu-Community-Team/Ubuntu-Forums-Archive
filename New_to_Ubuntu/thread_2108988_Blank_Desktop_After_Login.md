---
title: "Blank Desktop After Login"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by Pyramist on 2013-01-26
So I had originally posted in another section regarding setting up my wireless network adapter, and I got that taken care of but a bunch of other problems are occurring so I figured I'd make a new thread here.

I installed Ubuntu 12.10 via USB onto my old Dell Dimension 2400 desktop to give the OS a try, but I'm running into problem after problem.  Currently, after I log in, all that I get is the background image.  No bar at the top, no access to anything.  When I try to run terminal by pressing Ctrl+Alt+T, it takes about five minutes to load and once it does, it won't allow me to type any commands.  I'm really excited to start learning Linux so I hope someone can help me out!

---

### Post by kc1di on 2013-01-26
Hello Pyramist and welcome to Ubuntu,

go to my answer to [this thread]("http://ubuntuforums.org/showthread.php?t=2108986") and see if that will be of help to you.
good luck

---

### Post by Pyramist on 2013-01-26
I tried the 'nomodeset' command from the GRUB menu, and followed all the instructions, but when it boots the screen turns black and stays that way.

---

### Post by kc1di on 2013-01-26
> **Pyramist said:**
> I tried the 'nomodeset' command from the GRUB menu, and followed all the instructions, but when it boots the screen turns black and stays that way.

Sorry that didn't work the other thing may be that your graphics card is not set up correctly.

What is your video card?

---

### Post by Pyramist on 2013-01-26
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

---

### Post by bogan on 2013-01-26
Hi!, **Pyramist**,

Try: 'i915modeset=0' instead of 'nomodeset'.

Post: ```
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan**.

---

### Post by Pyramist on 2013-01-27
Alright booting with 'i915modeset=0" allowed me to login and access  terminal, although I'm still getting just the background image.  I ran  both commands and this is what I got:

lspci -nnk | grep -iA3 vga
00:02.0  VGA compatible controller [0300]: Intel Corporation  82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562]  (rev 01)
        Subsytem: Dell Device [1028:0160]
        Kernel driver in use: i915
        Kernel modules: intelfb, i915

/usr/lib/nux/unity_support_test -p
X Error of failed request: BadAlloc (insufficient resources for operation)
   Major opcode of failed request:   153 (GLX)
   Minor opcode of failed request:   3 (X_GLXCreateContext)
   Serial number of failed request:  32
   Current serial number in output stream:   33

---

### Post by DuckHook on 2013-01-28
I'm a tinkerer with old equipment, but even by my standards, your box is ancient. If it is in its initial configuration, it won't run Ubuntu 12.10. Even maxed out with memory, getting it to go will be like pulling teeth and you won't have an enjoyable experience. You need a far lighter distro like Lubuntu. In your case, you might even try Puppy Linux, which is designed to run on your level of equipment. I'm surprised that you managed to get 12.10 to load. I thought that the P4 CPU lacked support for PAE which the new Linux Kernel must have.

---

### Post by frank604 on 2013-01-28
I also vote for puppy linux.  Never tried but heard many good things about it in terms of very old hardware support as well as access to ubuntu's vast repositories.

[http://puppylinux.org/main/Download%20Latest%20Release.htm]("http://puppylinux.org/main/Download%20Latest%20Release.htm")

If you want slackware compatible it is slacko puppy.
If you want ubuntu compatible it is Lucid Puppy. (3rd one down I think)
Precise Puppy is debian compatible.

---

### Post by Pyramist on 2013-01-28
Yeah this machine is OLD!  I hadn't even turned it on in 2 years so that's why I figured I'd use it to experiment on.  Thanks a lot for your help guys!!  I'm gonna give one of the other distros a shot.

---

### Post by furything on 2013-01-28
Hi DuckHook

Your post confused me and may others you said about P4 but the Dell box is a P2 (which I think is what you meant) so yes puppylinux 

For anyone else reading this thread and getting confused P4 (certainly Northwood) is supported as I run 12.04 quiet happily on about 4 machines. In fact I have a couple that have to run x86 so must be older P4s

---

### Post by DanaLG on 2013-01-28
I am trying to do the same thing with an old DELL Dimension 3000. I am getting the exact same problem, the blank desktop after login.

I to was trying to find a use for this old PC. It runs Windows XP Professional fine. The cost of upgrading to Windows 7 on this machine is not worth it. I was hoping that ubuntu would give it a second life as a simple machine to do simple things.

---

### Post by DuckHook on 2013-01-28
> **furything said:**
> Hi DuckHook

Your post confused me and may others you said about P4 but the Dell box is a P2 (which I think is what you meant) so yes puppylinux 

For anyone else reading this thread and getting confused P4 (certainly Northwood) is supported as I run 12.04 quiet happily on about 4 machines. In fact I have a couple that have to run x86 so must be older P4s

The 3.2.x kernels (which Ubuntu 12.04 uses) will still run on non PAE cores, so your boxes will be quite happy. However, 12.10 uses the 3.5.x kernel, which dropped support for PAE. For all I know, P4 might support PAE, but I've never bothered to find out, as I run 12.04 on all of my old machines. My surprise arose because the OP mentioned that he had managed to install 12.10, so I guess a P4 is PAE enabled after all.

BTW, the specs for the OP's box says that it comes with either a P4 or a Celeron, so I'm assuming it was a P4. However, it's the memory and video that will be his bottleneck, as you need about 2 GB to run Ubuntu effectively whereas Lubuntu will run nicely on as little as 500MB. Moreover, Unity 3D will choke on the little video chip he has. I believe that his video maxes out at 64 MB and even that amount is shared system memory. It's like trying to haul a semitrailer with a motorcycle. Okay that's an exaggeration, but not by a whole lot.

These old machines can still be very effectively used, but it's best if they are repositioned for other purposes. See response to next post below.

---

### Post by DuckHook on 2013-01-28
> **DanaLG said:**
> I am trying to do the same thing with an old DELL Dimension 3000. I am getting the exact same problem, the blank desktop after login.

I to was trying to find a use for this old PC. It runs Windows XP Professional fine. The cost of upgrading to Windows 7 on this machine is not worth it. I was hoping that ubuntu would give it a second life as a simple machine to do simple things.

I've found that trying to get very old machines to run the latest and greatest (which is what Ubuntu 12.10 is) is never fruitful. Instead, the best use for these machines are either with very lightweight distros (enumerated in prior posts) or as servers that don't run GUIs. I have an old Optiplex 170L (P4, 768 MB Ram, Integrated Graphics) very much like your machine. I put a minimal Ubuntu install on it (this is a command-line-only Ubuntu that can be found [here]("https://help.ubuntu.com/community/Installation/MinimalCD")) and it now acts as a multi-purpose server. You can use it as a file/print server, a torrent server, a gateway/router, a VPN server, even a mail/web server if you are so inclined. None of these services require a GUI, not even a monitor. Mine runs headless and I ssh into it if I need to configure something. The crazy thing is that has the best uptime of any machine in my house because it chugs away silently and without fuss, always delivering, never complaining. Of course, I don't rely on it for production work because the power supply or the HDD can give way at any time on these old codgers, but the point is they can be co-opted nicely for the right uses. Unfortunately, 3D-heavy modern GUIs don't count as a good use.

Your machine is a good tinkering box. If it must be your production machine and you must have a GUI, then try Lubuntu. It has enough similarity to Ubuntu that it won't feel too foreign. Otherwise, trying to shoehorn Ubuntu 12.10 into these old boxes is an exercise in futility. IMO, the minimal practical specs for the latest Ubuntus are at least duo core, 2GB of memory and a proper 3D video card with at least 512MB of dedicated memory. Even if you manage to get Ubuntu to run on less, the experience won't be pleasant.

---

