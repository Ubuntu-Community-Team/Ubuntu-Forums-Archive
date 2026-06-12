---
title: "configure the dvd"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by soafy_san on 2008-06-25
hello ! in my laptop i have cd rewritable + dvd rom driver , when i put on dvd (for movie:popcorn: ) the driver , it seems that ubuntu didnt know it , i put cd it knew it and icon for cd appear in the desktop , i dont whats the problem ?
is it  cuz of it didnt know the dvd driver ? if yes how can i configure it ? or is it that i need particular program for read although i have movie player .

---

### Post by lostlinuxkiwi on 2008-06-25
you need to get codecs from the medibuntu repository. ubuntu cant include them for legal reasons, but you can get them here. 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

that page will tell you all you need to do :)

---

### Post by sayakb on 2008-06-25
Open a terminal and type in:
```
sudo apt-get install ubuntu-restricted-extras
```
This would install the necessary codecs.
Now open the DVD and open the VOB files in Movie player. 
Alternatively, you may install VLC media player and open the VOB files in VLC.

---

### Post by hyper_ch on 2008-06-25
if that doesn't work or you get a message about encryption and stuff, you'll need to install the libdvdcss2 package.

---

### Post by soafy_san on 2008-06-25
i installed ubuntu-restricted-extras  no result , and then i installed libdvdcss2  . but no use . i restarted the OS , but when i insert the dvd like nothing inserted . what should i do ?
:confused:

---

### Post by stchman on 2008-06-25
> **soafy_san said:**
> hello ! in my laptop i have cd rewritable + dvd rom driver , when i put on dvd (for movie:popcorn: ) the driver , it seems that ubuntu didnt know it , i put cd it knew it and icon for cd appear in the desktop , i dont whats the problem ?
is it  cuz of it didnt know the dvd driver ? if yes how can i configure it ? or is it that i need particular program for read although i have movie player .

I have tutorials to get your Ubuntu watching encrypted Hollywood DVDs.  Are you running 32 or 64 bit?  I will assume 32 bit.

Install the proprietary CODECs
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Install Medibuntu and libdvdcss2
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

You will be a media viewing person after this.

---

### Post by soafy_san on 2008-06-25
System--->Preferences--->Removable Drives and Media 
hey guys , i dont have multimedia portion why ???? i wanted to make vlc the default player for dvd , :(

---

### Post by soafy_san on 2008-06-25
hey guys thanks really for ur posts , but im really feel tired of that .
i think my OS doesnt know about the existing of dvd driver , i dont see any icon for dvd even when i wanted to replace the defualt player manually by edit /etc/gnome/defaults.list file , i saw in the site it must be written  x-content/video-dvd , but it contains /ogg = totem.desktop . 
 one more thing when i go to system> administration>synaptic.. >Repositories
it appears the universe checked ,main , restricted all are checked as well and source code has - sign . then written installable for cd-rom/dvd
then in the square written 
cdrom with ubuntu 8.04..
officially supported
restricted copyright 
besid it has empty square when i try to check and press revert it does nothing .
what is that mean ? 
how can be sure the ubuntu configure the dvd ?

---

### Post by hyper_ch on 2008-06-25
put a dvd into your drive and post the output of
```

ls -al /dev/dvd

```

---

### Post by soafy_san on 2008-06-25
i did , and here is the result 
lrwxrwxrwx 1 root root 4 2008-06-25 18:52 /dev/dvd -> scd0

---

### Post by WRDN on 2008-06-25
In the terminal, try using the command:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by soafy_san on 2008-06-26
i tried to open the dvd by vcl it shows that i have error 
and the error as is :  Unable to open 'dvd:///dev/scd0' 
what is that mean ?

---

### Post by alexcrossley on 2008-07-13
I am having the same issues and would really appreciate any assistance.  These are my results to some of the Q's

alex@XPS:~$ ls -al /dev/dvd
lrwxrwxrwx 1 root root 4 2008-07-13 20:12 /dev/dvd -> scd0

And VLC just tells me

Unable to open 'dvd:///dev/scd0'

---

### Post by outerspacerace on 2008-08-06
I'm getting this exact error from VLC when I use my DVD-ROM drive - yet in Totem the same drive works fine.

However, VLC plays discs from my burner fine, what's up I wonder?

---

