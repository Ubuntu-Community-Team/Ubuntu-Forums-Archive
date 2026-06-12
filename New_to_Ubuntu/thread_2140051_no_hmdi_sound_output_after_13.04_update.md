---
title: "no hmdi sound output after 13.04 update"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2013-04-28
Hi, as the title says, I'm unable to get sound through the hdmi cable to my TV after the update. I used to just change the output for vlc in pulseaudio, but the option for hmdi is no longer there. I have tried to reinstall pulseaudio and there is otherwise sound on the system (through the PC speakers). Any help would be appreciated and I guess I should mention that I'm not really a pro when it comes to this..

It works perfectly in windows, though windows does not work perfectly ;)

---

### Post by pqwoerituytrueiwoq on 2013-04-28
It is a bug in the kernel, you can use a [mainline kernel](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme) as a workaround

---

### Post by Mr.Kuchinawa on 2013-04-29
That did nothing, as far as I can tell.

---

### Post by 0N3 on 2013-04-30
Have you tried the alsa daily ppa

```
sudo add-apt-repository ppa:ubuntu-audio-dev/alsa-daily

sudo apt-get update && sudo apt-get upgrade
```


Worked for me.

---

### Post by pqwoerituytrueiwoq on 2013-04-30
> **Mr.Kuchinawa said:**
> That did nothing, as far as I can tell.

Did you install the kernel, that is just the program to make it easy to download?
If you run [FONT=courier new]uname -r[/FONT] and it says [FONT=courier new]3.8.0-19-generic[/FONT] you did not upgrade the kernel

---

### Post by Mr.Kuchinawa on 2013-05-02
> **pqwoerituytrueiwoq said:**
> Did you install the kernel, that is just the program to make it easy to download?
If you run [FONT=courier new]uname -r[/FONT] and it says [FONT=courier new]3.8.0-19-generic[/FONT] you did not upgrade the kernel

Thanks, it worked now. However: my wlan does not work now.. any obvious and quick way to fix this? It seems that it doesn't recognize that I have a wlan card at all.

edit: I booted 3.5.0-27-generic, and both work now. However, I guess using an old kernel is not exactly optimal..?

---

### Post by cuyabro on 2013-05-08
Thank you, installing the latest Kernel worked for me.  I had to use the instructions in the "[COLOR=#333333][FONT=Helvetica]Recovery Console Install: (Also works if you are too lazy to do the above)" section as the GUI instructions would run the script but the Kernel wouldn't get updated or no notification of new Kernel would come on.  

I haven't noticed any other issues with my PC so far.  

I can now go back to watching my shows and movies on XBMC!  

Thanks a ton!

-Elverth.[/FONT][/COLOR]

---

