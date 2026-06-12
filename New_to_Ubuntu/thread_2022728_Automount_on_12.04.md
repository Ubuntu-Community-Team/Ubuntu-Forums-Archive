---
title: "Automount on 12.04"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by quirino77 on 2012-07-11
Hello.

I was using automount for some time. But after i migrate to 12.04 (clean install - 64 bits), my automount stopped working. I had tried changing many things, but no success.

I had read there is a but on autofs with 12.04. Is it true or i am doing something wrong?

My auto.master:
/home/user/Desktop/goflex     /etc/goflex.cifs        --timeout=120 --ghost

My goflex.cifs:
public -fstype=cifs,ro,noperm,user=userA,pass=A,soft,async,noatime         ://192.168.0.253/goflex home public
personal -fstype=cifs,ro,noperm,user=userA,pass=A,soft,async,noatime         ://192.168.0.253/goflex home personal

---

### Post by quirino77 on 2012-07-13
Nobody?

---

### Post by NikTh on 2012-07-13
Hi ,
you can try this command . Copy-paste from here to you terminal for accuracy. 
```
dconf write /org/gnome/desktop/media-handling/automount '"true"'
``` 

See if problem corrected . 
Thanks

---

### Post by quirino77 on 2012-07-13
Thank's for your help. But didn't work.

Anyway, i get this error (nothing changed with dconf).


user@user:~$ sudo automount -v -f
Starting automounter version 5.0.6, master map /etc/auto.master
using kernel protocol version 5.02
syntax error in nsswitch config near [ syntax error ]

lookup(file): failed to read included master map auto.master
mounted indirect on /home/user/Desktop/goflex/read with timeout 120, freq 30 seconds
ghosting enabled
attempting to mount entry /home/user/Desktop/goflex/read/.hidden
lookup(program): lookup for .hidden failed
failed to mount /home/user/Desktop/goflex/read/.hidden
^Cumounted indirect mount /home/user/Desktop/goflex/read
shut down path /home/user/Desktop/goflex/read
autofs stopped

---

### Post by NikTh on 2012-07-14
> **quirino77 said:**
> Thank's for your help. But didn't work.

Anyway, i get this error (nothing changed with dconf).

Hi , 
Yes. Command is probably wrong. Read here --> [http://ubuntuforums.org/showthread.php?t=2024443](http://ubuntuforums.org/showthread.php?t=2024443)
Thanks

---

### Post by quirino77 on 2012-07-15
I got the solution.

Firt mistake, my auto.master has:
+auto.master
then i comment this line and the "lookup(file): failed to read included master map auto.master" was gone. Looks like with this line, it search for the file on a NIS.

Second mistake, my goflex.cifs has execute attribute. The autofs do not work this way. I had to chmod -x the file.

Now everything is ok.
Thank's.

---

