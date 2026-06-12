---
title: "Activating Hibernate"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by jrosado on 2013-04-29
I'd like to activate hibernate on xubuntu Raring Ringtail 13.04.  It is inactive by default.  I could use some help.

I found a  fix that said to:
go to the directory /etc/polkit-1/localauthority/50-local.d/ and create the file com.ubuntu.desktop.pkla (that's a lowercase 'L' in the extension and not the number '1'). You'll need to use sudo. Add the following content:
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes 

1. I found that directory, but don't see how to create a new file.
2. How do I  "use sudo" ?

---

### Post by lykwydchykyn on 2013-04-30
The simplest way to do this is open a terminal, use the "cd" command to go to the directory:
```

cd /etc/polkit-1/localauthority/50-local.d/

```
Then create the file using sudo and your text editor like so:
```

sudo mousepad com.ubuntu.desktop.pkla

```

Paste in your text and save.

"using sudo" means prefixing a command with the word "sudo"; it basically tells the system, "do the following command as the root (admin) user".

---

### Post by nerdtron on 2013-04-30
In sequence, (assuming you'll just follow the steps you want, I don't know if this will really enable hibernation)

Move the the directory you want:
```
cd /etc/polkit-1/localauthority/50-local.d/
```
Create the file:
```
sudo touch com.ubuntu.desktop.pkla 
```
Edit the file:
```
sudo nano com.ubuntu.desktop.pkla
```

While inside nano, add the following lines:
```
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```

Press CTRL+O to save it.
Press CTRL+X to close it.

---

### Post by fantab on 2013-04-30
One of the important prerequisites for activating 'Hibernate' is the size of your SWAP partition to be equal to or greater than your RAM in GiB, not GB. Otherwise you may experience issues later.

---

### Post by DuckHook on 2013-04-30
Firstly, addressing hibernate.

The reason hibernate was disabled in the various 'buntus was because some people were unable to resume from hibernate and thus losing data while trying to use it. It isn't entirely dependable. If you are prepared to accept this risk, then it's possible to re-enable it.

Before doing so, you ***must*** have already met the following preconditions:
1. You have a working SWAP partition.
2. SWAP partition is at least as large as your system RAM in GiB (not just GB--if unsure, Google the difference).
3. You do not have SWAP encrypted.

If all above conditions are met, then *you must test it first*!

1. You will be monkeying around with system files so back up all important data. If you fail to do this, and the next steps render your computer unbootable, then, given this warning, I will refuse to help you recover it!

2. Open a terminal and type```
sudo pm-hibernate
```...that is how you use "sudo". It gives you temporary root privileges for the one command that follows it. This is an excellent Ubuntu security measure that should not be disabled or changed. If your system is capable of hibernation, it will now do so. Make sure that you can resume from hibernation before changing any system files.

3. We want to open gedit as root to make a file with root ownership and privileges. To do so, we use a variant of *sudo* for graphical apps: *gksudo*. Do:```
gksudo mousepad /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```...you can use your filename if you prefer. The filename is unimportant. What matters is the content, which is next.

4. Type (or better--copy and paste) the following into the empty mousepad file:```
[Enable Hibernate]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```
5. Save the file, exit mousepad, then logout, login and the hibernate option should be visible again as a choice on your power-down menu.

Finally, addressing *SUDO*, which is in many ways the more important question.

If you are asking about *sudo*, then you are very new to Ubuntu and still very much in the learning phase about Linux behaviour. This is the time when you can get into big trouble because you are tempted to try making system changes that create consequences you are not even aware of. Therefore, I highly encourage you to read these introductions before you do anything further; even before you activate hibernation.

"Linux is not Windows" intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

General Ubuntu Intro:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

******And especially with regard to SUDO******

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Be sure to read this last one, as it not only answers your questions about *sudo*, but instructs you on safe and best practices.

<edit>

I originally gave you instructions for Ubuntu, and noticed only later you are using Xubuntu. Above instructions should now be corrected for Xubuntu.

</edit>

---

### Post by jrosado on 2013-05-01
A very sincere thank you to all the kind folks who replied.

In the advice offered were some cautions that I'm taking seriously.

Although I've been working with computers since the early 1970s (cobol, fortran, even Trash 80 and basic, CP/M, DOS and Windows from before it was even released), these excellent suggestions made me realize both how little I know of this OS and how much trouble I can get into by playing around with things I shouldn't - at least until I know a whole lot more about the system.

The links to learn more about what I need to know are very much appreciated and have been read carefully and saved.

Hibernating this laptop is not nearly as important to me as learning what I need to know.  So hibernate can wait.

The cordial support from a friendly community has warmed this old codger's heart and made me appreciate Ubuntu all the more.

Mahalo nui loa (thanks very much) and aloha from Hawai'i.

---

