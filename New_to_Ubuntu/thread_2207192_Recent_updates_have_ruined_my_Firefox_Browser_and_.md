---
title: "Recent updates have ruined my Firefox Browser and Flash isn't working sometimes now"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by linux_newbie3 on 2014-02-22
[ATTACH=CONFIG]250569[/ATTACH][ATTACH=CONFIG]250570[/ATTACH][ATTACH=CONFIG]250571[/ATTACH]

See above. This is my recently updated Firefox web browser. Reddit didn't look like this before I did the recent sudo apt-get update && sudo apt-get upgrade of my entire Ubuntu 12.04 system, just a few days ago.. Everything was perfect just a couple weeks ago. What happened, and how do I fix this problem? The two packages I noticed that were updated was my Firefox Web Browser  and my Adobe Flash Plugin. Those were the updates that download right before I started having problems using Firefox and Adobe Flash plugin. And, as a side-question, I was under the impression that Adobe Flash  wasn't going to be updated again since Adobe dropped support  completely for Linux, so why am I still receiving updates for Flash Plugin from time to time? It isn't like the are providing them, are they? So why are their updates for Adobe Flash plugin if it is no longer supported in Linux? Weird! 

Okay, so I -think- need to roll back my browser and my adobe flash plugin to stop the crashing and screen artifacts/anomalies when browsing. I need to know how to do this to try and test my hypothesis.

Can someone please post a step-by-step guide to help me rollback to make my browser work again? Thank you. Reinstalling the OS just gives me the latest brower and flash plugins, which are probably what are causing this problem. 

Any help would be gratefully appreciated.

---

### Post by SeijiSensei on 2014-02-22
First, I would try creating a new Firefox profile and see if that helps.

In your home directory, rename the folder called .mozilla to .mozilla.old.  Now start Firefox.  It will create a new profile.  Does that work any better?  If so, there's something in your current profile that is causing problems.

As for Flash, I believe that Adobe continues to publish security fixes for the Linux version of Flash Player, but will not add any new features or keep it in sync with the Windows version.  Since Flash has had a number of security vulnerabilities over the years, it's pretty important that those fixes are ported over to Linux.

---

### Post by linux_newbie3 on 2014-02-22
Okay, I will try that. 

Does anyone else have the same Firefox Browser and Flash on their system yet?  Do you notice anything like this happening after the update? Thanks.

---

### Post by deadflowr on 2014-02-22
> **linux_newbie3 said:**
> 
Does anyone else have the same Firefox Browser and Flash on their system yet?  Do you notice anything like this happening after the update? Thanks.

Just every single person who is up to date.
I've had no problem's with firefox or flash.

---

### Post by monkeybrain20122 on 2014-02-22
I have the same FF version, not a single problem.

---

### Post by linux_newbie3 on 2014-02-22
Do you think it could be my Nvidia graphics driver that is causing this problem? Which Nvidia drivers have a problem with linux? I heard the founder mention something about Nvidia in the past, and that Linux has a problem with certain video drivers, and can you please list the drivers that currently do not work with Ubuntu? Thanks.

---

### Post by linux_newbie3 on 2014-02-22
Just every single person who is up to date? The update came down a week ago. Everything here was fine before that time.  I thought it would be nice to mention it, since this is free software, in case anyone else might be having a problem with their updated system. I'm getting really tired of being a beta tester for Ubuntu. I just want my system to function as it did before the updates. Don't get snooty with me either.

---

### Post by monkeybrain20122 on 2014-02-22
> **linux_newbie3 said:**
> Just every single person who is up to date? The update came down a week ago. Everything here was fine before that time.  I thought it would be nice to mention it, since this is free software, in case anyone else might be having a problem with their updated system. I'm getting really tired of being a beta tester for Ubuntu. I just want my system to function as it did before the updates. Don't get snooty with me either.

Are you saying that we lied? :) I have FF27 and flash  on three systems (Nvidia, Intel and briefly amd)  and not a single problem. Did you test with a new profile as advised earlier? What happens? If you haven't here is an even easier way to do that, just log into the guest session and see if it works there. If it does, then it is your profile.

---

### Post by deadflowr on 2014-02-22
> **linux_newbie3 said:**
> Do you think it could be my Nvidia graphics driver that is causing this problem? Which Nvidia drivers have a problem with linux? I heard the founder mention something about Nvidia in the past, and that Linux has a problem with certain video drivers, and can you please list the drivers that currently do not work with Ubuntu? Thanks.

What's the card?
In general though, Nvidia(for all it's woes with the linux community) does a fair job at trying to address problems with its cards and drivers. But it can only address the problems that it knows about. So any list would probably be a moving target, at best.

Edit: +1 to what monkeybrain#### said.

To add, Firefox was updated a week ago, but flash had a new update yesterday.
I'm now on flash 11.2.202.341.
Was 11.2.202.336 last time, AFAIK.

---

### Post by linux_newbie3 on 2014-02-22
Have any of you looked at my OP post and looked carefully at the pics I attached? I took some time to put this article togather. I'm not some person here just trolling for attention. Have you seen any errors like that before, in general? 

I have entire parts of my browser missing on the browser window when it is open. It looks like a virus or a worm or something. 

I haven't seen a browser this messed up since I used to use Windows XP after catching a virus.

IMHO - This seems like a pretty important thing to address. If you want to tell me you don't have this problem with any of your existing updated system, well I guess I must be the exception. Still, you haven't told me any way to fix it. Are their Firefox extensions that could cause this problem? You never asked me if I installed any extentions. You never asked me if I made any changes to my browser. 

I work as a salesperson for a major big corp here. We are thinking about switching from WinXp to Ubuntu. I don't need attitude.. I just need to understand how to fix this problem.

---

### Post by linux_newbie3 on 2014-02-22
Which Nvidia do not work with Ubuntu?

---

### Post by linux_newbie3 on 2014-02-22
BTW - Why would changing the profile matter? What difference does it make EXACTLY to refreshing the profile in Firefox 27?  Are you specifically saying that an extention might cause this problem or that I caught some kind of virus? Did installing openjdk7 cause this to happen? This is very important because all my work in done through my browser.

I cannot stress this enough = I didn't have this problem two week ago. I have never had this kind of problem with flash since they were still working out the bugs with flash or anything since Ubuntu 9.04. The only thing I can think is something changed with my graphics driver. However, there was a kernal update recently right before the Firefox 27 rolledout in my updates too. Which nvidia drivers are no longer supported with Ubuntu 12.04? Would Ubuntu developers or kernel developers remove a graphics driver from the kernel and after updating my kernal would they no longer have the video support I had before? 

Update: I'm going to do a reinstall. I'm going to install pure debian until someone here can give me a adequate answer to what happened to my Firefox 27 and Nvidia driver. I just did a complete fresh re-installation of Ubuntu 12.04 LTS and I don't have time for this shenanigans. And yes, the problem still exists. And I certainly don't have time for this kind of immature attitude from any of you non-paid volunteers either. Login as guest didn't change anything. A new profile didn't help either. I apprieate the original reply I recieved to my post.. But this strange attitude from everyone else is very disheartening to say the very least. Again I am a salesperson for a large corp here in the USA. I don't want to recommend Ubuntu to my boss if this is the way new users are treated when they have a problem or issue after doing an official update.  I have no other repos enabled besides the default that come with Ubuntu.  I'm not saying anyone is "lieing" to me. What I am saying is - Nobody asked me any important questions about my problem. Nobody told me they have seen anything like this before either and nothing has changed on my computer except for the regular update I did. I'm not lieing because I want this resolved please.

TL;DR My other unanswered questions were:

How do I roll back to the my prevoius version of Firefox 26 and older depriencated version of Adobe Flash plugin. That way I can check and see if that is my problem or not. The solution you gave me was apparently something else than what I requested help with. How do I roll back please?

---

### Post by linux_newbie3 on 2014-02-22
Can anyone else verify what this user is saying to be true, and that Adobe is still providing security updates to Adobe Flash plugin in Linux? ? ?

My problems started when I updated adobe flash plugin. Just so everyone underrtands.. I just did this update yesterday. Why would adobe publically and verbally discontinue support of Flash Plugin but still provide Linux with security updates? That sounds kinda crazy to me guys.

---

### Post by deadflowr on 2014-02-22
> Why would changing the profile matter?

Profiles can get corrupted.

But for the record, all nvidia cards should work with Ubuntu.
If one has problems, it should be reported.

So again, what is the card?
And also did you install the nvidia drivers, or are you using the drivers that came with the installation?

> Can anyone else verify what this user is saying to be true, and that  Adobe is still providing security updates to Adobe Flash plugin in  Linux? ? ?

Which user?
And yes adobe still provides security updates for flash on linux.

---

### Post by linux_newbie3 on 2014-02-22
[ATTACH=CONFIG]250593[/ATTACH]

See attached for my currently installed Nvidia hardware. 

2nd question; Why would adobe publicly say they no longer support Adobe Flash plugin on Linux, but still provide these kinds of security updates? Isn't that kinda odd to you? Where are these updates really coming from? Are they coming from Adobe or are they compiled by someone other than Adobe to be used by Ubuntu (i.e reverse engineering) ??? I'm kinda confused here.  I'm almost positive that the Adobe Flash plugin update I did yesterday is causing these video artefacts.  And honestly, I think it is kinda strange that adobe would publicly (they made a big huge deal about it in the news) come out and say they no longer wanted to waste anymore effort on adobe flash plugin on linux system, yet still take the effort to provide security updates. That sounds almost too good to be true and cost-prohibitive, if that was my job at Adobe. There should be a way to rollback my flash plugin to the previous deprecated version too, but I just don't know the commands in terminal to do it. 

3rd question; What would cause Firefox to become corrupted after an update? Isn't corruption a sign of something like malware or a virus? My only experience with these kinds of artifacts in Firefox brower are from Windows XP and malware infections. etc etc.  My hardware was working great two weeks ago. This I can verify when I boot from my live USB backup clone of Ubuntu I made with remastersys backup. I do not experience these video artifacts in Firefox 26.

4th question (still unanswered since my OP); How do I roll back to the my prevoius version of Firefox 26 and older deprecated version of Adobe Flash plugin??? That way I can check and see  if that is my problem or not. The solution you gave me was apparently  something else than what I think should work for my system. How do I roll back  please? It is something I can do with synaptic package manager?

---

### Post by deadflowr on 2014-02-22
> I may be new to linux, but I know how tech support is supposed to work. imho 				

I don't know what this alludes to, but we are all volunteers here.

But to the point, Adobe no longer provides newer versions, which include updated features, for linux on flash.
They still provide security updates for flash, though.

A corrupted profile can be caused by any number of things, malware being one of them.
But it can, and in a lot of cases, be caused by mis-action by the end user.

Before jumping the gun on nvidia being poor, maybe you should try making a new profile and see what happens.
```
firefox -ProfileManager
```
go to create and launch it.
See what happens.

---

### Post by linux_newbie3 on 2014-02-22
I tried that already. It didn't make any difference. I want to rollback and lock in Firefox 26 and the depreciated verison of Adobe Flash plugin on Ubuntu 12.04 LTS. How this done either with Synaptic Package Manager or with terminal commands please? Thanks! :D

---

### Post by deadflowr on 2014-02-22
> **linux_newbie3 said:**
> I tried that already. It didn't make any difference. I want to rollback and lock in Firefox 26 and the depreciated verison of Adobe Flash plugin on Ubuntu 12.04 LTS. How this done either with Synaptic Package Manager or with terminal commands please? Thanks! :D

You may be able to find an older version of firefox here
[http://security.ubuntu.com/ubuntu/pool/main/f/firefox/](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/)
Though I don't recommend it.
As for flash, that ship has sailed.
Unless you have the older version somewhere, you can only get the latest version.
Flash is controlled by Adobe, and the package is not in Ubuntu's repo system.
So you can only get whatever Adobe puts out there.
Which is always the latest version.

---

### Post by linux_newbie3 on 2014-02-22
Oh that stinks! My system is borked and I can't roll back to what work flawlessly for me either? Anyone else have any workable solutions for me please? Maybe I will just install Ubuntu 12.04.02 and just not update it at all then. Thanks.

---

### Post by linux_newbie3 on 2014-02-23
[ATTACH=CONFIG]250612[/ATTACH]
See above. I still have the Firefox errors appearing in my browser window.

Does anyone have any other solutions? 

Thanks.

---

### Post by QIII on 2014-02-23
Hello!

Have you attempted to start Firefox from the terminal in safe mode?

```
firefox -safe-mode
```

Is this only happening on sites that have Flash content?

---

### Post by tripp98 on 2014-02-23
I have to deal with different car manufactures and they have issued a  report/notice about the latest version of flash.  We were experiencing  display errors on their sites.  Their request was to remove the latest  version of flash and downgrade it.  These are on windows machines but it  appears that you are experiencing the same issues on your Ubuntu  machine.  i have not been able to find any links to older versions of  flash.  have you tried chrome to see what the results are?

---

### Post by tgalati4 on 2014-02-24
Install google-chrome and use that until a fix is applied to Adobe Flash.

---

