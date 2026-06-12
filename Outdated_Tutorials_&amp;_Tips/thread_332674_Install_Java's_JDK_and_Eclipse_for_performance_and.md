---
title: "Install Java's JDK and Eclipse for performance and ease"
date: 2007-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by phossal on 2007-01-06
**INSTALLING JAVA (JDK/JRE)**
Here is the updated version used to install Java's JDK 6u1 on Edgy. The method doesn't use packages, opting to use Sun's .bin file instead. Visit [java.sun.com]("http://java.sun.com/javase/downloads/index.jsp") to download their .bin file. You probably want: jdk-6u1-linux-i586.bin.

[COLOR="SlateGray"]**STEP: **[/COLOR]Download it to your desktop. Once it's fully downloaded, open a command prompt and execute it like so:
```

cd ~/Desktop
sudo chmod +x *.bin
sudo sh ./jdk*.bin
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Executing the .bin file creates a folder on your desktop named jdk1.6.0_01. Rename that folder to Java6u1. Now move that folder to /usr/lib

```
sudo mv Java6u1 /usr/lib
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Now add Java to update-alternatives and make it the default like so:

```
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 300
sudo update-alternatives --config java
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Don't forget your Java plugin

```
sudo ln -s /usr/lib/Java6u1/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```





**INSTALLING ECLIPSE**
Download eclipse directly from eclipse.org. You probably want: [eclipse-SDK-3.2.2-linux-gtk.tar.gz]("http://download.eclipse.org/eclipse/downloads/drops/R-3.2.2-200702121330/download.php?dropFile=eclipse-SDK-3.2.2-linux-gtk.tar.gz")

[COLOR="SlateGray"]**STEP: **[/COLOR]Download the file to your desktop. Right-click and extract it. Move it to the directory of your choice. (I use /usr/lib)

[COLOR="SlateGray"]**STEP: **[/COLOR]Add links to /usr/bin (edit your paths as necessary):

```
sudo update-alternatives --install /usr/bin/eclipse eclipse /usr/lib/eclipse/eclipse 300
sudo ln -s /usr/lib/eclipse/startup.jar /usr/bin
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Add eclipse to the menu:

Right-click Applications -> Edit Menus -> Programming -> New Item ->
Icon: /usr/lib/eclipse/icon.xpm
Name: eclipse
Comment: Launch eclipse
Command: eclipse





**INSTALLING NETBEANS**

**[COLOR="SlateGray"]STEP: [/COLOR]**Grab the Netbeans Tarball ([Netbeans-5_5.tar.gz]("http://dlc.sun.com/netbeans/download/5_5/mlfcs/200612070100/netbeans-5_5.tar.gz")) from netbeans.org. Save it to your desktop. Right-click and extract it.

**[COLOR="SlateGray"]STEP: [/COLOR]**Move it to /usr/lib/netbeans
```
cd ~/Desktop
sudo mv netbeans /usr/lib/
``` 

**[COLOR="SlateGray"]STEP: [/COLOR]**Add links to /usr/bin (Edit your paths as necessary):
```
sudo update-alternatives --install /usr/bin/netbeans netbeans /usr/lib/netbeans/bin/netbeans 300
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Add netbeans to the menu:

Right-click Applications -> Edit Menus -> Programming -> New Item ->
Icon: /usr/lib/netbeans/nb5.5/netbeans.png
Name: netbeans
Comment: Launch Netbeans
Command: netbeans


---------------------------------------------------------------------------------
[COLOR="SlateGray"][SIZE="1"]The java packages do, in fact, still use the .bin file from SUN. They're just additional wrappers. By installing using the method above, you're able to install multiple JDK's, which can be set as defaults using update-alternatives --config. In addition, you can install older versions of the JDK, which are all available at the SUN site for Java.[/SIZE][/COLOR]

---

### Post by phossal on 2007-01-08
[edited]

---

### Post by phossal on 2007-01-10
[edited]

---

### Post by cnphch on 2007-01-12
I followed your guide, but when i type

```
java -version
```

Then it's still ver. 1.4

---

### Post by phossal on 2007-01-12
[edited]

---

### Post by phossal on 2007-01-12
~~

---

### Post by phossal on 2007-01-13
~~

---

### Post by phossal on 2007-01-13
Removed

---

### Post by phossal on 2007-01-19
Removed

---

### Post by phossal on 2007-01-22
Removed

---

### Post by bbgun on 2007-01-27
Hello-

I too am experiencing the problem of not being able to open Eclipse from the apps menu and getting the error:

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java

But I am able to open Eclipse from the command line. 

Forgive me, but I still didn't get the solution for this.  I have followed phossal's well-presented tutorial so far, including  making the changes to ./bashrc....but still no luck.

Any ideas on where to go from here?

Thanks

bbgun

---

### Post by phossal on 2007-01-27
~~

---

### Post by qpwoeiruty on 2007-01-28
Ed.

---

### Post by phossal on 2007-01-28
~~

---

### Post by qpwoeiruty on 2007-01-28
I know that I got mine by Synaptic before I installed any java which is how i got the problem I think.

> Plus, you can simply add a line to /etc/jvm that points to the JDK.
???
I assume this is the better way but I don't understand what to add to the file.

Sorry, it's really interesting learning but Linux is still in the voodoo stages for me :D

---

### Post by phossal on 2007-01-28
~~

---

### Post by linuxismyfriend on 2007-01-28
Thank you phossal for the awesome HowTo, it was exactly what I was looking for.  Regarding your method for making the jar files work when double clicked, does that work for only one file or does it set all the jar files to be doubl-clickable? If not, is it possible to create a ".mime.types" file in the home directory and have something like: "application/java    jar"? Thanks!

---

### Post by phossal on 2007-01-28
My experience indicates all files.

---

### Post by qpwoeiruty on 2007-01-29
> **phossal said:**
> Are you currently having a problem? ;) If you have good advice, you can PM me, and I'll incorporate it into the tutorial. Or, I'd even recommend posting your own How-To if you feel you have a better method.

eh? no. i guess i don't :P i guess i just was hoping that there was a better,right way to do it. didn't really feel like spending another 1/2 day re-DLing eclipse. anyway thanks for the great tutorial, it was easy enough for even someone like me to figure out =D

---

### Post by phossal on 2007-01-29
Removed

---

### Post by phossal on 2007-01-30
Removed

---

### Post by phossal on 2007-01-31
Removed

---

### Post by andyanderso on 2007-01-31
I can't seem to make the java plugin work for firefox?  I basically did your install without eclipse...??

---

### Post by phossal on 2007-01-31
~

---

### Post by phossal on 2007-01-31
Removed

---

### Post by phossal on 2007-02-01
Removed

---

### Post by phossal on 2007-02-01
Removed

---

### Post by phossal on 2007-02-01
Removed

---

### Post by filipblondeel on 2007-02-01
Thanks for the guide ! 

But I have a question: what about Java Web Start with java 6.0 ?? How can I install that ?

---

### Post by phossal on 2007-02-01
Removed

---

### Post by andyanderso on 2007-02-01
Phossal,

This is an easy-to-use, educational, well-written tutorial.  I just wanted to say thanks for all the time you have put into it.  It's great!

-Andy

---

### Post by phossal on 2007-02-01
> **andyanderso said:**
> This is an easy-to-use, educational, well-written tutorial.  I just wanted to say thanks for all the time you have put into it.  It's great!

Awesome compliment! I really appreciate you taking the time to say thanks, too. So, thank *you*. Cheers!

---

### Post by phossal on 2007-02-02
Removed

---

### Post by phossal on 2007-02-03
Removed

---

### Post by kmcconn9 on 2007-02-04
I am trying to install Java and Limewire and am having some difficulties.

I thought that i had Java installed, but upon going to the java site, I can still not view their icon which shows that I have Java installed.  Also, I used  about:plugins in firefox and i did not see where java was an option to be enabled..

Any guided help for a newb would be greatly appreciated...

Thanks guys

---

### Post by phossal on 2007-02-04
~

---

### Post by kmcconn9 on 2007-02-04
I do not believe that I have Java installed correctly.  Is there a way that I can check to see if it is funtioning as I will need the java to run/open limewire

edit:  So I opened limewire and double clicked runlime.sh...and it just brought up a notepad box with java code and text...there was no where to click run?

I also tried to enter 

sh ./runLime.sh

in the terminal and got nothing...

EDIT:  ok, I was trying to access the limewire.zip folder on my desktop.  i opened the limewire folder I just downloaded again and clicked runlime.sh, then selected run and nothing happened.  Which leads me to believe something is wrong with the java I have installed or lack there of..

---

### Post by phossal on 2007-02-04
~

---

### Post by kmcconn9 on 2007-02-04
```

student@student-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
student@student-desktop:~$ ls -l $(type -path -all java)
lrwxrwxrwx 1 root root 22 2007-01-23 15:45 /usr/bin/java -> /etc/alternatives/java
lrwxrwxrwx 1 root root 22 2007-01-23 15:45 /usr/bin/X11/java -> /etc/alternatives/java

```

---

### Post by phossal on 2007-02-04
~

---

### Post by kmcconn9 on 2007-02-04
That is the problem.  I cant do the first couple of steps that you have posted...

Here I will attempt to do the first steps your provided and you can see the errors excatly..

```

student@student-desktop:~$ sudo chmod +x jdk-6-linux-i586.bin
chmod: cannot access `jdk-6-linux-i586.bin': No such file or directory
student@student-desktop:~$ sh jdk-6-linux-i586.bin
sh: jdk-6-linux-i586.bin: No such file or directory
student@student-desktop:~$ 


```

---

### Post by phossal on 2007-02-04
~

---

### Post by kmcconn9 on 2007-02-04
I believe this is what you mean...

```

student@student-desktop:~$ pwd
/home/student
student@student-desktop:~$ ls
Desktop  Examples  libstdc++-libc6.1-1.so.
student@student-desktop:~$ sudo chmod +x jdk-6-linux-i586.bin
chmod: cannot access `jdk-6-linux-i586.bin': No such file or directory
student@student-desktop:~$ sh jdk-6-linux-i586.bin
sh: jdk-6-linux-i586.bin: No such file or directory
student@student-desktop:~$ 


```

Yes I am as new to Ubuntu as you can get.

Tne filename is exactly as it appears in the above code and the location is on the desktop.

---

### Post by phossal on 2007-02-04
Removed

---

### Post by kmcconn9 on 2007-02-04
Ok, thats makes complete sense.  I have jre-java-6-i586 instead of jdk...

Once I was in the desktop directory I put the first two codes in and the package unpacked and created the folder on the desktop..

```

Done.
student@student-desktop:~/Desktop$ ls
Java6  jre1.6.0  jre-6-linux-i586.bin  LimeWire
student@student-desktop:~/Desktop$ 

```

I am downloading jdk right now and I will go back thru the steps...I believe I downloaded the wrong file...thus all of the problems.  i didnt think that this could be THAT hard...

I will report back..

Thanks again

---

### Post by kmcconn9 on 2007-02-04
ok so I redid everything and installed the jdk and renamed the Java6 folder.

But when I type java -version I get 1.4.0 still?

```

student@student-desktop:~/Desktop$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
student@student-desktop:~/Desktop$ 



```

---

### Post by phossal on 2007-02-04
~

---

### Post by kmcconn9 on 2007-02-04
evidently I did something wrong in bash

```

student@student-desktop:~$ source ~/.bashrc
student@student-desktop:~$ echo $JAVA_HOME

student@student-desktop:~$ 


```

I copied and pasted everything that you listed and then saved the bash file and closed the terminal..

opened the terminal and did the above commands and got those results...

---

### Post by phossal on 2007-02-04
~

---

### Post by kmcconn9 on 2007-02-06
ok those steps are completed...and here is my output/code

```

student@student-desktop:~$ source ~/.bashrc
student@student-desktop:~$ echo $JAVA_HOME

student@student-desktop:~$ gedit /home/student/.bashrc
student@student-desktop:~$ source /home/student/.bashrc
student@student-desktop:~$ 


```

---

### Post by phossal on 2007-02-06
~

---

### Post by kmcconn9 on 2007-02-06
Here is my .bashrc file

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
export JAVA_HOME='/home/student/Desktop/Java6' 
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH

```

java version says 1.60...so looks to be installed and java home reports the location of java6 on the desktop

---

### Post by phossal on 2007-02-06
~

---

### Post by kmcconn9 on 2007-02-06
I believe so, I just need to see if it will run...and then I should be able to install limewire now

---

### Post by phossal on 2007-02-06
For the record, I don't *recommend* Limewire. It's commonly used for illegal music sharing. I don't do it, and I don't support it.

---

### Post by kmcconn9 on 2007-02-07
weird....I double clicked runlime.sh, and then clicked run and nothing happens...

so I go to test the Java by going to th e java site and clicking on this link:

[http://www.java.chttp://www.google.com/om/en/download/installed.jsp?detect=jre&try=2](http://www.java.chttp://www.google.com/om/en/download/installed.jsp?detect=jre&try=2)

The image/test does not load.  So I click on get plugin at the top banner on the screen and it says that there is no plugin available from firefox.  It then directs me to download Java version 5.0?

But I already have 6.0 installed and verified on my machine...

---

### Post by phossal on 2007-02-08
Removed

---

### Post by mr.blacke on 2007-02-10
Wonderful . Everything works as explained.  Just wondering if the environment variables set to /home/someone/.bashrc works only for someone or for every user on computer? Why these variables won't work on /etc/profile ?
Thank you again for your explaining!

---

### Post by phossal on 2007-02-10
Removed

---

### Post by phossal on 2007-02-13
Removed

---

### Post by phossal on 2007-02-20
Removed

---

### Post by manat on 2007-02-21
Thanks for the install guide. However, I found that step 5 and 6 doesn't work for me. So I did it by: 
```
sudo /usr/sbin/update-alternatives --config java
sudo /usr/sbin/update-alternatives --config javac
sudo /usr/sbin/update-alternatives --config javaws
```

Thanks for the guide again.

---

### Post by phossal on 2007-02-21
Removed

---

### Post by Cesa on 2007-02-23
> **bbgun said:**
> Hello-
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java
bbgun

I get this message as well, any suggestions for a noob? :)

---

### Post by whateverdood on 2007-02-23
Thanks Phossal.  I've followed your instructions but "java -version" is still showing gnu 1.4.2.  What am I doing wrong?  I've read the update-alternatives man page but nothing jumps out.  I'm new to Debian systems so please forgive my ignorance...

---

### Post by Cesa on 2007-02-23
Umm, didn't have the correct path in /etc/eclipse/java_home, works fine now.

---

### Post by phossal on 2007-02-23
Removed

---

### Post by whateverdood on 2007-02-24
I didn't see this mentioned in this thread, so here goes: if you follow phossal's excellent instructions but still see gnu's 1.4.2 jdk when typing "java -version", try using "sudo update-alternatives --config java" to select the JVM that you just installed.

Hope that helps someone.

---

### Post by mr tim esquire on 2007-02-24
Thanks for the tutorial i followed the steps but i cant use javac on the command line
tim@desk:~$ javac Guesser.class
bash: javac: command not found
thanks
tim

---

### Post by whateverdood on 2007-02-24
> **mr tim esquire said:**
> Thanks for the tutorial i followed the steps but i cant use javac on the command line
tim@desk:~$ javac Guesser.class
bash: javac: command not found
thanks
tim

Hrm - javac should be in your path (linked in /usr/bin) if you did all the stuff folks have listed.  Try:

```
sudo update-alternatives --config javac
```

You should see something like this:

```
rich@mowgli:~$ sudo update-alternatives --config javac

There are 2 alternatives which provide `javac'.

  Selection    Alternative
-----------------------------------------------
*+    1        /usr/lib/jdk1.5.0_11/bin/javac
      2        /usr/lib/jvm/java-1.5.0-sun/bin/javac

Press enter to keep the default[*], or type selection number:

```

How did you install java?

---

### Post by phossal on 2007-02-24
Removed

---

### Post by phossal on 2007-02-26
Removed

---

### Post by phossal on 2007-03-03
This [tutorial]("http://phossal.com/thread?view=702216931") has almost 9,000 views within Ubuntu Forums, and now almost 1,000 more at phossal.com. Thanks for checking it out.

---

### Post by phossal on 2007-03-18
Still one of the *best* guides for installing Java on Ubuntu!

---

### Post by FernandoMilton on 2007-03-22
<rant>
That's so lame, man. Seems like this was a very popular tutorial here on ubuntuforums, because I get here everytime I google anything about installing java on ubuntu. Unfortunately, you deleted everything from here in order to boost your little site and now it is offline. If the situation turns up to be permanent (I doubt your site will outlive ubuntuforums), this valuable piece of information will be lost forever. Lame, just lame, that goes contrary to everything Free Software stands for, it is not only about freedom of software, but freedom in general. Notice, I'm not mad because you put it on your site, but deleting it from here is just lame. 
</rant>

Anyway, I can figure it out by myself. Thanks for nothing.

---

### Post by phossal on 2007-03-23
This was a popular tutorial because I *made* it popular. It was hard work. What do I owe you?

---

### Post by FernandoMilton on 2007-03-23
> **phossal said:**
> This was a popular tutorial because I *made* it popular. It was hard work. What do I owe you?

Nothing. You are right on this point, it was your hard work, your thoughts, your "intellectual property" and you had the right to take it to wherever you wanted to. That doesn't make it less lame, barely hypocritical. What you did is not that different from turning free software in proprietary software, you turned a free tutorial in a proprietary one, even if the only price you are charging for it is the visit to your tiny site that, if it were up, it would be more a minor annoyance than anything. But, all right, **you** made it, it is your world, man, enjoy it and the couple thousands of clicks you will get a month.

---

### Post by linuxismyfriend on 2007-03-23
phossal is being really lame. He/She is acting like they created Linux. All phossal did was write a small tutorial on how to install java. Get over yourself, you wrote a tutorial on HOW TO INSTALL JAVA. nothing more. What if the people behind Ubuntu acted like phossal and decided that they weren't going to distribute ubuntu anymore. phossal's tutorial is worthless now, no matter how good it was because phossal can maybe write good tutorials but phossal is not so great at keeping their site up. phossal thanks for nothing! phossal, go back to using Windows!

---

### Post by phossal on 2007-03-23
You can view the tutorial on Ubuntu Geek's website: ubuntugeek.com, I think. It's posted by the admin, as are the other tutorials I wrote.

---

### Post by linuxismyfriend on 2007-03-23
phossal, just leave these forums and worry about the content on your "tiny site." You wasted this whole thread by deleting your posts. No one is going to go to your site because it sucks.

---

### Post by phossal on 2007-03-23
> **linuxismyfriend said:**
> Thank you phossal for the awesome HowTo, it was exactly what I was looking for.  Regarding your method for making the jar files work when double clicked, does that work for only one file or does it set all the jar files to be doubl-clickable? If not, is it possible to create a ".mime.types" file in the home directory and have something like: "application/java    jar"? Thanks!

Hmm. Quoted for posterity. I recommend editing your first ever post. People could get the wrong idea. You joined Ubuntu  Forums, and the only posts you've ever made are in this thread. One to thank and bait me, and two to insult me. Quite nice.

---

### Post by linuxismyfriend on 2007-03-23
You're right phossal. I'm new to Linux, at work I use windows and only on my free time do I use Ubuntu. I did find your tutorial very helpful and concise, thanks for the help. But I don't agree with you deleting the posts you made just to drive more traffic to your site. You are ruining this forum, what if everyone else followed your steps, then what?

---

### Post by FernandoMilton on 2007-03-24
Too good Feisty is coming to our rescue, making things simpler to install now. Here is my tutorial.
How to install Java6 on Feisty: 

sudo apt-get install sun-java6-jdk && sudo update-alternatives --config java && sudo update-alternatives --config javac

Now I think I will delete it from here, take it to somesite.50megs.myspace.net and claim this discovery was my hard work, my invention (disregarding everything I learned right here at the forums) and rejoice myself with pats on my own back, 35 cents/month richer because of Google Ads. So lame. Anyway, I already took it out of my chest now. See you later. NOT.

---

### Post by phossal on 2007-03-31
Updated for JDK 6u1

---

### Post by phossal on 2007-04-14
After a few not so pleasant requests to do so, I put the thread back together, including instructions for grabbing eclipse from eclipse.org, and adding the java plugin. Regards.

---

### Post by kinson on 2007-04-14
Hi Phossal,

thanks for the guide here :) My situation is a little different, cause I tried installing netbeans before finding this guide, so I'm a little confused as to what I've screwed up to be honest :/

What I wanted to do:
-Install Netbeans and Eclipse, get them running to see the differences
-Try and get back into Java programming. Last time I touched Java was in Windows during my college days.

What did I do?
-Download the netbeans bin package [here]("http://us1.mirror.netbeans.org/download/5_5/mlfcs/200612070100/netbeans-5_5-linux.bin").
-Install eclipse from terminal with apt-get

After that I didn't know where eclipse installed to :/ I think last night when I typed "where is eclipse" there was some path, but now it doens't return any path. So I don't know how to start it :(

As for Netbeans, When I first ran it, it said it could not find any JDK. So I tried downloading and instaling the JDK from terminal with 
```

sudo aptitude install sun-java6-jdk
```

After which there was still some problems :/ so I downloaded the netbean+java package [here]("https://sdlc2b.sun.com/ECom/EComActionServlet;jsessionid=B9D49CCD599D21D71D3A50F169E283F4"). But now that I can run the netbeans without it prompting any error. I can't seem to open any new java files or whatever. Even their "example" projects just open, and nothing happens. No source files, nothing :(

Even if I go to New->Project, there isn't anything like a "general" folder where I can select java file or whatever. So I'm very confused :(

Hopefully you can help me a little bit here. Not sure whether its directly tied to your post. If it isn't, just let me know and I'll create a new thread.

Thanks a lot in advance :)

Cheers,
Kinson

---

### Post by phossal on 2007-04-15
I say you start by posting the output to these:
```

java -version
ll /usr/bin/java
```

Anticipating your questions, I'm not sure what to propose. I don't like or use the packages. I have been able to diagnose a failed install or two, but I don't *prefer* doing that over just installing java, eclipse and netbeans as I normally would.

You can follow the tutorial to install Java and eclipse. By doing so, your new Java will become the system's default Java, and your new eclipse will take over too. I install netbeans in a very similar way. I'll outline how in the next post.

---

### Post by phossal on 2007-04-15
**Installing the Netbeans Tarball**

Appended to post #1

---

### Post by kinson on 2007-04-15
> **phossal said:**
> I say you start by posting the output to these:
```

java -version
ll /usr/bin/java
```


The results:

```

kinson@ubuntu:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
kinson@ubuntu:~$ ll /usr/bin/java
bash: ll: command not found

```
Not sure what the "ll" command you asked me to input is :/

Thanks for updating the guide. :) I'll give it a try, but can I just start off with your guide? Or do I need to uninstall/restore anything before I can begin that. Sorry, a little confused here :/

Cheers,
Kinson

---

### Post by phossal on 2007-04-15
LL is a commonly used abbreviation for ls -l. The .bashrc file shipped with my edgy had it preconfigured. 

```
ls -l /usr/bin/java
```

I don't see why you couldn't follow the guide. I sometimes do it myself, when I want to quickly work through the steps with someone.

---

### Post by kinson on 2007-04-15
Not to be a nitpick...but I followed your earlier post to go /usr/bin/java. In your last post you might have made a mistake and put /usr/lib/java.

Anyways, I've put the output of both here: :) 
```

kinson@ubuntu:~$ ls -l /usr/lib/java
ls: /usr/lib/java: No such file or directory
kinson@ubuntu:~$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2007-03-22 22:20 /usr/bin/java -> /etc/alternatives/java
kinson@ubuntu:~$

```

I was just worried if I followed an existing guide, it would be tailored for people who are starting without having installed the jdk or netbeans/eclipse, and so it'd be "clean"...mine is kinda mucked up, so I don't know whether I'd be screwing anything up :p or overwriting something :/

Cheers,
Kinson

---

### Post by phossal on 2007-04-15
What are the options when you type:
```
sudo update-alternatives --config java
```

[EDIT] It should be /usr/bin/java, yes. I can't anticipate every problem you might have, of course, but I don't think following the tutorial from scratch will cause any trouble. As another example of when I'm in a similar situation, I follow the same tutorial multiple times in order to have multiple JDKs and eclipses. I just change their file names in /usr/lib, so they don't "write over" each other. I might have Java6a, eclipse, Java6b, eclipse2, etc. You just modify the paths accordingly. You probably don't have to worry about that though. The package handles installations differently, which means your existing installations are named differently. However, it all seems a moot point, none of your existing installations work.

---

### Post by kinson on 2007-04-15
@Phossal:

```

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
      4        /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

```

I suppose that means that there are 4 versions of Java installed on my system..(doh!)

Anyways, thanks a lot for the help and lightning fast responses. I'll give this a try tomorrow evening. Need to sleep now(I don't wanna sleep, lol !) :( 

Thanks,
Kinson

---

### Post by kinson on 2007-04-16
Hi Phossal,

I've followed your instructions (except for the Eclipse IDE part, its still downloading).

I can run netbeans, but I'm still getting the same problem as before, I can launch netbeans, but I can't seem to get a "new java file" or "new java app" like in [this]("http://www.netbeans.org/kb/55/quickstart.html") example :(

And even if I try and open one of their default samples included, nothing opens up :( it creates the folder with the code, but nothing displays on the IDE :( (see screenshots)

Hopefully you can help me out here :/

Btw, is that how software is normally installed in Linux? Just download the Tar.gz, unpack and put it into the /usr/lib folder? :/

Thanks again :)

Cheers,
Kinson

---

### Post by phossal on 2007-04-16
Are you running Beryl? When I install Edgy, I download and install both Java and eclipse as I've outlined below. I don't use netbeans, but I've performed the steps as recently as a day ago, and it works fine for me. I'm not sure what to suggest for you at this point.

[EDIT] What are the images you've attached?

---

### Post by kinson on 2007-04-16
Lol, I was just curious, cause I normally install my stuff through the terminal, of if I need to download and install something from a site, its normallyl a *deb ... me <--- noob :p

And no, I'm not running Beryl or anything funky :/

---

### Post by phossal on 2007-04-16
Now that you've installed Java *again* let's see the output to these:
```
sudo update-alternatives --config java
ls -l /usr/bin/netbeans
```

---

### Post by kinson on 2007-04-16
```

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
      4        /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:
kinson@ubuntu:~$ ls -l /usr/bin/netbeans
lrwxrwxrwx 1 root root 26 2007-04-16 23:28 /usr/bin/netbeans -> /etc/alternatives/netbeans
kinson@ubuntu:~$

```

Thats the output. I enter any number when they gave me those 4 selections :/

Thanks for your patience man :)

---

### Post by phossal on 2007-04-16
Where is your Java?

---

### Post by kinson on 2007-04-16
> **phossal said:**
> Where is your Java?

Does this help? :/
```

kinson@ubuntu:~$ whereis java
java: /usr/bin/java /etc/java /usr/bin/X11/java /usr/share/java /opt/jdk1.6.0_01/bin/java /usr/share/man/man1/java.1.gz
kinson@ubuntu:~$

```

I know Java is installed, cause I'm running Azureus... :/

I followed this command of yours:
```

sudo mv Java6u1 /usr/lib
``` So I'm assuming I moved the java to /usr/lib :/

Thanks again :s

---

### Post by phossal on 2007-04-16
You need to download Java, per the tutorial, move it to /usr/lib, include it in update-alternatives, and make it the default Java. I can't do it for you. You have to follow the instructions. When you get that far, the clouds will part, the sun will shine, and your path will be clear.

---

### Post by kinson on 2007-04-16
> **phossal said:**
> You need to download Java, per the tutorial, move it to /usr/lib, include it in update-alternatives, and make it the default Java. I can't do it for you. You have to follow the instructions. When you get that far, the clouds will part, the sun will shine, and your path will be clear.

I thought I had already installed Java from the first part of your guide? I downloaded the jdk-6u1-linux-i586.bin file and extracted it, renamed the folder to Java6ul and moved it to /usr/lib

then I did the following commands
```

kinson@ubuntu:~$ sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 300
Password:
kinson@ubuntu:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
      4        /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:
kinson@ubuntu:~$ sudo ln -s /usr/lib/Java6u1/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
ln: creating symbolic link `/usr/lib/firefox/plugins/libjavaplugin_oji.so' to `/usr/lib/Java6u1/jre/plugin/i386/ns7/libjavaplugin_oji.so': File exists
kinson@ubuntu:~$

```
I'm guessing the last error is cause I've executed that command before?

So I've installed Java right? So I've got Java and netbeans installed :/ Am I supposed to make a selection when I perform "sudo update-alternatives --config java"?

---

### Post by phossal on 2007-04-16
Try this:
```
sudo update-alternatives --remove-all java
sudo update-alternatives --display java
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 601
sudo update-alternatives --display java
```

It will look like this:

```
bash 3.1:sudo update-alternatives --remove-all java
bash 3.1:sudo update-alternatives --display java
No alternatives for java.
bash 3.1:sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 601
bash 3.1:sudo update-alternatives --display java
java - status is auto.
 link currently points to /usr/lib/Java6u1/bin/java
/usr/lib/Java6u1/bin/java - priority 601
Current `best' version is /usr/lib/Java6u1/bin/java.
bash 3.1:

```

It will totally botch your existing Java setups. But, assuming you did download Java according to the tutorial, it'll get you right where you should be. If you didn't download it, you'll then be forced to. Are you running Edgy, 6.10? If not, avoid this.

---

### Post by kinson on 2007-04-16
Almost the same, but the last line still says no versions available :(

```

kinson@ubuntu:~$ sudo update-alternatives --remove-all java
kinson@ubuntu:~$ sudo update-alternatives --display java
No alternatives for java.
kinson@ubuntu:~$ sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 601
kinson@ubuntu:~$ sudo update-alternatives --display java
java - status is auto.
 link currently points to /usr/lib/Java6u1/bin/java
No versions available.
kinson@ubuntu:~$

```


...Crap...just read that part that you told me to avoid this if I'm not running Edgy !!! :( I'm running Dapper :( Man..I missed that line at the start...bleh....so this whole guide doesn't apply to me huh? :/ 

Sorry for wasting so much of your time :(

Thanks anyways :)
Kinson

---

### Post by phossal on 2007-04-16
lol Let's keep moving forward. Try this now.

```
cd /usr/lib/Java6u1/bin
pwd
ls
```

I'd like to see the output to those.

---

### Post by kinson on 2007-04-16
```

kinson@ubuntu:/usr/lib/Java6ul$ cd bin
kinson@ubuntu:/usr/lib/Java6ul/bin$ pwd
/usr/lib/Java6ul/bin
kinson@ubuntu:/usr/lib/Java6ul/bin$ ls
appletviewer   java          jcontrol    jstack        rmic         wsgen
apt            javac         jdb         jstat         rmid         wsimport
ControlPanel   javadoc       jhat        jstatd        rmiregistry  xjc
extcheck       javah         jinfo       keytool       schemagen
HtmlConverter  javap         jmap        native2ascii  serialver
idlj           java-rmi.cgi  jps         orbd          servertool
jar            javaws        jrunscript  pack200       tnameserv
jarsigner      jconsole      jsadebugd   policytool    unpack200
kinson@ubuntu:/usr/lib/Java6ul/bin$

```

Thanks :)

Lol, Azureus wont start now, probably because we removed java :p

---

### Post by phossal on 2007-04-16
```
sudo update-alternatives --config java 
```
And select the right (only) one.

I've never used Dapper. My impression is that its version of update-alternatives has slightly different syntax. Perhaps the install command is slightly different. It appears not to have accepted a priority, and it appears not to have defaulted Java. You could man update-alternatives, or ask someone who knows that version better.

---

### Post by kinson on 2007-04-16
```

There are 0 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------

Press enter to keep the default[*], or type selection number:

```

... :'(

---

### Post by phossal on 2007-04-16
I'm unfamiliar with the Dapper's syntax for update-alternatives. The work-around is this:
```
gedit ~/.bashrc
```

When it opens, you'll find a line something like this
PATH=<SOMETHING>

Add the following export line, and edit the PATH line as shown:
```
export JAVA_HOME='/usr/lib/Java6u1/bin'
PATH=$JAVA_HOME:<SOMETHING>
```

Then save and close the file. Then issue:
```
source ~/.bashrc
```

I suggest you still man update-alternatives to figure out how to install on your system.

---

### Post by kinson on 2007-04-16
this is the bashrc file
```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

I can't seem to find any PATH inside. I'm actually wondering whether I screwed up something badly :p it seems so complicated :p

---

### Post by phossal on 2007-04-16
If you've totally destroyed your system, you can always install Edgy. I'm pretty sure I can get Java installed on that. ;)

Just man update-alternatives to figure out how the install command works.

```
man update-alternatives
```

The syntax will affect how you install eclipse and netbeans, too. 

I have to run a few errands, get some lunch, pick up my check from Ubuntu for support ;) See you in a bit.

---

### Post by kinson on 2007-04-16
> **phossal said:**
> If you've totally destroyed your system, you can always install Edgy. I'm pretty sure I can get Java installed on that. ;)

Just man update-alternatives to figure out how the install command works.

```
man update-alternatives
```

The syntax will affect how you install eclipse and netbeans, too. 

I have to run a few errands, get some lunch, pick up my check from Ubuntu for support ;) See you in a bit.

No worries :) I'm planning to install Feisty when its released this week, so I'll probably have to go through the whole thing again :) Thanks again for your time :)

Cheers,
Kinson

---

### Post by phossal on 2007-04-17
Kinson, you can add this into your ~/.bashrc at the bottom of the file:

```
export JAVA_HOME='/usr/lib/Java6u1/bin'
PATH=$JAVA_HOME:$PATH
```
Once you've saved it and closed it, then issue:
```
source ~/.bashrc
```

And try to launch eclipse.

---

### Post by kinson on 2007-04-17
> **phossal said:**
> Kinson, you can add this into your ~/.bashrc at the bottom of the file:

```
export JAVA_HOME='/usr/lib/Java6u1/bin'
PATH=$JAVA_HOME:$PATH
```
Once you've saved it and closed it, then issue:
```
source ~/.bashrc
```

And try to launch eclipse.

I did that, but I didn't install eclipse as per your guide(as I mentioned before), i installed it through apt-get. And last night I was trying to get java to work, I think I installed JRE 1.4 or something like that.

I've added those 2 lines to my bashrc, and done "source ~./bashrc". but when I try to update alternatives:
```

kinson@ubuntu:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/j2se/1.4/bin/java). Nothing to configure.
kinson@ubuntu:~$

```

And obviously when I try to run netbeans, it says some error needing java greater than 1.4 :/

When I try to run eclipse I get the error message "The custom VM you have chosen is not a valid executable"(popup).

```

kinson@ubuntu:~$ eclipse&
[1] 598
kinson@ubuntu:~$ using specified vm: /usr/lib/Java6u1/bin

```

:/

---

### Post by phossal on 2007-04-17
Yeah, I know the eclipse error. It's because the packaged version uses a separate file to list the locations of the JVM you're using, rather than the environment variable JAVA_HOME. I tried to see if the syntax for update-alternatives is different on Dapper, but no one will answer me. So I don't know how to proceed that way either.

Frustrating, Kinson. :(

---

### Post by kinson on 2007-04-17
I think it might be better if we just drop it for the moment, I don't wanna be spamming up your thread :P and considering I'm gonna install Feisty on release in 2 days time, it really isn't that big an issue...I kinda want my azureus back running though :/

Thanks a lot for your patience and helpfulness anywyas :)

Cheers,
Kinson

---

### Post by phossal on 2007-04-17
I'd like to read about Dapper's update-alternatives. Would you mind attaching this: 
```
man update-alternatives > ~/Desktop/ua.txt
``` 
Or posting the output?

If I knew the syntax, we could make things work: 
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java 60
sudo update-alternatives --config java
```

---

### Post by kinson on 2007-04-17
Uploaded.

```

kinson@ubuntu:~/Desktop$ sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java 60
Password:
kinson@ubuntu:~/Desktop$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +    1        /usr/lib/j2se/1.4/bin/java
      2        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

```

Thanks :)

---

### Post by phossal on 2007-04-17
Okay, so if you did that, you can select choice #2, which is the Java that was selected previously. Then azureus should work. Thanks, too, for uploading ua.txt

---

### Post by phossal on 2007-04-17
I'm curious to know how you managed to get those options back in update-alternatives? Did you use the install command, or did you download packages again?

---

### Post by kinson on 2007-04-17
Thanks a lot for your help in helping me get Azureus working again :)

Unfortunately I don't know what I did to make it come back :( I just followed your instructions that you posted here, and didn't do anything else... weird :/

---

### Post by phossal on 2007-04-17
What?! So that works, but the other command - the one to install the new java - doesn't? ](*,) It couldn't be the --install command! You must've downloaded the package again or something?

---

### Post by kinson on 2007-04-17
I did install Java(JRE I think) through automatix, but that was last night(about 24 hours ago) after you said you had to run some errands. 

And I couple of hours ago, the last few things I did that were associated to Java was to follow your instructions on this post :confused:  So..weird :p

---

### Post by linuxismyfriend on 2007-04-22
phossal,

Thank you for posting the instructions back here. Your tutorial is by far the best and most informative (I'm tired of searching for instructions on how to install something and the instructions are just "1. Add the repositories 2. Install"). Thanks again for an awesome tutorial, it is exactly what I was looking for and is way better than using Synaptic Package Manager. I just installed 7.04 and so I had to come back here for your instructions.

---

### Post by slowhands36 on 2007-04-25
> **phossal said:**
> **INSTALLING JAVA (JDK/JRE)**
Here is the updated version used to install Java's JDK 6u1 on Edgy. The method doesn't use packages, opting to use Sun's .bin file instead. Visit [java.sun.com]("http://java.sun.com/javase/downloads/index.jsp") to download their .bin file. You probably want: jdk-6u1-linux-i586.bin.

[COLOR="SlateGray"]**STEP: **[/COLOR]Download it to your desktop. Once it's fully downloaded, open a command prompt and execute it like so:
```

cd ~/Desktop
sudo chmod +x *.bin
sudo sh ./jdk*.bin
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Executing the .bin file creates a folder on your desktop named jdk1.6.0_01. Rename that folder to Java6u1. Now move that folder to /usr/lib

```
sudo mv Java6u1 /usr/lib
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Now add Java to update-alternatives and make it the default like so:

```
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 300
sudo update-alternatives --config java
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Don't forget your Java plugin

```
sudo ln -s /usr/lib/Java6u1/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
```





**INSTALLING ECLIPSE**
Download eclipse directly from eclipse.org. You probably want: [eclipse-SDK-3.2.2-linux-gtk.tar.gz]("http://download.eclipse.org/eclipse/downloads/drops/R-3.2.2-200702121330/download.php?dropFile=eclipse-SDK-3.2.2-linux-gtk.tar.gz")

[COLOR="SlateGray"]**STEP: **[/COLOR]Download the file to your desktop. Right-click and extract it. Move it to the directory of your choice. (I use /usr/lib)

[COLOR="SlateGray"]**STEP: **[/COLOR]Add links to /usr/bin (edit your paths as necessary):

```
sudo update-alternatives --install /usr/bin/eclipse eclipse /usr/lib/eclipse/eclipse 300
sudo ln -s /usr/lib/eclipse/startup.jar /usr/bin
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Add eclipse to the menu:

Right-click Applications -> Edit Menus -> Programming -> New Item ->
Icon: /usr/lib/eclipse/icon.xpm
Name: eclipse
Comment: Launch eclipse
Command: eclipse





**INSTALLING NETBEANS**

**[COLOR="SlateGray"]STEP: [/COLOR]**Grab the Netbeans Tarball ([Netbeans-5_5.tar.gz]("http://dlc.sun.com/netbeans/download/5_5/mlfcs/200612070100/netbeans-5_5.tar.gz")) from netbeans.org. Save it to your desktop. Right-click and extract it.

**[COLOR="SlateGray"]STEP: [/COLOR]**Move it to /usr/lib/netbeans
```
cd ~/Desktop
sudo mv netbeans /usr/lib/
``` 

**[COLOR="SlateGray"]STEP: [/COLOR]**Add links to /usr/bin (Edit your paths as necessary):
```
sudo update-alternatives --install /usr/bin/netbeans netbeans /usr/lib/netbeans/bin/netbeans 300
```

[COLOR="SlateGray"]**STEP: **[/COLOR]Add netbeans to the menu:

Right-click Applications -> Edit Menus -> Programming -> New Item ->
Icon: /usr/lib/netbeans/nb5.5/netbeans.png
Name: netbeans
Comment: Launch Netbeans
Command: netbeans


---------------------------------------------------------------------------------
[COLOR="SlateGray"][SIZE="1"]The java packages do, in fact, still use the .bin file from SUN. They're just additional wrappers. By installing using the method above, you're able to install multiple JDK's, which can be set as defaults using update-alternatives --config. In addition, you can install older versions of the JDK, which are all available at the SUN site for Java.[/SIZE][/COLOR]

I did everything and when i try to move the file after renaming it it tells me i cant move it cause iam not the owner is there a way around this.Iam new to unbuntu and linux in general any help would be greatly appreciated

---

### Post by mikawber on 2007-05-05
how do I go about uninstalling eclipse or netbeans?

---

### Post by asymmetric on 2007-05-17
thanks, a great guide

---

### Post by netvampire on 2007-06-06
worked great. thanks :)

---

### Post by xpan on 2007-06-27
is there any way to increase the performance of eclipse IDE?

---

### Post by phossal on 2007-08-03
Does anyone think this needs an update? I know the JRE update has changed, but the important steps still seem accurate.

---

### Post by spaceW on 2007-08-18
thanks phossal, your tutorial worked well for me.

> **phossal said:**
> Does anyone think this needs an update? I know the JRE update has changed, but the important steps still seem accurate.

besides java 6 being on update 2, eclipse 3.3 is out now.  so, sure, why not update those numbers in the tutorial?

oh, also, i couldn't find a startup.jar so i skipped that line... everything seems to be working fine though.

---

### Post by taisao on 2007-08-21
yes, please update it :KS

---

### Post by happyface_0 on 2007-08-27
Can someone help me? I have been trying forever to get JDK 6u2 to install Edgy Eft. To start, I'm using Ubuntu on a USB drive and would like Java development on-the-go. But this shouldn't make a difference.

I followed the instructions of the original post (except with 6u2), and now *java -version* displays: [B]bash: java: command not found
[/B]

Originally I had java-gcj installed, but I also removed that.

More output:
```
sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/Java6u2/bin/java). Nothing to configure.

```

When opening Eclipse 3.3:
```
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/home/ubuntu/eclipse/jre/bin/java
java in your current PATH
```

Also, if I install sun-java6 using synaptic I get this error: [http://ubuntuforums.org/showthread.php?t=414851](http://ubuntuforums.org/showthread.php?t=414851)

Please help, I really need this working.
Thanks!

---

### Post by jamesstansell on 2007-08-28
Happyface_0, any luck with your feisty install?

---

### Post by adredz on 2008-05-07
phossal thanks for this excellent HOW-TO. it's perfect for Hardy.:)
though there is a minor glitch i encountered. whenever i close the app, a prompt pops up that tells me:
> Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.
can you please tell me what does it mean and how to resolve it? sorry for my ignorance...

---

### Post by phossal on 2008-06-16
adredz, thanks for the compliment. As for the pop-up, I can't say for sure. I haven't used Ubuntu seriously for more than a year, and I've basically forgotten everything I knew. :(

---

