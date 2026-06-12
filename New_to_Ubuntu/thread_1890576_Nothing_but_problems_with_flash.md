---
title: "Nothing but problems with flash"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by anewguy on 2011-12-03
Since I did my 11.10 install (don't remember what it was like in 11.04 - worked in prior releases), I have had nothing but problems with the flash player.  It will play the advertisements that precede the videos, but it just shows the little circle afterwards and after a little while comes up and says the video is no longer available.

During this time, sometimes the video plays behind the text.  Other times you hear the sound but see the video and the sound of the advertisement mixed in.  Other times it just sits there with the message.  Sometimes when you try to close the page, or even while it has the message displayed, it goes to the "gray" screen which I always thought meant something was really busy on the PC (hey, I've got 4 cores running at 3gig each!).  I think at that time the player is aborting, but I can find nothing in the logs in /var/log to indicate a problem.

I've tried deleting everything flashplayer and adobeflash related from a search of the hard disk, then installing the installer via synaptic - same problems.  I then have removed everything again and tried gnash and the gnash browser plugin.  Even though the "tools" of the browser show the addon, anything flash comes up and asks me to install the flash player.  Whenever I have followed that link I have downloaded the tar.gz then unpacked the files, but never know which directory the .so is supposed to be moved to - and of course no readme comes with the download.

I have given up on ever having flash working unless someone has some great ideas.  I've followed, and posted in, other threads on the forum regarding flash problems, and nothing has helped.

I'm not sure this belongs in the beginner's forum or not, except that if other people are updating and having flash problems it might help them.

Just in case it has anything to do with it (I haven't found anything on the net to indicate so) I am using a nVidia GeForce 9500GT video card and the driver that additional drivers recommended I use.

Thanks in advance!
Dave ;)

---

### Post by lovinglinux on 2011-12-04
Get [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)and install the latest Beta. If you are on a 64bit system, then make sure you disable the HWVideo Decode in the extension tweaking options.

---

### Post by anewguy on 2011-12-04
I should have mentioned - tried flash-aid already with the same results.

I do have a question on the HWVideo Decode option:  I am running 32-bit Ubuntu but on a 64-bit processor - I assume the 64bit you refer to is for the OS?  Also, where exactly is the option?  I've checked under tools/extensions and don't see that option.  I've checked under add-ons and don't see that option, nor do I see it as an option there for flash player.

Thanks!!

Dave ;)

---

### Post by anewguy on 2011-12-04
I should probably also post here the odd and ends of things I posted in other threads where people were having similar problems.

- I have a DSL connection, that sometimes takes a very long time to connect and download.  Sometimes I think there is some sort of time out happening in the loading of the video - I've seen an option you can add in the HTML for flash player for this, but obviously I have no control over what comes in to my browser in that regard.

- I have tried a couple of other options some recommended in the about::settings for Firefox with no avail.

- I have an nVidia GeForce 9500GT video card, using the recommended driver from the additional/restricted drivers selection.

- I am running Firefox 8 as delivered.

What I would like to try:

- remove Firefox 8
- remove flash player
- install an older version of Firefox
- install an older version of flash player

and then see if that works.  I just haven't gotten around to trying that yet (I admit - on the fear I'll end up really hosed! ;) ).

Thanks again!

Dave ;)

---

### Post by wolfen69 on 2011-12-04
I had the same video card for a couple of years, and never had a problem with flash. I always download the tar.gz flash file, extract it, and put the libflashplayer.so into ~/.mozilla/plugins Never had a problem in years.

---

### Post by anewguy on 2011-12-05
I'll give that a try.  I even tried the chrome browser but it does the same thing, so it must be flash related.

Thanks!

Dave ;)

---

### Post by wolfen69 on 2011-12-05
Just make sure all other instances of flash and gnash are removed first. Btw, it's a "universal" way of getting flash to work in any distro.

---

### Post by anewguy on 2011-12-05
dumb question, but is "plugins" supposed to be a directory?  for some reason when I list the mozilla directory it shows only as a file.  I'll get the other stuff cleaned out and check back.

EDIT:  Cleaned out everything in the file system that seemed to be related to adobe flash except things like icons.  Started Firefox - no flash in plugins.  I then created a directory of plugins within .mozilla and copied the .so there.  Started Firefox - flash now in plugins, so tried one of the videos that failed before and there is no change - it still fails.

Thanks!

Dave ;)

---

### Post by wolfen69 on 2011-12-05
Is your install of 11.10 an upgrade or clean install? After countless installs of linux, I've never had my method of installing flash fail. It seems your install is borked in some way.

---

### Post by anewguy on 2011-12-05
Well, originally I decided to try something I normally wouldn't have done - an update.  Needless to say, contrary to what some people have said about how it is set up to work correctly, it still doesn't clear out some of the old stuff and seems to hose some of the new - the result of course was a system that wouldn't run.  So, I blew everything away.  So, I really did do a completely new installation - I had it format the partitions also to be sure none of the old would haunt me there.  So what I've been running off of is a completely new installation, plus all the stuff I've added for me.  I have a seperate /home partition, and I may not have cleared that the last time - this time I will, since it may have done something with one of the hidden folders for mozilla or one of the others (I'm thinking there's a Firefox 1 also - but that may have been somewhere else in the file system).

So, I'm thinking it might be worth (backing up this time, of course ;) ) blowing everything away again and trying a new install 1 more time.  The md5 checked out on the disk, so I assume the disk I burned was ok, but since I'm not sure I'm just going to download again and try everything from scratch.

This will probably take me a few days to accomplish with other things I have going on, so I'll post back in a day or 2 how things have gone and whether or not it solved my flash woes.

Thanks again!

Dave ;)

---

### Post by anewguy on 2011-12-05
Okay, this is not fun anymore.

I completely wiped my system then did a clean install of 11.10 (with the old disk), allowing it to download patches, 3rd party apps, etc., as it asks on one of the setup screens.

When finished and rebooted, I went right to Firefox - it shows flash player in the add-ons.  Went to a few videos that appeared okay, then went to [this]("http://shine.yahoo.com/tistheseason/tis-season-wrap-present-only-three-pieces-tape-164700355.html") one (all just random) and back to the same crap - video is not longer available with the video playing in the background.  In addition, trying to close the window it appears that flash must be aborting, as it gray screens again.

I did not install anything - not even a video driver.

My XP disk bit it, so I'm glad I have a copy of the virtual machine so I can at least use flash there (it works in the VM).  Right now I'm REALLY tempted just to go back to 10.04 LTS and wait for 12.04 LTS to see if anything improves.[http://www.yahoo.com/](http://www.yahoo.com/)

Is it worth reinstalling 11.10 again, this time NOT installing updates and 3rd party apps when asked, then installing flash in ~/.mozilla/plugins?


EDIT:  Update:  tried a plain install without the 3rd party apps, download of updates, etc..  Started Firefox - no flash player.  Went to Adobe, downloaded the tar.gz, extracted the .so, put the .so in a plugins subdirectory to my home .mozilla directory.  Started Firefox - shows flash player.  Went to the same page as above, got the same screwy mess. No "extra" video driver installed, etc.. 

I'm leaving this as-is for now - not downloading any updates, etc., in case someone wants some sort of information from this stupid installation before I blow it away and go back to 10.04 LTS.  I hope 12.04 LTS is better or I may need to rethink some things.

---

### Post by anewguy on 2011-12-05
Removed the plugins folder under my home .mozilla directory.  Installed flash-aid and let it do it's thing using the flash version in the repositories. Still no difference.  Then ran flash-aid again and selected the beta version from Adobe - it allows turning off hardware acceleration - no difference.

I still get the 10 second or so long grayed screens when I exit a page with flash on it, indicating to me it must be aborting.

When I select a flash video page, when it comes time that the video is the only thing being downloaded my wireless activity light still goes like crazy, telling me it's downloading the video.  Then I get the message about video no longer being available.  I really do think this is some sort of timing issue between the time-out on the flashplayer "call" in the web page versus the speed of the DSL connection I am using.

If anyone has any ideas - they would be GREATLY appreciated.  Otherwise I'm going to have to write flash off - and I'd really like to have that working.

---

### Post by anewguy on 2011-12-05
I think I should probably add something here:

For any new users or beginners, PLEASE do not be turned away from Ubuntu because of the problem I am having.  It is something very unique to my installation, I just don't know what.  You can tell by the replies here and by the lack of complaints in the forum that Ubuntu 11.10 has been better than ever - the number of posts in the forum, at least to me, seem to have dropped since 11.10.  Nor is this a problem specific to Adobe Flash player.  So PLEASE don't be turned away by this thread!

To others - 

I tried the latest nVideo driver with the post-release updates, etc., as recommended in the additional/restricted drivers.  That didn't make any difference.  I went back and instead enable the 173 driver with it's post release updates, etc..  I haven't noticed any difference, except that at least now if I go back quickly to a video that failed it will play.  I believe this is because it's still in cache so the load is not timing out.  I really do think this is a timing problem of some sort, but I have no idea how to trace it further at this time.

I'm not going to mark this as closed since the problem still exists.  I did, however, want to make any new users or beginners assured that this will not be their experience and not to shy away from Ubuntu.  That's why I hate making posts like this.

With that in mind, is there another forum in the Ubuntu group of forums where this might be more appropriate?  I've followed what I could from launchpad and made adjustments as I could.

Dave

---

### Post by anewguy on 2011-12-05
BTW - here's a screen shot showing when the text is there and the video actually starts playing in the background.  Please note that the leading advertisements always go okay, just the main video that follows has the problems.

EDIT:  Note this is with Firefox 7, and I have the same problem with Firefox 8, so it shouldn't be a Firefox problem either.  Does anyone know if there are any "hidden" parameters for Flash player?  I realize that wouldn't be a beginner topic so would probably need to be done in PM's.  It's just that I really think this is a timing issue, and I'm looking for any ways to tune Flash player.

---

### Post by beew on 2011-12-06
I am sorry to hear your problem. I am not really able to help,but have you tried a different browser (say opera) and see if it suffers the same problem? Just to pinpoint what is wrong. 

In my 10.10 install (and lesser extent in 11.04) I have been having similar problems with flash, but only in Opera (all versions in the last little while) and when hardware acceleration is enabled for flash. It works nicely in Firefox. I can live with not watching flash in Opera or uninstalling Opera all together so i haven't perused it any further when no solution was found after a few days (did a few reinstalling of flash and  Opera and cleaning out Opera config files and so on). Also have a Nvidia card but a different one from yours (G105M)

---

### Post by VeeDubb on 2011-12-06
I know that you have already done a good chunk of what I'm about to suggest, but I suspect that you missed a piece, or some reference to flashplayer in one of your previous attempts. (or possibly just did things in the wrong order)

In my experience, there is only one sure-fire way to get flash working, and it's as follows:

[LIST=1]
[*]Open up synaptic.  Then, search for and remove every package with any reference to flash, flashplugin, flashplayer, swf, or anything else that sounds even remotely like it could possibly be related to flash.
[*]Open a terminal and enter the following command to find all files on your system with "flashpl" in the name.  We're using flashpl because that will return flashplayer and flashplugin
[*]locate flashpl
[*]Delete every one of those files
[*]repeat the search and destroy with "swf"
[*]Open synaptic up again, and install "flashplugin-installer"
[*]Never again read or follow any other instructions for installing flash.
[*]Never again use any 'special tool' to fix your flash problems.[*]Never again follow any weblink or browser pop-up for installing, configuring or 'helping' with flash.
[/LIST]

It has been years since I had any trouble getting flash to work with the exception of problems I caused myself by trying to do something clever.  The package in the repo works, but because it's closed source commercial software, the ubuntu devs have little (if any) control over it, so it's easy to break if you monkey around.

Once you've monkeyed around and broken something, the only way to fix it reliably is to do as I've suggested.  Flash-aid may help many people, but depending on what you've done, it may or may not do the trick, and still leaves you dependent on a 4th party.

---

### Post by beew on 2011-12-06
> **VeeDubb said:**
> I know that you have already done a good chunk of what I'm about to suggest, but I suspect that you missed a piece, or some reference to flashplayer in one of your previous attempts. (or possibly just did things in the wrong order)

In my experience, there is only one sure-fire way to get flash working, and it's as follows:

[LIST=1]
[*]Open up synaptic.  Then, search for and remove every package with any reference to flash, flashplugin, flashplayer, swf, or anything else that sounds even remotely like it could possibly be related to flash.
[*]Open a terminal and enter the following command to find all files on your system with "flashpl" in the name.  We're using flashpl because that will return flashplayer and flashplugin
[*]locate flashpl
[*]Delete every one of those files
[*]repeat the search and destroy with "swf"
[*]Open synaptic up again, and install "flashplugin-installer"
[*]Never again read or follow any other instructions for installing flash.
[*]Never again use any 'special tool' to fix your flash problems.
[*]Never again follow any weblink or browser pop-up for installing, configuring or 'helping' with flash.
[/LIST]

It has been years since I had any trouble getting flash to work with the exception of problems I caused myself by trying to do something clever.  The package in the repo works, but because it's closed source commercial software, the ubuntu devs have little (if any) control over it, so it's easy to break if you monkey around.

Once you've monkeyed around and broken something, the only way to fix it reliably is to do as I've suggested.  Flash-aid may help many people, but depending on what you've done, it may or may not do the trick, and still leaves you dependent on a 4th party.

flash-aid does 1-5 automatically, and it may do 6 or install the adobe beta driver depending on your choice. The package in the repo may or may not work, or may work better or worse than the beta version from adobe. With flash-aid you can switch and try each easily. I am sure you can do it manually too just like your steps 1-6 , but it is just more conveniently using flash-aid.

---

### Post by anewguy on 2011-12-06
Yeah, I already manually deleted everything flash related and installed from the synaptic with no better results.  May try one more time.  Flash-aid has not been helping me either.

I have already tried the chrome browser also with no difference.

Thanks for the input!!

Dave ;)

---

### Post by anewguy on 2011-12-06
> **VeeDubb said:**
> I know that you have already done a good chunk of what I'm about to suggest, but I suspect that you missed a piece, or some reference to flashplayer in one of your previous attempts. (or possibly just did things in the wrong order)

In my experience, there is only one sure-fire way to get flash working, and it's as follows:

[LIST=1]
[*]Open up synaptic.  Then, search for and remove every package with any reference to flash, flashplugin, flashplayer, swf, or anything else that sounds even remotely like it could possibly be related to flash.
[*]Open a terminal and enter the following command to find all files on your system with "flashpl" in the name.  We're using flashpl because that will return flashplayer and flashplugin
[*]locate flashpl
[*]Delete every one of those files
[*]repeat the search and destroy with "swf"
[*]Open synaptic up again, and install "flashplugin-installer"
[*]Never again read or follow any other instructions for installing flash.
[*]Never again use any 'special tool' to fix your flash problems.[*]Never again follow any weblink or browser pop-up for installing, configuring or 'helping' with flash.
[/LIST]

It has been years since I had any trouble getting flash to work with the exception of problems I caused myself by trying to do something clever.  The package in the repo works, but because it's closed source commercial software, the ubuntu devs have little (if any) control over it, so it's easy to break if you monkey around.

Once you've monkeyed around and broken something, the only way to fix it reliably is to do as I've suggested.  Flash-aid may help many people, but depending on what you've done, it may or may not do the trick, and still leaves you dependent on a 4th party.

Remember the James Bond film Never Say Never Again?  You need to change your never's ;)  I just repeated all of this again and have the exact same result.

As I've said, I still believe it's a timing issue where the "call" in the html for FlashPlayer has a time-out, and that time-out is being hit either right at the time the last frame of the video arrives, or shortly before that.  That's why I'd like to find some option to override the call time-out.

Dave

---

### Post by anewguy on 2011-12-07
Another thing to note - I can play all the games on Shockwave.com with no problem - and they use the FlashPlayer.

Advertisements load and play.

It's the main videos I have problems with, a lot from Yahoo generated pages and a lot from other websites.

Since it does seem to be isolated to videos in my case, I still think it's a timing issue.  None of the settings make any difference, and I can't find anything about any hidden parameters of some sort to flash.

---

### Post by anewguy on 2011-12-08
I should also note that this has something to do with the Linux version of FlashPlayer.  I have a Windows 7 laptop with very similar specs to my desktop (quad core 3ghz, 4gb memory, etc.) that also connects wirelessly to the same router for the same DSL connection, and FlashPlayer on it does not fail on the very same items that fail in Linux.

---

### Post by anewguy on 2011-12-13
Another update:

Installed Windows 7 over the weekend, so I let it use the entire disk.  After that, I went back through and created the Linux partitions and also downloaded a new 11.10 cd iso, burned it and verified the md5sum.  Next I installed 11.10, allowing it to download updates during the install and to install 3rd party software.

So, flash still doesn't work.

I loaded synaptic so I could do some more checking and found that indeed the installer (actually 2) for flash were installed.  Something I did notice, but I imagine it can't make any difference, is that ubuntu-restricted-addons was marked as installed but not ubuntu-restricted-extras.  The notes for ubuntu-restricted-addons says not to install the package separately but to instead install ubuntu-restricted-extras.  So, could this mix up, done by the installation process, have anything to do with why my flash doesn't work?

---

### Post by kurt18947 on 2011-12-13
Just for grins, would it be worth creating a Live USB/DVD of Mint 12?  I'm pretty sure you can play flash videos in the live session without installing anything extra.

---

### Post by anewguy on 2011-12-13
Thought, hummmm, interesting idea.  Since Mint is based on Ubuntu (if I remember correctly) I thought to just try this with the 11.10 LiveCD.  Well, no flash appears to be installed when actually running off the LiveCD.

Thanks for a good thought, though!

Dave ;)

---

### Post by kurt18947 on 2011-12-13
> **anewguy said:**
> Thought, hummmm, interesting idea.  Since Mint is based on Ubuntu (if I remember correctly) I thought to just try this with the 11.10 LiveCD.  Well, no flash appears to be installed when actually running off the LiveCD.

Thanks for a good thought, though!

Dave ;)

You got somethin' weird goin' on.:confused:.  I just booted a LiveUSB with Mint 12 32 bit on it.  I played a couple YouTube videos just to check that they worked then went to this site:
[www.thewoodwhisperer.com]("http://www.thewoodwhisperer.com")
which will play both windowed and full screen in the live session.   Have you checked for gremlins,poltergeists and their ilk?:D  My rig is unremarkable.  The only thing I may have different is that this is a 32 bit Live session.  I know there were some issues with 64 bit flash but I thought those problems were in the past.
[ATTACH]209042[/ATTACH]
I wish I knew what to tell you.

---

### Post by anewguy on 2011-12-13
Brand new download, md5sum verified, brand new install.

I don't get it either - hence why I've been posting.

And like I've mentioned before - it's not for all flash - some play, but that's few.  The player works fine when I go to shockwave.com and play the daily jigsaw, daily diff, etc.

---

### Post by anewguy on 2011-12-13
BTW - I know this is limited to Linux because it works fine in Windows 7 (dual boot).  So, it can't be a hardware issue, etc., it's got to be flash, linux, some linux driver, etc..

---

### Post by mystika1 on 2011-12-14
I feel your pain. I have Lubuntu installed(32 bit but my processor is amd64) and had the exact same problem. Two months ago my hulu video played flawlessly..now..terrible. Tried flash-aid with hw settings off and at first I thought that did the trick but..no. I finally got results when I downloaded the older flashplayer 10 from adobe and extracted the libflashplayer.so file in the plugins folder. Removed all other flash versions. Now my videos play correctly. I am also running 11.10. I have my noobish directions here. [http://ubuntuforums.org/showthread.php?t=1861488](http://ubuntuforums.org/showthread.php?t=1861488)

I don't think reinstalling ubuntu will change your situation unless you try the 64bit which may help. I have noticed most people who say flash is working great are running 64bit.

I decided to install debian squeeze(32bit) on an old machine to see if flash would work better. I had the exact same problem in debian. The only thing I can see is that because I an using 32bit on a 64bit machine they may have a glitch. My next experiment will be to try lubuntu 64 bit and see if the problem continues.

Penny

---

### Post by anewguy on 2011-12-14
I'm going to give flash 10 a try!  I also have a 4-core AMD 64bit CPU but running 32-bit Ubuntu.  Never thought about that being a problem.

I'll take a look at your link, then give version 10 a try and see what happens.

Thanks!

Dave ;)

---

### Post by anewguy on 2011-12-14
Alas - ear wax.  No difference using the version 10 flash player.  I checked the flash window that opens to be sure it says version 10 so I know it had the old release - just doesn't make any difference.

But, going with what was in the thread you posted, does anyone know if the flashplayer that gets installed matches the Ubuntu architecture - 32bit or 64 bit?  I would assume a 64-bit app like that wouldn't run in 32-bit Ubuntu, but hey - maybe someone can verify that.

For you people who are reporting Flash working fine in 11.10 - are you running 32-bit Ubuntu or 64-bit Ubuntu?

Thanks!

Dave ;)

---

### Post by mystika1 on 2011-12-14
Ok, I just burned the 64 bit live cd and once it was loaded I installed lubuntu-restricted-extras/firefox with flash-aid and my video is beautiful. Not even a flicker. I will get my important files saved to a flash drive and install 64 bit to replace my 32bit install. You may want to try this....

Penny

---

### Post by anewguy on 2011-12-15
> **mystika1 said:**
> Ok, I just burned the 64 bit live cd and once it was loaded I installed lubuntu-restricted-extras/firefox with flash-aid and my video is beautiful. Not even a flicker. I will get my important files saved to a flash drive and install 64 bit to replace my 32bit install. You may want to try this....

Penny

I might try that again - I have had the 64-bit version in the past and had some problems with it and the powers that be "highly recommended" I go back to 32-bit at that time.  Since I already have my install backed up anyway, I might as well give this another try - probably over the weekend.

Thanks Penny!

Dave ;)

---

### Post by geekwanabe on 2011-12-15
> **mystika1 said:**
> Ok, I just burned the 64 bit live cd and once it was loaded I installed lubuntu-restricted-extras/firefox with flash-aid and my video is beautiful. Not even a flicker. I will get my important files saved to a flash drive and install 64 bit to replace my 32bit install. You may want to try this....

Penny

Thank you Mystika! I tried everything; I don't even know what I've done I tried so many things, but I installed the Ubuntu restricted extras and flash aid and it worked!

---

### Post by stchman on 2011-12-15
Flash works great in Ubuntu 64.

In 32 bit simply install the flashplugin-nonfree package.

In 64 bit bit you need to install the .so you get from Adobe.

[http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_11_for_other_Linux_%28.tar.gz%29_64-bit](http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_11_for_other_Linux_%28.tar.gz%29_64-bit)

Then copy it to the /usr/lib/firefox-addons/plugins/ folder.

---

### Post by geekwanabe on 2011-12-15
I'm using 11.10 in 64 bit and had problems since its inception.  So I removed everything having to do with flash by terminal and synaptic.  It only worked when I added restricted extras, both options in synaptic.

---

### Post by anewguy on 2011-12-15
I've already had the restricted extras, but the non-free flash is separate from what the restricted extras installs.  I also had trouble with flash in 64-bit in 10.10, but I'm going to give 64-bit a try in 11.10 just to see if i can get around my flash problems.  Flash-aid, as already noted, doesn't make anything better for me.

I'll see what happens when I try 64-bit.

---

### Post by anewguy on 2012-01-07
I've let this sit for a while, because it's really rather disappointing to me that in order to watch a flash movie I have to boot Windows.

The current status update is that nothing has changed.  Tried 64-bit, etc., still the same results.  Brand new installs - nothing added.  Doesn't work.

Dave

---

### Post by anewguy on 2012-03-01
Okay, I built a completely new system.  Installed the 64-bit version of 11.10, allowing updates to be downloaded and installed during the installation and to install 3rd party software.

Flash still gives me the same problems, mostly on any video that is associated with Yahoo!  I've had others work ok, but nothing from Yahoo.

One can only assume it's something with flash, but you never know.  I'm looking forward to 12.04 with the *HOPE* this will work.

---

