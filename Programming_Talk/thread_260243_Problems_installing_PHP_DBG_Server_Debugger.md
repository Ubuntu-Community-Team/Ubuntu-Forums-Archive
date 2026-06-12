---
title: "Problems installing PHP DBG Server Debugger"
date: 2006-09-18
forum: Programming Talk
---

### Post by MystaMax on 2006-09-18
Hello, I'm trying to use the [easy eclipse]("http://www.easyeclipse.org/site/home/") package for web dev, and am having troubles getting the debugger correctly installed. So far, I've downloaded the dbg package, unzipped it, and trying following the instructions in the "INSTALL" document. Here it is:

[quote=Install DOC for DBG]In order to install dbg server part follow instructions below.

- Have dbg unpacked in any directory OUT of tree of php sources. For example,
  in $HOME/dbg
  
- Make sure you have compiled and installed php engine. If you use 
  pre-compiled php, do not forget to install php-devel package and 
  make sure php-config is intalled.
  
- run "configure", then "make" command like below (don't forget to supply a 
  valid path to php-config):

$./configure --enable-dbg=shared \
            --with-dbg-profiler \
        --with-php-config=/path/to/php-config \
        --prefix=/usr/lib/php4
$make
$make install[/quote]

I'm running the following:

```

./configure --enable-dbg=shared \
--with-dbg-profiler \
--with-php-conifg=/etc/php4/apache2/php.ini \
--prefix=/usr/lib/php4

``` 
I receive the following errors:

```

loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

``` 
I'm not sure how to troubleshoot this issue? Can someone help? Thanks.

---

### Post by gmclachl on 2006-09-18
sudo apt-get install build-essential 

 should do the trick. 

 george

---

### Post by MystaMax on 2006-09-18
Thanks for the response george. After installing build-essential (which now I know I should of checked), I receive an error stating:

```
./configure: line 1171: php-config: command not found
configure: error: Cannot find php-config. Please use --with-php-config=PATH

```

If the path (etc/php4/apache2/php.ini) I provided isn't correct, then I'm not sure what they want? any ideas?

---

### Post by gmclachl on 2006-09-18
do you have PHP installed?

 PHP config is a tool to check php config details. 
 
 If you type something like 

 which php-config  

 I haven't installed the debugger in Eclipse, but I guess php may be bundled with that so in that case find the path to the php bin directory for your IDE and see if php-config is in that.

 George

---

### Post by MystaMax on 2006-09-18
I actually installed PHP Apache and MySQL before even getting started w/ easy eclipse. I verified it was working by creating a file with the phpinfo() in it, and that worked just fine.

When I run "which php-config", it just returns back to the next line displaying no information.

---

### Post by gmclachl on 2006-09-18
What happens if you type in 

  which php-config

---

### Post by MystaMax on 2006-09-18
nothing, no errors, no feedback, it just returns to back to the commandline, awaiting another command.

---

### Post by gmclachl on 2006-09-18
Did you install php-cli?

---

### Post by MystaMax on 2006-09-19
my fault, my reply did not get to you yesterday.  Thanks for taking the time to help.

I haven't installed CLI. I didn't see it anywhere that it was specifically needed. Although, I may of missed it. 

I was trying to locate something stating if this worked w/ php5. I would like to use php5 with eclipse. Can I install php5-cli? I found this on the [dbg website]("http://dd.cron.ru/dbg/home.php"):

**DBG 2.15.1 released (the most recent free version)**
[LIST]
[*]All php versions from 4.0.6 up to 4.4.2 and from 5.0.0 up to 5.1.2 are supported.
[*]Compatibility issues with gcc4 are fixed.
[*]Improved support for 64bit systems
[*]Improved building scheme[/LIST]

---

### Post by gmclachl on 2006-09-19
Are you using the Zend Eclipse  Plug-in. I think that comes bundled with everything. Although I haven't used it for a bit so can't remember. 

 [http://www.zend.com/phpide/](http://www.zend.com/phpide/)

 You can just apt-get to install php5-cli. 

 George

---

### Post by MystaMax on 2006-09-19
Ok, so I removed everything from easy eclipse and decided to use the PHP IDE from the link you provided. 

It looks as if this has a debugger and web server debugger built in. But, I cant get any of it to work. There isn't much [documentation on how to install and setup the PHP IDE]("http://www.eclipse.org/php/install.php"). I don't know how to set up the IDE to display output in the Debug window in eclipse. I can't get it to highlight errors in syntax. I also can't get the outline to recognize variables, functions, or classes (simple ones, for testing). 

The link above states that:

>              The PHP IDE project does not contain server side implementation for PHP debugging and will              welcome any open source or commercial implementation of the debug protocol              (The debug protocol implemented can be found at [http://www.eclipse.org/php/docs.php)]("http://www.eclipse.org/php/docs.php%29")Thats confusing as it states on the Zend page that a debugger is inlcuded:

>  The package includes:  [Eclipse Platform]("http://download.eclipse.org/eclipse/downloads/drops/M20060609-1217/"),   [JDT]("http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/M20060609-1217/eclipse-JDT-M20060609-1217.zip"),   [GEF]("http://www.eclipse.org/downloads/download.php?file=/tools/gef/downloads/drops/S-3.2RC6-200606270816/GEF-runtime-3.2.zip"),  [EMF]("http://www.eclipse.org/downloads/download.php?file=/tools/emf/downloads/drops/2.2.0/S200606271057/emf-sdo-runtime-2.2.0RC9a.zip"),  [JEM]("http://download.eclipse.org/tools/ve/downloads/drops/S-1.2RC2-200605301123/"),  [WTP]("http://download.eclipse.org/webtools/downloads/drops/S-1.5RC4-200605310507/"), PHP IDE and the Zend Executable Debugger Eclipse Plugin.
It seems like its going to be beyond my knowledge to get this to work correctly. I'll have to continue on windows until this is easier to setup. Thanks for your help, anyway.

---

### Post by gmclachl on 2006-09-19
Hmmm,
      I wouldn't give up just yet. Never used Zend IDE. Another option for you would be to use another plug-in 

 [http://www.xored.com/trustudio](http://www.xored.com/trustudio)

 I have used this one and I like it. It has a built in debugger (PHP4) but you can easily specify an external debugger. To do this you need to install php5-cli. 

George

---

### Post by Colonel Kilkenny on 2006-09-20
The newest Zend IDE needs newer Eclipse than the one in repositories.
Then you need to install umf (whatever that is) and gfe (whatever that is) using eclipses plugin update system and then you can install Zend IDE.
After this steps it is working, at least for me.

---

### Post by MystaMax on 2006-09-20
I actually downloaded the [all-in-one package]("http://downloads.zend.com/phpide/all-in-one/") from the Zend site. I did not install eclipse from synaptic or apt-get.  

The website from the link above states the following:
[quote=Zend PHP IDE Site]
The package includes:  [Eclipse Platform]("http://download.eclipse.org/eclipse/downloads/drops/M20060609-1217/"),   [JDT]("http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/M20060609-1217/eclipse-JDT-M20060609-1217.zip"),   [GEF]("http://www.eclipse.org/downloads/download.php?file=/tools/gef/downloads/drops/S-3.2RC6-200606270816/GEF-runtime-3.2.zip"),  [EMF]("http://www.eclipse.org/downloads/download.php?file=/tools/emf/downloads/drops/2.2.0/S200606271057/emf-sdo-runtime-2.2.0RC9a.zip"),  [JEM]("http://download.eclipse.org/tools/ve/downloads/drops/S-1.2RC2-200605301123/"),  [WTP]("http://download.eclipse.org/webtools/downloads/drops/S-1.5RC4-200605310507/"), PHP IDE and the Zend Executable Debugger Eclipse Plugin.[/quote]

Colonel, Are you referring to any of these plugins here? What features does the Zend PHP IDE offer? Code completion? Code hinting? Code browser?

I downloaded ActiveState's Komodo IDE 3.5, and got it installed and working in about 30 minutes. Its mozilla based so its cross-platform. Although its 30 bucks, its IMO worth it, @ least so far. I currently have a 21 day trial, but hope to get some type of debugging working w/ eclipse in the near future.

---

### Post by Colonel Kilkenny on 2006-09-20
> **MystaMax said:**
> I actually downloaded the [all-in-one package]("http://downloads.zend.com/phpide/all-in-one/") from the Zend site. I did not install eclipse from synaptic or apt-get.  

Colonel, Are you referring to any of these plugins here? What features does the Zend PHP IDE offer? Code completion? Code hinting? Code browswer?

Oh sorry, my mistake. I had to install those plugins, but as it seems that they are providing a package which has them all included my solution was quite stupid.
And it was GFE, not gef :)

But, I'm using Eclipse (from eclipse.org) + zend ide from eclipse update site. I haven't used it much yet nor examined what features does it have. But I can say that it has at least code completion, code hinting and some sort of browser. 

Well, if you have the all-in-one-package downloaded it ain't hard to try it out and see if it suits you. I actually like it a lot.

---

### Post by MystaMax on 2006-09-20
> **Colonel Kilkenny said:**
> 
But, I'm using Eclipse (from eclipse.org) + zend ide from eclipse update site. I haven't used it much yet nor examined what features does it have. But I can say that it has at least code completion, code hinting and some sort of browser.

 Well, if you have the all-in-one-package downloaded it ain't hard to try it out and see if it suits you. I actually like it a lot.


I'm going to attempt this again. I don't think I had code completion or hinting working. Were you able to get debugging working? If those are there, thats all I ask of it. Hopefully from what you know about it, we can get something complete and easy to setup for others to follow.

---

### Post by BenniP on 2008-12-05
to install php-config, you need the package 

php5-dev

---

