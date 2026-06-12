---
title: "LAMP on X, not terminal"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by mikevarela on 2008-09-02
Hi, I decided after reading about Ubuntu, to use my 3 yr old dell desktop as a server in my house. My aim is to serve my own web pages, as well as build pages for others. I'm also learning PHP.

I use a mac, and as such am slightly familiar with stacks (mamp). I've read up a little on LAMP, and have successfully installed the stack on my ubuntu system (gnome) via taskel in the terminal. My problem is though, I've never been a terminal guy. I'm headed there, but it's taking some time.

On my mac, i have a series of folders that i can drag docs too. like the htdocs folder for serving from port 8080.

I'd like to do this on my ubuntu system, but i can't find where anything visual gets installed. I see things in the terminal but would like to drag my php and html docs to the htdocs folder and thus the web

any help???

---

### Post by gmoney on 2008-09-03
Which type of Ubuntu did you install?  The first time I installed an Ubuntu LAMP server, I downloaded the server edition .iso, and was disappointed in the fact that I didn't have a GUI.  If this is the situation you're in, then you can download the complete Ubuntu (gnome) gui by executing:

```
sudo apt-get install ubuntu-desktop 
```

Perhaps you downloaded the desktop edition of Ubuntu, and then added the LAMP stack (via taskel on the command line, as you mentioned).  If you're just trying to drag html or php files to the proper folder (so they can be viewed as web pages in a browser, then you can just type:

```
gksu nautilus
```  

This will bring up a root version of nautilus (which is similar to Finder in OS X). The apache web root should be /var/www
Obviously, exercise extreme caution when using nautilus as the root user.  It is necessary to be root in order to copy files to the apache web root folder, though.

Hopefully that answered your question.  To throw in some more tips, I recommend PHPMyAdmin for administering mysql databases (without using the command line).  Also, Bluefish is an excellent download for creating web pages.

I'm not familiar with the taskel method of installing a LAMP stack.  It's definitely a good rule of thumb to use a package manager (Synaptic on the gui or apt-get on the command line) to install software on Linux though, because it makes it a heck of a lot easier to keep your system up to date.  When running a server, it's always good to have all of the latest security patches installed, ya know?  And plus, using synaptic to install a LAMP server on a desktop installation is super easy:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop)

---

### Post by Tatty on 2008-09-03
If you want to use a GUI on a server, you may wish to use the xubuntu-desktop insteado of the ubuntu-desktop package, as xubuntu uses xcfe which takes up much less resources than gnome.

```
sudo apt-get install xubuntu-desktop
```

---

### Post by mikevarela on 2008-09-03
thanks guys for the help.

I've got gnome installed. and all the lamp components as well.

I found the var/www folder and i've created a simple html doc to place there to try it out (drag from desktop to folder).

when i try and erase the existing doc, or place anything else in there i get a permission denied. I'm the root user, how can i let my system know that it's ok for me to update and delete in this directory... is it possible without going through terminal???

---

### Post by Paqman on 2008-09-03
> **mikevarela said:**
> 
when i try and erase the existing doc, or place anything else in there i get a permission denied. I'm the root user, how can i let my system know that it's ok for me to update and delete in this directory... is it possible without going through terminal???

Use gmoney's suggestion of running Nautilus as root.

By default your user has access to admin (root) priviledges, but they aren't active all the time. You temporarily take them on by using sudo (in the terminal) or launching graphical apps with gksu.

---

### Post by gmoney on 2008-09-03
Here's an explanation of the difference between sudo and gksudo:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by mikevarela on 2008-09-03
thanks again guys. should have done the gsuk earlier.

I'm obviously new at all this, but very eager to learn. can any of you guys point me in the right direction for materials on learning the command line and serving pages to the web?

oh, and I followed the link that explained graphical over normal sudo, but it didn't really explain how to implement the whole thing

---

### Post by gmoney on 2008-09-03
> **mikevarela said:**
> thanks again guys. should have done the gsuk earlier.

I'm obviously new at all this, but very eager to learn. can any of you guys point me in the right direction for materials on learning the command line and serving pages to the web?

oh, and I followed the link that explained graphical over normal sudo, but it didn't really explain how to implement the whole thing

If you're eager to learn, then that's all you really need.  Linux was designed from the beginning to be used by people who already knew how to use unix.  This can sometimes be frustrating for a new user, but the rewards are huge for learning how to use Linux--if you're willing to take the time and effort to do so.  You won't regret it.

Here's a page that describes sudo (which is almost identical to gksu) in more detail:  

[https://help.ubuntu.com/community/RootSudo/](https://help.ubuntu.com/community/RootSudo/)

Here's a page that helped me to understand a lot about the command line, and the structure of Unix (much of this can be applied to use on an Apple computer, which is also unix):

[http://freeengineer.org/learnUNIXin10minutes.html](http://freeengineer.org/learnUNIXin10minutes.html)

Here's a great post on users that are new to Ubuntu:

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

In general, searching Google and these forums are the best ways to find answers to any questions you may have.  If you run into a problem, chances are that someone else has already had that same problem, and there's almost always a solution.  99.9% of the users on this forum are very helpful.  Like anything else, though, there's always the exception.  Therefore, I recommend that you read this, just to know a little bit about malicious commands on the terminal:

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

And here's a guide on installing and setting up LAMP:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

