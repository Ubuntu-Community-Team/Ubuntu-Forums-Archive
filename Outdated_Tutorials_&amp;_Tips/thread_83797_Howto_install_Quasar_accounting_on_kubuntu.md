---
title: "Howto install Quasar accounting on kubuntu"
date: 2005-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2005-10-29
Hi,
   First of all this howto is not my own work, it was published by Brian Walker and I have just changed a few items to make it work on Breezy Kubuntu. I still need to find out how my windows PC can use the Quasar server on the kubuntu pc. If anyone has this working please let me know and I will update the howto. Please let me have any feedback to update as well.

**_How to install Quasar Accounting on Kubuntu _**
Compliments to Brian Walker

Quasar is an accounting software for Linux and may even be one of the better types currently available for linux. Its GPL and free to use, modify or even sell! It's powerful and easy to use and a full range of support packages are available from the authors. It needs a Linux server, but clients are available for both Windows and Linux. 

Unfortunately, Quasar's not straightforward to install on kubuntu, as no pre-built packages are available. The packages are thus built from source. 

The compiling of the packages can take a while and allow yourself a couple of hours before sitting down with this. I suggest also printing out the Installation and Setup manual in case you would like to know exactly what you are doing! It may help if you stumble somewhere and is very clear. We are using Postgresql as a database as we could not get Firebird to work on earlier versions of ubuntu and Sybase is a commercial program.

Install and build Quasar
First, go to, [ftp://ftp.software.ibm.com/software/globalization/icu/3.4/icu-3.4.tgz](ftp://ftp.software.ibm.com/software/globalization/icu/3.4/icu-3.4.tgz) and download the file icu-3.4.tgz to your desktop.

Next, go to [www.linuxcanada.com](www.linuxcanada.com), and download the file quasar-1.4.7_GPL.tgz to your desktop or the latest version if they have updated. While you're there, also download the comprehensive and excellent product documentation provided by Linux Canada.

Ensure that your repositories are enabled and use Adept or Synaptic to install the following:
build-essential, libqt3-mt-dev ,autoconf, tcl8.4-dev, tk8.4-dev, postgresql-7.4, postgresql-dev and qt3-apps-dev 
Stop all applications that are running to be on the safe side.
Right click on your desktop and create a new directory called quasar
Move or copy the downloaded files quasar-1.4.7_GPL.tgz and icu-3.4.tgz to the new directory quasar
Now go to the new folder and right click on icu-3.4.tgz and extract to here
Also right click on quasar-1.4.7_GPL.tgz and extract to here.
The next steps will take quite a while until finished while the compiling is done:
cd   /home/<username>/Desktop/quasar/icu
./configure
make
sudo make install
sudo cp /usr/local/lib/icu* /usr/lib/
sudo cp /usr/local/lib/libicu* /usr/lib/
cd   /home/<usename>/Desktop/quasar/quasar-1.4.7_GPL
./configure
make
sudo make install

Creating your menu icons
Open Kmenu Editor (right click on Menu button) and create entries for Quasar Server start, Quasar and Quasar Admin in the Office menu.

Quasar Server Startup: (or do with a script when PC starts)
Command: gksudo /opt/quasar/bin/quasard
Icon: /opt/quasar/setup/quasar_setup.xpm

Quasar Admin:
Command: gksudo /opt/quasar/bin/quasar_setup
Icon: /opt/quasar/setup/quasar_setp.xpm

Quasar
Command: /opt/quasar/bin/quasar
Icon: /opt/quasar/setup/quasar_client.xpm

Set up the PostgreSQL database

sudo  -s  -u postgres             (make yourself the postgres user)
createuser  -d  -E  -P  quasar_dba      (give a dba password i.e. Thebear)
createuser   -E  -P  quasar                  (give a non dba password here i.e. Teddy)
exit
Edit the /var/lib/postgresql/7.4/main/pg_hba.conf file with konquerer, right click, actions, edit as root or use sudo kwrite or krusader in root mode to edit.

Add the second row, it allows all your lan pc's with ip 192.168.0.x to access quasar:

host all all 127.0.0.1 255.255.255.255 md5
host all all 192.168.0.0 255.255.255.0 md5
Also edit the /var/lib/postgresql/7.4/main/postgresql.conf and change the line with #tcpip_socket = false to tcpip_socket = true
Now restart postgresql:
sudo   /etc/init.d/postgresql restart
Set up Quasar with the PostgreSQL server
Click Quasar Admin icon to setup.

Go to the Drivers Tab, and click Configure. Enter these settings.
Hostname: localhost
Port: 5,432
Library: /usr/lib/libpq.so.3.1
DBA username: quasar_dba
DBA password: whatever you entered earlier (i.e. Thebear)
Username: quasar
Username password: whatever you entered earlier (i.e. Teddy)
Character set: UNICODE

If all this works, set up a client in windows by downloading and installing the Windows exe file. The windows and Kubuntu PC’s should now be able to use the program and you can set up the printer via Samba if required.
;)

---

### Post by derrick1985 on 2005-11-01
Ok, I have it installed (btw, thank you for this tutorial, I was trying on my own to get it installed with no luck, don't know much about databases)

Anyways, when I start up quasar, it finds the company database but I can't login to it. It asks for a username/password.

help!

---

### Post by Matchless on 2005-11-04
[QUOTE=derrick1985]Ok, I have it installed (btw, thank you for this tutorial, I was trying on my own to get it installed with no luck, don't know much about databases)

Anyways, when I start up quasar, it finds the company database but I can't login to it. It asks for a username/password.

help![/QUOTE]
Derrick,
         The default username as well as password are both "admin".

---

### Post by derrick1985 on 2005-11-04
[QUOTE=Matchless]Derrick,
         The default username as well as password are both "admin".[/QUOTE]
Thanks!

Now, If I could only figure out how to work this thing, i'd be set.

---

### Post by foxy123 on 2005-12-27
I've got a following error after 'sudo make install' in quasar:
```
./install: line 152: /etc/init.d/inetd: No such file or directory

```

I've checked and I do not have this inetd script. What is it?

EDIT: You might want to add netkit-inetd to your dependencies list. I did not have it on my system.

---

### Post by jmvbxx on 2006-03-13
First of all, thanks for the great instructions!

I've been using Ubuntu for almost a year now and have never been able to get Quasar to run.  Now, thanks to your post, I am closer than I've ever been.

So, I've followed all of your intructions but I can get the Quasar server to run.

Here is my error msg:
[I]
Error: Failed binding QSocketDevice
Error: Can't start server[/I]

Also, I have added netkit-inetd.

Thanks again!  Any help is greatly appreciated!

---

### Post by foxy123 on 2006-03-13
[QUOTE=jmvbxx]First of all, thanks for the great instructions!

I've been using Ubuntu for almost a year now and have never been able to get Quasar to run.  Now, thanks to your post, I am closer than I've ever been.

So, I've followed all of your intructions but I can get the Quasar server to run.

Here is my error msg:
[I]
Error: Failed binding QSocketDevice
Error: Can't start server[/I]

Also, I have added netkit-inetd.

Thanks again!  Any help is greatly appreciated![/QUOTE]


it looks like a generic error to me. I mean this thing about QSocketDevice is harmless as I remember. You should have a quasar log file in your /var/log. Is this what it says? Another good place is quasar wiki page (I do not remember where it is but I guess it should be easy to find. It has a troubleshooting instructions from Brad. Try to find it, because it helped me.

I did manage to make quasar work under Ubuntu and it ran very smoothly. Though I decided not to use it so I cannot be much of help.

---

### Post by jmvbxx on 2006-03-13
Thanks for the log location.  Here is the error msg in the log file:

*2006-03-13 11:13:11 Warning: Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentification failed*

I rechecked all my passwords and made sure Postgresql is running.

---

### Post by dmarquard on 2006-03-18
What if I do not have any drivers listed in the setup screen after installation of quasar? I have postres 8.1 installed and running.

---

### Post by LordMerlin on 2006-03-21
The topic says it's for Kubuntu. Let's say I installed Ubuntu as a server, without Gnome / KDE, will this still work for me?

---

### Post by foxy123 on 2006-03-21
[QUOTE=LordMerlin]The topic says it's for Kubuntu. Let's say I installed Ubuntu as a server, without Gnome / KDE, will this still work for me?[/QUOTE]
it should work if you meet all dependencies. I had it running on Ubuntu.

---

### Post by BrownieMan on 2006-04-06
[QUOTE=Matchless]
Now restart postgresql:
sudo   /etc/init.d/postgresql restart
[/QUOTE]

When I had to used the restart command it didn't work. I found that I didn't have a file called "postgresql" I had one with a version number at the end, so for some of you out there you might need ot go into that directory and see what version number it was, mine was "-8.1". Hope this helps someone in the future.

---

### Post by drfox on 2006-05-10
I got this error when I was ./configuring the quasar file

checking for tk.h include... no
configure: error: missing tk.h include file

Then, when I tried to make, I got this

make: *** No targets specified and no makefile found.  Stop.

What do you suggest?

Larry

---

### Post by derrick1985 on 2006-05-10
Well, if you were like me and finally got p'eed off at the fact that compiling by source didn't allow you to print the invoices off, I used the precomiled RPM's for Mandrake and used alien to convert/install them. OF course now I mainly use PCLinuxOS that is based of Mandrake, this should also work through alien though too.

[ftp://ftp.linuxcanada.com/pub/Quasar/1.4.7/binaries/Mandrake/9.2](ftp://ftp.linuxcanada.com/pub/Quasar/1.4.7/binaries/Mandrake/9.2)

Just instead of doing the compile from source stuff, use alien -i *.rpm to install the two packages. Server and Client (the GPL ones). And as for the packages to install, just make sure you have the non -dev packages and you will be ok. (instead of tcl-8.4-dev, just tcl-8.4). Also there is the libicu rpm available, no need to compile that either.

Good luck, tell me how it goes.

---

### Post by drfox on 2006-05-11
Thanks, Derrick. I am sloooooowly getting there. The rpm's installed perfectly. 
I'm trying to run the setup, and I'm getting some error messages trying to add a new company, so, before I get ask questions and maybe get flamed, I'll RTFM. 

Two quick questions, though: 
Which database should I use (and why?): Firebird or PostgreSQL?
What do you do for payroll?

Larry

---

### Post by derrick1985 on 2006-05-12
[QUOTE=drfox]Thanks, Derrick. I am sloooooowly getting there. The rpm's installed perfectly. 
I'm trying to run the setup, and I'm getting some error messages trying to add a new company, so, before I get ask questions and maybe get flamed, I'll RTFM. 

Two quick questions, though: 
Which database should I use (and why?): Firebird or PostgreSQL?
What do you do for payroll?

Larry[/QUOTE]

Well, personally i have been using postgresql since it was explained how to set it up properly in this post. If i'm not mistaken, Postgresql is a more open source form of database, althought I could be wrong. 

And as for payroll, i'll have to look more into that one. I don't usually do payroll as right now, i'm the only employee :D 

Tell me how it goes.

---

### Post by mjs355 on 2006-11-10
I am trying to install Quasar on Ubuntu. When I try to run 'sudo make install', I get the following error message:


make[1]: Leaving directory `/home/malcowee/Desktop/quasar/quasar-1.4.7_GPL/model_editor'
cd postgresql_driver && make -f Makefile
make[1]: Entering directory `/home/malcowee/Desktop/quasar/quasar-1.4.7_GPL/postgresql_driver'
make[1]: Nothing to be done for `first'.
make[1]: Leaving directory `/home/malcowee/Desktop/quasar/quasar-1.4.7_GPL/postgresql_driver'
./install all
./install: 57: Syntax error: "(" unexpected
make: *** [install] Error 2

Any suggestions?  Also, where do I find Brian Walker's original instructions? thanks

---

### Post by robertrej on 2006-12-29
> **Matchless said:**
> Hi,
   First of all this howto is not my own work, it was published by Brian Walker and I have just changed a few items to make it work on Breezy Kubuntu. I still need to find out how my windows PC can use the Quasar server on the kubuntu pc. If anyone has this working please let me know and I will update the howto. Please let me have any feedback to update as well.

**_How to install Quasar Accounting on Kubuntu _**
Compliments to Brian Walker

Quasar is an accounting software for Linux and may even be one of the better types currently available for linux. Its GPL and free to use, modify or even sell! It's powerful and easy to use and a full range of support packages are available from the authors. It needs a Linux server, but clients are available for both Windows and Linux. 

Unfortunately, Quasar's not straightforward to install on kubuntu, as no pre-built packages are available. The packages are thus built from source. 

The compiling of the packages can take a while and allow yourself a couple of hours before sitting down with this. I suggest also printing out the Installation and Setup manual in case you would like to know exactly what you are doing! It may help if you stumble somewhere and is very clear. We are using Postgresql as a database as we could not get Firebird to work on earlier versions of ubuntu and Sybase is a commercial program.

Install and build Quasar
First, go to, [ftp://ftp.software.ibm.com/software/globalization/icu/3.4/icu-3.4.tgz](ftp://ftp.software.ibm.com/software/globalization/icu/3.4/icu-3.4.tgz) and download the file icu-3.4.tgz to your desktop.

Next, go to [www.linuxcanada.com](www.linuxcanada.com), and download the file quasar-1.4.7_GPL.tgz to your desktop or the latest version if they have updated. While you're there, also download the comprehensive and excellent product documentation provided by Linux Canada.

Ensure that your repositories are enabled and use Adept or Synaptic to install the following:
build-essential, libqt3-mt-dev ,autoconf, tcl8.4-dev, tk8.4-dev, postgresql-7.4, postgresql-dev and qt3-apps-dev 
Stop all applications that are running to be on the safe side.
Right click on your desktop and create a new directory called quasar
Move or copy the downloaded files quasar-1.4.7_GPL.tgz and icu-3.4.tgz to the new directory quasar
Now go to the new folder and right click on icu-3.4.tgz and extract to here
Also right click on quasar-1.4.7_GPL.tgz and extract to here.
The next steps will take quite a while until finished while the compiling is done:
cd   /home/<username>/Desktop/quasar/icu
./configure
make
sudo make install
sudo cp /usr/local/lib/icu* /usr/lib/
sudo cp /usr/local/lib/libicu* /usr/lib/
cd   /home/<usename>/Desktop/quasar/quasar-1.4.7_GPL
./configure
make
sudo make install

Creating your menu icons
Open Kmenu Editor (right click on Menu button) and create entries for Quasar Server start, Quasar and Quasar Admin in the Office menu.

Quasar Server Startup: (or do with a script when PC starts)
Command: gksudo /opt/quasar/bin/quasard
Icon: /opt/quasar/setup/quasar_setup.xpm

Quasar Admin:
Command: gksudo /opt/quasar/bin/quasar_setup
Icon: /opt/quasar/setup/quasar_setp.xpm

Quasar
Command: /opt/quasar/bin/quasar
Icon: /opt/quasar/setup/quasar_client.xpm

Set up the PostgreSQL database

sudo  -s  -u postgres             (make yourself the postgres user)
createuser  -d  -E  -P  quasar_dba      (give a dba password i.e. Thebear)
createuser   -E  -P  quasar                  (give a non dba password here i.e. Teddy)
exit
Edit the /var/lib/postgresql/7.4/main/pg_hba.conf file with konquerer, right click, actions, edit as root or use sudo kwrite or krusader in root mode to edit.

Add the second row, it allows all your lan pc's with ip 192.168.0.x to access quasar:

host all all 127.0.0.1 255.255.255.255 md5
host all all 192.168.0.0 255.255.255.0 md5
Also edit the /var/lib/postgresql/7.4/main/postgresql.conf and change the line with #tcpip_socket = false to tcpip_socket = true
Now restart postgresql:
sudo   /etc/init.d/postgresql restart
Set up Quasar with the PostgreSQL server
Click Quasar Admin icon to setup.

Go to the Drivers Tab, and click Configure. Enter these settings.
Hostname: localhost
Port: 5,432
Library: /usr/lib/libpq.so.3.1
DBA username: quasar_dba
DBA password: whatever you entered earlier (i.e. Thebear)
Username: quasar
Username password: whatever you entered earlier (i.e. Teddy)
Character set: UNICODE

If all this works, set up a client in windows by downloading and installing the Windows exe file. The windows and Kubuntu PC’s should now be able to use the program and you can set up the printer via Samba if required.
;)

Your instructions look very good  ,just a question for a newbie  
If I do not have or plan to use a LAN should I omit part of the instructions
and should I install using  while in root or general user?

                                                                                  Thanks/BJ

---

### Post by Matchless on 2006-12-29
I hope I understood your question correctly. For non lan use do the complete procedure. If you are using Ubuntu there is no real changing from root to user. You log in as user and follow the guide. The instructions show where to add sudo to run that command  as "root".

---

### Post by robertrej on 2007-01-03
never give up



> **Matchless said:**
> Hi,
   First of all this howto is not my own work, it was published by Brian Walker and I have just changed a few items to make it work on Breezy Kubuntu. I still need to find out how my windows PC can use the Quasar server on the kubuntu pc. If anyone has this working please let me know and I will update the howto. Please let me have any feedback to update as well.

**_How to install Quasar Accounting on Kubuntu _**
Compliments to Brian Walker

Quasar is an accounting software for Linux and may even be one of the better types currently available for linux. Its GPL and free to use, modify or even sell! It's powerful and easy to use and a full range of support packages are available from the authors. It needs a Linux server, but clients are available for both Windows and Linux. 

Unfortunately, Quasar's not straightforward to install on kubuntu, as no pre-built packages are available. The packages are thus built from source. 

The compiling of the packages can take a while and allow yourself a couple of hours before sitting down with this. I suggest also printing out the Installation and Setup manual in case you would like to know exactly what you are doing! It may help if you stumble somewhere and is very clear. We are using Postgresql as a database as we could not get Firebird to work on earlier versions of ubuntu and Sybase is a commercial program.

Install and build Quasar
First, go to, [ftp://ftp.software.ibm.com/software/globalization/icu/3.4/icu-3.4.tgz](ftp://ftp.software.ibm.com/software/globalization/icu/3.4/icu-3.4.tgz) and download the file icu-3.4.tgz to your desktop.

Next, go to [www.linuxcanada.com](www.linuxcanada.com), and download the file quasar-1.4.7_GPL.tgz to your desktop or the latest version if they have updated. While you're there, also download the comprehensive and excellent product documentation provided by Linux Canada.

Ensure that your repositories are enabled and use Adept or Synaptic to install the following:
build-essential, libqt3-mt-dev ,autoconf, tcl8.4-dev, tk8.4-dev, postgresql-7.4, postgresql-dev and qt3-apps-dev 
Stop all applications that are running to be on the safe side.
Right click on your desktop and create a new directory called quasar
Move or copy the downloaded files quasar-1.4.7_GPL.tgz and icu-3.4.tgz to the new directory quasar
Now go to the new folder and right click on icu-3.4.tgz and extract to here
Also right click on quasar-1.4.7_GPL.tgz and extract to here.
The next steps will take quite a while until finished while the compiling is done:
cd   /home/<username>/Desktop/quasar/icu
./configure
make
sudo make install
sudo cp /usr/local/lib/icu* /usr/lib/
sudo cp /usr/local/lib/libicu* /usr/lib/
cd   /home/<usename>/Desktop/quasar/quasar-1.4.7_GPL
./configure
make
sudo make install

Creating your menu icons
Open Kmenu Editor (right click on Menu button) and create entries for Quasar Server start, Quasar and Quasar Admin in the Office menu.

Quasar Server Startup: (or do with a script when PC starts)
Command: gksudo /opt/quasar/bin/quasard
Icon: /opt/quasar/setup/quasar_setup.xpm

Quasar Admin:
Command: gksudo /opt/quasar/bin/quasar_setup
Icon: /opt/quasar/setup/quasar_setp.xpm

Quasar
Command: /opt/quasar/bin/quasar
Icon: /opt/quasar/setup/quasar_client.xpm

Set up the PostgreSQL database

sudo  -s  -u postgres             (make yourself the postgres user)
createuser  -d  -E  -P  quasar_dba      (give a dba password i.e. Thebear)
createuser   -E  -P  quasar                  (give a non dba password here i.e. Teddy)
exit
Edit the /var/lib/postgresql/7.4/main/pg_hba.conf file with konquerer, right click, actions, edit as root or use sudo kwrite or krusader in root mode to edit.

Add the second row, it allows all your lan pc's with ip 192.168.0.x to access quasar:

host all all 127.0.0.1 255.255.255.255 md5
host all all 192.168.0.0 255.255.255.0 md5
Also edit the /var/lib/postgresql/7.4/main/postgresql.conf and change the line with #tcpip_socket = false to tcpip_socket = true
Now restart postgresql:
sudo   /etc/init.d/postgresql restart
Set up Quasar with the PostgreSQL server
Click Quasar Admin icon to setup.

Go to the Drivers Tab, and click Configure. Enter these settings.
Hostname: localhost
Port: 5,432
Library: /usr/lib/libpq.so.3.1
DBA username: quasar_dba
DBA password: whatever you entered earlier (i.e. Thebear)
Username: quasar
Username password: whatever you entered earlier (i.e. Teddy)
Character set: UNICODE

If all this works, set up a client in windows by downloading and installing the Windows exe file. The windows and Kubuntu PC&#8217;s should now be able to use the program and you can set up the printer via Samba if required.
;)

---

### Post by robertrej on 2007-01-03
I am new to linux / ubuntu and need help installing Quasar accounting
I have followed the well written instruction but had 1 error message at:

sudo make install
Most of the install went well except there. 
I believe It may be that I should be in  root  user during this procedure but not
sure  .      ******************Please help****************************8

                                                                   ](*,)   Thanks / bob

---

### Post by scrooge_74 on 2007-01-05
Sorry can't help you have to post the details of the errors.  And also I am having problems myself with Postgres, I still can connect to the database

---

### Post by robertrej on 2007-01-05
I switched  over to kubuntu to see if that helps and all went well until I got to:

bob@bob-desktop:~$ sudo cp /usr/local/lib/icu* /usr/lib/
cp: omitting directory `/usr/local/lib/icu'
bob@bob-desktop:~$

and got a message "omitting directory " on the second line above.
Once again I am very new to linux but what is     " /icu* " ?
i believe it may be copy all but not sure .

Any help would be great  !             Thanks/bob :-k 






QUOTE=robertrej;1943904]Your instructions look very good  ,just a question for a newbie  
If I do not have or plan to use a LAN should I omit part of the instructions
and should I install using  while in root or general user?

                                                                                  Thanks/BJ[/QUOTE]

---

### Post by scrooge_74 on 2007-01-05
ICU you have to download and compile it first before compiling Quasar, this is the address for it  [http://icu.sourceforge.net/](http://icu.sourceforge.net/)

I am waiting for you at the corner of how to configure the postgreSQL, because I have not been able to make it work as per the instructions](*,)

---

### Post by robertrej on 2007-01-05
In regards to your reply I have downloaded and compiled icu with success
and quasar as well.I had the same error in ubuntu so not to sure if that
line of code is not right for my version or what.
In regards to postgre I was successful with the first line of instructions
" sudo -s -u postgre"
but thats were I can not move forward.

*************** Update to below article *********** I have since my last comments switched to Turbocash and found
it to be very easy to install, free to use and has all the features I was looking for ! It runs very well with wine installed(0.9.30).
---------------So when it comes to Linux if you can not find what you want just keep looking sooner or later you will find it! ----------feb 12.
                              good day / bob


*********** MY KINGDOM FOR AN EASY TO INSTALL FULL ACCOUNTING DEB PACKAGE*****
*********** WITH INVENTORY CONTROL************************************************
                                  Maybe Gnucash will produce one soon! 
                                                  Have a good day /Bob

---

### Post by scrooge_74 on 2007-01-05
Then you have arrive to the same conrner I am :D

I am stuck at the same place and wishing for the same

---

### Post by HailandKill on 2007-01-09
> **robertrej said:**
> I switched  over to kubuntu to see if that helps and all went well until I got to:

bob@bob-desktop:~$ sudo cp /usr/local/lib/icu* /usr/lib/
cp: omitting directory `/usr/local/lib/icu'
bob@bob-desktop:~$

and got a message "omitting directory " on the second line above.
Once again I am very new to linux but what is     " /icu* " ?
i believe it may be copy all but not sure .

Any help would be great  !             Thanks/bob :-k                                                     

robertrej, I'm been getting the exact same error with Kubuntu. How did you get around it?

I do have an icu directory under /usr/lib/icu but the verion appears to differ from the one I have at /usr/local/lib/icu. The folder is 3.4.1 opposed to 3.6

I have tried compiling quasar none-the-less, but I get a undefined reference to 'icu_3.6...' error. Obviously something has gone wrong with the icu installation, and since the copying part is the only part of the process that didn't work, I guess it's that.

Any ideas? Has anyone got any ideas?

---

### Post by Matchless on 2007-01-09
Hi all,
        Unfortunately Quasar did not do what I hoped for and seemed to be mostly for a shop type business. I thus never played with it after posting the howto way back and cannot give any further advice.

For those interested, the latest Crossover Office, 6.0 beta 3 installs nicely in Kubuntu Edgy and the old Quickbooks Pro 6.0 installs nicely and runs directly from a linux menu icon without any noticeable delay or speed loss. It seems as if the versions from 2005 onwards will not run in Crossover.
So all is not lost, just visit Codeweavers site.

---

### Post by scrooge_74 on 2007-01-09
I also tried Peachtree on Crossover and it run up to 95% of the things I used to do in Windows

---

### Post by jonny on 2007-01-21
I use Quasar extensively and find it powerful and easy to use.  However it's definitely tricky to install and I've created a page in the Ubuntu wiki that addresses the issues people have repoprted in this thread.  You can find it here: [https://help.ubuntu.com/community/QuasarAccountingInstallation](https://help.ubuntu.com/community/QuasarAccountingInstallation)

---

### Post by HailandKill on 2007-02-07
jonny, your wiki is a godsent but I'm not getting past the make stage of quasar:

ake[1]: Entering directory `/home/martin/.quasar-ins/quasar-1.4.7_GPL/postgresql_driver'
test -d ../drivers/ || mkdir -p ../drivers/
rm -f libpostgresql_driver.so
g++ -L../lib -shared -o libpostgresql_driver.so objs/postgresql_driver.o objs/postgresql_config.o objs/postgresql_config_dialog.o objs/moc_postgresql_config_dialog.o  -L/usr/share/qt3/lib -lquasar_driver -lquasar_widget -lquasar_util -lqt-mt -lpthread
/usr/bin/ld: ../lib/libquasar_driver.a(db_driver.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
../lib/libquasar_driver.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [../drivers/libpostgresql_driver.so] Error 1
make[1]: Leaving directory `/home/martin/.quasar-ins/quasar-1.4.7_GPL/postgresql_driver'
make: *** [all] Error 2

No idea where to start trying to figure out what's gone wrong here. I am installing on a x64 bit verion of kubuntu, and it does mention 'R_X86_64_32'... but I could really be barking up the wrong tree here.

---

### Post by robertrej on 2007-02-08
I decided to try some other accounting software apps. and found that Turbocash is a very 
good app. which runs very well with  wine 0.9.30 installed .It is in fact a Windows application
but who cares if it is easy to install , stable, not too hard to learn and has  all the
features you need !Compared to other FREE apps. that required many other downloads
and a lot of file configuring Turbocash  was a piece of cake to install and run.
Did I mention that Turbocash is FREE! I am sure once you get Quasar, SQL Ledger
Weberp and Ledger smb actually running they are good programs as well
however they need to be easy to install for newbies like myself.I believe Turbocash
has a USA version as well .My other choice was MYbooks but it cost about $79 U.S.  

What I really like about  Linux   --- lots of choices !--

                                                                               Good Day
                                                                                Bob  




> **robertrej said:**
> I am new to linux / ubuntu and need help installing Quasar accounting
I have followed the well written instruction but had 1 error message at:

sudo make install
Most of the install went well except there. 
I believe It may be that I should be in  root  user during this procedure but not
sure  .      ******************Please help****************************8

                                                                   ](*,)   Thanks / bob

---

### Post by scrooge_74 on 2007-02-08
Do you have a link for Turbo Cash? How good it is integrating accounting with invoice management?  I tried Quasar but gave up since I am lousy configuring PostgreSQL.

I am using Peachtree but it doesnt quite work as it did in XP,plus wine cant seem to run it any more so I have to use Cross Over and still has some problems

---

### Post by derrick1985 on 2007-02-08
> **scrooge_74 said:**
> Do you have a link for Turbo Cash? How good it is integrating accounting with invoice management?  I tried Quasar but gave up since I am lousy configuring PostgreSQL.

I am using Peachtree but it doesnt quite work as it did in XP,plus wine cant seem to run it any more so I have to use Cross Over and still has some problems

[http://www.turbocash.net/](http://www.turbocash.net/)

And for somebody interested in sql-ledger, it is easy. Search it out in synaptic/adept and it is there. Also, if you want to add the debian repository for it (more up to date version) and just download that package and then omit that repository again to return back to normal.

---

### Post by dips on 2007-04-05
Hi all. Whilst I am not exactly new at Linux - configure, make and make install hold no fears for me - I agree with some of the comments here about how difficult it is to set up some apps (I run both Kubuntu 6.10 and Ubuntu 6.06 LTS). I have attempted to install Quasar on the 6.06 machine only to stop dead because the postgresql dbase would not accept my password. So I have now installed it on the Kubuntu system and it all worked!!!!! :) . Thanks to this tutorial which I followed to the letter.

Trouble is whenever I go ito the Quasar Admin and enter the values given I get the following error box pop up.
"Failed to connect to template1 using the dba user" 

Aarrrggghhh:confused: 

It then asks if I have had any other error messages - not that I saw and then says that it might be because i have the wrong user name/password for the dba. As these as a simple as they can be I doubt that very much.

Anyone else had this problem? Anyone know what I am doing wrong?

I really, really don't want to use Turbocash as its a Windows product - *pause to spit on the ground* - but if I can't get Quasar  to work I may be forced into it.

Thanks in advance for anything.

Derek

---

### Post by jonny on 2007-04-22
> **dips said:**
> Trouble is whenever I go ito the Quasar Admin and enter the values given I get the following error box pop up.
"Failed to connect to template1 using the dba user" 


Sorry for the delay - I've been away from the forums for a while.

This problem usually means that you haven't set up PostgreSQL properly.  Does your connection work if you click the Test button on the Configure pop-up on the Drivers tab in the Admin program?

Assuming that your problem isn't a silly one (eg you mistyped your password when you set up the users), there's probably some difference between version 6.06 and 6.10 in PostgreSQL configuraration.  I no longer have 6.06 installed, so I can't investigate for you, but you might want to look at any files on your system called postgresql.conf or pg_hba.conf - these define the setup of PostgreSQL and might give you some clues as to the problem (eg are you listening to the right servers on on the right ports).  Note that you have to use sudo just to find these files - they're not visible to normal users.

---

### Post by scrooge_74 on 2007-04-23
I gave up on Quasar and went back to Peachtree by using Cross Over

---

### Post by impactpcs on 2008-12-15
I have encountered the same problem,No drivers after source installation.  turne out that I did not have the devel libraries for Postgresql installed. Make and make install again after you have installed the appropriate postgesql-server-devel.
Hope its helpfull

---

