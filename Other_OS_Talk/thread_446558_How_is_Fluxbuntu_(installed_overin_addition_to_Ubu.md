---
title: "How is Fluxbuntu (installed over/in addition to Ubuntu)"
date: 2007-05-17
forum: Other OS Talk
---

### Post by Grafster on 2007-05-17
I recently totally hosed my home system.
Fortunately my little bro hooked me up with his old laptop. (saving $ = good)

It's a toshiba travelmate 260.
Fortunately Feisty installed fine.
Unfortunately it's slow. I'm not talking about how it takes an extra 5 seconds to start up or something I mean....

If you have firefox open and you do anything else you're looking at 15+ seconds of total freeze.
If you open or do anything with update manager (open it, type something into the search window, etc) you can basically just go get a snack and have a conversation.
It does a 20+ second shudder everytime gmail renews itself (I don't keep gmail open all the time; its just an example).

Of course since it's Ubuntu it works great and has most everything I could want. I am running an old computer and I have no complaints about Ubuntu and accept that Ubuntu is just designed for a relatively better computer than I have.

However for my set up ubuntu seems like it's a bit too slow.

I'm under the impression that it's possible to get Fluxbuntu from the Repos and run it -over- ubuntu.

My questions are
1. Is my understanding correct (i.e. you can run fluxbox and have it be just like ubuntu with the same firefox/etc installation)?
2. How painful is it? (broken/buggy/fiddling around with command lines/etc)
3. Does it handle things like wine (for utorrent when I occasionally use it) or mono (for tomboy) well?

Thanks!

---

### Post by Grafster on 2007-05-17
I see from their forums that it's not out yet.
Anyone tried the release candidate? Comments/thoughts?

---

### Post by mips on 2007-05-17
It's more than just Fluxbox on ubuntu. They try to make it as light as possible and use applications accordingly.

Install fluxbox on ubuntu and see for yourself the speed improvements you get. Next try fluxbuntu or wait for the final release if you have bandwidth issues.

Are you referring to a Acer Travelmate as I don't think Toshiba made travelmate models ? Is this it, [http://www.starcomputersinc.com/tm260.htm](http://www.starcomputersinc.com/tm260.htm)
One thing that always helps is upgrading the ram, looks like that model can go up to 1GB which could be a really cheap upgrade path and make a big difference in your computing experience.

---

### Post by Grafster on 2007-05-18
Sorry you're completely correct. Its Acer... And I got the number wrong too. 
[ Travelmate 230]("http://www.acersupport.com/notebook/html/tm230.html")

Without making a big deal of it I was asking because upgrading from dapper to feisty was the catalyst for destroying my last computer. So I'm curious about whether fluxbuntu's speed improvements are that great and whether you can run it -over- (instead of?) ubuntu or you have to dual boot.

Hmm. I hadn't thought about getting a ram upgrade (laptop ram is usually expensive etc. etc.) but obviously that would be a good solutoin.

---

### Post by RedSquirrel on 2007-05-18
> **Grafster said:**
> Sorry you're completely correct. Its Acer... And I got the number wrong too. 
[ Travelmate 230]("http://www.acersupport.com/notebook/html/tm230.html")

Without making a big deal of it I was asking because upgrading from dapper to feisty was the catalyst for destroying my last computer. So I'm curious about whether fluxbuntu's speed improvements are that great and whether you can run it -over- (instead of?) ubuntu or you have to dual boot.


Fluxbuntu is a complete OS just like Ubuntu (with GNOME), but instead of GNOME/Metacity they use Fluxbox. They also pick lightweight apps, as mentioned above.

If you don't feel like waiting for Fluxbuntu, you could setup your own lightweight version of Ubuntu by installing the server edition and then adding Fluxbox on top of that. Once you've done that, you can continue to add apps to your system as you need them, rather than having a whole bunch of apps installed that you may never use.

You can do this with the following guide, which uses the net installer:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

or you could download the server edition CD from [www.ubuntu.com]("http://www.ubuntu.com") and install that and then just do:

```
sudo nano -wB /etc/apt/sources.list
```Comment out (put a # in front of) lines with **cdrom: **in them, otherwise you'll be asked to insert the CD each time you want to install something.

Then

```
sudo apt-get update
``````
 sudo apt-get install xorg xterm gdm fluxbox firefox gksu synaptic

```Configure the X server:
```
 sudo dpkg-reconfigure xserver-xorg
```Start X so you can login to Fluxbox:
```
 sudo /etc/init.d/gdm start
```This will be a very lightweight system. I think you'll be impressed by how fast and responsive it is. :)

---

### Post by mips on 2007-05-18
Nice post [RedSquirrel]("http://ubuntuforums.org/member.php?u=209540") !

---

### Post by RedSquirrel on 2007-05-18
> **mips said:**
> Nice post [RedSquirrel]("http://ubuntuforums.org/member.php?u=209540") !


Thanks. :)

What I described is exactly the system I'm using and I _love_ it! 

It's amazing the amount of flexibility we have: everything from GNOME/KDE, to Xfce, to Fluxbox/IceWM, all with the convenience and power of Ubuntu.

 :guitar:

---

### Post by hypersire on 2007-05-19
RedSquirrel - I've been researching doing a fluxbox/rox install all night - glad I found your post! Thanks!

One  concern I have - according to the official Ubuntu book, a server install differs from a desktop install in that:

"The most significant difference is a non-preemptible server kernel with an internal kernel timer frequency of 100 Hz instead of the desktop default of 1 kHz. We'll spare you the OS theory: the idea is to offer some extra performance and throughput for server applications. In addition, the server kernel supports SMP and basic NUMA. SMP, or symmetric multiprocessing..."

Does this not mean that you end up with a system more optimized for being a server than a desktop? Isn't there a way to install the regular desktop kernel but minimize the default packages?

---

### Post by RedSquirrel on 2007-05-19
> **hypersire said:**
> RedSquirrel - I've been researching doing a fluxbox/rox install all night - glad I found your post! Thanks!

You're welcome. :)


> **hypersire said:**
>  One  concern I have - according to the official Ubuntu book, a server install differs from a desktop install in that:

"The most significant difference is a non-preemptible server kernel with an internal kernel timer frequency of 100 Hz instead of the desktop default of 1 kHz. We'll spare you the OS theory: the idea is to offer some extra performance and throughput for server applications. In addition, the server kernel supports SMP and basic NUMA. SMP, or symmetric multiprocessing..."

Does this not mean that you end up with a system more optimized for being a server than a desktop? 

Yes, I think so. Having said that, the server kernel works well in my experience and I know of several people who use it for their desktop work and like it.


> **hypersire said:**
> Isn't there a way to install the regular desktop kernel but minimize the default packages?

I don't think there's a really easy way. :(

You could wait for fluxbuntu. 

You could install one of the desktop versions (GNOME/KDE/Xfce) and then start ripping stuff out. For example, it might be possible to install Ubuntu with GNOME, install the stuff you want, and then remove "ubuntu-desktop" (the metapackage). I haven't tried this, but it would be an interesting experiment.

You could compile your own kernel.

You could try another distro, such as [www.linuxfromscratch.org]("http://www.linuxfromscratch.org") and build everything to suit your needs (this type of thing is not for everyone).

EDIT:

It's possible that the net installer ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) would allow you to choose what you want to install along with a desktop kernel. Most people just use it to install the server, but it might be worth a look. 8)

---

### Post by hypersire on 2007-05-19
Thanks for the reply RedSquirrel . Yes, I 've downloaded the "mini iso" - it's only 8mb. Since it downloads only the packges that you need during install, I assume you have control over what packages are installed.

One thing that seems unclear - is selecting "server" from the install menu the same as downloading the actual Ubuntu Server CD (i.e. you get the server kernel)? I was looking through some tutorials on the net and it looks like in older versions, instead of the server selection on the alternate CD it said "install a command line system". I am wondering if it just means install a base, command line system or if it actually does install a server-optimized kernel.

---

### Post by dustigroove on 2007-05-19
[FONT=Arial][SIZE=2][COLOR=Black]Instead of using the Server install CD, you can use the [Alternate install CD]("http://releases.ubuntu.com/feisty/") and choose the Command Line System install option.

**EDIT:**  The CLS option does not install a server optimized kernel.

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by hypersire on 2007-05-19
> **dustigroove said:**
> [FONT=Arial][SIZE=2][COLOR=Black]Instead of using the Server install CD, you can use the [Alternate install CD]("http://releases.ubuntu.com/feisty/") and choose the Command Line System install option.

**EDIT:**  The CLS option does not install a server optimized kernel.

Cheers,

[/COLOR][/SIZE][/FONT]

Ah, ok so the CLS option is still there - good to know, thanks!

---

### Post by Grafster on 2007-05-19
This is brilliant stuff.
Assuming I do the "RedSquirrel method"
How would I handle twitchy little details like
Sound (it "just worked" in Feisty)
stuff like USB drives automatically loading and working when you plug them in (is that component included in the server?)

Again, this is totally fantastic! Once I finish with some work I'll launch it, set it up and see how it goes.

---

### Post by RedSquirrel on 2007-05-19
> **Grafster said:**
> This is brilliant stuff.
Assuming I do the "RedSquirrel method"
How would I handle twitchy little details like
Sound (it "just worked" in Feisty)
stuff like USB drives automatically loading and working when you plug them in (is that component included in the server?)

Again, this is totally fantastic! Once I finish with some work I'll launch it, set it up and see how it goes.

I haven't had time to play around with sound that much. If you install gdm, I believe alsa-utils is a dependency for it, so that's a big part of the sound stuff you need. I also installed xmms.

For automounting: I don't do this. I prefer to mount things manually. You could try ivman (it's in the repositories) or there's always gnome-volume-manager (and all of its GNOME dependencies! eek!).

Have fun! :)

---

### Post by Grafster on 2007-11-24
Months later, and after detours into Xubuntu (didn't do it for me) and Fluxubuntu I finally just gave up and came back to this thread.

It's taken a few hours but now I have (almost everything working) and it's unbeleivably fast. Much faster than Xubuntu. Even synaptic feels zippy.

The only thing I haven't managed to work out yet is how to get SCIM working. (and the menus but I haven't tried all the how-toos yet).

Thanks again!

---

