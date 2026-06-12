---
title: "[SOLVED] Good Anti-Virus Program?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by mitar on 2008-05-10
What's good antivirus program for Linux?

---

### Post by lespaul_rentals on 2008-05-10
Avast! is my personal favorite.

[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

---

### Post by Biggy on 2008-05-10
in linux has no antivirus or virus

has bad command

---

### Post by lespaul_rentals on 2008-05-10
> **Biggy said:**
> in linux has no antivirus or virus

has bad command

What are you talking about?  Linux has several anti-virus applications.  Linux also has about 900 viruses.  Are any of these running around infecting machines?  No.  But if he wants to know a good anti-virus application, just answer the question at hand.

---

### Post by tamoneya on 2008-05-10
i use clamAV which seems to work well yet I have heard good things about avast as the above poster mentioned.  While linux may have no current virii in the wild it is still important to consider virii since you may download a windows virus and inadvertently pass it on to one of your friends who runs windows.  By using antivirus you prevent this from occuring.

---

### Post by mitar on 2008-05-10
Ok. that solved the problem. By the way, how do I mark thread as solved. Up there under thread tools there is no "mark thread as solved" option

---

### Post by tamoneya on 2008-05-10
that is where it should be but it has not be reimplemented since the forum upgrade 2-3 weeks ago.

---

### Post by mitar on 2008-05-10
one more thing. Now that is installed how do I run the program? I know where it went (usr/share/...) but I don't see the aplication to open the program

---

### Post by marty1011 on 2008-05-10
In order to add Avast! to the application menu type the following in the terminal:
```
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install
```

---

### Post by tamoneya on 2008-05-10
is this avast or clamAv? did you install from the repositories or from source?

---

### Post by mitar on 2008-05-10
> **marty1011 said:**
> In order to add Avast! to the application menu type the following in the terminal:
```
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install
```

How am I supposed to know this? Are there some rules for adding applications on this way? because I have one program that I need to "activate". It's xmms (usr/share). What should I type in terminal to get it?

---

### Post by marty1011 on 2008-05-10
Can I suggest an alternative to xmms? It is Audacious. I read it somewhere that xmms is a discontinued project ( I am not sure though.) In order to install Audacious type the following in terminal
```
sudo apt-get install audacious
```

---

### Post by mitar on 2008-05-10
> **marty1011 said:**
> In order to add Avast! to the application menu type the following in the terminal:
```
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install
```

> **marty1011 said:**
> Can I suggest an alternative to xmms? It is Audacious. I read it somewhere that xmms is a discontinued project ( I am not sure though.) In order to install Audacious type the following in terminal
```
sudo apt-get install audacious
```

ok, ok. where do you get all theses codes????

---

### Post by tamoneya on 2008-05-10
I am pretty sure that xmms is still active.  They did change the site from xmms.org to xmms2.org since their last release and this may have caused some of the confusion.
EDIT: it appears that they got 6 google summer of code projects.  That seems active to me.

---

### Post by bilijoe on 2008-05-10
> **mitar said:**
> ok, ok. where do you get all theses codes????
Still, no one has answered mitar's question about where to find any documentation on the commands and syntax for using *install, apt-get, aptitude, etc.*  I have the same question.  Is there a "how-to" or some other documentation that describes these commands/key words, and their use?:confused:

---

### Post by tamoneya on 2008-05-10
the most common commands: apt-get, aptitude as well as many others are on the ubuntu cheat sheet: [http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)  The way I typically figure them out when I forget the syntax though is ```
some_command --help
man help
```

---

### Post by kshtjsnghl on 2008-05-10
hi i installed avast 4 workstation but i am getting a problem while updating it. I have entered the license key but as soon as i click on the update database button it shows the error -
  "Connect failed ; Operation now in progress" 

and then nothing happens

I had added the avast to applications menu according to the previous posts..

---

### Post by marty1011 on 2008-05-10
> **tamoneya said:**
> I am pretty sure that xmms is still active.  They did change the site from xmms.org to xmms2.org since their last release and this may have caused some of the confusion.
EDIT: it appears that they got 6 google summer of code projects.  That seems active to me.

I see. Sorry for the wrong info, I thought xmms was removed from hardy because it was old and dead.

---

### Post by tamoneya on 2008-05-11
> **marty1011 said:**
> I see. Sorry for the wrong info, I thought xmms was removed from hardy because it was old and dead.

no harm done.  Install it from the repos if you like it is under xmms2

---

### Post by FreewheelinFrank on 2008-05-11
> **mitar said:**
> ok, ok. where do you get all theses codes????

[http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html](http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html)

---

### Post by Canis familiaris on 2008-05-11
> **mitar said:**
> What's good antivirus program for Linux?

You do not need an antivirus in Linux unless you have a server and wish to protect Windows machines.

---

### Post by ejpyle on 2008-05-11
> **mitar said:**
> What's good antivirus program for Linux?


Anti-virus? You mean Anti-windows?

As of today there are no known active viruses targeting Linux.

---

