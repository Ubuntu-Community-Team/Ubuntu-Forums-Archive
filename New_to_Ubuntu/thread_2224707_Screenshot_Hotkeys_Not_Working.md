---
title: "Screenshot Hotkeys Not Working"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by DGINSD on 2014-05-17
After installing Ubuntu 14.04 I noticed my printscreen hotkeys for taking screenshots no longer work, after some research turned up these 2 links [http://askubuntu.com/questions/450070/assigning-print-button-to-screenshot-not-working-after-upgrade-from-13-10-to-14#](http://askubuntu.com/questions/450070/assigning-print-button-to-screenshot-not-working-after-upgrade-from-13-10-to-14#) and [https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1243733](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1243733)  putting the info from these two together it seems its a bug with HP keyboards assigning print to two separate keycodes at the end of the launchpad link it gives the commands...

```
david@HP-G6:~$ xmodmap -pk | grep Print    107        0xff61 (Print)    0xff15 (Sys_Req)    0xff61 (Print)    0xff15 (Sys_Req)    
    218        0xff61 (Print)    0x0000 (NoSymbol)    0xff61 (Print)    

```
```
xmodmap -e "keycode 107 = Sys_Req "
```
```
david@HP-G6:~$ xmodmap -pk | grep Print    218        0xff61 (Print)    0x0000 (NoSymbol)    0xff61 (Print)    

```

Which shows the two keys mapped to print then the second command changes it.  After executing these commands I can set the screenshot shortcuts using the keyboard GUI and everything works as designed till I have to reboot then the whole process must be repeated, kind of a pain.

So is there a way to make the the...   
```
xmodmap -e "keycode 107 = Sys_Req "
```

permanent so my keyboard works normally all the time, even through reboots or is there a CLI way to set the keyboard shortcuts for screenshots, so I can write a basic bash startup script to automate this process upon login?

I've looked through dconf-editor to look for a key to set with gsettings but the closest I came up with was org>compiz>integrated>command-screenshot>gnome-screenshot but nothing seemingly related to setting hotkeys to activate it. Hoping someone else will have some insight on a better way to fix this issue.

---

### Post by DGINSD on 2014-05-18
So after hours of searching I found a fix for my particular case, which is basically to edit file /usr/share/X11/xkb/keycodes/evdev, a file xkb uses to build keycodes for keyboards and places the files in /var/lib/xkb as a file, or in my case files, named server-[randomstring].xkm. The edit to evdev that needs to be made, is on line 93 and 94 changing this...

```
    <PRSC> = 107;
    //<SYRQ> = 107;

```

to this...

```
    //<PRSC> = 107;
    <SYRQ> = 107;

```

this comments out Print assignment to 107 and changes it to Sys_Req, for good measure I got rid of the old files in /var/lib/xkb which will be regenerated correctly upon reboot. Also after reboot I had to go into the; system settings> keyboard> shortcuts> screenshots GUI, and re-assign the keys to take screenshots. So quick steps...

```
gksudo gedit /usr/share/X11/xkb/keycodes/evdev
```

make the changes listed above and save

```
sudo rm /var/lib/xkb/server-*.xkm 
``` 

reboot and re-assign keys via the GUI, this will hold upon subsequent reboots. These instructions are specific to HP keyboards similar issues with different hardware may require different edits (then again this seems like a bad edit by a programmer that may have slipped through so it may help others).

---

