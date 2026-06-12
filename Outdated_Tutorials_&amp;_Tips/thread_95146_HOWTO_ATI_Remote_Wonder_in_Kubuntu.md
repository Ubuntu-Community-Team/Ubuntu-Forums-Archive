---
title: "HOWTO: ATI Remote Wonder in Kubuntu"
date: 2005-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by AdrianVeidt on 2005-11-25
I'm going to assume a few things here. First, I'm going to assume that the *ati_remote* module is being loaded at boot time. To check, you can open a terminal and type:

$ lsmod

Look over the list and you should see it there. If you have the receiver connected, and booted up with it connected, then it should be there. If not, then you may have a problem with the hardware, either the USB controller or the receiver itself.
One other thing I'm going to assume is that you're using KDE and not Gnome (or anything else). Someone who is a Gnome-ite can adapt this knowledge for Gnome's startup scripts and hotkeys if they want.
If you've gotten this far, then you're using KDE and have the module loaded. Believe it or not, you actually have quite a bit of functionality already. You may know that you can use the direction pad and the two mouse emulation buttons successfully. If not, try it. Works the same as with Windows. But you can also use the numerical pad, and the 6 'unassigned' buttons (the little buttons with the letters on them - a, b, c, d, e ,f). Open a terminal and try those buttons, and they should make the corresponding actions appear in the window, EG. the 'f' key will make the letter f.
What we're going to do is map the rest of the keys to XF86 keysyms, and then attach those keysyms to KDE shortcuts.
First, we have to find out what the keycode numbers are for the keys that have no functionality. Take out a pad and something to write with. Open a terminal and type:

xev

Put the mouse pointer on the small *Event Tester* window that pops up. Very carefully touch each button and observe the following information in the terminal window:

> KeyRelease event, serial 27, synthetic NO, window 0x3600001,
    root 0x48, subw 0x3600002, time 1163616, (31,30), root:(1368,63),
    state 0x10, [COLOR="blue"]keycode 41[/COLOR] (keysym 0x66, f), same_screen YES,
    XLookupString gives 1 bytes: (66) "f"


Record the [COLOR="blue"]keycode[/COLOR] number for each unused key. For me, the Channel Up/Down keys have no code, and I don't know how to assign them one. The useful keys are Volume +-, Play, Stop, Pause, Forward, Back, Mute. Other keys may or may not work, and you can customize them as you desire. I prefer to leave the keys that already work unchanged.
Now you can close the Even Tester window, which ends the *xev* command. What we're going to do now is map the keys to known XF86 keysyms and load that map automatically every time KDE is started.
What you'll need to do is create a new config file in your home directory. There are about a million ways to do this, but here's just one. From the terminal:

cd
kwrite .xmodmap

I'm using Kwrite here because I've had intermittent problems with Kate. You could also use Kate, or VI if you're really adventurous. The point is, a simple text editor. The config file is going to be in a format that the xmodmap program can understand. Here is a sample of mine (at least as I'm writing this; I do change it from time to time):

> ! QUIT
keycode 222 =q 
! PLAY
keycode 179 = XF86AudioPlay
! PAUSE
keycode 110 = XF86AudioPause
! STOP
keycode 232 = XF86Stop
! NEXT
keycode 233 = XF86AudioNext
! PREVIOUS
keycode 152 = XF86AudioPrev
! VOLUME DOWN
keycode 174 = XF86AudioLowerVolume
! VOLUME UP
keycode 176 = XF86AudioRaiseVolume
!MUTE
keycode 160 = XF86AudioMute


Note that the lines with the exclamation point are comments. Note also the keycode numbers you copied down in the previous step. I think it's a straightforward file and I shouldn't need to go over it in excruciating detail. If the keycode numbers correspond exactly to what your *xev* information is, then you can simply copy-paste what I've got here into your new .xmodmap file. If not, then modify the keycode numbers accordingly. Save the file. Now we need to load the file. In the terminal:

$ xmodmap .xmodmap

If you got no errors, then you're off to the races. Depending on your hardware, the volume buttons may already control the mixer volume. The others will be assigned later. If you got an error, then you may have made a sloppy mistake somewhere. remember that Linux is case sensitive. Look at the file again carefully.
Next step is to have the file load automatically in the background every time KDE starts. For this, we'll create a painless little script. Whenever you create a script in Linux you need to remember two things: One, the first line needs to point to the executable, such as perl, or sh, or bash. Two, the execute bit needs to be turned on. Don't sweat it - I'll show you how it's done. First, lets create the script. I called it .xmod, but you can name it whatever you want.

$ kate .xmod

The entire script is going to simply consist of:

> #! /bin/bash

xmodmap .xmodmap

That's it. Finished. One command.
KDE has a special folder called Autostart where scripts or symlinks to applications can be placed that the user wants running at startup (similar to the "startup" folder in Windows). In the terminal:

$ chmod 755 .xmod
$ cd ~/.kde/Autostart
$ ln -s ~/.xmod

Now here's where it gets a bit tricky. Just kidding. Now that you've taken care of the map file starting automatically, you can use KDE's shortcuts to have some fun with applications such as Amarok. Start Amarok and then click *Settings --> Configure Global Shortcuts*. I believe all KDE applications have a similar feature, and in the same place in the Settings menu. Now select Play, hit Custom and then Alternate Shortcut (Don't screw with the primaries; that's a recipe for a headache). Click that little 'x' box and then press the Play button on the remote. *XF86AudioPlay* should appear as the alternate shortcut. Repeat steps for the other shortcuts as desired. Note that the remote should control Amarok even if it is not the active window.

---

### Post by MBro on 2005-11-28
To apply this tutorial to gnome all steps through
$ chmod 755 .xmod
replacing kate with gedit of course

then go to System>Preferences>Sessions

click the start up programs tab
Then click the add button
in the startup command box type
```
/home/YOURUSERNAME/.xmod 
```

Then you'll be set.  It's working great for me.

---

### Post by AndRom6 on 2006-10-01
I am running Ubuntu 6.06 Dapper linux (Gnome)
I have an ATI Remote Wonder Plus (came with my TV Wonder Elite).
lsmod shows the ati_remote process running but I get no response from Gnome or the xev event tester when I push anything on it. I'm sure the batteries are plugged in and the USB device is hooked up correctly as it works in Windows XP (I dual boot). Any advice you could give to fix this would be great.
Thanks in advance.

---

### Post by pregoeater on 2006-11-13
guide worked great i have my remote working. just a few questions. i use totem, when i hit the power button totem closes then ubuntu tries to close. is there anyway to just make one thing close. i tired a few times incase it as me hitting more then once but thats not the case even when i tap it quick same problem. next problem is when i have totem minimized the remote wont work so if i have firefox open i have to open totem to use the remote or if another app steals focus i cant use the remnote. last problem remote does not work with all programs does not work with xmms i like totem but its HUGE. anyway to get remote to work for xmms OR make totem small.

Thanks,
Pre

---

### Post by ghstzr0 on 2006-12-10
> lsmod shows the ati_remote process running but I get no response from Gnome or the xev event tester when I push anything on it. I'm sure the batteries are plugged in and the USB device is hooked up correctly as it works in Windows XP (I dual boot).

I have THE EXACT SAME PROBLEM!  No response from xev after install of ubuntu.  I have tried installing LIRC but to no avail!

---

### Post by Epskampie on 2007-01-31
In KDE:
Some buttons are mapped to default actions in KDE, like mute (very ugly mute screen) and log out.

If you'd rather map those keys yourself, uninstall the 'kmilo' program. This plugin causes this behaviour.

---

### Post by mike4ubuntu on 2007-02-14
> lsmod shows the ati_remote process running but I get no response from Gnome or the xev event tester when I push anything on it. I'm sure the batteries are plugged in and the USB device is hooked up correctly as it works in Windows XP (I dual boot).

I have the same problem with GNOME in Dapper.

It appears that the ati_remote doesn't work in dapper GNOME, even though lsmod lists it, but it does work in edgy.

---

### Post by LtPitt on 2007-03-16
Hi guys!
I've tried this tutorial and everything went just fine...
I have just one problem...
When I set global shortcuts (e.g. in amarok) everything works but when I try to raise volume it looks like kmix it's "stealing" the focus not allowing me to set amarok volume.
This would be ok anyway if I'd be able to set global volume using kmix but this does not work (even using mouse if I set kmix volume to zero I can still hear music :| ) AND if I try to raise volume it goes to 100%, if I try to lower it it goes to 90%, no matter how many times I push the button.
I just have 10% more or less...
Any hint would be greatly appreciated! =)

---

### Post by Epskampie on 2007-06-09
Please read before posting, i posted the solution to your problem two posts up.

---

### Post by iamgregor on 2011-03-13
Necropost! 

I just did this and all is well so far, but I've remapped keys for basic letters apparently. What's the best way to only use the remapping for the remote or for certain programs then undo the damage afterwards?

Is there a quick key reset function or do I have to write another custom .xmod to do this?

---

### Post by Iowan on 2011-03-13
From Code of Conduct:
> # Thread Closing: Staff are not required to do so, but are requested to post an explanation in a thread that is closed when time permits. This is a non-exhaustive list of reasons a thread may be closed, but will give the general idea:

    * The thread has run it's course and posts have begun repeating themes
    * The thread has degraded into an argument
    * The thread topic is a duplicate of another current and active thread
    * [COLOR="Red"]The thread is very old[/COLOR].



---

