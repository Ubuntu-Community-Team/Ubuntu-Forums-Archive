---
title: "How to select updates for my version of Ubuntu?"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by germeten-i on 2013-11-29
My computer has begun to run very slow. I thought it might be the Update Manager co-opting system resources. I disabled automatic updates but I still get the orange triangle(!) to manually check updates and don't know if this alert is slowing down my system or not.  There are too many update apps and I don't know which one's I need for my system and which ones I don't need, vs. merely desirable. (I have no idea what KDE, gnome, etc. mean) Last time I installed them all and my tech friend had to deinstall some because they weren't needed and hindered performance. I don't like being dependent on my tech friend.

I tend to have lots of open browser windows and need to restart often just to have a semblance of speed. If it's not the browser, what's slowing me down? I have over 2 Ghz processor, a gig of memory and 10mbs connection which was more than adequate for speed months ago, but now everything is slow as molasses and I get nothing done. Is it the NSA capturing emails or browsing history? Is it just me?

---

### Post by fantab on 2013-11-29
Stop being paranoid, I don't think NSA is to blamed here unless you are involved in some prohibited/suspicious activity. Even it they did that won't slow down your PC. I am sure they carry out their 'snooping' activity with minimum footprint on your PC for you to suspect anything.

What version of Ubuntu have you installed? If you are not sure then post the output of the following commands from Terminal [ctrl+alt+t]:
```
uname -a
df -h
```

You say you have "a gig of memory", which I read as 1Gb RAM. This is LOW if you have a standard Ubuntu install. You must either consider adding more RAM (at least a total of 2Gb, more if you can) or install a light versions of Ubuntu, called [LUBUNTU]("https://wiki.ubuntu.com/Lubuntu") and [XUBUNTU]("https://wiki.ubuntu.com/Xubuntu"). If I were you I would go with [**Lubuntu**]("https://wiki.ubuntu.com/Lubuntu").

You can use Terminal to do your update check and install install updates/upgrades with the following:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Bucky Ball on 2013-11-30
Welcome. You don't mention what release you are using ...

Try running this:

```
sudo apt-get autoremove
```

This will remove everything you don't need. Then provide this file from a terminal. Run this command and post the file here:

```
nano /etc/apt/sources.list
```

---

### Post by 3rdalbum on 2013-11-30
> **germeten-i said:**
> My computer has begun to run very slow. I thought it might be the Update Manager co-opting system resources.

Almost certainly not - think about what Update Manager does, it periodically (every day) checks for updates and then does nothing until the next day. Merely displaying a symbol does not even use 1% of CPU power.

> There are too many update apps and I don't know which one's I need for my system and which ones I don't need, vs. merely desirable. (I have no idea what KDE, gnome, etc. mean) Last time I installed them all and my tech friend had to deinstall some because they weren't needed and hindered performance. I don't like being dependent on my tech friend.

Updates will never use more resources than the previous version, unless something is very drastically wrong. Updates within one version of Ubuntu are very conservative - bug fixes or security fixes only, no new features. You can safely install all updates, remember they are only updates for packages you already have, and they replace the old versions.

> I tend to have lots of open browser windows and need to restart often just to have a semblance of speed. If it's not the browser, what's slowing me down? I have over 2 Ghz processor, a gig of memory and 10mbs connection which was more than adequate for speed months ago, but now everything is slow as molasses and I get nothing done.

This depends on what is slow - is it just that web pages load slowly, or does your computer actually take longer to open programs and do non-web-related tasks?

If it's just that the CPU seems to be running slower, you can try running this command:

```
top
```

It will show you what is using the largest amount of CPU power, if your computer is supposed to be fairly idle and yet one program stays at the top of the list with a large amount of CPU% (more than a couple of percent) then it is likely the culprit and you could try killing that program (press K, type the "PID" number and hit Enter, then type 9 and hit Enter).

---

### Post by germeten-i on 2013-11-30
Wow, thank you everyone!

Fantab: 

I blog and send emails mostly, often I have to allow scripts (not globally)
using no-scripts and sometimes BS pop-up windows get through. 

 I ran the version command and got:

uname -adeanvon@deanvon-home:~$ uname -a
Linux deanvon-home 3.2.0-55-generic-pae #85-Ubuntu SMP Wed Oct 2 14:03:15 UTC 2013 i686 i686 i386 GNU/Linux
deanvon@deanvon-home:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        71G  7.0G   60G  11% /
udev            612M  4.0K  612M   1% /dev
tmpfs           248M  976K  247M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            619M  300K  619M   1% /run/shm
deanvon@deanvon-home:~$ 

Bucky Ball:

I know I'm running Ubunto 12.04 LTS, the rest is greek to me. I ran your code and got:

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ pr$
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted #Added by soft$
# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release i386 (20110720.1)]/ luci$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise restricted main multiverse$

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates restricted main mu$

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
                [ Read 88 lines (Warning: No write permission) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

When I check updates I see a lot of apps and such, always close to a quarter gig of stuff, 
it doesn't all seem necessary and how much disk space is really used up after running the 
janitor? (That's a digression from the speed issue, maybe.) Yes my tech buddy has told me 
more than once to add memory but I live on a budget. It didn't use to matter, current memory 
was adequate.

3rdalbum:

Point well-taken but SOMETHING is slowing it down. Could well be Firefox browser but
killing that app also kills what I'm doing! Restarting with the only last open webpage is
the only thing that brings back functionality. (I love Firefox's session manager for saving
tabs, I'm embarrassed to say how many) But opening other apps with firefox as well, 
takes forever, didn't use to.

Hey, that <top> command is cool. Yes it looks like Firefox is using + or - 50% of memory
resources.

---

### Post by deadflowr on 2013-11-30
>  Yes my tech buddy has told me 
more than once to add memory but I live on a budget. It didn't use to matter, current memory 
was adequate.

How much RAM do you have?

---

### Post by DuckHook on 2013-11-30
> **deadflowr said:**
> How much RAM do you have?OP mentioned "a gig" of RAM which I interpret to mean 1 GB. If OP also has an "embarrassing" number of tabs open, then that's the problem right there. More RAM will definitely help. An easier solution is simply to close most of those tabs.

@OP

Firefox (and most browsers) is built so that every open tab is almost like having a separate instance of Firefox running. Okay, I exaggerate, but not by much. The point is that each tab is very memory-intensive. Having an embarrassing number of tabs open on a 1 GB system will quickly exhaust your memory and send you into swap, which will slow your system to a crawl and give you *exactly* the symptoms you are experiencing. If you don't have enough swap space, or disabled your swap, your system will likely crash—Linux does not handle running out of memory very well.

Two simple solutions... pick your poison.

---

### Post by mörgæs on 2013-11-30
Let's hear more about the hardware. Please run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

---

### Post by germeten-i on 2013-12-01
Duck Hook:

Is an open tab in firefox considered open if the page hasn't loaded? For example I thought I could have a very large number
of tabs visible, so long as I hadn't actually visited to reload the page. The pages that ARE loaded, (say video hosting sites),
and blogs with advertising, could very well hog memory.

Morgaes:

I ran that code and got description of the command itself, no HW info.

---

### Post by DuckHook on 2013-12-01
> **germeten-i said:**
> ...Is an open tab in firefox considered open if the page hasn't loaded?Excellent question. In all honesty, I've never experimented because  whenever I open tabs, it's done dynamically. My often-visited sites are  bookmarked and therefore actively invoked when visited. In a low-RAM  system you can see memory being mapped to each additional tab simply by  keeping a terminal open and running either```
top
```or more  summarily```
watch free -m
``` and then opening more tabs. On my  system, on average, each tab is 15KB. Sites like UbuntuOne are, for some  reason, almost 40 KB. YouTube is 30KB. Variances seem to be very  site-specific. Ten tabs is 150KB, 20 tabs is 300KB&#8212;that's 30% of a 1 GB  system. If the system decides to start a background task during this  time (say, update manager), or you have a memory-intensive app open at  the same time (say, GIMP or a photo-editing app), then it could easily  push the OS over the threshold at which it starts invoking swap. And my  experience is that once it goes to swap, you're response time drops to  awful, especially on systems that are resource constrained to start  with.

Perhaps a never-invoked tab takes little/no memory. I don't know. But  then, why have them? Dormancy means they aren't being used, so isn't  that what Bookmarks are for? As to your question itself, it would be  great if you conducted the experiment and reported the results. It  should be easy using the top/free commands above.

&#8212;EDIT&#8212;

More evidence that I'm past my sell-by date... That should have been MB above. The cited usage in KB would be awesome. Unfortunately, it's MB.

---

### Post by fantab on 2013-12-01
The output is saved as a text file. Look in your 'Home' folder for the file 'lshw.txt'.
IMO, and as I expressed it earlier, your performance issues are related to you having only "one gig of RAM". And the simple solution is to either add more 'gigs' of RAM or install a lighter *buntu.

Do you have a SWAP partition? Post the output of 
```
sudo parted -l
```

---

### Post by germeten-i on 2013-12-02
Duck Hook:

Are you saying top will report how much memory a single tab uses???

OK well if I said (sheepishly) that I had maybe 700+ tabs in 4 to 6 windows ready to be opened by mere clicking
(many Youtube & other video sites, ...would I sound like a complete computer illiterate? I don't like using bookmarks, 
that's a needle in a haystack. I do research that can last for months and just keeping a tab is more convenient, 
'cause I may never find a site again, or remember why or where I bookmarked it. (You might presume everyone 
who uses a computer has a well-organized mind, while some of us struggle with that, especially as we get older.)

---

### Post by Bucky Ball on 2013-12-02
You need Zotero. You must have a heck of a good memory to remember where a tab is that you haven't seen for two weeks if you have 700+ of them. You're going to have to close them sometime and if Firefox crashes, you're screwed. Do you have Session Manager installed? I hope so.

I too do research on projects for months and couldn't work without Zotero now, especially if you are inserting references into your documents.

Off-topic, but just a suggestion.

---

### Post by DuckHook on 2013-12-02
You needn't worry about coming across as an illiterate anything on these forums. I make brain-cramped decisions all the time that require the expertise of my fellow forum members to bail me out. But 700 tabs is definitely and absolutely killing your memory space. In fact, it's probably some kind of Guinness World Record.> **germeten-i said:**
> Are you saying top will report how much memory a single tab uses???Yes. Keep it running in a terminal. Look at the info in the header. See the second field on the "Mem" line? That's the memory used by the system. As you open tabs (or in your case, activate tabs) you will see that figure increase. The difference between before and after is roughly the amount of memory that your tab ate up. Right below it is the amount of swap you are using. If swap used is anything more than a number close to zero, your system will start slowing down.

Top tends to be distracting, and the memory used field balloons due to buffers and caching, which top doesn't account for when reporting. It's better to use my second command that gives a truer "used memory" figure on the second line. This is your actual committed memory, stripped of buffers and cache.

Well, you solved at least one mystery for me: it is obvious that dormant tabs don't grab memory (or not much, anyway). If they did, your browser would have splintered into a thousand pieces long before this.> (You might presume everyone who uses a computer has a well-organized mind, while some of us struggle with that, especially as we get older.)<sigh> I am well acquainted with the "getting older" = "disorganized mind" effect. Me? I'm waiting for memory implants. Yup. I suspect that I'll be faster than a speeding bullet and will leap tall buildings in a single bound were I only to get memory implants.

Seriously though, *Bucky Ball* recommends an app that I've never used, but that should help your present needs. His recommendations are invariably useful. What I do know is that you just can't keep going on like this, especially on 1 GB of RAM. Right now, you are just begging... aching... for a crash that will wipe out all of your tabbed history. You've turned your system into a delicate porcelain teacup and I haven't run across a more brittle, fragile setup in a long time. If you don't like Bookmarks, then use Zotero, but you need to do something other than keeping 700 tabs in the air at one time.

---

### Post by jimmyh1972 on 2013-12-03
sudo apt-get update && echo 'y' | sudo apt-get upgrade

---

### Post by JKyleOKC on 2013-12-03
> **DuckHook said:**
> Perhaps a never-invoked tab takes little/no memory. I don't know. But  then, why have them?Your use of an open terminal window running *top* or *watch* is the best way to tell.

Incidentally, the top few lines displayed by *top* are also quite useful for determining whether one is running into swap territory or not. The fifth of those lines tells you all about swapfile usage: how much is available, how much is used, and so on.

As for whether a never-invoked tab is "open" or not, I'd say it's halfway open. As your tests showed, it takes about 15K, which is probably mostly "housekeeping" information; when invoked, it will balloon out to provide buffer space to hold the page being displayed -- and Firefox in particular is notorious for failing to turn such memory back to the system when the tab is closed. Consider the minimum 15K size; since RAM is handled internally as 4K-sized pages, that actually takes 16K from the system. Now if you have 100 such tabs in use, that's more than 1.5 MB taken out of the system. It won't take many pages being opened to push the RAM usage into hundreds of MB, and once you have 25% of the entire available RAM being used by Firefox it won't be very long before swap cuts in and slams the brakes down hard on the entire system!

Adding more RAM is, of course, the best cure for the problem. Even a few hundred MB can make a huge difference in performance. If that's not financially feasible, the other solution would be to change one's operating procedure to use less RAM -- and keeping a terminal open with *top* or *watch* is a great tool for determining what parts need changing.

---

### Post by germeten-i on 2013-12-05
> **JKyleOKC said:**
>  ...the other solution would be to change one's operating procedure to use less RAM -- and keeping a terminal open with *top* or *watch* is a great tool for determining what parts need changing.

Changing my operating procedure is like asking me to not be a hoarder! (LOL) Open tabs serve as memory devices for *me*, threads of
continuity for work-in-progress, however long it takes. My own memory isn't good enough to remember what I was doing, a tab
closed is a thought not followed. Follow-through of our thoughts is what determines our lives.

I noticed that firefox is often using up to 75% of CPU.

Jimmyh1972:  Thank you for that command, if it sorts through the stuff not needed.

---

### Post by JKyleOKC on 2013-12-05
As a confirmed packrat of long standing, I can appreciate that reply!

My own solution to the personal-memory problem is to keep a plain text file (mine has the remarkably meaningful filename "zzz.txt") in my home directory, and add notes at the front of this file each time I work on a different project. I close the file immediately after each such addition, and open it again when I need to refer to the notes. Thus I don't need to keep lots of tabs open in Firefox; I hardly ever have more than two at any instant, and most of the time there's only one.

The "Show All History" command and its search features help greatly when the notes in zzz.txt don't have enough detail, also. It won't show the detailed history of going from one site to another, but it does let me return to any site that I've visited in the past year or two.

When the browser is eating 75% of your CPU capability, it's almost certain that the rest of your system -- and the browser itself -- is churning into and out of the swap partition, and this cuts your speed to less than 1/10 its normal value. However, I did fail to mention a third option in this situation: simply put up with it as a result of not having adequate resources.

Sometimes reality can be quite harsh, unfortunately.

---

### Post by DuckHook on 2013-12-06
There is one more option but it will make your computer even more brittle; not less. Its one and only advantage is that, until your box crashes, it will run relatively quickly. You can set your [swappiness]("https://help.ubuntu.com/community/SwapFaq") to a very low number&#8212;say, "1" or "0"&#8212;and this will prevent your system from going to swap until the last vestige of RAM has been used up. Taking this thinking to its logical conclusion, you could turn off swap altogether and have good speed right up to the point that your computer has its heart attack. Note that I mention this as a technique, not as a recommendation. In your case, turning off swap is simply inviting disaster. The truth is: your setup is already the most fragile one I've ever run across.

BTW, the update/upgrade command does not sort through any unneeded stuff and will not help in your situation.

---

