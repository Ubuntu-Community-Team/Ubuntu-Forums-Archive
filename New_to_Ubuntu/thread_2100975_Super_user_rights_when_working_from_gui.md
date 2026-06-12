---
title: "Super user rights when working from gui?"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by sim085 on 2013-01-03
Hello,

How can I get super user rights from the user interface? For example if I double click on a document not in my /home directory I find that after I edit it I cannot save it because I do not have enough privileges! 

Every time I have to open Terminal and edit the document using sudo gedit. 

Is there a way how I can get super user right also when working from the gui?

---

### Post by Pjotr123 on 2013-01-03
Security has a price. In this case a slight decrease in user ease. I advise to value your security and learn to play by the secure rules. :)

---

### Post by mlentink on 2013-01-03
> **sim085 said:**
> 
Every time I have to open Terminal and edit the document using sudo gedit.

And there's a good reason for that. "Documents" outside of your home-folder are usually system files. If you were to allow all files to be opened and edited from your account, that would imply that anybody using your credentials, or even belonging to your group could as well. Not safe.

You could obviously edit the quicklist entry for Nautilus to start it with gksudo, which would require you to start the file browser with your password. But please be aware that that would also save those edited files as owned by root, so would have to change the ownership of the files anyhow.

Perhaps read up on Linux file-permissions?

---

### Post by ibjsb4 on 2013-01-03
> **sim085 said:**
> Is there a way how I can get super user right also when working from the gui?

```
gksudo nautilus
```

---

### Post by haqking on 2013-01-03
> **sim085 said:**
> Hello,

How can I get super user rights from the user interface? For example if I double click on a document not in my /home directory I find that after I edit it I cannot save it because I do not have enough privileges! 

Every time I have to open Terminal and edit the document using **sudo gedit**. 

Is there a way how I can get super user right also when working from the gui?

use **gksudo **and not **sudo** for graphical apps (or **kdesdudo** for KDE etc)

Though it does not happen often, you run the risk of giving root ownership to files in your /home

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

As mentioned above you can run your file manager with root permission when needed, but with great power comes great responsibility ;-)

---

### Post by audiomick on 2013-01-03
> **sim085 said:**
> Every time I have to open Terminal and edit the document using sudo gedit. 

Firstly, this is wrong in itself. When using graphical applications, you should use gksudo, not sudo. Here is why
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Secondly, you are asking for advice on how to operate as root. Since that contradicts the security concept of Ubuntu, it is discouraged here on the forum to explain how. I don't know how, either, mostly because I have never felt the need to circumvent the sudo mechanism on Ubuntu.

For the amount of work where you have to do what you say, i.e. edit files that belong to root, surely it is not too much trouble to use gksudo to either start gedit or start nautilus to have root privileges for whatever it is you want to do in that moment. Pesonally, I really appreciate the reminder that I am doing something that could possible really break my system.

---

### Post by sim085 on 2013-01-03
Thanks to all for the replies. I understand the reason why the need for the security. However I simply wondered if there was a way - when I know what I am doing - how to edit file in an other location that is not /home without having to always have to go to terminal. 

To run the gksudo command I still need Terminal right?

I'll give another example where I had problems (which for now I only know how to solve from Terminal).

I downloading a zip file in /home/sja745/Downloads. I doubled clicked on it and opened it. I wanted to extract the content to /usr/local/my_folder. I get an error message that I do not have enough privileges to do that.

---

### Post by audiomick on 2013-01-03
> **sim085 said:**
> 
To run the gksudo command I still need Terminal right?

Yes, but then whichever graphical application you invoke opens, and you work in there with root priviliges.

> 

I'll give another example where I had problems (which for now I only know how to solve from Terminal).

I downloading a zip file in /home/sja745/Downloads. I doubled clicked on it and opened it. I wanted to extract the content to /usr/local/my_folder. I get an error message that I do not have enough privileges to do that.

I would probably invoke the file manager with 

```
gksudo nautilus
```

to do this. From there, you can move the file to /usr/whatever or any other root owned file, and then extract it there.

Note that when you start Nautilus that way, it seems to always through up errors. That is apparently not a problem. I did see an explanation for that somewhere, but I can't remember exactly what it was.

From the "root" nautilus, you could also right click on a file and choose "open with gedit" to edit with root priviliges.

Just remember: be careful with a root instance of nautiulus, and shut it as soon as you have finished whatever it is you were doing. Apart from being able to break you system, if you start messing around with your own files from there, you might find that they suddenly belong to root...

---

### Post by haqking on 2013-01-03
You dont need to use terminal.

You can also alt +f2

---

### Post by audiomick on 2013-01-03
> **haqking said:**
> You dont need to use terminal.

You can also alt +f2

Ah, new trick. Thanks... ;)

---

### Post by RottNKorpse on 2013-01-03
You can type the command in terminal or alt+f2.

There is another difference with running apps as gksudo vs sudo. I don't have to explain the dangers of this because many others have but if you run "gksudo" (or gksu) in a terminal you can close the terminal afterwards where as using "sudo" will close whatever you launch when you close the terminal.

You can also add a desktop shortcut by right clicking the desktop choosing "Create Launcher" and then follow this screenshot. Then if you want you can drag it to the Unity Launcher...and the fun just keeps on going. :) (for example: you can also add it to the Dash but that requires installing another app to do it)

[IMG]http://i.imgur.com/CeVOq.png[/IMG]
[http://i.imgur.com/CeVOq.png](http://i.imgur.com/CeVOq.png)

---

