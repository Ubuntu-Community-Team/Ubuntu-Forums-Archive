---
title: "Any practical difference between 18.04 &amp; 20.04"
date: 2020-07-05
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-07-05
Hello everyone,

So I'm currently running Ubuntu 18.04 on my laptop, but I am putting together my first PC soon and was planning to install Ubuntu 20.04.

Are there any huge practical differences in setting it up? Obviously I know PPA's for certain software will be different, but are the packages available for 18.04 by and large the same as 20.04? and I'm assuming built in shell commands / available binaries are the same, things mostly stored in the same place in the directory tree etc?

I'm just free-styling here but if anyone can think of anything I should be aware of please do speak up!

---

### Post by sudodus on 2020-07-05
I suggest that you test Ubuntu 20.04 LTS in your current computer. There are two options, that are both rather easy

- The standard test method is to create a **live USB drive**, and run Ubuntu live from that computer (do not install it now). A variant of the live system is the persistent live system. You can create a live system with many tools. You can create persistent live systems with [mkusb](https://help.ubuntu.com/community/mkusb) in Ubuntu and with [Rufus](https://rufus.ie) in Windows.

- Another test method is to clone from a [compressed image file of an installed Ubuntu 20.04 LTS system](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS) into a USB drive with at least 16 GB. This can be done with many extraction tools + cloning tools, but maybe easiest with [mkusb](https://help.ubuntu.com/community/mkusb). The advantage with this method is that you are running a system in the same way as if it were installed into the internal drive (somewhat slower because the USB drive is probably slower than an internal drive, but otherwise the same).

---

### Post by kurt18947 on 2020-07-05
If you're planning on a Ryzen APU system, I would recommend 20.04.  Ryzen APUs are CPUs with integrated graphics, you can tell them by the G (graphics) suffix. An example is Ryzen 3 3200G. I installed a new 18.04 (20.04 was not yet out) system with the previous generation Ryzen APU and the graphics subsystem was NOT happy. A newer kernel helped but when I installed 20.04 with newer graphics components it was finally happy.

---

### Post by atomicblondy on 2020-07-05
also you can run on virtual machine

---

### Post by jcdenton1995 on 2020-07-05
Thanks, I've just this minute finished poking around 20.04 on this laptop (using a live USB) and it seems to run just fine. Amazingly it even felt faster than my proper 18.04 install, but maybe that was the newness feeling of it coupled with the retro futuristic Fossa desktop (I'm not going to pretend I knew what a Fossa was before now).

I get the feeling that fundamentally it's not changed much, or rather I get the feeling that a new user like me wouldn't get deep enough for any changes to matter, but I guess I'll find out...

---

### Post by jcdenton1995 on 2020-07-05
Thanks, I have got a Ryzen 3400G as a stand in until I get a proper GPU so good to know. Funnily enough this laptop I'm using has an old AMD APU (not a Ryzen though) and 20.04 did look much more polished in a strange way, but as I said above that may just be the feeling of newness it has to me at the moment.

I'm going to leave my laptop running 18.04, just so my new computer feels exciting and futuristic in comparison!

---

### Post by jcdenton1995 on 2020-07-05
> **atomicblondy said:**
> also you can run on virtual machine

Thank you, I would definitley try this method if I wasn't afraid my humble laptop would either melt or explode under the sheer strain!

---

### Post by uninvolved on 2020-07-05
> **jcdenton1995 said:**
> Amazingly it even felt faster than my proper 18.04 install ...

Once booted, it probably was faster. The live instance is running from RAM and not loading anything from your hard drive. So, once the OS (and apps that you opened) are in RAM, they'll run faster than they would if they were loading from disk.

I often run a live instance with persistence. Once booted and things are loaded, it's pretty speedy - and I have gobs of RAM that enable me to load most anything I want into memory.

---

### Post by monkeybrain20122 on 2020-07-05
> **uninvolved said:**
> Once booted, it probably was faster. The live instance is running from RAM and not loading anything from your hard drive. So, once the OS (and apps that you opened) are in RAM, they'll run faster than they would if they were loading from disk.



It is faster for me. Both real install on hard drive, same machine. Also less buggy comparing to 18.04 on release date. So if anyone is installing Ubuntu at this point I recommend going straight to 20.04 and forget about 18.04 unless there is some special software that must be run on 18.04 or older (16.04)

---

### Post by grahammechanical on 2020-07-05
According to this article 20.04 might not only "seem" faster it might actually be faster.

[https://www.omgubuntu.co.uk/2020/05/how-ubuntu-made-gnome-shell-faster-20-04](https://www.omgubuntu.co.uk/2020/05/how-ubuntu-made-gnome-shell-faster-20-04)

Changes between 18.04 and 20.04

[https://www.omgubuntu.co.uk/2020/04/feature-spotting-in-focal-fossa](https://www.omgubuntu.co.uk/2020/04/feature-spotting-in-focal-fossa)

Regards

---

### Post by mastablasta on 2020-07-06
benefit is new(er) kernel for new hardware.

> **jcdenton1995 said:**
> Thank you, I would definitley try this method if I wasn't afraid my humble laptop would either melt or explode under the sheer strain!

it won't. they shut down when they reach critical temp to protect the user and themselves.

i have 16 years old single core PC that reaches about 500 on CPU benchmark (Core i3 for laptops have about 4000, Ryzen 5 3500U used on laptops has about 7700) with 4 GB ram and i can run Xubuntu in virtualbox with no major issues.

i also have 8 realy old pc with AMD E-450 that has about 400 passmark score and only 2 GB ram. it too can run virtualbox but is suitable only for server or some super light DE (LXQT). if i increased the ram it will run Mate or XFCE well.

---

### Post by jcdenton1995 on 2020-07-06
> **mastablasta said:**
> it won't. they shut down when they reach critical temp to protect the user and themselves.

I was only joking about the dramatic explosion part, what I mean is I would be amazed if this pokey laptop could run a VM in any useable way, I always thought they came with big CPU overheads (but now I think about it, I'm confusing simply running a VM with running a demanding program within a VM) so based on your experiences it probably would have no problem.

---

### Post by jcdenton1995 on 2020-07-06
> **uninvolved said:**
> Once booted, it probably was faster. The live instance is running from RAM and not loading anything from your hard drive. So, once the OS (and apps that you opened) are in RAM, they'll run faster than they would if they were loading from disk.

So what your saying is a live system is loaded into RAM in it's entirety, whereas a normal install initially loads only the necessary files into RAM, with the rest being fetched on a as needed basis?

---

### Post by sudodus on 2020-07-06
The normal behaviour is that programs are loaded into RAM, when started.

In addition, a live system loads the root file system into RAM. The current live systems were originally created to boot from optical media like CD and DVD disks that are read only. So in order to have a working root file system, it must be using some read/write media, and it should not tamper with the internal drive. So a ramdrive is used, part of the RAM configured to be a drive.

One step further: A live system can be booted with the boot option 'toram'. In this case the whole content of the compressed file system is loaded into RAM at boot instead of loading programs into RAM when booted. This makes booting slower, but once at the desktop, the system will be really fast. (But you need more RAM than when running without 'toram' for this to work well.)

[hr][/hr]
It might be worth talking about a persistent live system too. In this case there is an overlay system, so that the root file system is overlayed with a file system in a file or partition for persistence. If a partition, it can be big, only limited by the size of the drive. There is a copy-on-write feature for this overlay system, so that what is created or modified in the root file system is copied to the partition for persistence. This is slower than a pure live (live-only) system, limited by the write speed of the drive with the partition for persistence, but there is big advantage: What you install and/or copy to the root file system will persist, it will be there after shutdown and reboot.

---

### Post by jcdenton1995 on 2020-07-06
Thanks, that's a really good explanation. I had been reading a little bit about this online after I read your first comment and it sounds interesting.

I'm guessing that running a system loaded into RAM wouldn't do too much to improve the performance of a given program once it is running unless that program was particularly large, and relied on resources that were left in storage and loaded periodically (in other words my understanding is that it would improve load times but wouldn't necessarily improve performance over a regular system once the program was loaded)

But I would think the system overall would *feel *much snappier if the user is rapidly moving from task to task, opening and closing many different programs as he / she goes (similar to how 20.04 felt when I gave it a whirl - but I'm not saying this was definitley the reason) would you say that sounds about right?

---

### Post by sudodus on 2020-07-06
Yes, that sounds about right :-)

---

### Post by pantazi on 2020-07-06
> **jcdenton1995 said:**
>  (I'm not going to pretend I knew what a Fossa was before now).



I think our Portuguese friends must wonder who chose the name as Fossa in Portuguese is a form of septic tank!  As for speed, I find 20.04 is slicker and quicker than 18.04

---

### Post by jcdenton1995 on 2020-07-06
> **sudodus said:**
> Yes, that sounds about right :-)

Thanks! \\:D/

---

### Post by jcdenton1995 on 2020-07-06
> **pantazi said:**
> I think our Portuguese friends must wonder who chose the name as Fossa in Portuguese is a form of septic tank!  As for speed, I find 20.04 is slicker and quicker than 18.04

Ha that must seem bizarre, especially for it to share a name with something as unexciting as a septic tank.

It reminds me of a Mitsubishi 4x4 that was sold in the UK (and perhaps some other countries) as the "Pajero". I'm not sure if Mitsubishi were aware at the time of naming it but the name translates to a naughty word in Spanish - which I won't say here just because I'm not sure if it's against the forum rules - but it begins with a W.

The same vehicle was marketed as the Montero in Spanish speaking countries, but still it seems like an odd choice by a massive multinational company like Mitsubishi.

---

### Post by mastablasta on 2020-07-07
> **jcdenton1995 said:**
>  a massive multinational company like Mitsubishi.


well, they are japanese. Have you ever seen one of their TV shows?

---

### Post by ajgreeny on 2020-07-07
Just be aware that some packages that may be important to you are available as snaps only, not as .deb packages, the major one you might come across being chromium.

This may not be a major problem to you but it does possibly mean you having to amend folders to which you have in the past downloaded files; the only destination open to you from the snap is Downloads, if I remember correctly.

---

### Post by jcdenton1995 on 2020-07-07
> **mastablasta said:**
> well, they are japanese. Have you ever seen one of their TV shows?

Ha no, I'm sort of vaugely aware they have some sort of strange, saucy, slightly sexy seedy thing going on in some shows but I've never seen one so I can't comment, as I wouldn't want to cast aspersions on our Japanese friends (at least not without seeing the evidence).

---

### Post by jcdenton1995 on 2020-07-07
> **ajgreeny said:**
> This may not be a major problem to you but it does possibly mean you having to amend folders to which you have in the past downloaded files

Right, so what your saying is if, for instance, I installed Chromium as a snap package, I wouldn't be able to select any location other than ~/Downloads as the target for anything I downloaded through the browser?

---

### Post by ajgreeny on 2020-07-07
> **jcdenton1995 said:**
> Right, so what your saying is if, for instance, I installed Chromium as a snap package, I wouldn't be able to select any location other than ~/Downloads as the target for anything I downloaded through the browser?
Yes.

I am using a chromium version from a PPA [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) so install it in the usual way using the normal package manager.

You too can try this way if you want but many users are wary of using PPAs for security reasons.
I investigate fully any PPAs that I use and feel happy that they are safe, though there is never a 100% guarantee of this so only use PPAs once you are aware of the potential risks and know how to remove them if necessary.

---

### Post by jcdenton1995 on 2020-07-07
Thanks, I use a few PPAs but generally I do a bit of an internet search and see if they are a popular one or not, and remove most once I have installed whatever it is I want to fetch from them. Either way I just use Firefox and only really download into ~/Downloads anyway so I'm okay on that front.

I'm assuming the new restriction is some sort of security measure?

---

### Post by sudodus on 2020-07-07
If you use software from a PPA you should keep the PPA. That way you will get upgrades whenever there is a new version. It works in the same way as with standard program packages from the Ubuntu repositories. If you remove the PPA your system will not be informed about the upgrades.

(If you do not rely on the PPA, you should not use any software from it.)

---

### Post by ajgreeny on 2020-07-07
> **jcdenton1995 said:**
> I'm assuming the new restriction is some sort of security measure?
Yes, I believe so, but why Downloads is any more secure than other folders in your home is a bit beyond me.

---

### Post by mastablasta on 2020-07-09
> **ajgreeny said:**
> Yes, I believe so, but why Downloads is any more secure than other folders in your home is a bit beyond me.

probably they had to set a folder where you can store user files outside of application when they created snap and chose downloads. perhaps you can change it but not from browser but from CLI?

hmm i wonder how libre office then handles this? you can store everything only in documents?

---

### Post by monkeybrain20122 on 2020-07-09
> **jcdenton1995 said:**
> Right, so what your saying is if, for instance, I installed Chromium as a snap package, I wouldn't be able to select any location other than ~/Downloads as the target for anything I downloaded through the browser?

But why would you want Chromium? It is a poorly maintained, crippled version of Chrome and a perpetual alpha. It is not meant to be a finished product (which is Chrome) If you want a Chrome like browser just get Chrome (as a .deb) from its website. Opera and Vivaldi  are other browers based on the same engine (chromium) that work well on Linux.

Many new users don't know the difference and think that Chroumium and Chrome are the same and end up with a bad experience then complain  Chrome doesn't work on Linux, just to point that out in case you don't know yet.

---

