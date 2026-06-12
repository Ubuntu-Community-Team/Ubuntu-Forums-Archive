---
title: "Having trouble setting up File Sharing from Windows 10 to Ubuntu 14.04"
date: 2018-12-20
forum: New to Ubuntu
---

### Post by 1brokentopdesign on 2018-12-20
Hello, I'm thinking this is an easy question that is asked all the time, but I'm having difficulty setting up shared folders between Windows 10 and Ubuntu 14.04. 

I was following this thread:
[https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/)

and got to this point no problem:
sudo apt-get install cifs-utils
[COLOR=#000000][FONT=Monaco]then:
mkdir ~/Desktop/CNCShare

where CNCShare is my folder on the Linux Desktop

[/FONT][/COLOR]But when I go to this line:
sudo mount.cifs //techsupport1/CNCShare /home/plasma/Desktop/CNCShare -o user=techsupport1
I get this message:
mount error: could not resolve address for techsupport1: Unknown error

[B]Windows 10 name: techsupport1
Linux: plasma@plasma-desktop
Shared Folder Name: CNCShare[/B]

---

### Post by TheFu on 2018-12-20
Ubuntu 14.04 support ends in a few months and for some flavors of it, supported ended 2 yrs ago.

I'm guessing that the issue is Win10 changed the version of the CIFS protocol supported by default, so you old Ubuntu SMB implementation needs to be told to use the same version.

Usually after I post that, someone much smarter shows up with more help.

The error you are getting is pretty clear:
**mount error: could not resolve address for techsupport1: Unknown error**
If you can't **ping techsupport1**, then it won't work.  ServerName resolution is a basic need for any network.  If you won't/don't want to setup a solution for that, then use the IP address for the techsupport1 machine instead of the name.

---

