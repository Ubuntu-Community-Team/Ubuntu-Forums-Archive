---
title: "Can Tally program work on ubuntu"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by munezz on 2012-04-02
Hi! just a general doubt..............................does Ubuntu support Tally accounting program.

---

### Post by Bill Z on 2012-04-02
I found this for you on Google.

[https://answers.launchpad.net/ubuntu/+question/23104](https://answers.launchpad.net/ubuntu/+question/23104)

I am afraid that no software in ubuntu that matches up exactly as tally There are softwares like GNU Cash which are financial packages but not India specific. Tally is available on Red hat linux but you have to end up paying for it..
Or an alternative would be running tally under wine (Windows Emulator) But I'm afraid If the software fails to obtain a license it works in a limited functionality (Educational) mode. Features in education mode seem to work. and on obtaining a license,the software gives a memory violation error and exits.

Sorry for BAD NEWS

Bhavani Shankar

---

### Post by Frogs Hair on 2012-04-02
What I have found so far suggests that you would have to install via Wine or run Windows in V box. There was one reference to Tally working with Red Hat five years ago . A Wubi installation is for trail and has limited disk space , so how much data you are planning to store would be a consideration . Backup would be very important if using Wubi because it can be unstable for some users.

---

### Post by munezz on 2012-04-02
yeah............I'm aware of this too.............but in my workplace some say that it'll work fine on wine............so any better examples to convince them..................u see i don't want to make them look stupid..................:p

---

### Post by oldos2er on 2012-04-02
> **munezz said:**
> Hi! just a general doubt..............................does Ubuntu support Tally accounting program.

Doesn't look good: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=328](http://appdb.winehq.org/objectManager.php?sClass=application&iId=328)

---

### Post by munezz on 2012-04-03
ok thanks for that..................now one more help.............with tally we can generate reports directly to MS Excel..............any suggestions to make it go to Libre Office as well............I have Libre Office windows version too.....:p

---

### Post by flurospar on 2012-04-03
LibreOffice works in Ubuntu, but please run the native version of LibreOffice on Linux, not the Windows version! To install LibreOffice, type into the terminal:

```
sudo apt-get install libreoffice
```

However, if you do have Microsoft Office, you can run it in Linux using Wine.

---

### Post by munezz on 2012-04-03
> **flurospar said:**
> LibreOffice works in Ubuntu, but please run the native version of LibreOffice on Linux, not the Windows version! To install LibreOffice, type into the terminal:

```
sudo apt-get install libreoffice
```However, if you do have Microsoft Office, you can run it in Linux using Wine.

I have LibreOffice in both the OS,no problem in that.................what I want to know is can I generate Reports from Tally directly to LibreOffice.....................Tally works fine in Windows and it is compatible with MS Excel. My office has people using both Windows & Ubuntu and my work involves providing reports to both these users.So if there were an option to generate reports to LibreOffice as well it would help me a lot.:p

---

