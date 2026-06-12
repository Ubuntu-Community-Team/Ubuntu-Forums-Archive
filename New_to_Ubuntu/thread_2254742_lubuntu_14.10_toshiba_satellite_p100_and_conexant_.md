---
title: "lubuntu 14.10: toshiba satellite p100 and conexant audio not working"
date: 2014-11-29
forum: New to Ubuntu
---

### Post by max62 on 2014-11-29
I'm aware that this topic has already been covered quite extensively in this forum and somewhere on the web (sorry for that) but still I can't find a proper solution to my case so I hope that someone would be so kind and patient to help me (may be experienced the same problem!)

I'm pretty new to linux (and lubuntu) and I managed to "revitalize" my old laptop (toshiba satellite p100) with the installation of lubuntu 14.10;

everything seems working pretty fine EXCEPT the audio for which  there is no way apparently to make it working!

this is my configuration

```

max@max-Satellite-P100:~$ uname -a
Linux max-Satellite-P100 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:05:25 UTC 2014 i686 i686 i686 GNU/Linux

```


```

max@max-Satellite-P100:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
 
```

```

max@max-Satellite-P100:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: Conexant CX20551 (Waikiki)

```

I've been trying [COLOR=#333333][FONT=liberation sans]to append acpi=off to[/FONT][/COLOR] GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub and then [FONT=Ubuntu Mono]update-grub and then reboot [/FONT]but with no results at all...

I also think that my bios is updated (already flashed) as far as possible...

any help would be much appreciated!

please I need that machine "sounding" again also in linux (in win* - I do not even dare to pronounce that name here - was working pretty fine!)

thank you

max

---

### Post by ajgreeny on 2014-11-29
Look to see if pulseaudio is installed and if not, install it.  That worked for me in the past.

---

### Post by max62 on 2014-11-30
hi

thank you for the reply, I apprechiate your help

but it says ...already installed to the most recent version!
should I try to reinstall pulseaudio in some particular way?

...any other hint?

I've been reading somewhere about "alsa" but I could not figure out a proper way to deal with it...

thanks

---

### Post by mörgæs on 2014-11-30
You could try adding the volume control: 

```
sudo apt-get install pavucontrol
```

Often the problem is a muted setting which can be discovered using pavucontrol

---

### Post by max62 on 2014-11-30
YEEESSSS, it was!!!!!

...pavucontrol sorted out my problem

what a subtle well hidden thing it was....

thank you so much to you all for the great support, what an amazing forum is this one!

bye & thanks again

max

---

### Post by ajgreeny on 2014-11-30
Sorry, I thought pavucontrol was now part of pulseaudio and did not need installing separately.

---

### Post by mörgæs on 2014-11-30
You're welcome. Have fun with Lubuntu.

---

