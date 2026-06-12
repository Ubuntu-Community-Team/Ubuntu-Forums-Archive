---
title: "/sbin/udevtrigger"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by rossjman1 on 2008-11-06
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#xscreensaver.2Fgnome-screensaver](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#xscreensaver.2Fgnome-screensaver)

> Save the following as /etc/udev/rules.d/60-thinkfinger.rules and run # sudo /sbin/udevtrigger (you may need to reboot for this to take effect if udev trigger does not work): 
```
jeff@jeff-laptop:~$ sudo /sbin/udevtrigger
sudo: /sbin/udevtrigger: command not found

```

Trying to get ThinkFinger to work with Gnome-Screensaver, but the command is not found :(

---

### Post by Sand Lee on 2008-11-06
In all probability it doesn't exist. I couldn't find it in my /etc directory at least. It may be a distro-specific thing towards fedora.

---

### Post by minchal on 2008-11-13
hi,

try
sudo /sbin/udevadm trigger

thats help me.

but two last steeps are bad too:
2. Make him owner of his bir-file: # chown $USERNAME:root /etc/pam_thinkfinger/$USERNAME.bir 
3. Give him read-only access to his bir-file: # chmod 400 /etc/pam_thinkfinger/$USERNAME.bir

in ubuntu /etc/pam_thinkfinger/$USERNAME.bir don't exists. I do these steeps for file: /home/michal/.thinkfinger.bir 
4. (Give "execute only" ..) I just skip

now all works. Screensaver fingerprint too :)

--
sory for my english :P

---

