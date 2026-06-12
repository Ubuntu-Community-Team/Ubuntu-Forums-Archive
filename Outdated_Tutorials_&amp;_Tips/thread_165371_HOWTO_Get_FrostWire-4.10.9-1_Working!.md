---
title: "HOWTO: Get FrostWire-4.10.9-1 Working!"
date: 2006-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by S{yndrom}e on 2006-04-24
(Frostwire is a p2p client used to share music, videos, pictures and other files. The client itself is absolutly free from any spyware/adware/virus, etc. The only way you might get a virus is if you download something outrageously suspicious (i.e: An executable for a "crack" program or something like that), and/or you download porn. Just stick to downloading music and videos that have alot of sources and you will be fine. And besides, the probality of you gettinh a virus on LINUX is about less than 1%)


Hi im a complete linux noob that just started with ubuntu a week ago. It was pretty tough geting it set up but the resources, howtos, tips and guides where just enormous on these forums. It helped me settle in MUCH quicker.

Well seeing how the community helped me so much i decided to (try) and help in my own way.

Also please dont get mad at me if "I" screw up ur computer but it is highly unlikely that this will do anything malicious to your computer.

Anyway lets get started!

1) Install SUN JAVA 1.5 JRE. You can get this from Automatix, a script compiled by arnieboy. I reccomend you use automatix, its great! Easy to setup and downloads/installs a lot of programs for you automatically! Or you can install it via the java website or synaptic (More info on page 3 by Ribs)

2) Remove FrostWire from your computer.
The Terminal command is:

```
sudo apt-get remove frostwire
```

If that doesnt work than try these:
```

sudo rm -rf /opt/FrostWire
sudo rm -f /usr/bin/runfrost.sh
sudo rm -f /usr/share/applications/FrostWire.desktop
```

3) Next download the deb package of Frostwire-4.10.9-1 from [www.frostwire.com](www.frostwire.com). Select the Debian/ubuntu option.

4) Once it is downloaded move it to your home folder (note: i dont know if it really matters where the .deb file is located but thats what i did.)

5) Install it by opening up terminal and typing

   ```
 sudo dpkg -i FrostWire-4.10.9-1.i5836.deb

```

to get to terminal go to "Applications" --> "Accesories"-->"Terminal"


6)  Next dont open it yet. enter the follwing command:
```

    sudo nano /usr/lib/frostwire/runFrost.sh
```

     Enter your password in the terminal and a page will pop up with lots of    writting

7) Press "Crtl+O". Near the bottom the words "File Name To Write:" will appear

8 ) Now press "ALT+D". Part of the message should dissapear; the "[MSDos Format]" part or something like that.

9) Press Enter and you are done with Terminal!

10) Run Frostwire and it should now work!

          (Remember you need sun java 1.5 jre to run Frostwire)


Hope i helped someone with this problem of FrostWire not "doing anything".
FrostWire is an amazing app much better than Limewire in my opinion.

Also this is my first HOWTO (not to mention first post) so please dont be 2 harsh! ](*,) 

Any feedback/comments are welcome


BIG EDIT: SOLUTION FOR AMD64 USERS! (And  PPC)

Credit goes to Ribs, thanks!

This will be a *really* basic summary of what to do.

Do all the steps of my main howto

Then instead of doing 
```

sudo -i dpkg blah blah
```
at step 5)

Do this

```
sudo dpkg --force-architecture -i FrostWire-4.10.9-2.i586.deb
```

What this basically does is force the package to install even if it isn't your computer's arcatecture's type. 

Well yay that should get it working

Also make sure you have your respective amd64/ppc javas installed

For a more info on Java see Ribs last post on page 3.

---

### Post by halitech on 2006-04-28
well, I don't know if it's because no one has seen this or everyone is too scared to say anything but I want to say a big thank you for providing this. I normally use bittorrent for getting most of my stuff but it's always good to have a backup.

---

### Post by amunimanghi on 2006-04-29
will it harm your computer? ive heard that once you get limewire/frostwire on your computer, it is virtually impossible to get it off.

---

### Post by deadgobby on 2006-04-29
Well cool beans there. That made it work like a snap. I had Frostwire install from Automatix and did not bother to uninstall. It is working just fine. Thanks
Gobby

---

### Post by deadgobby on 2006-04-29
[QUOTE=amunimanghi]will it harm your computer? ive heard that once you get limewire/frostwire on your computer, it is virtually impossible to get it off.[/QUOTE]

 If you run Linux you can just Uninstall the program. I never had Limewire or GTK-Gnuella harm my linux box. Frost is alot like Limewire. Hence the name frostwire.  Yet, you may run the risk of Dl a virus which is really slim. You'll get a porn file under a bands video name. Like for example. I DL a Skippy Puppy video, I was like cool I would like to have "Dig It" vid. It ended up being a porn video. I was urked cause after an hour of DL and taken up my band width. It was porn! 
gobby

---

### Post by easyease on 2006-05-01
Very good indeed! Thanks a million it works for me, and without the need to install automatix to get it....nice.

---

### Post by easyease on 2006-05-01
Oh and a well written how-to......thanks!

---

### Post by disciple on 2006-05-01
worked for me as well, thanks!

---

### Post by openmind on 2006-05-01
[quote=deadgobby]If you run Linux you can just Uninstall the program. I never had Limewire or GTK-Gnuella harm my linux box. Frost is alot like Limewire. Hence the name frostwire.  Yet, you may run the risk of Dl a virus which is really slim. You'll get a porn file under a bands video name. Like for example. I DL a Skippy Puppy video, I was like cool I would like to have "Dig It" vid. It ended up being a porn video. I was urked cause after an hour of DL and taken up my band width. It was porn! 
gobby[/quote]

LoL!!:-D

Does anyone remember a few years ago Madonna released some files onto one of the networks as her album, but when you finished downloading it was a tirade from her on the Evils of File-Sharing!

Basically you're not 100% sure until you open it.

---

### Post by moontide on 2006-05-03
Yes, my thanks too. After updating Frostwire using Automatix Frostwire  wouldn't open. your items 7 and 8 fixed it for me. Great to have Frostwire back. Linux and its community realy rock!

---

### Post by Melciah on 2006-05-03
this worked for me too. cheers

---

### Post by janclodvandam on 2006-05-03
Thanks S{yndrom}e.It worked for me :D

---

### Post by S{yndrom}e on 2006-05-04
Heh thanks everyone for everything and glad i helped some people out.
Sorry i didn't reply earlier i was busy the last week.
In my opinion FrostWire is the best p2p client out there once you get it running.
Well thanks all for your great support! It's real rewarding. :KS 
Anything i should edit/change?

---

### Post by dj1120 on 2006-05-04
Is there a version for amd64 machines? I tried this and got this error message:


dpkg: error processing FrostWire-4.10.9-1.i586.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:

Has anyone else got this error?

---

### Post by Protostar on 2006-05-06
Kickass dude. I'll have to remember that. I was wondering why Frostwire didn't start. Now its works great.:KS

---

### Post by derk.d on 2006-05-06
Well I also installed it with succes now, only when I start it I get the tips & trics but after that I get a blank screen... I use the newest java and tested it with firefox on the web, everything works except frostwire, also limewire has the same problem!!!!! does somebody have the same problem?

---

### Post by lastrite on 2006-05-06
Thanks! You helped another linux noob :D

---

### Post by clay on 2006-05-08
AWSOME! i been trying to figure this out. thaks alot. :D

---

### Post by disciple on 2006-05-09
worked for me as well..
thanks..was very frustrating , before i read your post.. :-)

---

### Post by S{yndrom}e on 2006-05-16
thanks all :KS

---

### Post by jtech on 2006-05-18
[QUOTE=dj1120]Is there a version for amd64 machines? I tried this and got this error message:


dpkg: error processing FrostWire-4.10.9-1.i586.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:

Has anyone else got this error?[/QUOTE]

I don't know very much about this, but saw that no one else had commented so this may or may not work, but perhaps try compiling from source? It is worth a shot. :confused:

---

### Post by S{yndrom}e on 2006-05-18
GOOD NEWS!


I think the problem lies with the wrong java appplet. Just download the Linux amd64 option from here

[https://sdlc3b.sun.com/ECom/EComActionServlet;jsessionid=0A8FEFE96CAAB0DCC96A1CAFE68E0DD1]("https://sdlc3b.sun.com/ECom/EComActionServlet;jsessionid=0A8FEFE96CAAB0DCC96A1CAFE68E0DD1")

And use that java. As of now i don't think there is a fix for ppc users :( .

Can someone with an amd64 please try this?

Thanks

---

### Post by S{yndrom}e on 2006-05-19
anyone??

---

### Post by Ribs on 2006-05-26
Hi,

The link you post for the amd64 applet requires you to register...

Getting the frostwire .deb to work on amd64 is really easy:

Step 1 -- SKIP THIS IF YOU ALREADY HAVA JAVA RUNNING. Go to 1) b) if FrostWire does not start.
1) a) Get Java working... Use Sun's JRE 1.5, Or Blackdown's JRE 1.4 If you want Java working inside firefox (Sun's 64-bit Java does not have a brower plugin -- It's nice to have from time to time). I tested this with both Sun's 1.5 JRE and Blackdown's 1.4 JRE... and Blackdown looked MUCH better (I cannot explain this)... the choice is yours, I've had no problems with websites, Azureus or Frostwire with Blackdown's Java. I see no advantage to using Sun's Java over Blackdown's. Make sure you have the Multiverse repo enabled ( See [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) for help with this ) and use Synaptic to install the package of your choice.
Breezy AMD64 users see [https://wiki.ubuntu.com/JavaAMD64](https://wiki.ubuntu.com/JavaAMD64) for Sun's 1.5 Java or install j2re1.4 for Blackdown's 1.4 Java
Dapper AMD64 users can install sun-java5-bin package for Sun's 1.5 Java or j2re1.4 for Blackdown's 1.4 Java.
PPC users see: [https://wiki.ubuntu.com/JavaPPC](https://wiki.ubuntu.com/JavaPPC)

b) Make sure your system is using the right Java. Run the following and select "/usr/lib/j2re1.5-sun/bin/java" for Sun's java, or "/usr/lib/j2se/1.4/bin/java" for Blackdown's Java. On my system, it looked like this:
> ribs@aphrodite:~/Desktop$ sudo update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/j2re1.5-sun/bin/java
 +    2        /usr/lib/j2se/1.4/bin/java
      3        /usr/bin/gij-wrapper-4.0
      4        /usr/bin/gij-wrapper-4.1
      5        /usr/lib/jvm/java-gcj/jre/bin/java
      6        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/j2se/1.4/bin/java' to provide `java'.
ribs@aphrodite:~/Desktop$
In this case, I would press 1 and enter for Sun's java, or 2 and enter for Blackdown's Java. Don't panic if both are not shown in the menu, as long as one of them is (hopefully the one you picked in part 1) a)), you should be okay. Both are shown on my system as I happen to have both installed.

2) Install FrostWire. Goto the Frostwire website - [http://www.frostwire.com/](http://www.frostwire.com/) - Click the "Ubuntu/Debian" link... SAVE the file, do not open it directly.
Install using the following command in the console (remember to navigate to where the file has been saved, usually in ~/Desktop/ :
> cd ~/Desktop
sudo dpkg --force-architecture -i FrostWire-4.10.9-2.i586.deb

FrostWire will appear in your Internet menu, and should 'just work'.

If you find it doesn't work, your system may be pointing to the wrong Java. See instructions in 1) b).

Enjoy.

---

### Post by S{yndrom}e on 2006-05-27
--force-architecture gotta remember that one :)

Thanks for your help is it ok if I sorta implement some of this stuff on the front page?

---

### Post by Ribs on 2006-05-28
[QUOTE=S{yndrom}e]Thanks for your help is it ok if I sorta implement some of this stuff on the front page?[/QUOTE]

Go for it! 8)

---

### Post by S{yndrom}e on 2006-05-28
Thanks added it. One thing though, do you know for sure it works? Because theoritcally it should.

(BTW nice post on java you have a much better way with words then me :P)

---

### Post by BatteryCell on 2006-08-13
Alright, so I installed Limewire and it worked, and then I installed Frostwire (to compare) and it worked at first.  After opening Frostwire, I search for something and at this point my computer goes bonkers, slowin down to a snails pace and then giving me a wierd screen (all like fuzzled and such).  At this point I reboot (couldnt do anything else) and when I get back up instead of kdm I see a xubuntu login promt (I have xubuntu installed), so I try to select KDE from the login menu, at which point the gui crashed and gave me a text login, so I logged in and then ran dpkg-reconfigure kdm. Rebooted again and kdm worked.  However, now neither Limewire nor Frostwire work correctly.  Both just hang when I get to the splash screen.

Any ideas??

---

### Post by ReapingWildOats on 2006-08-15
I am also having similar problems.

I installed Frostwire and experienced the problem where it refused to open.  I then uninstalled it and changed my java config to 

 /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

from

 /usr/lib/jvm/java-gcj/jre/bin/java

I then reinstalled frostwire but am still experiencing the same problem.

Anyone have a solution yet?  Or need more info from me?

---

### Post by ReapingWildOats on 2006-08-15
Update: I removed gij 4.1 which was successful, leaving me with only sun's java, but it still has not fixed my problem.

How do I run it in terminal so that I can see the error message?

---

### Post by BatteryCell on 2006-08-15
I think its runFrost.sh ... though right now Im on vacation and can't check for sure, however Im pretty sure that it wont help.          Whenever I tried to load from the terminal it said that everything was fine, but then it whould hang at the splash screen and no debug info, only "Loading Frostwire".

---

### Post by BatteryCell on 2006-08-17
Oh no its just "frostwire" (no quotes).

---

### Post by BatteryCell on 2006-08-17
Hmmm, I just realized that if I let Limewire startup for like an hour, it eventually starts up...anybody else tried this?

---

### Post by glennric on 2006-08-17
To get Frostwire or Limewire to run, make sure you have the package sun-java5-jdk installed.  This is the package that has the java jar binaries in it, which are needed to run these programs.

Edit: By the way to install Frostwire in terminal type the folowing two lines.
```
wget http://mirror1.peercommons.net/frostwire/4.10.9/FrostWire-4.10.9-2.i586.deb
sudo dpkg -i FrostWire-4.10.9-2.i586.deb

```

There is no need to do anything with runFrost.sh as long as sun-java5-sdk is installed.

---

### Post by BatteryCell on 2006-08-22
Lol it was just the ports, had to make sure that my firewall wasnt blocking them, then it worked.

---

### Post by Bunyak on 2006-10-08
> **glennric said:**
> To get Frostwire or Limewire to run, make sure you have the package sun-java5-jdk installed.  This is the package that has the java jar binaries in it, which are needed to run these programs.

Edit: By the way to install Frostwire in terminal type the folowing two lines.
```
wget http://mirror1.peercommons.net/frostwire/4.10.9/FrostWire-4.10.9-2.i586.deb
sudo dpkg -i FrostWire-4.10.9-2.i586.deb

```

There is no need to do anything with runFrost.sh as long as sun-java5-sdk is installed.

Hmmmm... tried this one, with no luck.  Have JRE 1.5.09...  I get the usual :
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


HELP!  (a total noob) ](*,)

---

### Post by Bunyak on 2006-10-08
btw, tried syndrome's thing first....   same stuff...

ALSO, my Limewire does likewise:

Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


At least I'm consistent...;)

---

### Post by markster23 on 2006-10-09
I get this after trying to run frostwire from terminal...

```
root@markster23-desktop:~# frostwire
: not found: 7: 
cd: 10: can't cd to .
: not found: 11: 
: not found: 25: 
: not found: 27: 
runFrost.sh: 30: Syntax error: "fi" unexpected (expecting "then")
root@markster23-desktop:~# 

```

i followed all the instructions above.. install jre from automatix.. any ideas??

---

### Post by snoop666 on 2006-10-10
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in /usr/lib/ hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in /usr/java/ hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in /opt/ hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


Theres an easy way to fix this problem, goto [http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp) and download java now make sure you put the .bin file in /usr/java  and when thats done try to install it inside the /usr/java executing thise command ./jre-1_5_0-linux-i586.bin <-- subtitute the file here for the one you downloaded. Now let it install when its done try to run Frostwire again and this time it should work, well atleast it worked for me.

See this was a path problem , thats why it tell you it cant find it in /usr/java users dont really know that they have to install it in that directory so that frostwire can find it.

---

### Post by warjowuch on 2006-10-12
Jep, same problems here. HOWTO: is not entirely succesfull, thanks for the effort though!

It seems it searches for java in all the wrong places. How to solve??

Solution from above is quick n dirty. Things should be installed through apt, nog handmade thinges put everywhere. Sooner or later, it will turn against you.

Is it possible to make the paths on where to find java correct in runFrost.sh?

---

### Post by puppy on 2006-10-13
I've tried the fix that saves it as a linux file, rather than a DOS file, but I still get the following error:

runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")

Can anyone offer any advice?

---

### Post by rabid9797 on 2006-10-14
> **puppy said:**
> I've tried the fix that saves it as a linux file, rather than a DOS file, but I still get the following error:

runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")

Can anyone offer any advice?

i get the exact same problem, maybe something changed between 9-1 and 9-2 that has made this guide obsolete

---

### Post by warjowuch on 2006-10-15
No, too bad, it has the same problems. Anyone found a solution, of filed a bug at launchpad?

---

### Post by Bunyak on 2006-10-15
> **snoop666 said:**
> Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in /usr/lib/ hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in /usr/java/ hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in /opt/ hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


Theres an easy way to fix this problem, goto [http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp) and download java now make sure you put the .bin file in /usr/java  and when thats done try to install it inside the /usr/java executing thise command ./jre-1_5_0-linux-i586.bin <-- subtitute the file here for the one you downloaded. Now let it install when its done try to run Frostwire again and this time it should work, well atleast it worked for me.

See this was a path problem , thats why it tell you it cant find it in /usr/java users dont really know that they have to install it in that directory so that frostwire can find it.

ok...problem is...once I get the jre into the file /usr/java (which took SOME DOING), I cannot unpack it or install it, because I do not have root permission.  Also, do i use the debian installer or what?  My ubuntu seems to want to open it with a text editor!
](*,)

---

### Post by TFrog on 2006-10-15
For those having issues with Frostwire/Limewire in Edgy Eft, follow this procedure:


1.)  Check you're java version:
	
     Code: java -version

2.)  You're java should look like this:

     frog@kubuntu:~$ java -version
     java version "1.5.0_08"
     Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
     Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
     frog@kubuntu:~$

3.)  If not install Sun Java JRE from the repositories both current versions of Frostwire and Limewire require Java version 1.5.0 or greater:
	
     Code:  sudo apt-get install sun-java5-jre sun-java5-plugin

4.)  On Edgy Eft 6.10 Ubuntu/Kubuntu switched to dash as the default CLI.  Supposedly it's faster than Bash.  Frankly I don't see much difference on my hardware.  In order to make Bash the default you must:
	
     Code:  sudo dpkg-reconfigure dash

     Select “NO” when prompted in the CLI to install Dash.
	
5.)  Next, download the deb for Frostwire or download the rpm for Limewire (basically the same as Fostwire).  Should you download Limewire rpm you'll have the extra step of :
	
     Code:  alien -d limewire.rpm

6.)  Install the appropriate deb file:
	
     Code:  sudo dpkg -i (deb package name)
	
7.)  This should do it with minimal of work.  If you're menu selections don't appear then you should be able to get this fixed yourself.

The reason I had to shift from Dash to Bash was due to the fact that another program I use is written to use Bash shell scripts though it's going to move to Dash in the next version.  We can only hope that the coders for Limewire and Frostwire make the adjustments accordingly.  

By the way, if you're curious as to why I had to do this I run tovid a (S)VCD/DVD authoring suite.

---

### Post by DCM36 on 2006-10-15
Thanks TFrog,
your post fixed it.. i guess now all we can do is hope that the devs help us out and change the scripts.

---

### Post by TFrog on 2006-10-16
DCM36,

Your most welcome.  Took me a bit to understand why Limewire Pro would work on my Dapper laptop and it wouldn't on my Edgy desktop.  Same happened with tovid which I'm a big fan of for converting video's I download off the net to DVD format.  I found the solution on the tovid wiki pages some days ago and checked it after a reinstall of Edgy on the desktop.

---

### Post by Bunyak on 2006-10-16
[http://ubuntuforums.org/showthread.php?p=1625534#post1625534](http://ubuntuforums.org/showthread.php?p=1625534#post1625534)

I found the answer to my problem (see above)!  Thanks, Ubuntu Forum!

---

### Post by bg1256 on 2006-10-22
Hey all,

I've read through all the posts and followed the how-to step by step.

It seems that I've done the installation properly, and frostwire does begin to work... however, whenever I run a search and then attempt to download any type of file, the program freezes, and I'm left with no other option than force quitting.

The only thing I can think of that would potentially cause problems would be that I'm at school behind its LAN, but I'm not sure if that would affect anything or not.

Any help would be appreciated.

---

### Post by geezerone on 2006-10-30
I have java 1.5 already installed and used Automatix 2 to install Frostwire and although it starts the connection status is always connecting? Anyone any fix for this?

---

### Post by tninneman on 2006-11-02
FYI, if you KNOW that you have the right version of Java installed, you can just bypass runfrost.sh.  It is called by the "frostwire" script and is totally useless because all it does is check to ensure you have the correct JRE version installed. 

In /usr/bin/frostwire comment out:

sh runFrost.sh

and add in:

java -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. -jar FrostWire.jar

This should then start FrostWire without doing the preliminary Java checks.

Tj

---

### Post by geezerone on 2006-11-08
I hashed out the line and added the line you specified but now frostwire doesn't even start

---

### Post by svzy on 2006-11-08
I keep getting this error when starting up Frostwire:
```
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring
[Fatal Error] :2:6: The processing instruction target matching "[xX][mM][lL]" is not allowed.
CyberGarage warning : org.xml.sax.SAXParseException: The processing instruction target matching "[xX][mM][lL]" is not allowed.
org.cybergarage.xml.ParserException: org.xml.sax.SAXParseException: The processing instruction target matching "[xX][mM][lL]" is not allowed.
        at org.cybergarage.xml.parser.XercesParser.parse(XercesParser.java:122)
        at org.cybergarage.soap.SOAPRequest.postMessage(SOAPRequest.java:92)
        at org.cybergarage.upnp.control.ActionRequest.post(ActionRequest.java:137)
        at org.cybergarage.upnp.Action.postControlAction(Action.java:317)
        at com.limegroup.gnutella.UPnPManager$StaleCleaner.run(UPnPManager.java:530)
        at java.lang.Thread.run(Thread.java:595)
        at com.limegroup.gnutella.util.ManagedThread.managedRun(ManagedThread.java:64)
        at com.limegroup.gnutella.util.ManagedThread.run(ManagedThread.java:53)
Caused by: org.xml.sax.SAXParseException: The processing instruction target matching "[xX][mM][lL]" is not allowed.
        at org.apache.xerces.parsers.DOMParser.parse(Unknown Source)
        at org.cybergarage.xml.parser.XercesParser.parse(XercesParser.java:106)
        ... 7 more


```

---

### Post by whiskytroll on 2007-04-05
Hi there!

It was good to see that so many people are interested in FrostWire! :)

I have a strange problem (or at least I think it's strange...) whith my FW. I successfully installed it (the deb-package from their official site) and configured its settings. Then I tried to look at the chat-tab, but then FW just died.

That's ok. **** happens. But when I tried to open it again it just run until the GUI showed up, and then - a fraction of a second later - it died on me again. And the same again. I tried to check in the System monitor, but it wasn't running a "shadow" or what I should call it. I then tried to open it through the terminal, and this is the end of the output:

> SponsorLoader._loadBanners() exception java.net.ConnectException: Connection timed out
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1117ef6, pid=16928, tid=2968304560
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x31ef6]
#
# An error report file with more information is saved as hs_err_pid16928.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 122: 16928 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)


I didn't understand anything... I don't use the wrong java (it did afterall work fine for some time, I even got full connection before it crashed). The only thing I can imagine is that I did some stupid settings, but then I'm not that adept at this, so I can't imagine much... 8-[ 

I've searched a lot, and didn't find anything that worked. I've tried anything I could find, including the suggestions in this topic.
:-k
Hope to get some help... Thanx in advance!

---

### Post by whiskytroll on 2007-04-06
Update:

Later on I tried again to start FW, and now it did work! :shock: 8-[  :-D But again, when I tried to view the chat-tab, it died... And again, and again. Now I have unmarked it in the View-options. I suppose it works. I hope it does... [-o<  At least it seems so for now. I'm downloading "as we speak". But it would be nice to have the chat feature as well.

Again - thankful for any tip.

---

### Post by shcba on 2008-07-07
I am a new ubuntu user. I absolutely depend on these forums to bail me out. thank you for all your good advice.

---

