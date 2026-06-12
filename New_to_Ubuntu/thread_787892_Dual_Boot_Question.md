---
title: "Dual Boot Question"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by timorrill on 2008-05-09
I'm in the process of switching full time to Ubuntu, but while I'm working out the kinks I'm still dual booting.

In Ubuntu, is it possible to instruct the computer to reboot into Windows? I don't want to mess around with the default options in the GRUB loader, since I like that it defaults to Ubuntu after 10 seconds. What I would like most is to be able to click a button or issue a command that reboots automatically to Windows, so that I don't have to sit around and wait for the GRUB loader to ask me which operating system.

Does this make any sense?

---

### Post by hermes0710 on 2008-05-09
Yes it makes sense. When i had kubuntu installed and i pressed the shutdown button i had a menu for the "Restart" option referencing the entries of menu.lst. This is not present in Gnome but since it has been made for Kde it surely can be made for Gnome. I'll check it when I get to my box and will come back to you...

---

### Post by bumanie on 2008-05-09
As far as I know, you can't change to windows from within ubuntu (although the above post says it's possible from kde, I can't confirm or deny that). You could think about using virtualbox to run windows on - that would be the same effect as you want.

---

### Post by hermes0710 on 2008-05-09
> **bumanie said:**
> As far as I know, you can't change to windows from within ubuntu (although the above post says it's possible from kde, I can't confirm or deny that). You could think about using virtualbox to run windows on - that would be the same effect as you want.

He doesn't want to switch to windows while in ubuntu. He wants to restart computer but without having to select which os to boot but directly boot Windows. And not always, only for the next reboot. Right?

---

### Post by timorrill on 2008-05-09
> **hermes0710 said:**
> He doesn't want to switch to windows while in ubuntu. He wants to restart computer but without having to select which os to boot but directly boot Windows. And not always, only for the next reboot. Right?

Yes! That's correct. I don't mind the reboot.

My motivation for this is that when I reboot, I usually leave the computer to do something else. Even though it's not a long wait, I don't like having to wait for the computer to shut down, and then for GRUB to load, and then to have to select Windows.

It sounds like the option is KDE is exactly what I am looking for -- a list of OS choices presented to me when I choose restart. Now -- if we can only figure out how to get this feature into Gnome.

---

### Post by bumanie on 2008-05-09
Sorry I didn't get the gist of the post.

---

### Post by hermes0710 on 2008-05-09
The command is ```
grub-reboot x
```

where x is the number of the entry in menu.lst of the os you want to boot.

When calculating the entry number take in consideration that windows entries in menu.lst usually follow a transient entry "Other systems"

---

### Post by timorrill on 2008-05-09
This very nearly does the trick. I had to change the line 'default 0' to 'default saved' in order to get it to work (as per the instructions I found at [http://wiki.debian.org/GrubReboot](http://wiki.debian.org/GrubReboot)).

Now the problem that I am facing is that with the 'saved' option, when I am in Windows and reboot, the machine goes to Windows again.
I would like for the computer to continue to default to Ubuntu. (Of course, ideally, it would be nice to be able to select an operating system when I rebooted from Windows!).

Am I asking too much?

---

### Post by MiniMe on 2008-06-06
In menu.lst try changing where it says

savedefault

to

savedefault=false

This should stop the machine from booting to windows again. I'm guessing you should first reset the default to your 1st choice before trying it. 
grub-set-default [num]
Where [num] is your default preference.

See [http://ubuntuforums.org/showthread.php?t=722900](http://ubuntuforums.org/showthread.php?t=722900)

---

