---
title: "Low screen resolution after activating visual effects"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by The Silver on 2008-07-31
Hello there all of you nice linux users,

I am completely new not only to linux but also to Ubuntu.
A friend of mine recently told me about Wubi, which I now used to make myself familiar with Ubuntu. Which means for me trying out stuff, see what happens.

One of the first things I noticed was a very low reolution, which I changed easily. However, the next step made by me was trying to turn on the visual effects. Ubuntu told me to use them I need to download specific hardware drivers and so I downloaded the ones it gave me.

After rebooting the visual effects seemed to work (or so I believe. I got a new effect as I changed from one screen to another, the little two screen thingie at the bottom left). However, the resolution was very low again and couldn't be turned up. The maximal resolution was 720x640. But removing the hardware drivers removed the visual effects and made me able to select higher resolutions.

I searched the forums but only found these two threads: [http://ubuntuforums.org/showthread.php?t=258484]("http://ubuntuforums.org/showthread.php?t=258484") and [http://ubuntuforums.org/showthread.php?t=193556&highlight=low+resolution+avaible]("http://ubuntuforums.org/showthread.php?t=193556&highlight=low+resolution+avaible")
The latter might be what I need, however I am unfamiliar with the usage of the terminal and such. Therefore a step by step instuction would be probaly the best.
If somebody could help me or give me a link to a solution, it would be greatly appreciated.

Ohh, I almost forgot the general hardware information:
AMD x2 6400+
XFX8800GT
2 Gig of Ram

---

### Post by rockerphil on 2008-07-31
ok, i don't know for sure, but this is what my first attempt would be, just open up a terminal and run this:

sudo dpkg-reconfigure -phigh xserver-xorg

that will allow you to adjust the resolution of the X server itself. hope it helps,

Phil

----------------
Now playing: [Nirvana - Come As You Are](http://www.foxytunes.com/artist/nirvana/track/come+as+you+are)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by nbayiha on 2008-07-31
Silver you got a problem with your nvidia graphic card driver.
Follow those instruction, i gave in this thread and you should have your problem fixed. 

[http://ubuntuforums.org/showthread.php?t=871529&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=871529&highlight=nvidia)

---

### Post by The Silver on 2008-08-01
Both suggestions look good, but it seems that nbayihas might prevent later problems.
Still thank you, rockerphil!

Thank you for the link nbayiha, however I am having a few problems with the suggestion.

Maily with this:
> 4- Now you should log in and put your password. and go to the folder where you downloaded the nvidia drivers. mine was downloaded in home.
I am able to log in, however I do not know how to go to the folder I downloaded the drivers in. The file is on the desktop (that called home in Ubuntu?).
So if you would be so nice as to help me with the right commands, I'd be grateful.
I am new to a Linux based system, so I am unsure if the windows commands would do the trick but then, why would they? This is Ubuntu and not Windows.

So please have patience with me and my questions.

---

### Post by nbayiha on 2008-08-01
to get to my home folder i input those command. 
```
cd /home/xxxxxxx 
```

and my desktop look like this 
 ```
cd /home/xxxx/Desktop 
```

the xxx depend on everyone computer name, the name you gave while installing ubuntu.

PS: with the command ```
 ls 
```
You can list what is in the folder you are actually in .

---

### Post by northern lights on 2008-08-01
> **nbayiha said:**
> to get to my home folder i input those command. 
```
cd /home/xxxxxxx 
```
the xxx depend on everyone computer name, the name you gave while installing ubuntu.
The shell's default location is the home folder.
The 'xxx' is your _username_, the one you login with...

There also should be no need to download drivers from the nVidia website, as they are in the Ubuntu repositories.

Run ```

sudo apt-get update
sudo apt-get install nvidia-glx nvidia-settings nvidia-xconfig
sudo nvidia-xconfig

```

If the problem persists afterwards, restart X. If it still persists, post the output of ```
sudo lshw -C display
```

---

### Post by nivethan on 2008-08-01
Go to the terminal and type
vi /etc/X11/xorg.conf 
there you will find the available resolutions, in addition to the listed resolutions enter the resolution that you need (the best choice is the resolution of your monitor),then save it and restart the X server by tupeing ctrl+alt+back space
Your problem might be solved

Still Linux is having problems in identifying the exact resolution automatically but the important thing is any problem can be solved in linux!.

---

### Post by The Silver on 2008-08-01
Well, thank you for alle the commands.
However, I am having (still) a few problems.
I followed the instructions nbayiha gave me and installed the drivers. But as I boot Ubuntu the screen... well, how am I going to explain this.
Imagine the Ubuntu logo and name over the top of the screen, a few times and blurred. The lower half of the screen is normal, execpt for the fact that it is halfed (the right part is on the left side and viceversa) and that the desktop extend downward beyond the ohysical screen.
I am unsure if this is a good explaination but I hope it gives a devent idea.

Adding on to that I see part of a message saying: "Ubuntu is running in lowest graphics mode". The rest is not readable.
After rebooting a few times with the same result (also using the Esc key and selecting the "generic" Ubuntu during startup) I got a normal screen. However without high resolution and visual effects.

This "normal screen" seems to come quite randomly, I cannot see a connection between the normal booting and the "generic" selection. But they are the same, to my knowledge.

I would try out northern lights commands, but the "parted/halfed" screen problem is a little hinderance.

Anybody have a idea?

---

### Post by northern lights on 2008-08-02
Hit "Ctrl+Alt+Backspace" to kill X. Hit "Alt+F1" to log into the shell. Run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Alternatively you can run this from the Recovery Mode also. If done from Recovery Mode, reboot, then do the driver installation as explained above. If done from the regular user account, run ```
sudo /etc/init.d/gdm start
```to restart the graphical environment

---

### Post by The Silver on 2008-08-02
Thank you, northern lights. That got me back into the normal gui.
But there seem to be some problems again.
After running the "sudo apt-get install nvidia-glx nvidia-settings nvidia-xconfig" command I get this following message:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Conflicts: nvidia-xconfig but 1.0+20070502-1ubuntu1 is to be installed
  nvidia-xconfig: Conflicts: nvidia-glx


The "sudo lshw -C display" command gives me the following:
"  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GeForce 8800 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
"

I hope that helps to shed some light on my problem.

---

### Post by northern lights on 2008-08-02
mkey. My bad.

Do not install nvidia-glx. I.e run ```
sudo apt-get install nvidia-settings nvidia-xconfig
```

---

### Post by The Silver on 2008-08-02
Okay, I ran the command in combination with the others and end up with the "halved" starting screen again. Seems like it didn't make a difference.

---

### Post by northern lights on 2008-08-02
nvidia-xconfig halved your screen? You didn't just install and maybe reboot, you ran it also?

---

### Post by The Silver on 2008-08-04
Ahmm, I would guess so.
I mean the only way to install was using these commands, or so I understood, since the command offered by Nvidia doesn't do anything.

---

### Post by nbayiha on 2008-08-06
If you are still having that problem read this thread .

[http://ubuntuforums.org/showthread.php?p=5534401#post5534401](http://ubuntuforums.org/showthread.php?p=5534401#post5534401)

---

