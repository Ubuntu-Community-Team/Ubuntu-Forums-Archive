---
title: "Automatix Gone - What is its Replacement?"
date: 2008-05-11
forum: Recurring Discussions
---

### Post by OzzyFrank on 2008-05-11
OK, so Automatix has been discontinued, and there will be no version for Hardy. Besides installing **ubuntu-restricted-extras**, what other options are there? Is there an app similar to Automatix now, or in the making? Installing **ubuntu-restricted-extras** fixes many missing codecs etc, but gives you no control over what you are installing. Same with **Medibuntu**, which if I remember correctly was an app at one stage too, but is now just some repos you add to your sources.list. Any ideas?

---

### Post by jrib on 2008-05-11
I don't understand what is missing.  Instead of checking boxes in automatix, you check boxes in Add/Remove or Synaptic.  What exactly can't you do that Automatix did?

---

### Post by Mr. Picklesworth on 2008-05-11
ubuntu-restricted-extras is a metapackage, so if you really want control for some reason, just search for individual codecs (or check its dependencies in Synaptic). I seem to recall some codec packs only appearing in Synaptic. Not sure if that has been changed of late...

Also, most of the time, Totem will pop up a message to automatically download the needed codec, again giving you a bit more fine-grained control.

As for Automatix's replacement, it does not have one. Ubuntu is its replacement; there are very few - if any - functions at this point that it provided and Ubuntu does not.
For a few other very restricted (potentially illegal) codecs which Ubuntu does not officially provide, see [Medibuntu]("http://www.medibuntu.org/"). Medibuntu is a set of repositories because that is all you need, and because that is the standard way to do this in Debian. Because Medibuntu carries out installation through the same central system as everything else in Ubuntu, you can use it and still expect upgrades to go smoothly as well as all things to be orderly.

---

### Post by OzzyFrank on 2008-05-11
> **_jason said:**
> [COLOR="DarkRed"]I don't understand what is missing.  Instead of checking boxes in automatix, you check boxes in Add/Remove or Synaptic.  What exactly can't you do that Automatix did?[/COLOR]

Um... the big difference here I think is that Automatix wasn't filled with thousands of packages, but just listed those to do with non-free, multimedia codecs, etc, and because of that made it all easy to browse and find. To do so in Synaptic would mean knowing the names of the packages etc... while in Automatix you could just browse through a few items and go "Oh, I better install that too".

As for Medibuntu repos, yeah, I'm doing that anyway, but want to know if there is/will be something user-friendly like Automatix, as many people out there weren't happy with Ubuntu (or its lack of codecs etc) till they found Automatix. Keep in mind this isn't so much for me, but for when a newbie asks about this, which they always do. Used to be you could just say "Install Automatix!" rather than "Figure out which codecs you actually need, search through the thousands of packages in Synaptic, locate them, or figure out which metapackages they come in, then...".

[COLOR="#8b0000"]"there are very few - if any - functions at this point that it provided and Ubuntu does not"[/COLOR]

OK, not sure what that means, since Automatix is an app and Ubuntu is a distro... but if you are basically saying Automatix was never actually needed, coz Ubuntu has it all already, then I would have to disagree. That's what made Automatix so popular, that it filled the holes of a standard install, letting people play DVDs and different downloaded media. If you are saying you can do it all through Synaptic with a bit of searching, my earlier response regarding ease of use applies. And telling a newbie to install an app is much easier than explaining how to add the Medibuntu repos or telling him which metapackages he should be searching for.

---

### Post by jrib on 2008-05-11
I think the codec issue is taken care of in a better fashion than with automatix.  As Mr. Picklesworth's pointed out, when totem is missing a codec, it looks for the package and tells the user, "hey, you need to install this to view this file, want to do that?".

A similar thing happens with flash in Firefox.  A yellow bar pops up and the user clicks on it to install.

I see your point though.  You want an application that lists common things that users install so that they are more easily found.  However, excluding the codecs and flash for the reasons above, what is left?  I can think of dvd playback.  Anything else?

---

### Post by OzzyFrank on 2008-05-11
> **OzzyFrank said:**
> **Medibuntu**, which if I remember correctly was an app at one stage too, but is now just some repos you add to your sources.list. Any ideas?

I could have been thinking about Easyubuntu or whatever it was... unless Medibuntu did come as an app earlier.

---

### Post by p_quarles on 2008-05-11
> **OzzyFrank said:**
> I could have been thinking about Easyubuntu or whatever it was... unless Medibuntu did come as an app earlier.
EasyBuntu is probably what you were thinking of. Medibuntu never had an install helper script. 

In any case, those helper scripts aren't supported, since they don't really conform to proper package handling procedures. Frankly, it is not a lot of work to install ubuntu-restricted-extras, along with whatever other media things you might need. The medibuntu .deb packages can be downloaded directly from their site, without needing to add the repository.

For those not wanting to do that, Linux Mint provides a distro that is mostly identical to Ubuntu, but includes the extras by default.

---

### Post by OzzyFrank on 2008-05-13
For those who see no need for Automatix and can't understand why some people love it, here are some quotes from a blog where the instigator asked others why they bother with it. The misconception being Automatix just grabs stuff already available through Synaptic:

[COLOR="DarkRed"]What makes Synaptic/Adept difficult is not knowing off hand what packages you need to install. Multimedia support packages come to mind. Unless you have found the wiki page with the info, it is rather hard to decipher what you need to install.[/COLOR]

[COLOR="Blue"]It&#8217;s not used by most to install software that is in Ubuntu&#8217;s repos. It used to install software that is not, or can not be in there.

For example, Google Earth, Skype, beta versions of software not yet in the repos and FasterFox (or what ever it is). It provides an easy way to install all the codes, Firefox plugins, and things like that.

It lets you get your system loaded with that kind of software in minutes.[/COLOR]

[COLOR="Indigo"]Automatix is a great tool to help first timers get their machine up and running and start evaluating the OS instead of being forced to understand linux repositories and installation techniques from the ground up. Eventually those that like the platform learn that Automatix is unnecessary and move away from it due to redundancy but that doesn&#8217;t make Automatix any less useful.

I don&#8217;t understand why so many people seem to have such hatred or disgust for a program that HELPS draw people into your environment.[/COLOR]

[COLOR="DarkRed"]Automatix isn&#8217;t used for the same reasons that Synaptic is, so I don&#8217;t think a comparison between Automatix and Synaptic/Adept is really accurate.

And I&#8217;ve never had to edit anything to install Automatix. Automatix is the first thing I use on any new Ubuntu installation because it offers quick access to all of the codecs (FOSS and proprietary) and programs that I need to get my machine up and running without jumping through a lot of hoops.[/COLOR]

[COLOR="Navy"]Automatix was created to fill an important need in Ubuntu. Users should not have to jump through hoops just to view flash/java websites, watch movies, or listen to music.[/COLOR]

[COLOR="Indigo"]It takes away some of the pain of installing - and setting up - apps that people find useful and want to have on their systems. They *could* do it themselves, installing them one at a time, tinkering with them to set them up or they can just check some boxes, leave it while it runs and come back a little while later to a system that has all the bits and pieces they want installed.[/COLOR]

[COLOR="DarkRed"]yes, you can manually edit your repositories and select the packages and install them. but who wants to go through and click on 20 different codecs when one click in automatix will do the same thing?

automatix is meant to be run once really, after a fresh system install. after that go back to synaptic, all the packages will update through there.[/COLOR]

[COLOR="Navy"]Thx to automatix i dont need to loose my time searching for codecs.[/COLOR]

[COLOR="Indigo"]if it was not for automatix I would not be using Ubuntu right now. I knew immediately that I was dealing with an OS superior to the one I was currently using, but there was no way for somebody who had never used Linux to make it work right away. I know how to install all of the packages on my own now, but I didn&#8217;t then.[/COLOR]

[COLOR="DarkRed"]I have used Linux long enough to easily be able to install everything Automatix does. The key though is that I don&#8217;t WANT to. Don&#8217;t underestimate Automatix. It is a large part of what makes Ubuntu so great. Nobody wants to spend hours setting up codecs, media players, MP3 support, etc. That&#8217;s exactly the kind of stuff people want to just work.[/COLOR]

... etc.

---

### Post by jocko on 2008-05-13
Which part of opening up synaptic, searching for "restricted-extras" and clicking install is harder than googling for "automatix", downloading the correct version from a website (or adding it's repo to sources.list), installing it, running it and browsing through a few different categories, in the end finding "install multimedia codecs" and clicking install?

One reason for not using automatix is because it's *easier* to do it through synaptic or add/remove than through automatix, at least when you have added the appropriate repos.
True, if you don't want the entire meta package it's a bit of work to get the individual packages, but how would automatix help you with that?
As I remember automatix didn't list the individual codec packages but had one checkbox "install multimedia codecs", another "install multimedia players" and one to install libdvdread.
ubuntu-restricted-extras installs what most people used automatix to install (restricted codecs, libdvdread, msttcorefonts, unrar, flash and java). 
The non-free or restricted software that automatix got from different repos are now collected in one repo (medibuntu).

And, the real reason automatix is no longer available is because [the automatix developers decided to stop developing it]("http://www.getautomatix.com/forum/index.php?showtopic=2424"), not because of any decision from the ubuntu developers.

---

### Post by p_quarles on 2008-05-13
No one has denied that a number of people *like* Automatix. That doesn't change the fact that scripts such as Automatix are not supported by Ubuntu or its official support forums.

---

### Post by OzzyFrank on 2008-05-13
[COLOR="DarkRed"]Which part of opening up synaptic, searching for "restricted-extras" and clicking install is harder than googling for "automatix", downloading the correct version from a website (or adding it's repo to sources.list), installing it, running it and browsing through a few different categories, in the end finding "install multimedia codecs" and clicking install?[/COLOR]

What part of all of the above did you not understand? It's all about making things easier, especially for newbies. Would a newbie welcome a "complex" (for them) string of directions more than "Install Automatix"? Methinks not... (once you're in Automatix, it's all pretty self-explanatory what you need to install/enable. As for the hassle of installing Automatix, the site is at the top of a Google search, and their instructions are easy to follow).

As for **ubuntu-restricted-extras**, yes, great, but newbies don't know it exists... and even some users familiar with Ubuntu haven't heard of it... but they've heard of Automatix.

As for Automatix not being "supported", that may be the case, and I am aware the Ubuntu and Automatix teams were nearly at war with each other for some stupid reason, but (for most of us) Automatix worked just fine and didn't cause any problems (for most of us).

I'd gladly strike the word "Automatix" from my vocabulary if either Ubuntu included a similar tool, or there was more mention of the words **ubuntu-restricted-extras** for newbies to come across... like even a popup mentioning the package when one runs a media player for the first time, or whatever.

All I am trying to say here is that - like it or not - Automatix helped bring more new Ubuntu users into the fold, and its absence could mean less terrified newbies do so (no, elitism aside, this is not a good thing, hehe). And while we can try to patiently explain that even Windows doesn't come with all the codecs needed, most expect a degree of functionality regardless, which in this day and age means media playback without a million hassles. Which means in the place of Automatix, there should be an official tool for this task, which would be superior to Automatix. Or even a small script to just install **ubuntu-restricted-extras**?

---

### Post by zvacet on 2008-05-13
I visited Automatix site minutes ago and now I know what are you talking about.Thare is no Automatix for Hardy and EasyUbuntu is not mainteined anymore.Belive me that will not make your life difficult,because you can use [Medibuntu.]("https://help.ubuntu.com/community/Medibuntu") For ubuntu restricted extras I don´t know is there any easier way then described [here.]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by jrib on 2008-05-13
> **OzzyFrank said:**
> For those who see no need for Automatix and can't understand why some people love it, here are some quotes from a blog where the instigator asked others why they bother with it. The misconception being Automatix just grabs stuff already available through Synaptic:

[snip]

... etc.

All of these quotes are still speaking in general terms, with the exception of google earth and skype in the third comment.  We've established that codecs and flash are easily installed in recent ubuntu versions and automatix isn't needed for these anymore in previous posts here.  Now dvd playback, google earth and skype, seem to be things that you claim automatix makes easier to install (ie ubuntu doesn't take care of for you like it does codecs and flash).  Is there anything else?  Be specific please.

---

### Post by mozetti on 2008-05-13
One of the reasons there are a lot of people that aren't big fans of Automatix is because it was the cause of many problems when users ugraded from one release to the next. I can't remember if it was Dapper->Edgy, or Edgy->Feisty (or both?), but the way Automatix installed some of the software basically led to a lot of dead or unusable boxes after the upgrade.

There were additional security, choice, and generally messy problems that came with Automatix, too. One of the Ubuntu devs (i think) wrote a blog post about the problems they saw with Automatix. After reading that litany of issues, I decided not to use it anymore.

In the end, for me, busted boxes after upgrades because of using Automatix is a worse problem than **_searching_** Synaptic for packages you need. And the Ubuntu devs can control how well the OS's own systems work for installing everything you need -- and they did make improvements. With Automatix there was nothing they could really do to improve or repair the user's experience if something didn't work. 

I bolded "searching" in the paragraph above because if you know a general term or two for the package you need, you can find it very easily in Synaptic. In the end, it doesn't really matter because Automatix isn't around any longer. And, the ability to get the things you need has improved from release to release. And finally, lest we forget, you need to install codecs, plugins, and other software packages on every OS. Ubuntu's situation isn't much different than the status quo, so I' don't really understand the, "people don't know what to install for Ubuntu" argument -- they'd need to install all of this for Windows, RedHat, etc and would need to figure it out.

---

### Post by ryanhaigh on 2008-05-13
When do normal users find out that they are missing something?...When whatever they are doing doesn't work, trying to play a movie/music, visiting youtube or a site with java. At this point Ubuntu/Firefox/Totem etc provide advice on what to do. I remember in XP if there were no codecs for a video file media player would tell you it was downloading codecs, but if it was a divx (or whatever other format) encoded file it would just fail and start playing the audio stream. I think it may also have provided a link to a MS help article that explained that you need to install divx the free version of which was, at the time at least, bundled with a player (which of course took over playing everything) and spyware/malware junk. The other solution for 'knowledgeable' user was codec packs which installed every codec ever created often duplicating functionality and often leaving video playback a mess. After all that you still have to install flash and java (which unlike on ubuntu won't update with the rest of the system, instead nagging you constantly and will display a completely useless tray icon)

Once again in ubuntu the casual user tries to do something which doesn't work, ubuntu provides the simplest possible solution allowing them to install a package (or group of packages), the 'knowledgeable' user installs ubuntu-restricted-extras and not only gets codecs but also java, flash and more.

As far as ease of install goes CLICK HERE >>> [ubuntu-restricted-extras](apt://ubuntu-restricted-extras) <<< with your ubuntu supplied firefox browser. I will concede that this doesn't make everything work but thats why this page exists
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by aysiu on 2008-05-13
This is precisely the reason I think new users should start with Linux Mint, PCLinuxOS, or another distro that comes with proprietary codecs preinstalled.

I bought an Eee with Xandros, and everything worked out of the box. It included Skype, multimedia playback, etc.

---

### Post by NIT006.5 on 2008-05-13
> **aysiu said:**
> This is precisely the reason I think new users should start with Linux Mint, PCLinuxOS, or another distro that comes with proprietary codecs preinstalled.

I bought an Eee with Xandros, and everything worked out of the box. It included Skype, multimedia playback, etc.

The only concern I have with this, is that Ubuntu is "supposed" to be "Linux for Human Beings" which should therefore mean that Ubuntu should be the easiest option for new users, in my opinion. 

I can see both sides of the argument. I think half the problem is that the vast majority of users, as someone else said, simply aren't aware that restricted-extras even exists. More to the point, even if they see it in synaptic, they don't know what it does because it's not "obvious" straight away. Yes, the "you need this codec, would you like to install it" thing is valid, except for people like us who live in places like Zimbabwe where MOST of the population don't even know what the Internet is, so quickly downloading the codec, even if its automatic, just isn't an option in many cases. Whereas being able to use automatix one time to install all necessary codecs, means they won't have frustration later when they don't have Internet access. 

Regardless of how it might fit into this argument or not, I have lost count of the number of times I've heard comments like "well I didn't have to install anything extra on Windows but now I can't even open mp3's on this stupid system without downloading things". Whichever way you look at it, comments like that are a fact. The average user wants it to just work. And as stated above, it's fair and fine for most of the world where Internet access is considered a "human right" but it just doesn't apply here where people really do battle to get Internet access. In all other areas, Ubuntu is the first choice in a country like this where "free" means a lot.

---

### Post by LaRoza on 2008-05-13
> **aysiu said:**
> This is precisely the reason I think new users should start with Linux Mint, PCLinuxOS, or another distro that comes with proprietary codecs preinstalled.

I bought an Eee with Xandros, and everything worked out of the box. It included Skype, multimedia playback, etc.

I think the Linux's preinstalled usually have such codecs. If I remember correctly, Dell's Ubuntu systems have at least some codecs that don't come with Ubuntu normally.

> **NIT006.5 said:**
> The only concern I have with this, is that Ubuntu is "supposed" to be "Linux for Human Beings" which should therefore mean that Ubuntu should be the easiest option for new users, in my opinion. 

Regardless of how it might fit into this argument or not, I have lost count of the number of times I've heard comments like "well I didn't have to install anything extra on Windows but now I can't even open mp3's on this stupid system without downloading things". Whichever way you look at it, comments like that are a fact. The average user wants it to just work. And as stated above, it's fair and fine for most of the world where Internet access is considered a "human right" but it just doesn't apply here where people really do battle to get Internet access. In all other areas, Ubuntu is the first choice in a country like this where "free" means a lot.

I can't play my media on Windows without third party tools. I guess open formats are too much to ask for out of the box performance. Interestingly, I use VLC to fulfill the free media formats on Windows, and the proprietary ones on Linux.

---

### Post by aysiu on 2008-05-13
It's usually up to OEMs to make sure things are working. Vanilla Windows XP doesn't include a whole lot by itself. Nor does vanilla Ubuntu.

Dell, for example, provides commercial, legal DVD playback on its Ubuntu computers.

---

### Post by LaRoza on 2008-05-13
> **aysiu said:**
> It's usually up to OEMs to make sure things are working. Vanilla Windows XP doesn't include a whole lot by itself. Nor does vanilla Ubuntu.

Dell, for example, provides commercial, legal DVD playback on its Ubuntu computers.

Ubuntu includes a lot more than XP. Ubuntu has an entire functional office suite, drivers for all sorts of hardware including webcams and printers and enough security features for desktop users. XP comes with nothing useful I have seen. I wouldn't mind, but not having network drivers for common hardware and not having security software is a big minus. 

Now if one could get Vista, MS Office Home and Onecare (or whatever it is called) it may be a fair deal.

---

### Post by gameryoshi600 on 2008-06-11
> **aysiu said:**
> This is precisely the reason I think new users should start with Linux Mint, PCLinuxOS, or another distro that comes with proprietary codecs preinstalled.

I bought an Eee with Xandros, and everything worked out of the box. It included Skype, multimedia playback, etc.
+1
Mint is awesome although Ubuntu is my home and Mint is based on it but Ubuntu is just the way to go. If you want it all spoon fed to you then go for mint.

---

### Post by toucher5 on 2008-08-18
The replacement for Automatix is Ultamatix.

[http://ultamatix.com/#download](http://ultamatix.com/#download)

---

### Post by gjoellee on 2008-08-18
Ultamatix

[http://linux.softpedia.com/progDownload/Ultamatix-Download-24551.html](http://linux.softpedia.com/progDownload/Ultamatix-Download-24551.html)

---

### Post by OzzyFrank on 2008-08-18
Good news! We can now tell the newbies that they'll get far more media opening in Ubuntu that in Windows. In truth, anyone can play more out-of-the-box in Ubuntu than Windows, but people who have been running the same Windows system for years seem to forget Windows Media Player can hardly play anything on a fresh install.

I was happy enough installing what I needed via **Medibuntu** and the **ubuntu-restricted-extras** package, but this will make it so much easier for all of us, not just the newbs. Then they can marvel at all the vid clips they thought were corrupt because they wouldn't play in Windows (even with 3 different codec packs installed). So YAY! to the Ultamatix team! Here is a direct link to the universal installer:

[http://ultamatix.com/download/ultamatix-1.8.0-3_all.deb](http://ultamatix.com/download/ultamatix-1.8.0-3_all.deb)

Cheers

---

### Post by aysiu on 2008-08-18
Linux Mint makes it even easier. No script to run. All the proprietary codecs are preinstalled and set up for you.

---

### Post by picpak on 2008-08-18
> **aysiu said:**
> Linux Mint makes it even easier. No script to run. All the proprietary codecs are preinstalled and set up for you.

But on top of that, it comes bundled with an overwhelming amount of apps and options. My mom uses Ubuntu for Skype, Yahoo Messenger, and Java for Yahoo Games. Sure, with Linux Mint she'd come preinstalled with all three, but with the trouble she has getting around Ubuntu already, would Linux Mint really be worth it?

---

### Post by aysiu on 2008-08-18
> **picpak said:**
> But on top of that, it comes bundled with an overwhelming amount of apps and options. My mom uses Ubuntu for Skype, Yahoo Messenger, and Java for Yahoo Games. Sure, with Linux Mint she'd come preinstalled with all three, but with the trouble she has getting around Ubuntu already, would Linux Mint really be worth it?
Sure. Why would she have more difficulty getting around Mint?

---

### Post by picpak on 2008-08-18
> **aysiu said:**
> Sure. Why would she have more difficulty getting around Mint?

I wasn't sure what a lot of the options did myself, but admittedly, I haven't used it for a long time and it was an XFCE install.

---

### Post by aysiu on 2008-08-18
Mint has different default applications and themes, and a couple of extra utilities, but it's basically still Ubuntu.

If someone is used to getting around Ubuntu, you can install Mint, add in a second panel and change it to the Human theme, and she probably won't know the difference.

---

### Post by Anzan on 2008-08-18
Ultamatix breaks your install by forcing past APT. Unless you never intend to install any updates or any other programs you should avoid it. Or use Mint or such.

---

### Post by picpak on 2008-08-18
> **aysiu said:**
> Mint has different default applications and themes, and a couple of extra utilities, but it's basically still Ubuntu.

If someone is used to getting around Ubuntu, you can install Mint, add in a second panel and change it to the Human theme, and she probably won't know the difference.

One of the things I do for my mom anyway is delete the top panel and put the taskbar at the bottom. So that wouldn't be necessary?

---

### Post by aysiu on 2008-08-18
> **picpak said:**
> One of the things I do for my mom anyway is delete the top panel and put the taskbar at the bottom. So that wouldn't be necessary?
Yeah. Mint defaults to one panel at the bottom *a la* Windows.

---

### Post by picpak on 2008-08-18
> **aysiu said:**
> Yeah. Mint defaults to one panel at the bottom *a la* Windows.

One final question: her computer only has 256MB RAM. It's good enough for her to play a game and talk on Ubuntu, but Linux Mint doesn't have enough to slow it down too much, does it?

---

### Post by aysiu on 2008-08-18
> **picpak said:**
> One final question: her computer only has 256MB RAM. It's good enough for her to play a game and talk on Ubuntu, but Linux Mint doesn't have enough to slow it down too much, does it?
It has a lot of applications that take up space, but I don't think it has any extra services running. I've even seen reports of people having better performance with Mint than Ubuntu in terms of speed and responsiveness (in my experience, they're about the same).

---

### Post by picpak on 2008-08-18
> **aysiu said:**
> It has a lot of applications that take up space, but I don't think it has any extra services running. I've even seen reports of people having better performance with Mint than Ubuntu in terms of speed and responsiveness (in my experience, they're about the same).

My mom isn't much for change, even though she was the one who decided to use Ubuntu. If something ever goes wrong I might give Linux Mint a shot. :guitar:

---

