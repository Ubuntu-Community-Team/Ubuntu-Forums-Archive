---
title: "Setting JRE/JDK of Eclipse?"
date: 2005-09-10
forum: Programming Talk
---

### Post by amerigo5 on 2005-09-10
In Hoary, I have installed Sun's JDK manually using the following instruction: [http://ubuntuguide.org/4.10/index.html#jre](http://ubuntuguide.org/4.10/index.html#jre)

$ cd browse_to_your_download_folder
$ sh jre-1_5_0_01-linux-i586.bin
$ sudo mkdir /usr/java
$ sudo mv jre1.5.0_01/ /usr/java/
$ sudo chown -R root:root /usr/java/jre1.5.0_01/
$ sudo ln -s /usr/java/jre1.5.0_01/bin/java /usr/bin/java
$ sudo ln -s /usr/java/jre1.5.0_01/bin/java_vm /usr/bin/java_vm
$ sudo cp /etc/bash.bashrc /etc/bash.bashrc_backup
$ sudo gedit /etc/bash.bashrc

With the above manual installation for my Java setting, my Eclipse was using Sun's JDK. But after I upgraded to Breezy, I can no longer use Sun's JDK. Apparently, Breezy's default Java/JRE is gij-4.0. Whenever I point my Eclipse's build path to Sun's JDK (/usr/java/jdk1.5.0_04), it keeps on reverting back to gij-4.0. I cannot uninstall gij-4.0 because it will uninstall many of its dependent packages. 

Is there a way so that I can use Sun's JDK in Eclipse again (in Breezy)? 

Note: I would like to stay away from installing Sun's JDK from Synaptic.

Thank you.

---

### Post by LordHunter317 on 2005-09-10
Did you add Sun JDK as a valid JDK in the workspace properties?

---

### Post by amerigo5 on 2005-09-11
How can I add the Sun JDK on workspace properties? Is it on Windows > Preferences > Java > Installed JREs?

---

### Post by LordHunter317 on 2005-09-11
Yes.

But you also have to change what JRE is used for building, either somewhere in there or on another preference page.  I can't remember right now, I'll post tomorrow if you cannot figure it out after I reinstall eclipse on here.

---

### Post by amerigo5 on 2005-09-11
When I try to add Sun JDK at Windows > Preferences > Java > Installed JREs, it is successfully listed as one of the Installed JREs. Then I close the Preferences window. But when I re-open the Preferences windows, the JRE that I added is no longer in the Installed JREs list. Somehow, I cannot change the default JRE (/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0).

---

### Post by LordHunter317 on 2005-09-11
[QUOTE=amerigo5]When I try to add Sun JDK at Windows > Preferences > Java > Installed JREs, it is successfully listed as one of the Installed JREs. Then I close the Preferences window. But when I re-open the Preferences windows, the JRE that I added is no longer in the Installed JREs list. Somehow, I cannot change the default JRE (/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0).[/QUOTE]
 That is really odd... you're not running this as root or something, are you?

---

### Post by amerigo5 on 2005-09-11
This is really odd. This must be an Eclipse issue. But this just wasn't the case before I upgraded to Breezy.

Now, I am thinking of pointing the java (/usr/bin/java) link (which currently points to /usr/bin/gij-4.0) to /usr/java/jdk1.5.0_04. Is this a good idea even though OpenOffice2.0 depends on gij-4.0?

---

### Post by amerigo5 on 2005-09-13
Pointing /usr/bin/java to Sun's JDK (/usr/java/jdk1.5.0_04) works!!! Hopefully this doesn't break anything.

Thanks.

---

### Post by drgreborn on 2005-10-04
I'm really sorry butting in and hijacking this thread like this. I have a small problem. 

I've figured it by reading the above post. 
My apologies once again.

---

### Post by sanjose on 2005-10-04
another way to do this instead of making a link is

sudo update-alternatives --config java
sudo update-alternatives --config javac
sudo update-alternatives --config jar

this will give you a list of installed java
Choose sun java...

---

### Post by csanders on 2007-06-11
I believe the above solution will work for command line invocations of eclipse, but not if it's started from the applications menu. To fix this, you'll want to add your preferred JRE to the top of /etc/eclipse/java_home. You'll need to edit as root.

---

