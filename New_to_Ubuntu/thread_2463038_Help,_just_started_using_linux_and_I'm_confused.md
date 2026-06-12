---
title: "Help, just started using linux and I'm confused"
date: 2021-06-01
forum: New to Ubuntu
---

### Post by dakingsella on 2021-06-01
I am trying to download software and can't make it work. I opened Bash ctl+alt+T...that worked. but then tried to change to my download directory. I entered "cd /home", that worked. I entered "ls" to get a list of directories and there is one in the home directory "dakingsella", I expeced that, it would be my user directory. I entered cd "cd /kingsella" and got an error message "bash: cd: /dakingsella: No such file or directory" I think it is a security issue as I think I am logged in as root, if that makes sense.

Here is the complete log:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```
dakingsella@dakingsella-870-241:~$ cd /home/downloads
bash: cd: /home/downloads: No such file or directory
dakingsella@dakingsella-870-241:~$ cd /home
dakingsella@dakingsella-870-241:/home$ ls
dakingsella
dakingsella@dakingsella-870-241:/home$ cd /dakingsella
bash: cd: /dakingsella: No such file or directory
dakingsella@dakingsella-870-241:/home$
```

What am I doing wrong?

Dave

---

### Post by him610 on 2021-06-01
We were all beginners at one time, just as confused and bewildered as you. Hang in there.

Entering *cd* from the terminal will get you into your home directory. 
*pwd* will show your working directory
In your case, it would look like this,  */home/dakingsella-870-241*

Check out the link in my signature.

---

### Post by QIII on 2021-06-01
Hello.

What software are you trying to download?  Typically, you should not be trying to download software.  Most Linux distributions, including Ubuntu, have repositories that make installing software a matter of clicking once or twice.  Downloading random software is unnecessary and extremely dangerous in most cases.

"downloads" does not exist.  It's "Downloads".  Proper casing is required in Linux.

---

### Post by oldfred on 2021-06-01
When in a directory, you do not use the leading / as that is then looking for that folder in / (root), not a lower level from where you are.

Normally when you open a terminal you are at ~ which is a shortcut for /home/$USER

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cd /home [/COLOR]
[COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/home**[/COLOR][COLOR=#000000]$ ll [/COLOR]
total 12 
drwxr-xr-x  3 root root 4096 Oct 14  2020 [COLOR=#5454ff]**.**[/COLOR][COLOR=#000000]/ [/COLOR]
drwxr-xr-x 19 root root 4096 Oct 24  2020 [COLOR=#5454ff]**..**[/COLOR][COLOR=#000000]/ [/COLOR]
lrwxrwxrwx  1 root root   44 Oct 14  2020 [COLOR=#54ffff]**.directory**[/COLOR][COLOR=#000000] -> /etc/kubuntu-default-settings/directory-home [/COLOR]
drwxr-xr-x 18 fred fred 4096 Jun  1 12:24 [COLOR=#5454ff]**fred**[/COLOR][COLOR=#000000]/ [/COLOR]
[COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/home**[/COLOR][COLOR=#000000]$ cd /fred [/COLOR]
bash: cd: /fred: No such file or directory 
[COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/home**[/COLOR][COLOR=#000000]$ cd /home/fred [/COLOR]
[COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ echo $USER [/COLOR]
fred

[/FONT]
```

---

### Post by sofasurfer on 2021-06-02
Capitalize "Downloads"

---

### Post by The Cog on 2021-06-02
Just in case it's not clear from the above posts, the leading "/" makes a big difference. A leading "/" means starting "from the top", and just "cd /" will take you to the top of the tree.

If you don't use a leading "/", then you are naming a directory or file in (or below) your **current** directory.

The directory "/home" contains all the user's individual home directories (except root's), and on your system there is just one: dakingsella.

From anywhere you could change straight to your home directory with "cd /home/dakingsella". Just "cd" without naming a directory will take you home as well, which is a convenience. Also, "~" means your home directory, and this can be used with trailing subdirectory names. So to get to your Downloads folder, you could use any of these:
```

cd   # (takes you to /home/dakingsella)
cd Downloads
---
cd /home/dakingsella/Downloads
---
cd ~/Downloads

```
So it looks to me like the only things you were doing wrong were: 
1) Not realising that the leading / always means "starting from the top", and
2) Not realising that Linux is case sensitive, so "downloads" and "Downloads" are different names.

Incidentally, the leading slash rule applies to Windows too, although on Windows, people mostly tend to use backslash instead (rule still applies). The thing that catches Windows users out for a while is getting used to case sensitivity in Linux.

And I agree that you should probably not be downloading software from the internet at this stage - look in the Ubuntu repositories first. Lots of software is there, and much easier (and safer) to install.
Good luck.

---

### Post by ActionParsnip on 2021-06-02
Linux is incredibly case sensitive. What are you trying to install please?

---

### Post by scorp123 on 2021-06-02
> **dakingsella said:**
>   I entered cd "cd /kingsella" and got an error message "bash: cd: /dakingsella: No such file or directory" 

Slash matters.  You tried to access a directory that does not exist: "/dakingsella"  <== the position of the slash matters!!  The error message is thus correct. 

You should familiarize yourself how the directory structure works here. E.g. **"/"** is the top-most directory that can exist. Think of it as being analoguous to the ***"This Computer"*** location in Windows if you will. Everything else on the system is attached to this "/" location, e.g.

/boot = everything needed to boot the system
/usr = user-accessible binaries
/home = all home directories

So if you access e.g. "/home/dakingsella" then this should work: the subdirectory "dakingsella" is underneath "/home", and "/home" is underneath "/", so the path should be correct.

If you try to access "/dakingsella" then this should not work: There is no such location directly attached underneath "/".  You can check:
```
ls -al /
```

Also: The super-user **"root"** does NOT have "security issues" apart from using it being a serious security issue in itself. **"root"** is simply allowed to do **[COLOR="#B22222"]EVERYTHING[/COLOR]** without being asked stupid questions by the system. **[COLOR="#B22222"]AND THIS IS DANGEROUS.[/COLOR]**  In most cases there will be NO question like *"Are you sure?"* and whatever stupid command you typed in will very likely be executed right away, even if it is destructive.

Therefore please **[COLOR="#B22222"]DO NOT USE "root"[/COLOR]** unless you are 100% required to do so (e.g. because you really are doing administrative tasks that require his powers). Back in 1996 I was given the same warning and I didn't listen. Didn't even take me 1 hour and I hosed my system...  I learned the hard way.

---

### Post by scorp123 on 2021-06-02
> **dakingsella said:**
> I am trying to download software and can't make it work.

Also: **Linux is not Windows**.  We usually don't download software from the Internet. That's totally unsafe and one of the reasons why Windows has all kinds of viruses, malware and what not. Here on Linux we have **Package Repositories** and **Packet Managers** ... so on Linux you practically never ever download any software by hand. At all. You tell your system what software you want and it goes and fetches it from curated, well protected software repositories for you. And taddaaa, you get a new icon and the software you wanted is simply there.

There are a few exceptions to this but if you are a new user and unless you're doing something really really exotic then 99.99% of all software you as a desktop user might ever need is already accessible to you. You just need to tell the **"Software"** app what you want.

---

### Post by hk42 on 2021-06-02
Hi all.I agree with all you said except for :
The OP didn't say the software he was trying to download was for Linux. :-)

---

### Post by dakingsella on 2021-06-02
I have been using XAMPP on windows for my web server. Is XAMPP something that is packaged with Ubuntu? If so, how do I find it?

Thanks

---

### Post by dakingsella on 2021-06-02
The package I am trying to install is XAMPP. It might be in the Ubuntu distro but I haven't found it.

---

### Post by mIk3_08 on 2021-06-02
> **dakingsella said:**
> 

```
dakingsella@dakingsella-870-241:~$ cd /home/downloads
bash: cd: /home/downloads: No such file or directory
dakingsella@dakingsella-870-241:~$ cd /home
dakingsella@dakingsella-870-241:/home$ ls
dakingsella
dakingsella@dakingsella-870-241:/home$ cd /dakingsella
bash: cd: /dakingsella: No such file or directory
dakingsella@dakingsella-870-241:/home$
```


Dave

for me this will work,
it should be;
```

cd '/home/dakingsella/Downloads'

```
Just don't forget to the single quote. from the start of the location folder address and also the the end.
Just try it. It will direct you to your downloads folder
Welcome to the Linux world. Have fun and Good Luck!.

---

### Post by scorp123 on 2021-06-02
> **dakingsella said:**
> I have been using XAMPP on windows for my web server. Is XAMPP something that is packaged with Ubuntu? 

You're not on Windows anymore. This is Linux here. Apache, MariaDB, PHP, PERL all exist as native packages here. So if you want Apache, MySQL / MariaDB and PHP then install those packages. If you still insist you want to install "XAMPP" instead of familiarizing yourself with the proper way of doing this, then you can follow instructions such as this one:
[https://vitux.com/ubuntu-xampp/]("https://vitux.com/ubuntu-xampp/")

Just saying: I wouldn't do it this way. If I want Apache + MariaDB I just install what I need via the package manager. That way I'd also get patches and updates. This local installation via download package will not benefit from that and it's a security breach waiting to happen.

---

### Post by scorp123 on 2021-06-02
Proper way of doing a LAMP stack on Ubuntu:
[https://upcloud.com/community/tutorials/installing-lamp-stack-ubuntu/]("https://upcloud.com/community/tutorials/installing-lamp-stack-ubuntu/")

---

### Post by dakingsella on 2021-06-02
That was the instructions I was trying to follow when I encountered my lack of knowledge of Linux.

---

### Post by dakingsella on 2021-06-02
Thanks for the input! I really would prefer to install each component seperately, but could not find them. I'll go look again.

---

### Post by TheFu on 2021-06-02
> **dakingsella said:**
> Thanks for the input! I really would prefer to install each component seperately, but could not find them. I'll go look again.

All the necessary packages are in the normal Ubuntu Repos.  You don't need to download anything directly.  Use "apt" or "apt-get" or Synaptic to install software.

I don't exactly know what XAMP is, but if it uses nginx instead of Apache, and Perl instead of Php, and MariaDB instead of MySQL then I've been running that setup for over a decade.  There is probably a meta-package (that's a virtual package that includes other packages as dependencies). That meta-package will setup each of the installed parts so they know about each other.  I'm 100% positive that LAMP has this.  The command for linux, apache, mysql, and php to be installed and step is:
```
sudo apt install lamp-server^
```
That trailing carrot is correct.
Setting up something to work is just the first step of many required steps.  A working LAMP server isn't a secured LAMP server.  Lots of security things need to be added.

On Windows, LAMP is called WAMP?

BTW, none of these things is really beginner friendly.  All the configuration is done in a shell, like a programmer would expect. To my knowledge, there isn't any point-n-click solution that can be trusted to setup all this stuff.

Here's the book I used in my beginning Linux classes: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) . There are many others, but all of them will leave huge gaps in knowledge.  After almost 30 yrs, I figure I know only about 10%.

---

### Post by dakingsella on 2021-06-02
Thanks

---

### Post by dakingsella on 2021-06-02
Thanks for the information....very helpful! 

A little about my background, i am a retired technology manager. Came up through the ranks, started as a computer operator in the USAF, have a AAS degree in computer technology, worked as a programmer/system analyst, moved into management.

I have worked in many different environments, IBM mainframe and mid-range computers, client/server environments, etc.

I had a linux server up and running at home for a few years about 15 years ago, but got busy and abandoned it. Have forgot everything I knew about Linux, and Linux has changed a bunch since I was playing with it.

I have been running a LAMP (XAMPP) server on my Windows desktop but that is not ideal so decided to re-purpose one of my old computers as a Linux server. Just getting back into it, and my mind isn't as young as it used to be. XAMPP is a package of Apache, PHP, and MariaDB.

I appreciate your response, 

Dave

---

### Post by The Cog on 2021-06-02
synaptic may help you find packages to install (sudo apt install synaptic). It's much more detailed than that software store thing.
You probably want packages apache2, mariadb-server, mariadb-client, and also some kind of php but I don't know php at all.

---

### Post by ActionParsnip on 2021-06-03
If you want to install each part separately, you can. Just run:
```

sudo apt install mysql

```
To install the M in LAMP.
You can install Apache to get the A in LAMP with 
```

sudo apt install apache2

```
and you can install PHP to get the P from LAMP by running
```

sudo apt install php

```

---

### Post by ActionParsnip on 2021-06-03
As always, Digitalocean do some cracking guides
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04)

---

### Post by rsteinmetz70112 on 2021-06-04
Just a thought -  If you were to install XAMPP (Apache MariaDB, PHP, and Perl) using one of the installation methods outside the repositories you might introduce incompatibilities with the "standard" Ubuntu versions ether at installation or when you update. 
You will also be able to update the Ubuntu versions regularly and be pretty sure they are compatible with each other. 
The Ubuntu LAMP stack (Linux, Apache, MariaDB, PHP) does mostly the same thing and uses the standard versions for that Ubuntu release. You can easily add Perl if you need it.

---

### Post by TheFu on 2021-06-04
Perl is pre-installed on all major versions of Ubuntu.  Many core capabilities in all Linux are dependent on perl.  It is only when we go for extreme minimal linux installs that a perl isn't installed, so perhaps Ubuntu Core wouldn't have it?  Ubuntu Server, and the 10 desktop flavors of Ubuntu all do.  Same for Fedora, Mint, and Debian releases.

If you need a specific version, leave the Ubuntu-installed version alone and use Perlbrew to setup a specific perl version with specific perl modules.  I use perlbrew 20x a month - sometimes more. It is part of my web-app development process.
If you need a specific ruby or python, those also have tools similar to perlbrew for keeping the scripting environments separate and not polluting them in the OS.  
Using these tools is the best practice. Sometimes they are called virtual environments, which can be confusing since they have nothing at all to do with Linux Containers or Virtual Machines or Web Virtual hosts.

I suspect php has a way to do the same, but don't know what it might be. My experience says that php will go with a different program name rather than using environment variables to get the php version and modules we desire.  But that's probably just my ignorance.

---

