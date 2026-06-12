---
title: "Wireshark"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by KatyG on 2013-02-02
I have to use Wireshark for class.

Problem: Can't see network interfaces.

I know can see the interfaces if you run it as root but that is dangerous, so I have been trying to follow steps to do it differently. 

groupadd wireshark won't work. Reply:

groupadd: cannot lock /etc/group; try again later.

I did run gksudo wireshark for a sec before I realized it was a bad idea. Do I have to enter another command to make Wireshark stop running as root? I closed and then opened the program and I can't see any interfaces again, but I want to make sure.

So I shouldn't run it as root, but I can't seem to get some commands to work in my terminal.

What to do?




[http://www.rebojo.com/wireshark-on-debian-as-non-root-user/](http://www.rebojo.com/wireshark-on-debian-as-non-root-user/)
file:///usr/share/doc/wireshark-common/README.Debian

---

### Post by deadflowr on 2013-02-02
If you installed through the Ubuntu Software Center, the first review by Trenton Vanderwert gives you this:

> sudo dpkg-reconfigure wireshark-common
press the right arrow and enter for yes
sudo chmod +x /usr/bin/dumpcap
you should now be able to run it without root

---

### Post by KatyG on 2013-02-02
Thanks, :p  that did it.

---

### Post by deadflowr on 2013-02-02
Good. If you would, please mark this thread as solved using the thread tools.

Sidenote: I find looking over the reviews of programs I don't ordinarily run is a beneficial part of the software center.

It has saved me from inadvertently installing broken programs many a time. And the odd app like wireshark come with the handy tip or two.

---

### Post by paulClarke_1967 on 2013-12-14
This works.  However usb devices are not listed.  The only way I can get them to appear is to run wireshark as root.  Of course we know that is not recomended.  Does anyone know how to correct this problem?

---

### Post by deadflowr on 2013-12-14
> **paulClarke_1967 said:**
> This works.  However usb devices are not listed.  The only way I can get them to appear is to run wireshark as root.  Of course we know that is not recomended.  Does anyone know how to correct this problem?

Somewhat old thread.
What kind of usb device are you meaning?
A wireless usb device or something else?

I have a wireless usb thingy, which I rarely ever use, but it shows as wlan0 in wireshark.

You could read up on wireshark [here]("http://www.wireshark.org/docs/")

---

