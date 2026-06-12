---
title: "[SOLVED] when i plug in a usb flash drive...."
date: 2008-11-19
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-11-19
when i plug in a usb flash drive.... into my dell mini netbook. it works. I upload files or transfer them over.

when i want to unplug it. was there a certain way to do something to it to have it eject or whatever. or can i just pull it out?

cause in windows, i had to click on this taskbar when click on "Safely Remove Hardware

is there a similar way to do that for ubuntu linux or it doesn,t corrupt the file when i pull it out when it is on?

---

### Post by patrickballeux on 2008-11-19
Hi,

Simply right-clik on your usb drive (on your desktop) and click "Unmount" (or Eject...)...

Then it will tell you to wait if there is still some data transfer...  And notify when done.

---

### Post by Peter09 on 2008-11-19
Right Click on the icon for the device (should be on your desktop) and select unmount.

---

### Post by fiendishfish on 2008-11-19
I find it somewhat disturbing that people only ever give the overview and instructions for using the GUI, I think the person should be presented with the possible range of options, regardless if you think /s/he isn't going to use the shell.

To unmount it safely and not destroy all your transferred files use;

*replace 'DEVICE' with the location of the USB device, i.e. hda1 sda2.

```
sudo umount /dev/DEVICE/
```

If you get the message:

> umount: /mnt: device is busy


You can use the command 'fuser' to check which process is still interacting with the usb-drive:

```
fuser -m /dev/DEVICE
```

Which then you can choose to kill, or whatever.

Hope I helped


PS: As the other obvious options have already been presented, I'm not going to repeat them
(had to include that so my post didn't sound ironic)

-fiendishfish

---

### Post by vjones777 on 2008-11-19
> **fiendishfish said:**
> replace 'DEVICE' with the location of the USB device, i.e. hda1 sda2.

```
sudo umount /dev/DEVICE/
```

In order to know what the 'DEVICE' is on your system, at the terminal type 'mount' without any parameters.  There should be a line there that has something like 
/dev/sda1 on /media/kingston type vfat ....  
In this example, kingston is the memory stick manufacturer and you would ```
sudo /dev/sda1
```

If you find that mount gives you a long list to read through, you can shorten the output by filtering the output like
```
mount | grep media
```which should give you just the line of interest.

---

### Post by fiendishfish on 2008-11-19
> **vjones777 said:**
> In order to know what the 'DEVICE' is on your system, at the terminal type 'mount' without any parameters.  There should be a line there that has something like 
/dev/sda1 on /media/kingston type vfat ....  
In this example, kingston is the memory stick manufacturer and you would ```
sudo /dev/sda1
```

If you find that mount gives you a long list to read through, you can shorten the output by filtering the output like
```
mount | grep media
```which should give you just the line of interest.

Indeed, but you tend to notice when a new device has been added. Say your HDD is PATA and sda* appears, or even if your HDD is SATA you'd notice if a new drive has been added as it'll be sd*, ls suffices for finding out added usb drives.

---

### Post by patrickballeux on 2008-11-20
Hi fiendishfish,

> **fiendishfish said:**
> I find it somewhat disturbing that people only ever give the overview and instructions for using the GUI, I think the person should be presented with the possible range of options, regardless if you think /s/he isn't going to use the shell.

-fiendishfish

Regarding your "disturbance", as it is interesting to know the 1000 ways to do something, we are in a "Absolute Beginner Talk", meaning that people are asking for help on how to do something because they don't know how to do it.  They are not asking "What are the different possibilities to do this action?".

This would be appropriate in a more technical thread (or if it was asked for) but your answer (which is well documented) is the kind of answer that newbie find frightening and scary.

It's like asking for our way to go to Montreal.  I want the shortest and friendliest path to go there.  I do not want all the possibilities available, I just want to go to Montreal (or wathever city that you want).

Only if the newbie seems interesting to learn more, the we can suggest any "geek" road available.

Linux has a bad reputation that when you ask for help, you are answered with "command line instructions" and also that "you absolutely need the terminal to configure your desktop".


Just a "right-click, and select Umount" was enough for that simple task in this thread.

Amicalement,:)

Patrick

---

### Post by fiendishfish on 2008-11-20
patrickballeux,

Good point and a sufficient answer..

Although, I am still kind of a Linux newbie especially to many peoples standards. Personally I think the main advantage of Linux is the ability to do virtually everything in the command line if you choose to, the amount of ways you can do things and the ability to configure basically _anything_ to suit your needs!

I've never used an excessive Desktop Environment such as KDE or GNOME, and what I know so far has been through trial and error, research and reading stuff on the net. I've always stuck with Window Managers such as Fluxbox.

I am now learning about compiling kernels!

Yay for me!

</narcissism>

Thanks for the response anyway!

--fiendishfish

---

### Post by halitech on 2008-11-20
I'm actually going to come to fiendishfish's defense here for a moment. Patrick, I can understand your point that this is the Beginner section but how many other times do you see CLI commands being given here for assistance with a problem? I do agree that telling the OP to right click - unmount should be all they should need but what if they are using flux or Evil for a window manager? (I know, highly unlikely if they are a new user but still possible) In that case, right click - unmount may not work (I've never used the others so not sure) and having the CLI instructions would be handy so they don't have to come back and ask again for another way of doing it. Also, if the right click - unmount fails, its nice to have the backup of the CLI instructions to fall back on so they can check why it failed.

Now, was not my intent to start a flame war, just wanted to point out that fiendishfish's instructions were valid for this question. :)

---

### Post by patrickballeux on 2008-11-21
Hi halitech,

This is not a flamewar, this is an interesting discussion between intelligent people. :guitar:

As you said, the absolute newbie will not use another window manager because he/she doesnt know about it.  And assuming that UMOUNT will fail is assuming that Ubuntu does not work.  Of course, this can happen, but in a minority of time (Actually, it never happened to me on all my PCs).

**fiendishfish**'s instruction are valid, that's not my point.  I was simply pointing to the fact that to a simple question, we should provide a simple answer.  Providing all the possibilities can be more confusing for new users than helping (and also for regular users).

We, as regular users must make a difference between helping and educating.  Sometimes, it's not the same thing.  I work in technical support and the worst thing to help a user/client is to give too much informations *at the same time*...  Instead, you can provide the alternative in a second or third message as "For your information, you could also..."

> **halitech said:**
>  but what if they are using flux or Evil for a window manager? (I know, highly unlikely if they are a new user but still possible) In that case, right click - unmount may not work (I've never used the others so not sure) and having the CLI instructions would be handy so they don't have to come back and ask again for another way of doing it. Also, if the right click - unmount fails, its nice to have the backup of the CLI instructions to fall back on so they can check why it failed.

Sometimes, I want to do some stuff on my laptop and then start searching the web to find how to do this.  Most of the time, I find really good procedure using the command line and that's great.  And then, I script that so I can use it anytime I want.  And, after a while, I discover that it can be done in a one click process using some options in the GUI or by "right-clicking ont it"...  Even if it was interesting to script it, I find it more useful to know about the GUI way because I don't have to manage all kind of scripts.  I just need to remember where to click for the next time, that's all.

Take for example the network configuration.  It can all be done using the CLI and that's great.  But it is more useful and easier to use the Network Manager instead.  Even for regular users... :lolflag:

Have a really nice day!

Patrick

---

