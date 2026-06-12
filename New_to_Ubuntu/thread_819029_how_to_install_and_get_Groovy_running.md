---
title: "how to install and get Groovy running"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by jocko_johnson on 2008-06-05
Hi,
I recently downloaded Groovy and extracted it to:
~/dev/env/groovy/groovy-1.5.6

I updated /etc/environment to:
GROOVY_HOME="~/dev/env/groovy/groovy-1.5.6"
PATH="/usr/bin:/bin:/usr/sbin:..........:$GROOVY_HOME/bin"

when I type "groovy" in the terminal I get this message:
"The program 'groovy' is currently not installed.  You can install it by typing:
sudo apt-get install groovy
bash: groovy: command not found"

I am having the same issue with Grails.

Any help is greatly appreciated.
Thanks

---

### Post by ajmorris on 2008-06-05
hi there,
have you tried running ```
sudo apt-get install groovy
``` from a terminal? and then run groovy the same way you are currently.

AJ

---

### Post by ameseisch on 2008-06-08
I installed groovy with the .deb file, and that didn't work either...

user@user:~$ groovy -version
groovy: JAVA_HOME not set and cannot find javac to deduce location, please set JAVA_HOME.
user@user:~$ groovy
groovy: JAVA_HOME not set and cannot find javac to deduce location, please set JAVA_HOME.

so actually it might have halfway worked... but didn't set enviroment variables for me so I don't really know how to do that at this point.

---

### Post by ajmorris on 2008-06-08
> **ameseisch said:**
> I installed groovy with the .deb file, and that didn't work either...

user@user:~$ groovy -version
groovy: JAVA_HOME not set and cannot find javac to deduce location, please set JAVA_HOME.
user@user:~$ groovy
groovy: JAVA_HOME not set and cannot find javac to deduce location, please set JAVA_HOME.

so actually it might have halfway worked... but didn'e t set enviroment variables for me so I don't really know how to do that at this point.

groovy exists in the repositories, you can install it via sudo apt-get install groovy, but, with the above error message, you can do:
```
export JAVA_HOME="<path>"
``` Replace <path> with your path that you want. This export command however only lasts for the length of your bash session, i.e. until you close your terminal, if it works, then you can make it permanent by adding it to ~/.profile in the form of:
export JAVA_HOME="<path>"

AJ

---

### Post by ameseisch on 2008-06-09
yeah, got this going. after running the .deb files for groovy and grails

add this line:

export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun

to ~/.profile where java-1.5.0-sun is a symlink to most current java version
and add these lines:

### Groovy
GROOVY_HOME=/usr/share/groovy
PATH=$PATH:GROOVY_HOME/bin
export GROOVY_HOME PATH

### Grails
GRAILS_HOME=/usr/share/grails
PATH=$PATH:GRAILS_HOME/bin
export GRAILS_HOME PATH

to ~/.bashrc

then things should be ready to go I think. If you manually installed the files somewhere else just modify these instuctions as needed.

---

### Post by Hendrixski on 2008-09-24
I'm amazed there aren't more posts here about Groovy and Grails. Having used this on my latest project I'm convinced that this is the future of Enterprise web development. I'm confident in saying this because Rails will never be enterprise-ready and PHP is for loosers.

So, if you stumble upon this post, give groovy a try! So just sudo apt-get install groovy and then try a few examples from a manual.

---

### Post by ameseisch on 2008-09-25
Groovy/Grails is definitely more powerful than PHP, but PHP has it place. I still use wordpress for blogs for example. Just simpler, and sometimes thats what you need.

a pimped out g-edit is what I have been using for my development environment. I tried NetBeans, but wasn't liking it. What has everyone else been using?

---

### Post by anung524 on 2009-08-18
@ameseisch

thanks mate,
i've been trying to set a path for my groovy installation.
it's solved now.

i just put these:
```
export JAVA_HOME=/usr/lib/jvm/java-6-sun/
export GROOVY_HOME=/usr/share/groovy/
export PATH=$PATH:$GROOVY_HOME/bin
```

to ~/.bashrc

i don't have any experience in programming nor even Java, but one of my colleagues said its pretty easy, so i'm willing to try it :D

regards.

---

### Post by krtica on 2010-06-19
I found another solution. I'm using Ubuntu 10.04.

After I installed groovy and trying to use it I also had message:
```
groovy: JAVA_HOME not set and cannot find javac to deduce location, please set JAVA_HOME.
```
So I tried to use javac. I received a next message:
```
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
Try: sudo apt-get install <selected package>
```
So I did it:
```
sudo apt-get install openjdk-6-jdk
```
After that, everything worked "out-of-box". No files editing needed.

---

