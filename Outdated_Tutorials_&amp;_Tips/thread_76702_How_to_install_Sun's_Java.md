---
title: "How to install Sun's Java"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Adamal on 2005-10-15
Since I haven't seen any how to's on how to install Sun's java (Any Version) I thought I'd write up a little how to.

First you will need to add all the extra repositories for Ubuntu.  (ie Multiverse, Universe...) Please see other how to's on how to do that.

Now go to Sun's website [http://java.sun.com](http://java.sun.com) and select the java jdk or jre that you want.  In my case I needed 1.4.2 so I downloaded j2sdk-1_4_2_09-linux-i586.bin.

Then run the following commands from the terminal:

First install the required packages:
**sudo apt-get install fakeroot  java-package java-common**
Create the Deb file for the install:
**fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin**
Install The deb file
**sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb**
Now make Sun's java the default by running this command and selecting it.
**sudo update-alternatives --config java**

I hope that helps.

[COLOR="Red"]The instructions above are dated, please do not use them.  Use the following instead: [/COLOR]
Execute one of the following:
**sudo apt-get install sun-java6-jdk** - For the JDK (Developer)
**sudo apt-get install sun-java6-jre** - For the JRE (User)

---

### Post by Arktis on 2005-10-15
Edit: removed alternate method and added to it's own thread. ;)  I also mentioned here that I didn't see java-package in the repos.

---

### Post by Adamal on 2005-10-15
Yes java-package is in the repositories.  Here is my sources.list

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse


---

### Post by bored2k on 2005-10-15
The above is not the default sources.list. We should assume the user is starting from zero ;).

---

### Post by Adamal on 2005-10-15
Re-read my first post.  You will see that I stated that you will need to add the extra repositories.

---

### Post by Arktis on 2005-10-15
Yeah, sorry about that.  I finished editing up my alternate method if you want to check that out.  'Twas an educational experience... probably nobody will use it. :rolleyes:

---

### Post by odie5533 on 2005-10-16
I get the following error:
```
fakeroot make-jpkg jdk-1_5_0_05-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXV5OMN4
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
```

---

### Post by bionnaki on 2005-10-16
just curious.
how would one uninstall this?

---

### Post by noxfu on 2005-10-16
[QUOTE=bionnaki]just curious.
how would one uninstall this?[/QUOTE]

```
dpkg -l |grep -i java
```

You will see that "sun-j2re1.5" is the package you're looking for.

```
sudo apt-get remove sun-j2re1.5
```

That's it.

---

### Post by kvidell on 2005-10-16
Why are we using fakeroot and not sudo? Or am I confused as to what fakeroot is/does?
- Kev

---

### Post by comradevik on 2005-10-16
[QUOTE=kvidell]Why are we using fakeroot and not sudo? Or am I confused as to what fakeroot is/does?
- Kev[/QUOTE]

running as root will mess it up

I've succesfuly installed java following the Ubuntu 5.10 starter guide in System>Help 
but i could not get the mysql connector installed properly

---

### Post by Arktis on 2005-10-16
Yeah, just TRY using sudo... it won't let you. Heheh. :D

---

### Post by RastaMahata on 2005-10-16
[QUOTE=comradevik]running as root will mess it up

I've succesfuly installed java following the Ubuntu 5.10 starter guide in System>Help 
but i could not get the mysql connector installed properly[/QUOTE]
I'f you're talking about tomcat... edit /etc/tomcat4/policy.d/04webapps.policy
add this to the end of the file:```
permission java.net.SocketPermission "127.0.0.1:3306", "connect,resolve";
permission java.util.PropertyPermission "file.encoding", "read";
};
```That will solve it, I hope.

---

### Post by t2kburl on 2005-10-16
[QUOTE=odie5533]I get the following error:
```
fakeroot make-jpkg jdk-1_5_0_05-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXV5OMN4
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
```[/QUOTE]


Same here   any ideas???

---

### Post by comradevik on 2005-10-16
[QUOTE=t2kburl]Same here   any ideas???[/QUOTE]


goto system>help>Ubuntu 510 starter guide, applications, java

that HOWTO worked well for me

---

### Post by t2kburl on 2005-10-16
[QUOTE=comradevik]goto system>help>Ubuntu 510 starter guide, applications, java

that HOWTO worked well for me[/QUOTE]
I'm in kubuntu and I see no starter guide in the KDE help specific to 5.10
If you could tell me where the file is that your path points to, Maybe I could find it there

---

### Post by comradevik on 2005-10-16
#

Make sure the multiverse repository is enabled. (See How do I add Universe and Multiverse?)

Go to [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) and click on “Download JRE 5.0 Update 4”. **Ensure you do not choose the link with the NetBeans bundle.**

You must first accept the licence, then click on “Linux self-extracting file” (jre-1_5_0_04-linux-i586.bin). Save this file to your hard drive.

apt-get install java-package

chmod +x jre-1_5_0_04-linux-i586.bin

fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin

dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb


do this but use the jdk 5 update 5 file instead

remmeber the java-package step

---

### Post by t2kburl on 2005-10-16
thanks ... the fakeroot step gives me the above error

I tried the non-repo method from another thread and it works now  :)

---

### Post by Adamal on 2005-10-16
Here is where I gathered most of the info for this how to:
[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

Hope that helps

---

### Post by riokerr on 2005-11-10
Hi, I've installed installed sun's version of java 1.5.0 and later blackdown's 1.4.2... after removing the links for mozilla, firefox and opera.... I added the multiverse repository and installed the j2re1.4 package and the java plugin package for mozilla browsers...

In all cases when I load a game on Yahoo it crashes my browser.  The only change is from installing the j2re package on multiverse is that firefox and opera recognise the java plugin....

The computer is running the amd64 architecture version.  If anyone can give me any tips I'd be very appreciative... I've read the posts and tried linking the files and what not... nothing seems to work...  :(   

Thanks in advance,

John

---

### Post by orangejon on 2005-12-01
Kev, the "root" in fakeroot refers to the root of the filesystem, not the superuser.  In short, fakeroot fools a program into thinking that it is writing into the root of the filesystem, when in fact it's writing to some subdirectory.

---

### Post by saivert on 2005-12-04
I have followed the guide in this threads starting post, but JAVA plugin does not load in Firefox. I have checked /usr/lib/mozilla-firefox/plugins and it contains symbolic links to java plugin in /usr/lib/mozilla/firefox which in turn is links to the plugin in /usr/lib/j2re1.5-sun/plugin/i386/ns7. How to make java plugin work?
Do I have to install the java plugin package even though the plugins are already there? I am a n00b. sorry!!

---

### Post by taiidani on 2005-12-05
I'm getting stuck on the same part as many of the other people in the thread, at the part where it says:
'Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.'

But I also get the text:
'dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)'

And I get it quite a few times. I tried using the DEB_BUILD_GNU_TYPE=i386-linux prefix but got the same problem.
Any suggestions?

---

### Post by ashrack on 2005-12-08
[QUOTE=taiidani]I'm getting stuck on the same part as many of the other people in the thread, at the part where it says:
'Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.'

But I also get the text:
'dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)'

And I get it quite a few times. I tried using the DEB_BUILD_GNU_TYPE=i386-linux prefix but got the same problem.
Any suggestions?[/QUOTE]
Get the same thing during installation. Any way to fix it?
btw, U=Im using this guide [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java)

---

### Post by Rackerz on 2005-12-09
dpkg-deb: building package `sun-j2re1.5' in `/tmp/make-jpkg.XXXXeJ2dUu/sun-j2re1.5_1.5.0+update06_i386.deb'.

I'm basically there, it seems to freeze on doing this bit everytime.

---

### Post by sandynata on 2006-03-08
i've already follow your instruction, but when i use this command to select the default java
# update-alternatives --config java
i did'nt see the installed package .. i'm sure i installed correctly, 
i can see the java version with 
# java --version

also i can see the with this
# dpkg -l | grep -i java

so what's the problem?

i'm newbie :D

---

### Post by sandynata on 2006-03-08
[QUOTE=sandynata]i've already follow your instruction, but when i use this command to select the default java
# update-alternatives --config java
i did'nt see the installed package .. i'm sure i installed correctly, 
i can see the java version with 
# java --version

also i can see the with this
# dpkg -l | grep -i java

so what's the problem?

i'm newbie :D[/QUOTE]

problem solved! \\:D/

---

### Post by groundpounder on 2006-03-09
I'm having the same problem - the firefox plugin won't install.  I've installed Java twice per [http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php).  I'd like to try the method from this thread or the System>Help method, but I have a very basic question that applies to both:  where do I save the .bin file??  :oops:

---

### Post by groundpounder on 2006-03-09
Nevermind, I got it.  Used the the process in this thread, just had to substitute 6 for 5 in a couple places, as the latest download is update 06.  Thanks a lot for the help!

---

### Post by TylerH on 2006-03-09
Hey guys

trying to follow the instructions. I have multiverse enabled but whenever I do:
sudo apt-get install fakeroot java-package java-common

it says: Couldn't find package java-package

and so when I try to do:
fakeroot make-jpkg jdk-1_5_0_06-linux-i586.bin

i get: /usr/bin/fakeroot: line 150: make-jpkg: command not found

Any ideas?

---

### Post by dolson on 2006-03-10
You need to enable universe/multiverse repositories.

---

### Post by Kadin2048 on 2006-04-16
I thought I would just add, in case it helps anyone else who is trying to install Java on a headless system (via SSH, in my case), that the only way I could find to easily download the BIN file was to use Lynx. (I couldn't figure out the direct URL to grab with curl, it's like Sun is intentionally hiding it.)

So I went and opened this in Lynx:
[http://jdl.sun.com/webapps/download/AutoDL?BundleId=10336](http://jdl.sun.com/webapps/download/AutoDL?BundleId=10336)
This is the 1.5.0 update 6 self-extracting file.

And it allowed me to download the 15MB .bin file on my remote machine. Kind of annoying to have to install Lynx just to get the file...but I couldn't think of an easier way to do it (without downloading it onto my local machine and then sending it to the remote one via scp or something).

The links to the various "download bundles" are from this page, in case the above link gets broken at some point:
[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
I just copied the URL from my browser and pasted it into Lynx in my SSH session, then let it download and save the file.

Aside from this small annoyance, the procedure seems to have worked perfectly for me. Thanks!

---

### Post by opiston on 2006-04-19
Hi Adamal,

I just finished installing jdk 5.0 update 6 with your step by step instruction.
Thanks a lot!

opiston

---

### Post by Blacktalon on 2006-04-19
Hello,

I am new to linux and java.  I have done a few programs now in class and I was trying to view them at home but it appears that my current java is out of date and that I need a java sdk 1.5 from sun.  Does anyone know the link and how I can get it installed on my mechine?



Thanks,
  Blacktalon8)

---

### Post by Gylu on 2006-04-20
when I try to install from the tut  [here]("http://help.ubuntu.com/starterguide/C/ch03s02.html") I this a few errors.  I am new to a lot of this but I have tryed to find some info on this and I have not seen anything addressing this as of yet.

```
Removing temporary directory: done
joe@ubuntu:~/Desktop$ dpkg -i sun-j2re1.5_1.5.0+update06_amd64.deb
dpkg: requested operation requires superuser privilege
joe@ubuntu:~/Desktop$ sudo dpkg -i sun-j2re1.5_1.5.0+update06_amd64.deb
Password:
dpkg: status database area is locked by another process
joe@ubuntu:~/Desktop$

```

any words on this would help.  thanks -Gylu-

---

### Post by IsKall on 2006-04-23
when I tryied to do this
sudo apt-get install fakeroot java-package java-com mon

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package

have it something with this repositories?

---

### Post by mleyden on 2006-04-28
[QUOTE=odie5533]I get the following error:
```
fakeroot make-jpkg jdk-1_5_0_05-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXV5OMN4
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
```[/QUOTE]

Check out this page:
[https://wiki.ubuntu.com/RestrictedFormats?action=show#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats?action=show#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

and try:
DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

Worked for me!

---

### Post by djbwhizz on 2006-04-29
HI guys..

i've been trying to install java according to the steps u all told earlier. however, this error keeps on repeating everytime i use the fakeroot command...

```
dpkg-deb: building package `sun-j2re1.5' in `/tmp/make-jpkg.XXXX6DUhyk/sun-j2re1.5_1.5.0+update06_i386.deb'.
    copy sun-j2re1.5_1.5.0+update06_i386.deb into directory /usr/java/
cp: cannot create regular file `/usr/java/sun-j2re1.5_1.5.0+update06_i386.deb': Permission denied

Aborted (/usr/java/).
```

when this happen, i could not install it. This error came up when i tried to install it...

  ```
dpkg: error processing sun-j2re1.5_1.5.0+update06_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-j2re1.5_1.5.0+update06_i386.deb
```

What went wrong.. pls help me out ere since im really new to linux system...

thanx..

---

### Post by aldacron on 2006-04-30
[QUOTE=IsKall]when I tryied to do this
sudo apt-get install fakeroot java-package java-com mon

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package

have it something with this repositories?[/QUOTE]

I'm having this same issue. I have enabled multiverse/universe repositories successfully, but java-package is not showin up anywhere. Has it been removed altogether? Is there an alternative download location?

---

### Post by djbwhizz on 2006-04-30
Hey guys... can somebody help me out ere wif this java problem.. i sorta need to haf java installed in my ubuntu box.. coz im in uni and learning programming in Java now.. help me out pls...

---

### Post by Mercuris on 2006-05-13
I downloaded jre-1_5_0_06-linux-i586.bin

I have tried all of these:
  sudo apt-get install j2re1.4 (couldn't find j2rel.4)

  chmod +x jre-1_5_0_06-linux-i586.bin (worked)

  sudo apt-get install fakeroot java-package java-common (couldn't find package java-package) Multiverse is enabled
 
  fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin  
 ( mkdir: cannot create directory `/etc/.java': Permission denied
  ./jdk-1_5_0_06-linux-i586.bin: line 507: /usr/share/mime-info/java-archive.keys: Permission denied)
 
  DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin (same)

What else can i possibly do? PLEASE HELP ME](*,)

---

### Post by thirdmusketeer on 2006-05-15
Like many before me, I have also fallen in this pit. I am running Ubuntu on VMWare.

I followed all the instructions I have come accross which are almost identical. The following is what I did

vmware@vmware-bavm:~/Desktop/tmp$ dpkg-architecture -qDEB_BUILD_GNU_TYPE
i486-linux-gnu
vmware@vmware-bavm:~/Desktop/tmp$ DEB_BUILD_GNU_TYPE=i486-linux-gnu fakeroot make-jpkg jdk-1_5_0_06-linux-i586-rpm.bin Creating temporary directory: /tmp/make-jpkg.XXXXoPDCIX
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
vmware@vmware-bavm:~/Desktop/tmp$ locate blackdown-j2re.sh
vmware@vmware-bavm:~/Desktop/tmp$ locate common.sh
/usr/share/java-common/java-common.sh
vmware@vmware-bavm:~/Desktop/tmp$


It seems that the plugins are not to be found, where does the fakeroot load this plugins or stuff. It would be great if my problem could be solved.

Thanks

---

### Post by thirdmusketeer on 2006-05-16
[QUOTE=thirdmusketeer]Like many before me, I have also fallen in this pit. I am running Ubuntu on VMWare.

I followed all the instructions I have come accross which are almost identical. The following is what I did

vmware@vmware-bavm:~/Desktop/tmp$ dpkg-architecture -qDEB_BUILD_GNU_TYPE
i486-linux-gnu
vmware@vmware-bavm:~/Desktop/tmp$ DEB_BUILD_GNU_TYPE=i486-linux-gnu fakeroot make-jpkg jdk-1_5_0_06-linux-i586-rpm.bin Creating temporary directory: /tmp/make-jpkg.XXXXoPDCIX
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
vmware@vmware-bavm:~/Desktop/tmp$ locate blackdown-j2re.sh
vmware@vmware-bavm:~/Desktop/tmp$ locate common.sh
/usr/share/java-common/java-common.sh
vmware@vmware-bavm:~/Desktop/tmp$


It seems that the plugins are not to be found, where does the fakeroot load this plugins or stuff. It would be great if my problem could be solved.

Thanks[/QUOTE]


Can anybody tell me why the above plugins are required?? Pardon my ignorance but if I am trying to install java, why does it look for java plugins.

How can I diagnose the problem, How can I make sure my multiverse is working?? 
Thanks

---

### Post by stalefries on 2006-05-16
Luckily, we won't have bend over backwards to install Java anymore, as Sun has changed its licensing to allow distros such as Ubuntu to include it inin multiverse as a single package! 

See here:
[http://blogs.sun.com/roller/page/richb?entry=jdk_distros_project](http://blogs.sun.com/roller/page/richb?entry=jdk_distros_project)

---

### Post by Milamber_Cubed on 2006-05-17
[QUOTE=stalefries]Luckily, we won't have bend over backwards to install Java anymore, as Sun has changed its licensing to allow distros such as Ubuntu to include it inin multiverse as a single package! 

See here:
[http://blogs.sun.com/roller/page/richb?entry=jdk_distros_project](http://blogs.sun.com/roller/page/richb?entry=jdk_distros_project)[/QUOTE]

Perhaps the first page of this post needs to be changed to reflect this? It will mean that people aren't killing themselves for this without reason.

---

### Post by petervk on 2006-05-18
[Get Java on Ubuntu Wiki]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-68565ae07a003332e82c9f23706638777396c249")

The first post should be updated to this.

---

### Post by thirdmusketeer on 2006-05-18
[QUOTE=Mercuris]I downloaded jre-1_5_0_06-linux-i586.bin

I have tried all of these:
  sudo apt-get install j2re1.4 (couldn't find j2rel.4)

  chmod +x jre-1_5_0_06-linux-i586.bin (worked)

  sudo apt-get install fakeroot java-package java-common (couldn't find package java-package) Multiverse is enabled
 
  fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin  
 ( mkdir: cannot create directory `/etc/.java': Permission denied
  ./jdk-1_5_0_06-linux-i586.bin: line 507: /usr/share/mime-info/java-archive.keys: Permission denied)


Once you install it you shouldn't have any problems.
  DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin (same)

What else can i possibly do? PLEASE HELP ME](*,)[/QUOTE]
 

I wasn't able to get java-package through apt-get but was able to get through Synaptic Package Manager

System>Administration>Synaptic Package Manager

Browse to the  Miscellaneous Text Based (multiverse) you will find java-package in there

If you can't find (multiverse) then you haven't activated it yet.

---

### Post by thirdmusketeer on 2006-05-18
[QUOTE=thirdmusketeer]Like many before me, I have also fallen in this pit. I am running Ubuntu on VMWare.

I followed all the instructions I have come accross which are almost identical. The following is what I did

vmware@vmware-bavm:~/Desktop/tmp$ dpkg-architecture -qDEB_BUILD_GNU_TYPE
i486-linux-gnu
vmware@vmware-bavm:~/Desktop/tmp$ DEB_BUILD_GNU_TYPE=i486-linux-gnu fakeroot make-jpkg jdk-1_5_0_06-linux-i586-rpm.bin Creating temporary directory: /tmp/make-jpkg.XXXXoPDCIX
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
vmware@vmware-bavm:~/Desktop/tmp$ locate blackdown-j2re.sh
vmware@vmware-bavm:~/Desktop/tmp$ locate common.sh
/usr/share/java-common/java-common.sh
vmware@vmware-bavm:~/Desktop/tmp$


It seems that the plugins are not to be found, where does the fakeroot load this plugins or stuff. It would be great if my problem could be solved.

Thanks[/QUOTE]


Everybody left me high and dry, either intentionally or they realized I was too stupid to follow instructions :) guess I proved that I am not THAT stupid, i was supposed to download .bin package only, not rpm.bin, once I did that

---

### Post by LuisC-SM on 2006-05-22
[QUOTE=aldacron]I'm having this same issue. I have enabled multiverse/universe repositories successfully, but java-package is not showin up anywhere. Has it been removed altogether? Is there an alternative download location?[/QUOTE]
Same issue here... I have installed jave in Ubuntu 5.10 around 20 times or more and never had a single issue till today...
It seems that java-package has been removed...
Can anyone point on the right direction about this issue please?

Kind Regards.

PS. I have Universe and Multiverse repositories all unncommented

---

### Post by thirdmusketeer on 2006-05-22
It should be in Miscellaneous Text Based (Multiverse)

The other method is to get the debian package yourself and install it. Worked for me once but after that I found out how to install it using Synaptic Package Manager, although I wasn't able to get it through apt-get

---

### Post by xyz on 2006-05-23
Hi - in need of a little help here understanding why I have Java installed and yet (on sites using Java), Firefox requires to download the plugin?
```
sudo apt-get install sun-j2re1.5
  OR   sudo apt-get install j2re1.4

```

> sun-j2re1.5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```
java -version

```

> Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

Did I do something wrong? Many thanks for your help.

---

### Post by lukew on 2006-05-23
[QUOTE=xyz]Hi - in need of a little help here understanding why I have Java installed and yet (on sites using Java), Firefox requires to download the plugin?
```
sudo apt-get install sun-j2re1.5
  OR   sudo apt-get install j2re1.4

```



```
java -version

```


Did I do something wrong? Many thanks for your help.[/QUOTE]
Hi,

You need to make Firefox aware of the plugin, this is done via a sudo link, an example is blow, but make sure you get the right versions that you have installed.

I hope this helps.

Luke


Open a terminal 
Change to your Mozilla (or Mozilla Firefox) plugins directory 
Issue the following command: ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

---

### Post by xyz on 2006-05-23
[QUOTE=lukew]Hi,

You need to make Firefox aware of the plugin, this is done via a sudo link, an example is blow, but make sure you get the right versions that you have installed.

I hope this helps.

Luke


Open a terminal 
Change to your Mozilla (or Mozilla Firefox) plugins directory 
Issue the following command: ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so[/QUOTE]

Hi,
Thanks a lot Luke. I didn't know this! Soooo many things to learn...but I'm not complaining...it is soooo interesting! See you.

---

### Post by Thorne on 2006-05-23
Thanks, plain and simpe. And works too. :)

---

### Post by LuisC-SM on 2006-05-24
Now it works :=)

Regards

---

### Post by TFrog on 2006-05-27
[QUOTE=Adamal]Since I haven't seen any how to's on how to install Sun's java (Any Version) I thought I'd write up a little how to.

First you will need to add all the extra repositories for Ubuntu.  (ie Multiverse, Universe...) Please see other how to's on how to do that.

Now go to Sun's website [http://java.sun.com](http://java.sun.com) and select the java jdk or jre that you want.  In my case I needed 1.4.2 so I downloaded j2sdk-1_4_2_09-linux-i586.bin.

Then run the following commands from the terminal:

First install the required packages:
**sudo apt-get install fakeroot  java-package java-common**
Create the Deb file for the install:
**fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin**
Install The deb file
**sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb**
Now make Sun's java the default by running this command and selecting it.
**sudo update-alternatives --config java**

I hope that helps.[/QUOTE]

For your information, the link in your post is no longer correct except for the JDK.  In order to get the JRE you can get it at:

[http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

There you can manually download the bin file for the JRE.

---

### Post by balivo on 2006-10-24
Many of us have no idea how to add multiverse repository. There is the best link: [https://jdk-distros.dev.java.net/ubuntu-dev.html](https://jdk-distros.dev.java.net/ubuntu-dev.html)

Actualy, ONLY uncomment repository from list will not install multiverse.

---

### Post by Skorzen on 2007-11-02
Thanks for the tuto! That helped me out with Mercury's installation.

---

### Post by theresajayne on 2008-06-28
i am trying to install JDK 6 on ubuntu 8.04

i followed the instructions fully and then did the install successfully

however i am now getting the following errors....

root@ubuntu:/home/ubuntu# java
java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory


can anyone advise?

---

### Post by Adamal on 2008-06-29
Hi theresajayne,

This is a pretty old post and the instructions are no longer nessessary in Ubuntu 8.04.

Execute one of the following:
sudo apt-get install sun-java6-jdk

or 
sudo apt-get install sun-java6-jre

The difference is the jdk is for developers and the jre is for just running java apps.

---

### Post by punpradip on 2008-07-01
I downloaded "jre-6u6-linux-i586-rpm.bin" self extracting file and I tried
"sudo apt-get install fakeroot java-package java-common" command. As I entered the password, it displays: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Why is it so? How can i know root password of myself? Please help me to sort it out. Thanks.

---

### Post by Adamal on 2008-07-01
> **punpradip said:**
> I downloaded "jre-6u6-linux-i586-rpm.bin" self extracting file and I tried
"sudo apt-get install fakeroot java-package java-common" command. As I entered the password, it displays: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Why is it so? How can i know root password of myself? Please help me to sort it out. Thanks.

You probably had synaptic or the update manager open while executing that command.  You should never need to login as root, or even need the root password.

Executing the command sudo makes you act as root for the duration of the command anyways.

Also I'd recommend you grab the java version from the Ubuntu repositories instead of sun's site.

---

### Post by nunee on 2008-08-15
I was able to install java by first typing sudo-apt get update.
Then I typed sudo apt-get install sun-java5-jdk. After that the whole installation started and asked me something in which you type y for yes. Then after the blue screen of the license comes out in which you are asked to accept but you cant yet. First you must exit the terminal then go to synaptic package manager, in which it might ask you to dpkg --configure -a. To do this you go to the terminal and type dpkg --configure -a. After that go to synaptic package manager, and search java or sun java and itll give you the list of the java to download. 

This worked for me. 
Please reply if it did not work

---

### Post by zaivala on 2008-08-17
> **Adamal said:**
> Hi theresajayne,

This is a pretty old post and the instructions are no longer nessessary in Ubuntu 8.04.

Execute one of the following:
sudo apt-get install sun-java6-jdk

or 
sudo apt-get install sun-java6-jre

The difference is the jdk is for developers and the jre is for just running java apps.

I followed the instructions of another user, 
sudo apt-get install sun-java6*

It worked to a point... but it hung on a screen that says 

Package Configuration

Configure sun-java6-bin

Operating System Distributor License

...and a long page of things to agree to, with an < OK > at the end...

but the OK is not linked to anything, so I can't go beyond that page.

Any clues?

I halted execution, and started over in Terminal...

sudo apt-get install sun-java6*
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
dpkg --configure -a
dpkg: requested operation requires Superuser privilege

OK, does that mean I need to run 'sudo dpkg ...'?  I'm such a dweeb.

I did that... it was followed by several lines, ending with

ldconfig deferred processing now taking place.

???

So I ran sudo apt-get install sun-java6*  again...

and it went right back to the screen it is hung on.

---

### Post by zaivala on 2008-08-17
Issue is solved... what nothing anywhere tells me is that I have to hit the Tab key to select Ok.  Grrrrrrr

---

### Post by scratchy172 on 2008-10-16
uh...ok just one miner problem with me... i just got ubuntu like 2 days ago and i have no idea what i am doing so can someone tell me how to do it so even a 1 year old can understand please...

---

### Post by Adamal on 2008-10-16
> **scratchy172 said:**
> uh...ok just one miner problem with me... i just got ubuntu like 2 days ago and i have no idea what i am doing so can someone tell me how to do it so even a 1 year old can understand please...

Open a terminal and type:

sudo apt-get install sun-java6-jre

it will prompt you for your password.  Type it in and hit Enter. Wait for it to finish, and java is installed.

You should be able to install java from Add/Remove programs too, but I don't have a machine to walk you through the steps.

---

### Post by zaivala on 2008-10-16
> **scratchy172 said:**
> uh...ok just one miner problem with me... i just got ubuntu like 2 days ago and i have no idea what i am doing so can someone tell me how to do it so even a 1 year old can understand please...

Do what Adamal said, and if, during the Java installation, you get to a box where you don't seem to be able to select "OK" to continue, use your Tab key to select it.  

Moss

---

### Post by 162019444 on 2008-10-18
&#39030; &#35797;&#39564;&#19968;&#21704;&#33021;&#19981;&#33021;&#21457;&#35328;&#20102;

---

### Post by Adamal on 2008-10-18
> **162019444 said:**
> &#39030; &#35797;&#39564;&#19968;&#21704;&#33021;&#19981;&#33021;&#21457;&#35328;&#20102;

A top Kazakh pilot can speak?

What the heck is that suppose to mean...

---

### Post by zaivala on 2008-10-18
I think someone forgot to tell him this forum's in English.

---

### Post by scratchy172 on 2008-10-19
> **Adamal said:**
> Open a terminal and type:

sudo apt-get install sun-java6-jre

it will prompt you for your password.  Type it in and hit Enter. Wait for it to finish, and java is installed.

You should be able to install java from Add/Remove programs too, but I don't have a machine to walk you through the steps.

ok did that and got this error messege

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Adamal on 2008-10-19
> **scratchy172 said:**
> ok did that and got this error messege

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Sounds like you might have either blocked or killed the process while it was running.

You should do what the message states and run:

sudo dpkg --configure -a

From the terminal.

---

### Post by jarome on 2009-03-27
> **Adamal said:**
> Since I haven't seen any how to's on how to install Sun's java (Any Ve
[COLOR="Red"]The instructions above are dated, please do not use them.  Use the following instead: [/COLOR]
Execute one of the following:
**sudo apt-get install sun-java6-jdk** - For the JDK (Developer)
**sudo apt-get install sun-java6-jre** - For the JRE (User)

But the version I have now is 1.6.10, whereas Sun has 1.6.13. 
sudo apt-get install sun-java6-jdk says I have the latest version.

How do I update to the latest version from Sun's .bin file? The fakerootinstructions do not work.
~/download/java$ fakeroot make-jpkg jdk-6u13-linux-i586.binCreating temporary directory: /tmp/make-jpkg.JbVPz26849
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.

Not having the latest (security bugs fixed) version is a problem. Why aren't the repositories updated?

---

### Post by carlosalvatore on 2009-04-11
> **jarome said:**
> But the version I have now is 1.6.10, whereas Sun has 1.6.13. 
sudo apt-get install sun-java6-jdk says I have the latest version.

How do I update to the latest version from Sun's .bin file? The fakerootinstructions do not work.
~/download/java$ fakeroot make-jpkg jdk-6u13-linux-i586.binCreating temporary directory: /tmp/make-jpkg.JbVPz26849
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.

Not having the latest (security bugs fixed) version is a problem. Why aren't the repositories updated?

I'm having the same issue

---

### Post by AngelDrangel on 2009-07-05
Hi Guys,

on this Site will be explain to this phenomenon. - *gg*

[http://rblondon.blogspot.com/2007/09/eclipse-and-java-sdk-15-on-debian-etch.html](http://rblondon.blogspot.com/2007/09/eclipse-and-java-sdk-15-on-debian-etch.html)

This issue is trick and simple.
You need to the filename change to jdk-6u12....bin to jdk-1.5.14....bin

Issue resolved.

---

### Post by Aakriti on 2009-07-31
hello, i'm new to ubuntu & i'm just helping myself by following instructions on the internet.

i wanted to download java jre 1.6 and wrote a sudo command in terminal, the download sort of dint complete before i accidently closed my terminal 
now when i tried to do it again this is what happened in my terminal, can anyone please help me?

$ sudo apt-get install sun-java6-jre 
[sudo] password for aakriti: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


how do i manually run sudo.. ??

---

### Post by Aakriti on 2009-07-31
i'm using 32 bit ubuntu jaunty

---

### Post by Aakriti on 2009-07-31
i did that and then this 

aakriti@aakriti-laptop:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
aakriti@aakriti-laptop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
aakriti@aakriti-laptop:~$

---

### Post by Aakriti on 2009-07-31
i think the problem got solved, when i restarted my lappy, update manager said some packages are incomplete and then it did it all by itself with my one click!

---

### Post by kotoro on 2010-03-08
I wrote another howto for manually installing using Sun's provided self-extracting binary for linux, for those of you that can't get the alien command method to work and would like to install the most recent version of java.

Note to moderators, my other thread should probably be moved from the programming forum to the tutorials forum, my mistake posting it in the wrong place.

Currently its URL is : [http://ubuntuforums.org/showthread.php?t=1422727](http://ubuntuforums.org/showthread.php?t=1422727)

---

### Post by TodoInTX on 2010-06-03
From the sun forumns... [http://forums.sun.com/thread.jspa?threadID=5428712](http://forums.sun.com/thread.jspa?threadID=5428712)

This works in Lucid 10.04

1. sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
2. sudo aptitude update
3. sudo aptitude install sun-java6-jdk

Then you have to select it:

sudo update-alternatives --config java

Easy, peasy!

---

