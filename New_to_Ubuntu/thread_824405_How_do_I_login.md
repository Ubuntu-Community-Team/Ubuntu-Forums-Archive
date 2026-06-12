---
title: "How do I login?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Yondergod22 on 2008-06-10
yay I finally got ubunutu up and running...or so I thought.:mad:
after the ubuntu splash screen I get a black screen that says:
  
  Booting command-list

Filesystem type is ntfs, partition type 0x7
  [Linux-bzImage, setup=0x2a00, size=0x1ce278]
  [Linux-initrd @ 0xf6e1000, 0x782f2e bytes]
loading please wait...

Ubuntu 8.04 taylor-desktop tty1

taylor-desktop login:
---------------------------------------------------------------
I figured I was supposed to type in my user name, so I did, and pressed enter and it asked for my password, but it wont let me type anything in. 

Thanks for you help:)

---

### Post by wolfen69 on 2008-06-10
when you type in your password, it doesnt show up. it's silent.

---

### Post by Epidemic_HardyBoy on 2008-06-10
Wait, you are typing your password, its just hiding it for security reasons, so type your password RIGHT then hit enter.

You will be logged in, then just hit ctrl+alt+f8 (or f7 i dont remember)

Hope this helps.

---

### Post by iaculallad on 2008-06-10
> **Yondergod22 said:**
> yay I finally got ubunutu up and running...or so I thought.:mad:
after the ubuntu splash screen I get a black screen that says:
  
  Booting command-list

Filesystem type is ntfs, partition type 0x7
  [Linux-bzImage, setup=0x2a00, size=0x1ce278]
  [Linux-initrd @ 0xf6e1000, 0x782f2e bytes]
loading please wait...

Ubuntu 8.04 taylor-desktop tty1

taylor-desktop login:
---------------------------------------------------------------
I figured I was supposed to type in my user name, so I did, and pressed enter and it asked for my password, but it wont let me type anything in. 

Thanks for you help:)

You cant see the password as you type but it's there. Just type your username and password after it prompt your login.
After a successful login, type **startx** on your terminal if it gets you to GUI.

---

### Post by rockerphil on 2008-06-10
sounds like a login manager didn't get installed, so you log in at the command prompt. you remember that user name and password you punched in when you installed Ubuntu? just punch in your user name, press Enter then enter your password (it's not gonna show up on a command line login) and it'll take you to a command line interface. the bad thing about that is you'll have to manaully start your window manager. here's what i'd do, once you get logged in type this

sudo apt-get install gdm

that will install the gnome display manager. which is a log in manager so that you can log in graphically and will start your window session for you, hope this helps.



Phil

---

### Post by Yondergod22 on 2008-06-10
thanks, that kinda worked, but now it says

-bash: /devnull: Permission Denied
and it repeats a bunch of times 
then it says 
taylor@taylor-desktop:~$

---

### Post by Yondergod22 on 2008-06-10
I did the sudo apt thing and it told me to run 'dpkg --configure -a', so I did that, and it says it requires superuser privilege.

---

### Post by iaculallad on 2008-06-10
> **Yondergod22 said:**
> thanks, that kinda worked, but now it says

-bash: /devnull: Permission Denied
and it repeats a bunch of times 
then it says 
taylor@taylor-desktop:~$

If you can log in as root, try to issue the command:

```
ls -l /dev/null
```

The value that you see should be similar with the line of text below:

> crw-rw-rw- 1 root root 1, 3

If not, delete (as root) /dev/null:

```
rm /dev/null
```

And recreate it:

```
mknod -m 0666 /dev/null c 1 3
```

That should enable you to execute your sudo command

---

### Post by Xiong Chiamiov on 2008-06-10
If you are able to login, but running
```

startx

```
doesn't work, it could very well be an issue with video card drivers.

---

### Post by Yondergod22 on 2008-06-10
> **iaculallad said:**
> If you can log in as root, try to issue the command:

```
ls -l /dev/null
```

The value that you see should be similar with the line of text below:



If not, delete (as root) /dev/null:

```
rm /dev/null
```

And recreate it:

```
mknod -m 0666 /dev/null c 1 3
```

That should enable you to execute your sudo command
It still says I need superuser privilege and what I got was similar, it just had -- instead of rw. but I just tried the other thing anyways, and it didn't work

---

### Post by Xiong Chiamiov on 2008-06-10
Ok, just to make sure I'm caught up, you can login as your normal user, correct?

What happens (specifically) if you run
```

sudo aptitude update; sudo aptitude install gdm

```

Those commands that iacullad gave you are meant to be entered as root (which he said, but indicating how).  Add the word "sudo" infront of them, eg
```

sudo ls -l /dev/null

```

---

### Post by Yondergod22 on 2008-06-10
> **Xiong Chiamiov said:**
> If you are able to login, but running
```

startx

```
doesn't work, it could very well be an issue with video card drivers.
nope it didn't work, the screen flickered and I saw some colors, and it went back to the black screen. so, I don't know much about computer, but yeah I guess it seem like a video card problem to me.

---

### Post by rockerphil on 2008-06-10
by default when you instll Ubuntu you're the superuser. but when you run a command that requires superuser privileges you need to type "sudo" before the command. like: sudo apt-get install gdm. that tells the computer that you want to run "apt-get" as the super user. once you enter the command you'll need to enter your password again (which again won't show up for security purposes)

oh, and it may simply be a resolution issue. so try running this command at your command prompt. 

sudo dpkg-reconfigure xserver-xorg

---

### Post by Xiong Chiamiov on 2008-06-10
> **Yondergod22 said:**
> nope it didn't work, the screen flickered and I saw some colors, and it went back to the black screen. so, I don't know much about computer, but yeah I guess it seem like a video card problem to me.
Ok, that sounds like a video card problem to me.  It'd still do you good to read the post I posted a split-second before you, but more importantly, can you give us the make and model of your video card please?

---

### Post by Yondergod22 on 2008-06-10
> **Xiong Chiamiov said:**
> Ok, that sounds like a video card problem to me.  It'd still do you good to read the post I posted a split-second before you, but more importantly, can you give us the make and model of your video card please?
I just have the onboard video card that can with it. it a Dell Dimension 2400

---

### Post by rockerphil on 2008-06-10
if it's just the on board video card with a pretty standard Dell then it shouldn't be a video card issue. like i said, try reconfiguring your xserver

sudo dpkg-reconfgiure xserver-xorg

---

### Post by iaculallad on 2008-06-10
> **Yondergod22 said:**
> I just have the onboard video card that can with it. it a Dell Dimension 2400

Run the command below on your terminal and post it:

```
lspci | grep VGA
```

---

### Post by Yondergod22 on 2008-06-10
> **iaculallad said:**
> Run the command below on your terminal and post it:

```
lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation 82845g/GL[Brookdale-G]/GE
hipset Integrated Graphics Device (rev 01)

---

### Post by iaculallad on 2008-06-10
Try re-configuring your video config:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Do answer the questions properly and use "good" guess if you don't know the answer.

---

### Post by Yondergod22 on 2008-06-10
> **rockerphil said:**
> if it's just the on board video card with a pretty standard Dell then it shouldn't be a video card issue. like i said, try reconfiguring your xserver

sudo dpkg-reconfgiure xserver-xorg
nope, just goes back to taylor@taylor-desktop:~$

---

### Post by Yondergod22 on 2008-06-10
> **iaculallad said:**
> Try re-configuring your video config:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Do answer the questions properly and use "good" guess if you don't know the answer.
it did ask any questions, it just said something about overwriting possibly-customized configuration

---

### Post by Xiong Chiamiov on 2008-06-10
After doing said command, you'll have to try
```

startx

```
again.

---

### Post by Yondergod22 on 2008-06-10
> **Xiong Chiamiov said:**
> After doing said command, you'll have to try
```

startx

```
again.

nope screen flickered again. but I just remember something, the live CD only worked in safe mode, I thought that might be important. and if this doesn't get solved within like 10 minutes I need to go to bed b/c its 1:15 AM. and hopefully you can try to help me again tomorrow.

---

### Post by CameO73 on 2008-06-10
I read about this specific problem [in this (old) thread](http://ubuntuforums.org/showthread.php?t=51954). The two solutions they offered were:

[LIST=1]
[*]install the latest BIOS from Dell (easiest) OR
[*]follow the steps [here](http://ubuntuforums.org/showthread.php?t=27029).
[/LIST]
I would first check the current BIOS version (usually displayed on startup ... for Dell it looks something like **A06**). If you have an older version than the one Dell is offering, you might give that a try.

Be warned that when BIOS flashing goes wrong, your PC won't start anymore. Nowadays it's not as big as a problem as it used to be, but keep it in mind!

If you don't like doing the BIOS flash (or it doesn't solve your problem), try the steps mentioned in option #2. Good luck!

---

### Post by peakshysteria on 2008-06-10
To reconfigure X. This is the right command for Ubuntu 8.04 Hardy Heron:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And not the code you said you tried on the bottom of page two here. That is the wrong command for Hardy. As you can see there are some differences.

---

### Post by Xiong Chiamiov on 2008-06-10
If you do end up having to update your BIOS (though that doesn't seem like the thing to me, but hey, odd things happen), I seem to remember that you have to first update to A26, then to A30 (or something like that).  You can't update all the way directly, but they don't tell you unless you happen to get a tech who knows (or find a forum post of someone who did, as did I).

---

### Post by Yondergod22 on 2008-06-10
> **peakshysteria said:**
> To reconfigure X. This is the right command for Ubuntu 8.04 Hardy Heron:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And not the code you said you tried on the bottom of page two here. That is the wrong command for Hardy. As you can see there are some differences.
I don't see any difference

---

### Post by Yondergod22 on 2008-06-10
> **CameO73 said:**
> I read about this specific problem [in this (old) thread](http://ubuntuforums.org/showthread.php?t=51954). The two solutions they offered were:

[LIST=1]
[*]install the latest BIOS from Dell (easiest) OR
[*]follow the steps [here](http://ubuntuforums.org/showthread.php?t=27029).
[/LIST]
I would first check the current BIOS version (usually displayed on startup ... for Dell it looks something like **A06**). If you have an older version than the one Dell is offering, you might give that a try.

Be warned that when BIOS flashing goes wrong, your PC won't start anymore. Nowadays it's not as big as a problem as it used to be, but keep it in mind!

If you don't like doing the BIOS flash (or it doesn't solve your problem), try the steps mentioned in option #2. Good luck!
I went to dells website and got the latest version, but its the same one I already have.
and for the second one do I need to be connected to the internet?

---

### Post by Yondergod22 on 2008-06-11
ok Give up for now, thanks for your help everyone that tried to help me. but im going to wait till I can get more RAM then ill install the normal way, instead of through windows.

---

