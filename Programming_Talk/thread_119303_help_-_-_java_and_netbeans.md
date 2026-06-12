---
title: "help - - java and netbeans"
date: 2006-01-19
forum: Programming Talk
---

### Post by slowlearner on 2006-01-19
here it goes...

i have installed j2sdk1.4.2_10 and jre1.5 which are distributed by sun.. these are the self extracting files;

i want to use NETBEANS for development, so i downloaded it and try installing, it  is also in a self extracting format...
the installer begins by searching for JVM but stops and prompts and error like this "cannot find wizard.inf"

can anybody help me...

or can just anyone tell me how to set the classpath and java_home;; i guess this might be the problem.....

---

### Post by Viro on 2006-01-19
You need to make sure that your Java installation can be found. To accomplish this, you need to set the variables JDK_HOME and JAVA_HOME to point to your Java installation and also update your PATH. 

There are a few ways of doing this, but I personally just add the definitions to .gnomerc. Here's what you need to do.

[LIST=1]
[*]Launch the terminal
[*]type "gedit .gnomerc"
[*]You should add the next few lines to your .gnomerc file:
```

JAVA_HOME=/opt/jdk
JDK_HOME=/opt/jdk
PATH=$JAVA_HOME/bin:$PATH

export JAVA_HOME JDK_HOME PATH

```
[/LIST]

Just log-out and log-in again and you should be able to install Netbeans.

Edit: I forgot to mention that you need to replace the path /opt/jdk with the location of *your* installation of the JDK (not the JRE).

---

### Post by auburn on 2006-02-16
this is an old post but I'll update it for others who search the forums like I did:

howto install netbeans:

1) download and install the latest automatix from [http://beerorkid.com/automatix/](http://beerorkid.com/automatix/)

2) run it and make sure and select Sun jdk from the list
(If anybody wants to add how to use the free sdk pkg that would great.)

3) download the latest netbeans IDE installer from [http://www.netbeans.info/downloads/download.php](http://www.netbeans.info/downloads/download.php)

4) chmod +x TheFileYouJustDownloaded

5) the netbeans installer should open and ask where to install (anywhere you want) and ask where the java jdk app is. Tell it to look in /usr/lib/j2sdk1.5-sun (or whatever the name of the folder that starts with j2sdk...)

---

### Post by abhaysahai on 2006-03-06
Netbeans is now available integrated with Java SDK on Sun Download page. 
It is a single binary file that you need to download and install. 

Enjoy.

---

### Post by mjreged on 2006-03-06
I work with Netbeans and ubuntu on daily basis and this is what i do :

1) download JDK  example:  jdk1.6.0-beta2.bin  into your home folder
2) in terminal run :  ./jdk1.6.0-beta2.bin 
      result :  you will get a folder in home  such as jdk1.6.0/
3) in terminal run : sudo mv jdk1.6.0 /opt
        result : you just moved jdk1.6.0 into  /opt folder  so now /opt/jdk1.6.0 is      the location of the jdk

4) in terminal run : sudo rm /usr/bin/java
     result: remove any link that is in your system path for java so you can replace it with the jdk in /opt
5) in terminal run : sudo ln -s /opt/jdk1.6.0/jre/bin/java /usr/bin
      result : made a link to your new jdk so that it is easy to be found by other programs like azureus or limewire

6 ) dowload the latest snapshot of netbeans ex.  nebeans 6.0 
7) in terminal run : ./nebeans6.0-blahblahblah.bin
      result : netbeans installer will find you jdk and will use it for installation of the IDE
8) at the end of installation you should have an icon on your desktop for nebeans that uses java JDK that you placed in your /opt/jdk1.6.0 folder

Note : jdk1.6.0 is a development build, so is netbeans 6.

in netbeans folder structure you can find a file  ~/netbeans6/etc/netbeans.conf
in there you can also point to a jdk of your choosing 
like this : netbeans_jdkhome="/opt/jdk1.6.0"

have fun .

---

### Post by yager on 2006-03-13
[QUOTE=auburn]
4) chmod +x TheFileYouJustDownloaded

5) the netbeans installer should open and ask where to install (anywhere you want) and ask where the java jdk app is. Tell it to look in /usr/lib/j2sdk1.5-sun (or whatever the name of the folder that starts with j2sdk...)[/QUOTE]

Did all of the above and had to cancel the install because I could not access the  directory that I had planned to put Netbeans.  Now that I have the directory established, Netbeans will not start from this command as it did the first time.

I even deleted the file and downloaded a fresh copy and this did not work either.  Any help would be appreciated.

---

### Post by perbl on 2006-03-21
I am also having some frustrating problems with Netbeans. I recently started using Ubuntu on one of my computers (x86 PC), mostly for java development, which kinda sucks on OS X.

The problem is that everything installs fine (downloaded the bundle from Sun with both Netbeans5 and JDK1.5.0_06), but when I start Netbeans, it displays the splash screen with the progress bars and everything fine, but I will only end up with a window with a title (Netbeans IDE 5.0), while the tray icon says Java. 

So, my question is if anyone here can point me in a direction for locating the cause of the problem :)

---

### Post by weichsel on 2006-03-26
hi perbl!

I have exactly the same problem. Did you solve it yet?

---

### Post by weichsel on 2006-03-26
self answer:
It seems the problem comes from xgl/compiz:
This post has a possible solution
[http://ubuntuforums.org/showpost.php?p=861677&postcount=26](http://ubuntuforums.org/showpost.php?p=861677&postcount=26)

---

### Post by perbl on 2006-03-28
Well, my problem is that I do not run compiz :)

---

### Post by perbl on 2006-03-30
Actually, I have it working now, if I run it on my computer. 

The problem is that I plan to use this machine as a server, and would be able to run the program over an NX connection. This does not work, I still get the same problem, no window decorations, I can even see it in the startup splash screen, the text that tells about what is currently starting up is just a white bar. 

Help is most wanted :)

---

### Post by irfanr on 2006-04-29
> 
7) in terminal run : ./nebeans6.0-blahblahblah.bin
      result : netbeans installer will find you jdk and will use it for installation of the IDE
8) at the end of installation you should have an icon on your desktop for nebeans that uses java JDK that you placed in your /opt/jdk1.6.0 folder

Note : jdk1.6.0 is a development build, so is netbeans 6.

in netbeans folder structure you can find a file  ~/netbeans6/etc/netbeans.conf
in there you can also point to a jdk of your choosing 
like this : netbeans_jdkhome="/opt/jdk1.6.0"



I tried to install Netbeans 5.0 according to your guide. Well, it works just fine for 4.1, but when I tried to install 5.0 the installation stop at process "Creating unistaller ....." and the progress bar showing 98 %. I'm waiting almost half an hour and the progress bar didn't even move from 98%.  What's wrong with it ? It has something to do with the installer ? 

I'm using Ubuntu 5.10 and Sun JDK 1.5.0

---

### Post by mjreged on 2006-05-05
Hmm. that never happened to me...
But if it's stuck on the uninstaller i am sure the files needed to run the app already got placed in your specified location so if you installed nebeans in let's say :
~/apps/netbeans/

so now just navigate to :
~/apps/netbeans/bin/

and double click on the   netbeans.sh
choose to run the script and see if the netbeans will load.

eventually you can create a launcher on desktop by yourself by pointing to 
~/apps/netbeans/bin/netbeans.sh


What i also do sometimes with new installation is that i choose to download the "Platform Independent" package. the app in this case is simply ziped document.  Just unziping it into a folder of your choosing and accessing the 
~/nebeans/bin folder clicking the netbeans.sh will get the up running.
******** if not there is only one explonation ******************
open ~/netbeans/etc/netbeans.conf  check that jdk_home path is set to your JDK

---

### Post by d2klein on 2006-05-23
hi
i try to use netbeans 5.5 beta. it works quite well when i work as root but trying to start netbeans from a user shell results in many io-exceptions (although the ide starts).
i already changed permissions on the appropiate directories but that doesn't solve the problem. installing in user directoy instead of /opt/ doesn't help too.

anyone a idea about that?

i will post the complete error message this evening when im at home ;)

greetings d2

p.s. 
bad english ... i'm from germany

---

### Post by biffta on 2006-06-16
I've just setup netbeans on my dapper install of Kubuntu. It all works fine but it uses that god awful metalic theme and the fonts make my skin crawl!
I have tried editing the **netbeans/etc/netbeans.conf** line to
> netbeans_default_options=”-J-Xms128m -J-Xmx256m -J-XX:PermSize=32m -J-XX:MaxPermSize=96m -J-ea -J-DuseGtk=true”
But that doesn't change anything. 

Has anyone encountered this and found a fix? 

Thanks for reading!

Dave.

---

### Post by mjreged on 2006-11-13
The General rule is not to install netbeans in root owned folders. Instead  you should install in your home folder of your choosing.  

JDK should be installed under system files like /opt  or  /usr/share   etc...

there is no reason to run Netbeans as root.


Generally, the most important advice i can give is to make sure that netbeans  does not invokes the GNU JAVA implementaion. 

That issue can be solved using many different ways :
1) if GNU /usr/bin/java  exists  - remove it and link SUN java in it's place. you can check if you have GNU JAVA by inputing command java -version 


2) place JAVA_HOME=/opt/jdk1.5.0 in the  /etc/environment file and add /opt/jdk1.5.0/bin to  PATH= ;
3) open ~/netbeans/etc/netbeans.conf  and specify the location of the JDK there.

any of the 3 examples should take care of  JAVA being accessable to applicaitons.  you can do all 3 if you like.


TIP : if you want to skin NETBEANS , to use GTK wigets i would recommend for you to get JAVA JDK 6  since this version uses native wigets instead of emulation.  and append a flag in the ~/netbeans/etc/netbeans.conf  like this:

netbeans_default_options="-J-Xms128m -J-Xmx256m -J-XX:PermSize=128m -J-XX:MaxPermSize=256m -J-Xverify:none -J-Dapple.laf.useScreenMenuBar=true -J-XX:+UseConcMarkSweepGC -J-XX:+CMSClassUnloadingEnabled -J-XX:+CMSPermGenSweepingEnabled **-laf com.sun.java.swing.plaf.gtk.GTKLookAndFeel**"
result :
[ATTACH]19296[/ATTACH]




if you like to use a custom Lnf like JGOODIES plastic, add this :

-cp:p /home/martin/dev/LOCALCVS/lib/plastic.jar -laf com.jgoodies.looks.plastic.PlasticXPLookAndFeel


So what do you think ???

---

