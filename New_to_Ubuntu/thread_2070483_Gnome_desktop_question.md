---
title: "Gnome desktop question"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Deucalion29710 on 2012-10-12
OK, so I am now on my 6th fresh format and install of Ubuntu 12.04 (in under a month).  I installed gnome shell, gnome desktop, and tweak tool.  For whatever reason I cannot select _shell user-theme" because there is an orange triangle next to it which when I hover over it I get "shell user-theme extension not enabled".  How do I fix this?  Is there a way to determine what version of gnome shell I am using so that I don't break this again with unmet dependencies?  Where is the best place to look or even begin to fix this?  Thanks in advance for any and all help.:guitar:

---

### Post by Frogs Hair on 2012-10-12
If running 12.04 you should have Gnome 3.4 . Add this PPA from the terminal to get basic extensions.  Navigate  to the  extensions tab in the Gnome Tweak Tool  to enable them.```
sudo add-apt-repository ppa:webupd8team/gnome3
``````
sudo apt-get update
```
```
sudo apt-get install gnome-shell-extensions
```

A shell theme will not be available if you log in to Unity . You can add other extensions from the link.  I used this PPA while running 12.04 

[http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html](http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html)

---

### Post by Deucalion29710 on 2012-10-13
Thank you for the reply.  This makes no sense for it is a fresh install.  The error I got is as follows:



sudo apt-get install gnome-shell-extensions
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell-extensions : Depends: gnome-shell (>= 3.5) but 3.4.1-0ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.


I am in Gnome3 desktop.  How do I fix this?

Also, I have the weather extension it's just that gnome shell user theme does not work.  I would be just tickled pink if somebody could help me to resolve this.  :)

---

### Post by cmcanulty on 2012-10-13
make sure you are logged into gnome shell or else the extensions will behave like that

---

### Post by Frogs Hair on 2012-10-13
I suggested the PPA because I was using it 13 days ago on 12.04. Open Software Sources > Other Softrware and remove the PPA source( ppa:webupd8team/gnome3) 

There should be 2 lines and then run the follwing ```
sudo apt-get update
```

The official extension site is at the link but I did not use it while running 12.04 and some extensions have been updated for 3.6.
[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by Deucalion29710 on 2012-10-13
I was in Gnome desktop and everything worked but the shell themes.  I attempted to purge my repositories and now my problem is even bigger.  Now Gnome 3 will not work at all.  Gnome Classic works (which I detest) but when I try to go to Gnome desktop all I get is my pointer pretty much.  Nothing else loads but my wallpaper.  Any suggestions?

---

### Post by cmcanulty on 2012-10-13
just reinstall the gnome shell it won't affect your files

---

### Post by Linux_junkie on 2012-10-13
It is Gnome-tweak-tool you need to install to be able to change themes.
```
sudo apt-get install gnome-tweak-tool
```

Remove the PPA for Gnome3 from within your repositories.  You don't need that.

Keep the default repositories.

Do 

```
sudo apt-get update
```

---

### Post by Deucalion29710 on 2012-10-13
I have uninstalled Gnome shell, shell pref, and tweak tool and then reinstalled them to no avail.  I might just have to start fresh again, but I guarantee it will take me back to the original problem which was that shell theme problem.  AskUbuntu wasn't able to answer the question.  They simply mark as "solved" when they are stumped.  Nobody knows in the Facebook groups either.  I have seen numerous screenshots of the same issue, so I am to assume that it is a common problem.

---

### Post by Frogs Hair on 2012-10-13
Shell Extensions : [https://extensions.gnome.org/](https://extensions.gnome.org/)

I think you already know this , but orange triangle will appearer in the Tweak Tool when logged into Unity as below It should not appear in the Gnome Shell.

---

### Post by Cheesemill on 2012-10-13
You first need to install the [User Themes]("https://extensions.gnome.org/extension/19/user-themes/") extension to get this functionality.

Just install the extension then restart Gnome Shell (*ALT+F2* then *r* then *Enter*).

---

### Post by Deucalion29710 on 2012-10-14
Yes I am aware, however I have only had Gnome3 fully functional once and it was short lived.  I have not re-loaded the os yet because it is murder on a tethered connection.  Thanks for the input on everything.  If I do in fact have the same problem upon a new installation, would it be a bad thing to start a new thread?  I know that over at the Ask Ubntu forum they get all bent about that and spend more time policing the forum than answering questions, which is why I am now here.

---

### Post by Frogs Hair on 2012-10-14
If you have the same problem with a new installation start a net thread . If you install again add the synaptic package manager and check for Gnome Shell Extensions there. I write this because on my 12.10 installation the basic extensions  such as user themes were available from the official repository.

---

### Post by Deucalion29710 on 2012-10-15
Thanks for all of the help.  I will know more tomorrow when I reload, but I think I got my answer a couple of posts above.  Thanks again.

---

