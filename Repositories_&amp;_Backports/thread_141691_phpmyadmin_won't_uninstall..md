---
title: "phpmyadmin won't uninstall."
date: 2006-03-08
forum: Repositories &amp; Backports
---

### Post by Aine on 2006-03-08
Hello all. 

I've tried to google it and search here, and I can't figure out my solution.

When I go to remove phpmyadmin, I get an error

```
E: phpmyadmin: subprocess pre-removal script returned error exit status 127
```

I tried to do

```
sudo apt-get clean
```


apt-get check displays


```
travis@ubuntuTravis:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  phpmyadmin: Depends: apache2 or
                       httpd
E: Unmet dependencies. Try using -f.
travis@ubuntuTravis:~$

```

Any help will be appreciated.

---

### Post by Xian on 2006-03-08
[QUOTE=Aine]You might want to run `apt-get -f install' to correct these.[/QUOTE]

What is the result of 'apt-get -f install'??

---

### Post by Aine on 2006-03-08
It wants to install apache and apache common...but when I install it then try to uninstall it again, it'll uninstall everything except phpmyadmin giving the same error.

---

### Post by ctucker10 on 2006-03-10
You describe the same problem I have. Here's the output when trying to remove phpmyadmin from the command line:

ubuntu@ubuntu:~$ sudo apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 69926 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 12: db_get: command not found
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

I want to install a local webserver with apache2, php4, mysql. phpmyadmin is one of the tools I use to work with mysql databases. Anyway, I was trying to get all this setup yesterday and I screwed up somewhere along the line. I just want to uninstall everything and start from scratch but, phpmyadmin won't uninstall.

Any help is appreciated. Thanks.

---

### Post by ctucker10 on 2006-03-10
Ubuntu is my first Debian-based distro and I certainly don't know the intracacies of how the apt-get handles package management but, here's what I did to get phpmyadmin to uninstall.

DISCLAIMER: Use this procedure at your own risk.

I saved a copy of the unedited offending file(script):

**cd /var/lib/dpkg/info/**

**sudo cp phpmyadmin.prerm phpmyadmin.prerm.orig**

Then I opened the file in a text editor:

**sudo gedit phpmyadmin.prerm**

Next, I commented out Line 12 by adding the "#" character to the beginning of the line. Then I saved the file. 

Here's the output after my edit session:

ubuntu@ubuntu:~$ sudo apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 69926 files and directories currently installed.)
Removing phpmyadmin ...

I double checked  the sucessful uninstall in Synaptic Package Manager. phpmyadmin is no longer flagged as "broken", it is uninstalled.

---

### Post by maddog39 on 2006-03-10
What I highly suggest you do is download a web server package for free. The best one that runs on linux is XAMMP and it pre-installs all these things for you, PHP5, MySQL5, and PHPMyAdmin.

Heres the link to the site/download page.
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by Aine on 2006-03-10
Strangly, Maddog, I've used XAMPP when I was on windows and LAMPP (same thing) when I first switched to Linux. The problem came when I wanted to use LAMPP and the default linux services (apache and mysql) were messing my LAMPP up..so I tried to uninstall them and its what gave me my error.

@Chucky, I will give that a shot through SSH since I'm no where near home, and thanks for the help! :D

---

### Post by Aine on 2006-03-11
Where can I send my love for you?! It worked like a charm..I really want to thank you for helping me with this!!

---

### Post by Boss Happy on 2006-03-15
CTucker,
I just had the same problem and your fix worked beautifully.  Thanks!
\\:D/

---

### Post by NoNo_231 on 2006-03-16
Thanks, that was really great. 

I wanted to use LAMPP too, because I use it only for testing and there is no need to have all the system running all the time, but I once I installed I couldn't unistall it. Maybe this sould be corrected in some next version.

Thanks again ctucker10.

---

### Post by patsissons on 2006-03-17
hmmm not really a fix, more like a hack... but hey, if it gets phpmyadmin uninstalled I'm more than happy.  This brings to mind however, whoever is maintaining the phpmyadmin package should really fix this issue in the pre-uninstallation script.

---

### Post by JurB on 2006-03-19
Thanks for the solution!

---

### Post by Burke on 2006-03-20
Yeah, somebody poke Yada with a pointy stick, this prerm is broken ;) 

Thank you so much for the hack, it worked perfectly, that has been irritating me for months.

---

### Post by fatsamurai on 2006-03-26
Add my thanks to that list too. Worked a treat!

:-D

---

### Post by scottgrant on 2006-03-28
Thanks all, your fix just saved me too!

I also use XAMPP on my windows box, but wanted to 'get smart' and do it all myself like a real unix techie...  And paid the price :-)

Still, nobody said learning would be painless.., so here I go again...

---

