---
title: "Where did Snap come from and why did it mess with the Files directory?"
date: 2022-05-14
forum: New to Ubuntu
---

### Post by cbiweb on 2022-05-14
I've returned to Ubuntu after almost 8 years, and things were going so well. I installed it yesterday, and got a basic setup done, and everything looked good.

This morning when I booted up, suddenly a directory called 'snap' appeared on the desktop.  And now, when I click the Files directory, it opens the Home directory and I can't get to Documents or Music or Pictures, etc.  It just throws an error saying those directories can't be found.

Where did this 'snap' thing come from when it wasn't there yesterday. Is it necessary, and can I get rid of it?

---

### Post by GhX6GZMB on 2022-05-14
Snap is the latest curse to descend over Ubuntu users. My understanding is, that it's an installation management system to make package maintenance easier for the distributions.
Users were not asked their opinion.
When doing a new install on a machine, my first action is do remove snapd from the installation. It's useless, complicates things and slows everything down.
But that's a very personal view.

---

### Post by QIII on 2022-05-14
Things like Snap, Flatpak and Appimage are beginning to show up all over the Linux landscape.  It's not just Ubuntu.

---

### Post by cbiweb on 2022-05-14
I reinstalled.  That won't stop Snap, but I'm hoping that the issue I had was maybe a glitch in the system.  I mean, why would they cut me off from my documents, pictures, downloads, etc.? That makes no sense.

---

### Post by grahammechanical on 2022-05-14
What version of Ubuntu did you install? It helps when people tell us these things.

It seems that you are running Ubuntu 22.04 LTS. I am writing this from 22.04. You say this:

> suddenly a directory called 'snap' appeared on the desktop.

I do not see what you see. But then I have not tried to install Firefox from a compressed file (tar). It is on your desktop, is it not? I am wondering what you have done. Why are you downloading files to the desktop? Have you set the Desktop folder as the default download folder. The snap folder should be inside the Home folder as well as folders for Desktop, Downloads, Music, Pictures, Public, Templates & Videos.

Regards

---

### Post by cbiweb on 2022-05-14
> **grahammechanical said:**
> What version of Ubuntu did you install? It helps when people tell us these things.

It seems that you are running Ubuntu 22.04 LTS. I am writing this from 22.04. You say this:

Yes, having just returned to Ubuntu yesterday, I would have installed 22.04 (and yes, LTS)



> **grahammechanical said:**
> 
...I have not tried to install Firefox  from a compressed file (tar). It is on your desktop, is it not? I am  wondering what you have done. Why are you downloading files to the  desktop? Have you set the Desktop folder as the default download folder.  The snap folder should be inside the Home folder as well as folders for  Desktop, Downloads, Music, Pictures, Public, Templates & Videos.

Regards

All I know is, I downloaded Firefox (I wanted to install the Developer Edition).  I did not tell it to go to the desktop. I haven't set any folders to be any different from the default.  I literally JUST installed Ubuntu last night, and this morning the first thing I tried installing was Firefox.  Go to the FF site, click the download button, let it do its thing, and that's it.  I did no telling of anything to go anywhere different.  I have *never* in my 23 years of computing downloaded a file to the desktop.

As for the snap folder, it just appeared there with no conscious prompting from me.  Same with the FF file and any other file/folder on the desktop.  The error dialog happened when I tried to view the Documents folder.

Just as my opening post said - *suddenly* - this happened.

---

### Post by GhX6GZMB on 2022-05-14
Check out this thread (post #4) where @TheFu has an excellent summary on pests like snap: [https://ubuntuforums.org/showthread.php?t=2475018](https://ubuntuforums.org/showthread.php?t=2475018)

An issue is, that Firefox is only available as a snap, which is what you've experienced.

The traditional method for installing applications on (x)ubuntu is the Synaptic way using PPAs. Works well, is non-intrusive and reliable.

There are ways to avoid snaps when installing Firefox, but as I regard FF as bloatware today, I use a different browser, which is fast and light (Brave).

As I said in my first post: I remove snapd immediately after an install. Never had any problems after doing that.

Welcome back, by the way :)

---

### Post by cbiweb on 2022-05-14
> **ml9104 said:**
> Check out this thread (post #4) where @TheFu has an excellent summary on pests like snap: [https://ubuntuforums.org/showthread.php?t=2475018](https://ubuntuforums.org/showthread.php?t=2475018)

An issue is, that Firefox is only available as a snap, which is what you've experienced.

The traditional method for installing applications on (x)ubuntu is the Synaptic way using PPAs. Works well, is non-intrusive and reliable.

There are ways to avoid snaps when installing Firefox, but as I regard FF as bloatware today, I use a different browser, which is fast and light (Brave).

As I said in my first post: I remove snapd immediately after an install. Never had any problems after doing that.

Welcome back, by the way :)


Thanks ml9104, and thanks for the welcome back! :)

---

### Post by TheFu on 2022-05-14
In Linux, we really don't go and find file on websites to install. We use the package manager.  This is important for beginners. In the last 10 yrs, many things have drastically changed.
Ubuntu is pushing snaps and for many uses, they work fine.

For Linux, firefox has the normal channel and the ESR channel.  The normal channel gets updates and new features from Mozilla quicker. This comes as a Snap package in 22.04, but not in earlier releases.  There are ways to avoid the snap package version, but I wouldn't recommend those to someone new to Ubuntu.
I've seen that Brave (the browser) is also being installed as a snap package on some Ubuntu systems. There may be a method to specify the normal APT package, but I don't know. 

I don't use Brave and haven't moved any of my desktops to 22.04.  I'll probably wait a year, or more, so issues can be corrected and the snap problems I've been experiencing the last 2-3 yrs can have better solutions or work-arounds. Of course, there are non-snap distros. Most of those use flatpaks where Canonical uses snaps.  Right now, there are mostly high-visibility programs getting on the snap/flatpak distribution methods. 

Today, a desktop install has about 2000 packages installed of all types. Of those, probably 10 are snaps.  Firefox, Chromium, and Thunderbird are the ones that most end-users would notice. Let's keep a little perspective.  Almost all packages installed still use APT and the normal package manager tools we know. It is just a few that don't.

Snaps aren't well integrated in to the update programs we've been using since the 1990s either and they update automatically - checking 4x a day - by default. We can change those defaults.  Mine are once a week.  Also, snaps will have at least 2 versions of the package on your system, but 3 is the default. We can change that too.  Why I'd want 3 copies of a snap package and 3 copies of the dependent library snap packages on my Chromebook with 16GB of total storage, I don't know. Fighting with a full HDD sucks.

---

### Post by DuckHook on 2022-05-15
> **ml9104 said:**
> Snap is the latest curse to descend over Ubuntu users. My understanding is, that it's an installation management system to make package maintenance easier for the distributions.
Users were not asked their opinion.
When doing a new install on a machine, my first action is do remove snapd from the installation. It's useless, complicates things and slows everything down.
But that's a very personal view.
A personal view indeed. And an unfair and misleading one at that.

@cbiweb

To answer your actual question:

It's more accurate to say that snaps are a new packaging system promoted primarily by Canonical. It is designed to do some good things, but is currently rough around the edges and executes some things poorly. It is bound to get smoother with time, but that doesn't help you with your current circumstances. Here's a more balanced assessment:

Pros: 
[LIST=1]
[*]Snaps naturally sandbox your apps so that a rogue app or piece of malware has limited access to your system. 
[*]Snaps allow apps to package all the required libraries needed to run, no longer restricted to only those libraries installed on the base OS. 
[*]Snaps allow developers to issue up&#8209;to&#8209;date apps and take responsibility for keeping their apps current independently of Ubuntu's lagging repos.
[*]Automatic forced upgrades mean generally better user security hygiene. Left to themselves, the level of computing hygiene practiced by certain users approaches the cringeworthy.
[*]
[/LIST]
Cons: 
[LIST=1]
[*]Poor sandboxing implementation can break workflow, necessary access and the app itself (what you are experiencing). 
[*]Packing all of those libraries for each app leads to system bloat and increased redundancy/inefficiency. 
[*]Launching snap apps takes more time and uses more resources in RAM and sometimes CPU. 
[*]Leaving app upgrades to their devs means far less oversight from Canonical and raises questions about snap app security/integrity.
[*]Automatic forced upgrades mean that users lose the control that Linux is rightly famous for. Sometimes, upgrades will break a mission&#8209;critical usage that requires an older version of an app.
[*]
[/LIST]
Snaps are still a relatively new technology and are a mixed bag. Like all new tech, it riles up people who don't like change. Some of the criticisms directed at snaps are legitimate. Some are just knee&#8209;jerk from people who think things like electricity to be the devil's handiwork.

The problem you are confronting arises from Canonical's decision to offload FF maintenance to the Mozilla team. Hence, they hived off FF to a snap. There is no choice in a default Jammy install—you can only get FF as a snap.

To work around your problem, see the last part of this post.
> **ml9104 said:**
> There are ways to avoid snaps when installing Firefox, but as I regard FF as bloatware today, I use a different browser, which is fast and light (Brave).
Um, welllll…

Not really that light.

All full fledged browsers have no choice but to be heavyweights these days. People expect them to be Olympic decathletes, so how else can they be?

[LIST=1]
[*]Lightweight browsers are ones like Midori and Epiphany. 
[*]Featherweights would be Dillo or Links2. 
[*]Flea&#8209;weights would be purely CLI browsers like Lynx or W3M, though these last would appeal only to über&#8209;geeks.
[/LIST]
I suspect that none of the above would be acceptable to the average user.

You are also going overboard about FF. It has its advantages, one of which is that its underlying Gecko engine is arguably more secure than Chrome's Webkit/Blink from which Brave is in turn derived. That is the reason why TOR chose FF as its progenitor for TOR Browser.

Brave is a fine piece of work. I really like its ad&#8209;free, script-restricting, cooking&#8209;killing, tracker&#8209;nerfing, privacy&#8209;preserving defaults. I use it co&#8209;equally to FF. But dismissing FF out of hand for one perceived fault does not present a balanced view of the browser landscape.

@cbiweb

It's true that Ubuntu offering only snap FF has caused many issues. Unfortunately, until they are worked out, experiences such as yours will continue to crop up. FF continues to be a good browser. The snap issues do not reflect on the browser itself.

Here is a recent thread detailing some of the strategies that you can use to install an alternate FF: [https://ubuntuforums.org/showthread.php?t=2473114&p=14087587#post14087587](https://ubuntuforums.org/showthread.php?t=2473114&p=14087587#post14087587)

A further caution:

The "traditional" method for installing apps is not through PPAs. Unless you are thoroughly familiar with the maintainer, PPAs are vectors for outdated software, incompatible libraries, apt breakage, bugs and even malware. PPAs are far more insecure than snaps because they have full access to your system. There is no sandboxing with PPAs unless you take independent measures to do so: either running them in a VM, a container or a real sandbox like FireJail.

If you are not a power&#8209;user, install PPAs with ultra caution and exceedingly sparingly. In your case—if you should decide to go that route—I would only recommend the Mozilla Team PPA and no others: [https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)

---

### Post by cbiweb on 2022-05-15
> **DuckHook said:**
> 
@cbiweb

To answer your actual question: ...

<snip> ... </snip>

If you are not a power&#8209;user, install PPAs with ultra caution and exceedingly sparingly. In your case&#8212;if you should decide to go that route&#8212;I would only recommend the Mozilla Team PPA and no others: [https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)

DuckHook, thank you for taking the time to explain all that so thoroughly! Super appreciated! Very helpful indeed. I was beginning to rethink my choice to return to Ubuntu, but your post makes me think I can probably work through it. :)

For the record - and others who read this - I prefer Firefox Developer Edition because, well, I'm a developer. So if there's a way to get it, I will. FF is still a good browser (they had a bit of a down-slide for a few years, but they recovered nicely), and it's the only browser I'll use for development until something better comes along (which isn't Brave, btw ;) )

---

### Post by TheFu on 2022-05-15
I'm with you cbiweb.  There are some complex websites that other engines just don't display correctly, which Firefox does. OTOH, I have a date() issue in a firefox webapp that doesn't happen anywhere else since the latest DST change happened. Nowhere else does this happen. It was happening in some complex, large, external websites, but they've since fixed the issue, somehow.  Alas, I'm not as smart. The webapp is fairly complex and uses far too much javascript for the needs, IMHO.  The UX devs almost always forget to hook up keyboard controls for dumb things like &#8594;/&#8592;, &#8593;/&#8595;, pgup/pgdw scrolling.  Drives me crazy.

DuckHook, provided a more measured answer. Very helpful.

The sky is NOT falling over snaps. But if you have complex workflows, especially test workflows, you may find that snaps prevent those from working. Depends on the test tool and how it works.  

Snaps aren't the only thing in the way for automatic testing or just straight GUI automation.  Some X11 capabilities (more are security bugs that have been known in X11 for decades) are being closed as more and more distros move from X11 to Wayland. I'm unsure what I'll do in 3-5 yrs, if X11 is effectively gone. It may not matter then.

Snaps really aren't THAT new.  They've been around since at least 2017, so there has been 5+ yrs of working on the main issues.  There are some really cool things that snaps do too.  When people post here, we often see only the issues.  For the 50,000 things our Ubuntu systems do daily, it is the 5 that don't work which bother us the most and get far too much of our time in these posts.
It is frustrating to see bugs reported in the 2017 snap system still open saying that some upstream project is the issue. Passing the blame doesn't solve the issue. As long as the issue exists, there needs to be a usable workaround provided by the snap team.

If you are running Firefox for web development, I truly hope you run 4 versions, on at least 4 different platforms.  With Linux, having multiple versions - say the Dev, normal, latest ESR and older ESR versions.  After all, your clients are running all of these with corporate users more on the ESR version.  

Producing code that only works on the latest version of anything is a common  developer mistake.  For about 15 yrs, I earned my living doing cross-platform development.  We wouldn't consider moving to the newest OS/platform until an enterprise client specifically asked for it.  As Solaris 9 was being released, we were just starting to move off Solaris 7.

---

### Post by DuckHook on 2022-05-15
> **cbiweb said:**
> …I was beginning to rethink my choice to return to Ubuntu, but your post makes me think I can probably work through it. :)

For the record - and others who read this - I prefer Firefox Developer Edition because, well, I'm a developer. So if there's a way to get it, I will. FF is still a good browser (they had a bit of a down-slide for a few years, but they recovered nicely), and it's the only browser I'll use for development until something better comes along (which isn't Brave, btw ;) )
Our philosophy on these forums is "use what works for you". If this means Windows, then use Windows, If this means MacOS, then use MacOS.

That out of the way, it should also be noted that, as a self&#8209;described developer, you will easily have the skills to make Ubuntu work for you. Don't let the whole snaps issue dismay you. Throwing out Ubuntu because of one irritating platform would be throwing out the baby with the bathwater (IMO).

If you want to use FF DE, then there is no PPA—not one I would trust anyway. More specifically, I only trust the PPA I cited in my previous post because it is authored and maintained by a team of devs from Mozilla itself. I can have some reasonable assurance that they aren't rogue, will be around to keep their PPA current, bugs will be squashed and that they are malware&#8209;free. I cannot bring myself to trust PPAs owned by any John Doe.

For FF DE you have two options:

[LIST=1]
[*]I believe the beta channel has the dev tools packaged in that version. It is also maintained by the Mozilla team, so security is acceptable. But the main drawback would be that it's a beta. Not exactly the most stable development platform, which could be a deal breaker. The beta channel is: [https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next](https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next)
[*]Download the standalone DE from Mozilla and install it independently. Bypassing the repos has certain benefits and certain drawbacks, but overall, I think this is the best strategy for you. The standalone version is supposed to alert you to new versions and I'm told that it will then download and update newer versions with little additional effort from you. This is only hearsay on my part as I prefer to add the PPA and rely on apt. You can get the standalone .deb from here: [https://www.mozilla.org/en-US/firefox/channel/desktop/](https://www.mozilla.org/en-US/firefox/channel/desktop/)
[*]
[/LIST]

Good Luck and Happy Ubuntu-ing!

---

### Post by deadflowr on 2022-05-15
Looking at the screenshot I'm not sure snaps are the issue here.
The issue is you have only the snap and the firefox.tmp directories in Home.
It cannot find the Documents folder because it does not exist.
Somehow you either deleted the Main Directories or they never existed in the first place.
 
The snap and firefox.tmp directories where regenerated whenever you ran firefox.
So those being there and other directories not makes sense.
(though the firefox.tmp directory should be in the Downloads folder, but I do not know what happens if that folder does not exist, so...)

I see Trash is still listed, does it open?
And is there anything in there?

Also, is the system setup in any odd or different way than a regular system is,
like is home on a separate partition or symlinked or network shared or something.

Or perhaps have you ran a backup restore (maybe?) that set things up this way?

If anything snaps are coincidental to what's happening. But not a cause.
You would be the first user that I have heard of having this happen because of snaps.

---

### Post by cbiweb on 2022-05-15
> **deadflowr said:**
> Looking at the screenshot I'm not sure snaps are the issue here.
The issue is you have only the snap and the firefox.tmp directories in Home.
It cannot find the Documents folder because it does not exist.
Somehow you either deleted the Main Directories or they never existed in the first place.
 
The snap and firefox.tmp directories where regenerated whenever you ran firefox.
So those being there and other directories not makes sense.
(though the firefox.tmp directory should be in the Downloads folder, but I do not know what happens if that folder does not exist, so...)

I see Trash is still listed, does it open?
And is there anything in there?

Also, is the system setup in any odd or different way than a regular system is,
like is home on a separate partition or symlinked or network shared or something.

Or perhaps have you ran a backup restore (maybe?) that set things up this way?

If anything snaps are coincidental to what's happening. But not a cause.
You would be the first user that I have heard of having this happen because of snaps.

A lot of that is answered in the first few posts of the thread. :)

---

### Post by ajgreeny on 2022-05-15
To try to find your main directories from home, eg Documents, what is the output of command ```
find Documents -type d
```

Perhaps you have inadvertently moved the whole directory (and the others) somewhere else in your filesystem; this command might tell you where that now is.

Can you also show us the content of your ~/.config/user-dirs.dirs file which lists the user directories that should be present and I believe are created if absent when you reboot or login.
I also can see you have bookmarks in the left hand pane of the file-manager so it may be worth seeing what is in your ~/.config/gtk-3.0/bookmarks file

---

### Post by pi-piper on 2022-05-25
Duckhook... I want to say that I think your answer is spot on..
I am new to Ubuntu and upgraded to 22.04 a few weeks ago. (when I say I am new, I mean NEW) I started with Windows back in the early 80's, then Mac till recently. Now at 74 I decided I need a challenge.
I have been running the Ubuntu 22.04 without glitches and the updates come in almost daily. I am not a heavy user, (I would like to be but the brain can only cope with so much) I gave up playing with Home Assistant as it was getting too complex for me) 
I now have a YubiKey 5NFC and attempting to set that up so I do not need passwords (another challenge) Of course I rely on web sites for info and copy and paste in to the command line. Mostly unsuccessful but I keep going..
In short and as a new user I have had no issues at all with Ubuntu 22.04

---

### Post by Tadaen_Sylvermane on 2022-05-27
> [COLOR=#000000]Snap is the latest curse to descend over Ubuntu users. My understanding is, that it's an installation management system to make package maintenance easier for the distributions.[/COLOR]
[COLOR=#000000]Users were not asked their opinion.

With all due respect I'd like to address this.

 Canonical does what they want. Take it or leave it. They manage the entire Ubuntu thing including what goes in it. They don't much care what you want nor are they obligated to care. Maybe a bit more than Microsoft does but if they see something that helps them with their goals then they will do it if they choose. If you don't like it you can remove it else go to another distro. While they are not obligated to "ask the users" the users are not "obligated to stay with Ubuntu".

Would you say the same thing about Red Hat? Suse? They along with Ubuntu, while open source are managed by corporate entities and those entities decide how they are assembled. Not the users directly. Anyone is free to fork any of them. If one isn't willing to do that then it needs to be accepted or move on. Don't complain about something that you pay exactly zero for.[/COLOR]

---

