---
title: "Dual boot Ubuntu and Xubuntu"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Wils on 2008-08-09
I would like to install Ubuntu as the main OS on the laptop. Can I dual boot Ubuntu with Xubuntu later if I wish?

---

### Post by finer recliner on 2008-08-09
you can install both desktop environments on the same partition (OS). when you log in, you can choose which environment you want to use. does this make more sense for you?

if this sounds more appropriate for you, install ubuntu normally, then do:
```
sudo apt-get install xubuntu-desktop
```

---

### Post by Wils on 2008-08-09
The only bit I have trouble with is where and how do I put the code in, thanks for the reply

---

### Post by pi.boy.travis on 2008-08-09
You can also keep Xubuntu separate if you wish.  Just boot into the Ubuntu live CD, go to System-Administration-Partition Editor.  Shrink down your Ubuntu partition, then use the Xubuntu live CD to install.  If you choose to set up partitions manually in the installer, you can have Ubuntu and Xubuntu share the swap partition.

---

### Post by Tsurugi13 on 2008-08-09
Would the same thing work with kubuntu subbed for xubuntu?

Also, the code (to my knowledge) should just go in a terminal.

---

### Post by Wils on 2008-08-09
> **Tsurugi13 said:**
> Would the same thing work with kubuntu subbed for xubuntu?

Also, the code (to my knowledge) should just go in a terminal.

I am unsure what benifits are with kubuntu over xbuntu

---

### Post by pi.boy.travis on 2008-08-09
> **Wils said:**
> I am unsure what benifits are with kubuntu over xbuntu

It's more about personal taste, and yes, it's possible with Kubuntu as well.

```
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
```

Not sure about Ubuntu studio. . .

BTW Xubuntu is really lightweight, so it's ideal for low resource systems or ALAP systems.
Kubuntu is most similar to Windows.
Ubuntu uses GNOME, my personal favorite desktop environment.

---

### Post by finer recliner on 2008-08-09
> **Wils said:**
> The only bit I have trouble with is where and how do I put the code in, thanks for the reply

type that command in the terminal:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by appier on 2008-08-10
I installed Ubuntu on a machine in my classroom at school, later installed the xubuntu desktop, and then later installed the kubuntu desktop.  The application trees are getting complex, but it would appear that everything works in all of the desktops.

---

### Post by Wils on 2008-08-10
> **pi.boy.travis said:**
> It's more about personal taste, and yes, it's possible with Kubuntu as well.

```
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
```

Not sure about Ubuntu studio. . .

BTW Xubuntu is really lightweight, so it's ideal for low resource systems or ALAP systems.
Kubuntu is most similar to Windows.
Ubuntu uses GNOME, my personal favorite desktop environment.

After I type in the code it asks for a password, but I cant not type anything I press enter and I get ased for the password

---

### Post by Reiger on 2008-08-10
Type the password you use to log onto your PC as User.

---

### Post by GuitarMatt on 2008-08-10
> **Wils said:**
> After I type in the code it asks for a password, but I cant not type anything I press enter and I get ased for the password

When u type the password it hides the letters. just type your password and hit return

Matt

---

### Post by Wils on 2008-08-10
> **GuitarMatt said:**
> When u type the password it hides the letters. just type your password and hit return

Matt



sorry guy's but it will not let me type anything

---

### Post by Paqman on 2008-08-10
> **Wils said:**
> sorry guy's but it will not let me type anything

Just type in your password and hit enter anyway. It's normal for it to not look like it's doing anything.

---

### Post by Wils on 2008-08-10
> **pi.boy.travis said:**
> It's more about personal taste, and yes, it's possible with Kubuntu as well.

```
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
```

Not sure about Ubuntu studio. . .

BTW Xubuntu is really lightweight, so it's ideal for low resource systems or ALAP systems.
Kubuntu is most similar to Windows.
Ubuntu uses GNOME, my personal favorite desktop environment.

ok I have entered the code and kubuntu starts up but i still can not enter the desktop

---

### Post by Wils on 2008-08-10
> **finer recliner said:**
> type that command in the terminal:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

thanks good link

---

### Post by nodnarb83 on 2008-08-10
> **Wils said:**
> After I type in the code it asks for a password, but I cant not type anything I press enter and I get ased for the password

Sorry to jump in, but when it asks for your password, what you type in will never show up.  Just type in your normal password and hit enter.

Oops... they already beat me to it...

---

### Post by finer recliner on 2008-08-11
> **Wils said:**
> ok I have entered the code and kubuntu starts up but i still can not enter the desktop

okay, after you installed an alternative desktop environment (kubuntu for KDE, and xubuntu for XFCE), you restart the computer, and when you get to the login screen, click the options button in the lower left corner, and from there you should be able to pick which desktop environment you want to use for that session. then continue to log in with with your username and password

---

