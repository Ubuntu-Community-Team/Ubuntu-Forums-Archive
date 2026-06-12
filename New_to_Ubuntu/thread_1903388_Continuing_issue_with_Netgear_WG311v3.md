---
title: "Continuing issue with Netgear WG311v3"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by rem1100 on 2012-01-02
With help from this forum I was able to get the wireless connection to work. There is still one lingering issue. The connection works fine but every time I reboot I must uninstall and reinstall the inf file. Once I do this a connection to our wireless network is established in a few seconds and so far has worked properly until the computer is shut down. I have to believe there is some setting that is not right but have no idea what it is. 
Any help is appreciated.
Jeff

---

### Post by plucky on 2012-01-03
> **rem1100 said:**
> With help from this forum I was able to get the wireless connection to work. There is still one lingering issue. The connection works fine but every time I reboot I must uninstall and reinstall the inf file. Once I do this a connection to our wireless network is established in a few seconds and so far has worked properly until the computer is shut down. I have to believe there is some setting that is not right but have no idea what it is. 
Any help is appreciated.
Jeff

Try [Steps to Install Wg311v3 driver](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

Good Luck

---

### Post by anewguy on 2012-01-04
Did you use the command line to install via ndiswrapper?  If so, you need to edit a file to force ndiswrapper to be loaded at boot:

sudo gksudo gedit /etc/modules

go to the end of the file and add the following line:

ndiswrapper

Now save the file via the Save funtion of the editor, then exit the editor and reboot - should be there then.  If not, post back and we'll trace what is happening.  I had a wg311-v3 on 3 computers I used to have, and the only way to make them work was via ndiswrapper.  I would have to go searching now, but I have posted some pretty detailed instructions in replies in more than 1 thread on the forum.

To others with similar problems:  DON'T use the command line for ndiswrapper - instead you need to install the additional package ndisgtk, a GUI'd front-end to ndiswrapper.  Takes away all of the command line input (and the chances for errors) and automatically updates things such as the blacklist, modules, etc..

Dave ;)

---

### Post by rem1100 on 2012-01-04
Dave,
[LEFT]You helped me get this working in early November. Did not use command line, used ndisgdk. When I open a terminal and type the command iwconfig [COLOR=Blue][COLOR=Black]wlan1 is identified as the wireless network[/COLOR]. [COLOR=Black]Then I type in the command sudo ndiswrapper -m[/COLOR][/COLOR] and the following comes up: adding "alias wlan0 ndiswrapper" to /etc/modules.conf ... 
As you can see wlan0 is identified. 
I put in the command sudo gksudo gedit/etc/modules and got the following response: (gksudo:2665): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
This is repeated 3 more times then command line shows up. 
I do not know what is going on but having 2 different wlan networks identified does not seem right.:confused:
Hope you can help me get this working correctly
Thanks,
Jeff 
[/LEFT]

---

### Post by anewguy on 2012-01-04
Well, the first thing would be not to worry about the warnings on the pixmap.

Since you used ndisgtk the first time, start up ndisgtk again but this time instead of adding anything, just delete any adapters that show until nothing shows, then exit ndisgtk.

Now open a terminal window and do the following:

sudo ndiswrapper -l <- that's a lower case "L" for list

if anything is returned in the output, do the following:

sudo ndiswrapper -e xxxxxx <- where xxxxxx is the device name shown in the list

repeat the above 2 commands until the list is empty.

Close the terminal window.

Now reboot.  After the system is back up, do the following in a terminal window:

sudo ndiswrapper -l <- lower case "L" again

The returned output should be nothing.

If an error is returned saying it can't find ndiswrapper, then for some reason it's not being loaded at boot.  So, you would need to check the modules file again:

gksudo gedit /etc/modules
open a terminal window again and
look at the end of the file -> there should be 1 line that says ndiswrapper.  If you see ndiswrapper more than once in the file, remove 1 of them (the ndiswrapper -m you tried used to add the entry to this file, but that hasn't worked for a long time - maybe yours did and there are 2 entries in the file).  If you needed to make a change here, reboot, and when the system is back up continue from here.

Open ndisgtk again.  There should be nothing showing.  Now do an add again, pointing it to the .inf file for the driver (remembering the .sys file[s] need to be in the same folder as the .inf file).  If you have made any changes, such as updating Ubuntu to a different architecture (32 vs 64 bit) remember the driver much match the architecture and be a Windows XP driver.

Does the wireless work again?  If so, reboot and make sure it is working after the reboot.

If not, we'll try to go from there.  It's possible we may need to check /etc/modules.conf as well.

Dave ;)

---

### Post by rem1100 on 2012-01-06
I removed the driver through ndisgdk then opened a terminal to verify there were none shown. I have only ever seen one driver installed. After reboot opened terminal, still no drivers shown. There never has been an error that ndiswrapper cannot be found.
Opened ndisgdk again, no drivers, installed inf file from a folder that contained two .sys files and a .cat file. Connected to our wireless network shortly thereafter. 
Rebooted, wireless did not connect. 
Opened ndisgdk removed driver then immediatly installed inf file again, wireless started working in a few seconds.  
This is the way the wireless has always worked for my Ubuntu installation. Once I get it working it works properly (I am using it right now). 
I am running 32 bit architecture XP also runs it and have no good reason to switch at this time. I am pretty sure I down loaded the right software from netgear but I do not know how to verify. The inf file shows that it is for both XP and Windows 2000.
Thanks,
Jeff

---

### Post by anewguy on 2012-01-06
I'll have to do some checking as I never had that problem with any of mine.

Dave ;)

---

### Post by anewguy on 2012-01-12
When you reboot and it fails, BEFORE you go to ndisgtk, please post the output of:

lsmod

Also, please use the editor and check that ndiswrapper is in the modules file:

gksudo gedit /etc/modules

If you don't see it, add a line at the end that simply says:

ndiswrapper

then save the file via the editor, exit the editor, exit the terminal window and reboot again. 

It's acting like ndiswrapper isn't loading until you start ndisgtk and then of course disapears on reboot if it's not specifically being loaded.

Dave ;)

---

### Post by rem1100 on 2012-01-14
This is the result of lsmod-

:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
dcdbas                 14098  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73673  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505159  3 
soundcore              12600  1 snd
parport_pc             32114  1 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
binfmt_misc            17292  1 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
e100                   36289  0 
floppy                 60310  0 

:~$ gksudo gedit/etc/modules

(gksudo:1972): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:1972): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:1972): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:1972): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
:~$ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

I have the feeling that when when the editor was checked that the warnings were the desired result. I hope you can make some sense of this, I am lost. 
For what is worth when I check the output of lsmod after reinstalling the inf file through ndisgdtk ndiswrapper is shown on the first line and is shown to be used by 0. There is no ndiswrapper in above list.
Thanks for the help thus far,
Jeff

---

### Post by anewguy on 2012-01-16
Please post the output of:

cat /etc/modules


You should see a line with:

lp

and another line with:

ndiswrapper


If all you see is lp, you need to:

- gksudo gedit /etc/modules

add the following line to the end of the file:

ndiswrapper

Then Save the file via the editor, exit and reboot.  It should work now.


thanks
Dave ;)

---

### Post by Cheesemill on 2012-01-16
I think one of your problems is that you're typing
```
gksudo gedit/etc/modules
```
where it should be
```
gksudo gedit /etc/modules
```

Notice the space between gedit and /etc/modules

---

### Post by rem1100 on 2012-01-17
Made change, rebooted, connected on it's own. Thank you Dave for bearing with me. Thank you Cheesemill, you caught my error. I was not putting the space between gedit and /etc/modules. Amazing how much better things went when I put the code in right. The code was presented correctly, I just failed to see it.
Jeff

---

### Post by anewguy on 2012-01-17
I'm just glad it's working for you.  Now that you know how to do this again, just play it forward if someone posts with the same problem.

Dave ;)

---

