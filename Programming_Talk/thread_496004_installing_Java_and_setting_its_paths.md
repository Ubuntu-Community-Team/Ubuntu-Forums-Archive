---
title: "installing Java and setting its paths"
date: 2007-07-08
forum: Programming Talk
---

### Post by lamdacore on 2007-07-08
Hi,

I have installed linux on Linux Mint: Cassandra but am facing problems in setting the classpath to invoke javac to run java programs. I know that this is a ubuntu forum but Linux Mint is a distribution based on Ubuntu. So i think solution u provide would easily solve many of my problems.

Anyhow, to simplify the problem, I did some homework on my own and managed to set some variable in /etc/environment as:

$CLASSPATH = /etc/java/jdk1.6.0_01/lib:.
$JAVA_HOME = /etc/java/jdk1.6.0_01/
$PATH = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

Now the main problem is that i cannot call 'java' or 'javac' at the terminal. However, when i get to the folder: cd $JAVA_HOME/bin/

and type './java' or './javac' only then do these executables work.

what i want is that i would like both of these executables to run from anywhere in filesystem directory when in the terminal. Because of this problem many IDEs will not compile any Java program.

Please help

Thanks

Lamdacore

---

### Post by AlexThomson_NZ on 2007-07-08
I am not sure how Mint installs Sun's Java, but if you adjust your path it should work:
export $PATH = /etc/java/jdk1.6.0_01/bin:$PATH

Otherwise you can fiddle around with symlinks, but I prefer my way.

// Looking forward to Linux being able to ship with Sun's java installed properly from the get-go! :)

---

### Post by jespdj on 2007-07-09
> **lamdacore said:**
> 
$CLASSPATH = /etc/java/jdk1.6.0_01/lib:.

Do not set the CLASSPATH environment variable like this. This is not necessary for Java 6.
Adding /etc/java/jdk1.6.0_01/lib to your classpath is wrong, since there are no *.class files in that directory.
Just remove this line from your /etc/environment.

Also, you have installed your JDK in a strange place. The /etc directory is meant for system **configuration files** only. You should not put executables or whole software packages in your /etc directory. A more logical place to install this would be /usr/share/java, for example.

---

### Post by nicktmro on 2007-07-12
You might find that you already have java installed in /usr/lib/jvm
Maybe it is something like **/usr/lib/jvm/java-1.6.0-sun**

HTH

---

### Post by Crinos512 on 2007-07-14
I have installed Sun Java using **"sudo sh jre-6u2-linux-amd64.bin",** having downloaded it from the Sun website, however when I use:
```
 java --version
```
I get:
```
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.
```

from what I can tell this is the default java that comes with Ubuntu... what did I do wrong? :confused:

---

### Post by grado on 2007-07-15
nothing is wrong, except you have to set path to your new java installation. Add this line to your bashrc

```
export PATH=/path/to/your/java/installation:$PATH
```

if you are using csh or tcsh add this to .cshrc
```

setenv PATH /path/to/your/java/installation:$PATH
```

If you don't know what is the /path/to/your/java/installation then try to figure out.

```

find / -name java --print
```

---

### Post by Crinos512 on 2007-07-15
Thanks for the info...

when I try  typing your suggestion into the terminal I get:

```

crinos@Fortress:~$ setenv PATH /home/crinos/jre1.6.0_02/bin/java:$PATH
bash: setenv: command not found

```

thoughts? (Sorry, I am very new @ linux.)

---

### Post by kknd on 2007-07-15
1) Put our Java under a more common place like /usr/lib/java
2) Put that lines into your profile (/etc/profile for system-wide, or ~/.profile)

JAVA_HOME = /usr/lib/java
CLASSPATH = /usr/lib/java/lib
PATH=$PATH:JAVA_HOME/bin
export JAVA_HOME CLASSPATH PATH

3) Reboot your system (its simplier to reboot).

That should do. If it still gives you another Java vm, then do update-alternatives thing and fix that.

---

### Post by Crinos512 on 2007-07-15
OK I moved my directory like you suggested: **sudo mv jre1.6.0_02/ /usr/lib/java**

and altered my /etc/profile to read:
```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

JAVA_HOME = /usr/lib/java
CLASSPATH = /usr/lib/java/lib
PATH=$PATH:JAVA_HOME/bin
export JAVA_HOME CLASSPATH PATH
```

**[COLOR="Red"]:rebooted:[/COLOR]**

When I typed **sudo update-alternatives --config java ** I get:
```
There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.
```

:(

---

### Post by jespdj on 2007-07-16
> **Crinos512 said:**
> OK I moved my directory like you suggested: **sudo mv jre1.6.0_02/ /usr/lib/java**

and altered my /etc/profile to read:
```

JAVA_HOME = /usr/lib/java
CLASSPATH = /usr/lib/java/lib
PATH=$PATH:JAVA_HOME/bin
export JAVA_HOME CLASSPATH PATH
```
[/CODE]

:(

Like I already wrote above, **DO NOT** set your CLASSPATH to /usr/lib/java/lib. This makes no sense. REMOVE this from your .profile. It should look like this:

```
# Set JAVA_HOME to the path where you installed Java
JAVA_HOME=/usr/lib/java

# Notice the '$' before JAVA_HOME, you forgot that!
PATH=$PATH:$JAVA_HOME/bin

export JAVA_HOME PATH
```
> When I typed sudo update-alternatives --config java  I get:
This only works when you install Java via the package management system, not when you install Java manually as you are doing.

Why don't you just install Java 6 via the package management system? That's much easier than trying to do it manually. Or is there some reason why you need the very latest version of Java 6 (which is Update 2)?

Try this instead of trying to install it manually:
```
sudo apt-get install sun-java6-jdk
```

---

### Post by jespdj on 2007-07-16
.

---

### Post by Crinos512 on 2007-07-16
The main reson I do not just use Apt-get is that I am on a dial up connecting through Gnome-ppp... @ 28.8 bps if I'm lucky. #-o

I had downloaded the AMD64 tarball from SUN's site a while back but have been struggling with it ever since.

I'll google "Java sun AMD64 .deb" while I have the fast work connection and take it hom on a thumb drive. (and of course undo all the mods to my /etc/profile.)

Thanks for the assist.

---

### Post by kknd on 2007-07-16
If you know someone that have Ubuntu installed, you can just download the package to transfer to you:

sudo apt-get --download-only install sun-java6-jdk

---

### Post by Crinos512 on 2007-07-16
> **kknd said:**
> 
**sudo apt-get [COLOR="Red"]--download-only[/COLOR] install sun-java6-jdk**

Now that's a helpful hint! I'll remember that one :D

I have grabbed (from [http://packages.ubuntu.com/feisty]("http://packages.ubuntu.com/feisty/")/ ):
[LIST]
[*]sun-java6-jdk_6-00-2ubuntu2_amd64.deb
[*]sun-java6-jre_6-00-2ubuntu2_all.deb
[*]sun-java6-fonts_6-00-2ubuntu2_all.deb
[*]sun-java6-bin_6-00-2ubuntu2_amd64.deb
[*]defoma_0.11.10_all.deb
[/LIST]

**Total: 37.4 Mb**
Hope that is all the big dependencies, I don't have a problem with downloading a few 100k debs, but I don't want to be downloading for 3 days straight! :D

---

### Post by jespdj on 2007-07-16
Since you are posting this in the Programming forum, I guess you are planning to write and compile your own programs in Java. If that's the case, then you need to download the **JDK** and not the JRE.

The JRE (Java Runtime Environment) does not include the Java compiler and other tools that you need to develop Java programs. The JDK (Java Development Kit) does.

---

### Post by Crinos512 on 2007-07-16
good catch. I hadn't noticed that....

Thanks again!

(turns out the JDK depends on the JRE, so I just grabbed that one as well.)

---

### Post by Crinos512 on 2007-07-16
Arg! each of the Sun-Java-*.deb files is dependent on 2 of the other ones in a catch-22 making it impossible to load 1 at a time in the correct order... if I try to install while online it reaches out to the repo and ignores the fact that all the files it needs are in the same dir!

<frustrated>

have done a man on **gdebi** in the hopes I could tell her to look in the dir 1st.... but sadly no.

---

### Post by jespdj on 2007-07-17
Indeed, it looks like sun-java6-bin depends on sun-java6-jre and vice versa...

You can add the directory on your disk that contains the *.deb files as a source for dpkg. I don't know exactly how to do this, but you can find more info on the [man page of sources.list](http://linux.die.net/man/5/sources.list).

You will have to add the correct line to /etc/apt/sources.list. The line will have to start with the "file://" schema, as the man page says:
> The file scheme allows an arbitrary directory in the file system to be considered an archive. This is useful for NFS mounts and local mirrors or archives.
Have a look at the man page to find out the details...

---

### Post by Crinos512 on 2007-07-17
:D

I cheated. (details follow)

**man apt-get**

```

Name
apt-get - APT package handling utility -- command-line interface 
Synopsis

apt-get [ -hvs ] [ -o=config string ] [ -c=file ] { update | upgrade | dselect-upgrade | install pkg ... | remove pkg ... | source pkg ... | build-dep pkg ... | check | clean | autoclean } 
Description
...
Files
/etc/apt/sources.list 
Locations to fetch packages from. Configuration Item: Dir::Etc::SourceList. 
/etc/apt/apt.conf 
APT configuration file. Configuration Item: Dir::Etc::Main. 
/etc/apt/apt.conf.d/ 
APT configuration file fragments Configuration Item: Dir::Etc::Parts. 
/etc/apt/preferences 
Version preferences file. This is where you would specify "pinning", i.e. a preference to get certain packages from a separate source or from a different version of a distribution. Configuration Item: Dir::Etc::Preferences. [COLOR="Blue"][B]
/var/cache/apt/archives/ 
Storage area for retrieved package files. Configuration Item: Dir::Cache::Archives. [/B][/COLOR]
/var/cache/apt/archives/partial/ 
Storage area for package files in transit. Configuration Item: Dir::Cache::Archives (implicit partial). 
/var/lib/apt/lists/ 
Storage area for state information for each package resource specified in sources.list(5) Configuration Item: Dir::State::Lists. 
/var/lib/apt/lists/partial/ 
Storage area for state information in transit. Configuration Item: Dir::State::Lists (implicit partial).
See Also
...
```

SO.... I copied all of my Debs into /var/cache/apt/archives/ (as sudo) and then  ran **sudo apt-get install sun-java6-jdk_6-00-2ubuntu2_amd64.deb**

worked like a charm. :)

---

