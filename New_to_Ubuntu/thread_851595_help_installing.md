---
title: "help installing"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-07-06
I want a program like flash cs3, and i found OpenLaszlo, but i can't figure out how to install it...:confused:
is it in the repos?
How would i find out?

---

### Post by iaculallad on 2008-07-06
> **pikabuntu said:**
> I want a program like flash cs3, and i found OpenLaszlo, but i can't figure out how to install it...:confused:
is it in the repos?
How would i find out?

[Flash CS3]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7120") won't work using WinE. I haven't had any experience with OpenLaszlo, but I could direct you to their [documentation]("http://www.openlaszlo.org/documentation").

---

### Post by pikabuntu on 2008-07-06
> **iaculallad said:**
> [Flash CS3]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7120") won't work using WinE. I haven't had any experience with OpenLaszlo, but I could direct you to their [documentation]("http://www.openlaszlo.org/documentation").

their documentation was too confusing for me

is there any way to see a list of the stuff in the repos?

---

### Post by iaculallad on 2008-07-06
> **pikabuntu said:**
> their documentation was too confusing for me

is there any way to see a list of the stuff in the repos?

You could try [Ubuntu's package section]("http://packages.ubuntu.com/").

---

### Post by Bentai on 2008-07-06
[http://www.openlaszlo.org/lps4.1/docs/installation/](http://www.openlaszlo.org/lps4.1/docs/installation/)
[http://www.openlaszlo.org/lps4.1/docs/installation/install-instructions.html](http://www.openlaszlo.org/lps4.1/docs/installation/install-instructions.html)

Ok one thing, it looks like you need the Java SDK installed on your machine to proceed. You've got two options. You can go to the [Sun Java JDK site]("http://java.sun.com/javase/downloads/index.jsp"), click the download link for "JDK 6 Update 6" and install that.

The other option, type this from the command line to get the non-commercial java SDK.
```
sudo apt-get install free-java-sdk
```
If you go that way, you'll need to manually set the JAVA_HOME variable and the PATH for the java sdk so OpenLaszlo knows where to go. In that case, you'll need to do this:

1) Go to the Terminal and type "gksudo gedit ~/.bashrc"
2) Add these lines at the bottom of the file
```
JAVA_HOME=/usr/lib/fjsdk
PATH=$PATH:/usr/lib/fjsdk/bin
export PATH
export JAVA_HOME
```
3) Save the file, close. Log out, log back in.

With all that done, now you can unpack and run the program as the installation instructions state.

---

### Post by wrtpeeps on 2008-07-06
> **pikabuntu said:**
> their documentation was too confusing for me

is there any way to see a list of the stuff in the repos?

You can search repos:

```
sudo aptitude search package
```

so

```
sudo aptitude search openlaszlo
```

(returned 0 results by the way).

---

### Post by Bentai on 2008-07-10
*bump*
So did it work?

---

### Post by pikabuntu on 2008-07-10
I did the java part but it said that the laszlo file was not there to download :(

(sorry it took so long to respond)

---

