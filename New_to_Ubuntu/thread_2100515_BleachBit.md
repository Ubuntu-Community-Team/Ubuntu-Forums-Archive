---
title: "BleachBit?"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by Yezinki on 2013-01-02
What options should be checked in Bleachbit as admin & normal & which should be run 1st?

Thanks.

---

### Post by fantab on 2013-01-02
If you use bleachbit as root then it can clean the "junk" from your filesystem which as normal user is not possible because of permissions.

As to what you should clean, Well that is personal IMO. 

I use bleach bit as root first and usually I clean up everything except memory (since it is an experimental feature). And when cleaning as normal users I don't clean my thunderbird passwords.

---

### Post by rburkartjo on 2013-01-02
great program use it all the time. just read what each does and check what you want.

---

### Post by ibjsb4 on 2013-01-02
Here's one hit I got

[http://ubuntuforums.org/showthread.php?t=2062995](http://ubuntuforums.org/showthread.php?t=2062995)

and another

[http://ubuntuforums.org/showthread.php?t=2098095](http://ubuntuforums.org/showthread.php?t=2098095)

---

### Post by Pjotr123 on 2013-01-02
I advise to avoid Bleachbit entirely. Do your cleaning safely:
[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)

---

### Post by Zill on 2013-01-02
> **Pjotr123 said:**
> I advise to avoid Bleachbit entirely...
+1 - Excellent advice IMHO.
> **Yezinki said:**
> I agree Ubuntu doesn't need to be cleaned works unlike windows...
Why do you keep posting questions about Bleachbit when you agree that it is not necessary to "clean" Ubuntu?

You are more likely to break your Ubuntu installation by using Bleachbit than "improve" it!

---

### Post by monkeybrain2012 on 2013-01-02
> **Pjotr123 said:**
> I advise to avoid Bleachbit entirely. Do your cleaning safely:
[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)

Nah, the risk is exaggerated. I have been using bleachbit since 10.04, never has a problem. Apart from the advice about scripts that automatically install stuffs that link is overly cautious, it is like telling people to not to go out after sunset lest you may get robbed, or not to go out at all. It is fear monegring IMO. You run considerably more risks in breaking your system by upgrading your OS through update manager.

---

### Post by monkeybrain2012 on 2013-01-02
> **Zill said:**
> 

You are more likely to break your Ubuntu installation by using Bleachbit than "improve" it!

How? Example please? Have you actually broken your system with bleachbit or just FUD? Have you actually used bleachbit at all? Just don't use the experimental features (e.g clean memory) and you should be fine.

---

### Post by Zill on 2013-01-02
> **monkeybrain2012 said:**
> ...Have you actually used bleachbit at all?..
No, I most certainly have not!  IMHO, there is no justification for installing such software on a Linux system.  Linux systems simply do not need "cleaning" in the way some other OS's do.  OTOH, running tools such as BleachBit, especially as root, could delete files that are desirable for system functionality.

I have been running pure Linux systems for around ten years now and have *never* had systems slow down or break due to an accumulation of "junk"!

---

### Post by JiuJitsu500 on 2013-01-02
Zill, in my opinion, you're both right and wrong.

You're right, absolutely, about bleachbit being 'unnecessary.' Linux by definition and design does NOT need to be cleaned like that. It's a journaled FS like OS X, but handles everything much better and will never, ever slow down due to accumulation of junk. Windows on the other hand, prefers about 30% free space on the installed HDD, where you can run into problems (as I have, though rare enough not to worry). Even OS X and BSD don't handle a desktop as well as linux I don't think. I've had more problems with Mac anyway, mostly just incompitence in simple operations. So yes, Linux does NOT 'need' to have it's own version of CCCleaner and truly won't ever slow down on behalf of accumulation.

BUT, you're wrong I think in the assumption that it won't improve anything. Bleachbit has the functionality to see EVERYTHING you will delete if you run it, and most of it is bash cleaning and autoremove (though deborphan is better for that). If you can isolate and whitelist system files, you will never break your system. I've ran bleachbit every kernel update or upgrade for half a decade on various linux boxes and have never noticed a problem. To ME however, I'm limited in space. I have 2 SSD's at 120GB each, one with Windows 7 and the oher with ubuntu as my most used box. I have a LOT of stuff on there, mostly rosetta stone, VM's, and a couple other large WINE programs and need the free space. That's what bleachbit does for me, and it overwrites the free space when deleting a decent amount of space, rather than a simple delete (where blocks are not truly deleted). 

I'm all for bleachbit, but I FULLY agree that it's completely unnecessary. I need the space, and I like overwriting free space after a mass of torrents or something like a game, or failed WINE project, anything more than 10GB or so. If you don't like bleachbit or don't use it, good for you, as I know full well you don't need it. Linux is just that cool. BUT, you can free up a TON of space if you re-write and overwrite a LOT. I use it and have used it without a problem for a long time, without ever whitelisting a single file. It does seem o have the potential to screw things up as root, but I've never, ever even came close to that. The developers designed it that way.

---

### Post by monkeybrain2012 on 2013-01-02
JuiJitsu500

Agreed with everything you say except that deboprphan IS dangerous. I haven't used it since the early day of 10.04 but I did manage to fry my system with it once. As far as I remember it classifies something as "orphaned" if there is nothing else depending on it so it managed to delete a lot of my system which which were not installed as dependencies. But it was a while ago so things may have changed, and also I was a total newbie back then so it could be that I did something stupid (it was no big deal because it used it on a test partition only), on the other hand bleachbit never did atrocious things like that.

---

### Post by JiuJitsu500 on 2013-01-02
I meant only that deborphan is better at finding orphaned packages.

gtk-orphan is a nice frontend for it too, but you are absolutely right. apt-get autoremove will remove a different set of jazz than deborphan.

Deborphan should be used with extreme caution, it is better at finding orphaned packages, but because the orphan system is dynamic, it can't really tell what is an INDEPENDENT package that doesn't have dependencies (some libraries or python packages, for example). They need nothing to run at all, though some things dynamically require THEM to run. But, deborphan sees them as orphans because they themselves need nothing else and it doesn't see any one program that needs it, as it is dynamically allocated - like you said, not necessarily installed as and thus not seen as a dependency.

Belachbit and autoremove don't do that, which to me makes them much less dangerous. I just meant that deborphan is much better at finding orphaned files. Unless you know exactly what depends on the things deborphan sees as useless, use EXTREME caution. I've screwed up a few fresh installs and tweaks because of deborphan.

---

### Post by Zill on 2013-01-02
JiuJitsu500/monkeybrain2012:  If you are running *any* Windows programs, either directly, in a VM or via Wine then I guess you will be installing lots of junk on your machine and may feel the urge to "clean" it from time to time.

However, regarding orphaned (Linux) packages, I really don't consider a few hundred MB of such programs to be a problem unless you are *really* short of disk space!

These programs just sit there minding their own business and do not slow things down in any way.  With modern HDDs with capacities of hundreds of GB, if not TBs, any orphaned packages can just be left in place.

---

### Post by Pjotr123 on 2013-01-02
Bleachbit, Computer Janitor and accomplices.... I always wonder how they ever made it into the repo's in the first place.... :shock:

They are at best useless and potentially very harmful. Stuff like that should never find it's way on a responsibly maintained Linux system. I've listed them on the "fatal mistakes" page of my website:
[https://sites.google.com/site/easylinuxtipsproject/fatalmistakes](https://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

Windows' "wonderful" ways simply aren't Linux's ways. For some, that's apparently hard to grasp. 

Oh well, I must admit that it was hard to grasp for me as well, when I first started with Linux, back in 2005/2006... At the time, among other things I also frantically wanted to install some useless antivirus. So I suppose I shouldn't be too harsh now. :p

---

### Post by Yezinki on 2013-01-02
Thanks for all your expert recommendations.

I shall use it checking all except the 3, i.e free disk space, localizations & memory.

---

### Post by ibjsb4 on 2013-01-02
> **Pjotr123 said:**
> Bleachbit, Computer Janitor and accomplices.... I always wonder how they ever made it into the repo's in the first place.... :shock:

They are at best useless and potentially very harmful. Stuff like that should never find it's way on a responsibly maintained Linux system. I've listed them on the "fatal mistakes" page of my website:
[https://sites.google.com/site/easylinuxtipsproject/fatalmistakes](https://sites.google.com/site/easylinuxtipsproject/fatalmistakes)


Bias, narrow minded and over confidante is how I rate that.  Everything you state as fact, should be stated as your opinion.

---

### Post by monkeybrain2012 on 2013-01-03
> **Yezinki said:**
> Thanks for all your expert recommendations.

I shall use it checking all except the 3, i.e free disk space, localizations & memory.
You should check localization as well, it removes language packs that you don't need (go to edit > preference > languages and check the boxes for languages you want to KEEP, the rest will be removed. e,g I checked the boxes en and Zh for English and Chinese)

You may also want to uncheck  session restore for your browsers so that in case your browser crashes for some reason you can restore all your tabs.

---

### Post by tartalo on 2013-01-03
I would appreciate examples of problems created by Bleachbit, other than "it removes your browser history if you ask it to", because I'm using and recommending it.

---

### Post by zombifier25 on 2013-01-03
> **tartalo said:**
> I would appreciate examples of problems created by Bleachbit, other than "it removes your browser history if you ask it to", because I'm using and recommending it.

Indeed. It's not like Computer Janitor (which is an abomination to God), it simply removes cache files and other junk and frees up some gigabytes. It does not speed up the system, it simply frees up space. The normal things that it does are in no shape of messing up your system (cache files, browser history, etc.). And about the experimental functions, well, it warns you that they are experimental doesn't it?

I do agree that launching it as root has some risks, but I use it carefully and safely. Computer Janitor, on the other hand,...

---

### Post by Pjotr123 on 2013-01-03
> **ibjsb4 said:**
> Bias, narrow minded and over confidante is how I rate that.
Happy New Year to you, as well. :)

> Everything you state as fact, should be stated as your opinion.

But of course it is. That goes without saying... When I give advice, it's *always* based on my own personal opinion and personal experience. 

Do with it what you think fit... It's all the same with me. No hard feelings either way. :cool:

---

### Post by JiuJitsu500 on 2013-01-03
I also now kind of wonder how the repos included bleachbit and that terrible computer janitor... Or any kind of anti-virus... I've never need one in windows at all, or mac either, let alone linux!

I NEED that space. You're right though, most new HDD's are WAY bigger than anyone would ever realistically need. I actually do need those 'few hundred' MB, or the GB's that it  from time to time.

What's wrong with removing old cache files though? I never said that bleachbit improves anything except freeing up space. I recommend it still, like a boss. I'm also a little drunk and kind of want to argue, so don't listen to me right now lol.

bleachbit is fine, but totally unnecessary. Over time, I'd clean the caches manually anyway, bleachbit jsut does everything I would minus removing old kernels. But computer janitor has screwed up my ancient Jaunty, KArmic, Lucid and Maverick installs. Natty slowed down but didn't break, and I haven't used it even in a VM since. That app is awful!

EDIT* Oh, wait.... there is absolutely no need to use the "free memory" option often either, I use it to wipe the drive when I have a TON of space I'd like completely clear, or when I'm wiping and formatting a new drive. It takes a while too, and anything more than a few GB in a standard HDD can take a LONG time. I'd only do it after moving a lot of files, but you never really need to.

---

### Post by mysteriousdarren on 2013-01-11
Well Bleachbit is for newer users, many of the things that JiuJitsu500 have said I did myself. It makes it easier, to do all those things and more. By using Ubuntu Tweak I also can clean old kernels, faster and quicker than ever before. I pride myself in efficiency, and hate wasting time.

---

### Post by Yezinki on 2013-01-11
Thanks mysteriousdarren for your expert reply.

I'm a noob & have heard that Ubuntu Tweak or Janitor at times can break Ubuntu?

How do I install Ubuntu tweak?

Considering that am a new user which options should be checked in Bleachbit?

---

### Post by publish905 on 2013-03-07
I would strongly advise against using Bleachbit.  I've used it two times since installing it and it has completely messed up my server. It removed samba and some other packages. Now, when I even try to update packages, there are a bunch of error messages.  I am so sorry I even installed it. All I did was do a system clean. I had unchecked memory but I had deep scan checked. Even when I tried to reinstall the packages that Bleachbit messed up, I still got errors.

Bleachbit is terrible to use for Linux server, but good for Windows. I do use it for Windows and like it for that system.

---

### Post by slickymaster on 2013-03-07
> **Yezinki said:**
> How do I install Ubuntu tweak?

```
sudo add-apt-repository ppa:tualatrix/ppa 
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

---

