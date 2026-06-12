---
title: "Linux app to make a database schema and some diagrams"
date: 2005-05-25
forum: Programming Talk
---

### Post by sapo on 2005-05-25
I have to make a database project here and have a printed version of the schema.. but i cant find any app to do it in linux...

I m used to do in paper but its for a public company.. then i have to print it in some kind of "readable" format... and my handwrint isnt readable at all...

Anyone knows how can i make a database schema like.. table relations, field descriptions... etc?

thanx :D

---

### Post by deuce868 on 2005-05-25
Check out dia and see if it will do it. I know it does UML diagrams and some others, but not 100% sure if it does database. If not check to see if there are any downloadable plugins for it before you give up on it.

---

### Post by sapo on 2005-05-25
[QUOTE=deuce868]Check out dia and see if it will do it. I know it does UML diagrams and some others, but not 100% sure if it does database. If not check to see if there are any downloadable plugins for it before you give up on it.[/QUOTE]

I ve found this:

[http://knoda.sourceforge.net](http://knoda.sourceforge.net)

This is what i need.. but it needs kde, i dont have kde and cant install cause i have some breezy packages that conflicts with it  ](*,) 

I ve found this too
[http://www.openoffice.org/product2/base.html](http://www.openoffice.org/product2/base.html)

But its not in the ubuntu reps  ](*,)

---

### Post by deuce868 on 2005-05-25
does dia not do it then?

---

### Post by Luke Redpath on 2005-06-09
Take a look at DBDesigner

[http://www.fabforce.net/dbdesigner4/index.php](http://www.fabforce.net/dbdesigner4/index.php)

---

### Post by sapo on 2005-06-13
[QUOTE=Luke Redpath]Take a look at DBDesigner

[http://www.fabforce.net/dbdesigner4/index.php](http://www.fabforce.net/dbdesigner4/index.php)[/QUOTE]

that is exactly what i m looking for.. thanx a lot  :grin:

---

### Post by froguz on 2005-06-14
[QUOTE=Luke Redpath]Take a look at DBDesigner

[http://www.fabforce.net/dbdesigner4/index.php](http://www.fabforce.net/dbdesigner4/index.php)[/QUOTE]

ubuntu users may have problems installing DBDesigner 4 from the tarballs.
this is the way it worked for me:

1. use alien to convert .rpm into .deb file:

sudo alien package.rpm package.deb

2.make sure you have this dependencies (open the image):

[image](http://www.archivum.info/ubuntu-es@lists.ubuntu.com/2005-02/jpg00004.jpg)

3.install with dpkg:

sudo dpkg -i package.deb

4.now you can run DBDesigner 4 with: startdbd

good luck  ;-)

---

### Post by KLineD on 2005-10-11
Ok I tried converting the RPM and installing from the tar, but everytime I try to connect to MySQL server (localhost) I get an error saying "Unable to load libmysqlclient.so"

Has anyone figured this one out? 

Thanks!

---

### Post by UbuWu on 2005-10-11
[QUOTE=sapo]
I ve found this too
[http://www.openoffice.org/product2/base.html](http://www.openoffice.org/product2/base.html)

But its not in the ubuntu reps  ](*,)[/QUOTE]

On breezy it is installed by default (you can find it in the office menu).

---

### Post by lupo on 2005-10-19
[QUOTE=KLineD]Ok I tried converting the RPM and installing from the tar, but everytime I try to connect to MySQL server (localhost) I get an error saying "Unable to load libmysqlclient.so"

Has anyone figured this one out? 

Thanks![/QUOTE]
Hi,
have you found a solution?
I've looked for a solution for 2 years.... But without success!! :( 
Once it worked, but then I had to reinstall the notebook and I forgot, what I had done to make DBDesigner4 working...
At the moment I'm using the windows-version with wine ;) 
Let's hope, that the follower version "mysql workbench" will be out soon!
[Here]("http://www.openwin.org/mike/index.php/archives/2005/09/mysql-workbench-alpha-released/") you find some infos about the new version.
Greets
 Lupo

---

### Post by Cosmin on 2005-11-25
[QUOTE=lupo]
Let's hope, that the follower version "mysql workbench" will be out soon!
[/QUOTE]

The alpha version is out! :D

[http://forums.mysql.com/read.php?3,56274,56274#msg-56274](http://forums.mysql.com/read.php?3,56274,56274#msg-56274)

---

### Post by lupo on 2005-11-25
Yea, 
great! Thank's for the info!
But unfortunately I can not start the app: :( 
*./mysql-workbench-bin: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory*
Any ideas?

---

### Post by Cosmin on 2005-11-25
libpcre.so.0 doesn't exist in Ubuntu Breezy!

A sim link to libpcre.so.3.11.0 should fix the error:

```
sudo ln -s /usr/lib/libpcre.so.3.11.0 /usr/lib/libpcre.so.0
```

Good luck!

It's working for me :D

---

### Post by Cosmin on 2006-04-27
FYI: **MySQL Workbench 1.0.6 beta released** :D 

[http://forums.mysql.com/read.php?113,84898,84898#msg-84898](http://forums.mysql.com/read.php?113,84898,84898#msg-84898)

---

