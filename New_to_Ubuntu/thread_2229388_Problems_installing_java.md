---
title: "Problems installing java"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by ImmortalWombat on 2014-06-12
Hi there,
New to Linux and I'm having some trouble installing java. I made a mistake and tried to delete the directory but the terminal says permission denied. Any help is greatly appreciated.

---

### Post by QIII on 2014-06-12
Hello!

Are you trying to install OpenJDK or Oracle Java?

If the former, simply install OpenJDK from the Software Centre or by using synaptic. 

 (You may need to install synaptic: In the terminal, do ```
sudo apt-get install synaptic
```)

If the latter, please go to the Java wiki in my signature.  Under the command line methods, find the link "Using webupd8.org's strikingly simple method" and follow the simple instructions there.

Best wishes.

---

### Post by ImmortalWombat on 2014-06-13
Thanks for the help, went with OpenJDK in the end. However, I did try Oracle at first and now it seems I don't have permission to delete the files. Any advice on that front?

---

### Post by mastablasta on 2014-06-13
```
sudo
``` in terminal or 

```
gksu nautilus
```

for GUI to get super user power. then feel like a computer god and delete everything. :-) seriously, carefull when deleting files. with those commandsyou can realy remove all of them.

as for java:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

for oracle java it's best to use the PPA (it's inthe instrucitons but in case you missed it): [https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)

---

### Post by QIII on 2014-06-13
What are you trying to delete and why?

---

### Post by ImmortalWombat on 2014-06-13
I had tried to creat a directory but made a mistake and when I tried to delete it it said I didn't have the permission

---

### Post by QIII on 2014-06-13
What is the name of the directory?  How did you attempt to create it?

---

### Post by ImmortalWombat on 2014-06-13
Also, I tried to use Nautilus, but it gave me this error **ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window)**)

---

### Post by slickymaster on 2014-06-13
Please answer QIII's questions asked in [post #5]("http://ubuntuforums.org/showthread.php?t=2229388&p=13048848&viewfull=1#post13048848") and [post #7]("http://ubuntuforums.org/showthread.php?t=2229388&p=13048995&viewfull=1#post13048995")

---

### Post by ImmortalWombat on 2014-06-13
I used the cd command to create the directory and rmdir to try and delete it

---

### Post by ImmortalWombat on 2014-06-13
/jack/local/java was the name of the directory

---

### Post by ImmortalWombat on 2014-06-13
I was using this tutorial [http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux](http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux)

---

### Post by slickymaster on 2014-06-13
> **ImmortalWombat said:**
> I used the cd command to create the directory and rmdir to try and delete it

The **cd **command isn't for directories creation, it's used to change the current directory (i.e., the directory in which the user is currently working). For directories creation you use the **mkdir** command.

But we could provide better help if you answer QIII's questions.

---

### Post by ImmortalWombat on 2014-06-13
right, getting the commands confused, sorry about that. I'm trying to explain how I made everything in the first place but I'm not sure how I did it in the first place so it's a little confusing. I made the directories using this command **sudo mkdir -p /usr/local/java**

---

### Post by QIII on 2014-06-13
To be honest, without knowing what else you have installed I would not recommend removing that.  It won't hurt.

Frankly, after looking at the tutorial you linked to, I find myself wishing some brilliant, if misguided, people would stop posting fantastically overly complex and convoluted methods for installing things.  Aside from the method I directed you to, I know of one other that I would recommend.  And there is another straight-forward one I recommend to Fedora users.

In the future, it might be best to ask here before using someone's random instructions from the web.  That's why we are here.  There are forum users who are very knowledgeable in subjects from soup to nuts.

In any case... are you able to use Java now? That's what is important here!  :)

---

### Post by slickymaster on 2014-06-13
> **ImmortalWombat said:**
> right, getting the commands confused, sorry about that. I'm trying to explain how I made everything in the first place but I'm not sure how I did it in the first place so it's a little confusing. I made the directories using this command **sudo mkdir -p /usr/local/java**

If you've run ```
sudo mkdir -p /usr/local/java
``` how come you get /jack/local/java? That just doesn't makes sense.

Also, from what I understand, you end up installing OpenJDK from the software center, right? If so it theoretically it got installed in **/usr/bin/java** and being so you can go ahead and delete the folder you created.

But just for playing on the safe side, can you please provide the output you get when running the following in a terminal window (one at a time):```
ls -la /usr/local/java
whereis java

```

---

### Post by ImmortalWombat on 2014-06-13
I should have specified, I used the same comand to make /jack/local/java. I don't know how that slipped my mind. I can't use java just yet, still trying to install java from openjdk

---

### Post by QIII on 2014-06-13
If you are trying to install OpenJDK from openjdk.java.net, please install it from the Software Centre instead.  That will make things much easier and ensure that you get updates when you do your periodic updates.

---

### Post by ImmortalWombat on 2014-06-13
Right, I did that but when I launch applications that require java they still say that java is not installed, any idea why this would be?

---

### Post by QIII on 2014-06-13
Could you execute ```
java -version
``` in the terminal and past back the results?

---

### Post by ImmortalWombat on 2014-06-15
java version "1.7.0_55"
OpenJDK Runtime Environment (IcedTea 2.4.7) (7u55-2.4.7-1ubuntu1)
OpenJDK 64-Bit Server VM (build 24.51-b03, mixed mode)

---

### Post by ImmortalWombat on 2014-06-15
Thanks for all the help, I've got it up and running now

---

