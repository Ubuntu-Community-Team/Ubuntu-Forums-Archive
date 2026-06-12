---
title: "How to Remove a User Account"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by davesmith on 2011-11-08
Could someone please explain how to delete a user?

After installing, I went to 'users & groups' and created another  account with non-administrator rights and installed Firefox, VLC and a  printer. For all sorts of reasons I now want to delete this account, but when I'm logged in as the admin and click 'delete user' a box says i dont have permission to  delete it. What gives?

Thanks in advance

---

### Post by matt_symes on 2011-11-08
Hi

Open a terminal and type

```
sudo userdel -r  <user_name>
```

Enter your password. It will not be echoed to the screen. Change <user_name> to the user to delete.

Kind regards

---

### Post by Frogs Hair on 2011-11-08
From the GUI change account settings needs to unlocked by the administrator before making changes .

---

### Post by davesmith on 2011-11-08
Thank you both, the terminal code worked:D:D

What happens to the deleted user's config files, are they still there?

---

### Post by matt_symes on 2011-11-08
Hi

> What happens to the deleted user's config files, are they still there?

From *man userdel*

> -r, --remove
           Files in the users home directory will be removed along with the home directory itself and the users mail spool. Files located in other file systems will have to be searched for and
           deleted manually.

           The mail spool is defined by the MAIL_DIR variable in the login.defs file.


Hope that helps.

Kind regards

---

### Post by davesmith on 2011-11-08
Thanks for the info, may the Ubuntu be with you:KS

Best Wishes

---

### Post by ahmed.cnbd on 2011-11-08
you should mark thread as solved

---

### Post by davesmith on 2011-11-08
ok I will if you could also help me with this....OT i know but there are some knowlegeable ppl on this thread

How to install the <  jre-6u29-linux-i586.bin > file available for Linux on the sunJava  website? The instructions with the file are generic Linux and not  specifically Ubuntu. 

The java available in the natty repos is < jre-6u26-linux-i586.bin > and I sorta like to keep ahead of the game if i can

Thanks in advance

---

### Post by matt_symes on 2011-11-08
Hi

> **davesmith said:**
> ok I will if you could also help me with this....OT i know but there are some knowlegeable ppl on this thread

How to install the <  jre-6u29-linux-i586.bin > file available for Linux on the sunJava  website? The instructions with the file are generic Linux and not  specifically Ubuntu. 

The java available in the natty repos is < jre-6u26-linux-i586.bin > and I sorta like to keep ahead of the game if i can

Thanks in advance

Download it to a directory - say Downloads, make it executable and run it.

Download it to Downloads. 

Open a terminal and type (this will change directory to Downloads)

```
cd ~/Downloads
```To make it executable (Enter password as before)

```
sudo chmod 755 jre-6u29-linux-i586.bin 
```To run it.

```
./jre-6u29-linux-i586.bin
```

or ```
sudo ./jre-6u29-linux-i586.bin
``` if it there are permission problems.

It should then install.

Kind regards

---

### Post by davesmith on 2011-11-08
How do you remove the older versions of java? Their website recommends it

[http://java.com/en/download/faq/remove_olderversions.xml](http://java.com/en/download/faq/remove_olderversions.xml)

Regards

---

### Post by matt_symes on 2011-11-08
Hi

Do you have OpenJDK, Oracle Java or both currently installed ?

OpenJDK is the default installed with Ubuntu so if you haven't installed any other version is it will be that.

The commands to remove it depends on the version you have installed.

Kind regards

---

### Post by davesmith on 2011-11-08
Thanks, is there terminal code that can tell which versions are installed? 

Regards

---

### Post by davesmith on 2011-11-08
Ah, its java version 1.6.0_26 from Sun Microsystems

Regards

---

### Post by matt_symes on 2011-11-08
Hi

```
dpkg -l | grep -E "java|openjdk"
```That is a small L after dpkg; big E after grep.

Post results back here.

Kind regards

---

### Post by matt_symes on 2011-11-08
Hi

Were cross posting :)
> 
Ah, its java version 1.6.0_26 from Sun MicrosystemsYou can uninstall that from the GUI or from the command line

```
sudo apt-get remove --purge sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts
```I'm pretty sure that will remove it but this is from memory so ....

It may be easier to run
[FONT=monospace]
[/FONT]```
sudo apt-get remove --purge sun-java6-*
```

but check what it wants to remove.

You can then install the new version.

Kind regards

---

### Post by davesmith on 2011-11-09
Hi

The removal procedure procedure worked, tnx. But installing the 

< jre-6u29-linux-i586.bin >

file did not go well - the code seemed to work, but the java website says "no java installed" and java apps are not running. What went wrong?

Regards

---

### Post by matt_symes on 2011-11-09
Hi

It sounds like the installation went well. Where did you install it ?

Have you set up the JAVA_HOME environmental variable and updated PATH ?

For the firefox plugin read this

[http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html](http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html)

Any questions post back.

It's getting late here though so it may be tomorrow.

Kind regards

---

### Post by davesmith on 2011-11-10
Hi Matt
 
Everything in the install went well with no problems using the code that you posted above, tnx
 
The .bin file installed itself inside a directory it created in /home/Downloads folder. I dont know how to set up the JAVA_HOME environmental variable and updated PATH (duh) but i'm willing to give it a go if you could post some more code
 
Thanks for all your help, i'm learning lots and lots here
 
Regards

---

### Post by matt_symes on 2011-11-10
[Hi

> 
The .bin file installed itself inside a directory it created in /home/Downloads folder. I dont know how to set up the JAVA_HOME environmental variable and updated PATH (duh) but i'm willing to give it a go if you could post some more code
I did have a quick look at the archive (jre-6u29-linux-i586.bin) last night after downloading it from Oracles' web site.

The archive itself is a self extracting archive. Nothing more and nothing less. This is why it extracted to your ~/Downloads folder. Most people would extract it to /usr or maybe /opt so as not to pollute their home directory.

To do this you may want to move the archive and extract it again. As you have already set it to be executable (the chmod command in a previous post) the you would be looking at.
```

sudo mkdir /usr/lib/jvm
sudo mv ~/Downloads/jre-6u29-linux-i586.bin /usr/lib/jvm/
sudo /usr/lib/jvm/jre-6u29-linux-i586.bin
```These three commands one after another would extract the archive to /usr/lib/jvm/jre1.6.0_29.

To export the JAVA_HOME and PATH variable you need to edit your file /etc/environment. Run these commands. (it is case-sensitive so use capital letters where i have).

```
sudo bash -c "echo JAVA_HOME=/usr/lib/jvm/jre1.6.0_29 >> /etc/environment"
``````
sudo bash -c "echo PATH=$PATH:JAVA_HOME/bin >> /etc/environment"
```You would then have to recreate the symlink for Firefox as highlighted in that Oracle document.

As this is the only version of Java you have then you do not have to worry about updating any alternative symlinks. You may want to check with

```
sudo update-alternatives --config java
```It should return an error.

Hopefully that will get you up and running. It's been a good while since i installed Java from a bin file so i may have missed something.

If you want to keep Java in your download directory then change the paths as required.

You will need to reboot for the settings to take effect.

> 
Thanks for all your help, i'm learning lots and lots here
Your welcome :)

If it have missed something then someone will point it out or i will set up Java correctly on my machine and tell you the steps i took.

Kind regards

---

### Post by davesmith on 2011-11-10
Hi Matt
 
I'm in the UK too, so i'll try to set up these symbolic links when I get home from work tonight. My guess is that creating the symlink to Firefox will be the issue to overcome. 
 
BTW i upgraded Firefox to ver 8.0 yesterday so this is a good time to master the intricacies of installing self-extracting .bin programs:) Any problems and i'll post them.
 
Thanks again
 
Regards

---

### Post by matt_symes on 2011-11-10
Hi

Please reread my last post as i removed a typo in one of the commands.

Kind regards

---

