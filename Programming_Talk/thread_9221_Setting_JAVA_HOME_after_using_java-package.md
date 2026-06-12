---
title: "Setting JAVA_HOME after using java-package"
date: 2004-12-25
forum: Programming Talk
---

### Post by offby1 on 2004-12-25
Now that I've installed the JDK 1.5 under Warty using java-package to do so, how can I figure out what to set JAVA_HOME to?  There doesn't appear to be a simple and single location for this sort of thing.

---

### Post by haha on 2004-12-27
[QUOTE=offby1]Now that I've installed the JDK 1.5 under Warty using java-package to do so, how can I figure out what to set JAVA_HOME to?  There doesn't appear to be a simple and single location for this sort of thing.[/QUOTE]

run xterm  And

$ echo $JAVA_HOME

after this, you can see your java home path

---

### Post by offby1 on 2004-12-27
Ah...

If $JAVA_HOME was already set, I would not be asking.

---

### Post by MaV on 2004-12-27
The following method may be a bit complicated ... at least I believe there must be a better solution, but this is what I came up within a few moments' thoughts.

You can get a first hint by typing:
whereis javac

The directory(-ies) shown are not likely the original, and the javac only a symbolic link, so type:
ls -al *directory*/javac
where *directory* is the one he printed the first time. This will show you the program it links to.
Continue this until you see something like */usr/lib/j2sdk1.5-sun/bin/javac* (that's the result in my case), which is the javac in the original directory. You can prove it by listing the directory; it should contain all the binaries of the SDK. So in my case JAVA_HOME has to be set to */usr/lib/j2sdk1.5-sun*.

Greets,
MaV

PS: I won't be online for the next week, so I can't give further help until then, but I'll be glad to hear if you succeded!

---

### Post by kl3rk on 2005-12-06
I think what offby is looking for is this:

user@user:~$ [COLOR="Red"]sudo update-alternatives --config java[/COLOR]

that should do it!

---

### Post by sphinx on 2005-12-06
I too have had a similar problem. You see, the 'update-alternatives' script is fine if you'd all you want to do is use java from the command line, but as far as I could tell, it didn't set the JAVA_HOME variable.

So why do I want JAVA_HOME set when the commandline worked anyway? well, the startup script for Tomcat needs to have JAVA_HOME set so it can start. So I tried setting JAVA_HOME in /etc/profile. Bingo! that works..... only when starting tomcat manually after you have logged in. Its not set when the initt.d script tries to start it at startup. I suspect /etc/profile is not run by that point.

Currently I have worked around the problem by explicly setting JAVA_HOME in my custom init script for tomcat, but I'd prefer a global place to put environment variables. /etc/profile dosn't seem to be the place.

Slackware has a way of splitting the /etc/profile file up (profile looks for scripts in a set directory, depending on the shell used), so that you can create a file for each group of env variables you want to set up. But my memory of how that all worked is fading as its been a while since I've used slackware.

So is there a global place one can put environment variables so they are available for startup scripts too?

---

### Post by RavenSensei on 2006-01-25
[QUOTE=sphinx]So is there a global place one can put environment variables so they are available for startup scripts too?[/QUOTE]

I'm looking for the same answer.  I installed 1.5 recently and I want to use eclipse as an IDE, but it won't install unless I have JAVA_HOME set and in my path.

A friend of mine told me about editing profile file and putting it there, but that didn't seem to work.

Any ideas?  I think if I could set it so that terminal read a file and set it before it started, that might work.

M@

---

### Post by Viro on 2006-01-25
A big hack is to add the definition for JAVA_HOME in .gnomerc, so that it gets set everytime you log into gnome.

---

### Post by Lov on 2006-02-12
user environment vars settings comes from a different file which is /etc/bash.bashrc. You will have to put these lines at the bottom of bash.bashrc:

JAVA_HOME="PATH_TO _YOUR_JAVA_INSTALLATION"
export JAVA_HOME

now all you need to do is logout and login again.

---

### Post by ZylGadis on 2006-02-12
I have set it in my custom init.d script for tomcat, and it works.

---

### Post by pf_ on 2006-05-22
Hi,

I have put the very ugly piece of code in my Makefile to avoid depending on the assumption that JAVA_HOME is set:

ifndef JAVA_HOME
  TEST := $(shell which java)
  ifdef TEST
    JAVA_HOME  := $(shell readlink -f $(TEST) | xargs dirname | xargs dirname )
  endif
endif

ifdef JAVA_HOME
  CXXFLAGS   += -I$(JAVA_HOME)/include -I$(JAVA_HOME)/include/$(ARCH)
endif

---

### Post by pvasener on 2007-06-13
It seems to me that the cleanest way to proceed is to add the JAVA_HOME variable definition to the /etc/environment file, don't you think?

---

### Post by nicktmro on 2007-07-12
> **pvasener said:**
> It seems to me that the cleanest way to proceed is to add the JAVA_HOME variable definition to the /etc/environment file, don't you think?

Could not agree more :)

Have a look @ [http://tmro.blogspot.com/2007/07/ubuntu-and-java-javahome-no-longer.html](http://tmro.blogspot.com/2007/07/ubuntu-and-java-javahome-no-longer.html) if you have issues with launchers as well. Setting the JAVA_HOME in the .bashrc might seem like a good idea if you only need JAVA_HOME in a terminal. But .bashrc won't help if you need to create a launcher for example :)

HTH

---

### Post by paul.reloaded on 2007-11-03
Hi. I found good solution here: [http://www.laliluna.de/blog/2007/02/22/ubuntu_environment_variable_java_home.html]("http://www.laliluna.de/blog/2007/02/22/ubuntu_environment_variable_java_home.html")

In /usr/lib/jvm are JAVA_HOMEs.

---

### Post by octoberdan on 2008-04-27
Here's a one liner to set it up. This will append JAVA_HOME=... to the last line of /etc/environment. Remember to check in /usr/lib/jvm/ ("ls /usr/lib/jvm") to make sure you're setting it to something that exists:

```

sudo bash -c "echo JAVA_HOME=/usr/lib/jvm/java-6-sun/ >> /etc/environment"

```

I bother responding again because this is the second response for googling "ubuntu java_home" which is common enough to be included in the autocomplete search bar of firefox.

---

### Post by vintermann on 2009-01-16
Thanks Octoberdan, I was looking for the "clean" way of getting JAVA_HOME set. 

Ideally, though, I'd like JAVA_HOME to be set to the same jre I chose with update-java-alternatives, since I need to switch back and forth now and then. I don't understand why update-java-alternatives doesn't just do it, but...

I thought I would be clever and run "which" with some dereferencing option to see where that symlink points to, but that doesn't seem to exist. I can't find any tool to dig through multiple file symlinks, in fact.

---

### Post by gaoagong on 2009-06-15
Sphinx,

How come /etc/profile is not the right place to put it? I am trying to run Intellij IDEA and it asks me to set up JAVA_HOME. At first I just put it in my local user bash.rc file, but it is really annoying to start the program manually from command line. Eventually, I came to the conclusion that I had to put it either in /etc/bash.rc or /etc/profile. I now just click on an icon to run Intellij.

Are there side effects to putting it in there?

It seems to me that /etc/invironment is where I should put it? I guess I'll just do that.

---

### Post by homepig on 2010-03-24
after you get to know where your java is installed, do:

1. only can run cmd line jedit
sudo vim /etc/bash.bashrc 
and add
**JAVA_HOME=/usr/lib/jvm/java-6-sun**
export JAVA_HOME

2. support gui jedit
sudo vim /etc/environment
and add
**JAVA_HOME="/usr/lib/jvm/java-6-sun"**

---

### Post by SETodd on 2010-06-04
/etc/environment is exactly what I was looking for but didn't know existed. Thanks!

---

### Post by albertwt on 2010-11-12
> **homepig said:**
> after you get to know where your java is installed, do:

1. only can run cmd line jedit
sudo vim /etc/bash.bashrc 
and add
**JAVA_HOME=/usr/lib/jvm/java-6-sun**
export JAVA_HOME

[U]2. support gui jedit
sudo vim /etc/environment
and add
[B]JAVA_HOME="/usr/lib/jvm/java-6-sun"[/B[/U]]


tahnks man after you showed to me how to add the java_home, however it didn't show up when i type the echo?

```
root@SSV:~# vi /etc/environment
root@SSV:~# echo $JAVA_HOME

root@SSV:~# export JAVA_HOME
root@SSV:~# echo $JAVA_HOME

root@SSV:~#

```

any idea in how to do this ?

---

### Post by a_nini75 on 2011-05-29
> **albertwt said:**
> 
[/CODE]any idea in how to do this ?

Hello, me too found out how, in another ubuntuforums thread:

[http://ubuntuforums.org/showthread.php?t=376632](http://ubuntuforums.org/showthread.php?t=376632)

so it seems that it's as simple as issue this command from a terminal:

source /etc/environment

---

