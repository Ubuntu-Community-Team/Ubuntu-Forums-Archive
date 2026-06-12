---
title: "Problems with Xampp"
date: 2007-09-17
forum: Programming Talk
---

### Post by Adicted on 2007-09-17
I don't know what's really happening I hope you all can help me =)

I just installed xampp on my ubuntu 7.04 festy and when i enter into [http://localhost](http://localhost) it request me a password, i don't know why, and I don't know the user and pass


I follow the installation guide in apachefriends's website

Regards, Adicted

---

### Post by mssever on 2007-09-18
Xampp is a useful workaround on Windows, but on Ubuntu I think it's more difficult than necessary. You can get a proper, normal setup easily in Ubuntu without resorting to Xampp:
 ```
sudo aptitude install apache2 php5 mysql phpmyadmin #Add whatever else you want
```The default DocumentRoot is in /var/www. Apache config files are in /etc/apache2 (and set up nicer than Xampp does it).

---

### Post by Adicted on 2007-09-18
Well, thanks, how can I uninstall xampp now?

I'm new on linux, :P

edit: i have uninstall id with: sudo rm -rf /opt/lampp

well, I'm installing that what you suggest me :P I'll post my experience later :P

---

### Post by jreis on 2007-09-18
This will stop Lampp. If you have it working.

**$sudo /opt/lampp/lampp stop** #Note this is the usual path, not necesserily yours

If you are new to linux the most easy and usable way is:

**$sudo nautilus /opt/ **#this will open opt folder as root

then select the lampp folder and click on DEL key. not that this way the lampp folder will be sent to the root trash. if you whant to erase permanently use SHIFT+DEL.

you can also remove using the terminal

[B]$cd /opt/
$sudo rm -r lampp[/B]

ps- to know more about the rm command try typing:
**$man rm**

hope this helps

Mental note: i have to learn to read the post to the end ... sorry!

---

### Post by Adicted on 2007-09-18
now, i used the command who msserver posted:

> sudo aptitude install apache2 php5 mysql phpmyadmin #Add whatever else you want

and when i acces into [http://localhost](http://localhost) it don't works, i don't know what it's happening with my ubuntu xD

---

### Post by mssever on 2007-09-18
> **Adicted said:**
> when i acces into [http://localhost](http://localhost) it don't works, i don't know what it's happening with my ubuntu xD

What are the symptoms?

---

### Post by LaRoza on 2007-09-18
> **mssever said:**
> 
 ```
sudo aptitude install apache2 php5 mysql phpmyadmin #Add whatever else you want
```The default DocumentRoot is in /var/www. Apache config files are in /etc/apache2 (and set up nicer than Xampp does it).

In Feisty:
```

sudo tasksel 

```

Quickly gets Apache2, MySQL, PHP5, and Perl. (Select "LAMPP" from the menu)

---

### Post by Adicted on 2007-09-18
now i have problems with mysql :P are you sure about the command is: mysql and not mysql-server-5.0?

---

### Post by mssever on 2007-09-19
> **Adicted said:**
> now i have problems with mysql :P are you sure about the command is: mysql and not mysql-server-5.0?My bad. I should have looked it up instead of relying on my memory. I would use mysql-server (which depends on the most recent version of mysql so you automatically get updates..

---

### Post by GodsDead on 2007-10-30
Hey there, in searching instead of starting a new topic, and found this, Most of the services used in XAMPP im in need of, and im gonna want to be able to edit files without haveing to login as SU SUDo ROOT whatever.. as its in teh opt dir, its a PAIN in the *** to edit anything.

But yea, gonna need Apache, PHP5 Mysql, phpmyadmin, GD, FTP, SMTP.. errr off the top of my head i cant rememeber, can / should i uninstall my XAMPP and use the command;
> 
sudo aptitude install apache2 php5 mysql phpmyadmin #Add whatever else you want 

If so, where is there a list of things that i can add to that line? THANKS! 
so that i can mix and match the things i need the webserver for!!!!!!

---

### Post by mssever on 2007-10-31
> **GodsDead said:**
> Hey there, in searching instead of starting a new topic, and found this, Most of the services used in XAMPP im in need of, and im gonna want to be able to edit files without haveing to login as SU SUDo ROOT whatever.. as its in teh opt dir, its a PAIN in the *** to edit anything.

But yea, gonna need Apache, PHP5 Mysql, phpmyadmin, GD, FTP, SMTP.. errr off the top of my head i cant rememeber, can / should i uninstall my XAMPP and use the command;

If so, where is there a list of things that i can add to that line? THANKS! 
so that i can mix and match the things i need the webserver for!!!!!!
Search in Synaptic (or aptitude) for what you want, then install it.

For write access, you can do ```
sudo chown -r youruser /var/www
```. After that, you'll have write access.

I personally wouldn't recommend running XAMPP under Ubuntu since using the official packages is just as easy and is better tested.

---

### Post by anthonylane13 on 2008-05-28
I too am having problems with my development environment.  I installed XAMPP, and I also installed to dev programs individually through sudo apt-get install etc...
I'm having problems with it! PHP works, but I can't find phpmyadmin anywhere.  I just ran the following command **sudo apt-get install phpmyadmin** and as far as I can tell, it's installed, but I can't find it on my localhost.
I am not able to set up any database web apps on my local server.
Can anyone tell me how to wipe all the programs and start again.  Bear in mind that I have possibly installed duplicates of some of these programs because I have XAMPP installed as well as installing the elements separately.
I am on ubuntu studio 7.10.
Thanks in advance.

---

### Post by jjgomera on 2008-05-28
don't it stay here: [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) ?

---

### Post by anthonylane13 on 2008-05-28
That's what I thought...
> Not Found

The requested URL /phpmyadmin/ was not found on this server.
:(

---

### Post by mssever on 2008-05-28
> **anthonylane13 said:**
> That's what I thought...The best thing is to completely wipe XAMPP. If you still have problems after restarting everything affected (or rebooting, if that's easier), then uninstall and purge all your dev packages, then reinstall them. It's likely that stuff is stomping all over other stuff.

---

### Post by ice60 on 2008-05-28
here are some links i have for setting it up -
[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)
[http://www.ibm.com/developerworks/linux/library/l-xampp/](http://www.ibm.com/developerworks/linux/library/l-xampp/)
[http://www.apachefriends.org/en/faq-xampp.html](http://www.apachefriends.org/en/faq-xampp.html)
[http://www.debianadmin.com/xampp-all-in-one-web-server-installation-and-configuration-in-debian.html](http://www.debianadmin.com/xampp-all-in-one-web-server-installation-and-configuration-in-debian.html)

---

