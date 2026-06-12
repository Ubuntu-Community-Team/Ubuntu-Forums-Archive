---
title: "Remastersys or Relinux"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by silverwolf5 on 2013-05-04
Hi. I'm trying to create my own Linux distro for a college project, from Xubuntu 64 bits (Raring Ringtail).
But I'm having issues with both Remastersys and Relinux when creating the ISO file, they won't save my custom theme (bar colors, menu font color), background image, booting and shutdown custom splash screen and won't save any file that I may have on the "Images" folder. It just saves the original Xubuntu desktop theme. The installed programs appear correctly though.
I've tried this but doesn't work: [http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/](http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/)
Any help from someone more experienced I would be very grateful.


This is a plus, does anyone knows modifications to the kernel that may improve multithreading/multicore performance? Thank you.

---

### Post by lkjoel on 2013-05-04
The issue you're having is because ubuntu makes the temporary guest account (the account that you use when you boot the CD) based off of a folder named /etc/skel. In fact, whenever ubuntu needs to make a new user account, it will copy the contents of /etc/skel to the folder of the new user account.

So whatever you want to be copied to the home folder of the installed/live user (such as the theme configuration files/folders, your "Images" directory, etc...), you need to copy it to /etc/skel. Just treat it as a home directory and then you should be fine (as long as you don't copy over your web browser history and such ;)).

I figured out a trick a while ago that helps with copying the correct files (as it can be hard to figure out which configuration files to copy over), I don't know if it could help you too. It's to run any configuration programs you use (such as ubuntu-tweak, gnome-control-center, or ccsm) like this (replacing *insert_program_name_here* with the name of the program, of course), under a terminal window:

```
HOME=/etc/skel insert_program_name_here
```

It will then run that program, making it think that your home folder is actually /etc/skel, so it will modify that instead (and then will modify the correct configuration files).

Anyways, hope this helps!! Let me know if I'm not clear or anything :)

---

### Post by silverwolf5 on 2013-05-04
You're telling me to treat */etc/skel* just as a normal "home" folder is that right? As it will used by the new distro for the live user and the one created afterwards. How about modifications to system files? I mean, I copied the original XFCE theme, modified it and created a new theme with a different folder name, I believe it is not on the user "home" folder.
I will test it later tonight and let you know of the results.
Thanks for your help.

---

### Post by silverwolf5 on 2013-05-04
I copied the folder "Images" from my home folder to /etc/skel, as well all hidden files starting with "."
No luck, after creating the ISO the live user still uses the same default XFCE desktop theme, but the files in the "Images" folder are placed correctly.
Do you have any other solution that may help or am I missing some step?

---

### Post by lkjoel on 2013-05-05
> **silverwolf5 said:**
> You're telling me to treat */etc/skel* just as a normal "home" folder is that right? As it will used by the new distro for the live user and the one created afterwards. How about modifications to system files? I mean, I copied the original XFCE theme, modified it and created a new theme with a different folder name, I believe it is not on the user "home" folder.
yes, that's correct. About your second point, you have to make sure that the theme is not under any of these folders, because relinux will exclude them:


[LIST]
[*]/dev
[*]/home
[*]/media
[*]/mnt
[*]/proc
[*]/sys
[*]/run
[*]/tmp
[/LIST]

If it is, then simply copy it somewhere else (maybe to /usr/share/themes?), and tell XFCE of its new location (don't copy it to /etc/skel though).

---

### Post by silverwolf5 on 2013-05-06
Hi again.
The theme is located in a folder with the name /etc/share/themes/ISPGAYA for my current user, but it still defines the default XFCE theme when creating the ISO.
How do I associate this theme to be default for all new accounts created and for the live user? Also I do I set the plymouth splash screen I created for both of them?

---

### Post by lkjoel on 2013-05-06
/**etc**/share/themes? Are you sure it's not /**usr**/share/themes? If it really is in /etc/share/themes, move it to /usr/share/themes (and update XFCE about it).
Also, run this in a terminal:

```
HOME=/etc/skel xfce4-settings-manager
```

then edit your default theme there.

For plymouth, see this: [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html).

---

### Post by silverwolf5 on 2013-05-07
Sorry my mistake, the theme is indeed in /usr/share/themes.
I've run  the code you provided, selected the default theme and wallpaper, created  the ISO and it's still not working. I end up with the default XFCE  theme and wallpaper in the live user. I am able to choose my custom  theme in the control panel, but I would like it to be the default when  the system first starts.
Thank you for your patience, I believe I'm  becoming a bit annoying with this issue but I really need it to work.  I'm rather new to Linux.

---

### Post by lkjoel on 2013-05-08
okay, great, I thought so :D
That's very interesting... and I presume that when you re-run that command, your settings are saved, right?

Just wondering, what would happen if you ran this in the booted ISO:
```
xfce4-settings-manager
```
It should show the default theme, right? Now what would happen if you did this:
```
HOME=/etc/skel xfce4-settings-manager
```
Does it *also* show the default theme? Or does it show your theme?

Also, just make sure that your theme, in the booted ISO, is indeed in /usr/share/themes (just to make sure it wasn't excluded or something).

---

### Post by silverwolf5 on 2013-05-08
When I execute the first code it appears the default theme as being "Greybird", but no console warnings.

Whe I execute the second it appears the default theme "Greybird" too, but I get these warnings:


(xfce4-settings-manager:3054): libxfce4util-WARNING **: Invalid XDG_CACHE_HOME directory `[I]/etc/skel/.cache', program may behave incorrectly.

(xfce4-settings-manager:3054): libxfce4util-WARNING **: Invalid XDG_DATA_HOME directory `[I]/etc/skel/.local/share', program may behave incorrectly.

(xfce4-settings-manager:3054): libxfce4util-WARNING **: Invalid XDG_CONFIG_HOME directory `[I]/etc/skel/.config', program may behave incorrectly.

(xfce4-appearance-settings:3057): libxfce4util-WARNING **: Invalid XDG_CACHE_HOME directory `[I]/etc/skel/.cache', program may behave incorrectly.

(xfce4-appearance-settings:3057): libxfce4util-WARNING **: Invalid XDG_DATA_HOME directory `[I]/etc/skel/.local/share', program may behave incorrectly.

(xfce4-appearance-settings:3057): libxfce4util-WARNING **: Invalid XDG_CONFIG_HOME directory `[I]/etc/skel/.config', program may behave incorrectly.


In both situations, my custom theme is there if I wish to choose, the name is ISPGAYA.
[/I][/I][/I][/I][/I][/I]

---

### Post by lkjoel on 2013-05-08
Oh, I think I know part of the issue now. I forgot that running **sudo** actually discards any environment variable information (including $HOME), so try this (in your host, not in the ISO):

```
sudo -s
export HOME=/etc/skel
xfce4-settings-manager
```

See if that works!

---

### Post by silverwolf5 on 2013-05-12
Hi again.
I tried that and for some reason now I'm not able to create the ISO with Relinux, it only creates the md5 file with 0 bytes? I've made a clone of my virtual machine just to test your code.
Reverted back to original VM and the ISO creation works fine.
Any clues?

---

### Post by lkjoel on 2013-05-12
Okay, I think I get the issue now... it's with xfce4-settings-manager being a bit *too* smart. So instead, first make sure that your normal user has the theme you want, and then run this:
```
sudo rm -rf /etc/skel/.config
sudo cp -R ~/.config /etc/skel/
```
I *think* it should work this time.

---

### Post by silverwolf5 on 2013-05-14
I tried that code, I was able to create the ISO, but when I choose to boot the "Live User" option in the menu I get this

[IMG]http://paginas.ispgaya.pt/~ei082425/images/busybox.jpg[/IMG]

What's BusyBox?

---

### Post by lkjoel on 2013-05-15
Odd, I tried doing this on my testing machine using relinux, and I came to 2 conclusions:


[LIST]
[*]My testing machine is *really* slow
[*]And, the issue that you're having is **not** caused by the commands I gave you, because it worked perfectly fine for me
[/LIST]


So something else must be causing it... maybe it's the combination of all of the commands I gave you? Try re-installing the master system (the one you run relinux or remastersys from), and see if that works (only run the last commands I gave you, the one I wrote 2 days ago, not any of the older ones). The issue you're having there seems to be much more low-level than just a /etc/skel error, so I think it will be simpler to just re-install than to try and pinpoint the issue.

Also, busybox is just a single executable that contains a lot of common shell utilities, such as mkdir and ls (and a shell). It's quite useful for recovery systems (such as the one your screenshot indicated), as they only have to bundle one executable, instead of hundreds. But that's not the cause and/or related to the issue :)

---

### Post by silverwolf5 on 2013-05-15
I tried that last code you gave me on a *fresh copy* of the system. I'll clone my original VM and try once more.
If I can't put this to work I'll just drop it, the essencial of the project it's already concluded.
Thanks for your help anyway. If you come around these parts someday I'll buy you a beer (I visited your personal website, not sure if I should though :P).

---

### Post by lkjoel on 2013-05-15
Okay, that's really odd... could you make 2 ISO's, one *before* running the commands, and one *after* running them? Also, before you make the first ISO, save a snapshot, and restore that snapshot (maybe create another one before doing that?) before running the commands and making the second one. That way, we can know if it's actually the commands that cause it, or if it's a completely different issue. It could also help with knowing what happened during the boot time that created the issue (if it's actually the commands that are causing the issue, it'll help us to know why, by using comparing files between both).

No problem! Haha, I might have to pass on that one XD

---

