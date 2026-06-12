---
title: "Can't play music"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-29
Hi,
Suddenly, I cannot play any music on my Hardy 8.04 system. I'm told the device is busy or I couldn't connect to stream because of invalid arguments. Have attached screenshots. These are for Kaffeine and RhythmBox but the same thing happens with MoviePlayer as well.
Why should this happen suddenly without me changing any settings?

phil

---

### Post by bobnutfield on 2008-07-29
I have seen it happen that some Java applet on a website or something will take over the sound device, and sometimes even when you close the browser, it is still tied up.  Try opening a terminal and type:

> ps -u <your user name>

Look for processes that have the word java or mixer-applet.  Note the process id to the left and kill it.  See if the sound comes back after this.

Bob

---

### Post by philk949 on 2008-07-29
Bob,
when I run the command, I notice this process (no javas)
[COLOR="DarkRed"]mixer_applet2 / process id 6079[/COLOR].
Do I now run: kill pid 6079?

---

### Post by bobnutfield on 2008-07-29
No, that is your default mixer.  Killing it would definite kill your sound until you reboot.  By the way, have you tried re-booting to see if that cures the problem?

---

### Post by RuleMaker on 2008-07-29
You can kill process by it's ID or by it's name, like:
pkill mixer_applet2

---

### Post by bobnutfield on 2008-07-29
See if you have "pulseaudio" in process list, and if you do kill that, log out (not necessary to reboot), and log back in.  Also, try in a terminal:

> sudo fuser -v /dev/dsp


This should tell you what process is using the sound device.

Bob

---

### Post by philk949 on 2008-07-29
Tried running the code:sudo fuser -v /dev/dsp 
Result is 'no such file or directory'
If killing mixer_applet2 is my default mixer, why was I advised to kill it by rulemaker?
A little consistency please. This is frustrating enough for a newbie.

---

### Post by frogotronic on 2008-07-29
> **philk949 said:**
> Tried running the code:sudo fuser -v /dev/dsp 
Result is 'no such file or directory'
If killing mixer_applet2 is my default mixer, why was I advised to kill it by rulemaker?
A little consistency please. This is frustrating enough for a newbie.

reboot

---

### Post by bobnutfield on 2008-07-29
Sorry, I should have mentioned a java process with mixer in the title.

---

### Post by philk949 on 2008-07-29
Reboot doesn't work.
And Bob, think nothing of it.
Have the uneasy feeling that something is failing on boot up - missing modules perhaps?

---

### Post by bobnutfield on 2008-07-29
OK, if rebooting doesn't work, then back to basics is required.  You said that sound SUDDENLY stopped working...were there any updates performed?  Type 

> lspci

and tell us what your sound card is.  The fact that you have no /dev/dsp file is troubling.  This is a character device file.  When you ran the fuser command, even if it returned nothing, it should not have reported no folder or file.

Also type

> sudo lsmod

This is to see what sound modules are loaded.  They will have a snd prefix.

Bob

---

### Post by philk949 on 2008-07-29
Have attached screenshots:
1. lspci output
2. sudo lsmod - no snd, nearest is sd module

Phil
(troubling? that can't be good)

---

### Post by bobnutfield on 2008-07-29
OK, in the visible part of your screenshot, for lsmod I cannot see enough to determine whether there are any sound modules loaded.  Do you see any entries that begin with
snd_ ?  Should be several of them.  The modules may be listed out of the screenshot visible.

You sound card is definite recognized by the system:

Intel Corp. 82891BA Multimedia Audio

Again open a terminal and type:

> cat /dev/sndstat

This should give some detail about your soundcard

---

### Post by philk949 on 2008-07-29
cat /dev/sndstat 

'No such file or directory'

There were no snd modules in the read-out

Phil

---

### Post by bobnutfield on 2008-07-29
Well, I have to tell that I have never know something like this to happen out of the blue.  It appears that you have NO sound drivers.  When you go to System>Preferences>Sound, what is shown in the box for Device under Default Mixer Tracks?  Also, type alsamixer in a terminal to see if it runs. If it does not, run:

> asoundconf reset-default-card

Bob

---

### Post by philk949 on 2008-07-29
System>Preferences>Sound>Default Mixers <no entries>

alsamixer - 'no such file or directory'

asoundconf reset-default-card  - no result (does that require a reboot?)

Phil

---

### Post by SunnyRabbiera on 2008-07-29
yipes, its not even picking up alsa... something screwy is going on here.

---

### Post by bobnutfield on 2008-07-29
No, rebooting at this point isn't going to help as it appears that ALSA is not showing up.

In the terminal, type:

> sudo apt-get install alsa

This to try and reinstall alsa.  Very, very strange that this happened suddenly.  Do you have more than one sound card (i.e. on-baord sound and a PCI card)?

---

### Post by bobnutfield on 2008-07-29
> **SunnyRabbiera said:**
> yipes, its not even picking up alsa... something screwy is going on here.

Hi, SunnyRabiera...hope you can help us out here..you're right, this is very strange as it happened suddenly out of the blue!

Bob

---

### Post by philk949 on 2008-07-29
Don't think I have more than 1 sound card.

Included result of running 'sudo apt-get install alsa ' as screenshot.
Thanks so much for your generous assistance guys, especially you Bob.
I'm all in, as it's getting pretty late here and I have an early start. If you don't mind, perhaps I may be able to re-connect tomorrow.

Phil

---

### Post by bobnutfield on 2008-07-29
OK, I will bookmark this post and get back to you when I have researched a solution.  Check back for further posts tomorrow.

Bob

---

### Post by stoffe on 2008-07-29
Sound disappeared for me today after some updates (didn't really scan them, Firefox -security rebuild as among them, last update I made before this one was probably thursday or friday). All of it. No warning dialogs but Totem and Rhythmbox both just froze then refused to play (RH pauses, Totem "plays" without sound).

For me, I could solve it by going to System->Preferences->Sound and set Music playback back to Autodetect - for some reason it had blanked out to nothing.

I have no further analysis or clues to provide, only saw that this thread looked somewhat similar to my problem, sound disappearing after updating.

---

### Post by bobnutfield on 2008-07-30
OK, if you are still interested in going further with this, open a terminal and type:

> dmesg | grep snd

This will list the kernel's effort to load sound modules.  Since there are none being loaded, it should give an error message which can be deciphered.  Also, checking in to this it appears that your sound card uses the snd-intel8x0 module.  Let's see what dmesg says.

---

### Post by philk949 on 2008-07-30
Evening Bob, thanks for coming back.
I'm afraid I have bad news though. Running the code produced no error message in the terminal. Is there a way of checking the System log for what might be going on?
Ran the code twice to make sure.

Phil

---

### Post by bobnutfield on 2008-07-30
If dmesg is not providing any output, you can run dmesg on its own with no arguments and it will produce a very long display.  It will take you a few minutes to scan it all.  I was just trying to confirm if there was any attempt by the kernel to install sound modules.  Your previous attempt to install alsa-base shows that it is already installed.

Run

> dmesg | less

The result will be very long and probably won't make much sense to you, but just scan it and look for any reference to you intel sound chip or the snd-intel8x0 module.  The system logs provide about the same output as dmesg.  The less porttion of the command lets you look at the output one page at a time

---

### Post by philk949 on 2008-07-30
Something to ponder, perhaps.
I coaxed an admission from a classmate that she had been fooling around in Synaptic after I had entered my password to open it. We are looking at setting up a virtual server on which to run some tests for an assignment, but I had decided against doing anything until I had cleared the decks and was more confident of a non-catastrophic result.
Seems friend gave it a shot on my PC without my permission, but justified it by saying she had uninstalled it and therefore, no problem. I am not convinced and feel this could well have a lot to do with the problem. What do you think?
You can leave out the part about how dumb I am leaving her alone with my computer.

---

### Post by bobnutfield on 2008-07-30
OK, I think the key word here is "uninstalled it"..

It's hard to comment without knowing what was installed and what was uninstalled, but I think that solves the "out of the blue" mystery...

Somehow, I believe all of the sound modules have been removed.

---

### Post by philk949 on 2008-07-30
I believe it was virtualbox-ose.

I could find no reference to any sound chips in the last terminal read-out.
Sorry I didn't know about this earlier, Bob. Would have saved you a lot of generous effort.
Are we dead in the water, this side of a re-install of Ubuntu?

Phil

---

### Post by bobnutfield on 2008-07-30
Well, I am not at all familiar with virtualbox (other than to know it is very popular.)

Try three more things:

> sudo apt-get install alsa-utils

It may report that it is already installed, but lets see anyway.

Then:

> sudo modprobe snd-intel8x0

This is to try and load the module your sound card uses.

Finally,

> sudo /etc/init.d/alsa-utils reset

Just in case there are any broken packages, try:

> sudo apt-get -f install

> sudo /etc/init.d/alsa-utils start

Lets see what this provides.  But if you do not have months of configuration set up on you machine, it may well be that re-installing would be the best option.  Before that, though, I am hoping that someone with extensive experience with a problem like this will see this post and chime in,

---

### Post by philk949 on 2008-07-30
Ran all the codes Bob. I feel bad that nothing has worked, after all you've done - you deserve a result.
And yes, there's a good deal of configuration on the system, but hey, I've been through this before when the operating system that dare not speak its name crashed and propelled me toward Linux. But I won't do that just yet.
Thanks again for everything, you're a credit to the Ubuntu community.

Phil

---

### Post by bobnutfield on 2008-07-30
Got one more thing I am going to search for you.  I will get the instructions for your sound card (which I have confirmed is in fact the snd-intel8x0) and post back.

---

### Post by philk949 on 2008-07-30
Thanks Bob

Phil

---

### Post by bobnutfield on 2008-07-30
> **philk949 said:**
> Thanks Bob

Phil

OK, rather than giving you the instructions from the ALSA site, I found this.  This post is over two years old, but I have examined it and it all still looks relevant and doable on Hardy.  Since your modprobe for the snd-intel8x0 driver revealed that it doesn't exit, you will need to install it.  So, what you will be mainly interested in is the section called Alsa Driver Compilation.  But read the beginning as well.  This is a very well written HOWTO, and I believe this will get you going. the post is here:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=linux+backports]("http://ubuntuforums.org/showthread.php?t=205449&highlight=linux+backports")

I believe the "apt-get" solution is all you need and will not need to compile the source tarballs from the alsa site.

Let me know how it goes.

---

### Post by philk949 on 2008-07-30
Sorry Bob, but there are 1,064 posts on this thread, and I can't see anything that matches the info in your last post.
Where am I supposed to be looking?

Phil

---

### Post by bobnutfield on 2008-07-30
Just the guide itself, not the following posts.  There is a section called Alsa Driver Compliation.  In this section, it explains how to install the drivers for your card.  Just before that is "Getting the Drivers from a fresh kernel".  The beginning of the guide is pretty much what we have already done, so I think that the next step would be getting the driver installed.  I suggested reading the first part of the guide only to note the warnings and how to enter the commands.  Particularly note the part about chossing your driver in the section Alsa Driver Compilation and remembeer the driver for your card is snd-intel8x0, as that is the one you will choose.

---

### Post by philk949 on 2008-07-30
All I see is a regular post page, no guide. What am I missing, for crying out loud?
Maybe it's time to take me out and shoot me?

Phil

---

### Post by bobnutfield on 2008-07-30
> **philk949 said:**
> All I see is a regular post page, no guide. What am I missing, for crying out loud?
Maybe it's time to take me out and shoot me?

Phil

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem")

Very sorry, looks like my link was bad...Try this

---

### Post by philk949 on 2008-07-30
> Very sorry, looks like my link was bad...Try this

The link above 'try this is the same page, Bob. Was there supposed to be something after try this?

It's very cruel to torture dumb animals, Bob.

Phil

---

### Post by bobnutfield on 2008-07-30
Well, can't explain that one....opens fine the way I linked it from my browser.  At any rate, go to the main page of the Ubuntu Forums, Multimedia and Video, and it is the first stickied post at the top of the page.

---

### Post by philk949 on 2008-07-30
This is the page you directed me to, Bob.
The first sticky is the first link that didn't work.
The second sticky isn't a guide that I can follow and I don't see its relevance.
Sorry, Bob, I can't follow any of this. It doesn't seem to bear any resemblance to what you're talking about.

Phil

---

### Post by bobnutfield on 2008-07-30
OK, would you like me to guide you step by step what this guide instructs?  I will do it one step at a time so that there is no confusion.  The whole purpose is to get the proper sound drivers installed and this WILL get them installed.

---

### Post by philk949 on 2008-07-30
My problem, Bob, is that I can't FIND the guide.

---

### Post by bobnutfield on 2008-07-30
On the screenshot you posted it is the first post by LordRaiden.  The section I am talking about is about half way down.  Do you see the post?

---

### Post by philk949 on 2008-07-30
I'm about 'half way down', but could you please be more specific? Each post has a name, and several are dealing with the problem.

---

### Post by decoherence on 2008-07-30
hi phil. i'm just going to jump in here because i see exactly where the communication breakdown is.

when people here refer to a guide, they're referring to a regular forum post that aims to be a comprehensive how-to. The first post in the thread is the guide. Everything after that are generally comments and suggestions on improving the guide or requests for further help.

So when Bob says halfway down, he mean halfway down the first post (the guide.)

Perhaps we need a guide guide? :lolflag:

also, if you really want to show bob some love, you can click the little medal in the lower right part of his posts. good luck with your issue!

---

### Post by bobnutfield on 2008-07-30
The relevant part is only the first post by LordRaiden.  The subsequent posts by other users are not what I am talking about.  See this screenshot.  If you would like, I will guide you using these directions myself.

---

### Post by philk949 on 2008-07-30
Thanks Bob. Still can't find it, or anything like it, so I'll have to take you up on your offer and sleep some other time.
Phil

---

### Post by philk949 on 2008-07-30
So sorry, Bob. My posts are ordered last to first for some reason, so I needed to go to page 107 to find it.
Take a time-out if you like and I'll let you know how I go.
So sorry for stretching your kind patience.

Phil

---

### Post by bobnutfield on 2008-07-30
OK, I know it's late there, still just afternoon in the UK.  OK, here goes.

The first thing is to completely remove the sound apps from your system.  Don't worry, we are going to immediately reinstall them:

> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

This removes them and cleans out any old garbage hanging about.

Now reinstall them:

> sudo apt-get install linux-sound-base alsa-base alsa-utils

The guide states that occassionally this will remove the desktop (gdm), and if that happens, do this:

> sudo apt-get install gdm ubuntu-desktop

Now reboot.

Once you have rebooted, test whether your soundcard is now detected:

> aplay -l

Try these first and post the results.

---

### Post by bobnutfield on 2008-07-30
> **bobnutfield said:**
> OK, would you like me to guide you step by step what this guide instructs?  I will do it one step at a time so that there is no confusion.  The whole purpose is to get the proper sound drivers installed and this WILL get them installed.

> **philk949 said:**
> So sorry, Bob. My posts are ordered last to first for some reason, so I needed to go to page 107 to find it.
Take a time-out if you like and I'll let you know how I go.
So sorry for stretching your kind patience.

PhilNo problem here, glad to help and no, my patience is much longer than that...

---

### Post by frank_costanza on 2008-07-30
My sound stopped working after installing kde 4.1. The following command fixed it for me:

sudo /etc/init.d/alsa-utils reset

Thanks to bobnutfield for that.

---

### Post by philk949 on 2008-07-30
Wish I could send you a sound bite, Bob.:) It's bouncing off the walls now.
So very appreciative of your patience and expertise. Well done.
Maybe talk again when my next problem comes around some time soon.

Phil ):P

---

### Post by bobnutfield on 2008-07-30
Congratulations!!  This is the kind of problem you get every now and then, but the more problems you solve, the more you realize what a great thing Linux is.

Hope to hear from you again.

---

### Post by philk949 on 2008-07-31
Hi again
I'm posting in this thread because my current problem is directly related.
After re-installing my sound modules, I did in fact lose my desktop, as warned in the Sound Guide. I ran the suggested code:
sudo apt-get install gdm ubuntu-desktop
and rebooted. No result - still in the dark place of the command line start-up screen. I also notice that VirtualBox may still be on my system ( a friend had installed and uninstalled it, she said).
Could someone come to my rescue on this two-pronged problem, again?

Thank you

Phil

---

### Post by bobnutfield on 2008-07-31
Hi Phil,

Go to /etc/event.d/re.default.  It's a short file.  Don't change anything, but copy and paste what it is.  You may just be starting in the wrong runlevel.  I think I can get you up and going.  Your frined who installed virtual box may not have actually known how to uninstall it.  If you want to do that:

> sudo apt-get --purge remove vitualbox

That should get it off your system.

---

### Post by philk949 on 2008-07-31
Hi Bob,
Might have known it would be you to the rescue!
Afraid I have to make a sheepish admission. The spare computer I was using was so slow and freeze-prone that I despaired of getting anything meaningful happening through the forum, so I bit the bullet and re-installed Ubuntu. Sorry to have troubled you unnecessarily, and thank you once again.
I'm sure the code would have worked a treat, but at least now I can add it to a repository of highly useful codes that I'm building up.
Best regards,

Phil

---

### Post by bobnutfield on 2008-07-31
No problem, at least you now a fresh system..

BTW, added you to my friends list.  If you run into anything you need help on, message me here if you like.

---

### Post by philk949 on 2008-08-01
Many thanks Bob. 

Phil

---

### Post by Bucky Ball on 2008-08-01
I lost sound also after updates and installing and uninstalling Firefox extension Better Youtube a couple of times. As mentioned earlier as one possibility, I think it was going onto a website where their java applet took over that may have actually killed it though because that is when it happened pretty sure.

I went through the steps of attempting to reinstall alsa-utils mentioned much earlier, and as predicted, it was installed. But told me I had a package that was no longer needed: libakonadiprivate0

I ran the command,

> sudo apt-get autoremove libakonadiprivate0

... then this one,

> sudo /etc/init.d/alsa-utils reset

... and bingo! ... :)

So thanks BobNutfield, I only needed that much to fix my problems.

---

### Post by bobnutfield on 2008-08-01
> **Bucky Ball said:**
> I lost sound also after updates and installing and uninstalling Firefox extension Better Youtube a couple of times. As mentioned earlier as one possibility, I think it was going onto a website where their java applet took over that may have actually killed it though because that is when it happened pretty sure.

I went through the steps of attempting to reinstall alsa-utils mentioned much earlier, and as predicted, it was installed. But told me I had a package that was no longer needed: libakonadiprivate0

I ran the command,



... then this one,



... and bingo! ... :)

So thanks BobNutfield, I only needed that much to fix my problems.

Sound can be a real stinker to get going again when you lose it...glad you got it going,

---

