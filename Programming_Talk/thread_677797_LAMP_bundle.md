---
title: "LAMP bundle"
date: 2008-01-25
forum: Programming Talk
---

### Post by jzdexta on 2008-01-25
Hi guys
I have just installed xubuntu in my pc with intention of migrating from windows to linux. Im a web programmer using apache mysql and php, in windows i simply install WAMP5 which does everything for me and i was wondering if their is a program bundle housing php, mysql and apache just to ease the hardships of getting the system to function fully in the shortest time possible.

Individual application installation is traumatizing at the moment

Thank you in advance

---

### Post by pmasiar on 2008-01-25
Synaptic is GUI frontend for apt, you may like it more. I know I do ;-)

---

### Post by Tuna-Fish on 2008-01-25
In terminal:
```

sudo apt-get install libapache2-mod-php5 php5-mysql

```

Should do the trick. All the rest is a dependency to those two.

---

### Post by jzdexta on 2008-01-25
> **Tuna-Fish said:**
> In terminal:
```

sudo apt-get install libapache2-mod-php5 php5-mysql

```

Should do the trick. All the rest is a dependency to those two.

Thank you for this response, im actually working on it.

Few questions though:
 - Once through with installation any steps i need to take/follow?
 - Will it install apache, mysql and php?
 - Any configurations other than mysql security issues ?
 - How do i access the applications?

Once again thank you.

---

### Post by Tuna-Fish on 2008-01-25
> **jzdexta said:**
> Thank you for this response, im actually working on it.

Few questions though:
 - Once through with installation any steps i need to take/follow?

Make any configuration you want to. the conf files are in /etc/apache2/, the docs are in [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)
> 
 - Will it install apache, mysql and php?

yes. In debian based distros, stuff is distributed in packages, that have dependencies. if you install a package, you always automatically also install all the depedencies. those 2 packages depend on apache, mysql and php
> 
 - Any configurations other than mysql security issues ?
Well, you should set some sites to be available for starters. at default, it shows  the contents of /var/www in port 80. Change at /etc/apache2/sites-enabled
> 
 - How do i access the applications?

apache starts by default, this can be changed from service settings.
To manually start/stop/restart, use "sudo /etc/init.d/apache2 start/stop/restart"

To access php from the command line, just type php. This, however, is likely not what you want :)
apache automatically renders any page as php as long as it's stored in the www dir with extensions .php .phtml .php3, change at /etc/apache2/mods-enabled/php5.conf

of mysql I don't know, i don't use it all that much.

---

### Post by Tuna-Fish on 2008-01-25
oh, it seems I was talking out of my ***. those only install the mysql connections for php, to install full mysql:
```

sudo apt-get install mysql-server

```

---

### Post by Tuna-Fish on 2008-01-25
I went and said to my friend that there was a bug in the repositories, that you can install php5-mysql without installing mysql. he looked at me oddly, and said that that's normal because you can write and use php scripts that use mysql without having mysql on that machine. I went silent and realized that not only can you write programs like that, I have written several. Stupid me.

---

### Post by leg on 2008-01-25
To access mysql enter something similar to ```
mysql -u user -p

``` which will log me onto the mysql server as user after prompting me for that users password. This is after starting mysql of course ```
/etc/init.d/mysql start
```. An alternative to that would be to install phpmyadmin and work on your databases through that much like you do in WAMP. Can't help you there though as I have never installed that but it may be in apt.

---

### Post by jzdexta on 2008-01-26
Thank you for the great response so far.

I was also wondering if i dont get the functionality i needed from installed packages, how do i un-install the packages installed inclusive of dependancies?

While rolling back what are the repercasions and effects in the overall performance on the whole system?

Regards

---

### Post by LaRoza on 2008-01-26
```

sudo tasksel

```

would have been much easier.

You can uninstal with that command also.

---

### Post by mech7 on 2008-01-26
There is also XAMPP

---

### Post by jzdexta on 2008-01-28
> **LaRoza said:**
> ```

sudo tasksel

```

would have been much easier.

You can uninstal with that command also.

One lesson learnt from your suggestion though is :
"Do not execute a command if you dont know its extensions and what it is meant to do..."

I executed the command and had to re-install the OS thereafter as it un-installed so many other softwares in the process.

Anyway you can never learn how to build if you dont know how to destroy.. another lesson too:)

Thanks for the lessons mate..

---

### Post by xlinuks on 2008-01-28
mech7 mentioned XAMPP, you should really give it a try, it's the easiest way to install apache, php & mysql all together without configuration, I did it (about half a year ago) just from curiosity, they were setup and running in a blink of an eye.
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by LaRoza on 2008-01-28
> **jzdexta said:**
> One lesson learnt from your suggestion though is :
"Do not execute a command if you dont know its extensions and what it is meant to do..."

I executed the command and had to re-install the OS thereafter as it un-installed so many other softwares in the process.

Anyway you can never learn how to build if you dont know how to destroy.. another lesson too:)

Thanks for the lessons mate..

What did you do?!

Did you uninstall something with it? 

Running that command just brings up the list, it doesn't do anything until you tell it to.

---

### Post by jzdexta on 2008-01-28
curiosity killed the cat they say; yes i did something with it. 

I run tasksel and un-check a couple of options in a bid to install video player, i didnt have to wait long to know i had un-checked the wrong option.
Terminal just run lines scrolling up on the screen and im like whats going on, then it say system restarting. I select my start options then i go for cup of tea, when i return i see missing scripts and stuff on screen then system restarting :confused: , this for like 3 times !! now i know my system is gone :).

Have to re-install whole thing again, damn!! ](*,) (learning is a process right?)

I'm happy though coz thats how i learn how to do stuff.

---

### Post by Tuna-Fish on 2008-01-28
> **xlinuks said:**
> mech7 mentioned XAMPP, you should really give it a try, it's the easiest way to install apache, php & mysql all together without configuration, I did it (about half a year ago) just from curiosity, they were setup and running in a blink of an eye.
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

Installing stuff that can be found from apt from outside sources is stupid. If you use xampp, it's all fun and games until you have to update them.

Just using apt, or tasksel, gets you exactly what using xampp will, only, you also get automatic security updates and tight integration with everything else found in apt.

i tested it when I answered to this thread the first time, and it took me less than 15 mins to have a php page render from port 80 when installing from apt, without actually knowing what I needed before i started.

Please don't advocate 3rd party scripts that might break something, now or in the future, to newbies when there is a good method of providing the needed functionality built-in.

---

### Post by LaRoza on 2008-01-28
> **Tuna-Fish said:**
> Installing stuff that can be found from apt from outside sources is stupid. If you use xampp, it's all fun and games until you have to update them.

Please don't advocate 3rd party scripts that might break something, now or in the future, to newbies when there is a good method of providing the needed functionality built-in.

While I do think that the repo route is usually the best way, there is nothing wrong with XAMPP (besides being slightly redundant)

It isn't stupid, just not recommended.

---

### Post by jzdexta on 2008-01-28
> **Tuna-Fish said:**
> Installing stuff that can be found from apt from outside sources is stupid. If you use xampp, it's all fun and games until you have to update them.

Just using apt, or tasksel, gets you exactly what using xampp will, only, you also get automatic security updates and tight integration with everything else found in apt.

i tested it when I answered to this thread the first time, and it took me less than 15 mins to have a php page render from port 80 when installing from apt, without actually knowing what I needed before i started.

Please don't advocate 3rd party scripts that might break something, now or in the future, to newbies when there is a good method of providing the needed functionality built-in.


Well let me get this straight...

You are saying that it is better to get applications using apt-get command because it provide security and integration to existing applications?

if the answer is yes, bet will be following this path all the way through.

One question for this though, how do i know there's an update for existing installed applications?

Thanks for the response/advice

---

### Post by LaRoza on 2008-01-28
> **jzdexta said:**
> 
You are saying that it is better to get applications using apt-get command because it provide security and integration to existing applications?

if the answer is yes, bet will be following this path all the way through.

One question for this though, how do i know there's an update for existing installed applications?

Thanks for the response/advice

The ease, security and reliablility of the repos is usually better than getting a third party app. 

The Update Manager will let you know when updates are available from the repos.

---

### Post by Tuna-Fish on 2008-01-28
> **jzdexta said:**
> Well let me get this straight...

You are saying that it is better to get applications using apt-get command because it provide security and integration to existing applications?

if the answer is yes, bet will be following this path all the way through.

Yes. Note that programs like tasksel, synaptic and aptitude are using the same repositories as apt-get, so they get all the same advantages. I think i know how you managed to break your system using tasksel though; if you untick a box in tasksel, it means you uninstall something. Among the things you can uninstall with it is ubuntu-desktop...

> 
One question for this though, how do i know there's an update for existing installed applications?

There is an icon in your system tray for that. what it looks like depends from your icon theme, for me it's kinda like a red *. This is assuming your computer knows there are updates, by default it looks once a day.

To manually force an update cycle, type "sudo apt-get update && sudo apt-get upgrade" into terminal. this updates everything on your computer to newest versions found in the repositories.

---

