---
title: "Help! Changed video driver and now have blank screen"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by Electronicman on 2011-12-03
I have a Dell XPS 400 with a Nvidia 7300LE video card, with dual boot Win XP and UB 11.10, in reading some of the articles I was tempted to change the drivers so that I could use Unity 3D. Now upon booting,  the monitor is going into standby. I tried booting in recovery mode and I can see a screen with some options, but the keyboard is unresponsive.

After trying re booting a few times, still nothing is happening. After booting XP and then trying UB again I was able to get an option screen in recovery mode that let me fix bad files. Tried that and again the monitor is going into standby.

Is there anyway to get to change the video driver back to, I guess generic? or is it easier just to reload a fresh version of UB 11.10. Since I am a Noob to UB I do not have any files than need to be saved, and UB is on it own Hard Drive, I just have to remember all the goodies I have loaded

Thanks
David

---

### Post by androssofer on 2011-12-03
> **Electronicman said:**
> I have a Dell XPS 400 with a Nvidia 7300LE video card, with dual boot Win XP and UB 11.10, in reading some of the articles I was tempted to change the drivers so that I could use Unity 3D. Now upon booting,  the monitor is going into standby. I tried booting in recovery mode and I can see a screen with some options, but the keyboard is unresponsive.

After trying re booting a few times, still nothing is happening. After booting XP and then trying UB again I was able to get an option screen in recovery mode that let me fix bad files. Tried that and again the monitor is going into standby.

Is there anyway to get to change the video driver back to, I guess generic? or is it easier just to reload a fresh version of UB 11.10. Since I am a Noob to UB I do not have any files than need to be saved, and UB is on it own Hard Drive, I just have to remember all the goodies I have loaded

Thanks
David

I had a similar problem before, however the solution requires you to boot into command line. 

when you boot up and everything should have loaded, press 

ctrl + alt + F1

this will take you to tty1. if it worked, it will load an all black screen saying 'login: ' and a blinking cursor.

just type your username, then hit enter, then your password, hit enter. and thats you logged in. 

then do:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

this backs up your xorg.conf file, but also renames it, so x11 wont find it. This files is how it knows which drivers etc to load. so after we do this when you reboot it should force ubuntu to use generic drivers...

```
sudo reboot
```

restarts your computer.

---

### Post by Electronicman on 2011-12-03
Hi Androssofer,

I followed your instructions and it did not appear work, but I re booted several times and at least I got the Ubuntu logo to come up before the monitor shut down.

I was then able to get to the boot menu and when I tried booting from previous versions I was able to get Ubuntu back to normal.

Now the nest question is how do I get it to boot normally?, if I select the normal version in the boot menu it results in a blank screen, but I works in a previous version.

Thanks for your help
David

---

### Post by androssofer on 2011-12-04
> **Electronicman said:**
> Hi Androssofer,

I followed your instructions and it did not appear work, but I re booted several times and at least I got the Ubuntu logo to come up before the monitor shut down.

I was then able to get to the boot menu and when I tried booting from previous versions I was able to get Ubuntu back to normal.

Now the nest question is how do I get it to boot normally?, if I select the normal version in the boot menu it results in a blank screen, but I works in a previous version.

Thanks for your help
David

Think i know how to fix it, (proceed with caution):

so you get the boot menu and it looks something like like this (version numbers may vary):

```
ubuntu, with Linux 2.6.32-22 Generic
ubuntu, with Linux 2.6.32-22 Generic (recovery mode)
ubuntu, with Linux 2.6.32-21 Generic
ubuntu, with Linux 2.6.32-21 Generic (recovery mode)
```

and you select the second option, and it works fine?

if so, make a note of the version number on the first entry (the broken 1), in this example its 2.6.31-22. then boot into the second option (the working one).

Once its booted, open up "synaptic package manager" 

System > Administration > Synaptic Package Manager

and in the 'quick search' box at the top search for that version number, ignoring the numbers on the end, eg: 2.6.32

it should bring up a number of entries. you want to look for 3 entries related to the 1st option (the broken 1). make sure the complete version numbers match.

```
linux-headers-2.6.32-22
linux-headers-2.6.32-22-generic
linux-image-2.6.32-22-generic
```

now for each of these right click and select 'mark for complete removal' and hit apply. that will remove them from your system. then reboot and the 1st option will be the working 1. 

then run a system update, and it should download the latest version again for you, but this time it should work :-)..

---

### Post by Electronicman on 2011-12-04
Hi Androssofer,

I tried your further suggestion and I deleted the version which was giving me trouble (3.0.0.13) and upon rebooting it worked, everything is back to normal.

However, there is always a however, I am unable to to update from the version that works (3.0.0.12). I tried selecting the update manually and it looks as if it is loaded but ever time I boot it shows version 3.0.0.12. I am going to see over the next day or so if I get an update.

Thanks for your help, at least I was able to record the software I have uploaded, and save the few wallpapers I had, so that if there is need to do a fresh install I can quickly get back to where I was.

David

---

### Post by androssofer on 2011-12-05
Humm...

how annoying... try this command in terminal:

```
sudo apt-get update
```

or did you already?

and at least you got it in a working state to get your stuff backed up. :-)

---

### Post by Electronicman on 2011-12-06
Hi Androssofer,


Just a quick update.

I tried the terminal command, and got some updates, then I tried system update and got more updates, but it did not change anything. So I took the bull by the horns and deleted update #12 in the hope it would force #13. Well that was disaster. So then I reloaded the whole system and connected to the Internet for the automatic updates. Still did not work, so I reloaded again and used the format disk option, and now I am back in business.

I am happy with the reload as somethings that were not working right now work, and the whole thing is faster.

Thanks for your help
David

---

