---
title: "Server"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Artan1s on 2008-04-29
Alright I've done some searching but I haven't particularly found what I'm looking for a guide or something that can show me how to accomplish what I'm looking to do. I want to make a file-server for my dorm-mates and I.  At first I want it to just be a simple file server to store files for all of us and then i will expand on it at a later date to add functionality. The computers we will be using will be windows based and the server will be ubuntu.  Any resources would be greatly appreciated.

Thanks,
Ryan

---

### Post by Monicker on 2008-04-29
Samba?

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

FTP?

[http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588")


What kinds of functionality do you think you might need to add?

---

### Post by iSplicer on 2008-04-29
Just get the Ubuntu server installation and install LAMP. store teh files in the the document root (usually /var/www), and then people can access it through the apache HTTP web server.

---

### Post by Artan1s on 2008-04-29
> What kinds of functionality do you think you might need to add?

Perhaps log-ins for my fellow suite-mates. Thats really the only thing I've considered so far but I'm sure there is more I'm going to want to add.

> Just get the Ubuntu server installation and install LAMP. store teh files in the the document root (usually /var/www), and then people can access it through the apache HTTP web server.

How would my roommates upload their files.

Thanks so far both of you, great info so far.

---

### Post by Ek0nomik on 2008-04-29
It may not be what you're looking for, but I run a DC++ hub at my University for my friends to share files over the network.

[http://dcplusplus.sourceforge.net/](http://dcplusplus.sourceforge.net/)

Linux DC Server: [http://www.verlihub-project.org/doku.php](http://www.verlihub-project.org/doku.php)

---

### Post by Ek0nomik on 2008-04-29
> **Artan1s said:**
> Perhaps log-ins for my fellow suite-mates. Thats really the only thing I've considered so far but I'm sure there is more I'm going to want to add.



How would my roommates upload their files.

Thanks so far both of you, great info so far.

You could setup different user accounts and let them log in via SSH.  You could also use an FTP Server and give them usernames/passwords.

---

### Post by Artan1s on 2008-04-29
> It may not be what you're looking for, but I run a DC++ hub at my University for my friends to share files over the network.

[http://dcplusplus.sourceforge.net/](http://dcplusplus.sourceforge.net/)

Linux DC Server: [http://www.verlihub-project.org/doku.php](http://www.verlihub-project.org/doku.php)

hmm that looks like a pretty good piece of software actually from what I read about it, but the only problem is that I dont have a windows license for the comptuer I want to make a server so no dice there.  Thanks for the link though, im definitely going to bookmark it.

---

### Post by Artan1s on 2008-04-29
> You could setup different user accounts and let them log in via SSH. You could also use an FTP Server and give them usernames/passwords.

Thats a great idea.

---

### Post by Ek0nomik on 2008-04-29
> **Artan1s said:**
> ...but the only problem is that I dont have a windows license for the comptuer I want to make a server so no dice there.

What's the problem?  I don't understand.

---

### Post by Artan1s on 2008-04-29
> What's the problem? I don't understand.

"DC++ is an open source client for Windows for the Direct Connect network."

---

### Post by Ek0nomik on 2008-04-29
> **Artan1s said:**
> "DC++ is an open source client for Windows for the Direct Connect network."

I gave you a second link.  Verlihub is the piece of software which lets you install the DC++ hub onto a Linux box.  (You can also install YnHub as a Windows DC++ Server)

Then, you can have friends connect to the hub (running on either Windows or Linux) via DC++ (Windows) or LinuxDC++ (Linux)

Linux Client DC++ Website:  [http://linuxdcpp.berlios.de/articles.php?um=index](http://linuxdcpp.berlios.de/articles.php?um=index)

Verlihub or YnHub = DC **Servers** (Hubs)
LinuxDC++ or DC++ = DC **Clients**

---

### Post by Artan1s on 2008-04-29
Ahhh, I overlooked the second link, my apologies.

---

### Post by Ek0nomik on 2008-04-29
> **Artan1s said:**
> Ahhh, I overlooked the second link, my apologies.

Anywho, I'm not trying to convince you into using DC, because it may not be what you want.

That being said, running a hub is fairly simple, and is much easier to do now that Verlihub is in the Ubuntu repository (all you need to do is run 'apt-get install verlihub').  There is also a front end to the server hub called VHCP.

[http://vhcp.verlihub-project.org/](http://vhcp.verlihub-project.org/)

What this does is it provides you with a graphical interface to change all the hub settings (share limits, bot names, etc) via the web.  So you can change any of the hub settings online anywhere in the world.

If you have questions feel free to ask about DC or any of the other options mentioned.  :)

---

### Post by denyasis on 2008-04-29
Actually, I have a question along similar lines:

I'm looking at building a small home file/media server. While I've heard of good features from WHS, I don't want some of the bugs and the large price tag is not so cool either. I want more functionality than an NAS box, too. I'd eventually like to use the server to manage "family information", like synching up calendars with computer/devices on the network, contacts, leaving meassages for eachother, etc. Hence I'm looking at using Ubuntu.

I would just like to know if I can easily set up Ubuntu (desktop or server) to do some (actually more like all) of the following:

- Automatic backups of my computers on the network (about 3-5 total)
- Allow my XP Desktops to access files on the server (not via http, but more like a network drive[s])
- Stream music/video from the server to my squeezebox, etc
- I'm assuming Ubuntu will auto-update, but I'll throw it in here anyway.
- Have some form of Permission and encryption systems. I'd like my taxes, and finances, etc to stay secure and use the permissions to keep, say the kids, from accidently deleting my taxes, subpoeanas, music, etc.

So, I guess, my question is Ubuntu what I'm looking for?

---

### Post by lazyart on 2008-04-29
Well, you kinda hijacked a thread here.  I'm just gonna drop this link on you, [http://www.amahi.org/](http://www.amahi.org/) and then quietly walk away.  Next time start up a new thread so that answers don't get muddled up.  Makes it easier when someone is looking for solutions 6 months from now. :)

> **denyasis said:**
> Actually, I have a question along similar lines:

I'm looking at building a small home file/media server. While I've heard of good features from WHS, I don't want some of the bugs and the large price tag is not so cool either. I want more functionality than an NAS box, too. I'd eventually like to use the server to manage "family information", like synching up calendars with computer/devices on the network, contacts, leaving meassages for eachother, etc. Hence I'm looking at using Ubuntu.

I would just like to know if I can easily set up Ubuntu (desktop or server) to do some (actually more like all) of the following:

- Automatic backups of my computers on the network (about 3-5 total)
- Allow my XP Desktops to access files on the server (not via http, but more like a network drive[s])
- Stream music/video from the server to my squeezebox, etc
- I'm assuming Ubuntu will auto-update, but I'll throw it in here anyway.
- Have some form of Permission and encryption systems. I'd like my taxes, and finances, etc to stay secure and use the permissions to keep, say the kids, from accidently deleting my taxes, subpoeanas, music, etc.

So, I guess, my question is Ubuntu what I'm looking for?

---

### Post by iSplicer on 2008-04-29
> **Artan1s said:**
> How would my roommates upload their files.

Thanks so far both of you, great info so far.

When you have an apache HTTP server running (comes default with LAMP), all you have to do is install SSH:

sudo apt-get install ssh

then your room mates can happily connect to your server and upload their files through ssh with a program like FileZilla

---

### Post by iSplicer on 2008-04-29
> **denyasis said:**
> Actually, I have a question along similar lines:

I'm looking at building a small home file/media server. While I've heard of good features from WHS, I don't want some of the bugs and the large price tag is not so cool either. I want more functionality than an NAS box, too. I'd eventually like to use the server to manage "family information", like synching up calendars with computer/devices on the network, contacts, leaving meassages for eachother, etc. Hence I'm looking at using Ubuntu.

I would just like to know if I can easily set up Ubuntu (desktop or server) to do some (actually more like all) of the following:

- Automatic backups of my computers on the network (about 3-5 total)
- Allow my XP Desktops to access files on the server (not via http, but more like a network drive[s])
- Stream music/video from the server to my squeezebox, etc
- I'm assuming Ubuntu will auto-update, but I'll throw it in here anyway.
- Have some form of Permission and encryption systems. I'd like my taxes, and finances, etc to stay secure and use the permissions to keep, say the kids, from accidently deleting my taxes, subpoeanas, music, etc.

So, I guess, my question is Ubuntu what I'm looking for?

Please start a new thread, more people will be able to help you!

---

