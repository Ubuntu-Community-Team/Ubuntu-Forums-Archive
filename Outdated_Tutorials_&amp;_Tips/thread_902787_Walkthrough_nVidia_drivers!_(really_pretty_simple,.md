---
title: "Walkthrough: nVidia drivers! (really pretty simple, if you put it that way...)"
date: 2008-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Lexicon101 on 2008-08-27
Firstly, go to the official nVidia website and download the official linux drivers. Of course nv's nice and all.. but I wouldn't use it over the real thing. Once you download the driver file (into your home folder), right click on it in nautilus (file browser), click properties, then permissions, checking the box that says "allow executing the file", then type into a TTY session ctrl+alt+f1-f3 (ctrl+alt+f7 to get back to GUI) and type in ```
sudo /etc/init.d/gdm stop
``` Which will stop your x-server.. (DON'T DO ANY OF THIS UNTIL YOU KNOW THE WHOLE PROCESS, BECAUSE TURNING BACK ON YOUR GRAPHICS COMES AT THE END!)
(Also note that this will be a text-only display! Remember or write down all the commands.) then hit ```
ls
``` to list the files in your home folder. Find the one with "nvidia" in it, and hit "sudo ./*nvidia filename*" it should install the "nvidia" driver on your computer. when it asks you whether or not you want to replace the existing "xorg.conf" file, let it do so. once that's done, type in "sudo /etc/init.d/gdm start" which will turn back on the graphical interface, allowing you to login again. (sorry. it logs you out of everything but the commandline part of ubuntu. save everything before you turn off gdm.) If your controls work perfectly in regards to the mouse and keyboard, rejoice, you're done! if your mouse isn't scrolling, or it's behaving funny.. you may have to hit alt+f2 (You'll still be in graphical mode after hitting this one. it's a nice little tool.), and type in ```
gksu gedit
``` then open your xorg.conf file (Usually in the "/etc/X11/" folder), looking somewhere other than me about how to fix that, if copying your "pointer" section doesn't fix it.
(Copying the pointer section worked for me, since I had it set up right in a previous xorg.conf file..)


**Now, in case of kernel update**, remember that the nvidia driver will NOT work without reinstallation. This is expected, so expect it. In this case, you'll be in CLI mode. Your previous driver installer will work just fine, I like to check for updates occasionally, just to be with the newest version.

Always make sure, with a new executable comes making it executable before trying to.. well.. execute it. With GDM (the graphical display) working, simply right click the file in the file browser and click properties, set it executable. In CLI: have the file in your home directory or know the directory it's in.. Then do "cd "/path/to/driver/" before finally setting it executable. Do this with "sudo chmod a+x "{driver file name}"" (You can use the ls command to once again list it exactly).

Now, execute the file by simply typing the filename into the command line. It will say there's a previous version installed, and ask to write over it. Do so. It shouldn't need to overwrite the xorg.conf file, as the NVIDIA driver's still being used. Don't let it and save some hassle.

So basically, set the file executable in the file browser, or use sudo chmod a+x "nvidiadrivernamehere", stop gdm if it's started (sudo /etc/init.d/gdm stop), then execute it, overwriting the driver, but not the xorg.conf. Then, start GDM back up (sudo /etc/init.d/gdm start)

If you overwrite the xorg configuration file (conf) just restore the backup. Look in the file browser (using alt+f2, typing in gksu nautilus and executing to get a root file browser. Needed for editing /boot/ files.) in "/boot/grub/" in list mode for the latest thing resembling .backup or .bak1 or something, listing files by date changed. delete the new xorg.conf, changing the name of xorg.conf.bak to xorg.conf.

So, in essence,
1: Download driver. Set as executable.
2: turn off graphics, going into only command line.
3: list files, execute driver installer.
4: follow installer's instructions, allowing it to replace your xorg.conf.
5: restart gdm. Hope everything goes smoothly.
6: *contingent upon condition in last step being met* DANCE! YOU WIN!
:lolflag:

To reinstall,
1a: change file to executable if gdm's booted up through the properties prompt.
1b: do a sudo chmod a+x {filename} if it's not.
2a: kill gdm server (sudo /etc/init.d/gdm stop in CLI (ctrl+alt+f1)) proceed to 2b.
2b: execute file. (sudo ./NVIDIA-x86-173.x.x-pkg1.run (or -x86_64-))
3: Follow prompts, letting it overwrite the old driver. Don't let it overwrite xorg.conf unless it's been changed to use another driver.
4: Start gdm. (sudo /etc/init.d/gdm start)
5: Rejoice! If it worked before, it should work now! If it doesn't, despair. Boot from a livecd if you have one, or use a computer at a library to come here and flame me. It happens frequently.


And.. Mods, please sticky this. I wish I'd known then what I know now. Don't make people search it out more...
(This is a post I basically copy-and-pasted from a thread from someone having problems with a very old nVidia card.. He ended up just getting a new computer, but.. Well, I think it's a good guide.)

---

### Post by chrisccoulson on 2008-08-27
Why not use the restricted drivers manager (System -> Administration -> Hardware Drivers, then enable NVIDIA driver), or for the newer driver, use Envy (available in the repositories). Both of these automate the installation of the driver.

Why do you need to manually install from the NVIDIA website?

---

### Post by Twinflower on 2008-08-27
Nice guide, but I dont get the command line-part to work.

When exiting the GDM, all i get is a blinking cursor underneath the [OK]-list.
It's not a prompt, and it basicly just feels like text editing. 

So, what did I do wrong?

---

### Post by Ewingo401 on 2008-08-27
This process does not work with the nvidia Geforce 6100 as per my personal experience.  I had much better luck using envy for that particular model.

---

### Post by damis648 on 2008-08-27
> **chrisccoulson said:**
> Why not use the restricted drivers manager (System -> Administration -> Hardware Drivers, then enable NVIDIA driver), or for the newer driver, use Envy (available in the repositories). Both of these automate the installation of the driver.

Why do you need to manually install from the NVIDIA website?

Seriously, +1. I would highly recommend this over the long method above.

---

### Post by northern lights on 2008-08-27
> **chrisccoulson said:**
> Why not use the restricted drivers manager (System -> Administration -> Hardware Drivers, then enable NVIDIA driver), or for the newer driver, use Envy (available in the repositories). Both of these automate the installation of the driver.

Why do you need to manually install from the NVIDIA website?

+1. I concur.

> **Lexicon101 said:**
> And.. Mods, please sticky this. I wish I'd known then what I know now. Don't make people search it out more...
(This is a post I basically copy-and-pasted from a thread from someone having problems with a very old nVidia card.. He ended up just getting a new computer, but.. Well, I think it's a good guide.)

Rather than seeing this stickied, I can't help but think this thread to be nowhere short of misleading and half-bred.

If of all graphics devices any should work out of the box they should have an nvidia chipset.
Which is only partially relevant as the driver the OP proposes to install is in the repositories. I.e. both support exactly the same devices. They are identical.

> **Lexicon101 said:**
> ...and type in ```
gksu gedit
``` then open your xorg.conf file, looking somewhere other than me about how to fix that, if copying your "pointer" section doesn't fix it.
Without words...

---

### Post by Twinflower on 2008-08-27
Well.
I tried the envy as well

```
sudo apt-get install envyng-gtk

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
'
```


What is this supposed to mean?

(I have a nv 8800 gts, using two lcd's on DVI.
Yesterday it all worked perfect with twinview and even nvidia-settings started up without whining about restarting the x driver.
Now i have cloned outputs and nvidia-settings refuses to start no matter what I to)


edit: When losing that perfect working setting, i was trying to enable both dual screen and a TV-out. (i know now that its not possible)

---

### Post by northern lights on 2008-08-27
> **Twinflower said:**
> ```
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
'
```

What is this supposed to mean?
 You either had apt-get/aptitude running in another terminal, the update manager running or Synaptic open, which caused a conflict.

> **Twinflower said:**
> I have a nv 8800 gts, using two lcd's on DVI.
Yesterday it all worked perfect with twinview and even nvidia-settings started up without whining about restarting the x driver.
The 8800 GTS is supported by the nvidia driver for linux, which renders envy superfluous. Check [here]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html"). The driver, again, is in the repos.

"System > Administration > Hardware Drivers"...

---

### Post by Twinflower on 2008-08-27
> **northern lights said:**
> You either had apt-get/aptitude running in another terminal, the update manager running or Synaptic open, which caused a conflict.
ding ding ding
Synaptics were running :)

Thanks

---

### Post by northern lights on 2008-08-27
> **Twinflower said:**
> ding ding ding
Synaptics were running :)
Thanks
Still, note (see above) that envy is not needed at all.

---

### Post by Lexicon101 on 2008-08-27
Sorry for taking a bit to respond.. My experiences with the "Hardware Drivers" bit hasn't been awesome, and I dislike seeing some script working what I could do myself. It's not that there aren't other ways to do it, just that they don't work for everyone, and this way really needs a more put-together help topic.

---

### Post by Twinflower on 2008-08-27
> **northern lights said:**
> Still, note (see above) that envy is not needed at all.
yeah, maybe.
But right now I am *thrilled* to inform you all that envy really fixed all my problems with the drivers. I dont know for how long i've been struggling to get this thing working, and envy did the job just like that.

So, thanks.

---

### Post by Lexicon101 on 2008-08-27
> **Twinflower said:**
> Nice guide, but I dont get the command line-part to work.

When exiting the GDM, all i get is a blinking cursor underneath the [OK]-list.
It's not a prompt, and it basicly just feels like text editing. 

So, what did I do wrong?

Nothing at all. It's supposed to be just text. Sorry if I didn't clarify that well.. That's what I meant by "turning back on your graphics comes at the end"
Anyway, when you get to that, type in ls and hit enter and find the nVidia driver..
type in "sudo ./{nvidia driver filename}" and hit enter.. There will be a prompt there, and it'll walk you through the rest. Then once you've finished with that, type in the gdm stop bit, but with start instead (You can usually just hit the up key a couple times and change it to start..)

EDIT: I'm glad to hear you don't have to do any of this. Have fun with ubuntu.

---

### Post by northern lights on 2008-08-27
> **Lexicon101 said:**
> Nothing at all. It's supposed to be just textHe didn't get a prompt, i.e. nothing along the lines of```
user@host:~$
```He would have had to hit 'Alt+F1', log into the shell and then follow your tutorial...
:roll:

---

### Post by Lexicon101 on 2008-08-27
> **northern lights said:**
> He didn't get a prompt, i.e. nothing along the lines of```
user@host:~$
```He would have had to hit 'Alt+F1', log into the shell and then follow your tutorial...
:roll:

Ah. Not logged into shell. Sorry, I have my setup so that GDM doesn't start on startup, I'll fix it.. Should be just "Hit ctrl+alt+f1" instead of just typing gdm stop into terminal, right?
I'll verify this.

EDIT: Well, I don't have a good way to verify this, it would take me a minute to search out changing GDM to start on startup, and I don't want to make that happen in the first place, so..

---

### Post by t0p on 2008-08-27
> **chrisccoulson said:**
> Why not use the restricted drivers manager (System -> Administration -> Hardware Drivers, then enable NVIDIA driver), 

Yeah, wouldn't that be wonderful?  Except System > Administration > Hardware Drivers appears to have gone bye-bye.

I've got a pretty aged machine - my card's TNT2 Riva something, a real legacy card, right?

Well, using the 2.6.24-16 kernel, Hardware Drivers has no problem sorting me out.  But I got a software update today, which delivered the 2.6.24-19 kernel... and suddenly Hardware Drivers has nothing for me!

So, I'm still using the old kernel for now.  I tried 1 driver package from NVIDIA's legacy page (NVIDIA-Linux-x86-96.43.07-pkg1.run) and it failed.  I've got to try the other 1 - NVIDIA-Linux-x86-71.86.06-pkg1.run - which I'm going to do tomorrow, and if that doesn't work I don't know when I'm going to be able to use 2.6.24-19.  Cos 800 x 600 res is no fun!
:(

---

### Post by Lexicon101 on 2008-08-27
> **northern lights said:**
> He didn't get a prompt, i.e. nothing along the lines of```
user@host:~$
```He would have had to hit 'Alt+F1', log into the shell and then follow your tutorial...
:roll:

... and alt+f1 = main menu.
I already had something about a TTY session in there, I just took out the bit about the terminal just now.

---

### Post by Twinflower on 2008-08-27
well, now that we got that sorted out.
does anyone know anything about dualscreen + tvout?
Will it be available some day somehow? 

So far i havent even got singlescreen + tvout to work, but i'm still learning.
(Been using linux for 3 days now^^)

---

### Post by Lexicon101 on 2008-08-27
I think the "NVIDIA X server settings" application in "Applications->System Tools" Should help with that... Although I don't have much experience with that kind of thing myself.

---

### Post by northern lights on 2008-08-28
> **Twinflower said:**
> well, now that we got that sorted out.
does anyone know anything about dualscreen + tvout?
Don't take me for granted, as even firmware can be hacked, but with a single card I highly doubt this to be possible under any OS.

You'd at least need SLI to pull off three screens, I think.

Anyway, today's standard graphics chips don't support three screens.

---

### Post by philinux on 2008-08-28
I used this how to which is very precise. 
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

Anybody following this needs to print it out.

You also have to remember that after any kernel update you have to reinstall the drivers by following part of that howto as you're back to low graphics mode. This is a royal pain.

I reinstalled and stuck to the drivers in the repo.

Some people obviously cannot do this.

---

### Post by Twinflower on 2008-08-28
> **northern lights said:**
> Don't take me for granted, as even firmware can be hacked, but with a single card I highly doubt this to be possible under any OS.

You'd at least need SLI to pull off three screens, I think.

Anyway, today's standard graphics chips don't support three screens.
It's possible under Windows.
(however, the tv-out is a clone from one of the monitors, which still is exactly what i'm after in ubuntu as well.  Can't see why that's so difficult)

---

### Post by northern lights on 2008-08-28
> **Twinflower said:**
> It's possible under Windows.
(however, the tv-out is a clone from one of the monitors
aight. that ain't three screens and is in theory much more possible. Never done it under any OS, can't give input on that one, as none of my graphics chips (Geforce 4 Ti on the desktop, ATI Radeon Mobility 9600 on the laptop) support it.

---

### Post by Lexicon101 on 2008-08-29
> **philinux said:**
> I used this how to which is very precise. 
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

Anybody following this needs to print it out.

You also have to remember that after any kernel update you have to reinstall the drivers by following part of that howto as you're back to low graphics mode. This is a royal pain.

I reinstalled and stuck to the drivers in the repo.

Some people obviously cannot do this.

Fun stuff. I just thought there were too many threads with the equivalent of "Help nvidia drivers!", then a bunch of people saying things like "You need to install the drivers from the nvidia website." Offering no good explanation of where to go from there, how to stop the x-server, how to make the file executable.. How to find the file easily once in CLI, then how to actually execute it..
And the link there is a bit technical, which some people don't like.. Of course, I would have loved finding that one.. Anyway, I got mine working, and now know how to do it myself (I always use this method, myself..)
I figured I'd help out.
I'll fix it to help with re-installation in the event of kernel update.

---

### Post by northern lights on 2008-08-29
> **Lexicon101 said:**
> Fun stuff. I just thought there were too many threads with the equivalent of "Help nvidia drivers!


Agreed, this is a neverending topic indeed.

I'd say though, the crux lies in the fact that there's more than just a few different chipsets out there which require different handling also...

---

### Post by Lexicon101 on 2008-08-29
> **northern lights said:**
> Agreed, this is a neverending topic indeed.

I'd say though, the crux lies in the fact that there's more than just a few different chipsets out there which require different handling also...

True. I guess I should also put in something about legacy drivers..
Also, it needs major cleaning and code tags.

EDIT: also, I think the summary part should be at the beginning, to break it down a little and make it easier to remember..
I'll make this a very good tutorial yet.

---

