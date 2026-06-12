---
title: "I am about to give up! Its just so hard."
date: 2014-02-22
forum: New to Ubuntu
---

### Post by blossomrevane on 2014-02-22
Well I thought I was pretty smart but this OS has proved me wrong. I am running 13.10 and am having no luck with anything really. I cant seem to figure the terminal out despite following others exact instructions. What is it that I am missing? For example I am trying to install GCCG [http://gccg.sourceforge.net/](http://gccg.sourceforge.net/) and I follow all the instructions and just well....nothing! What is my problem. Any help would be appreciated, I really like this OS better than windows but cant figure it out.

---

### Post by Bashing-om on 2014-02-22
blossomrevane; Hi ! Welcome to the forum .

Do not be so hard on yourself, It takes time and effort to learn any new operating system !
The install directions look pretty easy, did you, from this
> 
Install SDL, SDL_image, SDL_net, SDL_ttf and SDL_mixer using your distribution's package manager (i.e. apt, yum, yast etc...)

do:
```

sudo apt-get install SDL
sudo apt-get install SDL_image
##and so on ##

```
where apt is 'buntu's package manager and "apt-get" gets the requested package and the option "install" well, installs it. In linux case is sensitive, SDL does not equal sdl. Did you use the proper case ?

If the above completes, how far are you getting before there is a problem. describe in detail, most of us have never encountered the program or the installation procedure. Post back - between code tags - any errors you get. - the complete command/output.

and hey, this is ubuntu
[INDENT][INDENT]all things are possible
[/INDENT][/INDENT]

---

### Post by blossomrevane on 2014-02-22
Well usually I am getting messages that say it cant locate or find package.

blossom@GlaDos:~$ sudo apt-get install SDL
[sudo] password for blossom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package SDL

It seems to do this for most everything that I do.

---

### Post by Vladlenin5000 on 2014-02-22
Please use code tags to post the output -> Go Advanced, click # and paste it inside.

Now, the installation... Let me say you couldn't have picked a worse type of installation. Even some experts will have troubles with this (:P Naah, not really, but it takes a lot of steps - and lots of dependencies - even before you can start compiling the actual software you want). Example: You may have to start with this: [http://askubuntu.com/questions/344512/what-is-the-general-procedure-to-install-development-libraries-in-ubuntu](http://askubuntu.com/questions/344512/what-is-the-general-procedure-to-install-development-libraries-in-ubuntu)

---

### Post by Bashing-om on 2014-02-22
blossomrevane; Well !

That is no fault to you. The package IS NOT available in the 13.10 repository.
> 
sysop@1310mini:~$ sudo apt-get -s install SDL
[sudo] password for sysop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package SDL
sysop@1310mini:~$ 

I also did a "search" of the repository, negative results there too.
You must consult the author of the game console and see what the author advises for a means to obtain the required packages.
If the packages have not been forwarded to ubuntu's repository, then they are not available within the package management system.

It is possible that they "may" be added at a later time, but do not hold your breath. Takes a lot of testing to be admissable to the repository, and it is possible that these packages failed for some reason .

Talk to the author ! They will often make things right.

When all else fails
[INDENT][INDENT]go to the source
[/INDENT][/INDENT]

---

### Post by bab1 on 2014-02-22
> **blossomrevane said:**
> Well usually I am getting messages that say it cant locate or find package.

blossom@GlaDos:~$ sudo apt-get install SDL
[sudo] password for blossom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package SDL

It seems to do this for most everything that I do.

That's because the packages are not named as you see them at the GCCG site.  IF you are not using Synaptic as a GUI package manager I suggest you install it```
sudo apt-get install synaptic
```

Then search for the term.  For example SDL_image  is packaged as* libsdl-image *.  The instructions at the GCCG site are vague at best.

---

### Post by blossomrevane on 2014-02-22
> **Bashing-om said:**
> blossomrevane; Well !

That is no fault to you. The package IS NOT available in the 13.10 repository.

I also did a "search" of the repository, negative results there too.
You must consult the author of the game console and see what the author advises for a means to obtain the required packages.
If the packages have not been forwarded to ubuntu's repository, then they are not available within the package management system.

It is possible that they "may" be added at a later time, but do not hold your breath. Takes a lot of testing to be admissable to the repository, and it is possible that these packages failed for some reason .

Talk to the author ! They will often make things right.

When all else fails[INDENT][INDENT]go to the source
[/INDENT]
[/INDENT]



Well that is good to know I was literally losing it! Although I am having many similar problems with a lot of programs that aren't in the software center.

---

### Post by Vladlenin5000 on 2014-02-22
> **blossomrevane said:**
> Well that is good to know I was literally losing it! Although I am having many similar problems with a lot of programs that aren't in the software center.

Until you feel comfortable avoid anything that has to so with compiling; if possible avoid installing software that isn't in the Software Center.
However, if you really can't go without a given software and you're aware of the increased risks then using a PPA if available is quite easy. Usually with just 3 commands ```
sudo apt-add-repository ppa:softwareimcravingfor/andimnotalone
sudo apt-get update
sudo apt-get install mybelovedsoftware
```

Any other specific software giving you headaches? Feel free to post here. Chances are that someone already gone that same road and might have an easier solution.

---

### Post by Bashing-om on 2014-02-23
blossomrevane; Hey,

What others are you having problems with ? If you are attempting to duplicate Windows programs in linux, you will have a bit of a problem, there are some that there just are no alternatives.

To install applications in ubuntu, the repository is always the 1st source, then a trusted PPA (Personal Package Archive), and then there is from source.Many of the most used applications in the software world are available in the repository, 43,000+ are there at the click of a button . 
To install from source does entail a fairly deep understanding of the operating system as a whole, now-a-days it is a rarity to have to resort to having to do so. 

But, it is open source
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by blossomrevane on 2014-02-23
> **Vladlenin5000 said:**
> Until you feel comfortable avoid anything that has to so with compiling; if possible avoid installing software that isn't in the Software Center.
However, if you really can't go without a given software and you're aware of the increased risks then using a PPA if available is quite easy. Usually with just 3 commands ```
sudo apt-add-repository ppa:softwareimcravingfor/andimnotalone
sudo apt-get update
sudo apt-get install mybelovedsoftware
```

Any other specific software giving you headaches? Feel free to post here. Chances are that someone already gone that same road and might have an easier solution.

I am going to take your advice =) By the way Hitchens is the greatest R.I.P.

I am not going to give up on linux I actually love it! But wow its making me feel so dumb lol.

---

### Post by Bill Tetzeli on 2014-02-23
Most Linux programs not in Ubuntu's Software Center can be found by going to [http://www.launchpad.net](http://www.launchpad.net) and doing a search for the given program you're looking for.  If a program can be downloaded and installed from a package repository the instructions will be on it's Launchpad page; e.g., [here's the one for Variety]("https://launchpad.net/variety"), an app that automatically downloads and rotates wallpapers from various sites.

If there's no package repository, and there doesn't seem to be one for this particular program, you can usually download the .deb installation file (works similarly to an .exe installation file in Windows - just double-click on it and it will run automatically in either Software Center or GDebi Package Installer.  Think of them just like Windows Installer, except with bigger windows and more options. :-)).  You may be in luck, since there do seem to be .deb files on [SDL's Launchpad page]("https://launchpad.net/ubuntu/+source/sdl-image1.2").

---

### Post by Vladlenin5000 on 2014-02-23
> **blossomrevane said:**
> I am going to take your advice =) By the way Hitchens is the greatest R.I.P.

Yeah :(
We'll have to wait for a very long time until someone like him pops up again.


> I am not going to give up on linux I actually love it! But wow its making me feel so dumb lol.

Been there, done that... Back in the 90's I was a Windows power user, later a Windows server network & systems admin, and I still remember that first contact I had with Linux - a magazine with a Mandrake CD in my favorite newsstand... "Weirdness" comes close but doesn't sufficiently describes the feelings I had. It wasn't until 2006/7 that I started to really use it but soon after I ditched Windows for good, not even dual-boot. As soon as I managed to have a few games I wanted running acceptably (thank Crossover) I deleted that bloated NTFS partition and used the space for something useful instead. It has been a rewarding experience.

Occasionally I still use Windows at work now I can't help but feel weird whenever I use Windows, thinking "this is quite similar to the videogames "console" I used years ago" :lolflag:

---

### Post by Buenadriver on 2014-02-25
I (another nube) found out that 12.04 is a lot simpler to figure out. Also not all new installs are created equal. I downloaded 12.04 to 2 seperate disks before I got most of the stuff working. I hope I don't discourage you but think about a whole new install with 12.04. When options came up on the install I chose delete everything and install fresh. If I can be of any further help let me know.

---

### Post by mastablasta on 2014-02-25
> **Bashing-om said:**
> Many of the most used applications in the software world are available in the repository, 43,000+ are there at the click of a button . 


unfortunatelly that's the number of packages not applications. the number of applicaitons on default install is closer to about 1800 i believe. i think Muon shows hwo many programs there are available. probably software cneter show it as well. it's not 40.000 unfortunatelly.

---

### Post by squakie on 2014-02-25
As far as the "weirdness factor", back in the mid-80's we had a unix coprocessor installed in one of our mainframes that of course nobody in support new squat about.  It came with this set of unix manuals that had the same dang expression/command listed under like 5 sections across these manuals - I was going nuts.  I called national tech support and said "this stuff is really strange", and he said "You know where it came from, don't you?  A bunch of guys sitting around in their tie-dyeds and cutt-offs, eating a tomatio in the middle of the night and going 'Wow - look what I made it do!'".  So don't feel bad.  Things have gotten much better.  I first started with Linux about 1996 or so with Slackware.   To say it was "interesting" would be an understatement, but I was also still working then so the "technical" part of my brain was up to snuff and got it all figured out, had several PC's with it running networked, etc..  But it was the "hard" way.  Believe it or not, so much has changed that it is unbelievable.  Ubuntu is probably the easiest and most supported Linux distribution there currently is.  Easy?  No, especially for anyone coming from Windows, as it's a completely different animal.  Can you learn it?  SURE!!  At first it seems so overwhelming that you feel as dumb as a box of rocks.  With time it gets better.  Reading threads on the forums, even if you don't have the problem, can be very educational.  I've been doing this a lot of years, but unfortunately for me my days as a systems programmer and systems adaministrator on "big iron" gets in the way and I do some pretty stupid things.  I still asks so many questions that I'm sure a lot of people on the forum wonder just what the heck is up with me.  But you know - it's a hobby now, not work (I'm on disability), so I really don't care how dumb I look.  For me sometimes it's just a difference in terminology that throws me.  Other times it's just that things are different from the "old" days.

Don't give up, and don't feel stupid!!!  Some people misuse the word, but there is such a thing as ignorance:  if you haven't been exposed to it or had a chance to slowly build up knowledge, it doesn't mean you're stupid.  In fact, you're showing some smarts by coming to the forum and asking for help!  Don't be afraid to do so on anything!

---

### Post by Buenadriver on 2014-02-25
Amen, oh yeah, love that cat.

---

