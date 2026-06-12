---
title: "Sound through speakers in HP Pavillion DV-5 1250us in Jaunty"
date: 2009-08-09
forum: Outdated Tutorials &amp; Tips
---

### Post by SOULRiDER on 2009-08-09
This was tested and works on a HP Pavillion DV-5 1250us. If you have a similar laptop and it works for you too, or if you're using a different Ubuntu release, please post here.

Sound on this laptop only works through headphones, but not through the internal speakers. Surfing the net I found this fix (too bad I don't remember where I got it from).

First open up **/etc/modprobe.d/alsa-base.conf** as root

You can use nano:
```
nano /etc/modprobe.d/alsa-base.conf
```
**or** Gedit if you're using Ubuntu
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
**or** Kate if you're using Kubuntu
```
kdesu kate /etc/modprobe.d/alsa-base.conf
```

Now go to the end of the file and add the following lines:
```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
```
Save the file (press ctrl + x if you used nano) and reboot.

Sound through speakers should work now.


NOTE: I found another post about this in the forums, but I didn't test it and its a bit more complex than this one. [This]("http://ubuntuforums.org/showthread.php?t=1147764") is the forum post.

---

### Post by zblip2 on 2009-09-20
Hi

I tried to fix my computer writing the code lines as described in this thread but the folder is ''write only'' so I wasn't able.

You rote:

"First open up **/etc/modprobe.d/alsa-base.conf** as root"
You can use nano:
```
nano /etc/modprobe.d/alsa-base.conf
```**or** Gedit if you're using Ubuntu
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```****."

What is "as root"? I've seen this a couple of times on forums but NOBODY explains what it is, like it's some kind of secret.... Same with "nano", "sudo", "gedit"...

Would you (or some one else) be kind enough to explain exactly how to do this? I looked around in my computer and found folders and stuff named "gedit" and "nano" but was unable to do anything with that... On another forum some one talks about "sudo". I downloaded something from the sudo site but guess what, that didn't work also, meaning, I haven't the slightest idea of what to do with that.

Would some one be kind enough to write a step by step explanation  of the procedure?

Thanks

---

### Post by majiciannz on 2009-09-20
> **SOULRiDER said:**
> This was tested and works on a HP Pavillion DV-5 1250us. If you have a similar laptop and it works for you too, or if you're using a different Ubuntu release, please post here.

Sound on this laptop only works through headphones, but not through the internal speakers. Surfing the net I found this fix (too bad I don't remember where I got it from).

First open up **/etc/modprobe.d/alsa-base.conf** as root

You can use nano:
```
nano /etc/modprobe.d/alsa-base.conf
```
**or** Gedit if you're using Ubuntu
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
**or** Kate if you're using Kubuntu
```
kdesu kate /etc/modprobe.d/alsa-base.conf
```

Now go to the end of the file and add the following lines:
```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
```
Save the file (press ctrl + x if you used nano) and reboot.

Sound through speakers should work now.


NOTE: I found another post about this in the forums, but I didn't test it and its a bit more complex than this one. [This]("http://ubuntuforums.org/showthread.php?t=1147764") is the forum post.
I have a HP dv5 and had sound problems with pc speakers not working on Ubuntu and Kubuntu 9.04. However the headphones did work.

I found this fix on this forum and it works perfectly for me.........

Try inserting the following in /etc/modprobe.d/alsa-base.conf:

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

Cheers

---

### Post by zblip2 on 2009-09-20
> **majiciannz said:**
> I have a HP dv5 and had sound problems with pc speakers not working on Ubuntu and Kubuntu 9.04. However the headphones did work.

I found this fix on this forum and it works perfectly for me.........

Try inserting the following in /etc/modprobe.d/alsa-base.conf:

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

Cheers

That's great but when I try to do the same a pop-up tells me I don't have the privilege to edit this folder... How did you bypass this problem?

---

### Post by majiciannz on 2009-09-21
Ok, you have to be root user to save changes to system files such as alsa-base config.
If you google sudo you should find a wealth of onfo on the subject.

Try this link.....   [http://linux.about.com/od/commands/l/blcmdl8_sudo.htm](http://linux.about.com/od/commands/l/blcmdl8_sudo.htm)

In a terminal navigate to modprobe.d
Then type in sudo gedit alsa-base.conf
Then enter.

The sudo gives you root user permission and gedit is the text editor to open the file.

Make your changes and save.

If you don't like to use the terminal you can do it graphically by typing sudo nautilus in a terminal and a root file browser will open after you type in your password.
In the root file browser select filesystem.
Then etc, then modprobe.d, then alsa-base.conf
Do your copy and paste then save.

Hope this helps
Good luck

---

### Post by zblip2 on 2009-09-21
Thanks so much! But I'm so new at this that the vocabulary you use is a bit foreing to me for instance:


> **majiciannz said:**
> 
In a terminal navigate to modprobe.d
Then type in sudo gedit alsa-base.conf
Then enter.Good luck

What is a terminal? I mean a terminal is a computer wired to a sever isn't it? I don't have that at home so there must be another signification to this....

''Then type in sudo gedit alsa-base.conf"

 Do you mean by this:

Type in the following line: ''sudo gedit alsa-base.conf"

or do you mean:

Type in sudo the following line: ''gedit alsa-base.conf"



> **majiciannz said:**
> 
If you don't like to use the terminal you can do it graphically by typing sudo nautilus in a termina

Again the terminal (2x), and the typing ''sudo naytilus''


Am I the only one not understanding all of this? I feel so stupid...

---

### Post by zblip2 on 2009-09-21
STOP THE PRESSES! IT WORKED! i FINALLY FUGURED OUT WHAT TERMINAL WAS AND FROM THERE ON IT WAS SIMPLE. THANKS GUYS!

---

### Post by majiciannz on 2009-09-21
You've brought a smile to my dial. So happy you figured it out.

Cool

---

### Post by majiciannz on 2009-09-22
Perhaps this thread should be marked as solved.

---

### Post by darkG20t on 2009-12-02
Thanks a ton, this worked for my HP dv3t too. Additionally I didn't know about "sudo nautilus" either, thanks a lot!

---

### Post by hoeq on 2010-01-08
Thanks! Finally I got my dv3610 speakers to work! :D

---

### Post by kaffemonster on 2010-02-04
Awesome job, thanks mate :)

Just wanted to chime in: This works perfectly for the oooh-so sweet HP Probook 5310M

---

### Post by kaffemonster on 2010-02-05
Bummer - Mic input not working at all... Any ideas anyone?

---

