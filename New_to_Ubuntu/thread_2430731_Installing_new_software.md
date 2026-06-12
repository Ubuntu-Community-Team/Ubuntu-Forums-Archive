---
title: "Installing new software"
date: 2019-11-06
forum: New to Ubuntu
---

### Post by steag175 on 2019-11-06
Hello everybody,
Long time ago I installed a Linux version but at that tme it toke me to much time and effort getting used to it. I removed it from my system.
Now I wanted to try Ubuntu because some people keep saying it's so much better.
I installed Ubuntu in dual boot aside windows 10.
However, I was so surprised that it takes so much work to install the software I need. 
My question: is it really necessary to type all these commands in the terminal for just installing software? Maybe I'm doiing wrong?
If it's that complicated indeed I need to uninstall Ubanuntu again, just to difficult for me.
Thanks

---

### Post by deadflowr on 2019-11-06
Depends on the software you want/need to install.
A large selection of software is available with just the click of a button through the Software app.

---

### Post by CatKiller on 2019-11-06
A very important lesson to learn is that the way people communicate on a text-based forum, where we wouldn't know which version you're using, or which desktop environment is not the same as when you're using it.

*Here* we're going to give specific commands, and we'll expect the output to be copied-and-pasted, because it's all text-based.

*In use* you'll just poke at the menus the same as you would with any other operating system. When you do that, you'll find the Software Centre. Pick what you want and it will be automatically downloaded and installed, and updated as required.

---

### Post by TheFu on 2019-11-06
Server or desktop?
Which release?
Which GUI  - Desktop Environment?

As for installing software, if you are on a desktop, there are some GUI programs for this.  **Synaptic**, "Software Center", **aptitude**. Check your menus for *Software Center*.  I've never used it, but it is the default in Ubuntu desktops now.
 In these forums, providing instructions is quicker using the shell commands. No need to copy/paste images and waste people's time with GUI instructions.

Software Center is the dumbed down interface into APT, the package management system for Ubuntu.  Sadly, Canonical has decided to push more packages using a different package management system recently, snaps.  There are a few threads here about the pros/cons of snap packages, so I won't go into that, but it is important to know that there isn't just 1 package manager on Ubuntu anymore, at least for now.  Perhaps in 5 yrs, Canonical will step back, see their mistake, and fix it like they did with Unity Desktop.

There is something known as "tab completion" which means we never need to type more than 2-3 characters before auto-complete helps by hitting the {tab} key. This works on both Linux servers and desktops for many commands, options, and files.  It is one of those things that is easy to show, but hard to explain in text.  Check youtube for videos. 

If you learn to use file "globbing" with your commands, lots of typing can be saved where tab-completion doesn't work.  "The art of the command line" - google finds it on Github.  Crazy helpful for saving time and typing.

Linux isn't Windows.  Being efficient in Linux/Ubuntu requires thinking differently. It takes time and it is like learning a foreign language, but when you master the shell/CLI, you'll release the other ~80% of the power that all Unix-based systems have.  Without this knowledge, only ~20% of the power is available.

---

### Post by steag175 on 2019-11-06
Thank you all
Desktop 18.04.3 LTS
GUI? No idea.
Yesterdag installed XAMPP, could run the control panel, openend MySql management etc. Also installed Wordpress to use on localhost. Bitnami installed it on /opt/lampp/htdocs/.
However Wordpress could not be opened in the browser. Later I found out it should be in /var/www/ No idea how to realize this in /var/www/, at least not without dozens of commands in the terminal.
Today I wanted to try again but could not find out again in which folder my xampp installation was and how to start it.
So all this is why I asked: is it that complicated really?

---

### Post by TheFu on 2019-11-06
You should uninstall Ubuntu Server if you expect running a server without a GUI is easy without any training or effort.

OTOH, if you want to learn to run Linux servers, then people here can provide links to resources.  It will take time and effort.  Expect it to be like learning a foreign language on the level of effort.  Again, if you aren't up to that, just uninstall the server and start with baby steps running an Ubuntu Desktop as a desktop for 6 months first.

My best advice: [https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux)

---

### Post by CatKiller on 2019-11-06
> **steag175 said:**
> So all this is why I asked: is it that complicated really?
Installing and running software on Linux is really simple.

Configuring a web server, on the other hand, is *always* going to be done from the command line, whether you're using Linux or Windows: you're not terribly likely to be sat at the actual machine, and you want it isolated from every other process. If you're scared of the command line, configuring a web server is not a task you should undertake.

---

### Post by steag175 on 2019-11-06
I'm just running Apache server as localhost, so not really my own online webserver. In windows I'm doiing it for several years and you really don't need to do it from the commandline.

All I need is an easy way to install xampp (Apache, php and mysql/mariadb) in which I succeeded yesterday but cannot find where to activate xampp again, that's one of my problems with  linux: where is linux storing my stuff? In windows just open the explorer and that's it.

---

### Post by steag175 on 2019-11-06
Thanks, but I did not install Ubuntu server and that's not what I need or want also. Just installing XAMPP and if possible Wordpress. 
I'm also not running my own online webserver, just localhost.

---

### Post by SeijiSensei on 2019-11-06
To install the "[LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP")" stack (Linux, Apache, MySQL, PHP) on Ubuntu you need only run:
```
sudo apt install lamp-server^
```

Both Apache and MySQL will be started automatically and restarted at boot.  There's nothing to activate.

The default web site directory is /var/www/html. However you'll have to learn about [permissions]("https://help.ubuntu.com/community/FilePermissions") before doing much more.  By default, that directory is owned by the "root" or administrative user. To put files there, you'll need to use [sudo]("https://help.ubuntu.com/community/RootSudo") or change the permissions to permit your username to write in that directory.

---

### Post by mastablasta on 2019-11-07
LOL - reading this thread to me is like someone asked how to make a bannana pie and the other one replies on how to make the apple pie. they might be similar but still made slightly differently. maybe.

anyway - to the linux experts - what the OP here is talking about is XAMPP. 

there is a portable program on windows (and apparently on Linux as well)  that installs it all in a single folder you choose at installation. then you run it and it opens a GUI where you can select (click) to run Apache server; MySQL; PHP... once you do that you go to localhost in browser and tada - Apache is there. if you open the port to this interface you can get the server online. but this is actually by default all on local machine. it is ideal for a quick testing. again with GUI you would add "add-ons" (from bitnami stack) such as wordpress for example.  after you are done you turn off the servers with click and that is it. since it is all contained in one folder you can have multiple folders for multiple local servers. it's not really a super secure setup, but it is a good option to easilyl test osmething.

> **steag175 said:**
> Thanks, but I did not install Ubuntu server and that's not what I need or want also. Just installing XAMPP and if possible Wordpress. 
I'm also not running my own online webserver, just localhost.

so what people are advising you is to use the LAMP server provided by Ubuntu. that one runs automatically and also locally. you can disable it's autorun and can then have a command to turn it all off or on. and in this case everything goes into /var/www

this is pretty standard practice over the web. root folder from Apache is in it's configuration files. [https://www.tecmint.com/change-root-directory-of-apache-web-server/](https://www.tecmint.com/change-root-directory-of-apache-web-server/)
so to understand why you need to learn the file structure in Linux. there is a folder where all configuration files are. servers are setup through them or more commonly their .local versions. the reaosn you never met these is because you had local server. had you opened it to the web, you would have to at least harden it first.

i never tried xampp on linux. i did have default LAMP installed for testing. that is until i discovered virtualbox.

to get the wordpress going in virtualbox i would:
1. download the bitnami stack worpress image
2. open disk image and run it

ta da! server running. local host connects to it and there is wordpress waiting there to be configured. 

here is the awesome part - i make a snapshot of the configured wordpress (my theme selected and all that). i can then mess it up completely, destroy it, brick it... all i need is to restore the snapshot and i am back to where i was with wordpress in near pristine condition (on my 15 year old PC this takes about 45 seconds).
Also - l am not a programmer, so sometimes i need help with something from my brother who lives elsewhere. i bridge the network adapter in virtualbox and he can connect to this test server to see what is going on and likely fixes my issue and educates me.


so no, the xampp is not the best option for local server. i am not even sure that virtualbox is. but i do know that virtualbox is better than xampp.

few example vdi image: [https://blogs.oracle.com/oswald/importing-a-vdi-in-virtualbox](https://blogs.oracle.com/oswald/importing-a-vdi-in-virtualbox)
ova that bitnami stack uses: 
[https://docs.oracle.com/cd/E26217_01/E26796/html/qs-import-vm.html](https://docs.oracle.com/cd/E26217_01/E26796/html/qs-import-vm.html)[URL="https://www.maketecheasier.com/import-export-ova-files-in-virtualbox/"]
https://www.maketecheasier.com/import-export-ova-files-in-virtualbox/[/URL]

also Ubutnu (and linux in general) is modular OS. you can add server to desktop or desktop to server. you can mix and match. server apps are light, faster, can run in background, but they do have text configuration files. GUI apps are actually not always needed. Linux helped me to be reminded of that. though i still prefer GUI for desktop use.

also i use windows a lot and got very used to it since their first version. so my go to desktop is KDE found in Kubuntu. though i also like the XFCE a lot and i3 for no nonsense work only windows manager. Mate is also descent. my point is due to modular nature it pays off exploring and finding a GUI you like and feel comfortable with. i for example do not feel too comfortable with Gnome or default Ubuntu interface.

---

### Post by steag175 on 2019-11-07
Thanks, the last answers are very helpful. So I will follow the advice to install lampp. I just didn't know it is there in Ubuntu. I just looked for xampp because I use it on Windows.
Also grateful for the links you gave me.

---

### Post by TheFu on 2019-11-07
Nice communications bridge mastablasta.

The OP asked a generic question initially, so we were answering that.

When  XAMPP was mentioned, I wrongly assumed it was a misspelling of an XMMP chat server [https://en.wikipedia.org/wiki/XMPP](https://en.wikipedia.org/wiki/XMPP)  that is popular.  Guess I have dyslexia.

Bitnami was ignored because I'd never trust pre-built all-in-one packages as a source for anything. I've come across those and found them to be to restrictive with questionable security settings. Call it a bias. I am biased against solutions claiming to make things easier that usually don't.  It is a common thing for people really new to look for shortcuts. I should have realized.  Sorry.

Many coding training classes use these sorts of shortcuts to jumpstart students into coding as quickly as possible. It helps them concentrate on the purpose of the class, skipping over all the critical OS stuff.  Back when I helped run Ruby on Rails classes, we'd have to schedule 3 weeks to help students get their systems setup with a proper environment.  Most of the instructions were for OSX and I'd cover the Linux setup stuff [https://blog.jdpfu.com/2012/07/18/ruby-on-rails-environment-on-ubuntu-12-04](https://blog.jdpfu.com/2012/07/18/ruby-on-rails-environment-on-ubuntu-12-04) ... and then there were the MS-Windows people who had a huge hill to climb for many reasons. Things as simple as case sensitive filenames was the least of the issues.  Most of the MS-Windows people would stop attending after a few weeks.  The huge learning curve and fact that PWD mattered so much was completely foreign to them.
The 4th year, the classes switched to using pre-built environments, 100% web based.  That includes an online IDE.

The solutions that get people up and working quickly are great in the beginning, no doubt about it. Unfortunately, most of the students can't make the jump to setting up a viable environment on a normal Linux server like they would be expected to accomplish in the real world or even on a system at home.  They become so tied to the environment provided, most don't leave it and code in a more general way.  

Definitely begin using the crutches of bitnami (or whatever other environment) make it easy to get started.  But don't stay there too long.  Perhaps in a month or two, be certain to come back around and switch to using the standard way of deploying these environments. 

SeijiSensei does this php stuff for his day job. I'd read his posts carefully. Definitely pay very careful attention to file and directory permissions when setting up webapps.  These are the 1st line of defense against being hacked and lots of php webapps get hacked daily due to improper file permissions.  "Working" isn't enough. They need to be locked down as much as possible.  Over 2M wordpress websites are hacked right now. File permissions.

I do webapp development too, but not with php, rather with perl. Please take that into account for all my posts.

---

### Post by mastablasta on 2019-11-08
yeah, i don't think bitnami and such can be used for anything but the testing. i wouldn't use it live on the open web. server hardening would still be needed and i don't know what services are missing by default. there are much less of them than on standard Ubuntu server image install. this is quite obvious from the size of the image itself.  the images are still good to try and to learn. and i think once you get the basics down, you can learn the rest by diving into the configuration files.

---

