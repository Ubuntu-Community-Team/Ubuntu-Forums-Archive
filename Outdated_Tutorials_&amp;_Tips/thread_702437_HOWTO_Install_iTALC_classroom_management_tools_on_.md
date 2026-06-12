---
title: "HOWTO: Install iTALC classroom management tools on Gutsy"
date: 2008-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Prospero2006 on 2008-02-20
Hello all, 

I am a seventh grade teacher in San Antonio, Texas. I work with  a program known as interactive Media Applications at Krueger. I have set up several of our computer labs so that they run Ubuntu/Gutsy, and I recently went about installing the iTALC, Intelligent Teaching And Learning with Computers, software in two of our labs. 

Why this How To? 


The italc-client and italc-server packages in the repositories do not work. You have to use the newest version.

Homepage: 
[http://italc.sourceforge.net/localizations.php](http://italc.sourceforge.net/localizations.php)

What is iTALC?

Italc allows one computer to monitor and completely control a classroom set of computers with the client application installed. 
You can lock the monitor/keyboard, export the teacher's display to the rest of the class, export any student display to the rest of the class, remote control any computer in the class with a click, and monitor each screen from a single interface. At a glance, you can see who is on task, who isn't, and take decisive action within seconds.  (It runs on Windows and Linux, and is an open-source project.)

Step 1: Install the  application on all of the computers in the room.

   Warning: 
      If you are monitoring more than 15 computers, this application
      will max out the teacher's cpu. There are ways to minimize the  
      cpu usage, but it's best to designate a master machine and    
      only use it as an iTALC master if you have marginal hardware.
    
    Also:
      -In order for this software to work, you have to either have
      working name resolution or static ip addresses throughout
      the lab. This software does not have a discovery feature
      built into the latest version. IP addresses must remain
      constant throughout the lab.

    ** -Download the application here:**
            [http://sourceforge.net/project/showfiles.php?group_id=132465&package_id=145556](http://sourceforge.net/project/showfiles.php?group_id=132465&package_id=145556)
(The latest development release as of this posting is 1.0.6)

    ** -Unzip the file:**
```

bunzip2  italc-1.0.6.tar.bz2 
tar -xvf  italc-1.0.6.tar

```
   
**Install the libraries and programs required to configure and compile the source code through apt-get**

```

sudo apt-get install libqt4*
sudo apt-get install libxtst-dev

```

[B]Configure and install the program.
[/B]

```

cd italc-1.0.6
./configure
make
make install

```

**Now, on the master computer create directories for your public/private keys and then generate the keys to be used:**

**Only execute this direction on the master computer.**
 ```

mkdir -p /etc/italc/keys/public/teacher
mkdir -p /etc/italc/keys/private/teacher
ica -createkeypair

```

This will create two files, each called 'key' in those respective directories. The private key will remain on the master computer. The public key will be copies across the lab. 

**On the Client Machines**

Follow all of the above directions except for the part about key creation. 

**Only execute this direction on the client machines.** 
```

mkdir -p /etc/italc/keys/public/teacher
cp /location/of/public/key/created/on/the/master /etc/italc/keys/public/teacher

```

Make the client application start when the student logs in:
**For KDE**
```

echo /usr/local/bin/ica & > /home/student/.kde/Autostart/icascript
chmod 777 /home/student/.kde/Autostart/icascript

```

**For Gnome**
Add /usr/local/bin/ica to the startup programs through the interface at the desktop. (Gnome is good like that!)

Now, when the student logs in, a round green icon should appear at the bottom of the screen in the left-hand corner with a cursive 'i' in the center. 

**Start the Master**

To start the teacher application type
```

/usr/local/bin/ica &
/usr/local/bin/italc

```

At this point you should be able to create a classroom, add client ip addresses, and connect. 

If you have any problems, email me and I will address them!

---

### Post by Mindslant on 2009-02-18
You're the guy in San Antonio.  Man do I envy you down in Houston.  I have a lab of ~26 student pc's dual booting from xp/kubuntu.  I haven't changed mine over so it's running Ubuntu 8.04.  

I have iTalc installed, got the MAC address and IP put into the system for the master stystem.  On the XP side I don't have anyproblems on this machine.  On the linux side while testing with live viewing a connection is never made.  Any suggestions?

---

### Post by rick71 on 2009-02-25
./configure goes fine. When I try to make I get :



make[3]: Entering directory `/home/hattonr/Downloads/italc-1.0.9/ica'
/bin/bash ../libtool --tag=CXX --mode=link g++  -I/usr/include/qt4 -I/usr/include/qt4/Qt -D_REENTRANT -DQT_NO_DEBUG -DQT_CORE_LIB -DQT_XML_LIB -DQT_THREAD_SUPPORT -O2 -DBUILD_ICA  -g -O2 -Wall -fPIC -fno-strict-aliasing   -o ica  -mwindows -rpath /usr/local/lib/italc ica_main.o ivs.o isd_server.o local_system_ica.o system_service.o demo_server.o demo_client.o ica_qrc.o x11vnc.o auth.o cargs.o corre.o cursor.o cutpaste.o d3des.o draw.o font.o hextile.o httpd.o main.o rfbregion.o rfbserver.o rre.o scale.o selbox.o sockets.o stats.o translate.o ultra.o vncauth.o zlib.o zrle.o zrleoutstream.o zrlepalettehelper.o tight.o -L/usr/lib -L/usr/lib/qt4 -lQtCore -lQtXml -lQtNetwork -lQtGui -lz -ljpeg -lssl -lcrypto -lXtst -lXtst -lXtst  -lXext -lXinerama -lXrandr -lXfixes -lXdamage -lcrypt -lX11  -lpthread  -L../lib -litalc_core -lnsl -lpthread 
libtool: link: unsupported hardcode properties
libtool: link: See the libtool documentation for more information.
libtool: link: Fatal configuration error.
make[3]: *** [ica] Error 1
make[3]: Leaving directory `/home/hattonr/Downloads/italc-1.0.9/ica'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/hattonr/Downloads/italc-1.0.9/ica'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hattonr/Downloads/italc-1.0.9'
make: *** [all] Error 2


Does anyone have any ideas?

---

### Post by rick71 on 2009-03-02
> **Prospero2006 said:**
>  
    Also:
      -In order for this software to work, you have to either have
      working name resolution or static ip addresses throughout
      the lab. This software does not have a discovery feature
      built into the latest version. IP addresses must remain
      constant throughout the lab.

Can you point me to some docs on how to use dynamic with iTalc? IPs? I do have a 2003 AD server runnung.

---

### Post by rick71 on 2009-04-11
I have been able to connect and control an iTalc client using the client's hostname. I installed winbind and configured nsswitch.conf to use wins before dns. I have only tried this at home. I'll give it a shot in the classroom lab next week.

---

### Post by joeizang on 2010-03-19
Hey guys,

I am trying to install italc from source and I downloaded the 1.0.9 version. configure goes fine even though the apt-get install libqt4* yields a libqt ruby1.8 unsatisfied redundancy issue so my advice use synaptic to take care of this by installing all libqt4 debs on offer (well almost all).
but my issue is this. Configure works no problems but make gives this error:
```
In file included from ./include/dsa_key.h:49,
                 from ./src/dsa_key.cpp:46:
./include/types.h:33: error: ‘uint32_t’ does not name a type
In file included from ./include/isd_base.h:37,
                 from ./include/local_system.h:31,
                 from ./src/dsa_key.cpp:47:
./include/italc_rfb_ext.h:55: error: ‘Q_UINT32’ does not name a type
./include/italc_rfb_ext.h:56: error: ‘Q_UINT32’ does not name a type
```

so my question is has anyone encountered this? any clues on what to do? the key italc uses is it the same security rsa dsa used in linux?

Thnx for all the help

Joe

---

### Post by Pudy on 2010-05-30
Hello all,

[LIST]
[*]What is the best way to - minimize the cpu usage, for master machine, becuse in our classroom we have 18 computers?
[*]what is the best code for iinstalling the intalc master?
[*]What is the code for static IP?
[*]In our classroom we have: Teacher's comp. -ubuntu 10.04, Student's comp. 18 units.
[/LIST]Please advise me the full solution
 
Pudy

---

### Post by Pudy on 2010-05-31
**Re: HOWTO: Install iTALC classroom management tools on Gutsy** 
Hello all,
[LIST]
[*]What is the best way to - minimize the cpu usage, for master machine, becuse in our classroom we have 18 computers?
[*]what is the best code for iinstalling the intalc master?
[*]What is the code for static IP?
[*]In our classroom we have: Teacher's comp. -ubuntu 10.04, Student's comp. 18 units.
[/LIST]Please advise me the full solution

Pudy
*[[COLOR=#000000]Last edited by Pudy[/COLOR]]("http://ubuntuforums.org/posthistory.php?p=9383465"); 19 Hours Ago at 04:52 PM.. *

---

### Post by Keeper of the Keys on 2010-06-24
Hi,

I am a little stuck, and hoping that someone with iTalc experience can fill the gap.

I installed iTalc-client 1.0.9 as found in the ubuntu repositories on a bunch of lucid machines, and I have a master that has to run windows 7 to demonstrate several windows only apps to the students.

I can view, takeover, lock, send text-massages and have students do demonstrations from their machines succesfully.

But everytime I try to run a deomnstration from the windows 7 machine I just get a black screen with a cursor in the middle on the student machines.

At first I was having a problem connecting but that was solved by turning of the windows firewall (I know a tad crude but this is a test environment so it matters less, once it goes up for real I'll be cleaner about it I hope).

I don't know if I'm doing something wrong, lacking some setting etc. since the documentation is a bit sketchy...

Thanks in advance.

---

### Post by Keeper of the Keys on 2010-06-24
I installed italc under maverick and I was able to show my maverick screen on the lucid client.

On windows 7 1.0.9 doesn't install properly and only the 1.0.10 build available on the website works could it be that that is what causes it? (It would seem weird to me since iTalc just uses VNC to show desktops as far as I understood....)

---

### Post by Pudy on 2010-07-25
> **Prospero2006 said:**
> Hello all, 
 
I am a seventh grade teacher in San Antonio, Texas. I work with a program known as interactive Media Applications at Krueger. I have set up several of our computer labs so that they run Ubuntu/Gutsy, and I recently went about installing the iTALC, Intelligent Teaching And Learning with Computers, software in two of our labs. 
 
Why this How To? 
 
 
The italc-client and italc-server packages in the repositories do not work. You have to use the newest version.
 
Homepage: 
[http://italc.sourceforge.net/localizations.php](http://italc.sourceforge.net/localizations.php)
 
What is iTALC?
 
Italc allows one computer to monitor and completely control a classroom set of computers with the client application installed. 
You can lock the monitor/keyboard, export the teacher's display to the rest of the class, export any student display to the rest of the class, remote control any computer in the class with a click, and monitor each screen from a single interface. At a glance, you can see who is on task, who isn't, and take decisive action within seconds. (It runs on Windows and Linux, and is an open-source project.)
 
Step 1: Install the application on all of the computers in the room.
 
Warning: 
If you are monitoring more than 15 computers, this application
will max out the teacher's cpu. There are ways to minimize the 
cpu usage, but it's best to designate a master machine and 
only use it as an iTALC master if you have marginal hardware.
 
Also:
-In order for this software to work, you have to either have
working name resolution or static ip addresses throughout
the lab. This software does not have a discovery feature
built into the latest version. IP addresses must remain
constant throughout the lab.
 
**-Download the application here:**
[http://sourceforge.net/project/showfiles.php?group_id=132465&package_id=145556](http://sourceforge.net/project/showfiles.php?group_id=132465&package_id=145556)
(The latest development release as of this posting is 1.0.6)
 
**-Unzip the file:**
```

bunzip2  italc-1.0.6.tar.bz2 
tar -xvf  italc-1.0.6.tar

```
 
**Install the libraries and programs required to configure and compile the source code through apt-get**
 
```

sudo apt-get install libqt4*
sudo apt-get install libxtst-dev

```
 
**Configure and install the program.**
 
 
```

cd italc-1.0.6
./configure
make
make install

```
 
**Now, on the master computer create directories for your public/private keys and then generate the keys to be used:**
 
**Only execute this direction on the master computer.**
```

mkdir -p /etc/italc/keys/public/teacher
mkdir -p /etc/italc/keys/private/teacher
ica -createkeypair

```
 
This will create two files, each called 'key' in those respective directories. The private key will remain on the master computer. The public key will be copies across the lab. 
 
**On the Client Machines**
 
Follow all of the above directions except for the part about key creation. 
 
**Only execute this direction on the client machines.** 
```

mkdir -p /etc/italc/keys/public/teacher
cp /location/of/public/key/created/on/the/master /etc/italc/keys/public/teacher

```
 
Make the client application start when the student logs in:
**For KDE**
```

echo /usr/local/bin/ica & > /home/student/.kde/Autostart/icascript
chmod 777 /home/student/.kde/Autostart/icascript

```
 
**For Gnome**
Add /usr/local/bin/ica to the startup programs through the interface at the desktop. (Gnome is good like that!)
 
Now, when the student logs in, a round green icon should appear at the bottom of the screen in the left-hand corner with a cursive 'i' in the center. 
 
**Start the Master**
 
To start the teacher application type
```

/usr/local/bin/ica &
/usr/local/bin/italc

```
 
At this point you should be able to create a classroom, add client ip addresses, and connect. 
 
If you have any problems, email me and I will address them!
 
How can I fixe the fadout in the student's computers after 5 min. for the teacher started to transmit?

---

