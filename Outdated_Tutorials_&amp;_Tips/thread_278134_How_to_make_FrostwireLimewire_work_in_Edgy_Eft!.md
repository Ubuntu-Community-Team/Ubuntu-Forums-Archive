---
title: "How to make Frostwire/Limewire work in Edgy Eft!"
date: 2006-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by TFrog on 2006-10-15
1.)  Check you're java version:
	
     Code: java -version

2.)  You're java should look like this:

     frog@kubuntu:~$ java -version
     java version "1.5.0_08"
     Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
     Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
     frog@kubuntu:~$

3.)  If not install Sun Java JRE from the repositories both Frostwire and Limewire require Java version 1.5.0 or greater as o:
	
     Code:  sudo apt-get install sun-java5-jre sun-java5-plugin

4.On Edgy Eft 6.10 Ubuntu/Kubuntu switched to dash as the default CLI.  Supposedly it's faster than Bash.  Frankly I don't see much difference on my hardware.  In order to make Bash the default you must type the following into the current CLI:
	
     Code:  sudo dpkg-reconfigure dash

     Select &#8220;NO&#8221; when prompted in the CLI to install Dash.
	
5.)  Next, download the deb for Frostwire or download the rpm for Limewire (basically the same as Fostwire).  Should you download Limewire rpm you'll have the extra step of this writing:
	
     Code:  alien -d limewire.rpm

6.)  Install the appropriate deb file:
	
     Code:  sudo dpkg -i (deb package name)
	
7.)  This should do it with minimal of work.  If you're menu selections don't appear then you should be able to get this fixed yourself.

The reason I had to shift from Dash to Bash was due to the fact that another program I use is written to use Bash shell scripts though it's going to move to Dash in the next version.  We can only hope that the coders for Limewire and Frostwire make the adjustments accordingly.  

By the way, if you're curious as to why I had to do this I run tovid a (S)VCD/DVD authoring suite.  Have fun:-D

[COLOR="Red"]As of Ubuntu/Kubuntu Gutsy Gibon you no longer need to reconfigure Dash.  Packages for both Limewire or Frostwire have since shifted to using Dash for the shell scripts.[/COLOR]

---

### Post by scottrob12 on 2006-10-20
Many thanks for the above solution. Frostwire is launching now in Edgy.

---

### Post by domino on 2006-10-22
I didn't uninstall the older java version "1.4.2" before installing the newer java version "1.5.0_08". So I ran the command and it gave me the option to switch java version.

```
sudo update-alternatives --config java
```

---

### Post by daniel2501 on 2006-10-22
Huge help! Thanks :-)

---

### Post by Leonivek on 2006-10-29
Awesome!  Thanks!  Now if only I could get the Limewire icon in the notification area to show correctly... it's damn ugly and squished!

---

### Post by Aoplayo on 2006-10-31
I don't know if this works for everyone but i just double clicked the frostwire packedge icon and it went to a packedge installer window then installed.

Seems easier than what you were trying to do.






EDIT

Spoke too soon It wont run when i double click teh icon.

---

### Post by rackne on 2006-11-05
yay! i've finally managed to get limewire workin' ! :D thanks for help!

---

### Post by SexyPastry on 2006-11-05
when i followed those instructions i got this error 

```
alien -d '/home/carmine/Desktop/LimeWireLinux.rpm'
bash: alien: command not found
```

any ideas

---

### Post by fog on 2006-11-06
> **SexyPastry said:**
> when i followed those instructions i got this error 

```
alien -d '/home/carmine/Desktop/LimeWireLinux.rpm'
bash: alien: command not found
```

any ideas
In terminal type this:
> sudo apt-get install alien

---

### Post by myke on 2006-11-06
I have all of the current java and frostwire installed and it is launching.   It just won't connect.   It gets perpetually stuck in the "starting connection" mode while detecting a firewall that isn't there. I don't have a firewall installed on my home network directly and don't have one enabled on Edgy.  FW worked fine under dapper but simply won't connect now. I don't know what the problem is.  I tried a solution involving the gnuetella.net file suggested on the FW forums but that didn't work either.  I'm at a loss.  Anyone?

---

### Post by fog on 2006-11-07
> **myke said:**
> It gets perpetually stuck in the "starting connection" mode 
Same problem :(

---

### Post by TFrog on 2006-11-07
Not certain what is causing the connect issue.  Possibly the Java version is causing issues?  Not so sure on that either.  I do know I have Limewire Pro working flawlessly on Edgy on both my laptop and my desktop.  This is the first time I've seen a fail to connect issue out of any of the Gtunella network clients and I've even in the past configured Apollon which frankly I didn't care for.  Sorry I can't answer the connect issue.

---

### Post by Leonivek on 2006-11-07
> **myke said:**
> I have all of the current java and frostwire installed and it is launching.   It just won't connect.   It gets perpetually stuck in the "starting connection" mode while detecting a firewall that isn't there. I don't have a firewall installed on my home network directly and don't have one enabled on Edgy.

Do you have moblock installed?

---

### Post by linuxhacker on 2006-11-07
The following worked well for me: [http://www.frostwire.com/forum/viewtopic.php?t=666](http://www.frostwire.com/forum/viewtopic.php?t=666)
and: [http://mc3.electronicbox.net/gnutella.net](http://mc3.electronicbox.net/gnutella.net) for an alternative listing.

---

### Post by ashmew2 on 2006-11-09
TFrog!!!!!!! You're a real life saver!! i was getting problems running limewire pro but i followed your steps for dash and bash :P and its working fine now!!! ive been having this problem from so much time and its fixed now!! THANKS!!

---

### Post by blindmist on 2006-11-13
i keep getting a blank screen in both limewire and frostwire when it comes up and loads. just a white screen and nothing else. could the be a problem with beryl?

---

### Post by Mustafa Temizel on 2006-11-13
> **myke said:**
> I have all of the current java and frostwire installed and it is launching.   It just won't connect.   It gets perpetually stuck in the "starting connection" mode while detecting a firewall that isn't there. I don't have a firewall installed on my home network directly and don't have one enabled on Edgy.  FW worked fine under dapper but simply won't connect now. I don't know what the problem is.  I tried a solution involving the gnuetella.net file suggested on the FW forums but that didn't work either.  I'm at a loss.  Anyone?

I've same problem too :???:

---

### Post by xhaan on 2006-11-13
It seems that if you already have Frostwire installed (from before upgrading to Edgy) you only need to do this:

> **TFrog said:**
> 
     Code:  sudo dpkg-reconfigure dash

     Select “NO” when prompted in the CLI to install Dash.


I did that and Frostwire worked immediately.

---

### Post by dmitriyr333 on 2006-11-14
TFrog - you are the MAN. 
thank you!!!!

---

### Post by computx on 2006-11-16
I think it is beryl causing the white screen in frostwire. If i switch back to metacity using the beryl manager then frostwire displays correctly.

---

### Post by denisesballs on 2006-11-16
> **fog said:**
> Same problem :(

Same problem here too. Frostwire connected fine on Dapper.

---

### Post by gjtoth on 2006-11-16
As a noobie to Ubuntu (edgy), I felt I had to tell ya... The instructions you gave worked perfectly first time through.

Thanks a million! :KS

---

### Post by Shabutie on 2006-11-16
I've got the same problem as a lot of other folks here, got frostwire up and running just fine, but it never gets past the starting connection stage.  Can someone address this problem please? thanks!!

---

### Post by Shabutie on 2006-11-16
through a little research, i found the answer that seems to work for everyone, i'll just post the answer here though to save everyone else the trouble of finding it:

> **zappa420 said:**
> you need to replace gnutella.net

its located here:
/home/[USERNAME]/.frostwire/gnutella.net

replace it with this one:
[http://mc3.electronicbox.net/gnutella.net]("http://mc3.electronicbox.net/gnutella.net")

its just peer ip addresses so you can just cut and paste it.

this is the link I got the info from.
[http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&start=15]("http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&start=15")

i hope that works for you too

worked for me, see if it works for you!

---

### Post by blindmist on 2006-11-17
berly does cause the white screen

---

### Post by dougtheslug on 2006-11-17
I have installed Limewire and I get this error 
user1@user1-desktop:~/Desktop$ frostwire
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")
I have searched for answers but have not found the right one yet.
help anyone please.

---

### Post by BLTicklemonster on 2006-11-18
This fixes the connection problem

[http://ubuntuforums.org/showpost.php?p=1769128&postcount=24](http://ubuntuforums.org/showpost.php?p=1769128&postcount=24)

in dapper or in edgy, either one.

---

### Post by rios_ds on 2006-11-18
hey im new with dis and i dont know what u mean when u said  (deb package name) what is that
:confused: 

thanks

---

### Post by garbagefan2 on 2006-11-19
To people with the white screen. I believe it's a java problem. I go on gnutella forums and when people say they have a grey or white screen it usually ends up as a java problem. Go register at gnutellaforums.com and they will help you. I hope this helps.

---

### Post by dunomous on 2006-11-21
> **garbagefan2 said:**
> To people with the white screen. I believe it's a java problem. I go on gnutella forums and when people say they have a grey or white screen it usually ends up as a java problem. Go register at gnutellaforums.com and they will help you. I hope this helps.

Yep. This happens with other java applications such as IDE's (Netbeans, JBuilder). Sun is familiar with this and is currently working on a solution (though it doesn't seem to high on their priority list). I have lost the link to where they address this, but it is a problem between beryl/xorg/aiglx and java combination (someone please correct me on the exact).

---

### Post by slowtuna on 2006-11-26
Try starting frost with this script:

#!/bin/bash
cd /path_to_frostwire/frostwire
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
sh runFrost.sh

I was getting blank screen until I added the hostname line.

---

### Post by msak007 on 2006-11-26
So there's a known issue between Java and XGL / Beryl / etc.? I had Frostwire 4.10 working, and then read about the new testing version of 4.13 so I decided to try it. All that would load is a white screen, and a bunch of java error output in the terminal. I thought it was something wrong with the app so I reverted to 4.10, and the same thing happened. Switched to KWin instead of Beryl and it worked. Can anybody provide any more info or references about this? I googled and couldn't find anything relevant.

---

### Post by gubatron on 2006-11-27
[Please upgrade to 4.13.1]("http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb")


Info on what's new and how to install here:
[http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/](http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/)

---

### Post by Crosbie on 2006-12-05
Okay, but that doesn't fix the blank-screen issue... :(

---

### Post by Cows on 2006-12-27
my alien command isn't working. I got edgy updated.

root@CowsComp:~/Desktop# alien -d LimeWireLinux.rpm
bash: alien: command not found
root@CowsComp:~/Desktop#

---

### Post by msak007 on 2006-12-27
> **Cows said:**
> my alien command isn't working. I got edgy updated.

root@CowsComp:~/Desktop# alien -d LimeWireLinux.rpm
bash: alien: command not found
root@CowsComp:~/Desktop#

Why are you using alien / rpm? There's an Ubuntu .deb available on the official Frostwire page.

[http://www.frostwire.com/download.php?file=http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.4.i586.deb](http://www.frostwire.com/download.php?file=http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.4.i586.deb)

---

### Post by Cows on 2006-12-27
cause i installed frostwire and it sucked. out of 20 songs it downloaded 3 and the others were 'need more sources' with limewire i download 20 out of 20 songs. anyways i found out the problem. i needed to sudo aptitude install alien

---

### Post by Roobert on 2007-01-02
> **domino said:**
> I didn't uninstall the older java version "1.4.2" before installing the newer java version "1.5.0_08". So I ran the command and it gave me the option to switch java version.

```
sudo update-alternatives --config java
```

THANK YOU! This was exactly the problem I was having - Frostwire was detecting my old java 1.4.2 installation, and I couldn't figure out how to point it to my 1.5 install. You've been a great help!

~ Roobert.

---

### Post by Jongi on 2007-01-07
The dash config just what I needed

---

### Post by tchoklat on 2007-01-10
I have this same problem after following the install directions above. Any help is appreciated

tchoklat

---

### Post by tchoklat on 2007-01-10
fixed the unable to connect issue with this:

[http://mc3.electronicbox.net/gnutella.net](http://mc3.electronicbox.net/gnutella.net)

---

### Post by DJ_Peng on 2007-01-10
> **domino said:**
> I didn't uninstall the older java version "1.4.2" before installing the newer java version "1.5.0_08". So I ran the command and it gave me the option to switch java version.

```
sudo update-alternatives --config java
```

Thanks for this. I spent so much time trying to get 1.5 installed I was pulling my hair out until I tried this command. I never did see anything in my terminal window about this command when I installed Java. None of the three times, including an install of code right from Sun. I finally have my FrostWire running again.

One query: I had FW running fine a week or so ago, then something happened (an update from Ubuntu?) that downgraded my Java. Does anyone have any ideas what crapped the bed on this?

---

### Post by TuxFan on 2007-02-03
> **TFrog said:**
> 1.)  Check you're java version:
	
     Code: java -version

2.)  You're java should look like this:

     frog@kubuntu:~$ java -version
     java version "1.5.0_08"
     Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
     Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
     frog@kubuntu:~$

3.)  If not install Sun Java JRE from the repositories both Frostwire and Limewire require Java version 1.5.0 or greater as o:
	
     Code:  sudo apt-get install sun-java5-jre sun-java5-plugin

4.On Edgy Eft 6.10 Ubuntu/Kubuntu switched to dash as the default CLI.  Supposedly it's faster than Bash.  Frankly I don't see much difference on my hardware.  In order to make Bash the default you must type the following into the current CLI:
	
     Code:  sudo dpkg-reconfigure dash

     Select “NO” when prompted in the CLI to install Dash.
	
5.)  Next, download the deb for Frostwire or download the rpm for Limewire (basically the same as Fostwire).  Should you download Limewire rpm you'll have the extra step of this writing:
	
     Code:  alien -d limewire.rpm

6.)  Install the appropriate deb file:
	
     Code:  sudo dpkg -i (deb package name)
	
7.)  This should do it with minimal of work.  If you're menu selections don't appear then you should be able to get this fixed yourself.

The reason I had to shift from Dash to Bash was due to the fact that another program I use is written to use Bash shell scripts though it's going to move to Dash in the next version.  We can only hope that the coders for Limewire and Frostwire make the adjustments accordingly.  

By the way, if you're curious as to why I had to do this I run tovid a (S)VCD/DVD authoring suite.  Have fun:-D

Thank you very much......You've just ended several hours of horrible frustration. I only wish I would have found earlier.

---

### Post by TFrog on 2007-02-20
I just want to thank all for the kudos.  At the time I wrote this, I was unable to run ATI's proprietary drivers on my laptop and the desktop is unable to run any XGL.  I've since used another forum user's instructions and got ATI's proprietary drivers up in Edgy.  I tried Beryl but didn't care for the resource drain as such and unloaded Beryl.  I believe someone has already addressed the white or blank screen effect in Limewire and Frostwire due to the various other conflicts so I won't address this.

One other thing I'd like all of you to know.  Frostwire is nothing more than a Debianized packaging of the "free" version of Limewire.  There is a definite difference in the connection speed  and search propensities between Frostwire and Limewire Pro.  If you're lucky enough to find a copy of Limewire Pro for linux, it will be in Redhat RPM form.  Thus is the reason for the use of Alien.

---

### Post by Bananabonez on 2007-04-02
hey can u guys help me i got frostwire vers. 4.13.1 and installed the deb and the jre but when i go to launch it it gets stuck on the chat window can u guys help me? i am running kubuntu

---

### Post by Paradoxed on 2007-04-08
Seem to have the same issue on Fesity. 

Java seems fine 

j> 
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)



However when I launch Frostwire it just brings up the "tips of the day" box and thereafter a white screen with the heading Frostwire 4.13.1 Tuned for extended 
play.

And just a white screen.

---

### Post by royal314 on 2007-04-10
I followed the instructions given but a few seconds after frostwire opens it crashes every time

---

### Post by drumkitcat on 2007-04-15
yeah, I have followed the instructions so far on getting the latest java version, and installing Frostwire, which all appeared to go as it should.

When I launch Frostwire (I'm using Edgy 6.1) I get the splash screen, and it shows that it's configuring everything... then a few seconds later the main program window shows up, but then it immediately exits the program!

I did try and find the gnutella.net  file but it does not seem to exist on my file system... if anyone has any idea how I can get this Frostwire app running, that would be great, thanks!

---

### Post by amaan on 2007-04-20
i'm using the new version of java - 1.6 and frostwire wont run at all it gives me an error saying that i should upgrade and there is no java...?

---

### Post by Beta_Solution on 2007-05-15
I'm running Kunbuntu Edgy, but I don't know the version. When I download the .deb file for Frostwire, it opens in a program called 'Kate.' It says that the deb file is a binary file and saving it will cause a corrupt file. I can't figure out what to do or how to proceed from there.

---

### Post by myke on 2007-05-15
No matter which version of Kubuntu/Ubuntu that I've been on (dapper/edgy/feisty) ... the one thing that is easier and most often works with a 3rd party script is Automatix installing Frostwire.  I'd try that.  Automatix will update and install not only Frostwire but will update to the correct Java version as well.

---

