---
title: "[SOLVED] Run Xrdp on Ubuntu Hardy"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by infraction on 2008-09-28
I guess I'll start here, as it's been made abundantly clear in these forums that I'm not capable of asking a question anywhere else.

Does anyone have CLEAR information on how to get 'xrdp' running on Ubuntu 8.04 hardy, without being condescending???

Specifically....
- what underlying software does it require?   xvnc?, x11rdp?, vnc4server?, openssl?, what?????  No firm answer has been found in these forums.
- exactly how is this software obtained???  Must I build from source??  Can I take the package from Synaptic???
-  where is there help with errors once this is (yeah, right) running???  Or even being installed, for that matter.

Yes, quite frankly I AM looking for a roadmap.  Any assistance will be truly appreciated, as so far all that is found is a hodgepodge of great results with this software, but no firm detail.

Many, many thanks in advance.  And my apologizes for seeming frustrated.

---

### Post by infraction on 2008-09-28
*************  B  U  M  P  *****************

Surely there's a thread master out there that has a suggestion of where this question should be posted!?!?!?!

---

### Post by infraction on 2008-09-30
Just forget it.  Apparently nobody has the time or inclination.

---

### Post by milasch on 2008-11-04
You look frustrated! Welcome to the club! I've been trying to make Xvnc work for 2 months now... Posted several times but no one answered. Xrdp remains in my dreams only.

---

### Post by johnnyrevell on 2009-03-16
on 8.04

sudo apt-get install tightvncserver xrdp

and you're done!

Beware in Gnome the keyboard for your rdp client will be messed up. The fix is to login on the host machine as the client and run
gconf-editor
go to apps>gnome_settings_daemon>plugins>keyboard and clear the "active" checkbox

Firefox appears to have problems printing to cups from the xrdp client, so I changed to Opera- no probs! OpenOffice works and prints OK from client too

---

### Post by BFris on 2009-03-27
I see there is quite a bit of frustration with Xrdp. I managed to get it installed without too much fuss in Kubuntu. Apparently it is more painful if you are using Gnome as your desktop instead of KDE.

So this link has a pretty darn good explanation of how to get things working (even in Gnome):
```
[http://ubuntuforums.org/showthread.php?t=392184&highlight=xrdp&page=2]("http://ubuntuforums.org/showthread.php?t=392184&highlight=xrdp&page=2")

```

But before you run to that, here is a brief rundown
[LIST]
[*]install vncserver, vnc4server, or tightvncserver
[*]run vncpasswd to set the default password for your user
[*]install xrdp from debian packages
[/LIST]

It turns out that if you want to connect from an XP client the xrdp package in the Hardy repositories doesn't work. So I picked one off of the Debian Sid website (I googled "xrdp debian package" and found the right Debian website).

I've been using it for a day now from XP client and it's really slick.

---

### Post by infraction on 2009-05-24
I have gotten down the long strange road that is XRDP, and it is working and I love it death!!

Please have a look at this post in the 'Community Cafe' section......

[http://ubuntuforums.org/showthread.php?t=1168264&highlight=xrdp](http://ubuntuforums.org/showthread.php?t=1168264&highlight=xrdp)


Regards,

infraction

---

