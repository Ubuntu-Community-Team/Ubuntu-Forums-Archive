---
title: "PHPEclipse"
date: 2006-09-12
forum: Programming Talk
---

### Post by munwin on 2006-09-12
I downloaded Eclipse from [http://www.eclipse.org/downloads/index.php]("http://www.eclipse.org/downloads/index.php") and extracted it to my home directory /home/mark/eclipse . Next I downloaded [PHPEclipse Plugin]("http://sourceforge.net/project/showfiles.php?group_id=57621&package_id=70009") and extracted it to the relevant directories under the eclipse directory.

I also ran this command so enable Sun Java
sudo update-alternatives --config java

Eclipse starts, and I have created a new PHP Project.
 
I cannot edit any php files I create. In eclipse, I click File -> New -> PHP File. It is created, but I cannot edit it. The PHPEditor frame shows the tab for the file, but doesn't show anywhere to actually type ?!?!?!

Any help much appreciated.
Dam IMG tags, wont attach. A screenshot is here -
[http://www.open-audit.org/Screenshot.png](http://www.open-audit.org/Screenshot.png)

---

### Post by nereid on 2006-09-13
Why haven't you used the eclipse package provided by Ubuntu?

IMHO it seems to be a problem with the PHP plugin.

---

### Post by munwin on 2006-09-13
I read here somewhere, that the one in the repo's is not as uptodate as the released version on the Eclipse site....

---

### Post by munwin on 2006-09-14
Yep - the repo one is 3.1.2 and the current site one is 3.2

---

### Post by gmclachl on 2006-09-14
Zend have released their own Eclipse Plug-In. 

 It may be worth trying that. FWIW I tried PHPEclipse in the past and thought it was awful, for various reasons too long to list here. 

You can find out about it here
[http://www.zend.com/phpide/](http://www.zend.com/phpide/)

George

---

### Post by MblKiTA on 2006-10-04
Got the same problem here - nothing shows in the edit area, when trying to edit or create any .php file... ^(

---

### Post by subes on 2006-11-16
I had to remove anything related to gcj with synaptic, because eclipse always used gcj and ignored my Java configuration via:

update-alternatives --config java

To verify for yourself if it loads with gcj, you may run eclipse from a terminal and have a look at the output.

---

### Post by shining on 2006-11-16
> **subes said:**
> I had to remove anything related to gcj with synaptic, because eclipse always used gcj and ignored my Java configuration via:

update-alternatives --config java

To verify for yourself if it loads with gcj, you may run eclipse from a terminal and have a look at the output.

Indeed, eclipse (at least the debian/ubuntu package) doesn't use java, but take the jvm from the /etc/eclipse/java_home file instead.
It's a bit odd indeed, but there is maybe a reason for it.

---

### Post by behzadsh on 2009-09-28
I have the same problem,
I install eclipse from:
```

sudo apt-get install eclipse

```

after that I do what ever it said in [http://www.phpeclipse.com/wiki/Installation](http://www.phpeclipse.com/wiki/Installation)

PHPEclipse perspective opened successfully but when I try to open an php file it says:
> 
An error has occurred. See error log for more details.

in error log it says:
> 
Problems occurred when invoking code from plug-in: "org.eclipse.jface".


error log attached!


p.s: I'm using linux mint 7 - Gnome - (ubuntu 9)

---

### Post by Irvine_himself on 2009-09-28
Just last week I used Pulse to create a basic PHPeclipse installation, I then installed a few goodies by hand from the Project Amateras, (the Html/Java/Javascript  and  "Air Gear" editors). Pulse recognised the new "dropins" and even appeared to update a couple.

It works fine.

[http://www.poweredbypulse.com/eclipse_packages_linux.php](http://www.poweredbypulse.com/eclipse_packages_linux.php)
[http://amateras.sourceforge.jp/cgi-bin/fswiki_en/wiki.cgi?page=EclipseHTMLEditor](http://amateras.sourceforge.jp/cgi-bin/fswiki_en/wiki.cgi?page=EclipseHTMLEditor)

---

### Post by chrisjsmith on 2009-09-29
Don't use the Ubuntu-packaged eclipse.  It's ancient.

Download NORMAL 3.5 Ganymede eclipse from [http://eclipse.org/](http://eclipse.org/)

Decompress to ~/bin/eclipse/

Run ~/bin/eclipse/eclipse

Then use the add / update software to install PHPeclipse from their update URL (which I don't have handy).  

This works perfectly on 9.04!

---

