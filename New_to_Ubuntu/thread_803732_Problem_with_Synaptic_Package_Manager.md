---
title: "Problem with Synaptic Package Manager"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Tribulation on 2008-05-22
I tried adding a repository (not knowing what I was doing, I was trying to download VLC but the instructions on the site aren't helping) and apparently messed something up. Whenever I try to get into the Synaptic Package Manager I get an error message that states: E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I've been looking around but can't figure out how to get to the repository dialog.

---

### Post by bluefrog on 2008-05-22
system/admin/synaptic, settings/repositories

---

### Post by Kouki on 2008-05-22
Somethings gone wrong with your sources.list don't worry I've messed mine up many many times.

Open the terminal and paste the following in

> sudo gedit /etc/apt/sources.list

Copy and paste all the text onto here and we can have a look to see what's wrong with line 56.  (I probably won't have a clue how to fix it as I'm still a new to this but someone will for sure)

---

### Post by Tribulation on 2008-05-22
Thanks for that command, Kouki, I found the error myself. I'm still not sure I even entered the right thing but when I went to type http I typed in htto which is probably what ticked it off. I just deleted the entire line and everything's peachy now.

---

### Post by tormaser on 2008-05-23
i tried to install  Avant-Window-Navigator in hardy but something gone wrong and i get the following error...

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '' is not known on line 78 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

can somebody helpme??


never mind was an extra character in sources.list it's working now tanks anyway

---

### Post by Matt640 on 2008-05-24
Re: Synaptic Package Manager Problem
Re: Synaptic Problem!
Hey.
I'm sorta having the same problem here only the cause was something different. I'm using the ordinary Desktop Edition of Ubuntu 8.04 not the 64AMD one. So I read from the Forums that by installing Sun Java 6, I can get my FrostWire up and running again. So I use my SPM to find it and download it. In the middle of Download/Installing, it hanged/jammed and my only option was to reboot. After I did, I realize that I can't open my SPM and it ask me to manually run sudo dpkg --configure -a. When I do, this turns up:
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation. You will need to go download one of the
archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

As you can see, I'm in desperate need of HELP! Can anyone encrypt this for me?

---

