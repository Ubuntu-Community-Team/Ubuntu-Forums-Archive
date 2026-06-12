---
title: "HOWTO: Web Development in Ubuntu"
date: 2006-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by kingzasz on 2006-01-02
This guide is taken from my site, zimmertech.com at this URL:  
[http://www.zimmertech.com/tutorials/web-design/62/linux-web-development.php](http://www.zimmertech.com/tutorials/web-design/62/linux-web-development.php)

[SIZE="5"]Web Development in Linux[/SIZE]
*Tips and Tricks about designing web sites in Linux*

The purpose of this guide is to help Linux users be better and more efficient web developers without running Windows. 

[SIZE="4"]Advantages of Linux[/SIZE]

Linux has many advantages over Windows. For me, it is much more stable then Windows. I can keep my machine running without a reboot for an average of 4 months. That said, Windows XP is much more stable than ME or 98, which I had been running before. Another advantage is multiple workspaces. When I work, I can usually have over a dozen programs running--a few Firefox windows, IE, Photoshop, Email, FTP, local terminal, SSH, a coding program, a billing program, a bunch of directories, etc. This can quickly fill up a Windows taskbar. In Linux, I can keep everything organized. All coding windows in one workspace. All server windows in another (SSH and FTP). Last, if you use a LAMP environment (Linux/Apache/MySQL/PHP), then you can easily test on your own server before ever uploading to the web. Windows cannot perfectly emulate this.

[SIZE="4"]Program Installatoin[/SIZE]

Almost all of the programs that I listed can easily be installed through System | Administration | Synaptic Package Administrator) or at the command line through "sudo apt-get install programname". For the Windows programs, install wine, then download the Windows executable. Then type "wine programname.exe" in the terminal to install. So whenever you see a program name in this guide, try installing the package through Ubuntu's Synaptic Package Manager.

[SIZE="4"]Coding[/SIZE]

There are many options for coding in linux. Emacs, vim and a host of other editors such as gedit work fine. I prefer programs specifically built for web development such as Bluefish for Gnome or Quanta for KDE. These programs provide a lot of added functionality such as project management, tag help, table/form builders, syntax checking, and many useful plugins (such as tidy to beautify your code). Another option that I like is the internal preview. I can hit f5 to preview the current document in a inline browser without changing windows. Unfortunately, this will not run PHP code, so sometimes it is not very useful. Regexxer is a great GUI program that will let you do universal search and replaces. So you can search all of the files on your hard drive for a certain text string, then replace it with something else. It uses Perl style regular expressions so it's power is almost endless.

[SIZE="4"]FTP[/SIZE]

I have not found a great FTP program for Linux yet. gFTP is the best I found, but I don't like its interface and I've had problems with it. So for most jobs, I run my favorite FTP program Filezilla under Wine.

[SIZE="4"]SSH[/SIZE]

When I look for hosting, one of my requirements is SSH access. Because I use a lot of content management systems, SSH is incredibly valuable. Instead of extracting Exponent locally then spending all day FTPing the files up, I upload the compressed version and then uncompress it using SSH on the other end, saving a ton of time. Or if there are permission problems on files, I can use a recursive chmod (chmod -R 644). If you are reading this guide, I'm sure you know the advantages of the linux command prompt. The "ssh" command works fine from Linux, or Putty runs perfectly under Wine if you want an easier to use program with more options.

[SIZE="4"]Graphics Design[/SIZE]

Linux is weak in graphics design. Almost all graphics design programs are meant to run on Windows. Luckily, there are a few options.

[SIZE="3"]VNC[/SIZE]

The first option is to not run your graphics design program on Linux at all. This is the most problem free solution because your graphics program (probably Photoshop or Paint Shop Pro) will be running on a Windows machine. The downside is speed. You can forget using brushes. But this option worked for me for almost a year. First, you need to have a windows machine on the network. On that machine, install TightVNC, and start up the TightVNC server. Then on your Linux box, install a program such as krdc to connect to this VNC machine. Just type in the servers IP address, followed by a ":0". So for me, I enter "192.168.1.105:0".

[SIZE="3"]Wine / Crossover[/SIZE]

Wine and Crossover are Windows emulators that run on Linux. They allow you to run many Windows programs in Linux. Wine is free and can run many Windows programs including Photoshop 7.0. But it still has problems with many programs. A slightly better product is Crossover. Crossover Office is not free, but costs about $40. But it will run many popular programs almost perfectly--including the entire Microsoft Office suite, and Photoshop 7.0. Unfortunately, even Wine and even Crossover cannot run Paint Shop Pro, or Photoshop CS (and CS2), so you have to use older software. Another downside to this option is that there are bugs and glitches.

[SIZE="3"]GIMP[/SIZE]

GIMP is an open source graphics design program built for Windows. It is a very capable program. In my opinion, it is not as good as Photoshop for a variety of reasons--more difficult interface, less options, and less tutorials on the internet. But if the other options do not work, consider GIMP.

[SIZE="4"]Local Server[/SIZE]

There are many advantages to designing locally. Mainly, you don't have to FTP every file that you change each time you want to test something.
To install, follow these instructions. These are taken from a great guide to installing a public Ubuntu server.

**MySQL **

Type the following in the command line
```
 apt-get install mysql-server mysql-client libmysqlclient12-dev 
```
Then to set your mysql root password:
```
mysqladmin -u root password yourrootsqlpassword 
```

**Apache and PHP **

```
apt-get install apache2 apache2-common apache2-doc apache2-mpm-prefork apache2-utils libapr0 libexpat1 apt-get install autoconf automake1.4 autotools-dev libapache2-mod-php4 libkrb53 php4 php4-common php4-dev php4-imagick php4-mcrypt php4-rrdtool php4-sqlite php4-curl php4-domxml php4-gd php4-imap php4-ldap php4-mcal php4-mhash php4-mysql php4-odbc php4-pear php4-xslt 
```

Now place your web files in "/var/www/" or "~/public_html/". Make sure that your files are chmoded to at least 644 (owner read/write, group and other read). Now open up your browser. For files in "/var/www/", type "http://localhost/" and for files in "~/public_html/", type "http://localhost/~username/".

Unless you love editing your mysql database through the command line, I would recommend using a GUI program to create/edit databases. My favorite is phpMyAdmin. It is web based, so install it in /var/www or ~/public_html/. This is a package in Ubuntu that will automatically install in your /var/www, so to use it, just type in your browser "http://localhost/var/www/phpmyadmin/" ([http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) also works)

There are a few things you want to do to configure apache. You probably want to enable .htaccess. To do this, type "sudo gedit /etc/apache2/apache2.conf", then add this at the end:
```
<Directory />
AllowOverride None
</Directory>
<Directory "/var/www">
AllowOverride Options
</Directory>

#copy and paste this to allow .htaccess in specific directories
<Directory /var/www/directorytoallowhtaccess>
AllowOverride All
</Directory>


# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*
```

Before this will work, you need to restart apache. In the command line, type "sudo apache2ctlrestart".

Thats it! You have a working Linux server

[SIZE="4"]Testing
[/SIZE]
IE runs well under Wine. To ease your install, use "winetools".

[SIZE="4"]Other[/SIZE]

Karm is a great billing program. You can easily record the time you work on each project, then easily print out a invoice with your total time and history
Another idea that you might want to consider is to get dual monitors (using 2 monitors at once). This saves the time from switching between desktops--you can code for a Window and review the result without minimizing or maximizing anything.

Thats it! If you have any other tips and advice, please comment below. 

Thanks! :D

---

### Post by kingzasz on 2006-01-16
Does anyone have any suggestions?  

For example, I cannot get OpenType fonts to work in Photoshop7 under Wine.  Has anyone fixed this?

---

### Post by JimmyJazz on 2006-01-17
I would really reccomend just learning the Gimp (v3.6) and not wasting time with PS or any windows application.  Designers have been a bit brainwashed into the Photo Shop method over the years and I think its time that stopped.  I do all my design in GIMP and use Bluefish for CSS, PHP and HTML

---

### Post by pinballkid on 2006-01-17
[inkscape]("http://www.inkscape.org") is definitely worth mentioning. I've been a photoshop junkie for years, and I'm new to inkscape, but I think it has a lot of promise.

---

### Post by curtis on 2006-01-17
Instead of using VNC to use photoshop, you should try FreeNX.
I'm not sure if you can do it GNU/Linux -> Windows though...

---

### Post by endersshadow on 2006-01-17
[QUOTE=pinballkid][inkscape]("http://www.inkscape.org") is definitely worth mentioning. I've been a photoshop junkie for years, and I'm new to inkscape, but I think it has a lot of promise.[/QUOTE]

It should be noted that Inkscape is a vector based graphics program, and it's proprietary counterpart is Adobe Illustrator.  Inkscape is a phenomonal program, and I use it a lot, but it is not ideal for web based graphics because web graphics must be rastorized.  While it is true that you can go to File>Export Bitmap in Inkscape, it is necessary to understand that from an OSS software solution for web based graphics, GIMP is the way to go.

However, if you're going to cough up hundreds of dollars for Photoshop or Paint Shop Pro, I urge you to try out [Pixel](http://www.kanzelsberger.com/pixel/?page_id=12).  You can also download the demo for free to test it out.  It is supposed to be much more advanced than the GIMP, and it includes the one window interface.  I actually just downloaded it now, and I will play with it a bit later.

Moreover, it's also important to note that graphics design and editting, by its nature, are *not* easy tasks, and nobody should expect a decent graphics program to be easy or simplified by any means.  Graphics editting is a very complex task, and the programs that are designed to do it reflect that in their complexity.  I feel that I had to include that disclaimer because many times people who don't have Photoshop experience, and try out the GIMP often complain of the level of difficulty in using it.

---

### Post by steffen on 2006-01-17
You'll be happy to know that FileZilla 3 will be available for Linux as well. You can test a nightly build by visiting [http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php). Simply unpack to a directory and click on the filezilla icon in Nautilus to run it. Works great for me so far, even though it's only a nightly build. Don't expect it to work yet, though :)

---

### Post by kingzasz on 2006-01-17
Filezilla for Linux.. thats awesome!

It turns out that Linux and Photoshop under wine do run opentype fonts... I was just having problem with one font and assumed that it applied to all opentype fonts.

---

### Post by soma on 2006-01-17
I am very surprised this thread does not mention the[ Eclipse IDE]("http://www.eclipse.org/eclipse/"). It is my tool of choice for any platform at the moment, and I would label myself being a web developer at the scripting side. I currently use Eclipse for developing Ruby on Rails webapps, with the amazing new plugin [RadRails.]("http://radrails.org")

I have previously done developing in both PHP and J2EE, both in this IDE, and for java, its outstanding. For PHP there is the [phpeclipse plugin]("http://www.phpeclipse.de/").

For my development projects, from the coding side of it, I would consider Linux, and Ubuntu specifically, to be the platform to develop in. My second choice would be Mac OS X, but I personally rather use Linux because of the ease of apt and the control over the OS. Linux is programmer-friendly, and I love it!

- albert
[http://albert.delamednoll.se](http://albert.delamednoll.se)

---

### Post by Kremonte on 2006-01-17
Good HOWTO,
In the 'installing mySQL' portion, mysqladmin package does not exist in repos for me (with uni/multiverse) Maybe you meant mysql-admin?
In the 'installing apache/PHP' portion, you have an apt-get install right in the middle of the line. Maybe you meant to leave it out or for it to be in it's own code block?

Also, this is just a personal preference but the -u root password in apt-get seemed akward. I prefer sudo :D

All in all though, helped me get my box set up quickly, so I can stop using my windows system for web development :KS

EDIT: Just re-read it, wanted to make a few comments;
Wine can run Photoshop CS and CS2, the former works much better, and both can run (nearly?) flawlessly with a few Wine hacks. I personally have not tested Wine with CS2 (doesn't have many improvements over CS1 :P)
Also, for Photoshop users who cannot get it to work well enough, you can try GimpSHOP. It's nowhere near Photoshop still, but the menus and trees are very well placed to some-what emulate Photoshop. Although it's mostly aesthetic, it helps...

---

### Post by hen3rz on 2006-01-17
In my experience phpMy Admin is installed in /var/www/ but is viewed in localhost from [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin) not:
> [http://localhost/var/www/phpmyadmin/](http://localhost/var/www/phpmyadmin/)
As you mentioned.

All in all great tutorial.

---

### Post by siennalizard on 2006-01-17
Hey guys.
From the point of view of code file editing (in my case, PHP, CSS, conf and SQL files), I used to use only Windows tools: namely UltraEdit, which I found very reliable - the usual point-and-click stuff. For FTP, I used Filezilla.

I got back into Linux, and tried to find equivalents of these apps, but wasn't particularly happy with them (gftp is quite like filezilla (2 panes and drag-n-drop), so I bit the bullet and changed to the text-only terminal editor, Vim. I thought I was mad, as the going was very slow to start with, but I can honestly say that I now can work _much_ faster. This page provides a configuration file for Vim which makes it much easier to get your PHP done, with all the features (and more) that I was used to in UltraEdit (command completion, neat formatting, pretty printing, shortcuts for frequent functions, scripting, templates, etc.): 
[http://www.schlitt.info/applications/blog/index.php?/archives/278-Comfortable-PHP-editing-with-VIM.html](http://www.schlitt.info/applications/blog/index.php?/archives/278-Comfortable-PHP-editing-with-VIM.html)

I still find it pretty unbelievable that I'm using a text-only tool that would be just as much use from an early 80's unix terminal, but it's so well developed, and you can see where other coders have made it so fast to use. No amount of useability studies, etc. can ever create the sort of software like Vim (and Vi before it) that has just been used for years and years and improved during that time.

For ftp, I now use lftp. If you've got any MSDOS or unix command line experience, that translates perfectly to lftp. Its like doing cli file management, but you can practically forget that the remote files are on an FTP server.

My advice is to persevere: don't try to find linux equivalents of your Windows apps: the "Windows way" is not always the fastest. Just give it a full week or so with Vim and lftp, and see if you can pick it up. I was shocked. I'm happy to help you get started. Just PM me with your question, or stick it in a thread and let me know.

All the best, guys.
J.

---

### Post by siennalizard on 2006-01-17
[QUOTE=hen3rz]In my experience phpMy Admin is installed in /var/www/ but is viewed in localhost from [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin) not:

As you mentioned.

All in all great tutorial.[/QUOTE]

Yeah. Capitalisation, though. The Breezy default is [http://localhost/phpmyadmin](http://localhost/phpmyadmin), which does seem odd, but that's where to find it.

J.

---

### Post by quietglow on 2006-01-17
> nd both can run (nearly?) flawlessly with a few Wine hacks

I always see this in reference to matters wine and photoshop, but when I go hunting, I can never find these hacks. Do you have any places to look? How about leading google searches? :)

---

### Post by kingzasz on 2006-01-19
Thanks for the suggestions.  I made the fixes in the HOWTO.

---

### Post by browneyedgirl65 on 2006-01-26
Thanks very much for all these tips, i'm hoping to get to the point where I can do local web dev...tres cool.

However, I get to the point of
sudo apache2ctlrestart
and it comes back with
sudo: ...: command not found

not finding anything with whereis, which.  I rehashed the path, but no go.

?

I have the basic default $PATH (eg, I haven't added or edited this since installing ubuntu), do I need to add to this?  which apache2 gives me /usr/sbin/apache2

AHA!  there should be a space before "restart"...i just spotted apache2ctl in the sbin dir...shoudl fix that in the top post...

BEG

---

### Post by macluvjay on 2006-01-26
after:
 $ sudo apt-get install mysql-server mysql-client libmysqlclient12-dev

I get this:
...
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

can anyone tell me wht this means?

I'm running Breezy on a Rev. B iMac

---

### Post by kingzasz on 2006-01-29
Does "apache2ctl -k restart" work?

---

### Post by DonQuixote on 2006-01-30
[QUOTE=kingzasz]Does "apache2ctl -k restart" work?[/QUOTE]
It does for me.

John

---

### Post by el_rata on 2006-01-31
nice tips ... thanx ...

     RATMAN

---

### Post by jezjones on 2006-02-03
I have to say that this covers it pretty well, good HOWTO!

I am a web dev and i have switched to linux alternatives rather than trying to use wine and such.
Bluefish is an execellent editor for web scripting, and by that i mean html, xml, javascript, css, php et all. For classes in php it does colour coding which is nice but that is about all. This has always been enough for me.

Activestate's Komodo although not free is a pretty good php (and others) IDE with proper integration with the interpreter. I mention this non-free software as companies will often stump up £700+ for macromedia products, so less than £200 for an IDE is pretty good value.

For image manipulation GIMP is fine, if you are normally creative with PS then persevere with GIMP it can do alot!
For the simple web stuff that most web developers do (cropping etc) GIMP is pretty easy to use, ie a 10 minute tour.


One thing i have found very useful in my current job is the Terminal Server Client which was bundled in Gnome, which works perfectly to remote desktop to a windows 2003 server on the network. This meant that there was no downtime when switching from windows to linux on my desktop.

As the web servers at work are solaris, having linux as dev servers was easy to sell to the management, but with the promise of no downtime and self support, they saw that developing code on *nix from the start made sense, and saved money.

---

### Post by dunnerz on 2006-02-15
Hi

I have started using Quanta as my IDE for (php) web development in Linux - so far I have found it very nice to use.

However, most of the work I do requires me to connect directly to an ftp box to edit my files - this is possible in Qunta - exepect, I have to install Kubuntu, open up the KDE network settings, and add the new ftp site to it (so that Quanta can see it, and "mount" the remote ftp directory).

Now this seems quite excessive to me + I'm not too keen on KDE - so, if you haven't guess by now - is is possible to access/edit/add/hack the KDE add ftp site widget so that I can use it in Gnome, and therefore use Quanta in Gnome, without having to switch to KDE every time I want to add a new FTP site.

Hope that makes sense.

Many thanks for any help.


[edit: - sorry - i jumped straight to this thread from a search - then read the "before posting here" sticky - I'll ask the question in a help thread - and if I can a reply I'll post the answers back here - cheers)

---

### Post by fraction on 2006-02-15
[JEdit ](www.jedit.org) is a nice graphical text editor that has a good ftp/sftp pluggin allowing you to modify remote files easily.  It'll also syntax highlight just about every file format know to man or machine.

I use it for PHP/Java/Apache config/XML etc.  There's also a PHP plugin that will highlight PHP syntax errors for you.

---

### Post by dunnerz on 2006-02-15
[QUOTE=fraction][JEdit ](www.jedit.org) is a nice graphical text editor that has a good ftp/sftp pluggin allowing you to modify remote files easily.  It'll also syntax highlight just about every file format know to man or machine.

I use it for PHP/Java/Apache config/XML etc.  There's also a PHP plugin that will highlight PHP syntax errors for you.[/QUOTE]

Thanks

I have used JEdit - however, it is an editor - not an IDE, and lacks many of the functions that an IDE has.

Cheers.

---

### Post by KrazyPenguin on 2006-02-15
For FTP: 

How about Nautilus --> File --> Connect to Server

Then just copy and paste the files you want to update.

Maybe not the fastest, but it works.

;-)

---

### Post by dunnerz on 2006-02-16
[QUOTE=KrazyPenguin]For FTP: 

How about Nautilus --> File --> Connect to Server

Then just copy and paste the files you want to update.

Maybe not the fastest, but it works.

;-)[/QUOTE]

thanks - but not very handy when trying to alter/debug/rapid development, etc.

---

### Post by dunnerz on 2006-02-16
[QUOTE=dunnerz]Hi

I have started using Quanta as my IDE for (php) web development in Linux - so far I have found it very nice to use.

However, most of the work I do requires me to connect directly to an ftp box to edit my files - this is possible in Qunta - exepect, I have to install Kubuntu, open up the KDE network settings, and add the new ftp site to it (so that Quanta can see it, and "mount" the remote ftp directory).

Now this seems quite excessive to me + I'm not too keen on KDE - so, if you haven't guess by now - is is possible to access/edit/add/hack the KDE add ftp site widget so that I can use it in Gnome, and therefore use Quanta in Gnome, without having to switch to KDE every time I want to add a new FTP site.

Hope that makes sense.

Many thanks for any help.


[edit: - sorry - i jumped straight to this thread from a search - then read the "before posting here" sticky - I'll ask the question in a help thread - and if I can a reply I'll post the answers back here - cheers)[/QUOTE]


Right - found the answer myself

Very simple in the end....

Open up Konqueuer (spl), and type in 
remote:/

this brings up the remote connection dialogue, where you can add new ftp places, etc.

---

### Post by IdeaG on 2007-06-28
> **dunnerz said:**
> thanks - but not very handy when trying to alter/debug/rapid development, etc.
well, after you set up the connection, you can use your ftp as part of the file system - for example edit files with bluefish just like the local ones. Of course, saving takes a bit longer, but anyway, this pair - nautilus + bluefish - works best for me.

---

### Post by Rohen on 2007-07-14
I find Quanta to be a very good HTML & CSS editor.  I prefer it over Bluefish, Kompozer, and Screem.  I use it for all my current web design.

For Graphics I must back up what someone said earlier, Inkscape shows a lot of promise.  Unfortunately exporting the images are a pain.  Hopefully they will simplify this process in the future.

For FTP, the Firefox plug-in FireFTP works just fine for me.  I avoid having to switch applications.  It does everything I want it to do with a very simple and easy to use interface.

---

### Post by eng.menaemiel on 2007-08-29
thanxxxxxxxxxx

---

### Post by eng.menaemiel on 2007-08-29
Thnxxxxxxxxxxxx

---

### Post by hiloguy on 2007-10-17
> **soma said:**
> I am very surprised this thread does not mention the[ Eclipse IDE]("http://www.eclipse.org/eclipse/"). It is my tool of choice for any platform at the moment, and I would label myself being a web developer at the scripting side. I currently use Eclipse for developing Ruby on Rails webapps, with the amazing new plugin [RadRails.]("http://radrails.org")

I have previously done developing in both PHP and J2EE, both in this IDE, and for java, its outstanding. For PHP there is the [phpeclipse plugin]("http://www.phpeclipse.de/").

For my development projects, from the coding side of it, I would consider Linux, and Ubuntu specifically, to be the platform to develop in. My second choice would be Mac OS X, but I personally rather use Linux because of the ease of apt and the control over the OS. Linux is programmer-friendly, and I love it!

- albert
[http://albert.delamednoll.se](http://albert.delamednoll.se)

I'm running PhotoShop under CrossOver and I just installed dozens of TT fonts right off of one of our Windows machines (it was a drag-and-drop installation across a wireless connection) and they all work fine in P/S.

---

### Post by kpprem@gmail.com on 2007-10-18
My choices are eclipse IDE wih phpeclipse plugin and aptana plugin for eclipse.
phpeclipse takes care of php syntax and aptana takes care of html, css, javascript, ajax, ruby and much more.

Before finding aptana, phpeclipse and eclipse combination, i used to use bluefish and gedit.

---

### Post by dunnerz on 2007-10-18
> **kpprem@gmail.com said:**
> My choices are eclipse IDE wih phpeclipse plugin and aptana plugin for eclipse.
phpeclipse takes care of php syntax and aptana takes care of html, css, javascript, ajax, ruby and much more.

Before finding aptana, phpeclipse and eclipse combination, i used to use bluefish and gedit.


Zend Studio Neon encompasses all of the above, and supports working on remote files (so you don't have to create a whole new project just to write hello world) - although it is still in Beta and seems a bit flaky at the mo (and it costs a lot).

I'd still prefer Quanta over Eclipse, due to lack of remote file support in Eclipse, and its memory hungry nature (Quanta by comparison is quite light weight)

---

### Post by Tips on 2007-10-30
> **kingzasz said:**
> I have not found a great FTP program for Linux yet. gFTP is the best I found, but I don't like its interface and I've had problems with it. So for most jobs, I run my favorite FTP program Filezilla under Wine.

Konqueror makes a great FTP program.  Just right-click on the status bar and split it left/right so that you have two panes in one tab.  The load your remote server with ftp:// or fish:// (sFTP).  Use the left pane for your local machine ~/

If you are working with more than one remote server you can split the tab into extra windows, e.g., a top/bottom split on the right pane...

---

### Post by teishu on 2007-10-31
Great tutorial answers lots of my questions regarding web development in linux...

---

### Post by pooke on 2010-03-20
Hi!

I just found this thread and I think the howto is great.
I'm just curious; has anything gotten updated since this thread started?
I see in this HOW-TO you mention php4. What about php5, now?

Any updatings to be made for MySQL, PHP and Apache?

Also, is it necessary to have Apache admin (??).

Greetings,
pooke

EDIT: I noticed this [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP).

This might replace everything made in this HOW-TO for newcomers like me.

(I have edited this small post many times due to some minor typos..)

---

### Post by airtonix on 2010-03-20
> **endersshadow said:**
> It should be noted that Inkscape is a vector based graphics program, and it's proprietary counterpart is Adobe Illustrator.  Inkscape is a phenomonal program, and I use it a lot, but it is not ideal for web based graphics because web graphics must be rastorized.

Your argument against inkscape is null and void because PSDs or XCFs must also be rastorized.

But you forget that SVG is actually rendered by gecko and webkit based browsers.

So I would say that for web design stop stroking yourself and get real.

Vector based graphics are perfect for websites. 

> **endersshadow said:**
> While it is true that you can go to File>Export Bitmap in Inkscape, it is necessary to understand that from an OSS software solution for web based graphics, GIMP is the way to go.....

See above : 

1. SVG > PNG.
2. No web browser can render XCF or PSD.

> **endersshadow said:**
> 
Moreover, it's also important to note that graphics design and editting, by its nature, are *not* easy tasks, and nobody should expect a decent graphics program to be easy or simplified by any means.  Graphics editting is a very complex task, and the programs that are designed to do it reflect that in their complexity.


A good craftsman never blames his tools.

If you're so awesome as you allude to, then you would make do with mspaint.

> **endersshadow said:**
> I feel that I had to include that disclaimer because many times people who don't have Photoshop experience, and try out the GIMP often complain of the level of difficulty in using it.

More fallacious arguments born of cultural conditioning by brand based schools.


----

I have a teacher that never refers to word processing as just "word processing" its always "microsoft word"....

As if the activity of pressing keys on a keyboard and using a mouse to arrange words on a page is only possible in a microsoft product.

She gets angry when I refer to other software that isn't available for purchase on a supermarket shelf.

---

