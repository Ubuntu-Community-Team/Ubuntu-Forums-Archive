---
title: "can't get 1440x990 resolution on kubuntu with nvidia 7300LE"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by jasonwatkins on 2008-12-02
i go to the x server and it only offers me a default of 1024x768, so i googled around a bit and found a possible edit to the xorg.conf file, which was this ..

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth     24
                Modes "1440x990" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

which i did, and rebooted, and it still wouldn't offer me 1440x990.  i've got the recommended nvidia driver (177) installed but i'm a bit stumped.

any help greatly appreciated - thanks :)

---

### Post by anotherdisciple on 2008-12-02
Are you using Intrepid? I don't have a Nvidia card... but I heard the intrepid drivers are an issue.

---

### Post by jasonwatkins on 2008-12-02
i don't think so, but then to be honest i wouldn't know how to find out ..

i've only installed kubuntu this morning after having been on Windows for a fortnight to play (and complete) the new Tomb Raider game ;)

I was on my way back to linux mint until i discovered that kubuntu was KDE enabled ...

---

### Post by m_l17 on 2008-12-02
Give this a try:

[http://ubuntuforums.org/showthread.php?t=975058]("http://ubuntuforums.org/showthread.php?t=975058")

---

### Post by jasonwatkins on 2008-12-02
thanks for the link.  i tried it, but it didn't work - it defaults to 800x600 and now and only gives me the 'auto' option in x-server

this is my xorg.conf file

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       47
        VertRefresh     59

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection      "Display"
        Depth           24
        Modes           "1440x990_70"
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

---

### Post by jasonwatkins on 2008-12-02
if anyone is able to help they've got about an hour and 20 minutes as i'm downloading the KDE version of linux mint now.

(patience was never a strong point :D)

---

### Post by jasonwatkins on 2008-12-02
well it's intensely annyoing since even linux mint with KDE doesn't like my monitor

no KDE and everything is fine ..

KDE and everyone hates me ..

if anyone has any ideas for kubuntu still i'd be very grateful .. i do prefer that

---

### Post by stchman on 2008-12-02
> **jasonwatkins said:**
> i go to the x server and it only offers me a default of 1024x768, so i googled around a bit and found a possible edit to the xorg.conf file, which was this ..

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth     24
                Modes "1440x990" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

which i did, and rebooted, and it still wouldn't offer me 1440x990.  i've got the recommended nvidia driver (177) installed but i'm a bit stumped.

any help greatly appreciated - thanks :)

Install nvidia-settings as it will let you pick the resolution you want.

---

### Post by jasonwatkins on 2008-12-02
it won't though - i've already got the latest x-server installed and even if i go into the terminal and type "sudo apt-get install nvidia-settings" it still says i have the latest version.

the maximum resolution it offers me is 1360x768

---

### Post by jasonwatkins on 2008-12-03
this actually happened when i tried mandriva with KDE as well so it does make me wonder if KDE will actually work with my monitor at all

---

### Post by jasonwatkins on 2008-12-03
well i re-installed and tried the 173 nvidia driver and that was even worse - only offered me 640x480 as a resolution.

it surely can't be this difficult to work out ..

---

### Post by overdrank on 2008-12-03
Hi and I do not use KDE but have you tried booting into recovery mode and use the xfix option.
Recovery mode is usually the second choice from the grub, after using the xfix option to correct the graphics you should be offered a choice to continue to boot normally. Hope this helps.

---

### Post by jasonwatkins on 2008-12-03
i'll give it a try, thanks.

i've just tried the command

```
sudo dpkg-reconfigure xserver-xorg
```

and all it does is offer me various options to correct the keyboard rather than the monitor.

but i'll try your suggestion now

---

### Post by jasonwatkins on 2008-12-03
doesn't do anything - going in to the xserver config it still never offers me 1440x990 resolution

the maximum resolution offered is still 1360x768

it's frustrating because i know full well if i ditch KDE and go back to 'regular' linux with compiz it will work perfectly, so i can't really see how KDE is causing such a problem

---

### Post by jasonwatkins on 2008-12-03
actually if anyone is reading this then don't worry too much - i'm just going to re-install windows and be done with it as i really haven't got the patience today.  i don't really understand linux to the degree i can find the solution myself, so i'm just going to go back to windows and maybe try again next year and hope someone else has the same problem and solves it.

---

### Post by jasonwatkins on 2008-12-04
well i actually managed to solve the problem in a roundabout way.

i re-formatted and re-installed mandriva and again had the same problem.  someone on the mandriva forum suggest i change to the 1440x900 (not 990, my mistake) resolution and just restart the x-server with ctrl-alt-backspace which i swore blind i'd been doing.

anyway, did that and nothing happened.  tried to get in to the nvidia settings to see if i could alter the resolution but i got an error about the twin display being set to false or something like that.

manually altered the xorg.conf file and changed the flag to true and go in to the nvidia settings and changed the setting to 1440x900 .. and it worked!.

so, i saved the xorg.conf file to my memory stick, reinstalled kubuntu and replaced the xorg.conf file with the mandriva one and it worked !

i have 1440x900 resolution and i'm happy.

although there are a few minor niggles, but overall it's been solved.

---

