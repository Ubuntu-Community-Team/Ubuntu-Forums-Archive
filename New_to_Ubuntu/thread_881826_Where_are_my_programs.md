---
title: "Where are my programs?????"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by photoman64 on 2008-08-06
I spend 2 days to download and install a programs trough Synaptic. Half of them do not show in menu.  I have no need for OS if I have to waiste a time and can not use a programs that I downloaded.
Any program that will scan my HD and put them in menu???

---

### Post by tuxxy on 2008-08-06
system > prefs > main menu click on add then add any programs you need to the main menu, to run the program enter its name for example to run firefox the command would be firefox

---

### Post by maybeway36 on 2008-08-06
What programs did you download? Some/most of them you can launch through the terminal if you need to.

---

### Post by hvac3901 on 2008-08-06
Well I don't think my way is the best way, but i go to /usr/bin and find the program to get the launcher builder info and build my launcher from that.

---

### Post by hvac3901 on 2008-08-06
> **maybeway36 said:**
> What programs did you download? Some/most of them you can launch through the terminal if you need to.

Some of them ONLY run in the terminal, as another key point.

---

### Post by photoman64 on 2008-08-06
I was able to find a Wine and finally show-up in menu.
I found out that just typing in Synaptic root password does not mean anything.A lot of programs can be installed only as root.
Why the Synaptic asking me for my root passwork and after that still refuse to install some programs. Many of those programs are gui and should show in menu in the first time.
Something wrong with Ubuntu.

---

### Post by perlluver on 2008-08-06
> **photoman64 said:**
> I was able to find a Wine and finally show-up in menu.
I found out that just typing in Synaptic root password does not mean anything.A lot of programs can be installed only as root.
Why the Synaptic asking me for my root passwork and after that still refuse to install some programs. Many of those programs are gui and should show in menu in the first time.
Something wrong with Ubuntu.

Log out and back in.  That will fix it most of the time.

---

### Post by ByteJuggler on 2008-08-06
> **photoman64 said:**
> I was able to find a Wine and finally show-up in menu.
I found out that just typing in Synaptic root password does not mean anything.A lot of programs can be installed only as root.
Why the Synaptic asking me for my root passwork and after that still refuse to install some programs. Many of those programs are gui and should show in menu in the first time.
Something wrong with Ubuntu.

Synaptic does **not** ask you for your **root** password.  It asks you for ***your* password.**  You **should _not _have a root password on Ubuntu**, the account should be totally locked.  What exactly were you trying to install?  We can better help you with more information on exactly what you're trying to do.

---

### Post by gioland71 on 2008-08-06
Synaptic asks for the sudo password to ensure you know what you're doing. Then it lets you download and install programs.
Programs that require superuser authorization to run will ask you for your sudo password before running - each and every time. Just to make sure that you know what you're doing.
Ubuntu is completely configurable, that means the OS won't add things to your display unless you say so, as a form of respect for the user. To add programs to the menu, click on system-> preferences->main menu.

Bashing on the OS won't make people sympathetic to your case. I like to help  people who are nice and appreciate the effort the community is making to support them - remember, nobody is paying me to help you.

---

### Post by ace007 on 2008-08-06
> **photoman64 said:**
> Something wrong with Ubuntu.

Something **_IS_** wrong.  Ubuntu is not Windows, thats what's wrong.

Syanptic is not refusing to install programs.  
First off, you should know what you are installing.  If you just install something and think 100% of the time it'll magically appear you are mistaken and should not be using synaptic directly unless you have a better understanding.  The majority of the packages in synaptic do not have a graphical display as they are often just functions.  This is why they do not appear in the menu, because there is nothing to appear!  

Secondly, some patience and calmness will get you a lot further in life.

Use the Add/Remove application under "Applications>Add/Remove" to install programs that will all have graphical displays and will definitely appear under the main menu.

---

### Post by cgkades on 2008-08-06
Unfortunately some new users to Linux fail to realize that Linux is fundamentally different from windows. It requires a different mentality. You cannot just expect it to work perfectly all the time (though these days it works pretty darn well). Linux is for users who aren't afraid to use something new, something different, and something that you need to build a foundation of understanding in order to use.  Linux is free. You did not pay for your operating system, you did not pay for the support you are receiving here. If you relax, and use the live CD for a bit, read the forums, and learn a little about Linux and how it works, your frustrations will gradually decrease.  I am now running Linux on 3 out of 4 computers, and one of them is a laptop that I use for school. It has taken me a little while to gain the understanding needed to fully switch over. And the only reason I still have a windows box is because my wife needs some apps for her classes.  If you don't feel you have the time or energy to learn the system, keep windows and either dual boot, or use the live CD.

Oh and use the Add/Remove programs in the application menu. You will find that 99% of those will be added to their appropriate Applications folders.  The only ones that don't get added are usually command line only.

---

### Post by photoman64 on 2008-08-06
I apologize as I got frustrated with the programs. I figure out that the installed programs I will be able to access from menu.
I did had installed pclinuxos and all programs I downloaded did show in menu, but had to quit as the sound did not work and wireless refuse to co-operate too. I spend few days trying to make it working and give-up. Switch to Ubuntu 8.4 and the sound worked "out of the box" and wireless work too( had to install some programs and drivers).My ATI works very good. I fugure out somwe of those programs( what I can see) and add root password( do not have one by defoult) and log as root. I was able to install some of them, but only few show up in menu.
I am trying to learn about computer security and downloaded AIDA, but nowhere in menu. Official website show GUI for that program.

---

### Post by cgkades on 2008-08-06
You should never need to login as root. Issue the command "sudo" before the command you need to run as root. If you run the add/remove program, it will add to the GUI. As for your wireless card, it "should" work. You may need to configure it and tweak it a little. I would first search the forum for threads from others with similar problems, and if you cannot find anything, you could post a new thread that just deals with that issue. I'm sure you will be able to get it resolved.

---

### Post by gioland71 on 2008-08-06
If you add programs as root, you run into permission problems - that is, the programs won't run unless you stay as root all the time. To install new programs all you need it to be "superuser", just your usual log in name, but with root super-powers for about 20 minutes...:)

EDIT: you seem to have a new install. What a great chance to play and learn you have! If you really break it so much you can't do anything, just reinstall everything!

---

### Post by cariboo on 2008-08-06
Seeing as you have created a root password, if you login as root at the login screen you will probably see the programs you installed in the desktop menu. THat is one of the reason Ubuntu disbles root login, especially for newbies, so that they don't run into these problems.

Jim

---

### Post by ugm6hr on 2008-08-06
> **photoman64 said:**
> I am trying to learn about computer security and downloaded AIDA, but nowhere in menu. Official website show GUI for that program.

AIDA is not in the Ubuntu repository.

Where did you find it?

I think you need to do a bit of reading about sudo before continuing to use Ubuntu too.  Try some of the links in the Start here link below...

---

### Post by tuxxy on 2008-08-06
[https://help.ubuntu.com/](https://help.ubuntu.com/)

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

---

### Post by photoman64 on 2008-08-06
I have a wireless working.Comming from windows - we all are accustom to a menu and not a command line. I use a command line in DOS years back. Going back to command line it is like "stepping back in time". I learn about new software by experimenting with.
Just run and see what the software can do. In last few days I learned a lot about various software. It is a chance that someone will mark a package as GUI or command line. That way I will not waste a time to download a package.I had to use a commands to install driver for wireless and that was a "hard work".
That marking - gui or command- will help some other people too.
From what I read in forum - I am not the only one with "missing" applications.
Thank you all for response. I use the root as I want to learn all about the Linux. I do not like a restrictions. If I mess up - no big deal - just reinstall. I am experienced user in windows and still remeber some dos. 
Putting restrictions in programs it is like running a demo - never learn the full potential.
Thanks

---

### Post by ByteJuggler on 2008-08-06
> **photoman64 said:**
> ... and add root password( do not have one by defoult) and log as root....

Stop right there.  You are not supposed to unlock the root account in ubuntu.  It's not neccesary.  Read [this]("https://help.ubuntu.com/community/RootSudo").

Execute the following command from a terminal to lock your root password again:

```
sudo passwd -l root
```

---

### Post by ByteJuggler on 2008-08-06
> **photoman64 said:**
> I use the root as I want to learn all about the Linux. I do not like a restrictions. 

We also don't like restrictions.  But we do like good seucurity and good advice, which is what we're giving you. In any case, just because you don't log on conventionally into the root account does not mean you don't use it or it does not exist, so not logging into it int he normal way is arguably not a restriction, as you put it.  Using "sudo" allows you to run applications as root and e.g. "sudo -i" will give you a root shell, all the while keeping the root account locked and thus protecting you from a common hack/attack vector.

---

### Post by ugm6hr on 2008-08-07
> **photoman64 said:**
> I learn about new software by experimenting with. Just run and see what the software can do. In last few days I learned a lot about various software. 
That marking - gui or command- will help some other people too.
From what I read in forum - I am not the only one with "missing" applications.
Thank you all for response. I use the root as I want to learn all about the Linux. I do not like a restrictions. If I mess up - no big deal - just reinstall.

Some suggestions / responses:

Most people install software they have heard of / want to use.  The Linux repository allows access to loads more applications than you will ever need.  You do not need to know how to use all of them.  If you are looking for specific software to do something - ask here, or try something like osalt.com for a list.  Nevertheless, you can assume that any application that doesn't mention a GUI is a Terminal command application.

Missing applications can be found.  Remember some appear in the System Menu.  If nowhere to be found, just add (or select) it in System-> Preferences-> Main Menu.  Applications are (almost without exception) installed at /usr/bin/application_name (similar to C:\Programs).

If you want to learn everything about Linux, experimentation is fine.  I'd also suggest you actually do a little reading though, especially when you ask for help here, and are advised to do it.  It is apparent you do not understand the rationale for sudo.

---

