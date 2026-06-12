---
title: "Installing Cisco Packet Tracer 6.0.1 in Ubuntu 12.04 LTS"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by Weslee_Hollingswor on 2014-03-08
I'm a green-as-grass networking student trying to get Cisco's Netacad site running properly. One of the programs I need installed, both for lab work and for tests on the site, is Cisco Packet Tracer 6.0.1. There's a Linux download for this program available on Netacad. I've tried installing it a few times, but I guess I just don't understand how to do it right. I would link directly to the file in question, but as of this moment, netacad is temporarily down. ](*,)Anyway, I've tried making the downloaded file executable and opening it in a terminal with "sudo," but this only results in some error output akin to "unexpected end of file", probably because I don't know what I'm doing:

[IMG]http://i.imgur.com/nIC2eeh.png[/IMG]

I'm very, very new. If there's anyone that could walk me through this, that would be awesome. This is my output from the "uname -a" command:
 > 
Linux ubuntu 3.8.0-37-generic #53~precise1-Ubuntu SMP Wed Feb 19 21:37:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



I can provide other info as needed. I would have posed this issue in a Pidgin IRC chat, but I couldn't get that working either. :(

---

### Post by Vladlenin5000 on 2014-03-09
Hi, welcome.

The file name - if it really is a file - looks strange with all that spaces... I would suggest downloading it again just in case and then follow this instructions - first answer _and_ adapt it according to your file name/version -: [http://askubuntu.com/questions/335785/how-do-i-run-cisco-packet-tracer-6-0-1](http://askubuntu.com/questions/335785/how-do-i-run-cisco-packet-tracer-6-0-1)

---

### Post by Vladlenin5000 on 2014-03-09
Sorry, forgot to mention there's also a correct answer at the bottom of the previous link plus an important alert regarding 64-bit versions (the one you're running):

* If you are using 64 bit System Archutecture then to use it , you have to install ia32-libs by-*
```
   sudo apt-get install ia32-libs-gtk
```

---

