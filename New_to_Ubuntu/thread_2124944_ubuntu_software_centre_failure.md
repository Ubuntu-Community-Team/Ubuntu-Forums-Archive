---
title: "ubuntu software centre failure"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by Cajamarcawarrior on 2013-03-12
Hi,

I am a beginner in Ubuntu, and face with installing new programs. I use Ubunut 12.10 , the version which I installed on Win7. All the updates are installed.
My problem is, I can not download some programs. Such as Skype, or Wine. I search those programs on ubuntu download centre, I see the programs and click
to install. but it gives failure "since the failure message is in turkish, therefore I don't know what is the original english message. But as I translated it is something like :"The following packages have unmet/unmatched dependencies:skype: Dependency: skype-bin won't installed."

Any suggestions?
Thanks.

Ps: I also downloaded synaptic package manager and same thing happened.

---

### Post by Impavidus on 2013-03-12
That's not an uncommon problem with skype. Usually it's caused by inconsistent repositories and solved automatically after a few days.

In synaptic you can check the available version of skype and skype-bin. skype depends on a specific version of skype-bin (check in synaptic with right click>properties>dependencies>depends on) and if that is not the version available you get that error.

---

### Post by schwarzer ritter on 2013-03-12
Have you unlocked the ubuntu-partners repository?

---

### Post by Mark Phelps on 2013-03-12
> **Cajamarcawarrior said:**
> Any suggestions?

Yes ...

Since you're planning on using Wine, then before you try to install any Windows apps or games, do yourself a favor and visit the WineHQ website, the application compatibility pages. There, you will find ratings of specific versions of Windows apps and games.

Viewing the Test Results on a particular page will tell you what other folks experienced and what they did to get the app/game working.

Anything you plan to use on a daily basis needs to be rated Gold or better; otherwise, you will be frustrated by the lack of working features.

Anything rated Garbage is not going to work -- no matter what you do.

Anything not listed is likely NOT to work, as it hasn't actually been tested and the results entered into the WineHQ database.

---

### Post by Cajamarcawarrior on 2013-03-13
Hi MarkPhelps,
I visited WineHQ as you said and checked the application compatibility pages. The program I want to use "TRNSYS" is not there, but from I found a user who says it works : "https://mailman.cae.wisc.edu/pipermail/trnsys-users/2011/008000.html". It seems the program works with wine, but my main problem is, I can not install wine.

Hi schwarzer ritter,
I didn't know how to unlock, or reverse ubuntu-partners repository previously. But after you mentioned I read about it. Here is the situation: 
1- Canonical Partners repository and Canonical Partners repository (added by software center) are enabled. But still I can not install it from software center.
2- Then I read instructions in official website of wine, there it says I have to add "WineHQ PPA Repository" manually (from Software Sources). "http://www.winehq.org/download/ubuntu" . I did that too, but this also doesn't work.
 3- I downloaded the wine as .tar.gz from its official site. I tried to install it manually but it seems the program is written in 32bit version, my laptop is 64bit. 

Still, any ideas?

---

