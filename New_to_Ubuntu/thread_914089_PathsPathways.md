---
title: "Paths/Pathways ??"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by faron45 on 2008-09-08
Help ! I have absolutely no idea what I'm doing.But,I wish to learn ! I am attempting to install RealPlayer via the terminal but,as I said,I have absolutely no idea what I'm doing.Particularly,when it comes to using,"the terminal" or,"command lines".Remember please,I learned on "windows".So,basically,everything that I know boils down to "point & click".When I had a "windows" system running on my pc I had looked at the command line terminal & quite frankly...it scared me.Heh,heh.
  I am at this particular point in the terminal right now...

 Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/opt/real/RealPlayer]: 

I would like the player to be installed on the desktop.At least for now.But,I'm lost.How can I do this ? How do I know/find out what the correct pathway is ?
          Thanks very much
                        Yer pal,J.Garcia 
                               :guitar:
                                Aka:faron45

 Also...why,sometimes,when I try to post a new thread,is the site taking me to this awkward page...vBulletin Message

    Your submission could not be processed because you have logged in since the previous page was loaded.

    Please push the back button and reload the previous window.

 
 After doing what the above tells me,& trying to submit my post again it just continues taking me back to that vBulletin message.

---

### Post by tangibleorange on 2008-09-08
There is a quick guide to the terminal here:

[http://psychocats.net/ubuntu/terminal]("http://psychocats.net/ubuntu/terminal")

as for installing realplayer, do you really want to install to the desktop (this will create loads of folders on your desktop) or just to get a shortcut on the desktop?

---

### Post by bobnutfield on 2008-09-08
You can install it to the folder suggested, or to the location where many user-wide apps are kept in /usr/bin.  The you can right click on the desktop and choose "Create Launcher" and type in the path the /usr/bin/RealPlayer or whereever you installed it to.

---

### Post by Flimm on 2008-09-08
I found the answer in ubuntuguide.org:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin)
Unfortunately, it involves using the terminal! Sorry, pal! The instructions are specific, so hopefully, you shouldn't go wrong.
In general, if you can't find an application in the Add/Remove app, try looking for a .deb file. Those are by far the easiest to install on Ubuntu, and you can find lots on [getdeb.net](http://getdeb.net). Unfortunately, RealPlayer is closed source, and they have chosen not to package it for Ubuntu, (although they do have a RedHat package), and there's nothing we can do about it. No freedom makes things harder to use.

---

### Post by faron45 on 2008-09-08
tangibleorange...Yes,I want to create a shortcut.Thank you.

bobnutfield...No folder is being suggested.

Everybody else.....thank you all very much.Sorry for the lenght of time it took me to reply....comp froze up.....

I now have 2 realplayer icons on my desk.........one is just called realplayer11GOLD.bin........the other is called hxsetup

---

### Post by elmoosecapitan on 2008-09-08
These are now your best friends:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://linuxcommand.org/](http://linuxcommand.org/)

Good luck.

---

### Post by faron45 on 2008-09-08
elmoosecapitan.....Tank oooooooo very very much

---

### Post by tangibleorange on 2008-09-08
A folder is being suggested! the [opt/blahblah/] is the directory being suggested. Anything in [] is a default - simply press enter to accept it. In this case you can install to the default folder and then later create a launcher as suggested previously.

---

### Post by faron45 on 2008-09-08
tangibleorange-As I'm sure you've read above,I have a couple of new icons on my desktop.If I right click on either of them,I get an option to "create a launcher".At this point,I'm now wondering if'n I should just go ahead & try this.Whatcha think ?

---

### Post by tangibleorange on 2008-09-09
> **faron45 said:**
> tangibleorange-As I'm sure you've read above,I have a couple of new icons on my desktop.If I right click on either of them,I get an option to "create a launcher".At this point,I'm now wondering if'n I should just go ahead & try this.Whatcha think ?

Ok well if it's installed correctly, you should just be able to create a launcher to the executable. unfortunately, I don't know the default path, but if you installed it to the default path [opt/real/RealPlayer], could you post the output of:

```
ls /opt/real/RealPlayer/
```

---

