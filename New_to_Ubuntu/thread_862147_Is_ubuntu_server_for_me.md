---
title: "Is ubuntu server for me?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by devonps on 2008-07-17
Hi,

I've just downloaded the Ubuntu server 8.04v and my question is: Will Ubuntu server allow MS windows based clients to connect to the server and:

a) retrieve documents, spreadsheets, presentations, etc so that they can continue to work on them using MS Office

b) Stream videos, using either Real Player or Media player?

c) View pictures.

BTW: The windows clients will all belong on the same (home) netowrk.

My second question is about the above data.

I would like each user to have their own set(private) of documents, videos, etc - but also have access to a single share (public) of documents, videos, etc. I assume this is possible?

Thanks in advance.

---

### Post by Bachstelze on 2008-07-17
Yes, it would allow all of that. Samba will be your best friend ;)

---

### Post by Troll_the_Great on 2008-07-17
Just keep in mind that Ubuntu Server comes without a GUI.So, if you want a GUI you have to install it separately.
For Gnome
```
sudo aptitude install ubuntu-desktop
```
For KDE
```
sudo aptitude install kubuntu-desktop
```
For X-Face
```
sudo aptitude install xubuntu-desktop
```
Cheers!

---

### Post by hyper_ch on 2008-07-17
but then no gui is required to setup the server.

---

### Post by devonps on 2008-07-17
Thanks for the replies. One more question: Will Samba setup the different folders and access rights I mentioned above, i.e. private and public access?

---

### Post by devonps on 2008-07-17
Just thought of another question...Should I use a GUI to configure my server/users/folders then "switch it off" once I'm happy that everyting is working as I expect?

---

### Post by hyper_ch on 2008-07-17
editing text files isn't that different between gui and cli ;)

---

### Post by t0p on 2008-07-17
> **devonps said:**
> Just thought of another question...Should I use a GUI to configure my server/users/folders then "switch it off" once I'm happy that everyting is working as I expect?

That's a decision only you can make.  It depends on how you prefer to edit text files.

---

### Post by JillSwift on 2008-07-17
> **hyper_ch said:**
> editing text files isn't that different between gui and cli ;)Very true. So true that if you're ***at all*** comfortable with the command line, just forget the GUI - for most things server it just gets in the way and eats up resources.

---

### Post by devonps on 2008-07-17
> **JillSwift said:**
> Very true. So true that if you're ***at all*** comfortable with the command line, just forget the GUI - for most things server it just gets in the way and eats up resources.

I am comfortable with a CLI - so I'll go that way.

---

### Post by scorp123 on 2008-07-17
I suggest you read this thread ... it's long but worth it:

"Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller"
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Don't worry about it mentioning "Ubuntu 7.10" ... the instructions are the same for Ubuntu 8.04. "Armed" with these instructions you'd get a free equivalent to a Windows 2003 Server ("Domain Controller").

---

### Post by devonps on 2008-07-18
> **scorp123 said:**
> I suggest you read this thread ... it's long but worth it:

"Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller"
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Don't worry about it mentioning "Ubuntu 7.10" ... the instructions are the same for Ubuntu 8.04. "Armed" with these instructions you'd get a free equivalent to a Windows 2003 Server ("Domain Controller").

Thanks for the link - it was a good read, if a little lengthy! lol.

I mentioned in my 1st post that I'd downloaded a copy of Ubuntu server 8.04 and have burned it to a CD. After reading the above link it seems that the CD I have performs some of these tasks, i.e. it will install SSH and Samba (along with other items) for me.

So I think I'll follow the CD that I have and see where that takes me.

Once I've created my partitions and installed my media - should I use my 2nd hard drive for backup?

I've decided against RAID as the server I'm buildiing isn't a high availability server + I own over 95% of the media I intend to install.

---

### Post by bodhi.zazen on 2008-07-18
If you want a gui, install Ubuntu and add the server kernel and server packages you need.

If you want a server, with no gui, go with the server install.

IMO a server with no gui is the way to go, but it is a bit of a steep learning curve if you are unfamiliar with the command line.

[http://linuxcommand.org/](http://linuxcommand.org/)

On the other hand, you can run headless and ssh in from Windows with putty.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

Learn to secure your servers.

[uwiki]AdvancedOpenSSH[/uwiki]

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

