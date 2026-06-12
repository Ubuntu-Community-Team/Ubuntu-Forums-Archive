---
title: "After Intrepid upgrade, sounds works, just not on the internet."
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Dark006 on 2008-11-02
The title pretty much says it all. Sound will work on my computer (login sounds, music players etc.) but when I try to watch something on youtube.com or somewhere else I get no sound. I've also tried 
```
sudo killall pulseaudio
```
and
```
sudo alsa force-reload
```
and then switched all my sound settings to ALSA. It did work for a while, but after a restart it doesn't work again, and I tried running those same commands again.

Anyone run into this problem? Or have a solution? I've had so many problems after the upgrade (GRRRRRR!!!!!), please help.

---

### Post by Mazza558 on 2008-11-02
It sounds like an issue with Flash.

---

### Post by Dark006 on 2008-11-02
Hm, not sure if it is a problem with flash or not. But just to be safe I completely removed it and did a fresh install, then restarted the computer. It still isn't working though...

---

### Post by zephyrcat on 2008-11-02
I don't know if this is your problem, but sometimes Flash will "steal" your audio from other applications. If this happens, you will not be able to play audio from other applications until you reboot. To solve this proble, try this:

**sudo apt-get install libflashsupport**

If killing pulseaudio works, you can add the command to your session so that it will be killed as soon as you log in. To do this, go to System > Preferences > Sessions.

---

### Post by Yashiro on 2008-11-02
> The title pretty much says it all. Sound will work on my computer (login sounds, music players etc.) but when I try to watch something on youtube.com or somewhere else I get no sound.
- Open your sound mixer (alsamixer or the gnome applet). Make sure PCM FRONTs are on max volume.
- Remove Flash. Nspluginwrapper, libflash, and any other 'fixme' libs. Install the latest Flash.
If you're running 64bit, run the script in the x64 forum on these boards.

---

### Post by bigli on 2008-11-02
Which flash package have you got installed?

I had this problem and didn't have it resolved until I updated to flashplugin-nonfree 10.0.12.36ubuntu1 

However I can't remember if the package was displayed before or after I sorted my repositories out.

---

### Post by jason.b.c on 2008-11-03
> **zephyrcat said:**
> I don't know if this is your problem, but sometimes Flash will "steal" your audio from other applications. If this happens, you will not be able to play audio from other applications until you reboot. To solve this proble, try this:

**sudo apt-get install libflashsupport**

If killing pulseaudio works, you can add the command to your session so that it will be killed as soon as you log in. To do this, go to System > Preferences > Sessions.

your fix dosen't work... 

```
jason@HP-Vectra-VL:~$ sudo apt-get install libflashsupport
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  flashplugin-nonfree-extrasound
E: Package libflashsupport has no installation candidate
jason@HP-Vectra-VL:~$ sudo apt-get install flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  flashplugin-nonfree-extrasound
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8160B of archives.
After this operation, 65.5kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com intrepid/multiverse flashplugin-nonfree-extrasound 0.0.svn2431-3 [8160B]
Fetched 8160B in 3s (2341B/s)                        
Selecting previously deselected package flashplugin-nonfree-extrasound.
(Reading database ... 132769 files and directories currently installed.)
Unpacking flashplugin-nonfree-extrasound (from .../flashplugin-nonfree-extrasound_0.0.svn2431-3_i386.deb) ...
Setting up flashplugin-nonfree-extrasound (0.0.svn2431-3) ...

```

---

