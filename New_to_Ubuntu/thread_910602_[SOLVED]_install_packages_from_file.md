---
title: "[SOLVED] install packages from file"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by lengo on 2008-09-04
I had a problem discussed [here]("http://ubuntuforums.org/showthread.php?t=909839"). Basically, since xsomething wasn't recognised / installed as a result of trying to get an nVidia card working, I decided to reinstall the whole shebang. But before I did, and given my slow internet connection and not wanting to download all the packages I already had in my previous install, I did a bit of hunting and found that *.debs are stored in /var/cache/apt/archives. I copied the /apt folder to an SD card (internal card reader on my T61) thinking that I could install them without downloading them again. I installed a few--ndiswrapper, cabextract, etc.--but when I tried to do compiz files, things went wrong. I installed them by double-clicking on the *.deb file in the file explorer (is that Nautilus?) I'd get a dialogue stating whether dependencies were satisfied and then would be prompted for my password. I installed one compiz .deb, but when I went to do the second one I was informed that dependencies weren't met . . . sigh . . . So it gave me a bit of code that I entered with results shown below:
```
paul@T61-CTO:~$ sudo apt-get install -f
sudo: timestamp too far in the future: Sep  5 18:21:27 2008
```
Which apparently means that Ubuntu won't accept it to install it . . . Is there any way to do what I'm trying to do? I'd appreciate your help!

---

### Post by kjohansen on 2008-09-04
go to the dir where are the .deb files are and try

```

sudo dpkg -i *.deb

```

For future reference use AptonCD if you do this again.

---

### Post by halitech on 2008-09-04
check the date on your computer, sounds like something is off

---

### Post by lengo on 2008-09-04
> **kjohansen said:**
> go to the dir where are the .deb files are and try

```

sudo dpkg -i *.deb

```

For future reference use AptonCD if you do this again.
Thank you. Everything installed. <phew> Funny you should mention AptonCD . . . It's the first package in my list. Of course, I didn't use it because I didn't have a CD around at the time. It'd be nice if this would work with USB devices. I guess that'd be AptonUSB (which is currently in development). ;-)

One last (?) question [or should I start a new thread?]: since it installed everything, I've got two versions of the nVidia driver--'nvidia-glx-new (169.12+2.6.24.13-19.45)' and 'nvidia-glx-new-dev-envy (173.14.12+2.6.24.503-503.30)'. The latter (the envy driver) is 'broken' according to SPM. Can I just remove it?

---

### Post by kjohansen on 2008-09-05
> **lengo said:**
> Thank you. Everything installed. <phew> Funny you should mention AptonCD . . . It's the first package in my list. Of course, I didn't use it because I didn't have a CD around at the time. It'd be nice if this would work with USB devices. I guess that'd be AptonUSB (which is currently in development). ;-)

One last (?) question [or should I start a new thread?]: since it installed everything, I've got two versions of the nVidia driver--'nvidia-glx-new (169.12+2.6.24.13-19.45)' and 'nvidia-glx-new-dev-envy (173.14.12+2.6.24.503-503.30)'. The latter (the envy driver) is 'broken' according to SPM. Can I just remove it?
i would think that you could delete the envy one wihtout problem.

---

### Post by lengo on 2008-09-06
> **kjohansen said:**
> i would think that you could delete the envy one wihtout problem.
That's what I had already decided to do; rebooted, held my breath, and it worked (i.e., nothing "broke"). Now I'm left to wonder why it didn't work the first time I installed 8.04 . . . :confused:

---

