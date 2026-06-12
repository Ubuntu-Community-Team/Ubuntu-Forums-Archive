---
title: "[Solved]Can't save changed LXDM.CONF file in /etc/xdg/lubuntu/lxdm"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by Koenraads on 2013-05-10
In order to have the _num lock automaticly on after booting_ the computer, I found out that in the** lxdm.conf** file the numlock has to be uncommented and set to 1. (unther the root /etc/xdg/lubuntu/lxdm)
So far no problem. When I try to save the changed document, I first get the question that it already exists and if I want to replace it, but when I say yes I get the message that he can't OPEN the document?!

Any idea's?
Thx.

---

### Post by 2F4U on 2013-05-10
Are you editing with sudo privileges or as a normal user? Since the file is in /etc you need to have administrative rights.

---

### Post by Koenraads on 2013-05-10
I use the LXTerminal and navigate to /etc/xdg/lubuntu/lxdm$
If from that position I run the following command:
sudo xdg-open lxdm.conf I get the following error.

schoonjans@Vic:/etc/xdg/lubuntu/lxdm$ sudo xdg-open lxdm.conf
[sudo] password for schoonjans: 
Warning: unknown mime-type for "lxdm.conf" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
[3510:3510:0510/165852:ERROR:chrome_browser_main_extra_parts_gtk.cc(51)] Startup refusing to run as root.
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: firefox: not found
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: mozilla: not found
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: epiphany: not found
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: konqueror: not found
[3517:3517:0510/165948:ERROR:chrome_browser_main_extra_parts_gtk.cc(51)] Startup refusing to run as root.
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: google-chrome: not found
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: links2: not found
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: links: not found
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: lynx: not found
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: w3m: not found
xdg-open: no method available for opening 'lxdm.conf'

therefore I open it with my normal user who is administrator. :-(
I'm new in the linux world, sorry.

---

### Post by cortman on 2013-05-10
Just run

```
gksu leafpad /etc/xdg/lubuntu/lxdm/lxdm.conf
```

---

### Post by Werne on 2013-05-10
> **cortman said:**
> Just run

```
gksu leafpad /etc/xdg/lubuntu/lxdm/lxdm.conf
```

Lubuntu doesn't come with gksu installed, first  run
```
sudo apt-get install gksu
```
to install gksu and then the above command cortman wrote.

---

### Post by Koenraads on 2013-05-10
This worked just fine. The line I wanted to change in the rootfile/folder  LXDM.CONF (## uncomment and set to set numlock on your keyboard - numlock=1) worked. :-)
This was very helpfull. 
I'll start up a new threat because the num lock is still off after reboot. :-(

thx.

---

### Post by cortman on 2013-05-10
> **Werne said:**
> Lubuntu doesn't come with gksu installed, first  run
```
sudo apt-get install gksu
```
to install gksu and then the above command cortman wrote.

Whoops, thanks for catching that. I hadn't been aware of it.
@OP: Glad it's solved- please edit the thread title (in the first post) and add [SOLVED] so others can benefit as well. Good luck!

---

