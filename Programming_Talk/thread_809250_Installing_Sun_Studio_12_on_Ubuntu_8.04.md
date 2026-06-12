---
title: "Installing Sun Studio 12 on Ubuntu 8.04"
date: 2008-05-27
forum: Programming Talk
---

### Post by fsleeman on 2008-05-27
When I try to install Sun Studio 12 with the graphical installer, I get a message half was through that Java is not installed. In my case Sun's Java was already installed. I tell the Sun Studio installer to do the update and it finished what it was doing. After the install is done, I found that the Sun Studio executable is missing, so it looked like the installation did not work.

After this I uninstalled Java and Netbeans and started the system prep tool, which correctly said I was missing netbeans and java. I had the system prep tool install netbeans successfully but I get this message when trying to install java:

error: Failed dependencies:
	glibc >= 2.1.2-11 is needed by jdk-1.5.0_09-fcs.i586
	sh-utils >= 2.0-1 is needed by jdk-1.5.0_09-fcs.i586
	fileutils >= 4.0-8 is needed by jdk-1.5.0_09-fcs.i586
	gawk >= 3.0.4-1 is needed by jdk-1.5.0_09-fcs.i586
	textutils >= 2.0-2 is needed by jdk-1.5.0_09-fcs.i586
	/bin/sh is needed by jdk-1.5.0_09-fcs.i586

I know that at least some of those packages are newer than the versions listed above. My system is current as of 5/23/08 (4 days ago). 

Have anybody been able to install Sun Studio 12 on Ubuntu?

---

### Post by xlinuks on 2008-05-27
Try out the .tar.gz file, you don't need to install it, you just unzip it and put result where you wish your app to be, generally in some subdirectory of your home directory. I did so and it worked. After that you have to find what's the file you have to run to start the IDE, I don't remember since I deleted the studio but you'll find the path to it in the readme file.

---

### Post by fsleeman on 2008-05-27
The only packages I can find are .tar.bz2. I unziped the package but its only a collection of installers like .bin and .rpm, there is no sunstudio executable. Running the system prep gives me the save error.

Where did you find the package that you used? I would rather install the application so others can use it but right now I would be ok getting it to run at all.

---

### Post by xlinuks on 2008-05-27
Please have a look at the screenshot, does it answer your question?

---

### Post by fsleeman on 2008-05-27
Thanks that is what I was looking for, I can get the program run from that package.

Does anybody know how to get this stuff correctly installed? It looks like some sort of environmental variable or path problem.



Trying to run the installers give me this error:
The Sun Studio installer requires a compatible Java runtime to be installed on the system, but none were found. 
 
These Java runtimes were found: 
 
/bin/java
 
These Java runtimes are compatible with the Sun Studio installer: 
 
JDK1.4.2 
JDK1.5 


My varibales are:
$JDK_HOME /home/fsleeman/sun/jdk/jdk1.6.0_06
$PATH /home/fsleeman/sun/jdk/jdk1.6.0_06/bin
$JAVA_PATH /home/fsleeman/sun/jdk/jdk1.6.0_06/jre/bin

Running 'which java' gives me: /home/fsleeman/sun/jdk/jdk1.6.0_06/bin/java

Are my setting wrong or have I left something out?

---

### Post by xlinuks on 2008-05-27
Actually it's installed correctly unless you mean something else.
It's like the nightly builds of Firefox you only unzip it and use it, if you wish to create some link on the Desktop or some other bells and whistles you have to do that by hand.
If there's some actual problem I would suggest posting details so that others can investigate, but before doing that make sure you read the readme files first.

---

### Post by fsleeman on 2008-05-27
I will agree that it appears that the program is work ok as is. However I am wondering what their graphical installer is for if it is not necessary. Is there any reason I should be concerned that the installer does not like or could not find my java install? If everything is really ok I will just manually copy the files to the correct directory.

---

### Post by xlinuks on 2008-05-27
Generally it's about not getting support from Sun, thus as such for you as a programmer it prolly won't matter much:
```

If you install the Sun Studio 12 software using the Sun Studio 12 tarfile, your installation is unsupported, and you will not be able to apply Sun Studio product patches.

```
For more info go back to the page where you have 2 options (tar/package) and read the difference between them.

---

### Post by fsleeman on 2008-05-29
The one thing I have found that does not work in Ubuntu with either Sun Studio 12 for Linux or Sun Studio Express is the GUI dbx debugger. I get this message when I try to debug an executable:

(dbx) debug /home/fsleeman/cvs/rtrcf1/appl/demo/tstbench_image 
Reading tstbench_image
Reading ld-linux-x86-64.so.2
Reading libstdc++.so.6
Reading libm.so.6
Reading libgcc_s.so.1
Reading libc.so.6

dbx: internal error: signal SIGSEGV (no mapping at the fault address)
dbx's coredump will appear in /tmp
dbx terminated

Has anybody been able to run the debugger in Ubuntu? This seems work fine in the supported CentOS.

---

### Post by xlinuks on 2008-05-29
Unfortunately I can't help here, however I'm curious why are you willing to use Sun Studio 12 instead of Eclipse/Netbeans/Something else?

---

### Post by fsleeman on 2008-05-29
Most of the code I write will be run on Solaris machines although the code runs fine on Linux. I am using Linux on my desktop instead of Windows + X-Win32 as a matter of convenience. I can export the X session of Sun Studio on one of the Sun machines but its a little bit slow over the network, especially if somebody is running a batch job. 

I want to still use Sun Studio because I know how to use it, the interface is easy to use, the graphical debugging tool is easy to use, and everybody on the project can use the same project files in Linux and Solaris. I know there are other C++ IDEs out there but I have not been terribly impressed with them. Kdevelop works but it has an Open Source quality interface (i.e. messy). I have looked at Eclipse a little bit but haven't spend enough time to determine how easy it is to use. Does netbeans have C++ support now?

---

### Post by xlinuks on 2008-05-29
haha "an Open Source quality interface (i.e. messy)"

As to NetBeans, yes, and it's a lot more intuitive & friendly than I've experienced on other IDEs not to mention the other features.
There's even an option to download NetBeans with C++ integrated and it's only 14MB !! How do you like that? For Eclipse you gotta download like 50MB and for SunStudio like 200 :)
There's the Tools->Plugins from where you can _very_ easily (like in Ubuntu) install any other plugins you wish, like for mobile development, web, PHP, Python.. lots..
Sun is really done a good job of improving it, but I expect more to come!
Have a look here:
[http://download.netbeans.org/netbeans/6.1/final/](http://download.netbeans.org/netbeans/6.1/final/)

---

### Post by fsleeman on 2008-05-30
Thanks for the suggestion I will definitely check out NetBeans. I have used NetBeans for Java development before and have been happy with it, especially for the price.

---

