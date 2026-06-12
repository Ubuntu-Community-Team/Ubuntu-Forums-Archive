---
title: "[SOLVED] 8600 GT install (Pulling my hair out!)"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by drewcoon on 2008-07-03
Hey, I've been trying to install drivers for my NVidia 8600 GT card all day, and I'm down to tutorials and still having problems.

Basically, the driver installer wants me to stop the X server before it can install... The problem is that when I sudo /etc/init.d/gdm stop, I get an "out of range" message on my monitor (I guess the terminal runs at a resolution my monitor does not support). Also, none of the ctrl + alt + f1>f6 combonations seem to be working either for changing over to a terminal.

I had the driver working successfully under safe mode by using root terminal then resuming normal boot, but when I restarted back to a normal boot I was stuck at an 800x600 resolution with no drivers. I guess I can't install with safe mode root terminal?

Also, I've tried enabling the driver via the restricted drivers manager, but when I restart I log on and the box is unchecked again, what's going on?

I think the most urgent question is how to stop X without getting an out of range error... Can anyone help? Thanks in advance :)

---

### Post by phidia on 2008-07-03
I just answered this in another post so-hopefully this will work in your situation.
Try /sbin/init 2 
Not sure why CLI isn't working when x is killed though so that may not work either.

---

### Post by drs305 on 2008-07-03
Have you tried installing the nvidia drivers with envyng-gtk? It's in synaptic and works well. I don't know if it will work with the problem you are experiencing but might be worth a try if phidia's solution doesn't work.

---

### Post by Rocket2DMn on 2008-07-03
+1 for EnvyNG in this case.  Manually installing the newest drivers from Nvidia's website only worked about 1/2 the time for me, but EnvyNG has worked well for my 8600 GT, esp. with regular kernel upgrades in Hardy.  If you take this route, here is a link from the wiki: [uhelp]community/NvidiaManual[/uhelp], and a link direct to their site: [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

Be sure you remove the manually installed driver first:
```
sudo sh NVIDIA* --uninstall
```
Where NVIDIA* will call your installer .run file.

---

### Post by ZabiGG on 2008-07-03
Hi,

> **drewcoon said:**
> The problem is that when I sudo /etc/init.d/gdm stop, I get an "out of range" message on my monitor (I guess the terminal runs at a resolution my monitor does not support).

OK, so I take it you tried running the command from a terminal window, but not from a main terminal (tty), since the tty keys don't work.

> **drewcoon said:**
> I had the driver working successfully under safe mode by using root terminal then resuming normal boot, but when I restarted back to a normal boot I was stuck at an 800x600 resolution with no drivers. I guess I can't install with safe mode root terminal?

Yes you can. Once you've finished installing, you'll restart and have an 800x600 resolution because the driver is not initialed yet.

You simply have to run a virtual terminal and enter:

```
sudo nvidia-xconfig
```
or
```
sudo nvidia-xconfig --no-logo
``` (if you don't want the logo)

and restart one last time. You can then use nvidia-settings to adjust your settings (if it's not already on your system, you can use Synaptic and search for nvidia-settings or enter the following line in a terminal

```
sudo apt-get install nvidia-settings
```

> **drewcoon said:**
>  Also, I've tried enabling the driver via the restricted drivers manager, but when I restart I log on and the box is unchecked again, what's going on?

That's because you had not initialized the driver as described above.

> **drewcoon said:**
> I think the most urgent question is how to stop X without getting an out of range error... Can anyone help? Thanks in advance :)

The only way to do that is to be out of a graphic interface and inside of a TTY (CRTL-ALT F1-F6)

When you log in after, if the computer went into low graphics mode in the previous session, make sure you click Session and GNOME on the welcome page where you log on (it defaults to Last session, so if you don't do that, you'll keep rebooting into safe graphics mode and you'll use the vesa driver instead of the installed nvidia driver). 

Hope this helps,

Z.

---

### Post by phidia on 2008-07-03
The OP said:
> Also, none of the ctrl + alt + f1>f6 combonations seem to be working either for changing over to a terminal

/sbin/init 2 also takes you out of GUI

---

### Post by drewcoon on 2008-07-03
Alright, I'll give some your ideas a try tomorrow, it's quite late where I am :p... I'm posting from my Windoze with drivers installed and the card has quite a bit of power :)

Can't wait to get it working under Ubuntu!

---

### Post by drewcoon on 2008-07-04
THANKS! I managed to stop X from terminal without getting the out of range message, Ran uninstall from Envy first, then the driver .run file to make sure the driver was totally gone, then I went through the driver .run installer, started X again and everything is working great.

I think the mistake I made was that I tried manually installing a driver from Envy (it wouldn't autodetect my card), and then I was using the driver installer to install the driver over top of the already existing one. Also when I stop X while running at 800x600 I get out of range, if I switch to 640x480 however, that doesn't happen for some reason.

I'm running Nexuiz on Ultimate detail and getting about 70 fps... This card rocks :)

Thanks again!

---

