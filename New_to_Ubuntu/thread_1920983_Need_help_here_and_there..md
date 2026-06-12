---
title: "Need help here and there."
date: 2012-02-05
forum: New to Ubuntu
---

### Post by backhost on 2012-02-05
So today I finally got the chance from upgrading from xp to ubuntu and I love the user interface on this OS. I usually do web development work and web design and I am in need of help with finding good top of the line programs that can help me with my work environment.


I would appreciate if you guys could suggest me some programs like a php text editor , image editor, and any other useful programs that you think I would like and could use. Ill download them and hopefully its easy too. 

Thanks a lot and if you guys have any threads you think I should take a look at please do so and post the link below I am trying my best to learn much more about this OS and expand my knowledge on it.

---

### Post by astrobob.tk on 2012-02-05
> **backhost said:**
> So today I finally got the chance from upgrading from xp to ubuntu and I love the user interface on this OS. I usually do web development work and web design and I am in need of help with finding good top of the line programs that can help me with my work environment.

I would appreciate if you guys could suggest me some programs like a php text editor , image editor, and any other useful programs that you think I would like and could use. Ill download them and hopefully its easy too. 

Thanks a lot and if you guys have any threads you think I should take a look at please do so and post the link below I am trying my best to learn much more about this OS and expand my knowledge on it.

Welcome to the community. You've come to the right place.

I am no programmer but from my use of two text editors I can suggest to you:

gedit (already installed by default): View > Highlight mode > Scripts > PHP

geany (currently using it; requires installing): Document > Set Filetype > Scripting Language > PHP source file

The default image editor: The GIMP (a bit advanced & more flexible than *hotosho*)

No need to manually download anything. To search & install a software: Applications > Ubuntu Software Center (as you learn more you will install through other ways like "synaptic" or from the terminal)

I will leave the rest for others to help you; or I may return if I can help ;)

cheers

---

### Post by backhost on 2012-02-05
Thanks, I am going to check out the text editor that is already installed with the OS.

Anyone know if I can run a localhost server with apache and mysql on my computer running this distro? Something like xampp thanks.

---

### Post by aasdfasdfg on 2012-02-05
As described [here]("https://help.ubuntu.com/community/ApacheMySQLPHP"), you can install the LAMP stack by running the following from a terminal:
```
apt-get install tasksel
tasksel install lamp-server
```(with proper permissions)

---

### Post by backhost on 2012-02-05
Thanks I just found that page, so after i run those two commands I will have a LAMP server on my computer? Then where do I upload my php files / test files to try it on my computer?

---

### Post by LinuXofArabiA on 2012-02-05
[COLOR=Navy][COLOR=Black]Hello backhost and welcome to the world of open and free software. I am not a web developer by any means, but you know how in today's world one cant claim to be a proponent of free software and not have some knowledge of the tools to use it or defend it. Web page writing is not exception. To that effect, I have been toying with a free web development app available in the software center called 'bluefish'. You can download it. I dont claim it is the best, but I have been using it and I have no complaints. It serves my needs.

On a side note, are you familiar with Drupal? If you are into web development, then I am assuming you definitely are aware of it. If you are not then you must. It has been rated as one of the 10 most popular open source software, and it just happens to be for web development. [/COLOR] [COLOR=Black]

Also, 'Firebug' comes to mind as well. I havent tried it yet, but from the description, it seems to be quite a useful application. Visit 'firebug.com'[/COLOR] [COLOR=Black]

I hope this info helps. Maybe you already know all of it, but this is all I have.[/COLOR] [COLOR=Black]

Good luck and welcome to Ubuntu![/COLOR] 
[/COLOR]

---

### Post by aasdfasdfg on 2012-02-05
> **backhost said:**
> Thanks I just found that page, so after i run those two commands I will have a LAMP server on my computer? Then where do I upload my php files / test files to try it on my computer?

Yeah, the first command installs tasksel, and the second uses tasksel to install LAMP.

**Tasksel** is a nifty utility that provides "macros" for installing groups of packages at once. It has a "graphical" mode (using ncurses in a terminal) so you might want to have a look at that instead of running the second command. That way, you can get a feel for what kinds of things Ubuntu is used for (I am suggesting since you said you are new to Ubuntu). You should be able to find the LAMP stack in that list as well.

The default directory is ```
/var/www
```People like to use all sorts of configurations, so everything is configurable and nothing is set in stone. Some useful links:
[stackexchange]("http://askubuntu.com/questions/19898/whats-the-simplest-way-to-add-files-to-var-www")
[that same page as before has a testing example farther down the page]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual_Hosts")

---

### Post by backhost on 2012-02-06
Thanks to everyone that posted all the helpful information, I got the LAMP working and I installed bluefish I love that program and the way everything is.

I am just having one problem when I go to edit or save a file in the www directory it says I don't have permission so I am guessing there is some type of command I have to run to let me write and delete in the directory thanks.

---

