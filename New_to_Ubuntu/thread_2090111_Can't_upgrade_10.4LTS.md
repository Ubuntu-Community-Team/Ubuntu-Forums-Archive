---
title: "Can't upgrade 10.4LTS"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by Loren Bliss on 2012-12-01
Tried a dozen times  to upgrade 10.4 lts to 12.4 lts per the Update Manager's instructions and failed each time. 

Error message is preserved on screen shot which sorry I don't remember how to post.  The message seemed to indicate missing software.  

Hence I then tried sequential upgrading,intending to go  from 10.4 to 10.10 to 11.04 then eventually to the 12.4 goal. But that ended after I successfully upgraded to 10.10. 

When I try to upgrade to 11.04, I am obstructed by a combination of Internet connectivity problems and error 404 (files no longer exist). Obviously this means there is no longer any way to get beyond 10.10. 

Now it seems I'm stuck with dangerously unsupported 10.10, no way to go back to 10.4 lts and no way to go forward. 

Please advise.

---

### Post by howefield on 2012-12-01
Is a fresh install out of the question ?

Several benefits to a nice new and pristine install.

---

### Post by ibjsb4 on 2012-12-01
What's your computer specs?  Maybe you need something that's easier on resources.  Xubuntu?

---

### Post by howefield on 2012-12-01
> **Loren Bliss said:**
> When I try to upgrade to 11.04, I am obstructed by a combination of Internet connectivity problems and error 404 (files no longer exist). Obviously this means there is no longer any way to get beyond 10.10. 

Now it seems I'm stuck with dangerously unsupported 10.10, no way to go back to 10.4 lts and no way to go forward.

You can probably upgrade beyond 10.10 by pointing your sources.list to old-releases.ubuntu.com/ubuntu/ repositories.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Loren Bliss on 2012-12-01
Howefield: fresh install would require me to back up all data, most of which is photography, the downloading of which onto a flash drive would take -- no exaggeration -- at least 14 eight-hour days. For example, a single folder of 36 35mm frames takes about an hour to load onto a flash drive, and there are probably  150 of these, some 20 exposure, some 24 exposure, most 36 exposure, plus some 12-exposure takes of 120 film.  Next month I would have that kind of time; this month I do not, and I'm terrified of running unsupported 10.10 for even a few days.

---

### Post by howefield on 2012-12-01
> **Loren Bliss said:**
> Howefield: fresh install would require me to back up all data, most of which is photography, the downloading of which onto a flash drive would take -- no exaggeration -- at least 14 eight-hour days. For example, a single folder of 36 35mm frames takes about an hour to load onto a flash drive, and there are probably  150 of these, some 20 exposure, some 24 exposure, most 36 exposure, plus some 12-exposure takes of 120 film.  Next month I would have that kind of time; this month I do not, and I'm terrified of running unsupported 10.10 for even a few days.

Then use the link. 

Rhetorical question, are you really running without all those files already backed up. Wow.

Upgrading is also not without risk and to do so without having your files backed up is gross negligence to your data.

---

### Post by Loren Bliss on 2012-12-01
I've only used 28 percent of 1001 MiB

---

### Post by Loren Bliss on 2012-12-01
Had everything backed up on a flash drive -- took me most of two months to download it all -- but now that I need it, it seems to have disappeared. Tore apart the apartment looking for it: no joy.

---

### Post by howefield on 2012-12-01
> **Loren Bliss said:**
> I've only used 28 percent of 1001 MiB

Not sure that you mean this, that would take a few seconds to transfer to a flash drive, a few minutes at most.

> **Loren Bliss said:**
> Had everything backed up on a flash drive -- took me most of two months to download it all -- but now that I need it, it seems to have disappeared. Tore apart the apartment looking for it: no joy.

So the answer is yes, you are running without a backup ;-)

---

### Post by Loren Bliss on 2012-12-01
Will try the link after I get some sleep. Been fighting with this problem since 8 a.m. yesterday morning and am now at the nodding-out-at-the-keyboard stage. Whether your suggested approach works or not I'll post the results here tomorrow.  Many thanks!

---

### Post by howefield on 2012-12-01
Good Luck, hope it works out for you. 

I'd again, advise not to doing anything till you safely have a copy of your data backed up.

---

### Post by Loren Bliss on 2012-12-01
> Not sure that you mean this, that would take a few seconds to transfer to a flash drive, a few minutes at most.

Usage figure is from my system monitor. Text loads at light-speed, a 200,000 word manuscript literally in the snap of a finger.   But the photography downloads at a snail's pace.  Dunno why: others far more knowledgeable than I say it's a flaw in my machine.  (Reason I'm not too worried about the pix is they're also all on CDs.)

---

### Post by TheFu on 2012-12-01
Running without a backup - scary.  Running without a backup of your "critical data" **fracking, unbelievably scary**.

Seems that 33% of 1TB is 330GB.  500GB HDDs are $50 here. I find that $50 to let me sleep at night an extremely cheap price.  It is also less than spending more than a few hours on this issue. Please, **don't use USB2** to connect it to the system - use USB3 or eSATA or even open the case and directly connect it via SATA.  **Not having a backup is your biggest risk today - even more than not being on current, supported, OS versions.  **

With a backup, you can more easily perform a fresh install, get things working, and definitely **split your OS partition off** from your boot partition and your DATA partition(s) during the fresh install.  You should not accept all the defaults, if that isn't clear.  It also helps if your box gets hacked or has some other software or hardware failure.  With a backup, you won't have to worry about losing data during the next update/upgrade cycle to 14.04 LTS.  

A slight amount of planning ahead is useful.  Trust us.

There are thousands of reasons to have a good, versioned, backup.  A mirror backup, like rsync will make, is less useful, but still better than nothing.  Check out rdiff-backup, Back-In-Time, DejuDup, Duplicity, Duplicati for easy-to-use backup tools that will provide versioned backups.

Sorry if I sound like a broken record. Versioned backups are extremely important.

---

### Post by BlinkinCat on 2012-12-01
Hi,

A little tip from a not very experienced user.

I do my backups to 2 flashdrives at least twice a month. You can organize things so that you only backup new or altered files. Others will no doubt have better ways of going about it, but I am quite happy with this method.

Cheers - :P

---

### Post by Wim Sturkenboom on 2012-12-01
> **Loren Bliss said:**
> Howefield: fresh install would require me to back up all data, most of which is photography, the downloading of which onto a flash drive would take -- no exaggeration -- at least 14 eight-hour days. For example, a single folder of 36 35mm frames takes about an hour to load onto a flash drive, and there are probably  150 of these, some 20 exposure, some 24 exposure, most 36 exposure, plus some 12-exposure takes of 120 film.  Next month I would have that kind of time; this month I do not, and I'm terrified of running unsupported 10.10 for even a few days.
You like to live at the edge, don't you.

Instead of worrying about running an unsupported version, I would worry about my data. What if your HD crashes? If that data is that important to you, you would have made backups long ago. And have them reasonably up-to-date.

Also be aware that upgrades can go wrong (with possible data loss as a result).

Some solutions that can work:
[LIST=1]
[*]Buy an external harddisk (if you have enough money to spend) and make backups; they can run during the night; verify them and after that do a fresh install
[*]Install an additional internal HD (if money permits) and install 12.04 or 12.10 on that. Next start making backups.
[*]Put 12.04 or 12.10 on a usb stick (persisent install) and use that till you have time to sort out your PC; you can access your important data from there. Next start making backups.
[*]If your current setup has a seperate home partition and you know what you're doing, you can take the risk (for you to evaluate if that risk is acceptable) of a fresh install (make sure you don't format the home partition during the install). Next start making backups.
[/LIST]

Did I mention that you have you make backups :D In case you did not get that: MAKE BACKUPS

Good luck


// PS
Took me a while to type this (about 10 posts :()

---

### Post by Bartender on 2012-12-01
Loren, another option to consider.  Kind of a tweak to Wim's list.

First, this suggestion is based on the fact that HDD storage is cheap.  A 2TB HDD is - what - [just a bit over $100]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152245") nowadays?

Second, it's also based on an assumption that your existing HDD is [SATA]("http://en.wikipedia.org/wiki/Serial_ATA"), not the old ribbon-cable PATA, and that your motherboard has at least two SATA ports.  

Third, I'll assume you either can do this yourself, or can get someone to help you out for a couple of hours.

Buy a new SATA HDD.  Pull your existing HDD out.  Install 12.04 LTS clean to the new HDD, just like howefield suggested in Post #2.  You now have the latest LTS, and you didn't risk your data.

Slave your old drive to the motherboard and copy (not move) all your personal data off to the new HDD.

When you're sure you have the personal data safely copied, convert the old HDD to a backup drive.  Buy a [dock]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817153071").  Unless your PC has an eSATA port, or you can add one (easy if there's a spare SATA port on the motherboard), the simplest thing to do is just use the dock's USB 2.0 interface, but that's awful slow when you have multiple gigs to move.

Then use GParted to wipe the old drive clean, and reformat it to one big ntfs partition.  Connect the dock to the PC, drop the old drive into the dock, start copying (or moving) your pictures from the new drive back to the old drive again.   

After all that, you'd have safely upgraded to the latest LTS Ubuntu without risking losing your personal data, and you'd have a backup device that's far more robust than flash drives.

The above might sound complicated & scary, but these are all pretty basic steps.  Easy for anyone who's spent a little bit of time under the hood of a PC or two.

EDIT: You mentioned that copying to USB flash drive would take hours.  I've run into similar very slow USB transfers with Ubuntu.  Same data copied off Windows to a flash drive went much faster.  I don't know the answer; flaky USB support in Ubuntu for some devices?  Anyway, eSATA is much faster if you have it or can retrofit.

As far as running an unsupported version of Ubuntu, it's not recommended but I don't think it's any more risky than storing all your photos on just one HDD w/ no backups.  I ran 9.04 well past the end of life & nothing happened.  That I know of anyway ;)

---

### Post by Cheesemill on 2012-12-01
***Another massive +1 to not upgrading until you have a backup.***

All hard drives fail. It's not a matter of if it's a matter of when.

You're in the situation where you could lose all of your data instantly without any warning at the moment, get yourself an extra HD and back everything up ASAP unless you don't mind losing all of those photos.

Once you've done that we can figure out why your system isn't upgrading, although without knowing your error messages and now you've moved to 10.10 it would probably just be easier to perform a clean installation.

---

### Post by Loren Bliss on 2012-12-02
WOW! Very much to consider here. Thank you all.  Won't comment further tonight but will be back tomorrow. Thank you again.

---

### Post by TheFu on 2012-12-02
> **Cheesemill said:**
> All hard drives fail. It's not a matter of if it's a matter of when.

THIS!!!!!   +1000.

Everyone thinks there HDD will never let them down, until it does.  There is no predictable way to know when a HDD will fail. None.  People will try to explain that SMART data works as a predictor. That is not true.  There aren't any predictors.  Google did a HDD study and published it a few years ago about HDD failure stats.  Drives tend to fail very quickly if they will fail, however, drives of all ages fail ... though there are HDDs that last 7+ yrs and longer.

I've lost data because I didn't have a backup. The HDDs involved died without any warning.  I'd been doing backups manually for a few yrs, but I'm human and it is human nature to stop doing things that seem like a waste of time.  When the HDDs (2 of them) failed, it had been over a year since my last backup.  

I've learned from that mistake AND my work in enterprise IT architecture.  Backups are critical for many, many, many, reasons, not just the obvious.

Here's a prior thread just about backups that might help.
[http://ubuntuforums.org/showthread.php?t=1915813](http://ubuntuforums.org/showthread.php?t=1915813)

---

### Post by Zill on 2012-12-02
> **TheFu said:**
> ...I've lost data because I didn't have a backup...
There are two types of people in this world: those who have lost data, and those who will. ;-)

---

### Post by Bartender on 2012-12-02
Loren, you're probably tired of reading lectures about backing up.  I read back thru this thread, and I think I've identified what set things off.

[COLOR="Blue"]"Tried a dozen times to upgrade 10.4 lts to 12.4 lts per the Update Manager's instructions and failed each time.

I then tried sequential upgrading,intending to go from 10.4 to 10.10 to 11.04 then eventually to the 12.4 goal."[/COLOR]

That's the part that sent shivers down my spine.  It'd be one thing if you were banging away unsuccessfully with some old spare PC with no valuable data.  Folks on the forum would have admired your persistence and encouraged further efforts.

However, the fact that you're trying repeatedly to overwrite the OS on a PC with all your photos onboard changes everything.  

I'm not writing this to make you feel bad, just trying to explain why most of the responses detoured around your request for help upgrading and instead zero'ed in on the backup issue.

---

### Post by Loren Bliss on 2012-12-02
Bartender...I too am in WA, 253AC. You? 

All...

I know all about data-loss as my all life's work including two books in progress -- one generating serious interest in NYC publishing circles -- was destroyed in a 1983 fire. For me, a journalist (half writer/half photographer) since my 16th year (1956), this was an extinction-level event -- the lost photography killed the picture half of my resume and the subsequent clinical depression killed the reportorial half: no crazies allowed in newsrooms. So -- yes -- I believe I do understand the need for backups.  

Therefore to ease everyone's concerns (for which thank you all):  

Apropos  photography, it's all either on CDs and/or in old-time negative files.  The good is all this data is separate from any (definitively unreliable) machine. The bad is I've never figured out how to build an  efficient post-fire catalogue of the work.  (All my pre-fire negs, 1952 thru 1983, were listed  on a card  catalogue,  filed alphabetically by subject and  identified by take number; contact sheets and prints were filed by subject in a standard four-drawer cabinet; the negs were filed in negative pages stored in three-ring binders. Most of these negs plus all prints and transparencies were destroyed, but some salvageable negs were dug out of the rubble a year later and I have these, filed under old catalogue numbers in new pages.  Post-fire negs are also in the old-style negative pages but uncatalogued.  Likewise the negs now on CD. (When you still shoot only film, as I do -- can't afford the $1000-plus it costs to go digital hence never will -- it's film > negs > CD). Have never come up with an efficient post-fire system for cataloguing negatives because, frankly, I've never been able to bear the emotional discomfort of revising the old catalogue.  Best I've yet done with CDs is scribble subject/film/camera/date on the plastic covers and stack them in my bookshelves, but they are all there.      

Yes re-downloading from CDs would be  a huge  snail-paced pain (about 30 minutes per CD), but it's actually far less time consuming than (again) loading all pix to a flash drive.  

Text is a different story entirely as it flash-drives at the speed of light.  But text falls into two categories. One is unpublished writing: that I back up by flash drive and indeed do so frequently. Category two is my blog (mostly political, small but international audience) and relevant posts on various news-oriented websites: this is all "out there" -- that is, on the Internet, and to whatever extent the Internet is archival, so is that material.  (Anybody interested, just Google my name: I'm on two servers, TypePad and Blogger; the latter graphically gawdawful but for some reason necessary to reach my Eastern European readers.) 

Hence before attempting to climb out of this seemingly inescapable trap I've fallen into trying to upgrade, please rest assured I'll flash-drive all text I imagine is worth saving.  

Probably these backup methods seem hopelessly primitive to some of you, but I can afford no better. The contraction of the economy took away nearly 70 percent of my income, leaving me only with my Social Security pension, and the death of journalism as a viable occupation combines with my age (72) to strand me forever in inescapable poverty that worsens every year as U.S. social services are methodically terminated.   

This is not to tell a sob story, merely to explain why any backup options that require spending more than maybe $15 or $20 (if even that) are (forever) beyond my reach.  Indeed I would have been permanently off-line in 2009 had somebody not used me in lieu of a Dumpster to get rid of this Ubuntu-equipped but often weirdly nonfunctional computer.  

Again thank you all; your concern is deeply moving -- and I most assuredly do not mean that sarcastically. 

Now onto the real problem: 

As things stand, I cannot even begin escaping from the 10.10 punji pit.  As soon as I start the process, it terminates my Internet connection. 

If someone would please remind me how to post  screen-shots here -- I tried using the "insert image" feature and could not make it work  -- it would surely facilitate this dialogue. (I also have screen-shots of the error messages generated by whatever blocked  my efforts to update directly from 10.4 lts to 12.4 lts.) 

So now -- with the backup issue hopefully resolved -- it's back to y'all.  Now I'm gonna fix a late lunch and will check back in about an hour. 

Again my gratitude.

---

### Post by Cheesemill on 2012-12-02
To attach images when writing a post first scroll down and click on 'Manage Attachments'.
When the windows appears click on 'Browse' and select the image to upload from your computer.
When all required images are attached click on 'Upload'.
When your done uploading click on 'Close this window' and you can continue editing your post.

I'm glad to hear you have your backup sorted, now lets try and get you updated :)

---

### Post by viper250 on 2012-12-02
if you have some of the info about the computer you are using and your data has been backed up i could offer more information to you 
what flavor of ubuntu are you using?
I use pinguyos 12.04 
it runs well on older systems as well as newer ones.
trying to upgrade through update manager can be a daunting task indeed and can often take a long time.
Ive found it easier and faster to backup the data and install a newer version
then restore the backed up data.

---

### Post by TheFu on 2012-12-02
Upgrades sorta work, but doing upgrade after upgrade after upgrade definitely leaves some old versions of things on the system which can confuse some of the newer software.  This is mainly why the "experts" usually perform a fresh install for major Ubuntu updates.  

This can be performed risk free for most users.  Here's how.
* Smart partitioning - OS, Data, and boot in different partitions.
* Leave room on the HDDs for a few extra OS installs - just 10G or 15G is plenty
* When migrating between OS versions, use the dpkg get-selections/set-selections trick to get almost all of the same programs installed between different distro releases.  I love APT. Read more about that here: [http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)  Not all software is available between different released versions. This also avoids the old config file cruft.
* Since you'll have 2, 3, 5, 10 extra OS versions installed on different partitions, you can usually mount the "main" version you've been running previously and look at your old config settings easily.

That does not solve your "upgrade" problem, but it does get you to a supported release. BTW, 10.04 is not well supported already. Most developers are not back porting anything to that version.  

I manage a box for Mom that has it and Thunderbird appears to have removed their PPA for it last week. Mom is moving to 12.04 ASAP.  I plan to buy a new, cheap, HDD for her and perform a fresh install of 12.04, leaving lots of room for 3 other OS partitions, plus a Data, boot, and HOME partitions. Her old HDD is over 6 yrs old - I'm very afraid it will fail any second. We have backups - local and remote for her system and all the files on it.  She uses less than 12G total so it is easy to manage the backups.  She and I both run Lubuntu, which is great for older hardware.

Sorry that this isn't the answer you wanted, but it is an option that I've used many, many times the last 10+ yrs. It works and should work going forward for any APT-based release.

---

### Post by mansonfan78 on 2012-12-02
One thing you can do (if you have a cd burner and some blank cd's) would be to download the .iso images of ubuntu 11.04, 11.10, and 12.04 and burn them to cd's and try to incrementally upgrade that way.  If they aren't available on the ubuntu website you should still be able to google them and find them somewhere.

---

### Post by Loren Bliss on 2012-12-02
One last backup question just occurred to me:

Two vital sets of data are my address books (in Evolution email) and my bookmarks, which contain many hard-to-find links to European websites.  

Any way to download these onto a flash drive?  (I've tried everything I can think of but no joy.) 

(We get this issue out of the way, then I'll begin downloading those screen shots, Meanwhile thanks much to  Cheesemill for the screen-shot-loading  instructions.)

---

### Post by Loren Bliss on 2012-12-02
Sorry (damnit), totally unexpected guest. Back ASAP, probably in another hour, two max. Meanwhile again thank youse all.

---

### Post by Wim Sturkenboom on 2012-12-02
> **Loren Bliss said:**
> 
Two vital sets of data are my address books (in Evolution email) and my bookmarks, which contain many hard-to-find links to European websites.  

For evolution, it has a built in export and import functionality in the _file menu_. Not behind an Ubuntu machine, but I think it's called _backup_ and _restore_ respectively. It will export everything to a file somewhere on your HD; I have a dedicated directory where I dump my email backups.

I need to mention that I have had one occasion where restoring those email backups completely failed (possibly due to size of archive). But when I upgraded from 10.04 to 12.04, restore worked smoothly.

If I recall correctly, you can also export your contacts to vcf file(s). And lastly you can make a backup of the evolution folder that is somewhere in your home directory; but the only time that I tried to use that (Ubuntu 6.06), I found that evolution did not really like that approach; although this might have changed in general, Evolution in 12.04 uses a different format for storage and therefor this latter approach might also not work.

I'm not sure where firefox stores its bookmarks; someone else can advise.

---

### Post by Loren Bliss on 2012-12-03
Wim Sturkenboom...On address book I'm screwed. Error message says "The folder could not be displayed. Operation not supported."  My only option is to print it out -- and then desperately hope my failing eyes and arthritic fingers can type it accurately back into the computer. That loss alone -- with all my remaining non-local news-source access -- will kill my blog.  

Now Evolution has suddenly begun demanding I sign in -- and is rejecting my known-to-be-good (stored in the computer) password.  Am rebooting to see if that solves the problem 

The lost bookmark list is the loss of years of research and  could not possibly be restored in my remaining lifetime. 

Real panic setting in. Beginning to look like this upgrade debacle has brought me to computer doomsday.

---

### Post by Loren Bliss on 2012-12-03
Found an Ubuntu compatible  Firefox add-on -- Xmarks Sync -- that saves my bookmarks as a document downloadable to a flash drive, which I just did. 

Controls took a few minutes to figure out -- only problem was my compu-challenged mind -- but am now one step closer to a clean fresh instal of 12.4 lts, which increasingly seems the only rational alternative.   

Anyone else needs this bookmark accessory -- and it looks damn useful for  those of us who do serious research --  go bookmarks > get bookmarks  ad-ons > Xmarks Sync.

---

### Post by Loren Bliss on 2012-12-03
My evolution has died completely: won't recognize my password, won't connect with my server (Century Link); is now utterly useless and obviously beyond restoration. 

Good news is that some of my address book is already stored via q.com. I'll start tomorrow exporting everything else from Evolution into q.com.  All Evolution functions are now dead. Exporting thus  has to be done one item at a time, not by cut-and-paste or copy-and-paste (because the formats aren't compatible), but by old-style typing.  To be error-free this will take at least eight-10 hours, maybe more; I'm a writer, not a clerk-typist.  Plus there's one last-minute double-check for text I want to back up on the flash drive. (Have given up on saving the photos save by the CDs already described; be at least a week of work -- probably two -- to get all that back on the computer, but so be it.)     

After that -- assuming this computer still runs at all (which is increasingly doubtful) -- I'll be back for instructions on how to do a fresh instal. 

Many, many, many thanks to all.

---

### Post by Bartender on 2012-12-03
It kinda sounds like your PC is having hardware probelms, unrelated to Ubuntu or Windows

---

### Post by Loren Bliss on 2012-12-04
Any checks I can run to determine if the problem is indeed hardware? (HD is virtually new, replaced last spring. ) 

Meanwhile I'm continuing to back up stuff. notably my address books.

---

### Post by Bartender on 2012-12-05
It's just the things you describe - programs suddenly losing track of address books, stop working right, Evolution demanding to see a password that worked just fine for months or years.  Weird stuff like that.  More of a hunch than anything else.

If I'm trying to figure out a really glitchy Windows PC, I'll boot from a Linux LiveCD and run it for a few days.  If the PC shuts itself down, or can't run from the LiveCD, or acts weirdly in any way, then I know it's not just Windows.

One of the most important tools for a geek or geek wanna be such as myself is to have a few PC's laying around.  That way I can swap power supplies, plunk in a different hard Drive, what have you.

Which reminds me, you should probably run memtest.  I don't think memtest is available on the latest Linux CD's.  Or is it?  Anyway, an older Linux CD will give you a choice of running memtest at boot-up.

You can make a [memtest boot CD]("http://www.memtest86.com/").  It's not horribly hard, but can be confusing if you haven't made bootable CD's much.

memtest will check your RAM.  In my limited experience fixing PC's, RAM is probably second to power supply failures.

---

