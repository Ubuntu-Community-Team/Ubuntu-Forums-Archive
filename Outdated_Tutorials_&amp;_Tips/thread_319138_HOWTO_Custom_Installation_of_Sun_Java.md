---
title: "HOWTO: Custom Installation of Sun Java"
date: 2006-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by samjh on 2006-12-15
As a new forum member, I've seen quite a lot of threads asking how to install the latest Sun java JREs and JDKs.  Sometimes instructions are given, other times not.  The official help documentation doesn't really give instructions on installing Sun Java, without using the package from the package repositories.

So I am writing this to provide a one-stop shop for those wanting to install Sun's JRE or JDK on Ubuntu.  This how-to works with both 6.06 and 6.10 versions of Ubuntu, and with JRE 1.5.0_x and 1.6.0, and JDK 1.6 SE.  It also assumes that you run 32-bit x86 architecture systems.  Following these steps will accomplish:
1. JRE installation into your /opt directory, and plugin installation for Firefox.
2. JDK installation into your /opt for Java programming.
3. Setting correct references in /usr/bin for command-line invocation of Java tools.


**Step One - initial download**

Download the linux binaries for Java from Sun's official Java website.
[http://www.java.sun.com](http://www.java.sun.com)

Place the downloaded files in your home folder.  For example: /home/samjh/

**Step Two - installing the JRE**

Open Nautilus (the default Gnome graphical file manager).  Navigate to your downloaded JRE binary.  Right-click on the file, select Properties.  A properties dialog box will open up.  Select the Permissions tab, and tick the box that says to allow the file to run as an executable.  Click OK.

Double-click on the downloaded JRE binary.  A dialog box will appear, asking how to open it.  Select "Run in Terminal" (do not just select "Run").  A terminal window will open with the license agreement.  Keep pressing enter to scroll through the agreement (it takes several seconds if you hold it down).  It will ask if you accept the agreement, so type "y" without quotation marks, and press enter.

The file will unpack itself.  When it finishes, close the terminal window if it doesn't close automatically.

**Step Three - moving the JRE directory to /opt**

Open your terminal.

Navigate to the directory where the unpacked JRE folder is (the folder name should be jre1.5.0_x or jre1.6.0).  If you followed the instructions above, this will be in /home/yourusername/

Type this command (substitute yourjredirectoryname with the actual directory name):```
sudo cp -r ./yourjredirectoryname /opt
```For example:
sudo cp -r ./jre1.6.0 /opt

It will ask for your password.  Type it in and press enter, and the command will copy your JRE directory and its contents to the /opt directory.

**Step Four - create symbolic links in user binary directory**

Stay in your terminal window.  Type the following command to navigate to usr/bin:
```
cd /usr/bin
```
Then type these commands to remove existing java symbolic links (Do NOT type these all on the one line!  Use separate lines for each!):
```
sudo rm ./java
sudo rm ./java_vm
sudo rm ./javaws
```Don't worry if it tells you the files cannot be found.  Ignore them, because it just means that your existing Java installation didn't create the links.

Then type these commands to add new symbolic links (substitute yourjredirectoryname with your actual JRE directory name):
```
sudo ln -s /opt/yourjredirectoryname/bin/java ./java
sudo ln -s /opt/yourjredirectoryname/bin/javaws ./javaws
sudo ln -s /opt/yourjredirectoryname/bin/java_vm ./java_vm
```For example:
sudo ln -s /opt/jre1.6.0/bin/java ./java

**Step Five - create symbolic link to Java plugin for Firefox**

First, use Nautilus, and navigate to /opt/yourjredirectoryname/plugin/i386/ns7 directory.  Right-click on the libjavaplugin_oji.so file, and select Properties, then select Permissions in the dialog window.  Check to see that the owner of the file is you (it should say your user name).

If it says the owner is root, then the plugin will not work for anyone other than root.  You need to type this in terminal to get it to work for you:
```
sudo chmod 755 libjavaplugin_oji.so
```

Now, use the cd command in your terminal to navigate to the /home/yourusername/.mozilla/plugins directory.  Substitute yourusername with your actual user name, and take care to include the full-top (".") in .mozilla. :)
For example:
cd /home/samjh/.mozilla/plugins

(If the plugins directory doesn't exist, then create one.  Feisty Fawn users have reported that the plugin goes to /usr/lib/firefox/plugins instead, so please place your plugin link to that directory instead of the one I've specified.)

Now, command your terminal with this proclamation:
```
ln -s /opt/yourjredirectoryname/plugin/i386/ns7/libjavaplugin_oji.so ./
```

Close any existing Firefox sessions.  Re-start Firefox.
Go to [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) and click on the "Verify Installation" button.  The next page will check your installation for several seconds.  If it then says "We detected your Java environment as follows", then your installation of the plugin was a success.

Now go make love, have a shower, and return when well-rested. ;)  You have successfully installed the Java Runtime Environment. :)

**Step Six - install the JDK**

Repeat Steps Two and Three, but use your downloaded JDK binary instead of the JRE one.

**Step Seven - linking the JDK tools**

Similar to Step Four.

Navigate to /usr/bin using your terminal, and type the following:
```
sudo ln -s /opt/yourjdkdirectoryname/bin/javac ./
```
This will allow the javac command to be run without having to specify the path every time.

Optionally you can also run this:
```
sudo ln -s /opt/yourjdkdirectoryname/bin/jar ./
```But Ubuntu already ships with fastjar already linked, which should be a good enough jar packer.  So linking jar is entirely optional.  I personally use fastjar.

Now go make love, have a shower, and return when well-rested. ;)  You have successfully installed the Java Development Kit. :)

**Uninstalling JRE and/or JDK**

If you are uninstalling the JRE or JDK, you can do it using the terminal like this (where yourjavadirectoryname is the directory you want to remove):
```
cd /opt
sudo rm -r ./yourjavadirectoryname
```

Then navigate to /usr/bin, and do this for JRE...
```
cd /usr/bin
sudo rm ./java
sudo rm ./javaws
sudo rm ./java_vm
```

...or this for JDK...
```
cd /usr/bin
sudo rm ./javac
sudo rm ./jar
```...note that you won't need to remove the link for jar if you didn't make a link during installation.

To remove the firefox plugin, do this:
```
cd /home/yourusername/.mozilla/plugins
rm ./libjavaplugin_oji.so
```

Done! :)

Here endeth this newbie's guide to installing/uninstalling Sun Java, the non-packaged way.


Rationale for installing separate JRE and JDK:
I am a Java programmer.  As such, I have occasionally need to use multiple JDK and even multiple JREs for compatibility testing.  Separating your JRE and JDK installation will allow you to use separate Java build and test environments without affecting your ability to run Java software or applets.  Also, the loss of the JDK will not equal losing JRE functionality, so you have more flexibility over your Java installation.



DISCLAIMER: Your computer configuration may not be fully compatible with the instructions posted above.  The instructions are provided as-is, without any warranty or promise, express or implied, against direct or indirect damages of any kind.  Use these instructions at your own risk.

---

### Post by xyz on 2006-12-15
Glad to see your HowTo's up there!

---

### Post by jruschme on 2006-12-15
Personally, I've always preferred to install Java on Ubuntu using *java-package*.

A quick HOWTO can be found here:

[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation](http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation)

---

### Post by andyanderso on 2006-12-21
Thanks for the how to.  It seems great for those of us who are pretty new to the ubuntu world.  I have a very basic question - where are you finding the binaries for linux on sun's website?  I am having trouble finding the jdk binary...maybe I am just blind or something.

---

### Post by foureight84 on 2006-12-21
> **andyanderso said:**
> Thanks for the how to.  It seems great for those of us who are pretty new to the ubuntu world.  I have a very basic question - where are you finding the binaries for linux on sun's website?  I am having trouble finding the jdk binary...maybe I am just blind or something.

[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

from there choose which ever one you need. then download the self-extracting linux bin. if you are only in need of the runtime environment then look for JRE on the page.

---

### Post by Whhpssh on 2006-12-22
> **samjh said:**
> 
**Step Five - create symbolic link to Java plugin for Firefox**

First, use Nautilus, and navigate to /opt/yourjredirectoryname/plugin/i386/ns7 directory.  Right-click on the libjavaplugin_oji.so file, and select Properties, then select Permissions in the dialog window.  Check to see that the owner of the file is you (it should say your user name).

If it says the owner is root, then your plugin will not work.  You will need to reinstall the JRE again.  This will sometimes occur, although I'm not quite sure why.  It's a rare thing though, so don't fret.

Now, use the cd command in your terminal to navigate to the /home/yourusername/.mozilla/plugins directory.  Substitute yourusername with your actual user name, and take care to include the full-top (".") in .mozilla. :)
For example:
cd /home/samjh/.mozilla/plugins

Now, command your terminal with this proclamation:
```
ln -s /opt/yourjredirectoryname/plugin/i386/ns7/libjavaplugin_oji.so ./
```

Close any existing Firefox sessions.  Re-start Firefox.
Go to [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) and click on the "Verify Installation" button.  The next page will check your installation for several seconds.  If it then says "We detected your Java environment as follows", then your installation of the plugin was a success.


First off, thank you very much for a concise and well-written How-to.  I appreciate the help.

I have a problem with the step I quoted, though.  I have no plugin directory under .mozilla in my home folder.  If I remember correctly, I did a mass installation of a bunch of applications which set up my java plugin and now I'm unable to find the correct location.  I run Firefox 2.0.

Other than that, it looks like both the JRE and JDK are installed.

Any ideas?

---

### Post by dorcssa on 2006-12-23
[I]First, use Nautilus, and navigate to /opt/yourjredirectoryname/plugin/i386/ns7 directory. Right-click on the libjavaplugin_oji.so file, and select Properties, then select Permissions in the dialog window. Check to see that the owner of the file is you (it should say your user name).

If it says the owner is root, then your plugin will not work. You will need to reinstall the JRE again. This will sometimes occur, although I'm not quite sure why. It's a rare thing though, so don't fret[/I]

I have a problem with this. I reinstalled it, and it still says that the owner is root. Maybe I should just change the ownership(chown), and it will solve it?

---

### Post by bodhi.zazen on 2006-12-23
Nice How-to

This thread has been added to the UDSF wiki.

[Custom_JAVA](http://doc.gwos.org/index.php/Custom_JAVA)

---

### Post by victorbrca on 2006-12-23
> **dorcssa said:**
> [I]First, use Nautilus, and navigate to /opt/yourjredirectoryname/plugin/i386/ns7 directory. Right-click on the libjavaplugin_oji.so file, and select Properties, then select Permissions in the dialog window. Check to see that the owner of the file is you (it should say your user name).

If it says the owner is root, then your plugin will not work. You will need to reinstall the JRE again. This will sometimes occur, although I'm not quite sure why. It's a rare thing though, so don't fret[/I]

I have a problem with this. I reinstalled it, and it still says that the owner is root. Maybe I should just change the ownership(chown), and it will solve it?


Same problem here. Would the command bellow help?

```
 sudo chmod 755 libjavaplugin_oji.so 
```


BTW, thanks for the tutorial !!!! :)


Vic.

---

### Post by victorbrca on 2006-12-24
> **victorbrca said:**
> Same problem here. Would the command bellow help?

```
 sudo chmod 755 libjavaplugin_oji.so 
```


BTW, thanks for the tutorial !!!! :)


Vic.

This command has worked for me..... But don't take it from me, I'm just a noob...  :???: 


Vic.

---

### Post by dorcssa on 2006-12-24
By 755, you mean your username, right?

---

### Post by victorbrca on 2006-12-24
> **dorcssa said:**
> By 755, you mean your username, right?

Nope, it's chmod using octal notation... It's a different and faster way, IMHO. Not 100% sure if it's better or worse than the normal way, but it seemed easier for a noob like me.

[Explanation link]("http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation")

[Calculator link]("http://anarka.org/linux/chmodcalc.php")


Vic.

---

### Post by Unterseeboot_234 on 2006-12-26
Great HowTo! I finally realized WHY JRE is a separate download from the Java SDK when there is a JRE already inside the SDK. However, I'm AMD64. The 64-bit downloads do not include the plugin for any browser. So, I learned that from the 64-bit development perspective, I'm left with rigging my own browser with its own configured plug-in. The easy answer for a browser was to let Automatix2 install Swiftfox-32 bit and the links for the plug-ins  which are:

```
/opt/swiftfox/plugins/libjavaplugin_oji.so
/usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

I bookmarked this thread so I can come back to ponder all this. But, in any case, your excellent discussion got my javac to work in terminal. Important when you have two libaries making the java class. I now know why I have the links for which of the two most imporant java folders to run code or run a plug-in.

---

### Post by Asham on 2006-12-27
Great tutorial! Real nice job =D> 

I couldn't find out how to make jar-files runnable though. Instead they are opened by the "Archive Manager"?

---

### Post by Kingsley on 2006-12-31
fix "sudo rm ./java sudo rm ./java_vm sudo rm ./javaws" on your site. if i wasn't careful, i would've deleted sudo and i'm sure most other people won't catch this error.

---

### Post by MrQuincle on 2007-01-09
> **samjh said:**
> **Step Three - moving the JRE directory to /opt**
Type this command (substitute yourjredirectoryname with the actual directory name):```
sudo cp -r ./yourjredirectoryname /opt
```For example:
sudo cp -r ./jre1.6.0 /opt

...

If it says the owner is root, then your plugin will not work.  You will need to reinstall the JRE again.  This will sometimes occur, although I'm not quite sure why.  It's a rare thing though, so don't fret.
That seems default behaviour IMHO. You're copying with a sudo prefix. I suggest the following change: ```
sudo cp -rp ./yourjredirectoryname /opt
```For example:
sudo cp -rp ./jre1.6.0 /opt

The additional "p" will preserve all attributes, also ownership (see man cp).

---

### Post by orangep on 2007-02-11
Thank you VERY MUCH for this tutorial. I've been tearing my hair
out trying to get JRE to work, and this page gave the correct
answers. The Sun page, on the other hand, is just plain wrong,
and their instructions just do not work. And they forget to mention
JAVA_HOME and PLUGIN_HOME, as in how to set them....
Thanks again. My installation now passes the test you mentioned.

---

### Post by gtratter on 2007-03-04
**SAMJH**

I just followed your guide installing JRE & JDK (1.6.0) versions. It worked beautifully.
The install was done on Feisty Fawn 2.6.9-20 generic. 
I found the *plugins* directory for Firefox no longer within .mozilla but in
/usr/lib/firefox/plugins

I am not sure if this is because Feisty installs Firefox 2.0.0.2 or the way I installed. But maybe this bit of info is useful to someone.
Thanks for a great guide!!!!!
G

---

### Post by samjh on 2007-04-01
Wow, I didn't know that so many people used my tute.

Thank you for all the feedback.  I've made a few fixes to the original post.

> **Kingsley said:**
> fix "sudo rm ./java sudo rm ./java_vm sudo rm ./javaws" on your site. if i wasn't careful, i would've deleted sudo and i'm sure most other people won't catch this error.Do you mean that the commands shouldn't be in one line?  If so, I have amended the original post with an instruction to use separate lines for each deletion command.

---

### Post by wingnux on 2008-03-31
I LOVE YOU!!! 

Someone please make this a sticky!

Thank you very much!

---

### Post by samjh on 2008-05-10
Wow.  I'm glad to see this tutorial is still being used. :)

I wrote it when I was still a novice user, so looking back, it could have been better written.  I'll try to do some minor updates with better instructions, as soon as I can commit the time. :)

---

### Post by samjh on 2008-09-09
Update: Minor typo and architecture clarification.

:)

I still haven't had time to test the instructions on a modern Ubuntu release (7.10 and 8.04.x).  If anyone can confirm that they still work, it would be great. :)

---

### Post by WutCake on 2010-03-25
great HowTo. :)

just one question, how do i make it so u can use the "java" file in stuffs like terminal or .sh files without having to use folderdir to it'

example:
/usr/java/jre1.6.0_18/bin/java *javastuff here*
i want that to be:
java *javastuffhere*

get it? :o

---

