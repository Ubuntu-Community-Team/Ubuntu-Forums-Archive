---
title: "question on how to save vlc settings for device name and customise, when playing dvds"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-27
Hi folks. This is probably old information, There is probably also a quicker way of doing it, no doubt within the terminal.
Well When I folllowed the advice given by Mr Freak, or it Mrs Freak :)
when using Ubuntu 8.10, vlc would automatically play a dvd when inserted.
But things didn't work so well in Linux Mint, which I changed over to.
When I put in the dvd, Vlc player would come up, but nothing would happen.
The solition was simple. It was looking in the wrong place for the dvd. I had to right click the dvd icon. then go the Volume option in properties,then setting then copy the mount point. Then in Vlc player, go to file- open disk, and either in device name or customise, (you can write it in either or both)enter the mount point for the DVD.
Then it played fine.
The trouble is when you stop, and close down, then the next day or whenever, you will have to go through the whole process again.
so does anyone know how to save the settings.
Just to be more specific. the default option in vlc-device name and customise is dvd:///dev/scd0. Wheras if i right click the properties for the dvd, and go to Volume. The mount point is /media/cdrom1
So is there any way to change the option in vlc device name and customise to /media/cdrom1.
M

---

### Post by taurus on 2008-11-27
Start up VLC.  Then look in Tools -> Preferences -> Input & Codecs and see what Default disc device is pointing at.

Otherwise, look in your /etc/fstab.

```
cat /etc/fstab
```

---

### Post by irish66 on 2008-11-27
Hi Taurus. Thank you for your response.
Here is output from terminal
martin@martin-desktop ~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b6c8d06c-e784-4acf-b4b4-cb5bd733a645 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=3fa8660b-9e13-4c0c-8549-c9dd773c2173 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
martin@martin-desktop ~ $ 

Now, i tried entering /dev/scd1 into dvd device and vcd device. The same thing has been entered automatically in device name and customise options in "play disk" but no luck as regards playing the file.
I've trie entering /media/cdrom1 in both. bUt when i check the customise option it has dvd:///media/cdrom1 instead of just media/cdrom1. So it seems to be the customise option that has to remain as /media cdrom1, and although I've tried various ways in codec options, I can't get it to not reappear as   dvd:///media/cdrom1
M

---

### Post by taurus on 2008-11-27
> **irish66 said:**
> Hi Taurus. Thank you for your response.
Here is output from terminal
martin@martin-desktop ~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b6c8d06c-e784-4acf-b4b4-cb5bd733a645 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=3fa8660b-9e13-4c0c-8549-c9dd773c2173 none            swap    sw              0       0
[B][COLOR="Blue"]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0[/COLOR][/B]
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
martin@martin-desktop ~ $ 

Do you have one or two DVD players?  Looks like you have two entries in /etc/fstab, /dev/scd0 & /dev/scd1.

---

### Post by mc4man on 2008-11-27
never tried mint so don't know what your issue with autoplay is, (though shouldn't be hard to set up).
Also the failure to play fron a device (/dev/scd0. /dev/scd1) is somewhat a mystery.
 

Any way open vlc -> tools -> preferences and in the simple menu setting -> input and codecs you'll see a box to enter the default device.

Enter /media/cdrom[COLOR="Red"]0[/COLOR] (adjust red if needed , apparently in your case go /media/cdrom1
(normally it is sufficient to set to the device, ie. /dev/scd0 or /dev/scd1, /dev/dvd or /dev/dvd1 but no great harm in setting to mount point.

The main difference will be in some on the Osd displays, from the device will show movie title, from mount point cdrom or cdrom1, maybe some other minor diffs.

Click save (important

note: the dvd:///   is correct when playing a disc in 'normal' mode (vs. dvd simple)
Just don't enter in default setting, will show up in vlc's address bar


Edit: If your mint install is using vlc 0.8.x then the idea is the same but go instead settings -> preferences -> input/codecs (in plain sight if not using 'advanced options'

again click 'save'

---

### Post by irish66 on 2008-11-28
Thanks people. Yes it's vlc 0.8.6e
I have two dvd players in computer. Well one is also a dvd burning drive
I'm a bit confused by 
"note: the dvd:/// is correct when playing a disc in 'normal' mode (vs. dvd simple)
Just don't enter in default setting, will show up in vlc's address bar"
But anyway It was set to play dvd menu. so in codecs for dvd and vcd device, i have media/cdrom1. That ends up the same in play disk device, but with dvd:/// added in "customice"result when right clicking dvd in "places" and choosing to open with VLc, vlc opens but nothing happens.
The default setting is DVD menu. I changed it to dvd , which changes the customise dialogue to dvdsimple://media/cdrom1.I  pressed ok and get the message "Unable to open 'dvdsimple://media/cdrom1'"  I closed VLc. I right clicked disk icon for DVD, choose open with vlc media player. Vlc starts up playing the dvd menu music, but jerkily. I get a black screen for a second or two, then the mesage "Unable to open "'dvd://media/cdrom1'" Then i checked "open disk" and saw that it had reverted back to dvd menu.
Anyway at the end of the day it's not a major problem. I only choose Vlc because (a) it's the one I use in Windows. As a matter of fact in Windows, I had to point it towards the correct dvd drive everytime I wanted to play a dvd. It'll be interesting to find out if the tips I got here will have a better effect in Windows (b) it was recommonded
here To use Vlc instead of Totem movie player. But as a matter of fact Totem was playing fine for me, and I have additional incetive to go back to Totem. There is a site I use which streams Real player video files. Now Mplayer is the default player for those. But although It plays the sound, I can see no picture. When I changed default player for those files to Movie player, everything was fine. When I changed it to Vlc, I was told it didn't have the appropiate codecs.
So I'm gonna try Movie player again and see what happens.
.... well it plays fine. The only thing is it plays a warning about illegal dvds before going to the actual menu, wheras Vlc goes to the menu straight away.
M

---

