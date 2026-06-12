---
title: "Installing Groovy Grails on Ubuntu"
date: 2007-03-29
forum: Packaging and Compiling Programs
---

### Post by feravolo on 2007-03-29
Hello:

I would like to install the Groovy Programing Language and the GRAILS Web Application Framework on an Ubuntu System.

Has anyone done this before and could you please let me know if there are any debian packages already for these tools. Otherwise how can make the debian packages from the available tar balls, which I would be happy to make available to other people interested in Groovy/Grails.

Thank You

Mike Feravolo
OnA1A at earthlink.net

---

### Post by dfreer on 2007-03-29
dunno anything about groovy grails or a debian package for it.

but as for making debian packages, if you have the source files, it's pretty easy if you use the checkinstall program. just sudo apt-get install checkinstall, and then start compiling your program.
```
cd groovysource/
./configure
make
sudo checkinstall
```
Checkinstall should be fairly easy to use, as always just let us know if you have any problems running it.

---

### Post by wayneredmon on 2007-12-04
Hi Feravolo,

Here's what I did to get Groovy on Grails going on Gutsy:

Downloaded Grails release 1.02RC - I selected the tar/gz binary release.

Installed the Sun Java 5.0 Console from Ubuntu's Add/Remove Applications.  Make certain after installation that java version "1.5.0_xx" is set as your default (you can issue ***sudo update-alternatives --config java*** from the terminal)

From the terminal, GEDIT your .bashrc in your home directory, and add the following three lines:

#your JAVA_HOME directory setting
export  JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.xx

#your GRAILS_HOME directory setting
export GRAILS_HOME=~/grails-1.0-RC2

#your PATH setting to append the Grails bin directory
export PATH=$PATH:$GRAILS_HOME/bin

Save your .bashrc edits.

Log off and log back on - or, restart.

From Terminal, issue the command **grails** from within your home directory.

If the following displays, then you can happily begin devleoping with Groovy on Grails:

[B]Welcome to Grails 1.0-RC2 - [http://grails.org/](http://grails.org/)
Licensed under Apache Standard License 2.0
Grails home is set to: /home/wayne/grails-1.0-RC2

No script name specified. Use 'grails help' for more info[/B]


Let me know if this works for you.

---

### Post by prach on 2007-12-07
Debian package for Grails

Now we've got a
debian package for Grails  For those who're using Ubuntu 7.10, would you add
your source.list to:
to test.

 deb [http://ftp.opentle.org/people/prach/ubuntu/gutsy/](http://ftp.opentle.org/people/prach/ubuntu/gutsy/) ./
 deb-src [http://ftp.opentle.org/people/prach/ubuntu/gutsy/](http://ftp.opentle.org/people/prach/ubuntu/gutsy/) ./

For Ubuntu, you have to set multiverse repo as this package depends on JDK.

The following are setting for Debian :

 deb [http://ftp.opentle.org/people/prach/debian/](http://ftp.opentle.org/people/prach/debian/) ./
 deb-src [http://ftp.opentle.org/people/prach/debian/](http://ftp.opentle.org/people/prach/debian/) ./

Here's .deb file:

[http://ftp.opentle.org/people/prach/ubuntu/gutsy/grails/grails_1.0-RC2-1_all.deb](http://ftp.opentle.org/people/prach/ubuntu/gutsy/grails/grails_1.0-RC2-1_all.deb)

Please be patient for speed because the server is in Thailand.


    Cheers

---

### Post by dholbach on 2007-12-07
[http://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](http://wiki.ubuntu.com/UbuntuDevelopment/NewPackages) has information on how to get it reviewed and included in Ubuntu.

---

### Post by plugwash on 2008-01-01
but if you made it with checkinstall don't expect it to be accepted.

checkinstall is a dirty hack for use when you really need a package ASAP or doing it properly is unusually complicated for some reason.

Information on how to do it properly can be found in the debian new maintainers guide.

---

### Post by oerd on 2008-02-04
Hi,

I tried to install prach's ubuntu 7.10 deb packages for an easy solution, yet java5 is required. I think adding sun-java6 as an alternative to java5 is a good idea ;)

Still, good work prach

---

### Post by wayneredmon on 2008-02-24
Prach,

Will the Debian packages you refer to in your December 7, 2007, post be updated to include Grails 1.0.1, and subsequent later releases?

---

### Post by zubunt on 2008-03-17
Here's how I did it:

Installed Ubuntu 7.10 64-bit Deskop version (not Server, cuz i want the GUI stuff, because the GUI in Ubuntu is gorgeous) BTW, I'm doing this into a virtual machine using VMWare running on a Windows 2003 Server 64-bit, which is really nice to use.

Once I got Ubuntu up and running I had to let it update a ton of software through the automatic update system. I think it was almost 200 packages that had to get updated. I went ahead and let that run for a while.

Then I had to decide which Java to use. I found that Ubuntu comes with a Java runtime pre-installed, but there seems to be a lot of problems with it and according to a lot of forums it is out-of-date. If you open a Terminal on the dekstop and type "java -version" you'll see that it's a gcj version of Java. If you type "javac" to see if you can compile java, you'll see that there is no javac pre-installed. 

So basically you have to install a real Java development environment. There are a lot of options. The latest as of now seems to be IcedTea, but i'm concerned by the word "Temporary" in the description of the package inside Synaptic. IcedTea does seem to be using version 1.7, which makes me think it's Java 7 somehow, but according to Sun's Java site they are still at Java 6 so i'll just blow that off as an anomaly with IcedTea's versioning numbers and that it does not mean Java 7. Man, no wonder Linux is still for techies.

So i'm going to just use Sun's JDK 6 (which is sometimes referred to as version 1.6, which is confusing, can somebody just make a decision on this one). There do seem to be concerns about this not being 100% open source yet today, but i'll deal with that down the road if I have to. For now I'm going with the most mainstream Java from Sun.

**Installing Java**

To install Sun's JDK 6 just use Synaptic. Do a search for "jdk" and then pick "sun-java6-jdk" from the list of results. You'll be asked to install a bunch of dependent packages. Go ahead and install those too. BTW, Synaptic is not the "Add/Remove..." in the Applications pulldown menu on the Ubuntu desktop. That was confusing at first. It's actually the System -> Administrative -> Synaptic Package Manager. (Why is that? Don't know. Love Ubuntu, but that's not intuitive.)

Ok, now if you type "java -version" from the Terminal window you get:
[INDENT]java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)[/INDENT]

**Getting VNC going correctly so I can use Ubuntu nicely**

As a note, to paste the following lines above into this Ubuntu forum from my windows box where I'm VNC'ing from to do this install, I found that the VNC session I was doing into my Ubuntu box doesn't support clipboard transfers. So I took a timeout and researched why and now I've installed x11vnc to get full support. I also had to install vnc-common, which is not obvious. I had to also install autocutsel, which is a program not available in the Ubuntu repositories, that allows the clipboard transfers to work with a VNC client. To get autocutsel to work I had to install checkinstall, libx11-dev, and libxaw7-dev. Holy bajooli, this is insane how difficult this is.

To recap on setting up VNC correctly and getting clipboard transfers to work I did the following:

Thanks to a previous forum posting from "intangible" from June 2005 @  [http://ubuntuforums.org/showthread.php?p=236053]("http://ubuntuforums.org/showthread.php?p=236053")

**Setting up x11vnc**

Install x11vnc: (I just used Synaptic)
[INDENT]sudo apt-get install x11vnc [/INDENT]
Install vnc-common: I used Synaptic again
Make a directory for .vnc: 
[INDENT]mkdir ~/.vnc[/INDENT]
Set the password: (vncpasswd is included with vnc-common, it was not installed by default on my system) 
[INDENT]vncpasswd ~/.vnc/passwd [/INDENT]
Make it auto-start when the user logs in and show which port we're running on (useful if you run multiple vnc servers) the port will be put in ~/.vnc/port.txt: 
[INDENT]sudo gedit /usr/local/bin/sharex11vnc[/INDENT] 

Paste in the following code
```
#!/bin/sh

x11vnc -nap -bg -many -rfbauth ~/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}"|grep -Eo "[0-9]{4}">~/.vnc/port.txt

# comment out the following if you don't want a popup telling you which port you're using.
zenity --info --text="Your VNC port is `cat ~/.vnc/port.txt`"sudo chmod 755 /usr/local/bin/sharex11vnc 
```

Go to
System->Preferences->Sessions->Startup Programs then click Add and type in sharex11vnc for the name and the command

Now, when you log in the sharex11vnc shell script that you just wrote and made executable will run and replace Ubuntu's standard Remote Desktop Client. Oh, make sure you disable Ubuntu's Remote Desktop if you have it running.

**Installing autocutsel**

Download tar.gz from [http://www.lepton.fr/tools/autocutsel/](http://www.lepton.fr/tools/autocutsel/) 
Move file: 
[INDENT]sudo mv /home/user/location/autocutsel-0.9.0.tar.gz /usr/src[/INDENT] 
Extract file: 
[INDENT]cd /usr/src;sudo tar -xzvf autocutsel-0.9.0.tar.gz [/INDENT]
Install packages required to compile and install autocutsel:
[INDENT]sudo apt-get install gcc libc6-dev checkinstall libx11-dev libxaw7-dev [/INDENT]

This may take a while if you don't already have gcc or the xlibs installed. 

[INDENT]cd autocutsel-0.9.0 
./configure[/INDENT]
(The posting I borrowed this from wanted me to do a checkinstall, but since i'm on a 64-bit platform, that was failing. Instead i just did a make install. This is not as clean as doing a Debian package because now my system doesn't know about this app, but oh well. I couldn't figure out how to get that to work better. If you are on 32-bit or know more about checkinstall, do the following: sudo checkinstall -y --nodoc The resulting deb will be installed and the package will be left in the current directory )

So, to continue without checkinstall:
[INDENT]make
make install[/INDENT]

So I ended up compiling autocutsel. Then the make install placed the autocutsel binary executable in my /usr/local/bin directory. I ran it from the command line just to make sure it didn't error out and it seemed ok. Figured I was ready to go.

Make it auto-start when the user logs in:
System->Preferences->Sessions->Startup Programs then click Add and type in autocutsel 

Go ahead and log out and then log back in. You should get a popup dialog box telling you that VNC is running on port 5900 (or some higher port). When I first did this I got an empty dialog box and then realized I never made a .vnc directory in my home directory, so it was never able to make the port.txt file. I also realized the vncpasswd didn't store my password either. So I reworked those steps again. 

Then when you connect from your Windows box, or other machine, the clipboard should finally be working. That was a big relief. I've been wanting that for a while. Why that is not part of the standard install is beyond me. Do the Ubuntu folks really think this is used as somebody's main box all the time?

BTW, this VNC setup is still not ideal for my Grails development because I have to login from the VMWare Server Console first to get the VNC session started. This is sort of nice right now because it's an extra security precaution, i.e. i've never fully trusted VNC to be secure sitting out there on the Internet for anyone to attempt a login. Long term though this is annoying and I'd like to be able to directly VNC in and get a login prompt. I do think I'll setup SSH and do port tunnelling. That may be another post.

**Ok, now back to installing Java.**

Now when I type "java -version" I get:
[INDENT]java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)[/INDENT]

This is good. Now I need to have JAVA_HOME set as an environment variable. java and javac seem to be in my path, but it looks like Groovy and Grails and perhaps other apps really rely on those environment varaibles. Typing "env | grep JAVA_HOME" doesn't seem to show me anything, so let's figure out how to set that variable.

Looks like Ubuntu has a file for global environment variables, rather than you having to manipulate your .bashrc file. That seems like a nicer way than the older method, but that is definitely a big shift.

Type:
[INDENT]sudo gedit /etc/environment[/INDENT]

Then enter a line for:
[INDENT]JAVA_HOME=/usr/lib/jvm/java-6-sun[/INDENT]

**Grails, baby!**

Ok, now it's time to go get Grails. I don't think you need to separately get Groovy. I'm guessing Groovy is included in the Grails tarball.

Go to:
[http://www.grails.org/Download](http://www.grails.org/Download)

Then download the latest version. For me it was version 1.0.1 @ [http://dist.codehaus.org/grails/grails-bin-1.0.1.tar.gz](http://dist.codehaus.org/grails/grails-bin-1.0.1.tar.gz)

I saved it to my home directory.

Then I made a directory for Grails, near the Java directory, by typing:
[INDENT]sudo mkdir /usr/lib/grails
cd /usr/lib/grails/
sudo mv ~/grails-bin-1.0.1.tar.gz .
sudo tar -zxvf grails-bin-1.0.1.tar.gz[/INDENT]

Then I went back to Gedit, which I still had running, and I entered the path to the Grails directory by adding the following line:
[INDENT]GRAILS_HOME=/usr/lib/grails/grails-1.0.1[/INDENT]

Then, boy i had a big surprise coming, Ubuntu has a different approach to setting global environment variables which I talked about earlier, but don't think for a second this is a shell script. Which means don't do something like the following to append the path:
No! No! No! 
PATH=$PATH:$GRAILS_HOME/bin
No! No! No! 

This caused me to not be able to login anymore. Geez, thanks. I removed that line and realized you have to just physically edit the Path since you can't use shell script like commands. So edit the path to include your Grails/bin directory like the following:
[INDENT]PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/grails/grails-1.0.1/bin"[/INDENT]

For reference, my /etc/environment file now reads:
[INDENT]PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/grails/grails-1.0.1/bin"
LANG="en_US.UTF-8"
JAVA_HOME=/usr/lib/jvm/java-6-sun
GRAILS_HOME=/usr/lib/grails/grails-1.0.1[/INDENT]

I logged out and then logged back in to have the environment variables re-read.

Now, from a terminal I can type:
[INDENT]grails[/INDENT]

And I get the following:
[INDENT]Welcome to Grails 1.0.1 - [http://grails.org/](http://grails.org/)
Licensed under Apache Standard License 2.0
Grails home is set to: /usr/lib/grails/grails-1.0.1

No script name specified. Use 'grails help' for more info[/INDENT]

**Done**

Right on! I'm ready to go with Grails. Wow, that was a pile of work. That only took a full Sunday afternoon to figure out. Hope this helps you get it done wayyyyyyyy quicker.


**Update - Getting VNC to connect without being logged in**

Several hours later I did update my box to allow for VNC connections without being logged in. It just became too much of a pain without it. To solve security issues, please use SSH and tunnel the connection to port 5900.

Refer to the following posting for setting up VNC to work without being logged into your Ubuntu box, even though it's a little out-of-date [http://ubuntuforums.org/showthread.php?p=235746&posted=1#post235746](http://ubuntuforums.org/showthread.php?p=235746&posted=1#post235746)

Here's what I did:

Make another password file for the global VNC that is tied to the login prompt which is generated from the GDM (Gnome Desktop Manager). The password file should be stored in a global folder, since it's not really your password, it's everyones' that uses the box.

[INDENT]sudo x11vnc -storepasswd mypassword /etc/x11vnc.pass[/INDENT]

Ok, now edit the following file:
[INDENT]/etc/gdm/Init/Default[/INDENT]

I placed the following line almost at the end of the file. I put it before the Exit 0 statement. 

[INDENT]/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900[/INDENT]

So the end of my /etc/gdm/Init/Default looks like:
[INDENT]# This is to start VNC at the login prompt. Added by me 3/16/08
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900

exit 0[/INDENT]

Ok, now I tried to set this up so I wasn't kicked out of the initial VNC session after I logged in. To do that you have to make it so that x11vnc doesn't get killed after the login is successful. You would do this by editing the following file:

[INDENT]/etc/gdm/gdm.conf[/INDENT]

And finding the setting for KillInitClients and uncommenting it out and setting it to false like so:

[INDENT]KillInitClients=false[/INDENT]

I couldn't make this part work, so I gave up. At least I can now login without having to Remote Desktop first to my server and going into the VMWare Console. I just have to VNC in twice, but it's not too bad.

Also, I went ahead and added SSH access as well. That was super easy after you figured out that SSH was made available using the OpenSSH Server package. Just go ahead and use Synaptic again to install it. Search for "ssh". Click on OpenSSH and Apply the install. Done.

Now you can connect to your Ubuntu Grails box from Putty, SSH Secure Shell, or whatever favorite SSH client you like to use.

**Update - Needed to get CVS source control going**

I'm adding this a day later from the above content. I found that I needed source control because I really needed to use a local editor to make changes to my code, rather than doing this from an interactive VNC session on my remote Ubuntu box. That's just too slow. So I had to go figure out how to do CVS. Wow, another pile of work. Here's what I did.

I just went with CVS for now rather than SVN. I've heard good things on SVN so I might check that out after this. For CVS I just made sure to install CVS via Synaptic again. I searched for "cvs" and then just installed the package. That was easy. I also went ahead and installed cvsd so I could use a pserver for authentication. When I realized you can just use SSH to connect into a CVS repository I removed cvsd because I can't believe it's safe from hackers. I feel like cvsd has a lot of FTP-like aspects to it and FTP has been notorious for having problems. Why not just leverage the heck out of how awesome SSH is, if you can.

Ok, so now that I have CVS installed, I had to configure a repository. I had to learn the naming conventions here. Basically you need one repository. I suppose you could have more if you really have an intensive development environment, but one will work for me. You should create a directory for the repository in the /opt/cvs directory structure on Ubuntu.

So, go ahead and run the command:
[INDENT]mkdir /opt/cvs[/INDENT]

Then, make a directory for your repository. Call it whatever you want, or use my favorite name:
[INDENT]mkdir /opt/cvs/myrepos[/INDENT]

Then you have to tell CVS about the existence of this repository. This was a little hard to find the command for, so here it is in all it's glory for you:
[INDENT]cvs -d /opt/cvs/myrepos init[/INDENT]

Ok, now CVS knows about your "myrepos" directory and it considers that to be your CVSROOT. In fact, it created a directory in the myrepos directory called CVSROOT. Go check it out just for the heck of it.

Now you get to connect to this repository from anywhere you want, whether it be your local Ubuntu box or your Windows Vista machine running Eclipse or IntelliJ or whatever else. I wanted to get my first project into the repository so I could start replicating it all over the place. This process is called "Importing a Module". That's important to know they are called Modules. A Module sits inside a Repository. Who invented these names? Probably that dude who gets credit for inventing CVS for his students.

I tried to connect from Eclipse first. The most important thing to know is what the connection string should be for getting to your repository. This connection string reminds me of ODBC-like connection strings on Windows boxes, or perhaps fancy FTP-style URL's that contain the username and password. Well, here's what it will generally look like:

[INDENT]:ssh:username@myhost.company.com:/opt/cvs/myrepos[/INDENT]

So just substitute the username you use to SSH into your Ubuntu box. Then of course substitute your hostname in there. If you are doing this from the same host you can just use localhost (there's no place like 127.0.0.1 - one of my favorite bumper stickers). Then the directory is fairly obvious since that's the directory we did a cvs "init" on earlier.

**Eclipse connecting to your CVS**

In Eclipse, you have to go to File -> Import -> CVS -> Projects from CVS. Then Create a New Repository Location. Host is your hostname. Repository path is /opt/cvs/myrepos. User is your SSH username, which is the same as what you login with on your desktop. Connection type is "extssh". Just use the default port. I save the password too. The connection string that Eclipse generates says :extssh: at the beginning instead of :ssh: and I guess that's just their thing because I haven't seen that used elsewhere.

Then, after you hit Next in the Wizard, you get to view the current modules. Choose the "Use an existing module" radio button. You'll see there are no projects in there. At this point I moved on to IntelliJ because I couldn't figure out how to upload my first project into cvs with Eclipse. Later on I use this same technique to import my project and it works brilliantly. So basically you now know how to use Eclipse to do CVS.

**IntelliJ connecting to your CVS**

In IntelliJ you use the Version Control dropdown menu. Choose the Import into CVS menu item. Click the Configure button. Then click the little + (plus) sign in the upper left corner (this was a little unintuitive). Then paste in the connection string from above. Then hit Test Connection. Enter your password that you use to login normally to your box. Everything should be successful. 

Hit Next in the Wizard. Then you should see it say "Loading" as it looks for modules. Your list should be empty other than the CVSROOT folder icon. You want to import into the top level tree item here, which is selected by default. Don't import into CVSROOT. Hit Next and find the project on your local drive you want to import.  Blow past the keyword substitutions. On the next screen fill in the required fields with whatever you want. Hit finish and presto. You're cooking with gas! That's it for IntelliJ.

**Your Ubuntu box connecting back to it's own CVS**

I also installed a graphical front-end to CVS on my Ubuntu box. It's called gcvs. It's a little bit of an old-school looking interface and not super intuitive, but it gets the job done. Install it from Synaptic. Just search for "gcvs". After it installs it makes a group called Other in your Applications pulldown menu on the Desktop. That took a while to find and it didn't tell you that anywhere! 

You need to connect to yourself via the Admin pulldown menu. That took a little to figure out. Paste in your connection string in the "Enter the CVSROOT" box and hit OK. Since you are using SSH you don't need to Login... or anything like that. Now you can Checkout or Import a Module from your Ubuntu box via the Create pulldown menu. I would think these would be in different pulldowns because I don't think of Create for both of these tasks, but that's how these menus are setup.

Good luck with your CVS. Happy Groovy Grails'ing on your Ubuntu box.

---

### Post by lykeion on 2009-01-21
There is a debian package available from [http://www.grails.org/Download](http://www.grails.org/Download) (latest stable version is 1.0.4)

I didn't use this, instead I downloaded the binaries and extracted this to a folder. 

Then I set the environmental variable GRAILS_HOME not by editing ~/.bashrc or /etc/environment (since this didn't work for me). 

Instead I edited **<path_to_grails>/bin/grails** (the grails start script) and added this:

```
export GRAILS_HOME=<path_to_grails>
```

To get the grails script in your path you can add this to **~/.bashrc**

```
export PATH=${PATH}:<path_to_grails>/bin
```

---

