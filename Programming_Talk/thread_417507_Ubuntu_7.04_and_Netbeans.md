---
title: "Ubuntu 7.04 and Netbeans"
date: 2007-04-21
forum: Programming Talk
---

### Post by Luft on 2007-04-21
I was really glad to hear that Sun Microsystems has made Java development with Netbeans easier and that the packages would be available.

I've managed to install all of the Java stuff except Glassfish and now I'd like to install Netbeans but I don't know the file name.  **sudo apt-get install netbeans** fails to find the packages.

Can someone tell me the correct apt-get command to get Netbeans?

Thanks.

---

### Post by Mirrorball on 2007-04-21
You have to download Netbeans from the Netbeans site and follow the intallation instructions, it's not in a repository.

---

### Post by luizfar on 2007-04-21
Actually it is in the repositories, just type:
sudo apt-get install netbeans5.5

When you're not sure of a package's name, try apt-cache:
sudo apt-cache search netbeans

returns:
netbeans5.5 - NetBeans IDE for development of applications in Java
netbeans5.5-doc - NetBeans IDE documentation bundle
netbeans5.5-platform - NetBeans Platform for building rich desktop applications in Java
netbeans5.5-platform-ja - NetBeans Platform (Japanese Localization)
netbeans5.5-platform-pt - NetBeans Platform (Portuguese Localization)
netbeans5.5-platform-zh - NetBeans Platform (Chinese Localization)

---

### Post by Mirrorball on 2007-04-21
> **luizfar said:**
> Actually it is in the repositories, just type:
Oops... Sorry for saying it was not in the repositories.

---

### Post by luizfar on 2007-04-21
Don't worry, not a problem :D

---

### Post by luminair on 2007-04-22
I came from [http://blogs.sun.com/webmink/entry/full_java_stack_in_ubuntu](http://blogs.sun.com/webmink/entry/full_java_stack_in_ubuntu) looking for the same thing.  The news implies that the Ubuntu add programs app will have java jdk and netbeans available for download.  I didn't see it there.

I will add it manually now, but I hope it will be included in the GUI properly as I expected it to be.

---

### Post by Mirrorball on 2007-04-22
Both Sun Java JDK and Netbeans are in multiverse, like luizfar said, at least for Feisty Fawn. They don't need to to be manually installed.

---

### Post by domak on 2007-04-23
well... when I'm installing netbeans from repository, thre synaptic log window displays a message like "this package is only an installer, you have to download the netbeans tar.gz from netbans.org and put it in <a directory>" (sorry, it's not the exact message, I'm not on my ubuntu box).

So, what's the point of using this installer? I can install and remove as easily by hand, no?

---

### Post by bsantos on 2007-04-24
>  So, what's the point of using this installer? I can install and remove as easily by hand, no?Kind of. It should be simpler to manage uninstalling with dpkg. It would be cool to see java really integrated in Ubuntu, easy installation, without that cheesy download move (maybe would change when(if) the license changes) and the Human theme on swing. :)

Mark already talked about SUN collaboration or willing to, so i guess it can be just a question of waiting, maybe Gutsy will pave new ground for java, as soon as GPL3 is released and SUN decides do adopt it.

Oddly enough I tried the javaws app on [this post]("http://ubuntuforums.org/showthread.php?t=402023&highlight=java+look+feel") and GTK feel was equal to human. I'll check on changing Netbeans toolkit to see if it after all the human theme works for java apps.

---

### Post by bsantos on 2007-04-24
[http://wiki.netbeans.org/wiki/view/FaqCustomLaf](http://wiki.netbeans.org/wiki/view/FaqCustomLaf)

I looked for the GtkLookAndFeel class in the jars, but couldn't find it... :(

---

### Post by domak on 2007-04-24
> It would be cool to see java really integrated in Ubuntu
Yes. A lot of things have been done (like easy jdk installation and web start that's work!) but I'm a little bit disapointed by the netbeans installation. A lot of blogs anounced a java stack with jre, netbeans and glassfish but for me netbeans is missing!

They also  have to fix the bug that display a grey window in place of swing applications (surprinsingly, the swingset almost work but not the JConsole).

---

### Post by domak on 2007-04-24
> It would be cool to see java really integrated in Ubuntu
Yes. A lot of things have been done (like easy jdk installation and web start that's work!) but I'm a little bit disapointed by the netbeans installation. A lot of blogs anounced a java stack with jre, netbeans and glassfish but for me netbeans is missing!

They also have to fix the bug that display a grey window in place of swing applications (surprinsingly, the swingset almost work but not the JConsole).

---

### Post by nsleiman on 2007-04-24
well i have netbeans running like a horse :)

as for java i have the java6 packs and downloaded the IDE from: [http://www.netbeans.info/downloads/index.php](http://www.netbeans.info/downloads/index.php)

java is just amazing under linux

---

### Post by cyfex on 2007-04-24
Just use the following script:

#!/bin/sh
export AWT_TOOLKIT=MToolkit
netbeans

I works fine with the sun-java6-xxx packages.

---

### Post by domak on 2007-04-25
That's right, I know this workaround. But I think that it has to be fixed by the distrib not individually and by the way it dosen't help to fix JConsole... (ok, maybe I can put it in my .profile).

---

### Post by legolas_w on 2007-05-01
Hi
thank you for reading my post
can some one tell me whether netbeans, glassfisha and JDK  are included in Feisty Fawn DVD or not?

---

### Post by domak on 2007-05-04
The swing problem with compiz has been fixed: [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775")

And Sun seem to consider linux/GTK as a first player in the java world: [http://java.sun.com/javase/6/webnotes/ReleaseNotes.html]("http://java.sun.com/javase/6/webnotes/ReleaseNotes.html")

---

### Post by giannisdag on 2007-05-06
Hi all,
I have a problem with the installation of Visual Web Pack. After installing netbeans on ubuntu feisty, i installed the  visual web pack. When I started the Netbeans IDE I got the following error.

[I]Warning - could not install some modules:
	Sun Web UI Components - The module named com.sun.rave.libs.portletapi/1 was needed and not found.
	InSync Source Modeler Core API - The module named com.sun.rave.designtime/1 was needed and not found.
	Data Provider - The module named com.sun.rave.sql/1 was needed and not found.
	Design-Time Base Implementations - The module named com.sun.rave.designtime/1 was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.api.designer/1 was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.api.portlet.dd/1 was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.classloaderprovider was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.designer.cssengine was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.designer.markup/1 was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.designtime/1 was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.designtime.idebridge was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.extension.openide/1 was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.extension.openide.loaders was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.jsfsupport/1 was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.project.jsf/1 was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.propertyeditors/1 was needed and not found.
	InSync Source Modeler - The module named com.sun.rave.webui.designtime/1 was needed and not found.
	Woodstock Components Runtime and Designtime - The module named com.sun.rave.designtime/1 was needed and not found.
	Woodstock Components Runtime and Designtime - The module named com.sun.rave.libs.portletapi/1 was needed and not found.
	Woodstock Components Runtime and Designtime - The module named com.sun.rave.propertyeditors/1 was needed and not found.
	XHTML Components - The module named com.sun.rave.api.designer/1 was needed and not found.
	XHTML Components - The module named com.sun.rave.designer.cssengine was needed and not found.
	XHTML Components - The module named com.sun.rave.designer.markup/1 was needed and not found.
	XHTML Components - The module named com.sun.rave.designtime/1 was needed and not found.
	XHTML Components - The module named com.sun.rave.jsfsupport/1 was needed and not found.
	XHTML Components - The module named com.sun.rave.project.jsf/1 was needed and not found.
	XHTML Components - The module named com.sun.rave.propertyeditors/1 was needed and not found.
	4 further modules could not be installed due to the above problems.[/I]
Does anybody knows about it. Before upgrading to ubuntu feisty, netbeans with Visual Web Pack were working together without any problems.

---

### Post by giannisdag on 2007-05-07
I managed to figure out what was the problem. I had to install the Netbeans 5.5.1 IDE which collaborates with visual web pack, not the netbeans 5.5 version.

---

### Post by tmarble on 2007-06-30
All:

I've just updated our temporary repository with NetBeans 5.5.1.
This version is on track to get to the official feisty-updates repository.

[http://blogs.sun.com/tmarble/entry/netbeans_in_ubuntu](http://blogs.sun.com/tmarble/entry/netbeans_in_ubuntu)

Regards,,

--Tom

---

