---
title: "How does one remove plymouth without it marking many other packages for removal?"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by _Ouroboros_ on 2011-10-25
How does one remove plymouth without marking many other seemingly unrelated packages for removal?

I wish to have a text-only boot with minimal processes started during boot time, so I figured plymouth needs to go.

---

### Post by dwasifar on 2011-10-25
As I recall, plymouth is so tied into the boot process that it's difficult if not impossible to extricate it.

Why not just use the nosplash option in your boot instead?  That'll give you your text-only boot.

---

### Post by garvinrick4 on 2011-10-25
[FONT=&quot]Do not remove "plymouth" as you say carries packages with it that are vital.
Go to synaptic type plymouth in search window and go to "plymouth themes"
choose the theme you want looks like text and install it. (Make sure it is a Plymouth Theme)
Now run below in a terminal and pick out theme you wish to use by the number.
[/FONT]```
sudo update-alternatives --config default.plymouth 
```Once you have choosen and installed now run below:
```
sudo update-initramfs -u
```[FONT=&quot]
[/FONT]```
sudo reboot
```[FONT=&quot]


 
 [/FONT]

---

### Post by _Ouroboros_ on 2011-10-25
Thanks for the replies.

With regards to the nosplash option, would that be added to the grub line that executes linux?  If so, how would one edit that line?  My system boots straight into linux without the grub menu as it is, you see.

---

### Post by kemtnbkr on 2011-10-25
Yes, you boot with the nosplash option; I don't remember exact syntax, and I can't find any tutorials for GRUB2, but I do know if you hold down your shift key while your computer is booting, you can get to the GRUB2 screen- it'll pause loading an OS.

Sorry to not be more helpful...

---

### Post by _Ouroboros_ on 2011-10-26
Yeah holding down shift gets me to the GRUB menu, that's something I will remember forever now!  But I don't know how to make the changes permanent.  I will have to have a search around.

GRUB2 config is hard to edit manually I think but there must be a single file I could edit somewhere.

---

### Post by mc4man on 2011-10-26
Don't pay much attention to grub nor plymouth here so I'd just go to  - 
```
gksudo gedit  /etc/default/grub
```
in the top section shown below I'd  edit the blue line 

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR="Blue"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
GRUB_CMDLINE_LINUX=""

Making it look like this
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

After saving run 
```
sudo update-grub
```

Then go into synaptic, search plymouth & remove all the plymouth 'splash' packages - screen

---

### Post by garvinrick4 on 2011-10-26
Went into previous posts instructions and removed all plymouth themes, all of them just left plymouth and a libplymouth2 installed and made sure updated initramfs and rebooted
without the going into /etc/default/grub and removing "quiet splash" and it booted without the splash screen and in text. 
Was actually just playing around with it one step at a time and seeing results and worked before last step.
So anyone reading:
Follow mc4man's post and forget the removing "quite splash" and will be qood to go.

---

### Post by _Ouroboros_ on 2011-10-26
Hey, mc4man, thanks for the solutions, they have worked like a treat!  And now I know where the main grub file is that I would need to edit for other things.

I know what I am about to ask is a bit unrelated to this thread, but if I wanted to boot into runlevel 3, and not have X automatically started, would I add the command where "quiet splash" once was?

ps:  sorry garvinrick4, I only noticed your post after I had already applied mc4mans solutions.  Good job finding that out though.

---

### Post by garvinrick4 on 2011-10-26
@_Ouroboros_
> Good job finding that out though.     It was by accident just testing mc4man's post one step at a time and looking at plymouth
and its configuration. (seem to have learned a lot by accident)
Since plymouth came out just figured "text-theme" was text but was not anything close.

Below is a grub2 link to keep bookmarked that will explain all of /etc/default/grub and more.
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by _Ouroboros_ on 2011-10-26
@garvinrick4:  Thanks for that link.

---

### Post by mcduck on 2011-10-26
> **_Ouroboros_ said:**
> 
I know what I am about to ask is a bit unrelated to this thread, but if I wanted to boot into runlevel 3, and not have X automatically started, would I add the command where "quiet splash" once was?

The main grub configuration file is /etc/default/grub, and the files that determine the actual OS entries and such are found in /etc/grub.d/.

Anyway, getting Ubuntu to boot into runlevel 3 wouldn't do anything at all. Just like Debian, Ubuntu makes no difference between runlevels 2&#8211;5. The rest exist, though, so you could configure one of them to do what you want. On the other hand, if you never want to automatically boot into X then simply removing or disabling your DM would do the same trick with less work.

Either way, editing boot options alone will not do the trick.

---

### Post by JKyleOKC on 2011-10-26
> **_Ouroboros_ said:**
> I know what I am about to ask is a bit unrelated to this thread, but if I wanted to boot into runlevel 3, and not have X automatically started, would I add the command where "quiet splash" once was?As McDuck said, changing runlevels from 5 to 3 would have no effect on Ubuntu or Debian. The default level is 2, in the first place, and 3, 4, and 5 are exact copies of 2.

However if you replace "quiet splash" in the /etc/default/grub file with "text" you'll get the same effect.

It's really a shame that most of the books and advice you find that deal with boot options assume that the Red Hat way is the only way, since no distro based on Debian uses that technique!

---

### Post by _Ouroboros_ on 2011-10-26
Thanks for the replies.  I managed to get it to boot without starting X automatically, but the "secondary" boot messages are taking up tty7 by default (plymouth?) and I have to switch to tty1 manually to see the bash prompt once everything has loaded.

So when I start X, it has to go to tty8 because tty7 is already in use.  Any way to fix this?

---

