---
title: "gnome GUI does not start"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by beard3dgeek on 2013-01-19
Hi all,

I have installed ubuntu server on my machine, I then installed gnome gui ontop of this. however when i try to start the GUI all I get is the background image. no menus/option (like it normally looks) can any one help on what i might be doing wrong.

sorry if this doesnt make sense, i tried to explain it as much as i could. Please let me know if you need more info

---

### Post by ibjsb4 on 2013-01-19
What command did you use to install?

---

### Post by mcduck on 2013-01-19
+1 to above, and also how are you starting the GUI? Are you using some display manager? If yes, which one?

---

### Post by beard3dgeek on 2013-01-19
> **ibjsb4 said:**
> What command did you use to install?

I used aptitude to install it 

```
aptitude installe gnome
```

i then install xrdp so that i can remote onto the machine. otherwise i used to run the command

```
starx
```

I now get a message saying 

Nautilus could not create the required folder "/home/geek/.config/nautilus

when i checked the permissions for the file its owned by root, is this correct ??

---

### Post by mcduck on 2013-01-19
No, the permissions are definitely wrong. Everything in your own home directory should be owned by you.

Run this to recursively change ownership of your home directory & everything within, and then try starting the desktop again:

```
sudo chown -R geek:geek /home/geek
```

---

### Post by ibjsb4 on 2013-01-19
```
aptitude installe gnome
```That is not a valid command and will not install anything.

What are you trying to install?  And is this 12.04 or 12.10?

Edit:  McDuck has you covered, good luck :)

---

### Post by beard3dgeek on 2013-01-19
> **ibjsb4 said:**
> ```
aptitude installe gnome
```That is not a valid command and will not install anything.

What are you trying to install?  And is this 12.04 or 12.10?

Edit:  McDuck has you covered, good luck :)

sorry my bad  ... spelling mistake this is what I ran

```
sudo aptitude install gnome
```

mcduck, I tried that. All im getting is the desktop background. any ideas ?

---

### Post by ibjsb4 on 2013-01-19
> **beard3dgeek said:**
> sorry my bad  ... spelling mistake this is what I ran

```
sudo aptitude install [COLOR=Red]gnome[/COLOR]
```

Still an invalid command.

[COLOR=Red]Gnome[COLOR=Black] is not correct.
[/COLOR][/COLOR]

---

### Post by mcduck on 2013-01-19
Have you configured your .xinitrc file  to actually load Gnome? I believe you need to do that since you aren't using any display manager to define which session to load.

---

### Post by beard3dgeek on 2013-01-19
> **ibjsb4 said:**
> Still an invalid command.

[COLOR=Red]Gnome[COLOR=Black] is not correct.
[/COLOR][/COLOR]

sorry i just checked my history ... i did gnome-shell

---

### Post by beard3dgeek on 2013-01-19
> **mcduck said:**
> Have you configured your .xinitrc file  to actually load Gnome? I believe you need to do that since you aren't using any display manager to define which session to load.

can you help me out mcduck. I havnt setup a .xinitrc file.

my setup is as follows.

I have a microserver, ubuntu server on it. I have installed gnome just because i am still learning. what i wanna be able to do is remote desktop onto the server just when i cant do something through the terminal. 

so my question is :- is it possible to have gnome startup when i remote desktop onto the server ? then when im not remote desktoping it quits ? is this even possible or am i jus dreaming things up ?

sorry if this sounds stupid, im new to ubuntu !!

---

### Post by mcduck on 2013-01-19
> **beard3dgeek said:**
> can you help me out mcduck. I havnt setup a .xinitrc file.

my setup is as follows.

I have a microserver, ubuntu server on it. I have installed gnome just because i am still learning. what i wanna be able to do is remote desktop onto the server just when i cant do something through the terminal. 

so my question is :- is it possible to have gnome startup when i remote desktop onto the server ? then when im not remote desktoping it quits ? is this even possible or am i jus dreaming things up ?

sorry if this sounds stupid, im new to ubuntu !!
Sounds like it should be possible, but I have no experience with remote desktop connections.

Anyway, there's a pretty good guide to .xinitrc here: [https://wiki.archlinux.org/index.php/Xinitrc]("https://wiki.archlinux.org/index.php/Xinitrc") (It's for Arch, but should work just as well with Ubuntu).

Also perhaps you could apply something like this to get the X to start when you connect to the server: [http://linuxexpresso.wordpress.com/2010/10/03/startx-automatically-on-login-ubuntu/]("http://linuxexpresso.wordpress.com/2010/10/03/startx-automatically-on-login-ubuntu/").

---

