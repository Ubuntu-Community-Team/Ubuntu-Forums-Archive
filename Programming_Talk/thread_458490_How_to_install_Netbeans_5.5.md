---
title: "How to install Netbeans 5.5?"
date: 2007-05-29
forum: Programming Talk
---

### Post by Tsega on 2007-05-29
Hello people, I just wanted to know if anyone here could help with installing netbeans 5.5 with modules on my Ubuntu 7.04  Machine from a CD. I've read some of the topics in the forums but they all use the online installation, if I' m correct. Another, even more important thing is, if you guys could tell me a very good book to read and learn Linux/Ubuntu cause I completely suck!:( Just another thing I thought that java was preinstalled on 7.04  (I mean the SUN version).

---

### Post by daxumaming on 2007-05-29
Here's the Netbeans Downloads site: [http://www.netbeans.info/downloads/index.php](http://www.netbeans.info/downloads/index.php) it's 129MB and you don't have to install it from the CD since it's a stand-alone installer. It does contain the addon modules. As for installation instructions, you can also find it on the download page.

As for a book, I think this will suit you well: [http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942](http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942)

And no, Java isn't installed by default on all Ubuntu installs. You still have to download and install JRE.

---

### Post by Tsega on 2007-05-30
> Here's the Netbeans Downloads site: [http://www.netbeans.info/downloads/index.php](http://www.netbeans.info/downloads/index.php) it's 129MB and you don't have to install it from the CD since it's a stand-alone installer. It does contain the addon modules. As for installation instructions, you can also find it on the download page.

You see Dax I have a problem with that. I only have a 56 kb/s connection and I believe it would take ages to do all that. However,I have the CD that I got from Netbeans.org and it has a Linux (netbeans5_5.bin) file. I would really like it if I could install that. It also has the mobility pack and the java server as well. 

> As for a book, I think this will suit you well: [http://www.amazon.com/Official-Ubunt.../dp/0132435942](http://www.amazon.com/Official-Ubunt.../dp/0132435942)

I have checked this out and I was just wondering if it has all that I need to know about Linux in general as well? 

> And no, Java isn't installed by default on all Ubuntu installs. You still have to download and install JRE.

Same as netbeans I have the linux files (on a CD) but I just don't know how to install them. Thanks for helping me out and sorry for being a bit picky.

---

### Post by samjh on 2007-05-30
> **Tsega said:**
> ...I have the CD that I got from Netbeans.org and it has a Linux (netbeans5_5.bin) file. I would really like it if I could install that. It also has the mobility pack and the java server as well. 

You need to place that .bin file somewhere on your hard drive (eg. in your home directory), and run it.   To run a file in Ubuntu, right-click on the file, select Properties, choose the Permissions tab, and tick the box that says "allow executing file as a program".  Then you just need to double-click on the file to run.

If you have Sun Java installed on your Ubuntu machine, then Netbeans will install without hassles.

If you do not have Sun Java installed, then you need to run this command on your terminal (requires internet connection) and get it installed before trying to install Netbeans:
```
sudo apt-get install sun-java6-jdk
```
It will probably take a few hours to download on a 56k connection.

---

### Post by Tsega on 2007-05-30
Now that 's what I'm talking about!
> It will probably take a few hours to download on a 56k connection.
:( Well I really can't do that but I have a friend who can get me the complete Linux download easily. Maybe I can install it like netbeans without an internet connection ?  Thanks samjh.

---

### Post by malfist on 2007-05-30
copy with linux .bin off of the CD and then set read/write/execute privlege to it and run it, it will install.

edit: oh, you're talking about the ubuntu cd, not the netbeans cd. Do it overnight

---

### Post by daxumaming on 2007-05-30
I'm sorry, you weren't clear that you have the Netbeans CD... I thought you wanted to download the deb packages from another computer, probably at school or work, with broadband access and burn it on a CD.

Netbeans depends on JDK 5... And, although I haven't tried it yet since I'm still waiting for the CD, installing Netbeans will prompt you to also install JDK which "should" also be in the CD. And of course, JDK includesl JRE by default... It's a vicious cycle.

As for the book, the official ubuntu book is all you need for managing almost all Debian-based distros like, well, Debian, Xandros, Mepis, etc. minus the **sudo**. 

But if you want a book that you can use on all distros... then check this book: [http://tldp.org/LDP/intro-linux/html/](http://tldp.org/LDP/intro-linux/html/) in HTML and [http://tldp.org/LDP/intro-linux/intro-linux.pdf](http://tldp.org/LDP/intro-linux/intro-linux.pdf) in PDF. Just don't be scared of the command line.

Goodluck!

EDIT:
BTW, if JRE isn't on the CD, then have your friend download it here: [http://javadl.sun.com/webapps/download/AutoDL?BundleId=11187](http://javadl.sun.com/webapps/download/AutoDL?BundleId=11187)
it's a bin file and is around 18MB. On 56K, I think it'll take around 2 hours depending on how reliable your ISP or quality of connection is. Again.. Goodluck!

---

### Post by Tsega on 2007-06-01
Thanks dax! That was really helpful esp. the book, it is a very interesting read and I really like it. I haven' really tried what you told me cause I didn't have time but I'm going to try it now and I will let you know about everything.

---

### Post by Tsega on 2007-06-15
I'm back ppl! Dax Thanks again for the help but I still need your help. I've the .bin for the Java JDK installed it as you suggested but I'm having problems setting it as the default or rather replacing the original gnu distribution. 
How do I do it? I've tried this 
```
sudo update-alternatives --config java
``` 
but I get this 
```
There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.
```

Here's what I think, I read on Sun's Linux-Java installation notes that the self-extracting non-RPM version does not replace the pre-installed one. It just extracts itself on your directory of choice. But as for me I just extracted it into my home folder and then copied it both to "/etc" and "/opt". I really making a mess of things so I need your help in these two things.

1. Where and how do I extract it?
2. How do I replace the pre-installed version?

Thanks for reading this.

---

### Post by daxumaming on 2007-06-15
My JDK is installed on /usr/lib/jvm/java-6-sun-1.6.0.00 also make sure you create a symlink directory named java-6-sun so the apps can find it.

I don't think you have to replace the older version since it won't really affect anything.

---

### Post by ikki_72 on 2007-06-20
I also had a problem installing netbeans. I have netbeans-5_0-linux.bin and copied it at  /home/umar/Desktop/ and already installed JDK 1.5.0_05 (which was automatically) at /home/umar/jdk1.5.0_05. The problem is; when I "sudo sh -i" it, it searches for JVM and stopped. Here's what i got:

Initializing InstallShield Wizard........
          Searching JVM........            


                                         No Java Development Kit(JDK) was found on this system. 

Anyway to get it done? Or should I try installing the JDK bin file with another method?

---

### Post by NeoLithium on 2007-06-20
Hmm, well. I used synaptic to get Netbeans. It WILL stop the installer because it doesn't load the IDE, it gives you the download link, then you download the file and just move it to /tmp and give it root:root permissions.  Hit enter and it installs.  Works perfectly on my Feisty setup.

---

### Post by daxumaming on 2007-06-20
No, you don't have to. Create .bashrc on your ~ then type this in:
```

#Java
export JAVA_HOME=/home/umar/jdk1.5.0_05
export PATH=$PATH:$JAVA_HOME/bin

```
If you already have .bashrc on your ~, then append the code above. If not, create one.
That should do the trick.

I'm just curious, JDK should be installed on /usr/lib/jvm/ and a java-5-sun symlink should also be create. Try that out first then we'll go from there.
Also, the "No JDK Installed" error usually happens if the installer can't find your JDK installation directory. That's the reason why we need to have .bashrc. Lastly, this not only happens on NetBeans, but also during installation of NetBeans modules and even Eclipse. But goodluck!

---

### Post by ikki_72 on 2007-06-20
~? I don't get it, sorry. Would you please explain.

---

### Post by samjh on 2007-06-20
What daxumaming is trying to say is:

Create or open a file called **.bashrc** in your home directory.  You home directory should be the default directory that is opened when you run Terminal or click on main panel -> Places -> Home Folder.  If you really feel the need to fine it, it should be /home/umar/ if your user name is umar.

In **.bashrc**, you need to add this:
```
#Java
export JAVA_HOME=/home/umar/jdk1.5.0_05
export PATH=$PATH:$JAVA_HOME/bin
```The second line tells your computer where to find the Java installation directory for your login.  The third line tells your computer where to look for executable files related to Java when you type commands into the terminal (or when an application that tries to use Java).

---

### Post by ikki_72 on 2007-06-24
okay, i'll try.

---

### Post by ikki_72 on 2007-06-25
Yes, finally I done it! Thanks guys. The .bashrc file is hidden and I actually never realized its existence in the first place :)

---

### Post by hahnemann on 2007-06-28
Hey guys!
I used automatix for downloading and install the netbeans and the JDK; all works perfectly yet, but when i try to run for example a simple form with a "hello world" label, it doesn't appear.

The neatbeans say's "Build Succesful" ; but the instance not run.  

Any ideas?

Thax.

---

### Post by samjh on 2007-06-28
What kind of error is it?  When you say "form", do you mean you get a blank window?

Do you have Compiz/Beryl enabled (desktop effects)?  They are not compatible with Java Swing.

---

### Post by hahnemann on 2007-06-28
Thank You Samjh!

The problem with it was when I click in the Run button to see and "Run"  and test the program (As an example a jForm or whatever else visual component) it doesn't appear.  

Only the output compiler say: Build Successful; but i can't see the application.  Maybe could be a window manager or something.

---

### Post by samjh on 2007-06-29
Hmmm.

If you can run Netbeans without problems, then it probably isn't your window manager.

But to make doubly sure, disable your "desktop effects" option.

Now, post the source code of your application here (hopefully it won't be too big).  Use the code tags to preserve formatting.  Perhaps there is something wrong with your code.

---

