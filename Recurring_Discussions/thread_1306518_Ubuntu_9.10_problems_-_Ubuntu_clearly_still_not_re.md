---
title: "Ubuntu 9.10 problems - Ubuntu clearly still not ready for the mainstream"
date: 2009-10-30
forum: Recurring Discussions
---

### Post by Eliot Rosewater on 2009-10-30
I would just like to preface my comments by saying Im an avid fan of Ubuntu and up to yesterday have recommended it to many people. However the upgrade to 9.10 has reminded me of the huge leap that people have to take to use it, and the problems with getting Ubuntu working.

--- 

I had previously used ext3 so I decided to do a full reinstall to get the full benefit of ext4 on Karmic Koala. I was exited about the new Ubuntu and downloaded it as soon as it was available and burnt the ISO. After installing it, and rebooting, I get this message

"Grub 1.5 ... Error 15"

and no list of OS's, so I cant use even XP. I did a bit of searching on the net through the live cd. Most of the solutions were for grub1, so even though I did a few things I got nowhere. So I reinstalled 9.10. Same problem.

Given that my MBR needed fixing, that I love Ubuntu, and that Im persistent, I decided to install 9.04, and then upgrade. 9.04 installed and the same old message came up "Grub 1.5 ... Error 15."

This is the point the standard user unplugs their machines, sends it to a technician and curses the day they ever tried to use Ubuntu.

But Im not that stupid, so I booted the 9.04 live cd and reinstalled Grub. Then at last I ot into 9.04 and started the upgrade. Halfway through the upgrade I got a dialog concerning grubs menu.lst. I assume the default setting - keep current version - will be ok given, well, that its the default! A half an hour later and to my joy Im finally using 9.10.

Until I played some music. Then I discover the sounds broken. So I did a load of Google searching and find that the issue is the kernel. You see grub was loading the old kernel because the upgrade kept the old menu.lst. So I manually edited the menu.lst to point to the new kernel and now my sounds working.

The same cant be said for Ubuntu One, which doesn't work at all.

---

There is a moral to this story. Despite Ubuntu claiming to be "Linux for Human Beings" the fact remains that the only reason I got Ubuntu working on my PC was because Im persistent as hell and because Im some way computer minded. I know what grub does. I know how to edit its settings. I know what kernel means. The average user Ubuntu targets does *not*.

Firstly I dont know why the reinstall of Ubuntu 9.10 didn't work. If I wasnt persistent I would have given up.
Secondly keeping the old menu.lst is the default option. If a regular person was confronted with that dialog they would have done the exact same thing I did and kept the default option. But do you think the average user would be able to reinstall grub, and then edit it to point to the new kernel?

Look, theres plenty of distros there that focus on getting new and better features. So if I was Ubuntu I would concentrate on *usability*. At the moment its *not* usable. 95% of people who went through my experience would have given up. How could I in my right mind recommend Ubuntu to anyone given what Ive gone through in the last 24 hours? 

Forget about the 10 second start. Theres much more important issues to be addressed.

Just my two (euro) cents.

---

### Post by AlanR8 on 2009-10-30
It always amazes me the different experiences people have with Ubuntu. I feel your pain!!!!

I've been using U/Kubuntu for almost three years now and have been fortunate never to have an installation issue. I've installed it on a Dell Dimension, EeePC, Sony Vaio laptop, a HP Pavilion laptop, (last week),two home made machines of varying vintages oh and an Acer netbook. Those are the ones I remember and I've always done full fresh installs and just generally play around!

The Dell is the wife's and I tried her out on Kubuntu after a major doze infection. Unfortunately it happened at a busy time for her and she didn't have the time to learn a new system so XP had to be put back on.

Now, there's a story. It took 8 yes 8 hours to get the machine up and running! None of the drivers installed by default, including the network so I had to use another machine to find them and install from a freshly burnt CD and all was well eventually.

Until about a week later she asked why she couldn't play avi mp3 files etc. Bu**er me I then had to hunt down codecs!

I accept that Linux is not quite ready for Joe Public just yet but do you know something, I think its getting close. What happened on that XP install makes me wonder if XP was EVER ready for Joe Public or did he just swallow the red pill because he was told to.......

---

### Post by leandromartinez98 on 2009-10-30
Windows is not ready for mainstream either. My friend installed win7 the other day and he was unable to make his printer work, and some other ridiculous issue, I don't remember what exactly. He went back to his XP hard drive image then. Fortunatelly he is quite computer skilled so that he knows how to to a hard drive image and rewrite it afterwards.

---

### Post by PorkyPie on 2009-10-30
> **Eliot Rosewater said:**
> I would just like to preface my comments by saying Im an avid fan of Ubuntu and up to yesterday have recommended it to many people. However the upgrade to 9.10 has reminded me of the huge leap that people have to take to use it, and the problems with getting Ubuntu working.

--- 

I had previously used ext3 so I decided to do a full reinstall to get the full benefit of ext4 on Karmic Koala. I was exited about the new Ubuntu and downloaded it as soon as it was available and burnt the ISO. After installing it, and rebooting, I get this message

"Grub 1.5 ... Error 15"

and no list of OS's, so I cant use even XP. I did a bit of searching on the net through the live cd. Most of the solutions were for grub1, so even though I did a few things I got nowhere. So I reinstalled 9.10. Same problem.

Given that my MBR needed fixing, that I love Ubuntu, and that Im persistent, I decided to install 9.04, and then upgrade. 9.04 installed and the same old message came up "Grub 1.5 ... Error 15."

This is the point the standard user unplugs their machines, sends it to a technician and curses the day they ever tried to use Ubuntu.

But Im not that stupid, so I booted the 9.04 live cd and reinstalled Grub. Then at last I ot into 9.04 and started the upgrade. Halfway through the upgrade I got a dialog concerning grubs menu.lst. I assume the default setting - keep current version - will be ok given, well, that its the default! A half an hour later and to my joy Im finally using 9.10.

Until I played some music. Then I discover the sounds broken. So I did a load of Google searching and find that the issue is the kernel. You see grub was loading the old kernel because the upgrade kept the old menu.lst. So I manually edited the menu.lst to point to the new kernel and now my sounds working.

The same cant be said for Ubuntu One, which doesn't work at all.

---

There is a moral to this story. Despite Ubuntu claiming to be "Linux for Human Beings" the fact remains that the only reason I got Ubuntu working on my PC was because Im persistent as hell and because Im some way computer minded. I know what grub does. I know how to edit its settings. I know what kernel means. The average user Ubuntu targets does *not*.

Firstly I dont know why the reinstall of Ubuntu 9.10 didn't work. If I wasnt persistent I would have given up.
Secondly keeping the old menu.lst is the default option. If a regular person was confronted with that dialog they would have done the exact same thing I did and kept the default option. But do you think the average user would be able to reinstall grub, and then edit it to point to the new kernel?

Look, theres plenty of distros there that focus on getting new and better features. So if I was Ubuntu I would concentrate on *usability*. At the moment its *not* usable. 95% of people who went through my experience would have given up. How could I in my right mind recommend Ubuntu to anyone given what Ive gone through in the last 24 hours? 

Forget about the 10 second start. Theres much more important issues to be addressed.

Just my two (euro) cents.

:(

The ubuntu developers aren't focussing only on the ten second start, they look at what the public say, and use this information to improve ubuntu. And, if someone files a bug, the developers look at the problem, and will have it fixed for the next release.

I have to totally disagree on the "*usabillity*" bit which you wrote. Ubuntu is usable, you just have to get used to the way ubuntu runs things. And... it doesn't take that much effort to get used to it.

And, if you're comparing ubuntu to Windows, obviously, ubuntu isn't going to be as good as Windows in some ways.

---

### Post by Shibblet on 2009-10-30
First off, I can't get a single version of Ubuntu to install on my MSI Wind U100.  None of the netbook distributions, nor the regular i386 ISO's.  

I tried these from a jump drive, and then burned the ISO's to CD, and tried booting the MSI Wind from the external DVD drive.  All of the ways I have tried to install, end up hanging with a black screen in the installation.

Secondly, I downloaded Kubuntu Karmic for my Desktop.  The installation went off without a hitch, but it took a LONG time, as I am sitting there waiting for it to download language packs.

I get my desktop, and I can't get Handbrake to work.  So I tried the Handbrake snapshot, which has a dependency that isn't available in the repositories anymore.  I know this is not an OS specific problem, but it makes it so I have to go back to 9.04, because I utilize the heck out of handbrake.

My main gripe is with my MSI Wind.  I was waiting anxiously for the Intel Graphics bug to be fixed, so that I would have great performance on my MSI Wind, and now I can't even install the OS.

Canonical, please take the time necessary before you release 10.04.  If you cannot work out the bugs, it would be better to take an extra 3 to 6 months testing (in beta even) to get the problems worked out.  Nothing is more disappointing than a release that feels rushed.  And seeing as how 10.04 is your next long-term release, make sure its a good release.

---

### Post by HappyFeet on 2009-10-30
> **Eliot Rosewater said:**
> However the upgrade to 9.10 has reminded me of the huge leap that people have to take to use it

You upgraded. What did you expect? Upgrading any OS is asking for problems. People just don't get it. I install OS's for a living, I know. Apparently you don't.

---

### Post by HappyFeet on 2009-10-30
> **Shibblet said:**
> First off, I can't get a single version of Ubuntu to install on my MSI Wind U100.  None of the netbook distributions, nor the regular i386 ISO's.  


What does that tell you? It tells me your hardware is not linux compatible. If it was, you would not have any problems. What part of that don't you understand? Oh, I forgot, Ubuntu is supposed to work flawlessly on every computer in the world. :rolleyes:

---

### Post by overdrank on 2009-10-30
Moved to  Recurring Discussions

---

### Post by Tamlynmac on 2009-10-30
> HappyFeet
You upgraded. What did you expect? Upgrading any OS is asking for problems. People just don't get it. I install OS's for a living, I know. Apparently you don't.

Every new release receives the same repetitious "Not Ready For Prime Time" threads. You really shouldn't permit it to annoy you so much HappyFeet. For example look at the OP's post count.

I seriously doubt your feedback will inspire them to change their agenda. I learned to read them and laugh, knowing the next similar thread will be even more humorous. Laughter reduces stress and I've found it to be helpful when viewing these types of threads.

Just my $0.02

---

### Post by fenian on 2009-10-30
> **Shibblet said:**
> 
...and I can't get Handbrake to work.  So I tried the Handbrake snapshot, which has a dependency that isn't available in the repositories anymore.  I know this is not an OS specific problem, but it makes it so I have to go back to 9.04, because I utilize the heck out of handbrake.



Here is how to get Handbrake working by installing the svn.

1-Install the dependencies,open a terminal and enter...

> sudo apt-get install subversion yasm build-essential autoconf libtool zlib1g-dev libbz2-dev intltool (gui) libglib2.0-dev libdbus-glib-1-dev libgtk2.0-dev libhal-dev libhal-storage-dev libwebkit-dev libnotify-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev


2-Download the source,in the termial enter...

> svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake-source

3-Navigate to the Handbrake directory,in the terminal enter...

> cd ./HandBrake-source

4-Configure Handbrake (this will take a while),in the terminal enter...

> ./configure --launch

5-Navigate to the build directory,in the terminal enter...

> cd ./build

6-Make and install .deb package,in the terminal enter...

> sudo checkinstall


You will be able to remove the package using Synaptic.

---

### Post by germclown on 2009-10-30
> Oh, I forgot, Ubuntu is supposed to work flawlessly on every computer in the world.

It's a problem people often have when switching to a Mac as well. Long time Windows-only people have got themselves used to near-universal hardware compatibility. They don't care who's responsible, they just honestly find it baffling when they plug something in and it doesn't work. And they'll probably blame whatever the biggest recent change was (which is a new Ubuntu OS in this case).

There is a **huge** number of people that didn't start using computers until WinXP was over its early awkwardness. And that beast was around for so long it worked with whatever gold or crap you could get your hands on. Leaving that environment will cause problems for people. Even Win7 is having trouble competing with it.

I am surprised AlanR8 had so many software issues with XP, though. I never added a single codec until I downloaded a movie in some wierdo Russian homemade format. I found some mega codec pack and never had a problem with anything else. And my OEM disk (with proper SATA drivers) always installed smoothly.

---

### Post by SunnyRabbiera on 2009-10-30
Your issue can only be self blamed though, for me I was never able to get EXT4 to co operate with GRUB2.
Thats my main reason for sticking with EXT3, until GRUB2 becomes a little more stable I rather use EXT3.
EXT4 will probably be much better for 10.04, by then we would have time to see GRUB2 stabilize a little more.

---

### Post by John Bean on 2009-10-30
> **Shibblet said:**
> First off, I can't get a single version of Ubuntu to install on my MSI Wind U100.  None of the netbook distributions, nor the regular i386 ISO's.  
I have an Advent 4211 (rebranded Wind U100) and it works perfectly with any version of 9.04 and anything else I've tried on it (Mint, DSL, ...) and currently runs 9.04 Remix. Perhaps yours has a BIOS issue? There have been a lot of BIOS issues in the early days of the Wind. Mine has the most recent, downloaded a few weeks ago.

---

### Post by Shibblet on 2009-10-30
> **HappyFeet said:**
> What does that tell you? It tells me your hardware is not linux compatible. If it was, you would not have any problems. What part of that don't you understand? Oh, I forgot, Ubuntu is supposed to work flawlessly on every computer in the world. :rolleyes:

Roll your eyes all you want, but the answer is "Yes."  Yes it is supposed to work flawlessly on every computer.  Isn't that the idea?  You can't make a full released OS that only works on "some" computers.  What kind of plan is that?  "Ubuntu.  We strive to be mediocre?"  Come on, they aren't going that way.

Jaunty ran just fine, minus the intel graphics problem...  And why would Ubuntu make a "Netbook Remix" if it didn't run on my very popular Netbook?

I'm not a Windows lover, but I can tell you that Windows XP and Vista will install on my MSI Wind, and the word I would use is flawlessly, because the OS will install.  Hardware and drivers are secondary.  

I haven't run Windows 7 yet, but I can tell you beyond a shadow of a doubt that I would be able to install it without a problem.

This is the first time that I have had every effort to install Ubuntu fail miserably, time and time again.  I'm very, very disappointed in the Karmic Release.

---

### Post by Screwdriver0815 on 2009-10-30
another "Ubuntu is not ready for mainstream" thread... 

every 6 months it is the same: short after release all the whining people show up, complain "how Ubuntu fails and how it is not usable and how much windows is better"... after some weeks you just see "ah the new release its great"...

I am sometimes in the mood to open an idea at brainstorm: "people who whine that Ubuntu is not ready for the desktop and mention how much better Windows is at the same time should be banned from using Ubuntu"

seriously, what makes me angry is that when Windows comes up in a new version, which is full of bugs, nearly everybody "understands" that they can not test every possible hardware setup.
When a new version of Ubuntu or any other Linux-distro shows up, this "understanding" is not there. IT HAS TO WORK - even when the same conditions = the developers can not test every possible combination of hardware and therefore bugs and problems are possible and will be sorted out, depending on the feedback by the users apply. No, because its Linux - it has to work. If Windows doesn't work, its not the fault of anyone. No. But when there are problems in a Linux-distro, everything sucks, and everything still has a long way to go... 

I say: Ubuntu is ready for prime time. 
Just wait 1 or 2 weeks after the release. If you don't then you are not able to learn from previous releases --> your fault.

---

### Post by Shibblet on 2009-10-30
> **Screwdriver0815 said:**
> every 6 months it is the same: short after release all the whining people show up, complain "how Ubuntu fails and how it is not usable and how much windows is better"... after some weeks you just see "ah the new release its great"...

I like the new release for my desktop.  It's beautiful, and runs great.  The installer is a bit slow (Downloading language packs).

> **Screwdriver0815 said:**
> I am sometimes in the mood to open an idea at brainstorm: "people who whine that Ubuntu is not ready for the desktop and mention how much better Windows is at the same time should be banned from using Ubuntu"

I never said Windows was better, I just said that Windows would install.

> **Screwdriver0815 said:**
> seriously, what makes me angry is that when Windows comes up in a new version, which is full of bugs, nearly everybody "understands" that they can not test every possible hardware setup.

And neither can Ubuntu.

> **Screwdriver0815 said:**
> When a new version of Ubuntu or any other Linux-distro shows up, this "understanding" is not there. IT HAS TO WORK - even when the same conditions = the developers can not test every possible combination of hardware and therefore bugs and problems are possible and will be sorted out, depending on the feedback by the users apply. No, because its Linux - it has to work. If Windows doesn't work, its not the fault of anyone. No. But when there are problems in a Linux-distro, everything sucks, and everything still has a long way to go... 

Nothing works perfectly out of the box, is what you are saying.  And that is true.  But what if you can't even open the box?

> **Screwdriver0815 said:**
> I say: Ubuntu is ready for prime time. 
Just wait 1 or 2 weeks after the release. If you don't then you are not able to learn from previous releases --> your fault.

If a person who bought a copy of Windows 7 from the store, took it home, and it wouldn't install on their computer, it's going to be returned faster than my grandpa can drink a pint.

So, when I spend the better portion of a night trying all sorts of variations of installing Ubuntu i386, NBR, Kubuntu i386, Netbook, etc.  And none of which will install.  I say there is something wrong with the release. 

Problem number 2.  Canonical isn't going to fix the installer and release another ISO, they are just going to patch current installations.  So where does that leave me?  No install, and no way to patch the problem.

---

### Post by slumbergod on 2009-10-30
I think you actually might successfully argue that karmic is not ready for everyone...certainly anyone coming straight from windows might come unstuck if something goes wrong during the installation. For anyone else with a year or two of familiarity with linux I think most problems can be overcome.

That said, I wish they'd slow the release schedule down. Jaunty was a dog. Karmic is better for me but I've found a few naggy issues.

The big lesson is perhaps this: if proprietary OS producers (guess who) hadn't been so nasty to hardware developers then perhaps hardware would be better supported rather than all locked up. Sometimes I am amazed linux is as good as it is given the pathetic support by the manufactures.

---

### Post by SunnyRabbiera on 2009-10-30
> **Shibblet said:**
> Canonical isn't going to fix the installer and release another ISO, they are just going to patch current installations.  So where does that leave me?  No install, and no way to patch the problem.

Well you could try another distro, after all ubuntu is not the only one out there.
For me Karmic is near flawless but I am looking out for other distros too to see what I like, both Mandriva 2009.2 and openSUSE 11.2 have great promise on my machine.

---

### Post by Screwdriver0815 on 2009-10-30
> **Shibblet said:**
> 
Nothing works perfectly out of the box, is what you are saying.  And that is true.  But what if you can't even open the box?


then you can not use it. Look there is a very nice invention, called "Live-cd" - it allows to check if the machine runs with the system... hmmm... I read this somewhere before... maybe in zillions of other threads? 

> **Shibblet said:**
> 
If a person who bought a copy of Windows 7 from the store, took it home, and it wouldn't install on their computer, it's going to be returned faster than my grandpa can drink a pint.


thats what you say now. The reality is different: people who have bought Windows, do not want to admit that they have thrown out a lot of money for nothing. So no complaining, just abject waiting and praying is done. 
Maybe Ubuntu should cost some 100 bucks, then the complaining would stop or be heavily reduced.

> **Shibblet said:**
> 
So, when I spend the better portion of a night trying all sorts of variations of installing Ubuntu i386, NBR, Kubuntu i386, Netbook, etc.  And none of which will install.  I say there is something wrong with the release. 

Problem number 2.  Canonical isn't going to fix the installer and release another ISO, they are just going to patch current installations.  So where does that leave me?  No install, and no way to patch the problem.

I think, when you report a bug on this, the installer will be fixed anyway. At least it is possible, technically. ;)
But the developers need to know that. They do not get information from a complaining thread, they need a bugreport.

Edit: but I was not just answering your post - it should be a general statement towards all "Linux is not ready for anything" people

---

### Post by misfitpierce on 2009-10-30
I recommended a fresh install and not upgrade to 9.10 for reason it uses new GRUB system and new EXT4 filesystem to take advantage of new speeds on the new filesystem if not already on custom EXT4 setup from 9.04. I think its fine for mainstream since it is already in bestbuy on CD and on netbooks. Granted ppl will have diff experiences and problems but it does quite well considering how much hardware it supports built into the kernel which windows cant do as you gotta hunt down all your drivers and that was a mess with Vista at the start from what I read. I hope you get it all working and sorted but 9.10 uses a bunch of new features to be tested before the next LTS so I would expect some bugs etc at the beginning of release.

---

### Post by AlanR8 on 2009-10-30
Just scrolled through the thread.....

There's a couple of points I think.

First, how much did you (all of you) pay for Karmic?

Second, if you'd paid £100 ish for 7 and there were hardware issues, how bad would you feel?

Third, you can fix Karmic by listening to the peeps in this forum

Fourth, would that be the same in a Gates environment?

---

### Post by Shibblet on 2009-10-30
> **AlanR8 said:**
> First, how much did you (all of you) pay for Karmic?

I think the price is irrelevant.  If someone said "Free Beer!  But ***YOU*** can't have any."  You'd be a little put-off.

> **AlanR8 said:**
> Second, if you'd paid £100 ish for 7 and there were hardware issues, how bad would you feel?

Hardware issues are to be expected with any new OS.  You at least need the basics to work until the hardware issues are solved.  Give me my beer in a paper cup, until the glasses are available.  

> **AlanR8 said:**
> Third, you can fix Karmic by listening to the peeps in this forum

No install, no fixes.  Which means my beer is being served without any container at all.  So it's all over the floor and I can't drink it.

> **AlanR8 said:**
> Fourth, would that be the same in a Gates environment?

I don't quite understand what that meant.  But I think Bill's beer is served in a crystalline chalice.

---

### Post by Screwdriver0815 on 2009-10-30
@shibblet: Jaunty worked on your computer, did I get this right? So what's the problem, just stick with Jaunty, file a bugreport, wait and hopefully in the future you can install the newer version (if it is Karmic or Lucid Lynx...)

I keep the finger crossed that it will work for you too!

but saying that Bills beer is served in a better glass (or whatever "served in a crystalline chalice" means) is not the right and constructive way.

---

### Post by Shibblet on 2009-10-30
> **Screwdriver0815 said:**
> @shibblet: Jaunty worked on your computer, did I get this right? So what's the problem, just stick with Jaunty, file a bugreport, wait and hopefully in the future you can install the newer version (if it is Karmic or Lucid Lynx...)

Which is the plan.  But I'm upset that Karmic didn't work.

> **Screwdriver0815 said:**
> I keep the finger crossed that it will work for you too!
Thanks!

> **Screwdriver0815 said:**
> but saying that Bills beer is served in a better glass (or whatever "served in a crystalline chalice" means) is not the right and constructive way.

No, that's just a money joke.

Bill Gates has so much money... (How much does he have?)  He has so much money, that his beer is served in a crystalline chalice!

Boooooo! (from the crowd)

---

### Post by julianb on 2009-10-30
> I accept that Linux is not quite ready for Joe Public just yet but do you know something, I think its getting close. What happened on that XP install makes me wonder if XP was EVER ready for Joe Public or did he just swallow the red pill because he was told to.......

My experience with WinXP is that it Just Works. Sure, things break sometimes. Like Ubuntu, most of the time it works and sometimes things just go terribly. If you use a slower computer, though, I really recommend you avoid windows.

---

### Post by Tamlynmac on 2009-10-31
I always amazed when someone complains about a free anything. If one doesn't like it, don't use. No one charged them for trying it and they don't need to stand in line waiting for a refund.

Wasting time arguing and complaining about a free anything, implies one's not concerned about time as a resource. So the argument regarding the cost of Ubuntu based on time invested - isn't viable. Thus, one must conclude that the entitlement motive or some other agenda plays a role.

No one mandates that anyone install or upgrade Ubuntu. When choosing to do so, one must accept the responsibility. If they are dissatisfied, seek an alternative. Seems logical and simple, without wasting time.

Just my $0.02

---

### Post by JT9161 on 2009-10-31
The final release has been public all of a day, you can't predict or reproduce all bugs, something that can become very obvious when software goes public and gets into the wild. Software bugs exist, and will for as long as I can see.

---

### Post by Shibblet on 2009-10-31
> **Tamlynmac said:**
> I always amazed when someone complains about a free anything. If one doesn't like it, don't use. No one charged them for trying it and they don't need to stand in line waiting for a refund.

Let's say you paid for a magic show (Windows), and for the price of those tickets, you expect David Copperfield.  But you get a second rate magician (Windows) who at least tries to please the crowd.

Then you get invited to a free magic show (Ubuntu), and puts on a great show up until the final act.  Then the guy says "Watch me make this rabbit disappear!"  Then, instead of making it vanish into thin air, he just rips it apart in front of your face getting rabbit guts all over the stage.  "Ta-Dah!"  And you're sickened by this display, but you can't complain!  It's free, right?

> **Tamlynmac said:**
> No one mandates that anyone install or upgrade Ubuntu. When choosing to do so, one must accept the responsibility. If they are dissatisfied, seek an alternative. Seems logical and simple, without wasting time.

Just my $0.02

And for the most part, you're correct.  Ubuntu is free, Windows is not.  People will always complain about the differences.  But keep in mind no matter how free it is, you'd rather pay to see a magician than go to a free show.

---

### Post by cariboo on 2009-10-31
@Shibblet

I would suggest you reinstall 9.04, fully update it, and before adding any programs upgrade to 9.10. This will almost guarantee a working  Karmic installation

---

### Post by Shibblet on 2009-10-31
> **cariboo907 said:**
> @Shibblet

I would suggest you reinstall 9.04, fully update it, and before adding any programs upgrade to 9.10. This will almost guarantee a working  Karmic installation

That's the plan.  But I wanted to do a fresh install.

---

### Post by quinnten83 on 2009-10-31
i Would suggest wiping the disk clean with gparted b4 doing a complete install. ithink the problems you have are grub1 to grub2 transitional pains. Changing from ext4 to three aren't helping much either.
Image your PC using clonezilla, backup, backup, backup and then give it a go. oh and please remember to file a bug. I guarantee that someone else has also had this problem and this helps them to add themselves to the bugtracking, which will more easily get the attention of the developers, developers, developers....

---

### Post by AllRadioisDead on 2009-10-31
> **leandromartinez98 said:**
> Windows is not ready for mainstream either. My friend installed win7 the other day and he was unable to make his printer work, and some other ridiculous issue, I don't remember what exactly. He went back to his XP hard drive image then. Fortunatelly he is quite computer skilled so that he knows how to to a hard drive image and rewrite it afterwards.
Windows isn't ready for the mainstream? Windows IS the mainstream.

---

### Post by tsali on 2009-10-31
I've gotten used to hosed up grub menus ever since I started using Ubuntu back with 7.10

The installer has never...even once...correctly identified the hard disk with my Windows install. It always calls it hd0,0.

EVERY SINGLE TIME I have to boot to grub command or use the live CD to edit menu.lst to change it to hd1,0

I've learned more about menu.lst than anyone should EVER have to.

It took a long time to get Jaunty semi-right on my desktop. I don't see that Karmic offers much over Jaunty. I'm in no hurry to fool with it.

---

### Post by faical117 on 2009-10-31
> **tamlynmac said:**
> i always amazed when someone complains about a free anything. If one doesn't like it, don't use. No one charged them for trying it and they don't need to stand in line waiting for a refund.

Wasting time arguing and complaining about a free anything, implies one's not concerned about time as a resource. So the argument regarding the cost of ubuntu based on time invested - isn't viable. Thus, one must conclude that the entitlement motive or some other agenda plays a role.

No one mandates that anyone install or upgrade ubuntu. When choosing to do so, one must accept the responsibility. If they are dissatisfied, seek an alternative. Seems logical and simple, without wasting time.


=d>

---

### Post by kenweill on 2009-10-31
> **ihermit said:**
> Windows isn't ready for the mainstream? Windows IS the mainstream.

Windows 7 sux. It's the worst i've ever tried. Even worst than vista.

Network interface card and sound card not working on windows 7 ultimate final. Not detected. No manufacturer drivers.

Well, that's my experience this morning. Trying to install Windows 7 ultimate on my desktop. I just want to try if it works out of the box. Well, it doesn't. 

XP is better in detecting my network interface. Windows 7 sux this time.

Everything works out of the box with Ubuntu, and openSUSE.

---

### Post by Eliot Rosewater on 2009-10-31
To be honest, Im disappointed a more respectful discussion hasnt developed here. Instead everyone is jumping on my for criticizing Ubuntu. The only way forward is to be receptive to criticism and a lot have people here have shown an inability to accept a story which does not fit neatly into their pro-Ubuntu bias.

> **HappyFeet said:**
> You upgraded. What did you expect? Upgrading any OS is asking for problems.

Obviously. However Ubuntu is marketed as an easy to use OS. My point is thats it very hard to install for some, and impossible for some non-technical users.

> **Tamlynmac said:**
> You really shouldn't permit it to annoy you so much HappyFeet. For example look at the OP's post count.

Well I had to laugh at this. Your discounting my opinion, and my story, because I only joined these forums yesterday? I like the way you brushed it off without actually considering what I said. You see I didnt come here and say "Windows is great because..." and offer a list of opinions. I laid out a factual story of my experience and made the necessary conclusions.

> **SunnyRabbiera said:**
> Your issue can only be self blamed though, for me I was never able to get EXT4 to co operate with GRUB2.

The issue is that ext4 and grub2 are both the defaults, so an unsuspecting user will not know better. Do you see my point? Im not whinging about the trouble I had, Im stating how hard it would have been for someone unable to open a terminal, reinstall gruband then edit the boot options to point to the new kernel.


I can understand people complaining about how users of new releases complain about bugs. But if it is a new full release, surely they should wait until its fully ready? Isnt that what alpahs and betas and RCs are for?

A lot of people here are discounting my criticism by saying, well Windows does the same. Why does everything come back to Windows?

---

### Post by SuperSonic4 on 2009-10-31
> **Shibblet said:**
> Then you get invited to a free magic show (Ubuntu), and puts on a great show up until the final act.  Then the guy says "Watch me make this rabbit disappear!"  Then, instead of making it vanish into thin air, he just rips it apart in front of your face getting rabbit guts all over the stage.  "Ta-Dah!"  And you're sickened by this display, but you can't complain!  It's free, right?

That's OK, rabbits are pests - they eat crops and the skin makes warm gloves. Might not make a bad meal either :p

If you're having trouble with hardware detection then try another distro. As I'm sure you're aware just because something is popular doesn't mean it works for everyone

---

### Post by HNS-I on 2009-10-31
Your first post is this qed. If you want a mature discussion why don't you react to the perfectly fine comments that have been posted in your thread? You hook into the few negative comments. 

I would give you, some points you make are or may be valid. On a forum it will _never_ work however. I think I have a rational and reasonable opinion on ubuntu but I will probably never explicate it here or any other forum. 
Cheers
HNS

---

### Post by lancest on 2009-10-31
> **Shibblet said:**
> 
I'm not a Windows lover, but I can tell you that Windows XP and Vista will install on my MSI Wind, and the word I would use is flawlessly, because the OS will install.  Hardware and drivers are secondary.
.

Use the alternate 9.10 cd for installation. It worked on my MSI Wind U90. I don't expect Linux to be flawless to install but it will surely run alot better than XP or 7.  Windows = performance robbing anti virus, firewall and software install degradation

---

### Post by Eliot Rosewater on 2009-10-31
> **HNS-I said:**
> Your first post is this qed. If you want a mature discussion why don't you react to the perfectly fine comments that have been posted in your thread?


My point was that Ubuntu was not ready for the mainstream because on some computers one cant install it on some computers without some technical knowledge. The responses were like "Its ok because Windows is the same" "Its your fault for using the defaults Ubuntu installed (ext4+grub2)" "Your opinion is worthless because you only joined [www.ubuntuforums.org](www.ubuntuforums.org) yesterday" "Its your fault for downloading the new version of Ubuntu."

I think peoples attitude here is to live in a cocoon. Which is perfectly fine. Until ye start promoting Ubuntu as Linux for Human Beings, chastising the stupid Windows users. Its kind of hypocritical that the Ubuntu community half lives off anti-Windows sentiment, and yet any feedback of Ubuntu that isnt positive is looked down upon.

---

### Post by lancest on 2009-10-31
> **Eliot Rosewater said:**
> My point was that Ubuntu was not ready for the mainstream because on some computers one cant install it on some computers without some technical knowledge. 

Windows requires technical knowledge to install also. Especially when it necessary to hunt around for half a dozen drivers needed to get it going. And if you install them in the wrong order it's trouble. Ubuntu is often way easier to get going- especially on a desktop pc.

---

### Post by Tamlynmac on 2009-10-31
> Shibblet
And for the most part, you're correct. Ubuntu is free, Windows is not. People will always complain about the differences. But keep in mind no matter how free it is, you'd rather pay to see a magician than go to a free show.

You have some very odd analogies. Putting that aside, you also make assumptions. For example, you apply your logic to others.

You state that I'd rather pay for a magician than go to a free show. I hate to tell you this buts that's wrong. I would never pay to watch a magician - not my thing. If it were free, I "might" watch, if I had the time. It would help if you just spoke for yourself and not included others in your comments or analogies. I cannot speak for anyone but myself and my opinion is fundamentally just that.

As I said if it doesn't work for you, quit wasting time complaining about it and use something else. Find an alternative that meets your expectations and let it go. As even you admit, "it is free" and no one forced you to install or upgrade it.

Good Luck

---

### Post by Screwdriver0815 on 2009-10-31
> **Eliot Rosewater said:**
> To be honest, Im disappointed a more respectful discussion hasnt developed here. Instead everyone is jumping on my for criticizing Ubuntu. The only way forward is to be receptive to criticism and a lot have people here have shown an inability to accept a story which does not fit neatly into their pro-Ubuntu bias.

the main thing is:

if you wanted to do anything for Ubuntu, going the way forward, you would not post your critisism in a forum. You would file bug reports on technical issues. If you have technical issues.
If you do not have technical issues and just don't know how to do certain things or whatever: just read documentation and/or ask in the forum.
"critisising" in a forum is senseless.

As you obviously feel the only way to be constructive is to whine in a forum, I feel like telling you: Fail! 

if you feel the need to critisise, to post opinions, to make proposals and so on, you are free and invited to contribute to the community.
By (as I said before) filing Bugreports, reading and improving documentation, posting proposals on [www.brainstorm.ubuntu.com](www.brainstorm.ubuntu.com) and so on.
Though my feeling is you just want to whine, to troll and to get rid of your frustration.

sorry that my words maybe sound harsh but I can not ignore this and I can not stand this anymore.

In these forums everyday loads of people show up and do "constructive critics", thinking their opinion is the only one valid, thinking this is the right place for their "constructive critics" and thinking that it will have any effect.

- no it is not constructive

- no this forums is not the right place

- no it does not have any effect

/rant

---

### Post by Eliot Rosewater on 2009-10-31
I dont know why this thread is in this forum, I posted it the testimonials forum because its a testimonial but the mod moved it here for some reason??

Because its here your completely misunderstanding what Im saying. It was a testimonial about how hard Ubuntu can be to install and how it can be unsuitable for non-techie users. Is that what not the testimonials forum is for?

---

### Post by Shibblet on 2009-10-31
> **Tamlynmac said:**
> You have some very odd analogies. Putting that aside, you also make assumptions. For example, you apply your logic to others.

I have odd (I call them fun) analogies. Logic, fortunately, applies universally.  My truth might not be your truth, and that's fine.

> **Tamlynmac said:**
> You state that I'd rather pay for a magician than go to a free show. I hate to tell you this buts that's wrong. I would never pay to watch a magician - not my thing. If it were free, I "might" watch, if I had the time. It would help if you just spoke for yourself and not included others in your comments or analogies. I cannot speak for anyone but myself and my opinion is fundamentally just that.

It's not about a magic show, it could be any analogy.  Getting or buying a car; paying for a movie, or getting in for free; etc.

I think you might have missed the point of the analogy.  The Windows portion of it was a "decent" magic show that you paid for.

The Ubuntu portion of it was the free magic show that was great up until the end.  The end, or tearing the rabbit apart, being the one little aspect (could by any aspect) of Ubuntu that everyone is having a problem with.  And, like Ubuntu, it was a free show, but that one part might be enough to ruin the magic show for you the same way not being able to run games might ruin Ubuntu for you.  Some people may like the ripping up of the rabbit, some may not.

> **Tamlynmac said:**
> As I said if it doesn't work for you, quit wasting time complaining about it and use something else. Find an alternative that meets your expectations and let it go. As even you admit, "it is free" and no one forced you to install or upgrade it.

Have you ever heard the phrase "If you give a mouse a cookie...  He's going to come back for more."  What that means is when you give something away, people feel entitled.  When you feel entitled, you complain when something doesn't work the way you want it to.

See, you're under the impression that I was complaining about Ubuntu, and I'm only complaining about the installation on my Netbook.  It crashes, and that sucks.  And you can say that I make assumptions, but I know how people work when it comes to this kind of thing.  I see it on a day to day basis.

I work in an electronics store.  This is kind of strange, but the happiest customers are the ones that pay full price.  The people who get deals, always have problems.  And the best part, we never have more issues with a customer, than with a "cost customer".

You would imagine that the happiest customer is the one who just bought the product for WAY under what its retail price.  But they are the ones that complain the most.

So, my point is, cost is irrelevant.  You can't just look a person in the face and say, "Oh well, I guess you got what you paid for."  That's just rude.  You have to listen to the situation, and try to help with what you can.  It's not an argument, don't pick it apart.

---

### Post by Screwdriver0815 on 2009-10-31
> **Eliot Rosewater said:**
> I dont know why this thread is in this forum, I posted it the testimonials forum because its a testimonial but the mod moved it here for some reason??

Because its here your completely misunderstanding what Im saying. It was a testimonial about how hard Ubuntu can be to install and how it can be unsuitable for non-techie users. Is that what not the testimonials forum is for?

the testimonal forum is for experiences. Your rant or however this should be called is no experience. Experiences are things you experience (huh... really) - facts, things which have a true substance.

Saying "Ubuntu is not ready for mainstream" is no experience, its an opinion.
And I repeat myself (not that I enjoy to do this - but anyway): if you really want to improve things in Ubuntu, contact the developers, engage yourself in the community... and so on. 
this makes more sense.

---

### Post by Screwdriver0815 on 2009-10-31
@shibblet: your analogy and the way to think like that is kind of funny but I would not say that Ubuntu is like tearing the rabbit apart.
Its like you see it. Maybe its because you wear sunglasses with a monitor in there where the teared rabbit is shown... and all the other people see the magic show which is better than the "decent Windows show". But why do you wear sunglasses? because someone has glued them onto your nose or it just was an accident: glue ran on the glasses and you put them on...

do you get what I mean: its not the general problem of all people using Ubuntu, its yours, your special problem

Of course this doesn't make it better for you but we, as the ones who see the real magic Ubuntu show are not guilty or responsible for that. 

and this 

> I work in an electronics store. This is kind of strange, but the happiest customers are the ones that pay full price. The people who get deals, always have problems. And the best part, we never have more issues with a customer, than with a "cost customer".
 
 You would imagine that the happiest customer is the one who just bought the product for WAY under what its retail price. But they are the ones that complain the most.

is the thing I mean: people who pay a lot do not complain. Because they then have to admit that they have paid too much. 

But anyway, you have a solution for your problem, as you said before. Imagine that you pay 300 bucks for the OS and the electronics shop guy tells you "sorry, no solution..." you then want to get back the money... and so on. Lots of trouble... and over here in the magic Ubuntu show you get your solution for free and you could just wait... and try it sometimes later.

---

### Post by Shibblet on 2009-10-31
> **Screwdriver0815 said:**
> @shibblet: your analogy and the way to think like that is kind of funny but I would not say that Ubuntu is like tearing the rabbit apart.

Again, I think you're missing the point.  Ubuntu is not the mutilated rabbit.  The "aspect" of Ubuntu you didn't think about being a problem is the mutilated rabbit.  Remember that the rest of the free show was great.

The paid for show (Windows) was just pretty good, the whole way through.  No surprises, nothing super special, just good ol' stage magic.

> **Screwdriver0815 said:**
> Its like you see it. Maybe its because you wear sunglasses with a monitor in there where the teared rabbit is shown... and all the other people see the magic show which is better than the "decent Windows show". But why do you wear sunglasses? because someone has glued them onto your nose or it just was an accident: glue ran on the glasses and you put them on...

I'm completely flummoxed by that statment.  Or in the immortal words of Kramer (Seinfeld) "You just blew my mind!"

I'm going to chalk that one up to the language barrier, or lost in translation.

> **Screwdriver0815 said:**
> do you get what I mean: its not the general problem of all people using Ubuntu, its yours, your special problem

I'm not talking specifics.  I am sure there are things about Ubuntu that you don't like also.  But those things keep most people from dropping Windows entirely.  iTunes users and Gamers to name a few.

> **Screwdriver0815 said:**
> Of course this doesn't make it better for you but we, as the ones who see the real magic Ubuntu show are not guilty or responsible for that.

See, you're still under the impression that I prefer Windows.  You're dead wrong.  The only time I boot Windows is to use iTunes or play games.  Other than that, Kubuntu is my happy place.

> **Screwdriver0815 said:**
> But anyway, you have a solution for your problem, as you said before. Imagine that you pay 300 bucks for the OS and the electronics shop guy tells you "sorry, no solution..." you then want to get back the money... and so on. Lots of trouble... and over here in the magic Ubuntu show you get your solution for free and you could just wait... and try it sometimes later.

And that is the best part about Ubuntu, free to use, free to learn, free assistance, the only payment is patience.

And here's the funny part.  Windows, you pay to use, and you still have to go through the same hoops as you do with Ubuntu in order to get assistance.  Tech support for other issues like internet connection, and proprietary software is readily availble.  OS tech support is the same as it is with Ubuntu.

---

### Post by Screwdriver0815 on 2009-10-31
ah yeah, sorry I mixed it up a bit. I thought you mean that Ubuntu is the rabbit, but you meant that Ubuntu is the show, right? ;) :D anyway, never mind... 

> **Shibblet said:**
> 
I'm not talking specifics.  I am sure there are things about Ubuntu that you don't like also.  But those things keep most people from dropping Windows entirely.  iTunes users and Gamers to name a few.


of course there are things I don't like about Ubuntu. But whats the point in complaining? Complaining in the right place with the right words... thats it. Complaining in a forum? Its not the right place. Thats what I mean.

> **Shibblet said:**
> 
See, you're still under the impression that I prefer Windows.  You're dead wrong.  The only time I boot Windows is to use iTunes or play games.  Other than that, Kubuntu is my happy place.


nope, I understood that you are one of the people who have the understanding that there can be drawbacks or whatever. The sentence "free beer... okay, give me a paper cup until glasses are available" showed this. And thats good in my eyes. 

> **Shibblet said:**
> 
And that is the best part about Ubuntu, free to use, free to learn, free assistance, the only payment is patience.

And here's the funny part.  Windows, you pay to use, and you still have to go through the same hoops as you do with Ubuntu in order to get assistance.  Tech support for other issues like internet connection, and proprietary software is readily availble.  OS tech support is the same as it is with Ubuntu.
thats what I meant

---

### Post by Shibblet on 2009-10-31
> **Screwdriver0815 said:**
> ah yeah, sorry I mixed it up a bit. I thought you mean that Ubuntu is the rabbit, but you meant that Ubuntu is the show, right? ;) :D anyway, never mind... 

Yeah, well, my analogies are a little odd.  ;)

> **Screwdriver0815 said:**
> of course there are things I don't like about Ubuntu. But whats the point in complaining? Complaining in the right place with the right words... thats it. Complaining in a forum? Its not the right place. Thats what I mean.

Have you ever seen "The History of the World: Part 2"  It's a Mel Brooks movie.  There is a part where a caveman made the first cave drawing, and then the first "critic" came over and peed on it.  So the comedy of the situation is that from the dawn of time, people will be rude with their critiques.  :)  I'm used to it.  

But you're right, complaining, without adding anything constructive is counter-productive.

> **Screwdriver0815 said:**
> nope, I understood that you are one of the people who have the understanding that there can be drawbacks or whatever. The sentence "free beer... okay, give me a paper cup until glasses are available" showed this. And thats good in my eyes. 

I'm paper-cupping Handbrake right now...

> **Screwdriver0815 said:**
> thats what I meant

And thus the German-American language barrier was bridged.  And a new family was formed via Ubuntu.  ;)  I'm so full of crap sometimes.

---

### Post by Tipped OuT on 2009-11-01
> **Screwdriver0815 said:**
> the main thing is:

if you wanted to do anything for Ubuntu, going the way forward, you would not post your critisism in a forum. You would file bug reports on technical issues. If you have technical issues.
If you do not have technical issues and just don't know how to do certain things or whatever: just read documentation and/or ask in the forum.
"critisising" in a forum is senseless.

As you obviously feel the only way to be constructive is to whine in a forum, I feel like telling you: Fail! 

if you feel the need to critisise, to post opinions, to make proposals and so on, you are free and invited to contribute to the community.
By (as I said before) filing Bugreports, reading and improving documentation, posting proposals on [www.brainstorm.ubuntu.com](www.brainstorm.ubuntu.com) and so on.
Though my feeling is you just want to whine, to troll and to get rid of your frustration.

sorry that my words maybe sound harsh but I can not ignore this and I can not stand this anymore.

In these forums everyday loads of people show up and do "constructive critics", thinking their opinion is the only one valid, thinking this is the right place for their "constructive critics" and thinking that it will have any effect.

- no it is not constructive

- no this forums is not the right place

- no it does not have any effect

/rant

Well said screwy. :)

---

### Post by PryGuy on 2009-11-01
Let's face it. EVERY OS is not ready for the mainstream when it is out. Upgrades make it stable.

---

### Post by PorkyPie on 2009-11-01
> **Screwdriver0815 said:**
> the main thing is:

if you wanted to do anything for Ubuntu, going the way forward, you would not post your critisism in a forum. You would file bug reports on technical issues. If you have technical issues.
If you do not have technical issues and just don't know how to do certain things or whatever: just read documentation and/or ask in the forum.
"critisising" in a forum is senseless.

As you obviously feel the only way to be constructive is to whine in a forum, I feel like telling you: Fail! 

if you feel the need to critisise, to post opinions, to make proposals and so on, you are free and invited to contribute to the community.
By (as I said before) filing Bugreports, reading and improving documentation, posting proposals on [www.brainstorm.ubuntu.com]("http://www.brainstorm.ubuntu.com") and so on.
Though my feeling is you just want to whine, to troll and to get rid of your frustration.

sorry that my words maybe sound harsh but I can not ignore this and I can not stand this anymore.

In these forums everyday loads of people show up and do "constructive critics", thinking their opinion is the only one valid, thinking this is the right place for their "constructive critics" and thinking that it will have any effect.

- no it is not constructive

- no this forums is not the right place

- no it does not have any effect

/rant

+1

I fully agree with you on that. :)

Sorry if I'm gonna sound a bit harsh here too, but, I'm going to say it as it is:

These support forums were created to get and give support to other people. Usually, if a person posts a thread, they will get a reply within five minutes. And 99.9% of the time, they get their problems fixed. This thread was a total waste of time, complaining. If you had posted a thread about your problem, we would have been able to help. But, instead, you wait... then, decide to post a thread whining about your problems. That's not very nice though, whining. The developers of Ubuntu will sometime come across this thread, and they'll think that they didn't fix all these problems before it was released. They would be wrong though. There's thousands of happy Ubuntu users around the world, and they've never had a problem with it for a long time, or never. Why? Well, there's two reasons:

[LIST=1]
[*]They didn't need support, their installation went perfectly, and they are using it with no problems.
[*]They got support, here, on the forums, or Linux Questions.org etc., or maybe they got paid support off of Canonical. Everything is fine.
[/LIST]
If you'd used number two, I'd guarantee that Ubuntu would be running smoothly on your system.

So... instead of whinging, you could have got support.

---

### Post by Shibblet on 2009-11-01
> **PorkyPie said:**
> These support forums were created to get and give support to other people. Usually, if a person posts a thread, they will get a reply within five minutes. And 99.9% of the time, they get their problems fixed. This thread was a total waste of time, complaining. If you had posted a thread about your problem, we would have been able to help. But, instead, you wait... then, decide to post a thread whining about your problems. That's not very nice though, whining. The developers of Ubuntu will sometime come across this thread, and they'll think that they didn't fix all these problems before it was released. They would be wrong though. There's thousands of happy Ubuntu users around the world, and they've never had a problem with it for a long time, or never. Why? Well, there's two reasons:

[LIST=1]
[*]They didn't need support, their installation went perfectly, and they are using it with no problems.
[*]They got support, here, on the forums, or Linux Questions.org etc., or maybe they got paid support off of Canonical. Everything is fine.
[/LIST]
If you'd used number two, I'd guarantee that Ubuntu would be running smoothly on your system.

So... instead of whinging, you could have got support.

This is a recurring discussion, and it comes up after every release.  Windows this... Ubuntu that.  But it is a recurring discussion.  

So if you think that this is a waste of time, don't read any of recurring discussions threads, because they've all been talked about before.

---

### Post by Nightstrike2009 on 2009-11-01
Ubuntu 9.10 (Krappy Koala) has the worst error yet, I have a 3g modem my only way of accessing net and it doesn't work on 9.10 although it did on ubuntu 9.04.

Great Ubuntu's mainstream pick-up is Netbooks and Laptops. 

Tell you what lets bugger the modem connector up as you only need the internet to do everything on ubuntu & how the hell are we supposed to download the fix when we have no net?

Not impressed at all should have delayed release until fixed, if i was new to Ubuntu this would have finished me off.

Ubuntu 9.10 STUPID & POINTLESS, UBUNTU'S VISTA :(

---

### Post by SouthOfHell on 2009-11-01
Duno eh, i've had no problems apart from the fact I formatted my secondary HDD in windows as a dynamic drive.  But everythings working pretty good, enjoying it alot.

---

### Post by Nightstrike2009 on 2009-11-01
Wish i could say the same a lot of us with 3G modem dongles found they worked in 9.04 and are borked now something to to with 9.10's borked network manager apparently definately not impressed.

Less time messing about with pointless cack like ubuntu one, more time getting essentials working before release please? I hope ubuntu 10.4 hasn't got this problem i'll be tempted to leave for another distro this is pathetic.

> Banner note: Ubuntu 9.10 is out!!!
Ubuntu 9.10 has **tons of new features which make it the best version of Ubuntu yet**

LOL take it you aren't using it / tried it yet then? LMAO stick to Ubuntu 9.04 the new one's a joke :) (9.10)

---

### Post by Regenweald on 2009-11-01
I honestly don't feel physically well until i see this same thread after every release. I was getting worried :) I look forward to one immediately after Lucid. Don't disappoint me.

---

### Post by Shibblet on 2009-11-02
I'm not really sure any Linux distribution is "ready for mainstream."  

My reasoning isn't directly functionality, although that does play a part.

There are too many "gaps" in the installation, and boot-up that make it look like it's not professional.  When you boot your computer, you watch bios do it's thing, then you see the Ubuntu logo pop-up, and it drops to a text mode of some kind showing what's being loaded, then finally back to the Ubuntu screen with the "status bar" letting you know how much further until booted.

Load whatever you want, but make it look seamless.  Make it look like the computer is doing nothing but running Ubuntu.  You don't have to show the output on the screen, but allow an option for that for advanced users.

This same thing happens on shutdown.  Your resolution drops to text mode, and there is a bunch of stuff all over the screen that most people don't pay any attention to.

The functionality portion is the glitches.  Things like the NBR playing screwy with your screen brightness.  That's just plain bad.  And when I say glitch, I mean glitch, not bug.  Bugs are a product of coding, and that's understandable.  But the bug that has turned into a serious glitch, that actually impedes use, is unacceptable.

So, I can say that Ubuntu isn't quite ready to be a mainstream OS.  And a lot of it, is just cosmetic.

---

### Post by BETATEST on 2009-11-02
But isn't this The Community Cafe?  This isn't one of the primary support forums.  If someone wants to vent, let them vent.  I mean, not every post on this forum have to be happy Ubuntu ones.

About the 5 minute question answering thing and 99% solution - check out the Newbie forum.  Where's all the answers for those posts?

Just being devil's advocate.  But just because someone posts something contrary to Ubuntu in a non support area, doesn't make them bad.  And why would Ubuntu developers be trolling this forum anyway?  We just had a Unix joke thread and someone ask what TV we watch while on the Internet.

Peace everyone - can't we all just get along and play Pingus?

---

### Post by Shibblet on 2009-11-02
> **BETATEST said:**
> But isn't this The Community Cafe?  This isn't one of the primary support forums.  If someone wants to vent, let them vent.  I mean, not every post on this forum have to be happy Ubuntu ones.

I agree.  It's not in any of the help-threads.  So argue all you like!  ;)

> **BETATEST said:**
> Just being devil's advocate.  But just because someone posts something contrary to Ubuntu in a non support area, doesn't make them bad.  And why would Ubuntu developers be trolling this forum anyway?  We just had a Unix joke thread and someone ask what TV we watch while on the Internet.

A rope walks into a bar and says "Bartender, give me a beer."  The bartender says "Hey!  We don't serve ropes her.  Get out!"
So the rope goes outside and cuts one of his ends and pulls out some threads.  He walks back in the bar and says "Bartender, give me a beer."  The bartender says "Aren't you that rope I threw out of here?"  
"Nope," says the rope.  "I'm a fraid-knot."

---

### Post by JohnAStebbins on 2009-11-03
> 
I get my desktop, and I can't get Handbrake to work. So I tried the Handbrake snapshot, which has a dependency that isn't available in the repositories anymore. I know this is not an OS specific problem, but it makes it so I have to go back to 9.04, because I utilize the heck out of handbrake.

A new HandBrake snapshot built specifically for Karmic is now available.
[http://handbrake.fr/snapshot.php](http://handbrake.fr/snapshot.php)

---

### Post by fiklein on 2009-11-04
I first installed Ubuntu on a Vista box because it kept crashing. My teenage children had a choice every time they turned on the computer which operating system to use. They immediately preferred Ubuntu (Intrepid Ibex). Everything works and I have no plans to change to Jaunty or Karmic on that computer. I have since installed Jaunty on two laptops and tried installing Jaunty on this one. Jaunty was a pain on the other two laptops but I got it working. I gave up getting wifi with Jaunty on this one, after days of trying solutions. Karmic worked instantly on this one. If it works, don't upgrade, just update. If it doesn't work, try another distro. I figure anybody who installs Linux on a computer is a gearhead, anyway. Once it works, the other users are much less likely to screw up Linux than  Windows. Also, remember that most operating systems come preloaded when you buy the computer. Ubuntu is so friendly because you can set it up on hardware built for another operating system, and dual boot it as well. Karmic has some issues, but they will get fixed.

---

### Post by timsdeepsky on 2009-11-04
I have never had these problems with Ubuntu....A few quirks,,yes....But i always got her working in no time....I checked the forums for the supported hardware,,,,Tested my systems with the live cd's,,,,and always had good luck with Ubuntu....I love her!!!!....Most of the friends i have,that had Ubuntu fail,,,,were using machines they built....And they put the cheapest Chinese parts in them that they could....Could this be a factor??....Probably so....

---

### Post by ElSlunko on 2009-11-04
I had a similar issue with my box.

Seeing as I've repaired (by reformatting and doing clean install) of 3 PCs with windows that were riddled with viruses and one vista friend who was upgrading to 7, I'd have to say problems can come up with any OS. Now I'm getting emails from my W7 friend telling me his laptop won't shutdown fully & when it goes to sleep it doesn't wake up. I'm not willing to rule out user error since I haven't seen his laptop after having done a clean W7 install, but the point is every OS will have it's implosion here or there.

Look at the debacle over people losing all their data from a Snow Leopard Guest account issue. Or people losing all their 1st born's baby pictures from their iPhone getting wiped by an update in iTunes. S*** happens and the technology gremlins are out there in every OS. Doesn't mean any of the aforementioned products "aren't ready for mainstream".

---

### Post by leveillerems on 2009-11-05
> **HappyFeet said:**
> You upgraded. What did you expect? Upgrading any OS is asking for problems. People just don't get it. I install OS's for a living, I know. Apparently you don't.
off course he upgrade we all do as an IT it's best to upgrade to know the system before you can mention it to your clients if you don't know your system up front then when your client ask about it what would you say "don't know much" then your client will find someone who does so yeah upgrade is goo i also install os for a living and i know when the OS come out you upgrade from a computer you work on then fix some bugs your self or email the company.

---

### Post by leveillerems on 2009-11-05
and i can undestand where the original poster is coming from because i also was waiting for 9.10, once i install it a big frown on my face because not only i am having trouble with software center (when a software is done install the center freeze) but also all my download is slow even on synaptic PM is slow it's like the whole ubuntu network for 9.10 is full of downloader ( yeah i know not a wor but got point right) anyways if i am to push 9.10 as i did 9.04 coanical will have to re-check the problem from some random computer on the street with ubuntu offcoarse and fix them because even java download is crashing on me.

---

### Post by karlofski on 2009-11-05
Well, my university uses Ubuntu on many of their computers and I started to love it. So about a year and a half ago I installed it on my home computer. I had horrible sound problems that I solved by purchasing a new soundcard. After that all was well for about six months until my old computer finally kicked the bucket from old age. I think the CPU just up and died from something mysterious (I will never know...).  So I got a new machine and guess what?!! Ubuntu wouldn't work at all. I couldn't move the mouse, I tried suggestions from forums about playing with BIOS settings and menu.lst settings and all that crap for days or even weeks with no result! Finally I just said F@$#% it! I will wait for Ubuntu to release a new version and try it later. Then Ubuntu 9.10 finally comes out. I install it and TADAA! Same old problems. After days of monkeying around with the same old procedure I finally found the problem. I didn't have my mouse drivers setup just the way Ubuntu likes it. 
In Windows or Mac OS, the worst that can happen if your mouse drivers are on default settings, is that you lose your extra mouse buttons or your mouse doesn't work at all. But in Ubuntu, your machine can crash, your USB connections will go haywire, your keyboard will stop working... All this from default settings...

If Ubuntu wants to be easy to use, they got to get those default settings as safe as possible and there has to be error messages that can help you debug your system. It takes way too much energy to get started on Ubuntu, but once it works I do love it. I hope the devs read this and start working on those hardware issues instead of anything else. I don't care if the windows look fancier if I can't even get the system working at all...

---

### Post by AllRadioisDead on 2009-11-05
> **kenweill said:**
> Windows 7 sux. It's the worst i've ever tried. Even worst than vista.

Network interface card and sound card not working on windows 7 ultimate final. Not detected. No manufacturer drivers.

Well, that's my experience this morning. Trying to install Windows 7 ultimate on my desktop. I just want to try if it works out of the box. Well, it doesn't. 

XP is better in detecting my network interface. Windows 7 sux this time.

Everything works out of the box with Ubuntu, and openSUSE.
No, you think windows sucks. 
There are millions of people of people that use windows and are satisfied with it. My Windows 7 install went flawlessly, all hardware detected and useable even in beta. The way I see it, it's your hardware manufactures fault for not providing updated drivers.

---

### Post by lancest on 2009-11-05
Same deal- Ubuntu or Windows 7. Buy hardware that is compatible with the OS you want to use.

---

### Post by 23dornot23d on 2009-11-11
All my hardware works fine .... with UBUNTU 8.10 ..... and  ..... with 9.04 ...... 

but upgrade to 9.10 ........ Quack Quack Ooooops ..........

No wireless modem
No sound
Nautilus giving errors ...

worst of all which worried me like mad was when I came out of 9.10

No USB shutdown and unmount for my 1 terra drive ......

Which lead to the problem of not being able to boot ....... any new user to UBUNTU ..... 
would have probably been a little worried here .....

as it reports no grub and no boot options ........

________________________________________________

If I could restore my internet connection I could probably get some of the things working ....


I thought I would check the Bugs forum ...... 30 critical Bugs at the moment ....

[https://bugs.launchpad.net/ubuntu/+bugs?field.tag=compat-wireless](https://bugs.launchpad.net/ubuntu/+bugs?field.tag=compat-wireless)

plus lots of others I see to do with Nautilus and USB problems ....... 

that appear to be non important ( and then ) asking for users to re-submit their reports  !!! 

INCOMPLETE ..... how many are ?

I do not understand this ...... if there are problems and users are trying to help .......



Why not listen a little to them ........ 9.10 is not ready ..... but I would advise anybody

who reads this and is thinking of upgrading to check the Bug reports first .......

and hopefully if it reduces ........ it may become ready for mainstream use  ........

( Anybody monitoring the success and failures ,,,, on upgrades  ,,,,,,,, )
_______________________________________

This is not intended to be anything other than constructive advice ........


Windows is not the issue here ,,,,, this thread is about UBUNTU 9.10 " NOT " being ready

The Upgrade in my mind is a disaster waiting to happen .......

I have used LINUX for a long time now ....... and usually can sort it out ......

This I will reformat and go back to 9.04 ..... and re-install the ALSA drivers as the only thing
that did not work on that version was the sound ......

New Users that try this upgrade .... may possibly have a very bad taste left
of 9.10 after this .... is it still in a ALPHA development stage ?
 

Cheers for reading .....

---

### Post by Skara Brae on 2009-11-11
> **ihermit said:**
> No, you think windows sucks. 
There are millions of people of people that use windows and are satisfied with it.
...which says more about those people than about **kenweill** :p

Sorry, I just couldn't help myself.

---

### Post by yester64 on 2009-11-15
> **HappyFeet said:**
> You upgraded. What did you expect? Upgrading any OS is asking for problems. People just don't get it. I install OS's for a living, I know. Apparently you don't.

Thats what hackers do and we are hackers, because we like to solve things and learn more. :)
I learned my lesson and did a fresh install. Works perfect so far.
Plus, install it over the lifecd, that way you can select the server from where you get the updates. Worked for me.
Handbrake does not work anymore which is a bummer. But i am very convinced that there is a solution for that problem too.
Windows is perhaps easier to use for the average joe, because i can not picture my father to install linux and encounter problems.
One thing the developers should do for gfx problem (i had that problem) is to enable a fallback driver (like a generic one) that allows you to get into the desktop and not thrown into the command prompt. I remember that suse had that (years ago with xwindows).

---

### Post by scottuss on 2009-11-15
I appreciate the issues the OP is having, but I think that arguing Ubuntu is not ready for the mainstream is incorrect. My argument would be the metrics used to determine the readiness.

In this case, an issue arose, an error message was displayed and although the user in this case understood the message, it was deemed confusing to new users.

I defy any user on this forum to tell me that every error message ever given by any version of Windows is simple, clearly explained and comprehensible to new users. You can't do it, because Linux (in this case Ubuntu) isn't the only OS guilty of using such confusing language. It just so happens that when Windows does this, the user gets stressed, turns the PC off and calls their local computer person, or takes it to their local computer shop. They calm down and shrug it off as "just one of those things that computers do" When Ubuntu does it however, we get told it's not ready for the mainstream. 

By this logic, Windows is not ready for the mainstream. I would argue that to be more true that Ubuntu not being ready. However, the infrastructure for support is the one thing that Ubuntu doesn't have. Yes there are forums, yes there are mailing lists and websites. But "normal" users don't have the time or inclination to visit these places and mess about with the system. If computer shops offered the same support for Ubuntu that they do for Windows, new users could receive the errors they do now, and instead of running back to Windows screaming that Linux is too complicated and not ready, they might get stressed, calm down, shrug it off and take their Ubuntu box down to the local computer guy who would fix it, just as they would a Windows PC.

Let's not blame the OS entirely here folks, remember, Ubuntu as a piece of software IS ready for the mainstream, perhaps the rest of the world isn't ready for Ubuntu to be mainstream... yet!

---

### Post by yester64 on 2009-11-15
> **scottuss said:**
> I appreciate the issues the OP is having, but I think that arguing Ubuntu is not ready for the mainstream is incorrect. My argument would be the metrics used to determine the readiness.

In this case, an issue arose, an error message was displayed and although the user in this case understood the message, it was deemed confusing to new users.

I defy any user on this forum to tell me that every error message ever given by any version of Windows is simple, clearly explained and comprehensible to new users. You can't do it, because Linux (in this case Ubuntu) isn't the only OS guilty of using such confusing language. It just so happens that when Windows does this, the user gets stressed, turns the PC off and calls their local computer person, or takes it to their local computer shop. They calm down and shrug it off as "just one of those things that computers do" When Ubuntu does it however, we get told it's not ready for the mainstream. 

By this logic, Windows is not ready for the mainstream. I would argue that to be more true that Ubuntu not being ready. However, the infrastructure for support is the one thing that Ubuntu doesn't have. Yes there are forums, yes there are mailing lists and websites. But "normal" users don't have the time or inclination to visit these places and mess about with the system. If computer shops offered the same support for Ubuntu that they do for Windows, new users could receive the errors they do now, and instead of running back to Windows screaming that Linux is too complicated and not ready, they might get stressed, calm down, shrug it off and take their Ubuntu box down to the local computer guy who would fix it, just as they would a Windows PC.

Let's not blame the OS entirely here folks, remember, Ubuntu as a piece of software IS ready for the mainstream, perhaps the rest of the world isn't ready for Ubuntu to be mainstream... yet!

Personally, i think its routine. Most people only know Windows and are accustomed in the way it works and expect that (as an example) Linux works the same way.
There are some areas where Linux can be better in my opinion.
Like i highlighted in a earlier post, its a bad thing if the OS leaves you in the command prompt. Most people don't know what to do.
You have to have some skills to master that step.
In the latest version (Karmic) i had the same problems like others with the gfx card in that in ran fine in the lifecd but did not boot into the desktop.
So you have to update the gfx driver over the shell and even that takes some hurdles since you have access the driver and have the privilges to access it.
That said, its not impossible, but it takes skills.
It would be better if Linux would have fallback drivers it would use in case something does not work.
The other thing is, people don't get neccesarily the philosophy behind linux. They are different models in how the OS behaves.
On Windows you have a pretty fixed system which does not give you the freedom in how to customize your OS. Linux on the other hand can be customized in any way.

Every OS has its downfalls and hurdles and sometimes people are a little impassioned and expect that things work like they do under windows.

My first attempt to install the update did not work and i had to go back to the previous version. Now i tried it again and learned and it worked (beside the gfx problem).

My knowledge is limited but i'll try and i want to master Linux.

Is Linux ready for mainstream? I think it is, but there are areas were it can improve. They aim should be to be better than Windows, rather than be like Windows meaning to overcome installation problems. That would clearly help to convince people of Linux.

---

### Post by JohnAStebbins on 2009-11-15
> Handbrake does not work anymore which is a bummer. But i am very convinced that there is a solution for that problem too.
The latest handbrake snapshot has a working deb package for karmic.
[http://forum.handbrake.fr/viewtopic.php?f=6&t=12842](http://forum.handbrake.fr/viewtopic.php?f=6&t=12842)

---

### Post by rahul_dhankani on 2009-11-15
@eliot rosewatever : any new release takes a little while to get completely sorted andi will have a few niggles here and there in its initial stages(even final releases). 
The thing to do is that if you find a problem/bug then report and help to solve it. Post it up on the forum and ask for help. Contribute positively instead of complaining. 
other op-sys have problems too - do you think you could have solved a problem in windows as easily as u did ur problems with ubuntu. 

UBUNTU means : "I AM WHO I AM BECAUSE OF WHO WE ALL ARE" . Think about that

---

### Post by alexfish on 2009-11-15
> **Eliot Rosewater said:**
> I would just like to preface my comments by saying Im an avid fan of Ubuntu and up to yesterday have recommended it to many people. However the upgrade to 9.10 has reminded me of the huge leap that people have to take to use it, and the problems with getting Ubuntu working.

--- 

I had previously used ext3 so I decided to do a full reinstall to get the full benefit of ext4 on Karmic Koala. I was exited about the new Ubuntu and downloaded it as soon as it was available and burnt the ISO. After installing it, and rebooting, I get this message

"Grub 1.5 ... Error 15"

and no list of OS's, so I cant use even XP. I did a bit of searching on the net through the live cd. Most of the solutions were for grub1, so even though I did a few things I got nowhere. So I reinstalled 9.10. Same problem.

Given that my MBR needed fixing, that I love Ubuntu, and that Im persistent, I decided to install 9.04, and then upgrade. 9.04 installed and the same old message came up "Grub 1.5 ... Error 15."

This is the point the standard user unplugs their machines, sends it to a technician and curses the day they ever tried to use Ubuntu.

But Im not that stupid, so I booted the 9.04 live cd and reinstalled Grub. Then at last I ot into 9.04 and started the upgrade. Halfway through the upgrade I got a dialog concerning grubs menu.lst. I assume the default setting - keep current version - will be ok given, well, that its the default! A half an hour later and to my joy Im finally using 9.10.

Until I played some music. Then I discover the sounds broken. So I did a load of Google searching and find that the issue is the kernel. You see grub was loading the old kernel because the upgrade kept the old menu.lst. So I manually edited the menu.lst to point to the new kernel and now my sounds working.

The same cant be said for Ubuntu One, which doesn't work at all.

---

There is a moral to this story. Despite Ubuntu claiming to be "Linux for Human Beings" the fact remains that the only reason I got Ubuntu working on my PC was because Im persistent as hell and because Im some way computer minded. I know what grub does. I know how to edit its settings. I know what kernel means. The average user Ubuntu targets does *not*.

Firstly I dont know why the reinstall of Ubuntu 9.10 didn't work. If I wasnt persistent I would have given up.
Secondly keeping the old menu.lst is the default option. If a regular person was confronted with that dialog they would have done the exact same thing I did and kept the default option. But do you think the average user would be able to reinstall grub, and then edit it to point to the new kernel?

Look, theres plenty of distros there that focus on getting new and better features. So if I was Ubuntu I would concentrate on *usability*. At the moment its *not* usable. 95% of people who went through my experience would have given up. How could I in my right mind recommend Ubuntu to anyone given what Ive gone through in the last 24 hours? 

Forget about the 10 second start. Theres much more important issues to be addressed.

Just my two (euro) cents.
{here is my one cent.and quote  if you have a mother board and did a fresh install of xp or vista and you lost the drivers etc etc  what does linux do that windows can't ,yes in most cases linux works   and the more people that try linux and support it the more support it will get from mainstream vendors and i would also thank Canonical for there efforts in bringing a operating system that is available to everyone }

---

### Post by yester64 on 2009-11-15
> **JohnAStebbins said:**
> The latest handbrake snapshot has a working deb package for karmic.
[http://forum.handbrake.fr/viewtopic.php?f=6&t=12842](http://forum.handbrake.fr/viewtopic.php?f=6&t=12842)

Hey thanks, i'll appreciate that.
Last time i checked it wasn't there. So now we have it :popcorn:

---

### Post by bedhead75 on 2009-11-15
I think the OP is correct about Ubuntu not being ready for the "mainstream" if we define the "mainstream" as being people who don't enjoy problem solving and having to tweek and fiddle with things to get them working to a certain level of personal satisfaction.  Ubuntu needs to focus more on having a continuum of consistency.  Hardware problems are hardware problems and some times they can't be helped, but I don't think it's really a hardware problem if one release had issues X and Y, and then the next release fixes them but introduces problems A and B, which were working fine in the previous release.  Even the LTS releases aren't immune to this, and one can find examples of this in the forums.  I don't think the mainstream has the patience to do a fresh install each time there is an "upgrade", and then to have to totally reinstall the older release if the "upgrade" breaks certain critical necessities that were working before and might need a lot of personal time and effort to fix in the new release.  If everything that works in one release still continues to work flawlessly upon upgrading, and any bugs that arise only have to do with new things being introduced then I think Ubuntu would experience mainstream adoption at a faster rate.  I know this is very idealistic and isn't ever realistic for any OS, but maybe more focus should be put on fixing basic useability issues and regressions instead of increasing boot-times by another 3s for example.

The other side of the picture is the mainstream psyche.  To the general public, the existing mainstream OS's are simply "good enough" because they can pretty much do most of the things they want right away, the minute they get their computers from the store.  If they get virus or spyware issues a few months down the line, they don't equate that with being an OS problem.  Ubuntu needs to be that much better than current mainstream OS's in the eyes of the general public in order for faster adoption, and issues like wireless and graphics card regressions really hurt.

---

### Post by TenGees on 2009-12-04
I'm usually a K/Ubuntu fanboy but 3 out of 3 machines wouldn't boot after installing 9.10. All of these work fine with 9.04. So I believe there is an issue here even though many are saying otherwise in this thread. I'm not trying to say that they shouldn't add new features but this will turn some people off. I always recommended Ubuntu to friends but now I'm recommending 9.04. This release is a pain for multi-boot machines. Defend it all you want but 3 of 3 machines say your wrong. I'm confident that the Ubuntu team will iron things out but for this release I agree with the OP.

---

