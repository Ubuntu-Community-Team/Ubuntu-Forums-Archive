---
title: "How to install via the command line?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by tabithaboof on 2008-05-21
I had an idea that I would create a text file of a command line to install my favorite software/remove software I dont like, to use each time I reinstall and I had a couple of questions. First one being what is the command to install say the gimp. I would guess?

$ sudo apt-get install gimp

second how would I install multiple bits of software? like this?

$ sudo apt-get install gimp amarok

2 Further questions if I may, how do I know what the name of the software I want to install is? for example is I want to install something like Gnome Nethack is it "gnome-nethack" or "GNOMENethack" or Firefox2, how do I know if its "mozillafirefox2" or "firefox2" etc?

lastly if for example I dont like pidgin, what do I need to do to remove it?

Thanks alot!

---

### Post by Monicker on 2008-05-21
1) yes

2) yes

3) apt-cache search nethack

4) sudo apt-get remove pidgin

---

### Post by iaculallad on 2008-05-21
> **tabithaboof said:**
> I had an idea that I would create a text file of a command line to install my favorite software/remove software I dont like, to use each time I reinstall and I had a couple of questions. First one being what is the command to install say the gimp. I would guess?

$ sudo apt-get install gimp

second how would I install multiple bits of software? like this?

$ sudo apt-get install gimp amarok

2 Further questions if I may, how do I know what the name of the software I want to install is? for example is I want to install something like Gnome Nethack is it "gnome-nethack" or "GNOMENethack" or Firefox2, how do I know if its "mozillafirefox2" or "firefox2" etc?

lastly if for example I dont like pidgin, what do I need to do to remove it?

Thanks alot!

To uninstall a software: issue the command on your terminal
[B]
sudo apt-get remove app_name[/B]

To install multiple software/apps:

**sudo apt-get install app1 app2 app3** (Note: with spaces b/w them)

To install a package:

sudo dpkg -i package.deb

For the application names, there could be database names for the application used in linux. Try searching the web.

---

### Post by Xiong Chiamiov on 2008-05-21
First, you (since you've part of the set of everyone) should read [this excellent guide]("http://monkeyblog.org/ubuntu/installing/") to installing in Ubuntu.

Secondly, it's actually much easier to remember the commmands if you use [aptitude instead of apt-get]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/").  For instance, to search for a package, you can do something like
```

aptitude search foo

```
which searches for all packages with foo in the name.  The search term can also include regexes; in that way, to find a list of all the java packages I have installed, I can take [this]("http://www.linuxquestions.org/questions/debian-26/aptitude-how-to-get-a-list-of-all-installed-packages-458119/?#post2310207") and modify it like so:
```

aptitude search ~i | grep java

```

---

