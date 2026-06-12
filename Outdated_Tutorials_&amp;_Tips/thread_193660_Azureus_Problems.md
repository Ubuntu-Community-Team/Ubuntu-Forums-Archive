---
title: "Azureus Problems"
date: 2006-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Sir_Brizz on 2006-06-10
I have noticed occasionally that people are having trouble getting Azureus to work properly. I'm not going to explain how to install Java, so this tip is assuming you have already installed Sun Java instead of gij on your installation.

SYMPTOMS: Azureus runs, but the program exhibits one or more of the following symptoms:
[list]
[*]Window opens but shows nothing
[*]Toast (popup) message appear but the buttons do not work
[*]The Azureus tray icon does not show
[*]The program cannot be closed cleanly
[/list]

RESOLUTION: Simply download the latest CVS build from Azureus available at the following link:

[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

Download the jar file available there. Then, reaplce your Azureus2.jar with it (keep a backup, just in case!).

To locate your Azureus2.jar, simply go to a command line and type 'updatedb' and then 'locate Azureus2.jar'.

Voila! Working Azureus! :)

---

### Post by ijanos on 2006-06-10
Wow. It works.
I wonder why could the same azu version put the tray icon out on breezy.

ps.: I see, the ubuntu guys hacked the azureus: New icons, no menu entry for updates. Hm

---

### Post by xfile087 on 2006-06-11
[QUOTE=Sir_Brizz]I have noticed occasionally that people are having trouble getting Azureus to work properly. I'm not going to explain how to install Java, so this tip is assuming you have already installed Sun Java instead of gij on your installation.

SYMPTOMS: Azureus runs, but the program exhibits one or more of the following symptoms:
[list]
[*]Window opens but shows nothing
[*]Toast (popup) message appear but the buttons do not work
[*]The Azureus tray icon does not show
[*]The program cannot be closed cleanly
[/list]

RESOLUTION: Simply download the latest CVS build from Azureus available at the following link:

[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

Download the jar file available there. Then, reaplce your Azureus2.jar with it (keep a backup, just in case!).

To locate your Azureus2.jar, simply go to a command line and type 'updatedb' and then 'locate Azureus2.jar'.

Voila! Working Azureus! :)[/QUOTE]

You're a life saver! I use Azureus a lot and i've just moved from WinXP to Ubuntu permanently but Azureus wouldn't work properly which was a big shame. But now it works perfect thanks to you! :D

---

### Post by mandragor on 2006-06-11
I really appreciate the fix, but why is no updated package available seeing as the
problem is known and a fix is found?

---

### Post by ijanos on 2006-06-11
[QUOTE=mandragor]I really appreciate the fix, but why is no updated package available seeing as the
problem is known and a fix is found?[/QUOTE]
The bug is already filed, this is just a quick&dirty fix.

---

### Post by userundefine on 2006-06-11
Very easy, very simple!  Thanks.

---

### Post by kinematic on 2006-06-12
finally a working azureus...thnx!

---

### Post by Hairy_Palms on 2006-06-13
its a good thing :) thos error msgs were really annoying
thanx for the fix sir brizz :)

---

### Post by fatalfury24 on 2006-06-13
Thanks, that stupid message box was really getting annoying

---

### Post by volksman on 2006-06-13
worked like a charm!

In fact so far my only problems with Ubuntu have been with gij and this gave me the courage to unload it... :)

---

### Post by LopsidedElf on 2006-06-13
When i type updatedb i get the following error:
updatedb: fatal error: You are not authorized to create a default slocate database!
whats the problem?

---

### Post by ijanos on 2006-06-14
[QUOTE=LopsidedElf]When i type updatedb i get the following error:
updatedb: fatal error: You are not authorized to create a default slocate database!
whats the problem?[/QUOTE]
You are not root.
Try sudo updatedb, but anyway the Azureus2.jar you seek is in /usr/share/java

---

### Post by ronin69hof on 2006-07-02
You can also click on "help" and then "about" in azureus and while that window is open clicking on hide or hide all works

ronin

---

### Post by mimihu88 on 2006-07-04
donot understand why :"To locate your Azureus2.jar, simply go to a command line and type 'updatedb' and then 'locate Azureus2.jar'."
since I didnot do the above but azureus already works fine

---

### Post by bionnaki on 2006-07-05
thanks

---

### Post by bionnaki on 2006-07-05
wait.
do I rename the cvs .jar to simply "Azureus2.jar"? or just copy the file over?

edit: duh. nevermind.

---

### Post by depi on 2006-07-06
Thanks for this solution. But one another issue, when I start Azureus it always wants to download some updates, anyone has this problem too?

---

### Post by bionnaki on 2006-07-06
yeah, you should do the updates. but in order to do so, you usually have to change the permissions or run azureus as root.

my azureus installation is /opt/azureus

so I just sudo /opt/azureus/azureus

& it'll update.

---

### Post by kevinz on 2006-07-07
from my latest try, replacing ubuntu-built-azureus jar file will make azureus unable to start. What I did is to install Azureus from its official website and then replace the cvs .jar file with the latest build.

---

### Post by gorilla_king on 2006-07-07
this is kinda off topic
but i'm arguing with my friend at the moment about how azureus is pronouced in english. A little help on settling this bet would be great. Thank you in advance and sorry for making this kinda offtopic.

---

### Post by BKK on 2006-07-07
I let automatix install azureus. It seems to work much better when it is run using sudo. For example The DHT Firewalled yellow light goes green and shows the number of users. 

Anyways its screwy. I have a NAT router,ADSL it supports Upnp and its all enabled, I have followed many advice articles online trying to get it working properly. I set up iptables to allow ports etc... still not working right :(

---

### Post by SDREnate on 2006-07-07
Great fix! Now I guess the only thing I'll ever use Windows for is gaming.

---

### Post by gorilla_king on 2006-07-07
> **SDREnate said:**
> Great fix! Now I guess the only thing I'll ever use Windows for is gaming.
and even then you can get most of your popular games (quake 4, ect) to work on linux.

---

### Post by alphaomega on 2006-07-07
wow, I just did this the other day. Yep it works, now if I can only get my NAT problem solved. I posted a thread to no avail.

---

### Post by gorilla_king on 2006-07-07
> **alphaomega said:**
> wow, I just did this the other day. Yep it works, now if I can only get my NAT problem solved. I posted a thread to no avail.
i have the nat problem too, but it doesn't seem to affect my ability to dl stuff. idk what to do about it, but o well it works fine 4 me

---

### Post by alphaomega on 2006-07-07
> **gorilla_king said:**
> i have the nat problem too, but it doesn't seem to affect my ability to dl stuff. idk what to do about it, but o well it works fine 4 me

I just figured out the configuration of my firewall to open the NAT and DHT. I need to share files via bittorrent.

---

### Post by nhimf on 2006-07-08
> **gorilla_king said:**
> and even then you can get most of your popular games (quake 4, ect) to work on linux.

Unless you are using an ATI vga card...
OpenGL & ATI is horrible with my x1900xt card i get with World of Warcraft like 10 whole fps in opengl mode and 15 in D3D (with wine, with cedega its both near 3fps).
So i cannot change fully to Linux just yet, but the really annoying Azurus should be be fixed (was about to throw azureus away).

Anyway, thanks for the azureus tip, ill try it out cuase it was really fubar, i had all bugs stated here and also azureus broke downloaded parts, i had a 7GB torrent @ 60%, now i only have 2% ready left....

---

### Post by Kevf on 2006-07-09
I have the same problem, but I'm also a total newbie at working with Ubuntu. Could someone write down al the steps I have to take? Cause while I'm learning Ubuntu, I can't go without my  DL's :( 

Thanks in advance, 

Kevin

edit: never mind, a bit of puzzling on the net did the trick

---

### Post by mycelo on 2006-07-12
It's also of note that Azureus works better with JRE 1.5.x.
So try this command: 

sudo update-alternatives --config java 

And select the latest java version installed in your system.
That will affect all java applications.
Hope it helps.

mycelo

---

### Post by LosD on 2007-04-14
> **mycelo said:**
> It's also of note that Azureus works better with JRE 1.5.x.
So try this command: 

sudo update-alternatives --config java 

And select the latest java version installed in your system.
That will affect all java applications.
Hope it helps.

mycelo
Instead, use "sudo update-java-alternatives -l", find the right one (1.5 or 1.6 are both perfect), and do at "sudo update-java-alternatives -s the-one-you-found" (on mine that is "sudo update-java-alternatives -s java-1.5.0-sun"). This will update all Java utilities, not just the java command.

Remember, though, that it will update Java for ALL programs, not just Azureus, which is also why it's smartest to use update-java-alternatives instead, Azureus doesn't care, but some other Java program might.

---

### Post by Typhon on 2007-04-15
Interesting how many people have this problem. I've never had any problems with Azureus on Linux.

---

### Post by tankmcp on 2007-05-24
Thanks!  That was a simple & quick solution!

---

### Post by tveek on 2007-05-28
I checked the net if anyone had similar problems to mine but couldn't find any similar messages. I had a few different symptoms exhibited by my azureus installation from the Ubuntu (Feisty Fawn) repositories:
- Azureus starts cleanly and downloads work but after a while, everything stands still (no up/down-loading)
- Azureus cannot close cleanly, instead had to use ctrl+alt+esc and then kill the java process.

To remedy these problems:
1. remove Azureus
[INDENT]```
sudo aptitude remove azureus
```[/INDENT]

2. Make sure you have Sun Java installed as written in the [INDENT][URL="http://ubuntuguide.org/wiki/Ubuntu:Feisty"]Ubuntu unofficial installation guide 
[/URL][/INDENT]

3. Tell Linux to use the Sun Java.
[INDENT]First list the Java installations
```
update-java-alternatives -l
>>java-6-sun 63 /usr/lib/jvm/java-6-sun
>>java-gcj 1041 /usr/lib/jvm/java-gcj

```

Point to the appropriate installation, use the one above which mentions 'sun'. In my case, I do
```
sudo upate-java-alternatives -s java-6-sun
```
[/INDENT]
4. Download Azureus from the [website]("http://azureus.sourceforge.net/")

5. Run the azureus executable inside the package. 

For me, this worked like a charm. Maybe someone else has the same problems.

---

### Post by regomodo on 2007-05-29
wtf. this bug is still about?

cheers for the work sir_brizz. sorted my Azureus out a treat

---

### Post by ArtInvent on 2007-06-01
I seem to have a slightly different problem. I only have Sun Java 6 JRE installed. Azureus installs and works fine for a while. Then I try a new torrent and Azureus shuts down. Try to restart, the splash screen appears and the main program window flashes for an instant, then disappears, program completely fails to start. When I run it as root, it starts.  Had the same problem on Edgy, now on Feisty. 

Anyone have the same problem or know of a fix?

---

