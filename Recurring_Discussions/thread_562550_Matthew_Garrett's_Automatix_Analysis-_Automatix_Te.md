---
title: "Matthew Garrett's Automatix Analysis- Automatix Team Member's Response"
date: 2007-09-28
forum: Recurring Discussions
---

### Post by jtbl on 2007-09-28
First let me start off by saying that most of the issues stated in this analysis will be fixed in the Gutsy version of Automatix.  For more information on that visit:
[http://www.getautomatix.com/forum/index.php?showtopic=1558]("http://www.getautomatix.com/forum/index.php?showtopic=1558")

Now to answer the question of whether or not Automatix can break systems. Automatix can possibly break certain components in certain situations.  The problems usually occur when the usage of Automatix is mixed the usage of other installation scripts or third-party repos.  When Automatix is developed and tested, its only designed to be compatible with the Ubuntu repos, the Automatix repos, and third-pary repos used by Automatix.  It is impossible for the Automatix team to make Automatix compatible with every installation script and third party repo available for Ubuntu.  Hopefully, with Automatix's new community development model, other installation scripts and third party repos will become compatible with Automatix.

---

### Post by jrusso2 on 2007-09-28
Thanks for the reply and your efforts.  I have always had good luck with Automatix and I appreciate you taking the time and effort to offer it.

---

### Post by p_quarles on 2007-09-28
I don't really think that constitutes a response to Garrett's criticisms. [Here's]("http://http://mjg59.livejournal.com/77440.html") the link if you want to read it again. 

I'm *not* interested in a flamewar here, but I think it would be beneficial for an automatix dev to respond in more detail to the specific criticisms (which were far beyond "Automatix can possibly break certain components"). That's why I clicked on this thread.

---

### Post by kadath on 2007-09-28
Automatix is so terribly redundant. I don't understand how downloading, installing and running Automatix to download other apps is somehow easier than enabling all the repos and adding the Medibuntu repo via Synaptic.

---

### Post by starcraft.man on 2007-09-28
> **jtbl said:**
> First let me start off by saying that most of the issues stated in this analysis will be fixed in the Gutsy version of Automatix.  For more information on that visit:
[http://www.getautomatix.com/forum/index.php?showtopic=1558]("http://www.getautomatix.com/forum/index.php?showtopic=1558")

Now to answer the question of whether or not Automatix can break systems. Automatix can possibly break certain components in certain situations.  The problems usually occur when the usage of Automatix is mixed the usage of other installation scripts or third-party repos.  When Automatix is developed and tested, its only designed to be compatible with the Ubuntu repos, the Automatix repos, and third-pary repos used by Automatix. 

Holy cow, you have to be joking... it's been almost 2 months since that report. More? Less? When did we get that analysis? I know early August or so. Anyway, now you choose to respond and say "it's safe"? That doesn't seem much of a response either as p_quarles pointed out. I also noticed you said ***most*** of the issues, not all.

> It is impossible for the Automatix team to make Automatix compatible with every installation script and third party repo available for Ubuntu.  Hopefully, with Automatix's new community development model, other installation scripts and third party repos will become compatible with Automatix.
Right, there is an easy fix to this though. Teach users how to install packages/programs/whatever through proven official means, manage their computer on a daily basis effectively and don't get them to use scripts/third party services. No problems happen that way in my experience. An informed and knowledgeable user is a self sufficient and independent one.

Anyway, you can make all the fixes you like, none of them will ever address the two core issues I have with recommending Automatix to new users. I'd get into those reasons, but it'd just spiral out into another heated and pointless discussion, which I'm not interested in. That's my 2 cents.

---

### Post by southernman on 2007-09-29
> **starcraft.man said:**
> 
Right, there is an easy fix to this though. Teach users how to install packages/programs/whatever through proven official means, manage their computer on a daily basis effectively and don't get them to use scripts/third party services. No problems happen that way in my experience. An informed and knowledgeable user is a self sufficient and independent one.

Enough said... or should be at least. I've never contemplated using any thing of this sort, for the very reasons you mention. The only thing I disagree with you on, is when you say:

> No problems happen that way in my experience.
It's bound to happen (which I know you agree - know) the occasional foul up is going to occur. 

To me, the whole ideal of using GNU/Linux in the first place is to have more control over what my computer does. If I wanted a borked system I'd use that other OS! *wink*

Why do I get the feeling that UF will be getting ddos'ed again? *ponders* I am not suggesting that... well, err, ummm, never mind!

---

### Post by starcraft.man on 2007-09-29
> **southernman said:**
> Enough said... or should be at least. I've never contemplated using any thing of this sort, for the very reasons you mention. The only thing I disagree with you on, is when you say:

Glad I'm not alone in my thinking.

> It's bound to happen (which I know you agree - know) the occasional foul up is going to occur. 
Murphy's Law combined with the chaotic nature of the universe (and other tid bits) preclude any possibility of perfection/problem free from ever existing (OSX isn't even perfect and how much closer can you get?). 

So yes, I know most users are eventually going to run into a problem. I suppose what I meant to say is that in my experience the odds of an informed user running into a problem drastically decrease in likelihood and severity when one doesn't rely on such scripts and is knowledgeable about his/her system's basics/daily operation.

> To me, the whole ideal of using GNU/Linux in the first place is to have more control over what my computer does. If I wanted a borked system I'd use that other OS! *wink*

Yup, I agree. To that end I am working toward greater documentation (that's why I been kinda quiet. Working on my own so haven't been around as much) for Ubuntu and educating/helping users. I think teaching is the most effective means when combined with incremental OS improvements.

---

### Post by p_quarles on 2007-09-29
> **starcraft.man said:**
> Glad I'm not alone in my thinking.
Definitely not. When I first installed, I got all the proprietary/extra stuff running about a month before I even knew what Automatix was. 

And, yes, I'm on the geeky side, but I was still completely new to Linux and the directions in the user documentation wiki worked for me on the first try.

---

### Post by jtbl on 2007-09-29
The reason for the late response it that all of the Automatix Team members have been very busy for the past 2 months.  One of us has finally got around to writing a response.  I know it wasn't much of a response, but the specific bugs that Matthew Garrett discovered will be fixed.

There is part of his analysis I would like to further discuss, the dependency handling. When Automatix was originally created it was an installation script, and it still is, however it has become more advanced over time.  Dependency handling is usually found in package managers, like synaptic, and not usually found in installation scripts like Automatix.  The dependency management duties in Automatix are left up to apt and the Automatix developers.  If a .deb is installed through apt its dependencies will get installed along with it.  If its installed through dpkg then the Automatix devs will find out that .deb's dependencies and have Automatix install them through apt first.  Now a compressed, precompiled, archive follows the same dependency management technique as a deb being installed through dpkg, the only different is the archive is instead extracted into /opt/automatix/appname.  Now package removal is a bit tricky as we don't want to remove dependencies for other applications when removing one application.   When removing an application in Automatix, only the application is removed and not its dependencies.  This is where the drawback to being an installation script shows itself.

---

### Post by aysiu on 2007-09-29
For users who don't want to learn how to do things manually, I'd recommend Linux Mint over Automatix.

---

### Post by wolfen69 on 2007-09-29
> **aysiu said:**
> For users who don't want to learn how to do things manually, I'd recommend Linux Mint over Automatix.

i agree. linux mint is a great live cd to give out to people who are interested in linux. i'm using it now just because i like the menu structure and default look.

---

### Post by asmoore82 on 2007-09-29
> **starcraft.man said:**
> (OSX isn't even perfect and **how much closer can you get?**).

Red Hat 6.0 ??

Coming from a wealth of Linux and hence UNIX experience;
IMHO, OSX is a tangled mess of
"Please give me X11 and a Real Mouse!"

---

### Post by bapoumba on 2007-09-29
Moved to "Recurring Discussions".

---

### Post by compiledkernel on 2007-09-30
Unable to see full assessment on getautomatix site. Is the site down? 

Im recieving 404s.

---

### Post by American_Outcast on 2007-09-30
I have been reading up on some of the issues with Automatix. I have used it and installed it on another family members computer. I haven't had any problems with it, well that I have noticed. From experience I can't say anything negative about Automatix. I will keep a close eye on it for now just in case. I am also going to update from 7.04 to 7.10 and see if there are any issues, (of course after I back everything up just to be on the safe side, lol.)

And yes. I tried going to that website and it seems to be down.

---

### Post by jtbl on 2007-09-30
The site is currently down because of a ddos attack.

Edit: I just completed the bash code and everything Matthew Garrett has mentioned, except a few minor cosmetic issues, has been fixed.

---

### Post by jtbl on 2007-09-30
One thing that is said a lot on the Ubuntu Forums is that Automatix can cause problems when users are upgrading their systems.  I look through the forums and see many people having problems and also many having no problems at all. First let me start off by saying that as a person who has an above-average level of knowledge of the three major operating systems, never do a upgrade from one version to another.  The amount of problems you will have can vary but more often than not there will be problems with the upgrade.  The only exception to this rule that I have seen is a few installs of Mac OS 8. All of the Automatix developers would agree with me on this along with many other tech savvy people.  
So does Automatix cause problems when a user is upgrading their install of Ubuntu?  It might, but so can a poorly maintained package in universe/multiverse, a .deb found in a third-party repo, or even that really cool tweak to make Ubuntu do some really cool thing it wasn't meant to do by default that was found somewhere on the net.  So to stay safe, whether you use Automatix or not, never do an upgrade.  If you do wish to upgrade and do use Automatix, follow these steps:

Install the latest updates for the version of Ubuntu you are currently running

Install the latest version of Automatix

Run Automatix and uninstall everything

Run these next two commands in the terminal:

sudo apt-get --assume-yes --purge remove automatix2
rm -rf ~/.automatix

Upgrade Ubuntu

Install the latest version of Automatix for the version of Ubuntu you are now running

Run Automatix

---

### Post by reyfer on 2007-09-30
So, let me see if I understand: what I have been doing for the past five years, first with Debian and now with Kubuntu (upgrading) is not safe? Wow. What a lame excuse to cover the fact that Automatix DOES cause problems with upgrade. The only time I had upgrade problems, was when I used Automatix and upgraded from Dapper to Edgy. As I said, I have NEVER before or after that had ANY problems with upgrades.
So in your opinion everybody should just do a clean install?

---

### Post by jtbl on 2007-09-30
Just because there were problems with the upgrade doesn't mean Automatix was the cause of the problems.  I have yet to see any proof that Automatix is what broke an upgrade. All that has been said is that "Automatix broke my system after an upgrade."  With vague reports like this, I, and the other Automatix devs, are not able to fix any problems that could be caused when upgrading.

---

### Post by reyfer on 2007-09-30
See? Now you're talking: > I, and the other Automatix devs, are not able to fix any problems that could be caused when upgrading. And that's understandable because your script was not meant to upgrade with the distro. But from that to saying that people should never upgrade, well.....

By the way, just a small observation, when you talk about yourself as "a person who has an above-average level of knowledge of the three major operating systems", it sounds as if you're calling the rest of us ignorants. I know it was not your intention, but it seems like that.

---

### Post by compiledkernel on 2007-09-30
Threads Merged, same relative topic.

---

### Post by starcraft.man on 2007-09-30
Oh goodie!! Another post about Automatix, I wake up every day just wondering when the next one will pop into the community cafe (now merged in recurring). Is this going to be a daily thing leading up to the launch for Gutsy?

---

### Post by jtbl on 2007-09-30
"Automatix broke my system after an upgrade."  With vague reports like this, I, and the other Automatix devs, are not able to fix any problems that could be caused when upgrading.

I believe that was the full statement.

I am just trying to stop the spread of FUD about Automatix.

---

### Post by reyfer on 2007-09-30
> **jtbl said:**
> 
I am just trying to stop the spread of FUD about Automatix.
That's okay. But spreading FUD about the upgrade process is not the way. I repeat: I have been using the upgrade process for five years, first with Debian and then with Kubuntu. Only times I needed clean install were the first time I installed Kubuntu (Breezy), and when something broke the upgrade from Dapper to Edgy. And the only different thing I had on my system at that point  was Automatix. Before and after, without Automatix in my system, upgrades have gone great (minor solvable problems with X, but that's all). Maybe Automatix was not to blame, but until I have proof to the contrary, it is the prime suspect. 

Automatix is a good thing for new users, but since that incident, I am using the old apt-get and synaptic way, and also compiling myself.

---

### Post by p_quarles on 2007-09-30
> **jtbl said:**
> One thing that is said a lot on the Ubuntu Forums is that Automatix can cause problems when users are upgrading their systems.  I look through the forums and see many people having problems and also many having no problems at all. First let me start off by saying that as a person who has an above-average level of knowledge of the three major operating systems, never do a upgrade from one version to another.  The amount of problems you will have can vary but more often than not there will be problems with the upgrade.  The only exception to this rule that I have seen is a few installs of Mac OS 8. All of the Automatix developers would agree with me on this along with many other tech savvy people.  

> **jtbl said:**
> "Automatix broke my system after an upgrade."  With vague reports like this, I, and the other Automatix devs, are not able to fix any problems that could be caused when upgrading.

I believe that was the full statement.

I am just trying to stop the spread of FUD about Automatix.
I'm not really sure how the above two statements get along with each other.

More importantly: you're accusing Matthew Garrett of FUD? Your statements so far have included "no, that wasn't much of a response, but I've been busy" and "the new version of Automatix responds to all the points that MG criticized." Care to be more specific?

---

### Post by jtbl on 2007-09-30
I never accused him of FUD.  Matthew Garrett was one of the very few people that actually gave a bit more detail than just "Automatix breaks systems."  Because of his report, the Automatix devs were able to fix the problems and improve Automatix.  Spreading FUD and saying "Automatix Breaks Systems" gets us nowhere.

The reason you may have though I was accusing him was because the statement was meant for another thread titled "Does Automatix cause problems when upgrading? An Automatix Team member's response", and that thread was merged with this one.

---

### Post by compiledkernel on 2007-09-30
Im not sure its a matter of spreading FUD, jtbl. Its more a matter of past experience. Yes there exist users that have used automatix to the point that it broke their system. Does this meant that all systems that use Automatix were or will  themselves become victims of system breakage? No, most certainly not. But the Potential is there, and does exist. It could happen. And for some people (opinions notwithstanding), it would seem that Automatix breakage is more consistent than some system breakage caused by Ubuntu's own packages. 

Id imagine you need to concentrate more on correcting the issues, (which as of now it seems you might have done), then spending time trying to fend off what you call FUD. 

Engage Garrett again with your newely fixed product, and allow him (or whomever else there is) to look at the code and make another assessment. If indeed you have fixed as you say you have, then id think that kind of move would glorify you a lot more than posting rampant statements about how youve fixed things and so forth. Unless of course you havent fixed anything, or fixed things and created problems in other areas. Then of course doing the above might not be a good idea, and then ultimately, youll be fighting FUD wether you like it or not. 

Defeat FUD by producing a product that does not create the problems the FUD your fighting against speaks about.

---

### Post by jtbl on 2007-09-30
The bash and xml code is completed and ready for testing. However, we still have to ensure the python code is compatible with Gutsy.  Also, we still have a few things to do with python code, basically removing old code no longer being used. The first alpha will be available next weekend, after we get our Gutsy repos setup and a few issues fixed on the server. Until then, however, I can send anybody a copy of the bash and xml code if they want to look at it. All of the problems Matthew Garrett found were in the bash and xml code and they have been fixed.

> **compiledkernel said:**
> 
Id imagine you need to concentrate more on correcting the issues, (which as of now it seems you might have done), then spending time trying to fend off what you call FUD.

The problem is unless people that are having problems can tell me what the problem is I cannot fix it.  Just saying Automatix caused it is too vague.

---

### Post by frodon on 2007-10-01
Like aysiu well said it, i find automatix and install helper scripts in general being a non-sense if the argument is the ease of use because it is far easier to install a customised ubutnu distribution like linux mint or ubuntu ultimate which have all these packages installed from the beginning.

However i perfectly understand the pleasure to develop scripts and the nostalgia that some users feel.

---

### Post by compiledkernel on 2007-10-01
> **jtbl said:**
> 
The problem is unless people that are having problems can tell me what the problem is I cannot fix it.  Just saying Automatix caused it is too vague.

Then point people to your own forums. Run a Bugzilla install somewhere to file bug reports (At one time Launchpad was used for this, it is sadly however not used anymore), or point people to a google code project page (they are relatively easy to setup and maintain, they also supply subversion trunk access), and let people file bug reports there. You easily have a variety of avenues available to yourself to get the information you need, you just need to steer the users in the right direction, rather than trying to fight issues here on the UF.

---

### Post by pdlethbridge on 2007-10-18
I have had no problems using automatix with feisty or gutsy. What I have noticed is that there are much fewer downloads in automatix for gutsy. I think about 15 or 16, not like the last version that had maybe a hundred. If there are fewer files to install, there should be less problems and less whining. :rolleyes:

---

### Post by jtbl on 2007-10-18
We will be offering upgrade assistance for Automatix users today, Thursday October 18, starting at 6 A.M. Central Time on our irc channel #Automatix on irc.freenode.net

---

