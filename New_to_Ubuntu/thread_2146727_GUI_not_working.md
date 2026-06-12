---
title: "GUI not working"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by 3wais on 2013-05-19
Hi, I was messing with some packages and repositories and i think i messud up something. after restart gui did not work.I tried : ```
sudo service lightdm start 
``` it did not work. i then tried ```
 startx 
``` and it generated this error : ```
 /usr/bin/X not found 
``` as far as i remember. i then executed this command ```
 sudo apt-get install xserver-xorg 
``` successfully.now when i try to run startx again it generates a low graphics gui box saying failed to load session "ubuntu". whan i run lightdm start it generates a low graphics box saying:the system is running in low graphics mode, your screen graphics card and input device settings cannot be detected correctly.you will need to configure these yourslef.i press ok it then asks me if i want to troubleshoot or configure or run in low quality mode for just one session.none of these work. I'm then forced to return to ttys.can anyone help ? I'm using elinks from command line right now so I'm sorry for bad typing and code wrapping and so.

---

### Post by sp-1070 on 2013-05-19
lightdm isnt a service use sudo lightdm without service or start give that a shot

---

### Post by 3wais on 2013-05-19
I tried that too. did not work.and yes lightdm is a service.type service in command line and press tab twice and lightdm is listed among others.and also that command used to work just right before.

---

### Post by Cheesemill on 2013-05-19
Try reinstalling the desktop packages...
```
sudo apt-get install ubuntu-desktop
```

---

### Post by 3wais on 2013-05-19
thanks. that worked :)

---

### Post by Jules3766 on 2013-05-20
Having the same problem regarding the GUI.  The system can't find files -- as if the env paths are not working or incorrect.  I logged on with my account and to get root access have to enter su (sudo and kdesudo are not working at all) and have root access.  When I type apt-get install Ubuntu-desktop == the system returns [bash: apt-get: command not found]  Can you please provide the full path to this apt-get location?

---

### Post by steeldriver on 2013-05-20
It looks like your PATH is missing /usr/bin (or possibly /usr is not mounted)

```
$ which apt-get
/usr/bin/apt-get
$ which sudo
/usr/bin/sudo
$ which su
/bin/su
$
```

You can try either giving the full path to the program, or just add /usr/bin back to your path

```
export PATH=$PATH:/usr/bin
```

or you could reset PATH to its default value

```
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

or possibly even try

```
export $(/bin/cat /etc/environment)
```

These only apply to the current terminal, so you'll want to figure out why your setup is broken and fix it though (possibly something you entered in your ~/.bashrc or ~/.profile files)

---

