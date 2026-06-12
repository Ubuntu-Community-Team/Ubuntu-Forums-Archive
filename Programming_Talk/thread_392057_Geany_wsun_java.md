---
title: "Geany w/sun java"
date: 2007-03-24
forum: Programming Talk
---

### Post by Mochtroid-X on 2007-03-24
I want to use Geany so I can do my schoolwork at home but I cannot get it to compile my java apps and it gives me this:

```

javac "HelloWorld.java" (in directory: /home/----------/Desktop/Documents/Java)
/bin/sh: javac: not found
compilation finished unsuccessful

```

From what I've read around the forum I think it's similar to Eclipse in that I have to set up sun java for it but Eclipse is too much of a hassle and I just want a lightweight IDE to get my schoolwork done. Any insight on this?

---

### Post by kerry_s on 2007-03-24
Did you install java? (sudo apt-get install sun-java6-plugin)

Also, i have a question, does your geany have a green line down it? See pic
Edit: Never mine i see at the main site, all the screen shots have the green line.

---

### Post by samjh on 2007-03-24
> **Mochtroid-X said:**
> I want to use Geany so I can do my schoolwork at home but I cannot get it to compile my java apps and it gives me this:

```

javac "HelloWorld.java" (in directory: /home/----------/Desktop/Documents/Java)
/bin/sh: javac: not found
compilation finished unsuccessful

```

From what I've read around the forum I think it's similar to Eclipse in that I have to set up sun java for it but Eclipse is too much of a hassle and I just want a lightweight IDE to get my schoolwork done. Any insight on this?

What a nice simple IDE, I installed it to try to help you, but now I'm going to keep it! :)

No need to set anything up, apart from installing the JDK.

Open up the console, and type:
sudo apt-get install sun-java5-jdk

That's all you need.  Then in Geany, open up your Java source code file, and click Compile.  It should work.

---

### Post by Mochtroid-X on 2007-03-24
Hmmm, seems I had the JRE installed but not the JDK, but whenever I try to install it I get this problem:

```

The following packages have unmet dependencies:
  sun-java5-jdk: Depends: sun-java5-jre (= 1.5.0-08-0ubuntu1) but 1.5.0-10-1.1 is to be installed
                 Depends: sun-java5-demo (= 1.5.0-08-0ubuntu1) but it is not going to be installed

```

I cannot seem to install the JDK in any way, is there a place I can download the .deb files for it and the demo that anyone knows of?


-edit- I installed the Blackdown Java SDK and everything works fine now, except when I run the program the window containing it instantly closes...

---

### Post by samjh on 2007-03-25
If you're doing these for a programming class, you'd want the standard Sun Java.

Try uninstalling the JRE, and then reinstalling sun java using the JDK package as I showed in my previous post.

---

### Post by kerry_s on 2007-03-25
You need to turn all your repos, sun-java is in multiverse.

---

### Post by Mochtroid-X on 2007-03-25
I tried uninstalling the JRE but the JDK still would not downoad by giving me the unmet dependencies I showed in my last post. Is Blackdown Java's development kit not as good as the standard Sun JDK??

---

### Post by Ramses de Norre on 2007-03-25
There must be something wron with your /etc/apt/sources.list file... Mine is like this:```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release Candidate i386 (20061017.1)]/ edgy main restricted


#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release Candidate i386 (20061017.1)]/ edgy main restricted

##deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
##deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
#deb http://packages.freecontrib.org/ubuntu/plf edgy-plf free non-free
#deb-src http://packages.freecontrib.org/ubuntu/plf edgy-plf free non-free

## Medibuntu - Ubuntu 6.10 "edgy eft"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free

## wine
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

## Canonical commercial repo
deb http://archive.canonical.com/ubuntu edgy-commercial main
deb http://archive.canonical.com/ubuntu dapper-commercial main

## New amarok
deb http://www.kubuntu.org/packages/amarok-latest edgy main

## Newest binary ati and nvidia drivers (tseliot)
#deb http://albertomilone.com/drivers/edgy/nonlegacy/32bit binary/

## Beryl repo
#deb http://ubuntu.beryl-project.org edgy main

```

And sun's jre and jdk are the standards, blackdown has somewhat strange behavior sometimes... Sun's jre is also faster than blackdown's.

---

### Post by Mochtroid-X on 2007-03-25
I copied and pasted you sources.list over mine and I still cannot download the JDK. What is going on here? :confused:

---

### Post by Ragazzo on 2007-03-25
Can you install sun-java5-demo separately first?

---

### Post by Mochtroid-X on 2007-03-25
No I cannot, it says it requires the JDK and JRE (though I already have the JRE installed)

---

### Post by Ramses de Norre on 2007-03-25
What's the exact output of following command ```
apt-cache policy sun-java6-jdk sun-java6-jre sun-java6-bin sun-java6-demo sun-java6-plugin
```
And what's the **exact** error message when you try to install the jdk?

---

### Post by Mochtroid-X on 2007-03-25
I have the sun-java5-bin and sun-java5-jre installed and I get this for that command:

```

:~$ apt-cache policy sun-java6-jdk sun-java6-jre sun-java6-bin sun-java6-demo sun-java6-plugin
W: Unable to locate package sun-java6-jdk
W: Unable to locate package sun-java6-jre
W: Unable to locate package sun-java6-bin
W: Unable to locate package sun-java6-demo
W: Unable to locate package sun-java6-plugin
:~$ 

```


And the error I get was this one I posted earlier:

```

The following packages have unmet dependencies:
  sun-java5-jdk: Depends: sun-java5-jre (= 1.5.0-08-0ubuntu1) but 1.5.0-10-1.1 is to be installed
                 Depends: sun-java5-demo (= 1.5.0-08-0ubuntu1) but it is not going to be installed

```

---

### Post by Ramses de Norre on 2007-03-25
You've got messed up sources...
What version of ubuntu are you using? If edgy: did you try my sources??
If you're on dapper: I hope you saw mine were edgy sources?? (Sorry about not mentioning it)

Did you reload your package list? (sudo aptitude update)
Can you repeat the same command but change every '6' to '5'?

Did you add any external repos providing java? Because that's the only way of getting such dependency errors.

---

### Post by Mochtroid-X on 2007-03-25
I'm running Edgy, your sources gave me the same effect as mine, update gives no errors, replacing the 6's with 5' gives me this:

```

:~$ apt-cache policy sun-java5-jdk sun-java5-jre sun-java5-bin sun-java5-demo sun-java5-plugin
sun-java5-jdk:
  Installed: (none)
  Candidate: 1.5.0-08-0ubuntu1
  Version table:
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
sun-java5-jre:
  Installed: 1.5.0-10-1.1
  Candidate: 1.5.0-10-1.1
  Version table:
 *** 1.5.0-10-1.1 0
        100 /var/lib/dpkg/status
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
sun-java5-bin:
  Installed: 1.5.0-10-1.1
  Candidate: 1.5.0-10-1.1
  Version table:
 *** 1.5.0-10-1.1 0
        100 /var/lib/dpkg/status
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
sun-java5-demo:
  Installed: (none)
  Candidate: 1.5.0-08-0ubuntu1
  Version table:
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
sun-java5-plugin:
  Installed: (none)
  Candidate: 1.5.0-08-0ubuntu1
  Version table:
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
:~$ 

```


This is my sources.list, as you can see I have not added any external repos for Java:

```

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#Ubuntusoftware.info
# deb http://ubuntusoftware.info/ edgy all

#moblock
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main

## wine
deb http://wine.budgetdedicated.com/apt edgy main

## Canonical commercial repo
deb http://archive.canonical.com/ubuntu edgy-commercial main
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

---

### Post by Ramses de Norre on 2007-03-25
> **Mochtroid-X said:**
> ```

:~$ apt-cache policy sun-java5-jdk sun-java5-jre sun-java5-bin sun-java5-demo sun-java5-plugin
sun-java5-jdk:
  Installed: (none)
  Candidate: 1.5.0-08-0ubuntu1
  Version table:
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
sun-java5-jre:
  Installed: 1.5.0-10-1.1
  Candidate: 1.5.0-10-1.1
  Version table:
 [B]*** 1.5.0-10-1.1 0
        100 /var/lib/dpkg/status[/B]
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
sun-java5-bin:
  Installed: 1.5.0-10-1.1
  Candidate: 1.5.0-10-1.1
  Version table:
 [B]*** 1.5.0-10-1.1 0
        100 /var/lib/dpkg/status[/B]
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
sun-java5-demo:
  Installed: (none)
  Candidate: 1.5.0-08-0ubuntu1
  Version table:
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
sun-java5-plugin:
  Installed: (none)
  Candidate: 1.5.0-08-0ubuntu1
  Version table:
     1.5.0-08-0ubuntu1 0
        500 http://us.archive.ubuntu.com edgy/multiverse Packages
:~$ 

```

But you did install external packages, the two I made bold don't occur in any of your repos, as you can see. So to fix your problems you need to uninstall those higher versions and install the repo versions. You will then be able to install the other packages too.

```
sudo aptitude install sun-java5-bin=1.5.0-08-0ubuntu1 sun-java5-jre=1.5.0-08-0ubuntu1
```

> **Mochtroid-X said:**
> ```
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[B]# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse[/B]

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#Ubuntusoftware.info
# deb http://ubuntusoftware.info/ edgy all

#moblock
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main

## wine
deb http://wine.budgetdedicated.com/apt edgy main

## Canonical commercial repo
deb http://archive.canonical.com/ubuntu edgy-commercial main
deb http://archive.canonical.com/ubuntu dapper-commercial main
``` You didn't copy mine, you've got edgy-backports disabled, and that's the repo containing java6.
Java6 has way better performance than java5, so you might want to use that.

---

### Post by Mochtroid-X on 2007-03-25
Oh man I forgot, I must installed those from ubuntusoftware.info because that was in my repo list when i installed that java5, and I did use your repos but i couldn't install the JDK for Java5 so I just reinstated what I had with some minor changes. Thanks a lot for your help and I wish this forum had a reputation system!

Java6 works but running my source code in Geany still just opens the window containing "Hello World" and instantly closes it...

---

### Post by graabein on 2007-03-26
Check your code if nothing is waiting for input then the program just finishes up and closes.

A special thing about ubuntuforums is that there's no reputation system and it's still very helpful. 

=D>

---

### Post by samjh on 2007-03-26
> **Mochtroid-X said:**
> running my source code in Geany still just opens the window containing "Hello World" and instantly closes it...

That's strange, when I tried, the pop-up window said:
```
Hello World


-----------------------
(program exited with code: 0)
Press return to continue
```It didn't just disappear.

Here's my source code:
```
public class hello {
    public static void main (String args[]) {
        System.out.println("Hello World");
    }
}
```
What version of Geany are you using?  Mine is 0.10.2.

---

### Post by Mochtroid-X on 2007-03-26
Well I upgraded to the same version you have (I had 0.8 ) and the window stays open, but I get this error with my code and also with yours:

```

./geany_run_script.sh: 3: java: not found


------------------
(program exited with code: 127)
Press return to continue

```

---

### Post by Ramses de Norre on 2007-03-26
Have you got sun-java6-jre and sun-java6-jdk installed? (or the corresponding java5 packages)
Try running **sudo update-java-alternatives -s java-6-sun** for java6 or **sudo update-java-alternatives -s java-1.5.0-sun** for java5.

---

### Post by Mochtroid-X on 2007-03-26
-edit- It's working now, thanks a lot everyone for your help! :)

---

### Post by pratzy on 2010-06-25
Here is a clean solution

to enable java and javac. (java compiler)
download the jdk 
from: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

login as root

chmod +r+x jdk-6u1-linux.bin
sh jdk-6u1-linux.bin

after install: (as root)

ln -s /opt/jdk1.6.0_01/bin/javac /usr/bin
ln -s /opt/jdk1.6.0_01/bin/java /usr/bin


Now you have java in your system.
And Geany has java compiler for you.
:guitar:

---

### Post by pratzy on 2010-06-25
oh..one more thing...
if u can't login as root, just add **sudo** before each command above.

---

