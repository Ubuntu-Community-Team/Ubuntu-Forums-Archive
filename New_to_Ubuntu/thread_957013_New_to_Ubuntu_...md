---
title: "New to Ubuntu .."
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Aaron Kirk on 2008-10-23
Hey I know almost everything possible to know about Windows xp,and I recently decided to try Ubuntu Linux.Everything was going well untill I downloaded something off of the internet,then clicked on it,and it did not install like it normally would on Windows xp,but instead brought up some weird error in front of a thing called archive manager.. please help,thank you.

---

### Post by OutOfReach on 2008-10-23
Ubuntu installs things differently, it doesn't use .exes etc...
Can you tell us what exactly did you download?
Sounds like you might have to compile it.

---

### Post by jerome1232 on 2008-10-23
More info would be helpful.

What is it your trying to install.

What is it you downloaded (a link to the site would be great)

about 99.99% of the software you need can be found in the repos (Applications-Add/Remove, for the more advanced version System-Administration-Synaptic Package Manager)

There are three main ways to install programs

debian installers (.deb's) Easiest
binary installers (.bin, .run, .sh, well extensions don't actually matter, it's equivalent to a .exe in windows) Second easiest
Source Code usually comes archived in a .tar.gz archive and can be difficult to install

---

### Post by bsharp on 2008-10-23
Welcome! You are going to find that with Ubuntu that you don't install everything like you did in Windows. (Almost) Everything can be installed through the Synaptic package manager located under System->Administration->Synaptic Package Manager

Here are some links you should read:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://ubuntuforums.org/showthread.php?t=709685](http://ubuntuforums.org/showthread.php?t=709685)

---

### Post by damispyderbyte on 2008-10-23
Ubuntu is not like windows. To install a package on ubuntu it has to be in a .deb format. It is ubuntu's forum of an exe file. Most downloads can be found in the add remove programs menu. It contains 1000's of programs. If you want to install windows programs on ubuntu you can download wine. It can also be found in the add remove programs dialog. That dialog can be found in applications-add remove

Hope this helps!!
note: what was the error.

---

### Post by Aaron Kirk on 2008-10-23
I downloaded Regnum online,Amarok,or some music thing,and wine,none of those worked,but I did find Wine,and Amarok,in the add/remove programs list thankfully.. but as of the other I did not know what to do.But almost anything I would download I would click,and get some error..

---

### Post by OutOfReach on 2008-10-23
What error are you getting?
What are the contents of the file you downloaded?

---

### Post by Aaron Kirk on 2008-10-23
yes I installed wine,and Amarok from the Synaptek MAnager,thingy very useful program. I like the way Ubuntu is.I just have to get the fill of things.Because I am so use to Windows XP.But I think Ubuntu may get big some day..

---

### Post by jerome1232 on 2008-10-23
From here?

[http://www.regnumonline.com.ar/index.php?l=1&sec=6](http://www.regnumonline.com.ar/index.php?l=1&sec=6)

That's a binary install I'm downlading it right now but basically you need to do this:

right click it, select properties, select the permisions tab, check 'executable'.

Now double click, should work as long as you install to somewhere in your ~/.

If you want to do a system wide install you will need to run it as root. Easiest way for you to do that is to pop open nautilus as root and double click the file.

Alt+f2, type 'gksu nautilus', navigate to the file, double click it.

---

### Post by Aaron Kirk on 2008-10-23
it saves everything to the desktop,but since I am very new to this,I am also very confused.So should I just use the Synaptec Package Manager?

---

### Post by Aaron Kirk on 2008-10-23
Thank you! I believe that was the case! they were binaries,I know that for sure..

---

### Post by jerome1232 on 2008-10-23
That particular program is not in the repo's. You just need to make it exectuable then run it like any old .exe on windows. See my above post and ask questions if your still unsure.

---

### Post by Aaron Kirk on 2008-10-23
Also I tried to search for them in the registry,but could not even find one anywhere..

---

### Post by Aaron Kirk on 2008-10-23
The above worked for me thanks,now I will write that down so I can remember it! haha.

---

### Post by stalkier on 2008-10-23
> **Aaron Kirk said:**
> yes I installed wine,and Amarok from the Synaptek MAnager,thingy very useful program. I like the way Ubuntu is.I just have to get the fill of things.Because I am so use to Windows XP.But I think Ubuntu may get big some day..

It just takes some getting used to. Trust me it is well worth the trouble you have. I have been using Ubuntu off and on for over 6 years now and I have loved it from day one. I have had my fair share of trouble too. Luckily there are the Forums with many helpful people on here. Just take your time and you'll do good. If you mess something up, that is ok too. Just remember to come back here to get help fixing it.

Keep in mind to jot down errors (exactly what they say) what you did exactly, etc. This will help the users to find answers for you.

---

### Post by Aaron Kirk on 2008-10-23
Is there a really good movie player for Linux I like Amarok alot for Music,but Windows Media player still seems really good for videos...

---

### Post by bsharp on 2008-10-23
The default is fine, you just need to install the codecs:

```
sudo apt-get install ubuntu-restricted-extras
```

Also if you need to play .wmv or .wma files take a look at:
[www.medibuntu.org](www.medibuntu.org)

---

### Post by jerome1232 on 2008-10-23
Well I use totem it suits my needs. (installed by default, it's called movie player)

Alot of people swear by mplayer, it's great and can handle more formats than totem can. It's in the repos

VLC is another must have, I  haven't seen a file format it can't tackle but it's not very 'pretty' to look at. This is also in the repos.

---

### Post by Aaron Kirk on 2008-10-23
> **jerome1232 said:**
> That particular program is not in the repo's. You just need to make it exectuable then run it like any old .exe on windows. See my above post and ask questions if your still unsure.

Thanks you guys are great! Glad I came here.

---

### Post by Aaron Kirk on 2008-10-23
Am I allowed to discuss anything abount Ubuntu right here? or do I move to another section? Because I also wanted to know if my Blue-Ray disc player would work for Ubuntu?

---

### Post by Aaron Kirk on 2008-10-23
Are there any game designers for Linux? Becuae the best looking MMO I seen so far was Regnum Online,but I use to play Shaiya,Perfect world,and WoW.

---

### Post by jerome1232 on 2008-10-23
Wow works great with wine, for your other games do a search here for them [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true) They should give you workarounds to get the games to work if they work at all.

NWN: Platinum works nativly, ETQW, Doom3, Eve: Online, and many other games, Check out the gaming and leisure forums to get a better idea of the state of native games for linux [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

As for the blue ray thing I have no idea (dont' they use some proprietary codec?) and I would start a new thread, try to use a descriptive title next time like "how to get blue ray to work" Have you tested any movies to see if it does work?

---

