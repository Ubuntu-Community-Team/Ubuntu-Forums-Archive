---
title: "logging into my college account w/ ssh, default is Java build 1.4, need 1.5, help?"
date: 2006-03-12
forum: Programming Talk
---

### Post by ImplicitProcrastination on 2006-03-12
Hi there,

Bare with me because their may be another thread devoted to this topic or this may be completely out of place on these forums all together, but any help would be enormously appreciate it. If this is a re-post it's because I wasn't exactly sure how to precisely word my question and therefore had trouble coming up with search terms. I apologize for any of this.

I log into my college's server using ssh, and do my computer science labs from home thusly. The particular code I'm working on right now requires Java build 1.5, which I know (based on secondhand knowledge) is already installed on the machine. However a "java -version" reveals that this isn't the version I was running, and the guy in my labs told me there was a way to change that so I don't have to email my code back and forth to myself all the time... but he forgot to tell me how and I really need to get this work done efficiently tonight (I seem to be procrastinating now). Y'all are more likely to respond to me than he is sooner.

So I appeal to you guys for any ideas.

Please?

---

### Post by Zelut on 2006-03-12
Concerning the java I believe that is NOT included by default because it has a different license & you need to install it yourself.  If you're familiar enough with adding repos you should be able to get ahold of the j2re1.5 package if you add this line to your sources.list
> # Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free  This may be against some licensing in your location, blah blah blah, etc etc etc..

As far as not emailing the code back & forth.. I'm not sure what he would mean.

---

### Post by engla on 2006-03-12
This is pretty trivial, but I assume you want all our hit-and-miss suggestions.

I don't have java at home, but I logged into *my* university, where we had to use java in the first year's courses...

Java 5.0 /1.5 is used by default there, but if I type
$ java
and then hit <tab> I get a list of different java programs, among them "java14"
Try something similar on the box you are using, make it list completions for "java", and see if there is a binary called java15 java5 java-1.5 or anything like that.

Good luck.

---

### Post by ImplicitProcrastination on 2006-03-12
nope, all i get is javah javap javac and javadoc. I forgot to mention that my cs server uses gentoo, and I do not have root priviliges.

Guess I'll just copy and paste for awhile.

---

### Post by knalle on 2006-03-12
if your desperate just download the sdk tarball from java.sun.com, unpack in your home dir and set a new JAVA_HOME in your .bash_profile
then put the sdk's bin path infront of the system path in .bash_profile

---

### Post by jerome bettis on 2006-03-13
they probably have 1.5 installed, but 1.4 is just the one that's linked to in your path.

find / -type f -iname "javac" -o -iname "java" 2>/dev/null

type that and maybe you can track it down.  if you do, you can type
alias javac="/path/to/1.5/javac" (same for java or anything else you need).  you could put those alias lines in your ~/.bashrc file to have that be the default.

---

### Post by ImplicitProcrastination on 2006-03-13
jerome, that's hot... it turned up like a million results... I'm gonna try to figure out which one makes most sense.

engla, you look exactly like somebody I met last semester... and if I'm not mistaken and that's German on your website that's really really weird

knalle thanks very much for your input, I'l give it a try should jerome's suggestion fail.


sorry about the prior cussing, didn't realize this forum was censored.

---

### Post by ImplicitProcrastination on 2006-03-13
Well I tried all the ones that looked promising from the enourmous list it produced, and none of them seem to be 1.5 (although they swear up and down it's in there somewhere). Not shit.

knalle are you talking about ~/.bashrc? and what do you mean about setting a new JAVA_HOME?

---

### Post by ImplicitProcrastination on 2006-03-13
This may be an annoying thing to ask but what does -o 2>/dev/null and f and -iname do?

Oh yeah, and my dude emailed me back to suggesting a command to try... it totally didnt work.

---

### Post by jerome bettis on 2006-03-13
for i in `find / -type f -iname "java"  2> /dev/null` ; do echo $i ; $i -version ; echo ; done

that will run all versions of java with the -version option, you could put " | grep 1.5" (no quotes) at the end if you want, if nothing shows up than java 1.5 is not installed.

-type f tells the find command to look for files (-type d for dirs etc etc)

-iname "java" says look for files named java, you can use wildcards in here too

-o means or, -iname "x" -o -iname "y" -o -iname "*.z" will find files named x, y, and anything that ends in .z

2> /dev/null redirects stderr to /dev/null so you don't see error messages (without it, permission denied will be all over the place).  /dev/null is a write only file, a black hole if you will.

---

### Post by ImplicitProcrastination on 2006-03-13
awesome, trying it out right now, its like a little for loop that you run from the command line...

ok, im guessing stderr stands for something like standard error, and I can dig the greater than sign... but what's 2? (somebody should make an ubuntuforums book)

---

### Post by ImplicitProcrastination on 2006-03-13
ok, there are so many files on the server with that name that trying to run them all in one command seems to crash it flat on its ***.

I'll reboot and try to be patient and get back at you.

---

### Post by ImplicitProcrastination on 2006-03-14
It turns out my guy was wrong, and the Java 1.5 actually wasn't installed. I found this out after emailing higher up in the chain.

So I effectively have wasted your guys' time. However I thoroughly enjoyed the opportunity to learn some new things I can do with a command prompt, and for that I thank you.

---

### Post by jerome bettis on 2006-03-14
right there's probably a whole bunch of network file systems somewhere in /, that would make it take a long *** time.

try replacing the / right after find with /usr /opt

edit
i'm slow nevermind, tell that guy i said he's a dumbass!  :-P

you really don't need to install it, if you have the disk space you could just put the necessary parts of the sdk in your home directory.

---

### Post by ImplicitProcrastination on 2006-03-14
will do :)

he probably got that idea from the admin promising to install it tomorrow everytime we bug him about it each week.

what might those parts be?

how much space do they take? i have like a 40 meg quota

i also recently realized that I could just install sshd and do what I was doing in reverse.

---

### Post by knalle on 2006-03-14
[QUOTE=ImplicitProcrastination]Well I tried all the ones that looked promising from the enourmous list it produced, and none of them seem to be 1.5 (although they swear up and down it's in there somewhere). Not shit.

knalle are you talking about ~/.bashrc? and what do you mean about setting a new JAVA_HOME?[/QUOTE]

put this in the end of your **.bash_profile**:

```

export JAVA_HOME="/home/implicitprocrastination/unpackedjdkpath/"
export PATH="/home/implicitprocrastination/unpackedjdkpath/bin/:${PATH}"

```

logout and login

---

