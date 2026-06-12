---
title: "some beginner questions"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by widespread on 2008-07-08
Hey, I am interested in trying linux as an alternative to windows.  Just in case I don't like it, or I find it to be incompatible with this old dell laptop I have, I was going to try to dual boot at first.  But I was wondering, how easy is it to remove Linux if I dual boot and I just want to keep windows?  On the other hand, what happens if I love Linux and want to get rid of the windows OS, how hard is that? I know you need to partition the hard drive for dual boots, and I am not to familiar with that.  Also, from looking around at this site, I see "Broadcom" (spelling?) wireless cards, which dells have, need to be tinkered with to work with ubuntu.  Could I can seriously harm to card if I do this?  If I mess with it and want to go back to windows, will it not work?  I guess the same goes for any other hardware, but I was just curious.  Thanks for your time, I hope this questions already haven't been answered.

---

### Post by Inxsible on 2008-07-08
its easy to dual boot to test if you will be comfortable.

Check these two links on how to partition and dual boot. [Partitioning]("http://www.psychocats.net/ubuntu/partitioning") | [Installing]("http://www.psychocats.net/ubuntu/installing")

You can simply format the ubuntu partition if you dont like it. and then use the XP CD to fix MBR. If you don't have the XP CD, i think there are ways to do it without it as well.

Getting rid of windows is easy too by simply formatting it. Note however, that if you are into gaming, you will not be able to play those games on Linux. so you might just want to hang on to the Windows partition even if you use Linux for all your daily activities.

---

### Post by widespread on 2008-07-08
> **Inxsible said:**
> its easy to dual boot to test if you will be comfortable.

Check these two links on how to partition and dual boot. [Partitioning]("http://www.psychocats.net/ubuntu/partitioning") | [Installing]("http://www.psychocats.net/ubuntu/installing")

You can simply format the ubuntu partition if you dont like it. and then use the XP CD to fix MBR. If you don't have the XP CD, i think there are ways to do it without it as well.

Getting rid of windows is easy too by simply formatting it. Note however, that if you are into gaming, you will not be able to play those games on Linux. so you might just want to hang on to the Windows partition even if you use Linux for all your daily activities.

thanks for the guides, I think I am going to try dual boot once the computer is backed up.  So I can simply format the over one of the Operating Systems if I don't like it?  Also what do you mean by "using the XP cd to fix MBR?"  Thanks for the response.

---

### Post by Frenske on 2008-07-08
You metioned old laptop. The lastest version of Ubuntu requires considerable amount of RAM and a good CPU to run smoothly. If it has less than 512MB you consider a special version: Xubuntu ([www.xubuntu.org](www.xubuntu.org)) which weights less on the computer resources.

---

### Post by milan_cortana on 2008-07-08
Wellcome aboard.
J saw your post minute ago.
"fix mbr"?
J tried on google and found this:[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)
Hope u can use it.

Cheers

---

### Post by annda on 2008-07-08
> Also what do you mean by "using the XP cd to fix MBR?"

it means that unless you have a windows install cd (NOT a recovery cd), you will have to jump some hoops to restore your computer to pure windows setup (booting and using windows will be no problem any way you go).

not to discourage you, but this is something many people ignore and are irritated with later on.

---

### Post by widespread on 2008-07-08
> **Frenske said:**
> You metioned old laptop. The lastest version of Ubuntu requires considerable amount of RAM and a good CPU to run smoothly. If it has less than 512MB you consider a special version: Xubuntu ([www.xubuntu.org](www.xubuntu.org)) which weights less on the computer resources.


It is a Dell Inspiron 8600.  From the system proprieties menu: "Intel Pentium Processor 1.40 Ghz 1.40Ghz, 512 MB of RAM."  Do you think this is good enough for the latest version of ubuntu? Or should I go Xubuntu? Thanks for the heads-up.

---

### Post by Inxsible on 2008-07-08
> **Frenske said:**
> You metioned old laptop. The lastest version of Ubuntu requires considerable amount of RAM and a good CPU to run smoothly. If it has less than 512MB you consider a special version: Xubuntu ([www.xubuntu.org]("http://www.xubuntu.org")) which weights less on the computer resources.
Or if its really old then you may even think of installing a minimal and then choosing your own window manager. But if you are brand new to Linux, then simply go with Ubuntu or Xubuntu which will give you a usable desktop.

---

### Post by bhadotia on 2008-07-08
>  Also what do you mean by "using the XP cd to fix MBR?"
When you install ubuntu the boot-loader (program which boots the OS ), which is called GRUB, takes over as the main boot-loader and replaces the xp boot-loader in the MBR (Master Boot Record) . The MBR is first 512 bytes of the HD and is the place where MBR exists.
If you remove ubuntu the GRUB loader will also be gone with it - so that you will need to fix (or place) the xp bootloader in the MBR to boot xp.
A google search will give a lots of other info, e.g.:
[http://www.techzonez.com/forums/archive/index.php/t-3975.html](http://www.techzonez.com/forums/archive/index.php/t-3975.html)

---

### Post by abn91c on 2008-07-08
before you try all that possibly complicated partitioning try wubi: [http://wubi-installer.org/](http://wubi-installer.org/)
i use it on a dell inspiron 1000 with 512mb ram and it wroks perfectly fine

---

### Post by kevinatkins on 2008-07-08
Hi Widespread,

your system specs look OK to run Ubuntu - it won't be really quick, and depending on the graphics system on the machine, you may not be able to run the snazzy desktop effects, but it should run OK. The main thing is memory - you need at least 384MB to run the installer.

As for your wireless - yes, you may need to fiddle to get that working. I don't have personal experience of the Broadcom chipset, but chances are you might need to run a Windows driver within a Linux wrapper (known as NDISWrapper) - don't panic, it's not as complicated as it sounds. But! This is one of my big bugbears with Ubuntu - other distributions take a more sensible approach to NDISWrapper, but with Ubuntu, you'll have to compile it from source, and every time there's a kernel upgrade (which is relatively often, as part of the normal system updates), you'll have to compile it again. It's really not difficult, and there's plenty of help out on the web, but it's a nuisance, nonetheless.... Mandriva Linux is better in this respect (from memory - it's been a while since I used that)

You absolutely will not damage any of your hardware running Linux, rest assured of that. 

I suggest you just dive in - burn a CD, run a 'Live' session from the CD and see how everything works, then install if you like it.. Oh, you can also install Ubuuntu to run 'inside' Windows, which has to be the lowest risk way of evaluating it - just pop the CD in whilst you're in Windows and run the Wubi installer!

---

### Post by widespread on 2008-07-08
milan_cortana, annda, bhadotia--thanks for the info on booting issues, and MBR.  I will look into it more.

abn91c- thanks for the wubi-installer, it will really help if i go with ubuntu.

Inxsible, kevinatkins- thanks for the info. Do you guys think I should go with Xubuntu instead?  Im looking for this computer mainly to surf the web while in the library at school, maybe write some word docs, nothing too big I think.  Its just the old laptop is lighter and smaller than my main laptop, which makes it easy to carry back and forth.

---

### Post by Inxsible on 2008-07-08
> **widespread said:**
> milan_cortana, annda, bhadotia--thanks for the info on booting issues, and MBR.  I will look into it more.

abn91c- thanks for the wubi-installer, it will really help if i go with ubuntu.

Inxsible, kevinatkins- thanks for the info. Do you guys think I should go with Xubuntu instead?  Im looking for this computer mainly to surf the web while in the library at school, maybe write some word docs, nothing too big I think.  Its just the old laptop is lighter and smaller than my main laptop, which makes it easy to carry back and forth.Its your preference really. What it does depend on is how much memory you have and the power of your CPU.
Can you tell us your system specs...so we can make a better guess?

Gnome - is bloated, IMO. It installs a bunch of apps that I mostly dont use. So I end up having to remove that. Xfce also does the same, although to a lesser degree and therefore is much lighter than Gnome in terms of memory footprint.

If web browsing and some document editing is the primary use of the computer, then Xubuntu will suffice. (although it can definitely do a lot more)

Heck..even a minimalist WM like Openbox or Pekwm  or IceWM would be sufficient to do what you need :)

---

### Post by kevinatkins on 2008-07-08
Xubuntu may be a good choice. I personally prefer the Gnome desktop, but Xubuntu is pretty good. You could always install Xubuntu alongside regular Ubuntu and choose which to use - there's really no difference between them apart from the desktop, so you just need to install the Xubuntu-desktop package and you'll have the choice. Also, for general word-processing duties, you may find that Abiword is better suited to a slower machine than the full-blown OpenOffice, which is mega heavy on system resources...

---

### Post by Frenske on 2008-07-09
> **widespread said:**
> milan_cortana, annda, bhadotia--thanks for the info on booting issues, and MBR.  I will look into it more.

abn91c- thanks for the wubi-installer, it will really help if i go with ubuntu.

Inxsible, kevinatkins- thanks for the info. Do you guys think I should go with Xubuntu instead?  Im looking for this computer mainly to surf the web while in the library at school, maybe write some word docs, nothing too big I think.  Its just the old laptop is lighter and smaller than my main laptop, which makes it easy to carry back and forth.

I think you can run the normal Ubuntu with your laptop and certainly if XP was no problem. If I remember correctly it also has a decent graphics card. The latest Ubuntu has a good manager and my graphics card  and wireless broadband (a bit dinky on 7.10) work flawless.

If you are just going to use the internet and maybe open office. Perhaps you could just consider Xubuntu to keep every thing running smooth and fast. But I will warn you, Linux can be addictive and later you want more.

---

### Post by widespread on 2008-07-09
thank you everyone for the responses.  I decided I am going to try Xubuntu.  hopefully all goes well!  thanks again

---

