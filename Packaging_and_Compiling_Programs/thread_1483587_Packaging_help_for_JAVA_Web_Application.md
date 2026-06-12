---
title: "Packaging help for JAVA Web Application"
date: 2010-05-14
forum: Packaging and Compiling Programs
---

### Post by john4 on 2010-05-14
Hi All,

Real noob here when it comes to deb packages, but fearless.

I have a FOSS Project called Rental Portal that I recently moved up to Launch Pad ([www.launchpad.net/rentalportal](www.launchpad.net/rentalportal)) and am trying to get a PPA going.

I recently tried to use GiftWrap to do the packaging but was told that it would not work for a straight binary (did I use the right term?) like mine.

As the title says, Rental Portal is a web application written in JAVA.  It runs using Apache, Tomcat and Postgres.  Usually, I just deploy a WAR file out in tomcat and bada-boom bada-bing your in business.

Can anyone point me to some instructions on how to create a deb package for a web application like this?

Thank you,

John

---

### Post by r-senior on 2010-05-15
I've pondered this idea myself. Don't have a solution but some ideas ...

These are the basic instructions on making a .deb:

[http://ubuntuforums.org/showthread.php?t=910717]("http://ubuntuforums.org/showthread.php?t=910717")

Presumably for the WAR file, you need a dependency on Tomcat (assuming a simple servlet/JSP application with no EJB, etc.). I'd speculate then that you could put your WAR file into Tomcat's auto-deploy directory at /var/lib/tomcat6/webapps and it would auto-deploy?

You'd still have the problem of setting up the database, but that may give you a start?

Subscribed to thread - interested to see if anyone has a complete solution.

---

### Post by john4 on 2010-05-17
**EDIT**

Thanks for the reply r-senior.

I'm not too concerned with the DB for 2 reasons: 1) Postgres is on my list of dependencies and 2) when our application initially loads in Tomcat there is a set up wizard that creates the app db for you. (Maybe in future releases the PPA can drop in the changed config files for the middle-ware too)

I looked at the link you posted, plus the basic instructions and I think I found some basic steps to get this done.  I will need to post up some instructions based on my experience.

Again really appreciate the reply.

---

### Post by r-senior on 2010-05-17
Out of curiosity, I tried the approach I suggested above with one of my WAR files and it worked a treat. In a nutshell ...

$ cd ~/Documents
$ mkdir -p helloweb_1.0-1/var/lib/tomcat6/webapps
$ cd helloweb_1.0-1
$ cp ~/helloWeb.war var/lib/tomcat6/webapps
$ mkdir DEBIAN
$ vi DEBIAN/control

```

package: helloweb
Version: 1.0-1
Section: base
Priority: optional
Architecture: i386
Depends: tomcat6 (>= 6.0.24-2ubuntu1)
Maintainer: Me <me@mymail.com>
Description: Hello World (Web)
 Another classic web application

```

$ dpkg-deb --build helloweb_1.0-1
$ sudo dpkg -i helloweb_1.0-1.deb
(Reading database ... 68654 files and directories currently installed.)
Preparing to replace helloweb 1.0-1 (using helloweb_1.0-1.deb) ...
Unpacking replacement helloweb ...
Setting up helloweb (1.0-1) ...

Checked Tomcat Manager and the application was auto-deployed. Of course, this is an install with dpkg and there would be more work to set up a ppa but the .deb part was easy.

---

### Post by john4 on 2010-05-18
Trying it now. 

Got sided tracked yesterday because I had to work out the kinks in Tomcat6 (mainly folder locations).

PPA is probably the easy part. Get your project up on LaunchPad, register you GPG, host your deb package somewhere it can be downloaded, and provide instructions for people. That's pretty much it in a nutshell.

I'll let you know how it goes today.

---

### Post by john4 on 2010-05-18
Worked like a champ...kinda of...

1) Files were deployed, but I had to change permissions before the App would start properly.  Is there something I can do to prevent this?

2) I thought, and I may be waaaayy wrong, the deb package would install the dependent applications (apache, tomcat, postgresql, etc.)?  Am I off course here or is there a way to do that?

Other than those 2 issues, it's off to finish the PPA for 10.4

Thank you again r-senior

---

### Post by r-senior on 2010-05-18
File permissions? I didn't have to change any of those (sudo dpkg -i of course), although I do have Tomcat security turned off on my Tomcat installation so it's not a completely vanilla install.

I think you'd have to install the .deb with apt-get, etc. to get dependencies resolved. I don't think dpkg does that - in fact I think apt works out the dependencies and calls dpkg -i as it sees fit. Setting up your ppa may help with that. Assumiing you have specified the dependencies in ./DEBIAN/control of course.

Thanks to you too. Gave me the incentive to look into something I've had in the back of my mind. ;)

---

### Post by john4 on 2010-05-25
Well I upgraded to 10.04 this weekend, so I'm ready to finish the PPA.

I'll try apt-get for the dependencies.  I'll also check the permissions/owners as I create the .deb package because I might made it with the wrong ones before.

Crossing my fingers...

---

### Post by john4 on 2010-05-26
Weird, just tried to redo the package on the new version of Ubuntu and got an error:

dpkg-deb: failed to open package info file `rentalportal_10.5/DEBIAN/control' for reading: No such file or directory

But the folder and file are there!?! Any ideas?

I'll try recreating the whole thing over in the morning.

**EDIT**

Well don't I feel like an *** this morning (next day)! It helps a lot if you have your folder name correct and you are in the right position in the file tree.  Done and working.  Permissions issue was solved by making sure the files (war and 2 jar) had the right owners and permissions before I created the .deb package.

---

### Post by john4 on 2010-05-27
Ugh!!!!

After all this work getting a binary .deb package created and installing correctly, I find out that Ubuntu will only accept source .deb packages for PPA's. WTF!!!

I have found 3 solutions:
[LIST=1]
[*]Screw the PPA on LaunchPad and host it myself, but this soils any plans of ever getting into the MOTU.
[*]Create a "fake" source .deb with the binaries in the tar.gz file
[*]Create a true source package that compiles the JAVA (not really viable because it could take up to 10-30 min to compile depending on the size of your system)
[/LIST]

Here is the link to the "fake" source .deb instructions:
**[https://wiki.ubuntu.com/MOTU/School/PackagingWithoutCompiling]("https://wiki.ubuntu.com/MOTU/School/PackagingWithoutCompiling")**

Off to the IRC's to ask some questions.

---

