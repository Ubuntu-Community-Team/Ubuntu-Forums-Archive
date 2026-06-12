---
title: "home networking"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by ratdude747 on 2008-07-30
here's my problem- I have a network at my house and one of the computers runs on hardy. the rest run on on windows 2000. I would like to trade files, but I have no domain on my network in my win 2000 settings (I use a workgroup based network and I already configered samba to use that name). I need t know what to type in the domain and host bars in the ubuntu settings to make it be a member of my network.

---

### Post by bodhi.zazen on 2008-07-30
I do not think you need to make you Ubuntu box a member of the workgroup.

---

### Post by RbikeRider on 2008-07-30
If you are using Samba, then your Linux machine is going to be your file server.  On your Windows machine, you can then browse to or create a mapped network drive to your Samba share on your Linux machine.  It has been a while since I have worked with Samba, but you will need to make sure your permissions are set up correctly in Samba and possibly in the Linux directories you are accessing.  I hope this helps.  Let me know if I might be able to help more.

---

### Post by hrod beraht on 2008-07-30
Are you actually sharing a folder on the Ubuntu machine? My Ubuntu box wasn't visible to the Windows boxes until I actually shared something on it.

Domain name box is empty.

Bob

---

### Post by Efros on 2008-07-30
Nautilus is having issues browsing shares on a windows network in Ubuntu 8.04. the easiest way is to type in the address bar smb://ipaddress/sharename e.g. on my network I would type smb://192.168.1.200/250G1 , this will connect me to the share name 250G1 on 192.168.1.200 allowing me to browse that directory. This is a bit of a problem if you dont have static IPs on your network but seems to be the best way round it at the moment.

---

### Post by ratdude747 on 2008-08-04
the tip about having a shared folder was the key. apparently you must set a folder to beshared to enable networking. thanks "hrod beraht"!

---

### Post by loboc on 2008-08-04
on the windows boxes if you install bonjour for windows from apple.com (google it) and have the avahi packages installed in hardy which are there by default i think you can use hostname.local to resolve in both directions

---

### Post by Duwady on 2008-08-05
I am having the same problem.  Not only the shares, I can not see the printers either.  If I need to install the printers, I have to make sure I know the shared name.

The Windows share can be accessed, but not seen... Is it Nautilus issue, Ubuntu 8.04 issue, or Windows issue. Or is it only on my particular installation?  

Interestingly, someone who just installed Ubuntu 8.04 on laptop could see the share, at least the printers.

Any body who can shed some light on this? Or can point to where the light can be seen?

---

### Post by ratdude747 on 2008-08-05
dude, dont worry...  

first, make sure you have an internet connection
then, make a new folder on your desktop. go to its properties and select the sharing tab. make it shared. when it asks to add some software, select "yes". give it a few minutes, and after awhile, you should be fine. If you need to change your workgroup, download samba at: [http://packages.ubuntu.com/hardy-updates/samba](http://packages.ubuntu.com/hardy-updates/samba) 

or

[http://packages.ubuntu.com/hardy/samba](http://packages.ubuntu.com/hardy/samba)

then (after installing), go to system-administation-samba.  when in the utility, select prefrences-server settings. that should allow you to change the workgroup.

Hope that helps

Larry The computer surgeon

---

