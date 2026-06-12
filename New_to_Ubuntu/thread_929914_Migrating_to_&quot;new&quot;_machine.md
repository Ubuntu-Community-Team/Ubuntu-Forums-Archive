---
title: "Migrating to &quot;new&quot; machine"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-09-25
In the (hopefully near) future, my really old piece of junk to a new (read: slightly less old with more memory and better CPU/video card).  I will be moving the hard drive from the old to the less old machine.

Assuming that the new(er) machine does not have any hardware that is not supported, what is the likelihood that after swapping in the hard drive, that my setup will boot and run on the new machine?  Or, will this definitely require reinstallation of everything?

---

### Post by crazypenguin2008 on 2008-09-25
i had no issues swapping the 500gb hdd from a compaq with a dated  cpu into a dell box i built with a pentium III and aftermarket sound and graphics cards. 

what are the specs of the less old box??

---

### Post by LowSky on 2008-09-25
should have any huge issues, I took my laptop install, used remastersys and then installed it to my desktop, everything work fine.

I even swapped hard drives before, just uninstall any restricted drivers the "old" computer may be using, and that will keep the problems to a minimum

---

### Post by Herman on 2008-09-25
> In the (hopefully near) future, my really old piece of junk to a new (read: slightly less old with more memory and better CPU/video card). I will be moving the hard drive from the old to the less old machine.

Assuming that the new(er) machine does not have any hardware that is not supported, what is the likelihood that after swapping in the hard drive, that my setup will boot and run on the new machine? Or, will this definitely require reinstallation of everything?If you are running Hardy Heron or later, you should be able to just unplug the hard drive from one machine and plug it into another and it will boot up and run just fine. 
It may be a little slow booting up the first time in a different machine, but it should be able to reconfigure itself automatically. (Unless you are unlucky and have totally unsupported hardware). 
Hardy Heron uses the latest [Xorg 7.3]("http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-34da8c8d2432823a293ea6a0639fe8b9a24c0f77")  Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/").

As far as GRUB in concerned, just make sure you plug it in as the primary master if that's what it was in the old machine and check the jumpers on any other hard drives too. If you have cable select IDE cables then set all drives as cable select and plug the Ubuntu hard drive into the Primary Master end of a cable.
I can elaborate if required.

---

### Post by hyper_ch on 2008-09-25
most drivers are contained in the kernel... so most things should work out-of-the-box... when I upgraded my computer (new mobo, new cpu, new ram, new videocard) the only thing that complained was the switch of the onboard soundcard. I just had to set everything to use the new one as default.

---

### Post by H.Callahan on 2008-09-25
The new box will be a (Dell) 1.8Ghz P4 with 1.25Gb memory and an FX5200 GPU.  This is up from a P3 633Ghz with 384Mb memory and a built-in GPU.

Unfortunately, I am running 7.10 as I was afraid that 8.04 would push the older machine over the edge.  The current drive is the master (and only drive in the machine).  I will be putting the drive in as master (I hate CS!) with a 2nd drive as a slave.

---

### Post by HittingSmoke on 2008-09-25
> **H.Callahan said:**
> The new box will be a (Dell) 1.8Ghz P4 with 1.25Gb memory and an FX5200 GPU.  This is up from a P3 633Ghz with 384Mb memory and a built-in GPU.

Unfortunately, I am running 7.10 as I was afraid that 8.04 would push the older machine over the edge.  The current drive is the master (and only drive in the machine).  I will be putting the drive in as master (I hate CS!) with a 2nd drive as a slave.

Not really related to your issue, but with 1.25GB of RAM, are you running in dual channel? What size and how many memory modules do you have? Might run faster if you cut it down to a round number.

---

### Post by H.Callahan on 2008-09-25
No, it is not dual channel.  I have a 1Gb stick and a 256Mb stick.  Two memory slots on the motherboard.

---

### Post by crazypenguin2008 on 2008-09-25
pentuim III runs hardy fine. at least mine does.

---

### Post by egalvan on 2008-09-25
> **crazypenguin2008 said:**
> pentuim III runs hardy fine. at least mine does.

I agree, up to a point.

Point being, the amount of RAM.
And the speed of the drive.

My PIII 966mhz with 256m RAM and 4200rpm drive is rather slow.

My PIII 966mhz with 1gb RAM and 7200rpm drive is MUCH snappier.

Both are usable.

My point further being,  "CPU alone does not a fast machine make".


Yes, I have experimented swapping the 4200rpm to a 7200rpm, and the speed-up is very noticeable.
But this machine will soon be a thin-station, part of a disk-less lab running off a central server (Edubuntu).

ErnestG

---

### Post by Herman on 2008-09-26
> Unfortunately, I am running 7.10 as I was afraid that 8.04 would push the older machine over the edge. If you are running a version of Ubuntu earlier than Hardy Heron, you will not likely be able to boot to a GUI interface the first time you boot in in a strange machine. Instead, it will most likely boot to a black screen with a command line interface. You'll need to log in with your username and password. Then , you'll need to type the following command, 'sudo dpkg-reconfigure xserver-xorg'.
```
sudo dpkg-reconfigure xserver-xorg
```
It will take a few minutes and ask you a lot of questions about your hardware which most people probably wouldn't know the answers for, but try to answer them anyway. If you're not sure it's best to just leave them at the defaults. Most of the time the defaults will be correct anyway.
When you get to the end of all the questions, (about your keyboard, mouse, monitor and video card and so on), you will be returned to the command prompt.
Type 'startx',
```
startx
```I recommend upgrading to Hardy Heron as soon as you can, I don't think Hardy Heron uses any more system resources than Gutsy Gibbon, and it's a much nicer operating system. :)

---

### Post by cwmoser on 2008-09-26
Is migrating to new hardware as easy as unplugging the hard drive and connecting it up to the new hardware?

Now that would be a nice feature with Linux.

Carl

---

### Post by H.Callahan on 2008-09-26
> **Herman said:**
> 
It will take a few minutes and ask you a lot of questions about your hardware which most people probably wouldn't know the answers for, but try to answer them anyway. If you're not sure it's best to just leave them at the defaults. Most of the time the defaults will be correct anyway.Hopefully, this won't be a problem.  I am fairly computer proficient (computer tech with several certifications and the manager of IT at a governmental institution -- just not savvy with Linux). 
> **Herman said:**
> I recommend upgrading to Hardy Heron as soon as you can, I don't think Hardy Heron uses any more system resources than Gutsy Gibbon, and it's a much nicer operating system. :)I may try that then.  I was under the understanding that HH would be a bit more resource intensive than GG.  As I am running on the ragged edge of acceptability now, I didn't want to push the issue.

---

### Post by Herman on 2008-09-26
> Hopefully, this won't be a problem. I am fairly computer proficient (computer tech with several certifications and the manager of IT at a governmental institution -- just not savvy with Linux).:) Okay, you probably won't have any problems then, and Welcome to Linux! 
> I may try that then. I was under the understanding that HH would be a bit more resource intensive than GG. As I am running on the ragged edge of acceptability now, I didn't want to push the issue.I used to run Ubuntu Warty Warthog 4.10 in an old PC Chips 'Book PC', which came with Windows 98SE installed in it.
It has a 400 mhz celeron processor and only had 128 mb of RAM. at that time.
Here's an web page I made about my old 'Book PC',[herman543 - *Book PC Gets* Big *Power Supply*]("http://herman543.googlepages.com/bookpcgetsbigpowersupply2"), (LOL) :)
So far it has run every release of Ubuntu that has ever been made. 
My old 'Book PC' still works, I have it running right now. It currently has ( 256 + 128 ) = 383 MB of RAM in it and it is running Ubuntu Hardy Heron well enough. I still 'fire it up' once in a while. I don't use the 'Book PC' as my main computer any more though, I'm spoiled now that I am used to more modern computers with faster hardware.

---

### Post by Herman on 2008-09-26
> Is migrating to new hardware as easy as unplugging the hard drive and connecting it up to the new hardware?

Now that would be a nice feature with Linux. With Hardy Heron and newer, I am able to boot and run Ubuntu in a USB flash memory stick in all the computers I have tried so far that are capable of booting a USB disk.. Sooner or later I imagine I will run into one or two that Ubuntu might not work in, but so far the smallest has been my wife's new Asus EeePC, and the largest has been my Acer Aspire T310 with an ATI Radeon 9200 graphics card and an Acer 20" AL2016W LCD monitor, ( 1680x1050 resolution ). :)

---

