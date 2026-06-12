---
title: "OpenOffice viewer for Windows XP?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by TRANQU111TY on 2008-08-18
If I save an OpenOffice Word Processor document with tables in an MS Office format my tables come out all skew-whiff in the Windows so I am wondering whether there is a proggie for Windows XP to perfectly view OpenOffice files so I can print them. It sucks having the printer on the XP machine.

---

### Post by tarps87 on 2008-08-18
You could use open office on the windows machine.
[http://download.openoffice.org/index.html](http://download.openoffice.org/index.html)
This problem seems to be common with pictures and arrows too. I'm amusing your xp and Linux os are on separate pc's? Are you on a network?

---

### Post by TRANQU111TY on 2008-08-18
> **tarps87 said:**
> Are you on a network?

My computer isn't on a network but both computers share the same wireless router wirelessly. I don't see how it could be possible to network each computer using wireless and print from my Ubuntu machine to the XP machine.

---

### Post by nicedude on 2008-08-18
How about buy a $5 1GB USB stick and you can just copy any documents to the USB and plug it in your XP PC and print. Also if you didn't catch what the other nice person said, Open Office has a windows installer and works in XP & Vista so just visit their website and download the Windows installer and use Open Office in your Windows XP.

As far as the networking, if you have a wifi router and they both connect to it then yes I believe you could use one of many ways to do this. Such as setting up a samba server and sharing your files. Someone else will have to sound off on how to setup samba as I don't use it.

Goodluck

---

### Post by sstusick on 2008-08-18
You could also send these files via email from the Ubuntu machine to the XP machine.

---

### Post by TRANQU111TY on 2008-08-18
No worries about the USB drives I have a couple of 8 gigs but this Samba sounds like the way to go.

---

### Post by Sef on 2008-08-18
> ...but this Samba sounds like the way to go.

[Samba Tutorial]("http://help.ubuntu.com/community/SettingUpSamba")

---

### Post by TRANQU111TY on 2008-08-18
With both computers having one Wireless Network Card and both connected to the router using Wireless, I can still network using Samba without disconnecting from the internet?

And how much easier would it be if both machines were running Ubuntu Hardy?

---

### Post by tarps87 on 2008-08-18
Samba can be used to file and printer share, the reason I asked about a network is if the two pc's can see each other then you should be able to print.
If you want to try, first open the command window in xp (click run on the start menu then type cmd)
now type ipconfig and make a note of your ip address then on the Ubuntu pc's open the terminal window and type
```

ping <ip address of xp pc>

```
if you get a response they can see each other.
To share you printer on xp go to printers, right click on your print and click share, you can add a password if you want but when you first set it up it is easier to leave it off.
On Ubuntu got to printers and then add and there should be an option for windows printer sharing and hopefully this will auto detect your printer, if not try browsing for it.
If you have any problems or don't understand any part, let me know and I will try to help

---

### Post by tarps87 on 2008-08-18
> **TRANQU111TY said:**
> With both computers having one Wireless Network Card and both connected to the router using Wireless, I can still network using Samba without disconnecting from the internet?


Yes you can, samba works with different ports to the ones a internet connection uses (HTTP, FTP,..)

---

### Post by nicedude on 2008-08-18
Once you are connected to a wireless AP ( router ) it is just like you had a Ethernet cable plugged into the router. So yes you should be able to do anything that you could if they were both hardwired to the router :-)

Goodluck in this little project.

---

