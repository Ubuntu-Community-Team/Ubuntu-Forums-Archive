---
title: "Installing Sun JDK 6"
date: 2007-01-07
forum: Programming Talk
---

### Post by laxmanb on 2007-01-07
Can somebody give me the apt-get commands for installing the Java 6 SDK??

and also how do i install netbeans?? it isn'y mentioned in synaptic... i have a self extracting .bin file but that gives me problems..

---

### Post by phossal on 2007-01-07
I recommend...

**[COLOR="#248"]1. Download Java JDK[/COLOR]**
Download the [32Bit JDK]("http://java.sun.com/javase/downloads/index.jsp") right from SUN.
You want this: jdk-6-linux-i586.bin

**[COLOR="#248"]2. Download Eclipse[/COLOR]**
Download the [32Bit Eclipse]("http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/") right from eclipse.org
You want this: eclipse-SDK-3.2.1-linux-gtk.tar.gz


**[COLOR="#248"]Installation[/COLOR]**
A. Eclipse simply needs to be extracted.
B. The JDK requires that you run: *sh  jdk-6-linux-i586.bin*, and agree to the terms.
Rename the folder it produces to something simple: JDK6.32
C. Configure BASH to export the JAVA_HOME env variable like so:


```
[COLOR="DimGray"]
#BEG Copy and Paste 
#Copy and Paste at the bottom of your /home/<user>/.bashrc file 
#Then close all of your terminal windows. Reopen one, and type "eclipse"
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) ~~~~~~~~~~~~~~~~~~~~~ [/COLOR]
export JAVA_HOME='/home/<user>/Desktop/JDK6.32'
PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH 
[COLOR="DimGray"]
# The eclipse alias below assumes that you have extracted the eclipse folder 
# to your desktop. It can be anywhere. Edit path as necessary[/COLOR] 
alias eclipse='java -jar /home/<user>/Desktop/eclipse/startup.jar' 
[COLOR="DimGray"]#END Copy and Paste[/COLOR]
```


**[COLOR="#248"]Additional Info[/COLOR]**
This is a very simple way to install the latest JDK. Obviously this method isn't supported by the package managers. You'll have to update on your own. The advantage is that the cooperation and performance of the two 32bit packages rivals the same on Windows. Also, this way, you can actually have multiple eclipses, JDK's, and, when you decide to, multiple Tomcat instances. They all can be installed in nearly the same way.


**[COLOR="#248"]Notes[/COLOR]**
Once eclipse is running, you'll need to change the default compiler, and possibly add the JRE:
Window -> Preferences -> Java -> Compiler (Set the version ie 6)
Window -> Preferences -> Java -> Installed JREs (Confirm your JRE)

A few times I've downloaded the JDK, only to be presented with an error that a file could not be found, and that installation could not continue. It seems that, occasionally, the file available for download has been prepared incorrectly. Once the problem is reported, and a few hours go by, I try again with success. It doesn't happen often, but it's happened more than once.

---

### Post by laxmanb on 2007-01-07
Thank You!! a very informative reply!

---

### Post by phossal on 2007-01-07
:D Welcome.

---

### Post by amgeex on 2007-01-07
Could you especify how to run the install script and where to find it? I find the installation instructions the the java website quite vague and unclear. Thanks! :D

---

### Post by phossal on 2007-01-07
Assuming you have downloaded the JDK, and you have file *[jdk-6-linux-i586.bin]("http://java.sun.com/javase/downloads/index.jsp")* on your desktop....

Open a terminal window and cd to your desktop:
```

cd ~/Desktop

```

Run the script:
```

sh jdk-6-linux-i586.bin

```

It will present you with the License Agreement. Read it (the first time) by holding enter as it scrolls, or press *q* to skip it.

Do you agree to the above license terms? Type y at the prompt and press enter.
```

y

```

It will unpack a  file to your desktop. Go back to my earlier post where I suggest renaming the file. It's just that easy.

---

### Post by icyisamu on 2007-01-07
> **laxmanb said:**
> Can somebody give me the apt-get commands for installing the Java 6 SDK??

and also how do i install netbeans?? it isn'y mentioned in synaptic... i have a self extracting .bin file but that gives me problems..
Do you still need help with installing Netbeans?

I believe all you have to do is to execute the bin file after you have install the JRE. JDK 6 is supported only in Netbeans 5.5.

---

### Post by amgeex on 2007-01-07
Oh, thanks phossal, its all clear now, its just that I didn't know what to do with that file that got decompressed off of the bin file. Thanks again!

AMGeeX

---

### Post by laxmanb on 2007-01-08
actually i have Eclipse up and Running... but i'm more comfortable with Netbeans... can you tell me how to install it?? It also comes in a self extracting .bin file... but installation fails as it fails to find a suitable JDK...

you should put netbeans in the ubuntu repositories... it a very good open source IDE...

---

### Post by phossal on 2007-01-08
If you want netbeans, you can download it with the JDK from [http://java.sun.com:](http://java.sun.com:)
jdk-6-nb-5_5-linux.bin (see my earlier link)

---

### Post by amgeex on 2007-01-08
Thanks tons phossal! I now have Java 6 on my system! :D

---

### Post by phossal on 2007-01-08
You're welcome. :D

---

### Post by GSMD on 2007-01-13
A good explanation with in-depth details on JDK6 installation is [here](http://www.centricware.org/confluence/display/~alex.yanchenko/Installing+JDK6+on+Debian+Etch+%28or+Ubuntu%29).

---

### Post by phossal on 2007-01-13
> **GSMD said:**
> A good explanation with in-depth details on JDK6 installation is [here](http://www.centricware.org/confluence/display/~alex.yanchenko/Installing+JDK6+on+Debian+Etch+%28or+Ubuntu%29).

For the record (I checked out your recommendation), I didn't run into any trouble, and much *prefer* the 32Bit JDK on my AMD64. I realize everyone has their own preference - some people are Ubuntu *purists* and think everything should be installed in a proper, *Ubuntu* way.

I disagree.

To get up and and running *easily*, I would never do it any other way than [this way]("http://ubuntuforums.org/showthread.php?t=332674")

---

### Post by Asham on 2007-01-13
Thank you so much for this! 

I got it working in just about 2 minutes and if I got it working on the **first attempt** - anyone can! 

Again, thank you. :D 

edit:

one thing though, how can I make jar-files runnable? They open the package manager instead of being run by the JRE. It's likely a simple thing to fix but I don't know what's causing this.

 - Adam

> **phossal said:**
> I recommend...

**[COLOR="#248"]1. Download Java JDK[/COLOR]**
Download the [32Bit JDK]("http://java.sun.com/javase/downloads/index.jsp") right from SUN.
You want this: jdk-6-linux-i586.bin

**[COLOR="#248"]2. Download Eclipse[/COLOR]**
Download the [32Bit Eclipse]("http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/") right from eclipse.org
You want this: eclipse-SDK-3.2.1-linux-gtk.tar.gz


**[COLOR="#248"]Installation[/COLOR]**
A. Eclipse simply needs to be extracted.
B. The JDK requires that you run: *sh  jdk-6-linux-i586.bin*, and agree to the terms.
Rename the folder it produces to something simple: JDK6.32
C. Configure BASH to export the JAVA_HOME env variable like so:


```
[COLOR="DimGray"]
#BEG Copy and Paste 
#Copy and Paste at the bottom of your /home/<user>/.bashrc file 
#Then close all of your terminal windows. Reopen one, and type "eclipse"
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) ~~~~~~~~~~~~~~~~~~~~~ [/COLOR]
export JAVA_HOME='/home/<user>/Desktop/JDK6.32'
PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH 
[COLOR="DimGray"]
# The eclipse alias below assumes that you have extracted the eclipse folder 
# to your desktop. It can be anywhere. Edit path as necessary[/COLOR] 
alias eclipse='java -jar /home/<user>/Desktop/eclipse/startup.jar' 
[COLOR="DimGray"]#END Copy and Paste[/COLOR]
```


**[COLOR="#248"]Additional Info[/COLOR]**
This is a very simple way to install the latest JDK. Obviously this method isn't supported by the package managers. You'll have to update on your own. The advantage is that the cooperation and performance of the two 32bit packages rivals the same on Windows. Also, this way, you can actually have multiple eclipses, JDK's, and, when you decide to, multiple Tomcat instances. They all can be installed in nearly the same way.


**[COLOR="#248"]Notes[/COLOR]**
Once eclipse is running, you'll need to change the default compiler, and possibly add the JRE:
Window -> Preferences -> Java -> Compiler (Set the version ie 6)
Window -> Preferences -> Java -> Installed JREs (Confirm your JRE)

A few times I've downloaded the JDK, only to be presented with an error that a file could not be found, and that installation could not continue. It seems that, occasionally, the file available for download has been prepared incorrectly. Once the problem is reported, and a few hours go by, I try again with success. It doesn't happen often, but it's happened more than once.

---

### Post by amgeex on 2007-01-13
> **phossal said:**
> For the record (I checked out your recommendation), I didn't run into any trouble, and much *prefer* the 32Bit JDK on my AMD64. I realize everyone has their own preference - some people are Ubuntu *purists* and think everything should be installed in a proper, *Ubuntu* way.

I disagree.

To get up and and running *easily*, I would never do it any other way than [this way]("http://ubuntuforums.org/showthread.php?t=332674")

I agree. And to run jar files I guess you just have to open the terminal and type java yourfile.jar :mrgreen:

---

### Post by Asham on 2007-01-13
Yeah, I know that :p. But I want the jars to be runnable by double-clicking them. Any ideas?

---

### Post by arashbi on 2007-01-13
I installed sun's jdk package but eclipse from the ubuntu package. I can run the eclipse from the command line but not from the menu, seems X is not aware of JDK installation nd could not pass it  to the eclipse and it searches the JDK in /use/somewhere. How Can I fix it?

---

### Post by phossal on 2007-01-13
> **Asham said:**
> Yeah, I know that :p. But I want the jars to be runnable by double-clicking them. Any ideas?

**[COLOR="#248"]Make Your Jar Files Double-Clickable[/COLOR]** *(optional)*
In this example, I'm working with Java set up as outlined in my tutorial (which isn't necessary), and the soon-to-be executable hello.jar on my desktop.
[SIZE="1"][COLOR="DimGray"]* Your JAR file must be properly exported to include the manifest (with main method).[/COLOR][/SIZE]

**[COLOR="#248"]1.[/COLOR]**  Right click hello.jar -> Open With -> Open With Other Application -> Use a custom command

```
'/home/phossal/Desktop/JDK6.32/jre/bin/java' -java
```

**[COLOR="#248"]2.[/COLOR]**  Rick click hello.jar -> Properties -> Open With -> java 
[SIZE="1"][COLOR="DimGray"](I'm selecting java, which is the command we just created, and  have deselected Archive Manager as a result)[/COLOR][/SIZE]

**[COLOR="#248"]3.[/COLOR]**  Double-click and run the file.

---

### Post by Asham on 2007-01-13
Sorry. I am guilty for thinking it would function as in Windows. Doh! ](*,) 

I think that I've actually been able to run Python files by adding executable permissions before. 

Another question, if you guys don't mind:
can I make *all* present and future jar-files clickable, or am I thinking too much in Windows ways (again)?

---

### Post by phossal on 2007-01-13
If you do what I outlined below, *all* of your .jar files become clickable.

---

### Post by Antiparadigm on 2007-01-14
Very informative!

---

### Post by strumluff on 2007-01-16
Should I remove previous versions of Java first? I have Eclipse installed at the moment and it works using an old Java 5 update.

When i run:  update-alternatives --config java

I get:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/j2re1.5-sun/bin/java

So if I was to install version 6 I feel like I'd have plenty of unnecessary versions too, how do I go about removing them? (I've only recently migrated to Ubuntu) 
Would eclipse have to be reinstalled following this? I also intend on getting NetBeans up and running too.

---

### Post by phossal on 2007-01-16
You can download netbeans *with* the JDK from sun as one .bin file if you prefer it. As for removing other versions of java/eclipse, I don't. I don't bother to remove them. If you install the JDK, eclipse and Tomcat the way I recommend, they operate isolated. It is possible to create sym links which will include the JDK6 as a listed alternative, but again, I don't do it.

You can remove packages using a GUI, like Synaptic. Search for java, find what you want to remove, and 'unclick' it. You can do it from the command line if you know the package name, like so:
```
sudo apt-get remove *package*
```

---

### Post by strumluff on 2007-01-16
Alright thanks for the assistance. Just so I can understand your method, could you explain why you rename the folder from jdk1.6.0 and what the effects of exporting the JAVA_HOME variable are to the .bashrc file. Does that mean netbeans would need an alias?

Also, I've noticed that in most other tutorials the folder is not renamed but just moved to the usr/lib/jvm/ directory where my current JRE is installed. Without sym links does that mean you can only use JDK6 for development as it is not selected as a JRE for use elsewhere.

I apologize for asking a fair bit that may seem trivial but I'd like to understand the concepts involved here =)

Thanks

---

### Post by WATERBOYsh on 2007-01-16
I've read through a few different things online about installing jdk 6.0 on ubuntu 6.10 and they all seem to be different. I tried one way, <a href="http://ubuntuforums.org/showthread.php?t=332884">This Way</a> and I don't tihnk it work worked. I installed eclipse through the synaptic package manager and it seems someone else in this thread did the same and eclipse didn't realize that the jdk was installed, but regardless it didn't seem to be working so I removed all the files in /usr/java that I had put there. I would like to try <a href="http://ubuntuforums.org/showthread.php?t=332674">this</a> but I am brand new to linux and don't know anything about where or how to configure BASH. Any pointing in the right direction would be greatly appreciated.

---

### Post by phossal on 2007-01-17
The last way of installing Java/eclipse is pretty easy. Just follow the tutorial. The only configuring of *bash* that you *have* to do is  adding an entry to the *.bashrc* file. 

You open that file this way:
```
sudo gedit ~/.bashrc
```

---

### Post by WATERBOYsh on 2007-01-17
Okay I followed your directions and eclipse seems to be happy now, but I can only access it from the terminal. I have the eclipse installed from the repositories so I don't know the path for it to put in the bash config file. I still can't run eclipse from the applications menu, I get the error

> A Java Runtime Environment (JRE) or Java Development Kit (JDK) must be available in order to run eclipse. No java virtual machine was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java

Also, how do I get the java plugin for Firefox to work?

---

### Post by ssavelan on 2007-01-21
How, pray tell do you configure bash in the manner originally described?

---

### Post by ssavelan on 2007-01-21
Indeed... what he said as well...

First I tried, from ubuntuguide.org,

Choose "Java Runtime Environment (JRE) 5.0 Update 10" and click on "Download"
Accept License Agreement 
Download the "Linux self-extracting file"

    * Install the required tool : 

sudo apt-get install java-package

    * Create the Ubuntu package : 

fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin

    * Install the resulting package : 

sudo dpkg -i sun-j2re1.5_1.5.0+update10_i386.deb

Is the ubuntuguide simply not to be trusted?

I got:

biouser@reishi-tsunami:~/Desktop$ fakeroot make-jpkg jre-6-linux-i586.bin 

Creating temporary directory: /tmp/make-jpkg.CcxTZ10409
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

---

### Post by laxmanb on 2007-01-21
OK, here's how i did it...

I followed this guide: [https://www.centricware.org/confluence/display/~alex.yanchenko/Installing+JDK6+on+Debian+Etch+(or+Ubuntu](https://www.centricware.org/confluence/display/~alex.yanchenko/Installing+JDK6+on+Debian+Etch+(or+Ubuntu))

the good thing about this is all apps now detect Java, and you aren't restricted to Eclipse and can freely install Netbeans/jEdit/BlueJ/etc....

To make mozilla show Java Applets... 
a. make a folder called plugins in the .mozilla folder in your home folder( select show hidden folders to see it)

b. you have to make a symbolic link to the Java plugin in the /usr/lib/jvm/jdk1.5.0/jre/plugin/i386/ns7 folder in the /home/<user name>/.mozilla/plugins folder...

complicated sounding, ain't it?? do a google search on how to make a symbolic link, it aint too hard!!

---

### Post by phossal on 2007-01-21
What way *restricts* you to eclipse? And what way prevents other apps from detecting Java?

---

### Post by laxmanb on 2007-01-21
see... i got errors saying that i don't have a JDK installed when i tried to install netbeans...

in the other method, netbeans installed ... so i prefer that one more... just in case it might happen to others... and the other method registers the JRE with linux... so programs other than IDEs are able to use the JRE and enjoy the better performance Java 6 brings...

---

### Post by MadMan2k on 2007-01-21
> **laxmanb said:**
> 
complicated sounding, ain't it?? do a google search on how to make a symbolic link, it aint too hard!!
if youre on edgy you can as well use my backported packages which create that link four you:
[http://www.ubuntuforums.org/showthread.php?t=325182](http://www.ubuntuforums.org/showthread.php?t=325182)

you will also get it automatically in update-alternatives

---

### Post by phossal on 2007-01-22
> **laxmanb said:**
> see... i got errors saying that i don't have a JDK installed when i tried to install netbeans...

I'm glad you're up and running, no matter how you did it. I would encourage you to consider the downside of using a package prepared by an unknown third party. Plus, it's always a good idea to understand your system well enough to be able to use the tools as recommend by the software vendor. For example, Sun does *not*, in any way, recommend using Mr. Mad's package. 

The issue seems to be that you needed to integrate your new Java into your system. That's easy, and *still* didn't require Mr. Max's package, but a basic understanding of your system as a whole. I added a [tutorial about using update-alternatives (including how to add your new Java)]("http://ubuntuforums.org/showthread.php?t=332674"), which is worth looking at even though you're up and running. 

It'll come in handy in the future, and make you a *better* Linux user.

---

### Post by laxmanb on 2007-01-22
Thanks!! i'll look that up... update-alternatives is quite important, esp. if you have multiple java versions!

---

### Post by z600 on 2007-01-28
Thanks phossal! Great instructions! :)

---

### Post by phossal on 2007-01-28
> **z600 said:**
> Thanks phossal! Great instructions! :) You're absolutely welcome. Thanks for taking the time to *say* thanks. :D

---

### Post by allix on 2007-01-28
JDK6 is in edgy-backports. Enable the backports repo in synaptic and install sun-java6-jdk. =)

---

### Post by phossal on 2007-01-28
> **allix said:**
> JDK6 is in edgy-backports. Enable the backports repo in synaptic and install sun-java6-jdk. =)

Yeah, we all know. It took a long time though, and many of us follow the updates from Sun, rather than waiting months for the packages. It's just as easy to go direct, and your source is *Sun*. Besides, unless you *need* a package there are advantages to grabbing the files from the vendors, and disadvantages to using the backports. Congrats to you, if you're up and running. Cheers.

[edit] I've helped a *lot* of people get Java programs up and running. Lately, I've even suggested they use the package in the repos. Most times, though, the number of steps involved in walking them through a Java installation direct from SUN, and then configuring update-alternatives is as easy, fast, and successful as any other method. Plus, there is the added bonus that the users will see an additional side of update-alternatives and how things really work. The package manager is great, but it's a *tool* not a necessity. I believe in teaching a man to fish in addition to guaranteeing him his first catch. ;)

---

### Post by amgeex on 2007-01-28
Hey Phossal, your guide is great! I do prefer your method to installing packages, because now I can install java on ***any*** distribution, not just ubuntu! Thanks!

---

### Post by phossal on 2007-01-28
**Awesome! **That's freedom, *as in liberty*. Thanks for taking the time to say thanks, too. Cheers!

---

### Post by phossal on 2007-02-20
Just a note: I refined the tutorial I had written on manually installing Java directly from SUN into six steps. Pain free, and no waiting for updates in the repositories. The link is in my signature.


> **phossal said:**
> [edit] I've helped a *lot* of people get Java programs up and running. Lately, I've even suggested they use the package in the repos. Most times, though, the number of steps involved in walking them through a Java installation direct from SUN, and then configuring update-alternatives is as easy, fast, and successful as any other method. Plus, there is the added bonus that the users will see an additional side of update-alternatives and how things really work. The package manager is great, but it's a *tool* not a necessity. I believe in teaching a man to fish in addition to guaranteeing him his first catch. ;)

---

### Post by Sethiano on 2007-02-20
Thanks for the quick help!

---

### Post by datajelly on 2008-08-26
Is there anything wrong with using:
```
sudo apt-get install sun-java6-jdk
```

I am only wondering just to make sure that this is the recommended version of Java to use?

---

### Post by tinny on 2008-08-26
> **datajelly said:**
> Is there anything wrong with using:
```
sudo apt-get install sun-java6-jdk
```

I am only wondering just to make sure that this is the recommended version of Java to use?

+1

Install the Sun JDK from the repositories!!! Why make work for yourself???

BTW: For a full Sun Java 6 environment I use...

```

sudo apt-get update
sudo apt-get install sun-java6*

```

Installs the JRE, Java browser plug-in and the JDK.

---

