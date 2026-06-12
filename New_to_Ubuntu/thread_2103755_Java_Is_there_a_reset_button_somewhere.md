---
title: "Java: Is there a reset button somewhere?"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by SteamDonkey74 on 2013-01-11
I have been trying to get JMRI 3.0 (a Java based model railroad program) to work on my computer running Xubuntu 12.04. In trying to get something squared away with the program's ability to recognize USB port connected devices I tried several things including installing probably more version of Java than I should have, and I would like to just hit the "reset" button if there is one.

I have the Oracle version of Java, I think (but I don't know how to confirm this) and aldo both OpenJDK Java Runtime 6 and 7. If I can zonk all of them in one fell swoop and then just reinstall one of the OpenJDK versions I am fine with that, but I am having a hard time determining where those files are stored and how to go about deleting them. I am fine with doing this on the command line if need be.

Thank you in advance for your help,
Adam

> **Mr. Furious**: Okay, you know what, can we just start again? Is there like a reset button on this thing or something?[B]
Captain Amazing[/B]: No you little freak, there's no button for resetting! 

---

### Post by SteamDonkey74 on 2013-01-11
If there is directory within the file system that holds all the Java stuff and all I have to do is delete everything in it including the hidden files I would consider that. I suppose I could also reinstall the system and just start all over, though that seems a little more extreme.

---

### Post by oldos2er on 2013-01-11
Use the Software Center or apt-get remove, whichever you prefer, to remove Java. If you delete files willy-nilly some may be left behind to cause future problems.

---

### Post by SteamDonkey74 on 2013-01-11
That's why I put the question here. Being new to Ubuntu I knew that there was something I wasn't considering. Thank you for your response!

I went through the terminal emulator popping back commands in my history until I found the moment I installed oracle java and I went ahead and switched it from sudo apt-get install <package> to sudo apt-get --purge remove <package>. It seemed to proceed smoothly. I also went ahead and deleted through the Ubuntu Software Center the OpenJDK Jave Runtime packages. I think I have now brought myself back to square one.

---

### Post by arpanaut on 2013-01-11
This may help you out:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by SteamDonkey74 on 2013-01-11
Thanks for the link. I will check that out.

Adam

---

### Post by SteamDonkey74 on 2013-01-12
Well, I was having multiple problems with Java and Java related things I had installed on bad advice, and it's not like I had a lot of things to re-do on this only 9 or 10 day install of Xubuntu so I went ahead and did a clean installation, checked the java version at the terminal, and then went and ONLY added OpenJDK Java 7 Runtime from the Ubuntu Software Center.

Thanks for your help!

Adam

---

### Post by oldos2er on 2013-01-12
Oracle's Java has some serious security flaws: [http://www.cbsnews.com/8301-205_162-57563619/u.s-tells-computer-users-to-disable-java-software/](http://www.cbsnews.com/8301-205_162-57563619/u.s-tells-computer-users-to-disable-java-software/)
As far as I know this does not apply to OpenJDK.

---

