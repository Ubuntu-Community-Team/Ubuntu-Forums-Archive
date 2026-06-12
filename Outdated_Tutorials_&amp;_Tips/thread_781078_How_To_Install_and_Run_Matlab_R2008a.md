---
title: "How To: Install and Run Matlab R2008a"
date: 2008-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by jweber on 2008-05-04
[COLOR="Red"]NOTE: This guide is written for Ubuntu Hardy with Compiz enabled and Sun Java version 1.0.6_06 installed. I did not devise all of the techniques employed in this guide but have made my best efforts to acknowledge those who did.[/COLOR]


**[SIZE="4"]Before Starting[/SIZE]**

Ensure that you have the current Sun Java release installed (currently version 6). You can check this by opening a terminal (Applications-> Accessories->Terminal) and typing the following:
```
java -version
```
Which, assuming you have the current version installed, should output something like this:
```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

```
If you receive the above output, things should be in order to start the installation and you can move on to the next section. Unfortunately, properly installing Java is beyond the scope of this guide; for instructions on how to install Java you will have to search the forums. 

[COLOR="Red"]NOTE: It is important that you have the Java version 6 or newer installed for this guide to be useful, some of the code will NOT work with version 5 and could keep Matlab's window contents from being shown. The following workaround for running applications with Java version 5 and Compiz does NOT work for version 6:[/COLOR]
```
export AWT_TOOLKIT=MToolkit
``` 

**[SIZE="4"]Basic Matlab Installation[/SIZE]**

Now for the actual installation of Matlab, be sure you have the Matlab installation media intended for UNIX. First insert the Matlab DVD into your computer, the DVD should be automatically mounted. Open the terminal (Applications-> Accessories->Terminal) and navigate to the root directory of the DVD. This can be accomplished on most computers by typing the following:
```
cd /media/cdrom
```

You can verify that you are in fact currently in the DVD's root directory by typing the following:
```
ls
```
Which will list all of the files and folders in the current directory. For the Matlab R2008a DVD, ls outputs the following:
```

install		       inst_doc.pdf  mac_install_guide.pdf  update
InstallForMacOSX.app  license.txt   readme.txt		    utils

```

Now the DVD is mounted and you are in its root directory. The install script needs superuser privileges in order to copy files to certain parts of the filesystem. In order to run the install script with elevated privileges, type the following into the terminal:
```
gksu ./install
```
This will start the installer; you will be prompted for your preferred method of installation and for the "Matlab root directory location." This is where Matlab will be installed, the Matlab installation guide recommends you install Matlab to /usr/local/matlabR2008a and warns you not to install in the same directory as a previous release, but the choice is yours. Once you have chosen a installation directory, a progress bar signifies the beginning of the actual copying of files. Once it's finished you will be prompted to locate a license file which concludes the installation. Admittedly, there is nothing groundbreaking here, the more useful stuff comes in the next section.

**[SIZE="4"]Coaxing Matlab Into Running[/SIZE]**

This section is really the reason I set out to write this How To, hopefully it will be useful to someone. The two main problems which I ran into when I first installed Matlab are listed below.

**Problem 1:**
Matlab doesn't start, the splash screen comes up but Matlab never actually runs. I do not know why this problem occurs but the solution was posted on another thread, you can find it [here]("http://ubuntuforums.org/showthread.php?t=444144&highlight=awt_toolkit&page=2"). It comes from karel.007 and is as follows:
```
mv $MATLAB/sys/java/jre/glnxa64/jre1.5.0/lib/amd64/motif21/ $MATLAB/sys/java/jre/glnxa64/jre1.5.0/lib/amd64/motif12
```
Where $MATLAB is the directory you specified in the installation above, you may need to have superuser privileges to accomplish this for files not in your home directory. Running the command with superuser privileges would look like the following:
```
sudo mv $MATLAB/sys/java/jre/glnxa64/jre1.5.0/lib/amd64/motif21/ $MATLAB/sys/java/jre/glnxa64/jre1.5.0/lib/amd64/motif12
```

**Problem 2:**
Matlab occasionally stops taking input form the keyboard. In my case this happened whenever the help window was opened. To solve this problem, we must undo the workaround for Java 5. The workaround gives the system variable AWT_TOOLKIT the value MToolkit. You can check to see what the current value is by entering the following:
```
echo $AWT_TOOLKIT
```
More than likely the above command will output:
```
MToolkit
``` 

You can temporarily erase the value of the system varible by opening the terminal (Applications-> Accessories->Terminal) and typing the following:
```
unset AWT_TOOLKIT & matlab

```
If the above code opens Matlab and runs it to your satisfaction, you can make this change permanent by editing the script that starts Matlab. To do this, first open the terminal and navigate to Matlab's bin directory. You can do this with the following:
```
cd $MATLAB/bin/
```
Again, $MATLAB is Matlab's root directory and should be replaced with the installation directory specified above. Once in the bin directory you need to open the matlab script which runs Matlab. You can do this with your favorite editor, in this case the code below opens it in gEdit for simplicity.
```
gedit matlab
```
Once you have the matlab script open, add the following line just below the header ~line 181:
```
unset AWT_TOOLKIT
```
Your matlab script should look something like the following:
```
# Copyright 1984-2007 The MathWorks, Inc.
# $Revision: 1.100.4.47 $  $Date: 2007/11/12 22:52:38 $
#__________________________________________________________________________
#

   unset AWT_TOOLKIT

# Enable proper operation on Windows when using a UNIX-compatible shell
```

**[SIZE="4"]Running Matlab[/SIZE]**
In order to run Matlab from the GUI, you must use the -desktop parameter, making the command to run Matlab:
```
matlab -desktop
```

**[SIZE="4"]That's All![/SIZE]**
You should, hopefully, now have a completely functional Matlab installation!

---

### Post by slaanco on 2008-05-05
Im tryining to get Matlab R2007b running under linux, but for some reason I can start it, but the GUI is blank (splash loads everything looks fine). Im using new ubuntu 8.04. Did anyone get passed this? 

everything works fine with: 
matlab -nojvm

but GUI seems dead.

---

### Post by GLRenderer on 2008-05-07
Hi
    It seems that the Matlab GUI can't run in the new Sun Java 1.6. Every single time I tried to run the interface I've gotten the same assertion error.

XXXX@Solaria:/opt/Matlab/bin$ ./matlab
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5a65767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb5a658b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb5dd11bd]
#3 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa06d176e]
#4 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa06776e6]
#5 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa067792d]
#6 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa0677b38]
#7 [0xadc69b7a]
#8 [0xadc63a7b]
#9 [0xadc63a7b]
#10 [0xadc61157]
#11 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb28f48ec]
#12 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb29e3378]
#13 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb28f471f]
#14 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb294cebb]
#15 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb2ee72cd]
#16 [0xadc6942b]
#17 [0xadc639a4]
#18 [0xadc61157]
#19 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb28f48ec]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5a65767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb5a6581e]
#2 /usr/lib/libX11.so.6 [0xb5dd0518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb5dc70a6]
#4 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa0676573]
#5 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa0676804]
#6 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa0677a74]
#7 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa0677b38]
#8 [0xadc69b7a]
#9 [0xadc63a7b]
#10 [0xadc63a7b]
#11 [0xadc61157]
#12 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb28f48ec]
#13 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb29e3378]
#14 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb28f471f]
#15 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb294cebb]
#16 /opt/Matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb2ee72cd]
#17 [0xadc6942b]
#18 [0xadc639a4]
#19 [0xadc61157]

The only way I managed to run the GUI is by running the application from a terminal and accepting the assertion errors.

---

### Post by jweber on 2008-05-08
@slaanco

A few things you might check:

1 - Does it work without compiz enabled? If so you may check that you have the java workaround enabled. This can be done with the compiz config settings manager by going to the "Utility" section, clicking workarounds and then clicking the "Java Window Fix" box.

2 - You can try adding "AWT_TOOLKIT=MToolkit" in your matlab script instead of "unset AWT_TOOLKIT" although this specifically caused problems for me.

3 - You can also try adding "export MATLAB_JRE=/usr/lib/jvm/java-6-sun/jre" or "export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre" below "unset AWT_TOOLKIT" as sugested by neurostu and Bungler on [this]("http://ubuntuforums.org/showthread.php?t=444144&highlight=matlab") thread and MaximusTG on [this]("http://ubuntuforums.org/showthread.php?t=467133&highlight=matlab") thread. Make sure the path you use actually points to the jre folder.

That's about all of the solutions I've seen, I tried a lot of combinations of solutions to write this guide so you may have to mess with it a bit.

@GLRenderer

I forgot to mention that to run Matlab from the GUI you have to run ```
matlab -desktop
``` I will add this to the guide.

---

### Post by reg2117 on 2008-07-07
Article great help for installation.
For updating java to version 6 the following thread is useful: [[COLOR="Blue"]java 6 update 6[/COLOR]]("http://ubuntuforums.org/showthread.php?t=848683")

---

### Post by toolisima on 2008-10-13
Hi, I have the problem that you describe about matlab not really starting, only the splash screen appearing and disappearing.
I tried what you said, but it didnt work.
 mv /usr/local/matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21 /usr/local/matlab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif12

Note that I am trying to install an older version of matlab so I had to look for the motif21 folder which is under i386 and this is different from what you posted here. I am installing Matlab R2006b, which I installed before in another laptop running Ubuntu (like a year ago) and now I cant remember exactly what I did last time but as soon as I installed it, it worked out perfectly.

Please help!

(I am sure I have java up to date)

---

### Post by jweber on 2008-10-15
I assume that you first tried to install matlab without any of these instructions, that being said I now have Java version 1.6 and matlab runs without any modifications. You may try updating to that version or if that is not an option, you may want to try the suggestions in post #4.

---

### Post by toolisima on 2008-10-17
Ok finally I managed to make matlab R2007b work perfectly!!
So yeah, I didn't quite follow instructions here but it helped me understand better what to do...so thanks.
What I did in case someone is curious, is unistall the whole thing, and installed again. 
The instructions I have required me to run lmstart from a user other than root...which now I cant remember if I did before, but I did now.
Then ran matlab and at this point the splash screen  came up and matlab worked except that I could not see anything!
But, I found how to fix it here: 
[http://ubuntuforums.org/showthread.php?t=802919](http://ubuntuforums.org/showthread.php?t=802919)
and now it works just fine!

---

### Post by jweber on 2008-10-19
I'm sorry I couldn't be more helpful though I am glad to hear that you got it working.

---

### Post by s53ostlund on 2008-11-06
I also had the locking assertion failure. I resolved it as follows

1) Locate your matlab installation directory. In my case
    it was /usr/matlab.

2) find the current  jre libraries on your machine
    in my case it was  /usr/lib/jvm/java-6-sun soft linked
    to /usr/lib/jvm/java-6-sun-1.6.0.07. 

3) as superuser go to matlab installation directory
$ su
$ cd /usr/matlab/sys/java/jre/glnx86
$ mv jre1.6.0 jre1.6.0.bak
$ ln -s /usr/lib/jvm/java-6-sun/jre jre1.6.0

If that does not work its obviously easy to undo these steps.

---

### Post by Captain_Falafel on 2009-08-19
it seems like I cannot even start the installation.. I'm using Jaunty.. I've mounted and gone into the directory where the install file is.. but when I run
```
gksu ./install
```
nothing happens.. I'm prompted to put in my password.. then I wait.. and wait.. and wait.. nothing happens.

I'm using Java version:
```
$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK Server VM (build 14.0-b08, mixed mode)

```

---

### Post by ak9394 on 2010-01-14
Try the following code, it fixed the problem for me.

sudo update-java-alternatives -s java-6-sun

---

