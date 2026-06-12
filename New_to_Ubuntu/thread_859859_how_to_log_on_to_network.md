---
title: "how to log on to network??"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Chetanji on 2008-07-15
Hello to all!,
I just installed Ubuntu 8.04 on a new Dell laptop with most devices working right out of the box.  Very nice!

first problem:
I go  to places> network and see all the window shares on the corporate network (wired, manual config).
I am not given a logon screen for the folders I normally logon to.
I am using  gnome and am quite new to Ubuntu.

second problem:
Am not allowed to logon as root from boot. As I need to set up a project the permissions problem need to be rectified.
Can't I just relax everything until I set up Java, Eclipse, project etc. then turn the police back on?
I can download off Web only into the desktop, not anywhere else.

Thanks for your help,:)
Chetanji

---

### Post by Chetanji on 2008-07-15
Hello again,
I just looked in the network forum and found almost the same exact post as mine but without an answer that worked.

I can see all the machines and log on to some but not able to log on to all.

I just reboot into windows xp and can log in to all all network folders.  The gunbuntu sees all the folders.
This has got to have an answer

I have web access just can't download where I want to on my laptop

I really want/need to get Ubuntu working.

Thanks for your help,
Chetanji:)

---

### Post by iaculallad on 2008-07-15
> **Chetanji said:**
> Hello to all!,
I just installed Ubuntu 8.04 on a new Dell laptop with most devices working right out of the box.  Very nice!

first problem:
I go  to places> network and see all the window shares on the corporate network (wired, manual config).
I am not given a logon screen for the folders I normally logon to.
I am using  gnome and am quite new to Ubuntu.

First Problem: Normally, you are prompted for login/password screen when accessing secured Shared folders from windoze, either domain shared or local shared only.

OR

Had you login before and checked the option for Ubuntu to remember the password for that Shared folder forever?


> **Chetanji said:**
> second problem:
Am not allowed to logon as root from boot. As I need to set up a project the permissions problem need to be rectified.
Can't I just relax everything until I set up Java, Eclipse, project etc. then turn the police back on?
I can download off Web only into the desktop, not anywhere else.

Thanks for your help,:)
Chetanji

The ROOT account is disabled by Default for security reason. To manually enable it, navigate to System->Administration->Users and Groups, select the Root Account, click on Properties and set the password by hand.

---

### Post by Chetanji on 2008-07-15
> **iaculallad said:**
> First Problem: Normally, you are prompted for login/password screen when accessing secured Shared folders from windoze, either domain shared or local shared only.

OR

Had you login before and checked the option for Ubuntu to remember the password for that Shared folder forever?

On the regular folder I use on our rather large network at the job I do not receive the login window.  If I try it in Windoze XP the network folder opens automatically because the user and password are saved earlier.

In ubuntu i double click and nothing happens in this same folder.
However on some other folders I get the login screen.
This irratic behavior is strange.


> **iaculallad said:**
> 
The ROOT account is disabled by Default for security reason. To manually enable it, navigate to System->Administration->Users and Groups, select the Root Account, click on Properties and set the password by hand.

I did like you said and on bootup I am still given the error upon typing username:root & password:xxxxxxxxx
"The system administrator is not allowed to login from this screen"

Also, I in System>Administration>Users and Groups
I click into users settings>groups settings>group 'root' Properties and check the two boxes in the 'Group Members' window (my user name and 'root')
I did the same for my user name properties (checked both boxes for 'root' and username)
Still very strict system, not allowing me to setup work.

Thanks
Chetanji

Blessings,
Chetanji

---

### Post by appi2012 on 2008-07-15
You really shouldn't need to use the root account. just type:
```
sudo
```
before launching commands in the command line, and.
```
gksudo [app]
```
to run gui apps as root.
its much safer than a root account.

---

### Post by Chetanji on 2008-07-16
[QUOTE=appi2012]You really shouldn't need to use the root account.[/QUOTE]
Correct me if I am wrong...
I thought the root account was for administrative duties like setup of projects, installing new software; all of this off the web or network.
Then...Later (especially on the network and especially on the web)
we live in our user layer for safety, etc.

I am in the new Linux install phase and have installed/deinstalled two other excellent Linux OS's in the last month, because they did not support my needs, as this is a work related project, not pleasure.
Like I mentioned earlier I am behind, and running out of time and need to setup a project in eclipse with a number of tools that must be compiled with C++ and perl scripts for training, etc.
Forgive my ignorance, for Linux was last used a year ago and I'm still on the nipple with training wheels on my two wheeler.
Blessings,
Chetanji:)

---

### Post by tramir on 2008-07-16
You are absolutely right that the root account is needed to install software and perform admin tasks. But you should not log in as root, because that means you allow yourself, and presumably anybody who would gain access to your computer, do anything. For this reason, ubuntu disables the root account and allows regular users to **temporarily** run applications as a "superuser". So, for instance, when you want to install a program via Synaptic, you're asked for your password because you temporarily switch to a superuser, meaning that **only Synaptic** is run as a superuser and has the right to write in certain folders etc.

Long story short: you can do everything you need to do from your own account - when you need the permissions of root, just use "sudo" in front of the command, like it was suggested above. Logging in as root is really really not recommended.

As for the Windows share problem - on which I'm much less knowledgeable: sometime linux has problems getting to Windows share by name. If you know the IP address of the network share, try to type it directly into Nautilus, in the location bar, and see if that works. Good luck.

---

### Post by Chetanji on 2008-07-16
Thanks tramir,
I will use the command line instead of the GUI and sudo correctly.

Here is the problem in a nutshell...
I am attempting to download a file into a folder other than desktop with firefox and down_them_all.
I am not allowed to, there is no prompt for user password, etc.
simply the app does not move any further, clearly the process fails here as well as other places.

It appears Ubuntu is too involved with Windoze and thus has blended a little too far into the unknowingness.
I miss the old, old daze of log in as root do your correct work in the correct way at the correct time, then log out and plug the cables in.

So I am not going to be able to use firefox for downloading needed files.

And I am not going to be able to use the GUI for moving files either.

It seems like a bit of a disappointment.

Right now I don't have the time to download and try another OS.
Fedora Core 9 did not have Graphic support for this laptop
OpenSUSE 10.4 could not connect to web or network easily and had other problems.
Ubuntu installs fine, sees most all devices and configures nicely but over manages my security. Hmm, where is the blessed middle ground?

Blessings,
Chetanji:)

---

### Post by appi2012 on 2008-07-16
press alt+F2 and type:
```
gksudo firefox
```
and then try downloading the file.

or, download it to your desktop, and then run:
```
gksudo nautilus
```
then you can move the file through nautilus.

you don't have to use command line

---

### Post by halitech on 2008-07-16
because of the way the security is set up, you can only save files in your home folder (IE /home and any folders in your home folder). you should be able to select a different location to save them and then use the gksudo nautilus to move them where they need to be outside your home folder.

---

### Post by jimv on 2008-07-16
For Pete's sake, someone just tell the man what he wants to know instead of try to show how smart and great you are with your security lectures.

Here's how to enable ROOT login:

Go to System>Administration>Login Window 
Click on the Security tab 
Check the box that says "Allow local system administrator login"
Close the control panel

Now you should be able to login as root with the password that you set earlier.

---

### Post by tramir on 2008-07-16
I think it's better, rather than explaining how to enable the root user and mess up his setup, to explain how the linux filesystem works.

As a normal user, you have the right to write only in your "home" folder, which is /home/your_user_name. That's also where your "desktop" is located. So, if you want to save stuff from Firefox using Down-them-all, just choose a folder in your home folder. Then you won't have any permission problems. For example, I have a folder called "MyDownloads" inside my home folder and I set up Firefox to automatically download stuff there. Like this, it doesn't clutter my desktop and I don't have any permission issues. Also, there's usually no need for you to copy files in places other than your home folder.

Hope this makes sense, it's a little bit different than the way Windows is organized.

---

### Post by AndrewEsther on 2008-07-16
jimv, I think you're the first person I've seen anywhere in this forum that advocates telling people how to login as root. I thought users were encouraged to use sudo/gksudo except for very high-level, complicated procedures which are outside the scope of many everyday users...?

---

### Post by Chetanji on 2008-07-17
> **jimv said:**
> Now you should be able to login as root with the password that you set earlier.

JimV, I greatly appreciate your help and knowingness in telling me.

This laptop will rarely be connected to the web after setup.
It is for a project in developing a large database involving a java based speech recognition system that is in development stages still.
So I need a C++ compiler, a Perl script environment, Eclipse IDE, with Java runtime SDK, Wave recording and editing, many tools being used with a tremendous amount of data being moved to and from different folders, etc. 

I think I made my point.
I am older now and getting back into linux with more important things in my life taking priority over computers.
I want to thank everyone for their help and for taking the time to write in my sad thread is greatly appreciated.  Thanks to all.
I am sure with all your help I will get to the bottom of these small problems.  It is also cool to see your interaction.
Linux people are so much more cool headed, as opposed to the typical windoze people.  

Blessings,
Chetanji:)

---

### Post by Chetanji on 2008-07-17
> **tramir said:**
> I think it's better, rather than explaining how to enable the root user and mess up his setup, to explain how the linux filesystem works.

As a normal user, you have the right to write only in your "home" folder, which is /home/your_user_name. That's also where your "desktop" is located. So, if you want to save stuff from Firefox using Down-them-all, just choose a folder in your home folder. Then you won't have any permission problems.

Except I want to download into the directory where it will be used.
I don't need my hand held. I started programming when there was no such thing in memory as a 'word'.  We were in the '8 bit data types' then.  64 bit data was no more than a dream.

I understand what Ubuntu is doing.  This is too much like kindergarden for Linux.  Although it is very safe.
I guess programmers dig under or unlock the gate of their fences rather than play peacefully within the confines of.

Respectfully Chetanji:)

---

### Post by cariboo on 2008-07-17
Just a word of caution, don't install the programs you need from outside sources, as every time an update comes out you will have to reinstall your programs again. Everything you want is available in the repositories, and it is quicker and easier to install the programs using Synaptic Package Manager. I have worked with a couple of senior programers, and sometimes they get so focused on the project, they forget about the supporting details.

Jim

---

### Post by jimv on 2008-07-17
> **AndrewEsther said:**
> jimv, I think you're the first person I've seen anywhere in this forum that advocates telling people how to login as root. I thought users were encouraged to use sudo/gksudo except for very high-level, complicated procedures which are outside the scope of many everyday users...?

I'm not advocating anything.  But Chetanji asked a specific question, and no one was giving him the answer.  He doesn't sound like a computer novice who needs everyone telling him not to do what he's trying to do.

Not everyone who uses Ubuntu needs security pampered.

---

