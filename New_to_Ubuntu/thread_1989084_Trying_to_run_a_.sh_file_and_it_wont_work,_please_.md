---
title: "Trying to run a .sh file and it wont work, please help"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by ultan on 2012-05-28
Im a very new Ubuntu user, just switched over the other day.

):P

Ive downloaded a program off the net that only runs on linux.


the program turns text into factual statements and then turns those into questions
like you put in a history book with something like

 "hitler invaded poland on september 1st 1936" 

in it and the program will make questions out of it like

 " who invaded poland on the 1st september 1936?" 

and 

"when did hitler invade poland".

i want to use it to make quiz for books in college as a study aid.

i downloaded it from 

[http://www.ark.cs.cmu.edu/mheilman/questions/](http://www.ark.cs.cmu.edu/mheilman/questions/)

the README. file just say to execute the run.sh file and it should start installing

ive tried to execute the file by clicking it and running it and clicking on it and running it in terminal.

it doesnt do anything

ive also tried changing the file so that it is executable.

it doesnt do anything.

ive tried telling it to bash run.sh 

it doesnt do anything.

ive tried using sudo and putting in  my password

it doesnt do anything.

ive tried getting help from someone who know ubuntu better but hes stumped too

Can anybody help please?

Ive been looking for this program for ages and finally got it and now i cant get it to work.

Please could somebody help me, its driving me nuts!

:lolflag:

thanks in advance for any help you

---

### Post by roton on 2012-05-28
In terminal:

chmod 700 run.sh
./run.sh

---

### Post by codingman on 2012-05-28
> **roton said:**
> In terminal:

chmod 700 run.sh
./run.sh

If you wish to edit it, replace 700 with 750

---

### Post by Lars Noodén on 2012-05-28
Is there a mailing list that you could turn to?  There might be a community using that program that could help.

The reason I suggest that is that all the standard tips and hints are missing.  I downloaded the tarball and found no installation instructions nor documentation on how to run the program once installed.  There are not even any manual pages.  

It is written in Java, so if you know a little Java maybe you can figure things out.  But does look potentially complex.

My only guess might be to run ./build.sh to see if that sets up your system.

---

### Post by ultan on 2012-05-28
thank you very much guys

ive tried 

chmod 700 run.sh
./run.sh

in terminal 

and it tells me that


chmod: cannot access `run.sh': No such file or directory

am i inputting the file name wrong?
 its on my desktop so i thought that it would be covered by the $  ?

as far as i know there are no mailing lists or forums for this program, its a phD project.

I emailed the guy who made it and he said that he didnt give any help for it

i dont think there is anything wrong with the code i just dont know what im doing here because ive only just started using ubuntu.

any help anyone could give me would be great, i really want this program, ive been looking for it for ages!

---

### Post by Lars Noodén on 2012-05-28
The tar ball extracts the files with the right permissions to run them.  It's just the small matter of the missing documentation.  How familiar with Java are you?

---

### Post by steeldriver on 2012-05-28
it sounds to me like you have not changed to the correct directory (the directory containing the run.sh file) - the tar archive is extracted to a directory called 'QuestionGeneration' so if you are in the directory from which you executed the tar command you would need to go

```
cd QuestionGeneration
./run.sh
```

---

### Post by ultan on 2012-05-28
that sounds like it might be the problem alright

ive tried 

cd QuestionGeneration
./run.sh

but it tells me there is no such directory

i tried "pwd" and it told me that im in

/home/ultron

(ultron is the user name obviously)

the question generation folder that has the run.sh file in it is on my desktop

im sure this is probably a simple enough problem that i cant do because i just dont know ubuntu well enough, especially the terminal cli.

what should the file name be for the run.sh file be if its on my desktop?

ive tried 

"/home/ultron/Desktop/QuestionGeneration/run.sh"

but it doesnt seem to do anything.

ive tried it using bash and .sh and sudo, but honestly ive no idea what im doing.

it seems to start to work if i click on the file.sh in the question generation folder but it seems to just stop at

"Loading question ranking models from models/linear-regression-ranker-reg500.ser.gz..."

anybody any idea what might be wrong?

thanks again for all ayour help

---

### Post by ultan on 2012-05-28
"The tar ball extracts the files with the right permissions to run them. It's just the small matter of the missing documentation. How familiar with Java are you?"

i have absolutely no familiarity with Java.

is this a problem that i can solve? or that could be solved?

---

### Post by evilsoup on 2012-05-28
Your desktop isn't the same as your $HOME (which is what a terminal will open into, in your case '/home/ultron'), unless you deliberately set it that way.

After opening the terminal, use

cd Desktop
ls

the first command brings you into the 'Desktop' folder within your /home/ultron folder, where all the files that are on your desktop are actually stored, and the second command will show you what folders and files are in your Desktop directory.

(BTW if you want to set your $HOME as your desktop folder,  use the command
gedit $HOME/.config/user-dirs.dirs
and change the line that says
XDG_DESKTOP_DIR="$HOME/Desktop"
to
XDG_DESKTOP_DIR="$HOME/"
then log out and log in again)

---

### Post by ultan on 2012-05-28
thanks a lot evil soup, that helped me understand what was going on a good bit more.

ive tried it and it told me what files and folders where there, like you said it would

but then i tried to execute the run.sh with bash

"/Desktop$ bash run.sh"

it gave me this response

"Error: Could not find or load main class edu.cmu.ark.QuestionAsker"

anybody any idea what the problem is and what i might be able to do to fix it?

---

### Post by linuxman94 on 2012-05-28
That's a java error, so you did get the script to run.  I suggest running the build.sh script first to see if that solves your problem.

```
./build.sh
```

---

### Post by LiamOS on 2012-06-01
I extracted everything and ran  build.sh (Requires *zsh* and a java devel. kit) and got some output which looked promising, but alas when I ran run.sh I got this output:
```
Exception in thread "main" java.lang.UnsupportedClassVersionError: edu/cmu/ark/QuestionAsker : Unsupported major.minor version 51.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: edu/cmu/ark/QuestionAsker. Program will exit.

```
I don't have any experience with java at all, but it looks like there might be some missing declaration of some class or something similar.

---

### Post by inashdeen on 2012-06-01
simpler, right click sh file > properties > permission > executable. 
then run again. short note, sh is similar to .exe in windows. permission is similar to run as administrator on windows.

---

### Post by linuxman94 on 2012-06-01
Just tested it on my machine and it seems to run fine...

Can you provide the output of this command?
```
java -version
```

---

### Post by ultan on 2012-06-02
java version "1.7.0_03"
OpenJDK Runtime Environment (IcedTea7 2.1.1pre) (7~u3-2.1.1~pre1-1ubuntu2)
OpenJDK Client VM (build 22.0-b10, mixed mode, sharing)

Cheers again for the help Liam

thanks for any help you could give me Linuxman94.

Linuxman94, if you got the program working could you tell me if its any good?

Id hate to go to all this trouble and then discover that its crap!

---

### Post by ultan on 2012-06-07
has anybody else got any good advice on this problem?

---

### Post by steeldriver on 2012-06-08
> Unsupported major.minor version 51.0it looks like you are trying to run the app with a jre that's older than the jdk you built it with 

run the following and make a note of which version is starred (*)

```
sudo update-alternatives --config javac

```then run 

```
sudo update-alternatives --config java

```and make sure it is the same or numerically higher

---

### Post by ultan on 2012-06-09
When i input  
 

 sudo update-alternatives --config javac
 

 it outputs
 

 There is only one alternative in link group javac: /usr/lib/jvm/java-7-openjdk-i386/bin/javac 
 Nothing to configure.
 

 When i input  
 

 sudo update-alternatives --config java
 

 it outputs the exact same thing
 

 There is only one alternative in link group java: /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java 
 Nothing to configure. 
 

 when i input
 

 ./run.sh < tests/article461.Mary_II_of_England.txt
 

 it says  
 

 bash: tests/article461.Mary_II_of_England.txt: No such file or directory
 

 Ive absolutly no idea what Mary II has to do with anything, but you sound like you really know what youre talking about steeldriver so ill do as you say!
 

 Could you please help steeldriver? 



Im at my wits ends here!

---

### Post by steeldriver on 2012-06-09
Well I don't know what else to suggest - I have no special knowledge about this, I just downloaded the package to try to help you out. If I execute ./build.sh with java-7-openjdk and then try to run it with java-6-openjdk I get the same error as you:

```

$~/Downloads/QuestionGeneration$ sudo update-alternatives --config javac
There are 2 choices for the alternative javac (providing /usr/bin/javac).

  Selection    Path                                        Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/bin/javac        1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/bin/javac        1061      manual mode
* 2            /usr/lib/jvm/java-7-openjdk-i386/bin/javac   1051      manual mode

Press enter to keep the current choice
[*], or type selection number: 


$~/Downloads/QuestionGeneration$ sudo update-alternatives --config java
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java        1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java        1061      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java            63        manual mode
* 3            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode

Press enter to keep the current choice
[*], or type selection number: 1
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/java to provide /usr/bin/java (java) in manual mode.


$~/Downloads/QuestionGeneration$ ./run.sh < tests/article461.Mary_II_of_England.txt
Exception in thread "main" java.lang.UnsupportedClassVersionError: edu/cmu/ark/QuestionAsker : Unsupported major.minor version 51.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: edu/cmu/ark/QuestionAsker. Program will exit.
$~/Downloads/QuestionGeneration$ 

```If I change the jre to java-7-openjdk it runs as follows (I've snipped some of the output - it's loooong - I have no idea what any of it means!)

```
$~/Downloads/QuestionGeneration$ sudo update-alternatives --config java
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java        1061      auto mode
* 1            /usr/lib/jvm/java-6-openjdk/jre/bin/java        1061      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java            63        manual mode
  3            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode

Press enter to keep the current choice
[*], or type selection number: 3
update-alternatives: using /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java to provide /usr/bin/java (java) in manual mode.


$~/Downloads/QuestionGeneration$ ./run.sh < tests/article461.Mary_II_of_England.txt
Jun 09, 2012 10:08:59 AM net.didion.jwnl.util.MessageLog doLog
INFO: Installing dictionary net.didion.jwnl.dictionary.FileBackedDictionary@23f599
Loading question ranking models from models/linear-regression-ranker-reg500.ser.gz...
parsing:Mary II of England
Loading parser from serialized file config/englishFactored.ser.gz ... done [18.1 sec].
parsing:Mary II -LRB- 30 April 1662 28 December 1694 -RRB- reigned as Queen of England , Ireland and Scotland from 1689 until her death .
parsing:Mary , a Protestant , came to the thrones following the Glorious Revolution , which resulted in the deposition of her Roman Catholic father , James II and VII .
parsing:Mary reigned jointly with her husband and first cousin , William III and II , who became the sole ruler of both countries upon her death in 1694 .
<< SNIP >>
parsing:...
Trying recovery parse...
FactoredParser: no consistent parse [hit A*-blocked edges, aborting].
Jun 09, 2012 10:10:05 AM net.didion.jwnl.util.MessageLog doLog
INFO: Installing dictionary net.didion.jwnl.dictionary.FileBackedDictionary@71c3b3
loading most frequent sense information (old format)...done.
Who converted to Roman Catholicism in 1668 or 1669?    The Duke of York converted to Roman Catholicism in 1668 or 1669, but Mary and Anne had a Protestant upbringing, pursuant to the command of Charles II.    the Duke of York3.5244947629562207
Where did the Duke of York convert in 1668 or 1669?    The Duke of York converted to Roman Catholicism in 1668 or 1669, but Mary and Anne had a Protestant upbringing, pursuant to the command of Charles II.    to Roman Catholicism    3.4801535513855484
Whose uncle was Charles II served for a lengthy period as Charles's chief advisor?    Mary's uncle was Charles II; her maternal grandfather, Edward Hyde, 1st Earl of Clarendon, served for a lengthy period as Charles's chief advisor.    Mary's uncle    3.4552854265468183
<< SNIP >>
$~/Downloads/QuestionGeneration$ 

```If I build it in java-6 it runs in either 6 or 7.

I don't know why it's not working for you - or why you don't have the tests/article461.Mary_II_of_England.txt file - maybe you downloaded a different tarball (mine is QuestionGeneration-03-21-11.tar.gz)

---

### Post by TMD on 2012-06-09
It's failing because it can't find the QuestionAsker.class file. The way Java works (and feel free to beat me down if this is telling old-age-pensioners to eat chicken foetuses with straws) is that the .jar files are just .zip files with a different extension. If you make a copy of the question-generation.jar, rename it .zip, and look in there, you should see an edu/cmu/ark/QuestionAsker.class file. If not, you have a knackered jar and you should redownload it. (i checked, and I can see one.)

The .sh file has a -cp arg with the jar. That's the class path arg, and it's like the PATH for Java. What this means is that it is telling Java to find all the .classes it needs from that file; so for the .sh to run properly it needs to be running from a place where it can see the .jar file. This probably means you should be running in the same location as it. 

For the question of the Mary_II: I can see that file in the test dir. Can you? If you can, you are just running from the wrong place. If you can't, I think you downloaded the wrong thing, download the 'Code for the whole system', the QuestionGeneration-03-21-11.tar.gz, like steeldriver (and I) did.

I think it's good that you built it, but I suspect that's not your problem - Java is normally pretty good at telling you when it hits incompatible versions. 

Hope that helps!

T

---

