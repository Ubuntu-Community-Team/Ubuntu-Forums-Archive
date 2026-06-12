---
title: "ChrUbuntu mount error/authentication issues/iomem error"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by Gigaswipe on 2013-06-15
To start, let me say that I'm absolutely new to Linux/Ubuntu/etc. I bought an Acer C7 chromebook as it was cheap, then discovered I could put Linux on it and use it like a real computer instead of just a glorified browser. I installed it from [http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html](http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html) and this worked perfectly-ish. 

Heres where my problems are. I set up the account as not requiring a password for login. Yet to unlock, I need a password of some sort. To install ChrUbuntu, the username and password was "user." Obviously that isn't working. Ive been looking for answers elsewhere, and i've seen that I need to reach the "GRUB?" Problem is, there is no boot screen for me to hold SHIFT and open the GRUB menu from. I get an er[SIZE=2]ror: "invalid Iomem error. you may experience problems." does this have anything to do with that? Also, when i open my Home Folder in Ubuntu (because I can use the Os, I cant change anything about the account though) I have 4 devices. There are two "ROOT-A" and neither will "mount." I dont mind if it isnt spmething that can, but I like to keep my workspace tidy. The other two devices are 9.6 GB Filesystem (which is probable GoogleOs) and "OEM" which I dont know what that is.

I know it's a lot to ask, but I don't know what I'm doing. Im not opposed to wiping and starting over, but I just need help :(

Edit: This also means I cant download, like Skype which I desperately need :([/SIZE][/FONT]

---

### Post by oldrocker99 on 2013-06-21
The 12.04 version of Chrubuntu gives everyone the iomem error, and I have had no problems. 

I just upgraded to 13.04. Yes, I had to wipe and start over. I (hating Unity) used:

curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd lubuntu-desktop latest

And it worked perfectly for me.

Chrubuntu does not use GRUB, just so you know. You'll get kernel upgrades, but you'll still be using the custom Chrubuntu kernel, which is 3.4. 

IF you can get the system to accept the 'user' password, I strongly urge you to open Users And Groups, and create a new user, with your own name and password. Make 100% sure that you give yourself Administrator access. You might also look at Groups for sudoers, and make sure your username is checked there.

By the way, the various *buntu names refer to the GUI included. Ubuntu uses Unity, which a lot of people like (and it is pretty advanced, with some features that NO other GUI has), and a lot of people (such as I) who don't. I chose lubuntu-desktop, which is a nice, lightweight, low memory-using GUI. Xubuntu uses XFCE, which is similar to LXDE, which a lot of people like, and Kubuntu uses KDE, which has its detractors, but is the most mature, and by far the most configurable GUI for any OS.

There's also razor-qt, which is built using the QT toolkit (as is KDE) and is very lightweight, and MATE (pronounced MAH-tay, named after the Argentinian caffeniated herb so popular there), which is a fork of the old GNOME 2.x interface, which Ubuntu used until a couple years ago, and which long-time Linux users (for example, myself) like. There's also Cinnamon, which is an attempt to produce a GUI based on GNOME 3 which doesn't irritate people the way GNOME 3 does, and a number of other GUIs available.

It's a very simple matter to install a different GUI in GNU/Linux, since "free software" doesn't just mean no cost: it means FREEDOM. Try installing a different GUI in Windows or OSX, and you'll start to realize that Linux gives YOU 100% control over your computer, rather than an OS that "lets" you do some things, and keeps you from doing others.

By the way, GMail has videochat which is just as good as Skype.

And this website:[http://cr-48.wikispaces.com/Dual+Boot+Shortcuts](http://cr-48.wikispaces.com/Dual+Boot+Shortcuts)
will tell you how to add a "chromeos" command to Ubuntu, and a "ubuntu" command to ChromeOS, so you can type a single command and reboot into the other OS.

And don't be afraid of The Big Bad Penguin. And thanks for asking your question, and welcome to the GNU/Linux community! Sorry it took me 5 days to see your post.

---

### Post by temujin1 on 2013-06-22
If one likes Unity, how should the script you posted be modified?

---

### Post by oldrocker99 on 2013-06-23
curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd default lts [installs 12.04 with Unity]

curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd default latest [installs 13.04 with Unity]

is how you do it.

---

### Post by temujin1 on 2013-06-24
Neither script worked for me. I ran the second one and it said "-sh: 1: curl: not found", then asked for the sudo password, then said "bash: s9ryd: No such file or directory". When I ran the first script, it said "-sh: 2: curl: not found", but without asking for my password.

---

### Post by temujin1 on 2013-06-25
Could someone help, please?

---

### Post by temujin1 on 2013-06-26
Update: tried running sudo apt-get install curl. Result was this:

Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) raring/main curl armhf 7.29.0 -1ubuntu3
   Something wicked happened resolving 'ports.ubuntu.com:http' (-11 - System error)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I've looked this up, and come across threads like [this one]("http://askubuntu.com/questions/111597/how-can-i-work-around-something-wicked-happened-resolving-mirror-errors"), which I have no idea how to follow. Someone *please* help!!!

---

### Post by 23senick on 2013-06-26
I used an earlier version of Chrubuntu for my Samsung S550. Worked perfectly (tho see later). All I did for the user name was went into user accounts after installing and changed my user name and password. Was simple but as I mentioned it was an earlier version of the script so not sure if its different now.  

One caveat, the battery became an issue. It took two replacement laptops before I realised that charging with the chromebook on while booted into Ubuntu was destroying the battery. It quickly went down to 92%.  Now I only charged it with the chromebook switched off and it's fine, still lasts 7 or 8 hours.

---

### Post by temujin1 on 2013-06-27
I think part of the issue was that I was not connected to wifi when trying to install Unity. This time I waited to connect before entering the command, and it did appear to work -- it spent several minutes installing, asked me about encoding, and then rebooted -- but when I logged in again, I was still in the terminal. When I entered "startx", it just said "not found"...

---

### Post by oldrocker99 on 2013-06-28
I just read someone suggest that, at the terminal screen, hit CTRL-d, as your Xscreen may be covered with a full-screen terminal.

Try it, anyway.

---

### Post by temujin1 on 2013-06-28
Thanks for the suggestion -- I will try that after this post.

This morning, having gone through what I think was the Unity installation process (see my post from yesterday), I entered the same command again in the Chrome OS dev console after waiting for Chrome OS to connect to wifi. It worked, I think, and went through the whole installation process again (and, I think, a bit further). After it rebooted into the ChrUbuntu terminal, I entered the script again and it said "Not found", like before. Should I enter some command to connect to wifi first? I don't think ChrUbuntu is connecting automatically to wifi like Chrome OS does.

Also, is Unity actually installing? I'm concerned that installing Unity multiple times will clutter up the OS....
[B]
UPDATE:[/B] Ctrl+D didn't work; it just signed me out of ChrUbuntu. startx still not working also.

---

### Post by temujin1 on 2013-06-29
bump bump bump bump bump

---

### Post by temujin1 on 2013-07-01
bump bump bump bump bump

---

### Post by temujin1 on 2013-07-02
bump bump bump bump bump

---

