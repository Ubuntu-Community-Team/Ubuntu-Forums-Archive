---
title: "chat help"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by jjstein on 2008-05-17
I've at last gotten just about everything to work how I want it but one thing.  I've tried everything I know to try but nothing seems to work.  Every time I try to go to any form of chat room it just refuses to work.  The main one I'm trying to use is: [http://www.megadeth.com/chat.php](http://www.megadeth.com/chat.php)

Any help would be great.

---

### Post by sstusick on 2008-05-17
You might need to install flash.

---

### Post by NightwishFan on 2008-05-17
You can try installing java and the restricted extras, although it seems to me there is only a 30% chance it will work.
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by jjstein on 2008-05-17
Sorry but how would I go about doing that?

---

### Post by NightwishFan on 2008-05-17
Do not be sorry I am here to help. Press alt+f2 and type:
```
xterm
``` then push enter. In the black box, type:
```
sudo apt-get install ubuntu-restricted-extras
```
Do not close the terminal window, it will ask for password but not appear to type but it does, just type blindly and press enter. Answer any questions with "y" and push enter. If you get a blue window, press tab to select "agree" or something along those lines, and press enter. Then close and open firefox and try to chat. If nothing, reboot and try again, it should work ok, if not it is the sites fault for using an old form of java. Good luck, and ask if you have any questions.

---

### Post by jjstein on 2008-05-17
I already have restricted extras installed apparently.  It still doesnt work :/

---

### Post by NightwishFan on 2008-05-17
I see, then your version of java may not be compatible. ;/

---

### Post by dstin1 on 2008-05-17
I assume you are using firefox type ```
about:plugins
```and tell us what you are using for java make sure you look at the entire page in the description column.

---

### Post by Xiong Chiamiov on 2008-05-17
[Installing Java on Ubuntu]("http://www.psychocats.net/ubuntu/java")

---

### Post by jjstein on 2008-05-17
```
Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_03 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_03 	Java 		Yes

```

hope that helped?

---

