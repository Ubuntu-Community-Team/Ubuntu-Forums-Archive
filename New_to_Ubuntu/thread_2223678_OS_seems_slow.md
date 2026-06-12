---
title: "OS seems slow"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by windowsfree on 2014-05-12
Hello,

I read some threads about this, but still curious.   I have installed Ubuntu 14.04 (64bit) on a Clevo B5100 Laptop.  It has a i5 2.4ghz proc and 8 gigs of ram.  Hard drive is a 7200RPM 320 gig drive.

The OS response time seems very slow.  The only thing I have added was the updates from Ubuntu and the apps: Leafpad, Gparted, and Unetbootin.  I have added my USB printer also.
I am comparing this to a Linux Mint live CD. The CD is much quicker loading the OS and in switching apps and opening apps. My Ubuntu install is the only OS on the hard drive.  The OS speed has not changed from fresh install to when i added the above mentioned apps.

Any input gladly accepted.

Thank you,

---

### Post by veddox on 2014-05-12
While 14.04 does feel rather slower than 12.04, what you are describing sounds pretty abnormal - especially if a live disk is quicker than the installed system. Did you by any chance forget to add swap? That's the only explanation I could think up of at the moment, unless something went wrong during install.

---

### Post by windowsfree on 2014-05-12
swap partition shows 8 gig.

I just tried using the Nvidia driver as this is a Intel/Nvidia dual setup, no change.  thanks for the reply.

---

### Post by sudodus on 2014-05-12
Maybe your system needs BumbleBee? Check at these links

[http://bumblebee-project.org/](http://bumblebee-project.org/)

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by windowsfree on 2014-05-12
Thank you for the info about BumbleBee.  I tried that and it did indeed install with out issue.  Response time in OS still seems slow.  Using REDO i am making an image of this and then formatting the hard drive and re-installing.

---

### Post by sudodus on 2014-05-12
Maybe you should also check that your hard disk drive is good. Start checking the ***S.M.A.R.T.*** information. Then you can run

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number for the root partition.

---

### Post by LastDino on 2014-05-12
With 8 Gig of RAM swap will hardly matter unless you're running some program which is consuming more than 75% of that RAM. Full installed OS with normal use never really goes 1.5 Gig+ cahch which you should clear occasionally (Again if you're running system heavy things). My system only enters swap when I'm running VM with almost 1.8 GB RAM of my original 4GB.

Problem might indeed be what Sudodus pointed out. So, lets see if that helps you.

---

### Post by Danger_Monkey on 2014-05-12
For grins, you can run "top" or "htop" to see what is using system resources.  It might show you a heavy hitter that you don't want running.

---

### Post by windowsfree on 2014-05-12
I should have included that, nothing major running, compiz jumping back and forth but not using much memory.  Have system imaged, going to reinstall later today.  Thank you.

---

### Post by windowsfree on 2014-05-12
here are the screenshots.
i don't know why it shows dual screen, i only have the laptop, no other monitor hooked to VGA or HDMI ports.

---

### Post by sudodus on 2014-05-13
Maybe Bumblebee is causing the problem with the dual screen. What happens if you remove it? I think something is wrong, but I don't what it is. *I hope someone can help, who knows more* about the hardware in your Clevo B5100 Laptop and standard Ubuntu's graphics. I run Lubuntu and Xubuntu most of the time.

-o-

Have you tried Ubuntu 12.04.4 LTS? It has still several years to go (until April 2017), and it is well debugged and polished now, two years after the release.

---

### Post by windowsfree on 2014-05-13
I don't have Bumblee running, this is a fresh install.  I also found that it appears to be the OS itself as after wiping the OS, i installed Linux Mint 13 on it and it was very quick and responsive.

---

### Post by sudodus on 2014-05-13
Linux MInt 13 is based on Ubuntu 12.04 LTS 'Precise Pangolin". I think also other flavour and re-spins based on Ubuntu 12.04 LTS will work

Standard Ubuntu, Kubuntu, Lubuntu, Xubuntu,

Bento, Bodhi, LXLE ... ,

and if you are happy with Linux Mint, that's fine.

---

### Post by cwmoser on 2014-05-13
I had trouble with the nvidia drivers when I initially installed 14.04.

I did this:
- reboot and go to recovery mode
- boot up in safe mode X 
- go to command prompt and enter:
   sudo apt-get remove nvidia*
   sudo apt-get install nvidia-current
- reboot and log on normally

The symptoms I had was very slow and then the OS would freeze, then I had to press RESET button.

Carl

---

### Post by Kal P on 2014-05-13
The thing is that your laptop uses something thats called nvidia optimus. Which in windows it automatically chooses whether to use the discrete graphics card or just the on-board one, in linux on the other hand, the is no support for that from nvidia. So to do that in ubuntu, you'll need bumblebee. I think there are one or two other solutions, but I dont know about them. Basically bumblebee lets you decide when you want to use your discrete graphics card through a command. Its easy, and it works!
   Oh, and the two monitor thing, I think is from your second graphics card. Been bumping in the same problems with a lenovo Y570 laptop few days ago.

---

### Post by windowsfree on 2014-05-13
i really appreciate your input.  I did install Bumblebee before wiping and reinstalling and issue persisted.   I may try a few other distros just to be sure.  Thanks again

---

### Post by windowsfree on 2014-05-15
I reinstalled and it does seem better this time.  I am not sure what would have caused the slow down.   After the updates it still seemed ok.  i reformated the hard drive again and installed Linux Mint 13 (64bit) and this distro is quicker on my equipment.  I tried a few different desktop environments also and it is a bit more responsive.  I am closing this thread.  Thanks to all for your input.

---

