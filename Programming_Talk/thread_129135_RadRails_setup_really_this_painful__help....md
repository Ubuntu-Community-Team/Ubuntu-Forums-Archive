---
title: "RadRails setup really this painful?  help..."
date: 2006-02-13
forum: Programming Talk
---

### Post by telepathetic on 2006-02-13
let me bring you up to speed

0) installed ubuntu, and ruby and rails..

1) then i installed sun java and set it to be default

2) then i installed eclipse with synaptic, but it was still using gcj java to run and still sooooo slow so i did this:
3) apt-get remove --purge java-gcj-compat

and also i did this:
4) echo JAVA_HOME=/usr/lib/j2re1.5-sun > ~/.eclipse/eclipserc

now finally ecliipse was using the sun java and a little peppier.

but then when i went into add the radrails plugins, it complained about a feature.xml missing?  so then i did this:
5) sudo ln -s /usr/lib/eclipse/features/org.eclipse.rcp.source_3.1.1 /usr/lib/eclipse/features/org.eclipse.rcp_3.1.1

that got rid of that error, but installing RDT and RadRails was giving errors, so then i tried launching eclipse with sudo:
6) sudo eclipse

7) that let me install the plugins now
(also gksudo did not work-- for some reason when i did that it wasn't trying to use the sun java anymore and it couldn't find a java to use-- i read somewhere that all gui's should start with gksudo if you want to start them with root-- not sudo-- is this true?)

now i have the plugins in place, but i get an error when i start a new project that says "unable to create master table", but that does not happen when i start eclipse as root.  But I'm assuming i should not have to be starting eclipse with sudo everytime?

thanks so much for any help you can offer!!
so frustrating figuring all this out...

also-- is radrails the best rails ide right now?  or should i be using jedit? or freeride? or??

thanks!

---

### Post by concept10 on 2006-02-13
Forget that method of installation!  Just goto RadRails.org and download the Linux tarball and run it directly from the folder.

I have used RadRails for a couple of months, but now I use gvim (Cream for ViM) and I use Nautilus for file navigation and always have a terminal open.

RadRails is a young app, and it might mature to something great, but it after working with Ruby on Rails for 6-8 months, you just don't need the wizards and other stuff that goes along with it.

---

### Post by gtoddv on 2006-04-07
I followed your instructions to the letter and have had absolutely no problems. 

Breezy 5.10
Ruby 1.8.4 - hand configured and compiled on my machine
Gems 0.8.11

Sorry it didn't work out for you but thanks for helping me out!

---

### Post by gtoddv on 2006-04-09
[quote=gtoddv]I followed your instructions to the letter and have had absolutely no problems. 

Breezy 5.10
Ruby 1.8.4 - hand configured and compiled on my machine
Gems 0.8.11

Sorry it didn't work out for you but thanks for helping me out![/quote] 


I have never quoted myself before!

  	 	 	 	 	 	 	 	  Anyway, I decided that a non-functional help system was enough of a reason to blow away the synaptic installation. I went out and downloaded the package from eclipse.org and installed in under /opt. The current release is 3.1.2 and Ubuntu's is 3.1.1. Everything is working perfect except:
 [LIST=1]
[*]Can only start the program by 	clicking on the binary in the install directory.
[*]Can't save any settings, including workspaces because of 	permissions issues, most likely related to how I have to start the 	program.
[/LIST] I wouldn't be going through all this pain (see my signature) if it weren't for the fact that I can use Eclipse for Rails, Ruby, AND PHP. I still occasionally play with JAVA too so this would be a good solution for me if I could get it working. Bottom line is the original author of this thread is right, does it really have to be this painful?

---

### Post by krueger on 2006-04-10
I used Gentoo (great) before and now Ubuntu (also great). I've always found it to be easier to manage Eclipse outside of whatever packaging system that is used in your distro. Eclipse is just moving too fast and also has excellent support for upgrades inside the application. Installation of Eclipse is very simple just unzip/untar into some directory of choice. If you need a link in the menu you can create a menu entry manually with the menu editor, that points to the Eclipse binary.
 
I also like to download features and plugins into a directory that is housed outside of the default installation path. If you do this you can upgrade the Eclipse SDK and still use the features you've already downloaded (of course you need to check which versions of the SDK the features require etc.)
 
Here is how i manage Eclipse currently. 
 
I have two SDK:s installed
 
~/lib/eclipse-sdk/3.1.1
~/lib/eclipse-sdk/3.1.2
 
I install all features and plugins into the following folder. 
 
~/lib/eclipse-ext/3.1.x
 
I try to use remote feature update sites as much as possible. For RadRails you have [http://radrails.sourceforge.net/update]("http://radrails.sourceforge.net/update") . It's easy to disable and enable this location inside of Eclipse.
 
Maybe when 3.2 is coming out I will create a whole new extension directory for the 3.2.x series.
 
Hope this helps with the Eclipse setup in Ubuntu!!

---

### Post by jonasbuntu on 2006-04-17
I had no trouble running radrails, however it refuses to connect to my local myql database. I had j2re 1.5 installed long before I used radrails, so maybe that helped a bit. 

The mysql problem is still ongoing. I don't know if it's eclipse or radrails that's in the way of my database connection. Even with the correct database.yml file settings radrails says it is unable to connect. And there is no logging of any connect or non connecting error. There is no evidence in the system logs or the radrails logs of any database connecting or error reporting. 

The radrails looks great, but the database connection is a primary concern. My setup is MySQL 4.1.12, ruby 1.8, Ubuntu Breezy 5.10 kernel 2.6.12-10, radrails .6.2. 

Is anyone getting any logged database information?

---

### Post by Tasu on 2006-06-08
[QUOTE=telepathetic]that got rid of that error, but installing RDT and RadRails was giving errors[/QUOTE]

Hi!
I think I have sorted out the radrails rdt problems, even I had some problems installing it, radrails was invalidating eclipse by requesting org.rubypeople.rdt.launching as a plugin, wht it can't find is the line referring to that plugin in the feature.xml file under
eclipse/features/org.rubypeople.rdt.source_0.8.0.604272100PRD (note the source bit in the name here! ^_^)
All these lines are in the rdt folder's feature.xml file, but radrails seems to look for them under the source one, after coping all the plugins declarations there, radrails installed properly.

Here are the lines I added to the file:
eclipse/features/org.rubypeople.rdt.source_0.8.0.604272100PRD/feature.xml

> 
	<plugin id="org.rubypeople.rdt.launching" download-size="0" install-size="0" version="0.8.0.604272100PRD"/>
	<plugin id="org.kxml2" download-size="0" install-size="0" version="2.1.4"/>
	<plugin id="org.rubypeople.rdt.doc.user" download-size="0" install-size="0" version="0.8.0.604272100PRD" unpack="false"/>
	<plugin id="org.epic.regexp" download-size="0" install-size="0" version="0.1.4"/>
	<plugin id="org.rubypeople.rdt.ui" download-size="0" install-size="0" version="0.8.0.604272100PRD"/>
	<plugin id="org.rubypeople.rdt" download-size="0" install-size="0" version="0.8.0.604272100PRD" unpack="false"/>
	<plugin id="org.rubypeople.rdt.testunit" download-size="0" install-size="0" version="0.8.0.604272100PRD"/>
	<plugin id="org.rubypeople.rdt.debug.ui" download-size="0" install-size="0" version="0.8.0.604272100PRD"/>
	<plugin id="org.rubypeople.rdt.debug.core" download-size="0" install-size="0" version="0.8.0.604272100PRD"/>
	<plugin id="org.rubypeople.rdt.core" download-size="0" install-size="0" version="0.8.0.604272100PRD"/>

---

