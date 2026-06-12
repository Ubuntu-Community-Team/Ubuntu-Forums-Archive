---
title: "Ubuntu won't work for some reason. =/"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by infernohit on 2008-09-02
I can start it up until it says Ubuntu with the orange status bar is filling up, then afterwards I get an error message. How can I bypass this? I remember someone told me before to press F(some number) when I had a similar problem.

---

### Post by oldos2er on 2008-09-02
What is the error message?

---

### Post by infernohit on 2008-09-02
> **oldos2er said:**
> What is the error message?

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs)__

---

### Post by falcon61102 on 2008-09-02
Have you attempted to boot up in the recovery mode?  Normally the second option in your GRUB menu.

---

### Post by infernohit on 2008-09-02
> **falcon61102 said:**
> Have you attempted to boot up in the recovery mode?  Normally the second option in your GRUB menu.

Yeah I get the same message.

---

### Post by falcon61102 on 2008-09-02
It looks like it has something to do with a BIOS setting.  If you go into your BIOS you should see a setting called something like SATA Mode and right now it's probably set at IDE.  If you switch that to RAID, you should be able to boot up though I've heard this causing problems with some windows installs.  You can try it and see if it works for you.

---

### Post by infernohit on 2008-09-02
> **falcon61102 said:**
> It looks like it has something to do with a BIOS setting.  If you go into your BIOS you should see a setting called something like SATA Mode and right now it's probably set at IDE.  If you switch that to RAID, you should be able to boot up though I've heard this causing problems with some windows installs.  You can try it and see if it works for you.

Well if I haven't touched anything there, it shouldn't have changed. Ubuntu has been working for me for like 6 months. I think the problem was Windows was installing Windows Update, and when I restarted, I went to Ubuntu, not XP, so maybe that messed things up.

If not, I don't know what it was.

---

### Post by falcon61102 on 2008-09-02
Alright after some further research it appears that while that BIOS command worked for some, its not an all out fix.  Some others had success with adding either one or a combo of the following commands to their boot string:
```
all_generic_ide 
floppy=off 
irqpoll
```

To test those settings, restart and when you get to the GRUB, select one of your kernal versions and then hit "e" to edit.  Type those at the end of the kernal string.  If that works for you, you need to make it permanent by editing the menu.lst for the GRUB.  You can do that by:
```
gksudo gedit /boot/grub/menu.lst
```

Add those to the same kernal string as you did to boot up and then save.  You should be good then.

Further info can be found at:
[http://ubuntuforums.org/showthread.php?t=765195&highlight=apci](http://ubuntuforums.org/showthread.php?t=765195&highlight=apci)

---

### Post by falcon61102 on 2008-09-02
A windows update should not effect Ubuntu, they are completely seperate.  And Windows wouldn't affect your BIOS either so I don't know about that.  It might be possible that an update in Ubuntu might have caused this, and by the amount of people who have posted in the above link, it seems to be a pretty widespread error.

---

### Post by infernohit on 2008-09-12
Can you go more in-depth on how to do it? I'm not sure I'm doing it right, because it's not working.

---

### Post by jolx on 2008-09-12
the problem could be that a hard drive isnt plugged in properly

---

### Post by infernohit on 2008-09-12
But it's been working for more than 6 months. Why would the hard drive be the problem now? I can still dual-boot to Windows XP, I just can't use Ubuntu for some reason.

---

### Post by jolx on 2008-09-12
> **infernohit said:**
> But it's been working for more than 6 months. Why would the hard drive be the problem now? I can still dual-boot to Windows XP, I just can't use Ubuntu for some reason.

idk

it's just i took my computer to a mates place one day and i was getting this error and i soon found that one of my hard drives wasnt connected properly, so i plugged it in and it worked.

---

### Post by infernohit on 2008-09-12
I only have one hard drive and I haven't moved the computer anywhere.

---

### Post by falcon61102 on 2008-09-12
What exactly have you tried from the link that was posted earlier?
Knowing that we can narrow down some possiblities of what might work for you.

---

### Post by infernohit on 2008-09-17
I tried editing the boot sequence with that code he gave me, but I don't know how or where to put it because I can only do one line.

I just need to know where I edit that part in.

---

### Post by falcon61102 on 2008-09-19
When you say you can only do one line, what do you mean?

To edit the boot sequence at boot, select the install you wish to edit in the GRUB and select 'e'.  That will bring up a screen which shows you the details of that boot selection.  Those lines that were posted early need to be placed at the end of the kernal string.  Once you type them in, you should just be able to hit 'b' to boot.

---

### Post by infernohit on 2008-09-23
> **falcon61102 said:**
> Alright after some further research it appears that while that BIOS command worked for some, its not an all out fix.  Some others had success with adding either one or a combo of the following commands to their boot string:
```
all_generic_ide 
floppy=off 
irqpoll
```

To test those settings, restart and when you get to the GRUB, select one of your kernal versions and then hit "e" to edit.  Type those at the end of the kernal string.  If that works for you, you need to make it permanent by editing the menu.lst for the GRUB.  You can do that by:
```
gksudo gedit /boot/grub/menu.lst
```

Add those to the same kernal string as you did to boot up and then save.  You should be good then.

Further info can be found at:
[http://ubuntuforums.org/showthread.php?t=765195&highlight=apci](http://ubuntuforums.org/showthread.php?t=765195&highlight=apci)

Well do I type all_generic_ide and press enter, then type the next one?

Basically, I mean do I need a line break for it or no?

---

### Post by infernohit on 2008-09-28
Still haven't figured it out. =/

---

### Post by skullmunky on 2008-09-29
> **infernohit said:**
> Well do I type all_generic_ide and press enter, then type the next one?

Basically, I mean do I need a line break for it or no?

No, you just add them at the end of the line.

```
all_generic_ide  floppy=off  irqpoll
```

so  a full example might look like this:

```

/boot/vmlinuz-2.6.24-16-generic root=UUID=6bfa1153-4ae8-4180-bcd
7-82e2d4e035c1 ro quiet splash all_generic_ide  floppy=off  irqpoll

```

I'm not convinced it couldn't be caused by the Windows Update.  Nobody knows WHAT those things do, really.  :P

---

### Post by bobpur on 2008-09-29
I don't know all of that "code" stuff. I envy those that do; however, to me, it's about as clear as mud. 

This don't do you much good now, but for next time set yourself up with a separate "\home" partition and if this happens again just pop in your Ubuntu disk, reinstall the OS and drive on. All your data will be safe and there when you get up and running again.

Just my two cents. Good Luck.

---

### Post by infernohit on 2008-09-30
> **skullmunky said:**
> No, you just add them at the end of the line.

```
all_generic_ide  floppy=off  irqpoll
```

so  a full example might look like this:

```

/boot/vmlinuz-2.6.24-16-generic root=UUID=6bfa1153-4ae8-4180-bcd
7-82e2d4e035c1 ro quiet splash all_generic_ide  floppy=off  irqpoll

```

I'm not convinced it couldn't be caused by the Windows Update.  Nobody knows WHAT those things do, really.  :P

I tried it and it didn't help. Still the same error. =/

---

### Post by infernohit on 2008-10-15
Been without Linux for about a month now. It sucks. -_-

---

### Post by infernohit on 2008-11-24
Bah, it's been like 2 months since I've used Linux. I need help. x_x

---

### Post by falcon61102 on 2008-11-25
I know it's not a direct solution for your problem that you're having now, but it might work.  Have you tried a fresh install with 8.10?

---

### Post by infernohit on 2008-11-26
> **falcon61102 said:**
> I know it's not a direct solution for your problem that you're having now, but it might work.  Have you tried a fresh install with 8.10?

Would that erase everything I have in my current Linux partition?

---

### Post by handydan918 on 2008-11-26
> **infernohit said:**
> Would that erase everything I have in my current Linux partition?

It will if you make a mistake. Can you spell "backup"?

---

### Post by falcon61102 on 2008-11-27
A fresh install will overwrite everything on your partition.  You can back up your home directory that way you don't lose any personal information and then restore it once you get the install completed.

---

