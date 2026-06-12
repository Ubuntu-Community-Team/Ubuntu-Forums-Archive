---
title: "UbuntuPlus - Addon CD for Multimedia, Firefox 1.5, and much more"
date: 2006-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by CompShrink on 2006-05-29
Hello! I am here to announce the first release of [UbuntuPlus]("https://ubuntuplus.bountysource.com/").

The main focus of the project is creating a CD for users who have slow/no internet on their Ubuntu computer, and want to install upgrades and commonly used extras, like media playback, language support, etc. Of course, users who reinstall frequently may find it useful as well.

This is mostly updates since Breezy/Dapper's release, along with a few unique items, like an MPlayer built with extra codecs, Firefox 1.5 upgrade (Breezy), Thunderbird 1.5 upgrade(Breezy), transmission (a bittorrent client similar in feel to utorrent for Windows), and more.

KDE users, see note at the bottom, this is aimed at Gnome.

You can either get the CD or add it to Synaptic/apt-get/aptitude.
**Dapper:**
[Dapper 6.06 CD]("http://www.tikal26.net/ubuntu/ubuntuplus-dapper_2006-06-07.iso")
MD5: 76012973ca89b41ee2941fbcf98aa47a
once you burn the CD and put it in your drive, open Synaptic and go to Edit -> Add CD-Rom...
This is also [mirrored here]("https://files.bountysource.com/file/download/243/ubuntuplus-dapper_2006-06-07.iso"), so if the above link doesn't work, give that a try.

Dapper Repository, add this to your /etc/apt/sources.list file:
deb [http://www.tikal26.net/ubuntu/apt](http://www.tikal26.net/ubuntu/apt) dapper main

**Breezy:**
[Breezy CD 5.10]("http://www.tikal26.net/ubuntu/ubuntuplus2006-05-30.iso")
once you burn the CD and put it in your drive, open Synaptic and go to Edit -> Add CD-Rom...

Add a repository:
Open /etc/apt/sources.list AS ROOT (or sudo) in your favorite text editor, and add the line:
 deb [http://www.tikal26.net/ubuntu/apt](http://www.tikal26.net/ubuntu/apt) breezy main


Then, you can search for "ubuntuplus" in Synaptic to find meta-packages which will install media, internet, utilities, etc.

Also, hit "Mark All Upgrades", or use the Update-Manager icon (red and white, with a little green exclamation mark) to install all the updates.


This is a result of:
[http://ubuntuforums.org/showthread.php?t=136955](http://ubuntuforums.org/showthread.php?t=136955) **but the CD linked to there is older and is not organized, and does not have firefox 1.5** on it.

The Breezy version will also be maintained for... some period. I don't see a reason why it would stop being maintained soon.

Also, it is currently only in i386, but I am working on getting PPC and AMD64 versions made. If anyone has PPC or AMD64 Ubuntu and can make a 5 gb partition to work on this, I would love the help! It's really simple, and I can step anyone through the process.

I would also like to make some documention for what is on the CD, how to use it, get a logo perhaps, etc. I'd appriciate any volunteers for that as well.

In the mean time, enjoy this release, and comments/suggestions/complaints are welcome!

Oh, and no, win32codecs, libdvdcss won't be included. They are illegal in several countries, and don't have dependancies, they are easy to install seperately and well documented.

*** For KDE users:
Just type in a terminal:
```
apt-cdrom add
```
Assuming you inserted the CD into your "main" cdrom drive (the one /CDROM/ points to), that will add the UbuntuPlus CD, and you can use whatever you normally use to manage official Ubuntu Deb package installation.

Still note that is was made with a standard (Gnome) Ubuntu install in mind. You may have to download Gnome libraries to get it working on a fresh Kubuntu install. I hope to make a Kubuntu version when I get a chance. Volunteers to help welcome.

---

### Post by vinodis on 2006-06-05
Will this work on Dapper?.
TIA.

---

### Post by CompShrink on 2006-06-05
No, it won't work on Dapper yet, but I should have a version by tomorrow that works for Dapper.

I could send you what I have now if you wouldn't mind helping me test it.

---

### Post by vinodis on 2006-06-06
Sure. I am more than willing. :)

Would you Please consider the following software too on the CD:-
1) MONO
2) FF 1.5.0.4
3) F-SPOT
4) KOffice 1.5.1
5) KDE 3.5.3
6) Amarok 1.4
7) Eclipse
8 ) JDK 1.5 Update 7

---

### Post by CompShrink on 2006-06-06
F-Spot is already included.

Dapper already has Firefox 1.5.0.3, and assuming 1.5.0.4 is only a bug fix, it should be in Dapper in a couple days. If not, I may add it. What changes are there from 1.5.0.3 to 1.5.0.4?

MONO is not a commonly needed package, if you can show me otherwise, I would be happy to include it. Eclipse likewise, commonly used for programmers, but not for everyone. 

As this is mainly for low speed internet (and no internet) installations, so I want to keep the size of the CD down. I am working on making an easy way to add your own programs onto the cd, and then you could add less commonly used packages like that yourself.

Amarok in installed by Kubuntu, if I recall.
KDE is included in Kubuntu.
KOffice requires KDE installed, making it take a lot more space. Right now the CD is Gnome focused, but I may work on that. Isn't KOffice part of Kubuntu anyway?

Sun's Java is not re-distributable. Although you can download it freely, the official Ubuntu package only downloads it off SUN's website due to the legal restriction. Therefore it's useless to put it on the CD, you still need internet access.

More comments/suggestions are very welcome! 

**Is anyone using the Breezy version, or would use the Dapper version?**

---

### Post by vinodis on 2006-06-06
[QUOTE=CompShrink]
F-Spot is already included.
Ok. Thanks.
---------------------
Dapper already has Firefox 1.5.0.3, and assuming 1.5.0.4 is only a bug fix, it should be in Dapper in a couple days. If not, I may add it. What changes are there from 1.5.0.3 to 1.5.0.4?

[COLOR="Orange"]Here's what's new in Firefox 1.0.5:

    * Several security fixes.
    * Improvements to stability.[/COLOR]
------------------------


MONO is not a commonly needed package, if you can show me otherwise, I would be happy to include it. Eclipse likewise, commonly used for programmers, but not for everyone. 

[COLOR="Orange"]Beagle needs Mono. And rumor would have it that GNOME is moving to Mono.
Eclipse is mainly targeted towards Programmers. I am one. May be many more. But not definitely for many. The call is surely yours.[/COLOR]
-----------------------

As this is mainly for low speed internet (and no internet) installations, so I want to keep the size of the CD down. I am working on making an easy way to add your own programs onto the cd, and then you could add less commonly used packages like that yourself.

[COLOR="Orange"]How will it look like?[/COLOR]

----------
Amarok in installed by Kubuntu, if I recall.
But Its not the latest version.

KDE is included in Kubuntu.
KOffice requires KDE installed, making it take a lot more space. Right now the CD is Gnome focused, but I may work on that. Isn't KOffice part of Kubuntu anyway?
[COLOR="Orange"]I couldnt see KOffice anywhere on Kubuntu. It defaults to OpenOffice just like Gnome.[/COLOR]

----------------------------

Sun's Java is not re-distributable. Although you can download it freely, the official Ubuntu package only downloads it off SUN's website due to the legal restriction. Therefore it's useless to put it on the CD, you still need internet access.

[COLOR="Orange"]I can see JDK 1.5 U7 [here]("http://sdlc-esd.sun.com/ESD24/JSCDL/jdk/1.5.0_07/jdk-1_5_0_07-linux-i586.bin?AuthParam=1149499494_4bfc1f34d9ea5f169cc70b5c22a69e85&TUrl=an1npDpbKod7kSYrROhENTonIeU1W0D1Lc4nXz+pGFFranixdCdgxDTPbW4=&TicketId=dld9OQVGMeo++w==&GroupName=SDLC&BHost=sdlc5i.sun.com&FilePath=/ESD24/JSCDL/jdk/1.5.0_07/jdk-1_5_0_07-linux-i586.bin&File=jdk-1_5_0_07-linux-i586.bin").[/COLOR]


More comments/suggestions are very welcome! 
[COLOR="Orange"]Is gStreamer broken on Dapper Ubuntu?
Can we have Banshee and Tomboy too?
Can you include an offline dictionary for linux?
Can you include Wine ( or is it already there?)
Would you pleas include Media Codecs? ( most required )
[/COLOR]

**Is anyone using the Breezy version, or would use the Dapper version?**[/QUOTE]
[COLOR="Orange"]I think most have moved over to Dapper now.[/COLOR]

TIA

---

### Post by CompShrink on 2006-06-06
[QUOTE=vinodis]
> Amarok in installed by Kubuntu, if I recall.
But Its not the latest version.

> Sun's Java is not re-distributable. Although you can download it freely, the official Ubuntu package only downloads it off SUN's website due to the legal restriction. Therefore it's useless to put it on the CD, you still need internet access.

I can see JDK 1.5 U7 here.


More comments/suggestions are very welcome!
Is gStreamer broken on Dapper Ubuntu?
Can we have Banshee and Tomboy too?
Can you include an offline dictionary for linux?
Can you include Wine ( or is it already there?)
Would you pleas include Media Codecs? ( most required )
TIA[/QUOTE]

Amarok:
Like Firefox, what are the improvements you desire?

JAVA:
Yes, but the SUN licence agreement states that you may download it for personal use, but it is not redistributable. What that means, is I can't legally put it on my CD. Yes it's stupid since you can download it for yourself freely, but it's the law.

From my understanding gStreamer 0.10 is fine, and extra codecs are included, along with mplayer and vlc as alternative media players. I did not include w32codecs again due to legal issues, but it's one small file with no dependancies, easy to install seperately if needed. Considering the codecs I did include, you probably don't need it anyway.

I don't know of any good offline dictionaries, any suggestions? That does sound like a good idea! 

Tomboy looks interesting, and is small. I'll consider it.

I think rhythmbox is fine, banshe is just another option. That's why I'm working on allowing people to add their own packages.

Wine is included. Beagle is included, so I just checked and you're right mono is included, but only the libraries, not the programming tools.

---

### Post by CybaCowboy on 2006-06-06
How about:
* Adobe Reader - essential in *any* operating system!
* Gmail Notify - runs in the background & lets you know when you have new mail...
* J-Pilot - Sync your Palm Pilot with Ubuntu!
* Opera - The fastest & most secure internet browser!
* Thunderbird - An extremely well-made alternative to Evolution (Mail)...

---

### Post by CompShrink on 2006-06-06
Adobe reader (acrobat) is already included, along with thunderbird. I have a PDA too, but they aren't a common thing, sadly, so again something not everyone needs. 

Opera, an option compared to Firefox, and frankly, Opera can't compare to Firefox's extentions for versatility. And the GUI is ugly(boxy), and not gnome-ified at all.

I'll probably add gmail-notify.

---

### Post by sharperguy on 2006-06-06
Someone needs to write a program in which allows you to download packages and their depencancies to a disk of portable drive.

A list of their current setup could be stored on floppy or other re-writeable medium so that they only get the packeges they need.

It would have to ported to as many os's as possible but I think it would be a more popular alternitive to installing only what other people belive to be important software.

And yes, its a PAIN about the non free software.

---

### Post by CompShrink on 2006-06-06
I agree. See the link in the first post, we went through a long thread discussing what should go on this CD, and now that we're moving on to Dapper I'm updating it, by myself, as sadly that previous thread is dead. We tried to have a general consensus on what should be added, but it still won't work for everyone.

Ultimately, having an easy way to edit the CD is a very useful, but there will be many novice users who could use a CD with some pre-selected basic extras on it. The best thing would be easy adjusting of what's on the CD, but for now I'd like to get a good initial Dapper CD, and then I will work on creating the editing ability.

---

### Post by rcarring on 2006-06-06
Um, what exactly is the point behind the ubuntuplus cd given that enabling all the repositories on Ubuntu gives you access to over 18000 packages, including many of the items you describe on your cd? I can only imagine it is for people on slow internet connections or those with no network.

I think your idea is commendable if it helps new users.

That said, I would hate to be a user reliant on a third party prepared cd or repository.

Just my two cents.

---

### Post by aysiu on 2006-06-06
[QUOTE=rcarring]I can only imagine it is for people on slow internet connections or those with no network.[/QUOTE] You imagine correctly--that's exactly the target audience.

---

### Post by CompShrink on 2006-06-06
Yes it is mainly aimed at dialup users and those with no internet on the target system. I ment to say that in the first post, now I see I forgot, thank you.

There are also a lot of people who reinstall frequently, and don't like redownloading the same debs every time, and trying to remember what they have to search for and mark. I'm one, and I've heard others say this too.

---

### Post by rcarring on 2006-06-07
Excellent idea.

Hope that you manage to roll out the plus cd soon =D

---

### Post by Chickenmonger on 2006-06-07
Now, of course, if you want -everything- downloaded for offline use, you could use this guide, replacing breezy with dapper:

[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)

I was about to try it, using an rsync mirror instead, but I realized that dapper's main, universe, and multiverse repositories added up to a little under 12 GB. 

Then I found this project, and figured it might work for my purposes.

---

### Post by vinodis on 2006-06-07
But those DVDs represent the entire repositories. Download size is too high. What would be interesting is something the size of a CD (like UbuntuPlus CD).

---

### Post by bettermentflux on 2006-06-07
I have a computer with ONLY wireless access and a wireless card that doesn't work out of the box. 

A few clear html how-to docs taken from these forums bundled with copies of fwcutter, ndiswrapper-utils, ndisgtk and build essentials would be great.

Edit - plus any dependencies for the above that aren't installed with a base system.

---

### Post by vinodis on 2006-06-07
[QUOTE=bettermentflux]I have a computer with ONLY wireless access and a wireless card that doesn't work out of the box. 

A few clear html how-to docs taken from these forums bundled with copies of fwcutter, ndiswrapper-utils, ndisgtk and build essentials would be great.

Edit - plus any dependencies for the above that aren't installed with a base system.[/QUOTE]

of these - the 'build essentials' are for sure there on the install CD - fully.
Do this after inserting the install CD :-
sudo -install build-essentials

---

### Post by CompShrink on 2006-06-07
I was about to mention that, build-essentials are on the default CD.

And yes, all the ndis stuff is included on the CD.

And it's:

sudo apt-get install build-essentials

you forgot to type the apt-get, which a little important.

I should release the first Dapper version ofthe CD in a couple hours, I would very much appriciate any feedback on it.

---

### Post by CompShrink on 2006-06-07
[Dapper 6.06 CD released]("http://www.tikal26.net/ubuntu/ubuntuplus-dapper_2006-06-07.iso")
once you burn the CD and put it in your drive, open Synaptic and go to Edit -> Add CD-Rom...

Dapper Repository, add this to your /etc/apt/sources.list file:
deb [http://www.tikal26.net/ubuntu/apt](http://www.tikal26.net/ubuntu/apt) dapper main

Then, you can search for "ubuntuplus" in Synaptic to find meta-packages which will install media, internet, utilities, etc.

Also, hit "Mark All Upgrades", or use the Update-Manager icon (orange with a white * in the middle) to install all the updates.

---

### Post by Impsy on 2006-06-07
Yes! im downloading it right now, ill tell you how it goes afterwords.

---

### Post by Impsy on 2006-06-07
(USING XUBUNTU) wow i got a huge error after trying to add the cd....

E:Sub-process gpgv returned an error code (2). W:signture verification failed for : cdrom/disks/dapper/release.gpg


can someone help me out?

---

### Post by CompShrink on 2006-06-07
Not a huge error, sorry I should have mentioned adding the key.

You haven't added my gpg public key yet, so the CD isn't considered "trusted" by apt yet.

Simply open up a terminal and put in:
```
apt-key add /cdrom/public.key
```

After that you won't get that warning.

Search for "ubuntuplus" (without " " of course) in Synaptic or Aptitude to find meta bundle packages... I'll post a better explanation of how to use the CD soon.

---

### Post by Impsy on 2006-06-07
when i use that line in the terminal i get this.

gpg: no writable keyring found:eof
gpg: error reading '/cdrom/public.key  general error
gpg: imprt from '/cdrom/publickey.key' failed

wow what is this :P

---

### Post by AndyAWS on 2006-06-07
I cannot seem to get the public.key from your repo to work.

Also libdivxdecore0 and libdivxencore0 will not install from the repo ..

```
W: Failed to fetch http://www.tikal26.net/ubuntu/apt/dists/dapper/main/binary-i386/external/libdivxdecore0_1-0x1.318aa08bd8c9ap-55.0.1-1_i386.deb
  404 Not Found


W: Failed to fetch http://www.tikal26.net/ubuntu/apt/dists/dapper/main/binary-i386/external/libdivxencore0_1-0x1.318aa08bd8c9ap-55.0.1-1_i386.deb
  404 Not Found
```

---

### Post by CompShrink on 2006-06-07
[QUOTE=AndyAWS]I cannot seem to get the public.key from your repo to work.

Also libdivxdecore0 and libdivxencore0 will not install from the repo ..

```
W: Failed to fetch http://www.tikal26.net/ubuntu/apt/dists/dapper/main/binary-i386/external/libdivxdecore0_1-0x1.318aa08bd8c9ap-55.0.1-1_i386.deb
  404 Not Found


W: Failed to fetch http://www.tikal26.net/ubuntu/apt/dists/dapper/main/binary-i386/external/libdivxencore0_1-0x1.318aa08bd8c9ap-55.0.1-1_i386.deb
  404 Not Found
```[/QUOTE]
I will look into the key. It will give you a warning about installing unauthenticated packages, but you can still install.

I am not on my own machine right now, but I will re-upload those packages asap, probably in 2 or 3 hours.

I installed from the CD myself, it should have those 2 files missing on the ftp, and install fine, even despite the key issue.

---

### Post by Impsy on 2006-06-08
can you please read my last post and help me out, thanks.

---

### Post by CompShrink on 2006-06-08
Ok, lmpsy, the first line of my last post was for both you and AndyAWS, it still works without the key, you just have to click through the warnings.

I just tried adding the public key with the command I posted, it worked, but you can also try the following:

Open Synaptic: System > Administration > Synaptic Package Manager
menu: Settings > Repositories
"Athentication" tab
"Import Key File" button
browse to the CD, the public.key file is on base of the CD.

And AndyAWS, as for the two divx packages, I fixed that. Apparently the FTP didn't like me having a % in the deb name of those two, I just checked and it works now. And the key on the FTP was my old key, so opps, sorry. The correct one is up now.

The CD works fine even with the old names for divx, and it had the correct security key already, so the CD is fine.

---

### Post by vinodis on 2006-06-08
CompShrink !! Thank you soo much. I'm downloading the CD Now. Will report tomorrow.

---

### Post by ivago on 2006-06-11
excellent idea, just installed the CD on a dial-up box and it worked like a charm... also the ndisgtk is a great feature wich will help alot of users to get started... btw if you would get into problem with the bandwith I can provide a host for the file.

---

### Post by CompShrink on 2006-06-11
Thanks, I'll keep that in mind.

Actually, might not hurt to have a backup mirror incase the current host goes down, I'll send you a PM.

Anyone else actually install it and have some feedback? Wish it had x, glad it had y... or just to let me know more than 2 people used it...

---

### Post by vinodis on 2006-06-12
I installed it successfully on my dapper!. Thank you. But some of the problems as documented earlier popped up. One was that the CD does not have a label ( i burned it using k3b) but you can enter the value as 'UbuntuPlus'. Next was the public key problem. The apt-key command did not work for me. But fortunately the Synaptic settings options to import a public key worked.

I found Tomboy not been installed by default. You have to manually install it. 
I feel like having a complete system now!. Except that I am not able to read my .chm ( eBooks & Windows Help files).  I wish UbuntuPlus had the xChm or gnome CHM readers in it!

I gave the CD to my friend but he reported that when he selected UbuntuPlus filter and installed the internet,multimedia etc.. packages through synaptic, it failed at some point saying ' post processing command failed'. But it succeeded for him after he did the 'Update' button.

I thought I saw KDE/GNOME extra themes in UbuntuPlus CD, Are they installed by default or do I need to install  manually?

If you are thinking about updating the current CD, it would be great to have the following too:-

1) a CD/DVD ripper
2) an offline thesaurus/dictionary application
3) Gnochm / xCHM
4) GnuCash
5) Latest Ubuntu Dapper Updates.


Thanks a ton for your efforts!
:)

---

### Post by CompShrink on 2006-06-12
I always include the latest updates.

I would love to include an offline thesaurus/dictionary application. The only one I can find is really old, the word list was last updated in the 1940s. I suppose that's better than nothing though... I'll consider it.

Hm... how often are chm's actually read? Other than MS Windows help, which I doubt all that many would be reading on linux.

Ubuntu comes with a CD ripper. A DVD ripper would be rather useless without decss, which is illegal in many countries and will not be included on the UbuntuPlus Addon CD.

GnuCash sounds good, I'll add it to the next one.

---

### Post by vinodis on 2006-06-12
Thanks for the prompt response.
Most of the technical ebooks which I have is in the .chm format.

I found a way to have an offline dictionary in Ubuntu - but rather using Wine.
The wordweb can be installed and used using Wine.
Ok.. let me add one more to the wishlist counter..! Banshee.

---

### Post by kriding on 2006-06-12
I'm downloading it now, but it will be about a week before I can try it:-(

---

### Post by xfile087 on 2006-06-12
Great job all!!

The ISO won't download though, which is a bit of a shame.

---

### Post by CompShrink on 2006-06-12
[QUOTE=xfile087]Great job all!!

The ISO won't download though, which is a bit of a shame.[/QUOTE]
Can you tell me what error you get?

I just tried both the Breezy and Dapper links on the first post in this thread, and they both start downloading for me...

---

### Post by vinodis on 2006-06-12
Me too checked now..
Links are working GOOD.

---

### Post by xfile087 on 2006-06-12
[QUOTE=CompShrink]Can you tell me what error you get?

I just tried both the Breezy and Dapper links on the first post in this thread, and they both start downloading for me...[/QUOTE]

I think it must of been  my ISP (it plays up sometimes) because it seems to be working now. Thanks for testing people!

---

### Post by stimpsonjcat on 2006-06-12
nice job! will there be a PPC version for all the poor mac users who can't afford broadband?

---

### Post by macias on 2006-06-12
CompShrink, I have to say it is excellent idea and I was looking for something just like UbuntuPlus. However, I think that reasons of including/excluding particular programs are questionable (of course, you are the maintainer, not me) -- Opera for not looking good or chm viewer for not being used too often? I read PS, chm and pdf files all the time -- for me it is every day tool.
  Similar thing with Opera -- it is a really good browser. 

  And just to add my 2 cents, if anybody is curious -- I would like to see EverythingInOnePlace add-on :-) Really. I better download 7GB or anything like this, burn several CDs, but then I could sit and work at my computer being sure that some tiny, but useful program is on the disc.

That's all from me, thank you for your work!

---

### Post by CompShrink on 2006-06-13
As much as I would like to include eveything, one main aim of this disc is for people who have dialup internet, or limited bandwidth (such as some developing countries) can download the CD once, and have the most useful programs, which can be reinstalled whenever without redownloading.

But, along with that, the initial download time needs to be taken into account. Therefore, duplicate programs should be avoided when possibly, say Opera. I cannot claim to be unbiased, and perhaps I shouldn't have made that remark. But as I mentioned, there are several reasons why Opera is not used.

I will consider CHM support. It is not as commonly used, to my knowledge, as other things on the CD, such as media codecs, flash, news reader, etc. WHich is why I am reluctant to increase the scope of the CD.

There are way more useful programs in Ubuntu than will fit on one more CD. I would like to keep it as small as possible while maintaining the most commonly used packages, hopefully well under the size of a full CD.

It still needs some work, but in a few days I should be releasing a program to create your own CD full of deb installers. I already have the basic functionality, but I'd like to polish it a bit more. 

At the moment, you need to run it on an Ubuntu Dapper install to pick the packages you want, and it creates downloading scripts (which also download all dependancies) which you can run on Windows, Mac OS X, or Linux. Then you bring the single archive file from whereever you ran the download script (Win,Mac,Lin) back to your Ubuntu install, and rerun the program, and it will create a CD, and offer to install everything you downloaded.

If anyone's willing to test it out, I could get them a copy in a day or less. I would really appriciate it.

As for PPC support, if you want it, could you help me with it? I don't have a Mac to work with. I can tell you how to make it, and it shouldn't be too difficult, in my opinion.

---

### Post by macias on 2006-06-13
[QUOTE=CompShrink]As much as I would like to include eveything, one main aim of this disc is for people who have dialup internet, or limited bandwidth (such as some developing countries) can download the CD once, and have the most useful programs, which can be reinstalled whenever without redownloading.
[/QUOTE]

The most common situation around me (and me too) is slow connection at home but very fast connection at work. So the most wanted scenario looks like that you go to work to download several GB at night, you get back next day, burn the data, go home and... hurray, you don't need to get all those programs from home.


[QUOTE=CompShrink]I will consider CHM support. It is not as commonly used, to my knowledge, as other things on the CD, such as media codecs, flash, news reader, etc.
[/QUOTE]

I agree, on the other hand it is _popular_, not as the other tools, but it is popular.

[QUOTE=CompShrink]
At the moment, you need to run it on an Ubuntu Dapper install to pick the packages you want, and it creates downloading scripts (which also download all dependancies) which you can run on Windows, Mac OS X, or Linux. Then you bring the single archive file from whereever you ran the download script (Win,Mac,Lin) back to your Ubuntu install, and rerun the program, and it will create a CD, and offer to install everything you downloaded.

If anyone's willing to test it out, I could get them a copy in a day or less. I would really appriciate it.

As for PPC support, if you want it, could you help me with it? I don't have a Mac to work with. I can tell you how to make it, and it shouldn't be too difficult, in my opinion.[/QUOTE]

Looks really great, that's want I need. I would like to download everything for Ubuntu (SuSE platform), prepare the disc, and get home and install it on my Ubuntu machine.

Unfortunately I can't help you with PPC, x86 only.

thanks again, bye

---

### Post by muzakman on 2006-06-13
CompShrink, cheers and long life to you. Exactly what I needed and more. Thanks.

---

### Post by vinodis on 2006-06-14
>  At the moment, you need to run it on an Ubuntu Dapper install to pick the packages you want, and it creates downloading scripts (which also download all dependancies) which you can run on Windows, Mac OS X, or Linux. Then you bring the single archive file from whereever you ran the download script (Win,Mac,Lin) back to your Ubuntu install, and rerun the program, and it will create a CD, and offer to install everything you downloaded.

If anyone's willing to test it out, I could get them a copy in a day or less. I would really appriciate it. 

I am ready to volunteer.

---

### Post by georgevn on 2006-06-14
Can you list all the packages you have in the ubuntuplus cd? i think that piece of information is needed here and on your site.

---

### Post by CompShrink on 2006-06-16
I was hoping to get a bit more done first, but I have to put developement of the script on hold for a little over a week. During that time, I might not be able to view this thread very often.

Feel free to continue posting comments and suggestions, but other than perhaps simple updates or fixes to the Breezy and Dapper Addon CDs, there will be no new work on the project for about a week.

Thanks for everyone's support, and look for some new developements within 2 weeks from this post.

---

### Post by vinodis on 2006-06-29
any updates?!

---

### Post by ccc1 on 2006-07-01
first of all thanks for the addon, saved me a lot of work.

two bugs i encountered:

.) ati fglrx driver is missing

.) tranmission doesn't work -> complained about that libcrypto is missing.

ccc1

---

### Post by vitesse on 2006-07-05
CompShrink you have done an amazing job here!

Today I installed 3 ubuntu boxes thanks to your ubuntuplus cd. People was amaze with the power of ubuntu. In less than 1 hour 3 working ubuntu boxes w/o internet! :D

About the chm reader, I want it too. :D

Other aplications needed are (IMHO):

k3b
bluefish
inkscape
scribus

Thankyou again for your hard work :D

Peace!

---

### Post by adam.tropics on 2006-07-06
Ok, so if you look up your isp, you may find that they have a file server that DOES NOT affect your monthly download limit, and is very fast. So for all you Australians on Bigpond, you can get this [HERE ]("http://files.bigpond.com/library/?go=details&id=23335"), and it will not show up on your download level. For everyone else, check your ISP, they often have special rules applying to Linux, take advantage of them. (You just fill a form and put in a request, they do the rest!)

---

### Post by CompShrink on 2006-07-07
Sorry for the lack of updates for longer than I expected.

It looks like chm is more needed than I had thought, it will be included.

Inkscape I should have thought of as well, I will be sure to add that to the next release.

I will look into bluefish and scribus.

K3B requires a bunch of the KDE libraries last I checked... and since this is focused on Gnome at the moment (I'd like to address that as well when I get the time) it adds quite a bit more size to the disc. I will consider it  however, you're right something beyond dapper/breezy's built in CD burning should be added.

And thanks adam.tropics, that's very interesting info.

---

### Post by aysiu on 2006-07-07
CompShrink, I just want to thank you for really sustaining this project. I stink at making add-on CDs, but you've got it down!

---

### Post by vitesse on 2006-07-07
CompShrink, right something to burning cd/dvd is needed specially to burn more UbuntuPlus CDs.

One think I notice, when playing movies with VLC i'm having some problems to display subtitles. When I load a sub.(pack with subtitles, with more than one language stream) file I can't see the letters. Maybe is something with VLC because with Mplayer everything is fine.

---

### Post by justask on 2006-07-08
What's the md5sum of the ubuntuplus-dapper_2006-06-07.iso please?

---

### Post by picallo on 2006-07-08
Im using Kubuntu, but i have no clue how to add the CD as repository and then install the packages. Can somebody explain it? because im losing my mind.

---

### Post by CompShrink on 2006-07-08
Just type in a terminal:
```
apt-cdrom add
```
Assuming you inserted the CD into your "main" cdrom drive (the one /CDROM/ points to), that will add the UbuntuPlus CD, and you can use whatever you normally use to manage official Ubuntu Deb package installation.

Sorry about that, I will add that to the first post. Also, this is a Gnome focused CD, so you may need to download some extra Gnome libraries if you don't have them already. A fresh Kubuntu install won't work with this CD, as far as I know.

---

### Post by picallo on 2006-07-08
so then which files should i install before??

---

### Post by glenn45 on 2006-07-09
Great Job Comp! Ahmmm...how about that amd64 version of the cds? :) . Id like to help.

---

### Post by CompShrink on 2006-07-09
Great!

Glad to hear it **glenn45**! I'll PM you in just a second. Look forward to getting that out.

And **picallo**: Just download the CD from the link in the first post on this thread. As you said you're using KDE, open up K3B to burn the CD. Once the CD you made is in the main CD drive of the system you want to install it on, type that line in the terminal. Then use whatever you normally use to manage official Ubuntu Deb package installation. I don't know what that is in KDE. You can always used apt-get in the terminal.

Example:
```
sudo apt-get update
sudo apt-get install ubuntuplus-recommended
sudo apt-get upgrade
```
will install the majority of the packages included on the CD, and then install upgrades, which are also included on the CD. There may be other upgrades which are not on the CD, which apt-get will download off the internet if you are connected.


And hmm, I should go make a thread in PPC section of this forum asking for some help with that version. I should have thought of this obvious course of action sooner...

---

### Post by kagashe on 2006-07-12
Hi,

When I try to add the CD in Synaptic I am getting following error:
> E: Sub-process gpgv returned an error code (2)

W: Signature verification failed for: /cdrom/dists/dapper/Release.gpg

Please help.

Sorry. I did not read the thread fully. Problem solved. Public key imported from CD on Synaptic.

kagashe

---

### Post by vitesse on 2006-07-12
2 things:

I was wondering it's posible to add XGL to UbuntuPlus? 

I think the Ati drivers are missed or is just me?.

And so bad that you are not in Japan anymore CompShrink :(

---

### Post by gnudoc on 2006-07-18
First off, thanks very much, CompShrink, for putting this together, and for putting in the maintenance effort. have a big-old gold :KS  I've actually been looking into doing just this for some friends - now i can just point them at you! :D 

> **CompShrink said:**
> you're right something beyond dapper/breezy's built in CD burning should be added.

if you're still considering this, may i suggest gnomebaker? probably strikes the balance between the barebones inbuilt functionality and the full-blown (but heavy on dependency) k3b.

also, can i re-iterate the request for a list of your package choices? that would be really, really helpful.

all the best, and please keep asking for help - i'd love to help in any way i can, and i'm sure others feel the same. :)

---

### Post by vitesse on 2006-07-18
> **gnudoc said:**
> if you're still considering this, may i suggest gnomebaker? probably strikes the balance between the barebones inbuilt functionality and the full-blown (but heavy on dependency) k3b.

Right

> **gnudoc said:**
> also, can i re-iterate the request for a list of your package choices? that would be really, really helpful.

Right too.


> **gnudoc said:**
> 
all the best, and please keep asking for help - i'd love to help in any way i can, and i'm sure others feel the same. :)

Amen

---

### Post by CompShrink on 2006-07-19
Sorry about the lack of work on this, although there has been a bit of slow progress...

I generally hate excuses, but the truth is I just got back to the US, just had house guests leave yesterday, and start a new job on Monday.

And I'm perfectionistic. I know the error correcting and crash recovery I'm building into the new script is a bit of overkill, but I like to be cautious.

And the list of packages included on the CD. This is not all the dependancies, only the ones I purposely included. I will make a list of every single package on the CD soon and attach it.

*Ok, here's what's on the Dapper version dated 2006-06-07*:

**nvidia-glx-legacy** - nVidia official driver for older video cards
**nvidia-glx** - nVidia official driver for newer video cards
**nvidia-settings** - control options for the nvidia official driver
**xorg-driver-fglrx** - ATI official driver for video cards
**fglrx-control** - control official ATI drivers
**gmail-notify** - panel applet
**python-libgmail** - use gmail as SMTP server, and then you can use thunderbird or evolution to manage gmail
**tomcat** - turn your desktop post-it notes into wikipedia!
**bcm43xx-fwcutter** - create linux native wireless drivers out of broadcom-based windows drivers

**libflash-mozplugin** - the GPL flash player for mozilla(firefox), replacing with non-free is suggested, but it is illegal to be put on the CD
**sun-java5-bin** - Sun's Java2 version 5 (sometimes referred to as 1.5)
**sun-java5-plugin** - mozilla(firefox) plugin for Sun's Java2 version 5
**wwwoffle** - caching program, to view webpages while offline
**liferea** - news feed (RSS) reader
**liferea-mozilla** - mozilla based backend to display the news
**acroread** - official pdf viewer
**mozilla-acroread** -  official pdf viewer for mozilla(firefox)
**mozilla-thunderbird** - mozilla email client
**mozilla-nukeimage** - plugin to manually get rid of annoying picture ads
**d4x** - download manager
**gftp-gtk** - graphical FTP client
**transmission** - single window style bittorrent downloader
**bittornado-gui** - multiple window style bittorrent downloader

**xfonts-intl-arabic**
**xfonts-intl-asian**
**xfonts-intl-chinese**
**xfonts-intl-chinese-big**
**xfonts-intl-european**
**xfonts-intl-japanese**
**xfonts-intl-japanese-big**
**xfonts-intl-phonetic**
**xfonts-efont-unicode**
**xfonts-efont-unicode-ib**
**xfonts-baekmuk**

**beagle** - Linux's answer to Google Desktop Search
**gdesklets** - Desktop Widgets engine
**gdesklets-data** - The widgets themselves
**bum** - Boot Up Managers
**wine** - allows some windows programs to be run in linux
**sun-java5-bin** - Sun's Java2 version 5 (sometimes referred to as 1.5)
**gparted** - hard drive partition manager
**firestarter** - firewall control
**unrar-free** - unpack old .rar files
**unrar** - unpack new .rar files 
**lzop** - unpack .lz files
**sharutils** - pack and unpack .shar files
**lha** - unpack lh files
**alien** - convert .rpm installers into .deb installers that can be used with Ubuntu
**smbfs** - MS Windows networked filesystem
**samba** - Graphical interface for setting up MS Windows
**openssl** - Security for networking
**xsmbrowser** - Graphical interface for viewing
**nvu** - Web Page creation
**vpnc** - connect to virtual networks (often used for wireless security)
**ndis-gtk** - wrapper that can use many types of windows wireless drivers

**  gstreamer0.10-ffmpeg** - various audio and video playback
**  gstreamer0.10-plugins-bad** - various audio and video playback
**  gstreamer0.10-plugins-ugly** - various audio and video playback
**  gstreamer0.10-plugins-bad-multiverse** - various audio and video playback
**  gstreamer0.10-plugins-ugly-multiverse** - various audio and video playback
**  gstreamer0.10-fluendo-mp3** - play mp3s
**  gstreamer0.10-fluendo-mpegdemux** - Mpeg, Mpeg2(DVD) video
**  gstreamer0.10-gl** - OpenGL video card output
**  gstreamer0.10-pitfdll** - use windows codecs with gstreamer (w32codecs)
**easytag** - edit title, artist, etc of audio files
**rhythmbox-applet** - panel applet, small simple controls for your jukebox
**kino** - non-linear video editor
**kinoplus** - extra plugins
**kino-dvtitler** - plugin to add text
**kino-timfx** - more plugins
**f-spot** - photo management
**audacity** - audio editor
**mplayer** - alternative media player
**mozilla-mplayer** - alternate music player's plugin for mozilla(firefox)
**vlc** - another alternate media player
**alsa-oss** - audio output connector

**scim** - main input program
**scim-chinese** - chinese input
**scim-chewing** - alternative chinese input
**scim-gtk2-immodule** - graphical input switcher
**scim-hangul** - korean input
**scim-m17n** - various language input
**scim-tables-additional** - additional various language input
**mlterm-im-scim** - terminal that propperly handels these inputs
**scim-tables-ja** - japanese input

**uim-anthy** - japanese input
**uim-xim** - input bridge
**uim-gtk2.0** - graphical input switcher
**ami** - korean input
**chinput** - chinese input
**uim-applet-gnome** - more graphical input
**uim** - main input program
**mlterm** - terminal that propperly supports non-western text


PS: Yes, I will look into whether the official ATI binary driver is missing. And MD5 for the Dapper CD is 76012973ca89b41ee2941fbcf98aa47a, and has been added to the first post in this thread.

---

### Post by AliBi on 2006-08-15
im a cheap guy. i dont want to burn a cd for just 200MB. so i would like to mount the iso manually.

```
sudo mount -t iso9660 -o loop ubuntuplus-dapper_2006-06-07.iso /media/cdrom0

```
you see no problem there, BUT how can i persuade synaptic to use this mounted iso?
any help would be appreciated.

greets AliBi

p.s. keep up the good work!

---

### Post by eccentricity on 2006-08-15
I wanted to resurrect this thread for a minute. Are there any plans on updating the PLUS cd to the 6.06.1 new release? Thanks

---

### Post by vitesse on 2006-08-16
Yea let's keep this thread alive...

Ubuntu Plus Rocks

---

### Post by simosx on 2006-08-17
What I see missing is an Update CD for those who happen to have the original Ubuntu 6.06 Installation CD.

Is there such a thing? I have installed Ubuntu 6.06, my Internet connection is a miserable dialup link and I would like all the necessary updates in a CD that Synaptic will recognise through UpdateCD. The update CD should have the necessary updates for, let's say, August 15.

---

### Post by CompShrink on 2006-10-09
[SIZE="4"][COLOR="Red"]NOTICE: I NEED NEW HOSTING.[/COLOR][/SIZE]

I have been informed by tikal26, who has been generously hosting this project up until now, that it has started taking too much bandwidth. If anyone can help with this, I would be extremely greatful.

> **simosx said:**
> What I see missing is an Update CD for those who happen to have the original Ubuntu 6.06 Installation CD.

Is there such a thing? I have installed Ubuntu 6.06, my Internet connection is a miserable dialup link and I would like all the necessary updates in a CD that Synaptic will recognise through UpdateCD. The update CD should have the necessary updates for, let's say, August 15.

That's exactly what this is, an update CD (for the default installed programs) and a few extra addons.



Sorry I've dropped off the face of the earth (or at least this forum) for a couple months. I've been really busy, and still am, but I'm going to try and make time to continue working on this anyway.

---

### Post by bruenig on 2006-10-09
If you don't have a fast internet connection which prevents you from downloading packages, how do you download this cd?

---

### Post by hikaricore on 2006-10-09
> **bruenig said:**
> If you don't have a fast internet connection which prevents you from downloading packages, how do you download this cd?



wget -c [http://www.tikal26.net/ubuntu/ubuntuplus-dapper_2006-06-07.iso](http://www.tikal26.net/ubuntu/ubuntuplus-dapper_2006-06-07.iso)

or whatever the current release is

if you start that command from the same directory (home for example) over a few days time you should be able to download the whole cd quite easily.

just keep an open terminal on your desktop running this while doing other things, not that complicated at all :)

---

### Post by CompShrink on 2006-10-09
Exactly as hikaricore said. The command he gave will resume, only the url was cut off when he put it: ```
wget -c http://www.tikal26.net/ubuntu/ubuntuplus-dapper_2006-06-07.iso
```

So, yes, since you have a slow download speed, it will take a while to download. But how could that be avoided?

It's a standard type of CD image, so you could go to the library, download it there, and make a CD of it, assuming the library computer has a CD burner. Or do the same from school or work. 

Without this CD, you couldn't download the upgrades on another computer and transfer them over. Not without a lot of hassle anyway.

I'm working on something that will let you download only what you need, from any (modern) Windows, Mac, or Linux computer, and make your own custom CD. For now, you can download the CD.

---

### Post by gblob331 on 2006-10-12
> **bruenig said:**
> If you don't have a fast internet connection which prevents you from downloading packages, how do you download this cd?

That's no real problem as long as you know a computer that has a fast internet connection (work, school, neighbor's house, etc.). Go there and download the .iso and stick the iso onto a USB drive and then bring it home and burn it.

---

### Post by shifan on 2006-11-05
i tried the cd for dapper as said i add the cd rom through synaptic  
but it gives and error about a file and doesnt add to my software list any upgrade i dont know what i did wrong there i tried it severel times but no change. what could be the problem?

---

### Post by CompShrink on 2006-11-07
If you could try again and give me the exact error, that would help.

And it does not automatically mark any upgrades. Once you add the CD, search for "ubuntuplus" and install the categories that you want.

---

### Post by bsalt on 2007-01-14
Is there an UbuntuPlus CD for Edgy (6.10) yet - or would that be a waste of time?

---

### Post by airtonix on 2007-02-22
chm read is a must.....entire msdn knowledge base is Compiled HTML Manual format.

orrrr include the chm to html convertor? yes that is more in line with future use of linux..... bemoan mecroflop. /cheer

---

### Post by C Shore on 2007-03-22
I've been working on being able to make custom ubuntu and debian cd sets, and am making some headway.  

Overview:

1) From lists of wanted packages generate package lists including dependencies (and optionally build dependencies and sources)

2) Download the packages and create a local reposity with the packages from 1)

3) Create the CD/DVD set

1) can be done with germinate (apt-get germinate) which is a standard ubuntu tool

I have the first half of 2) as a script that I have posted on the debian wiki [http://wiki.debian.org/DebianCustomCD/CustomDownload]("http://wiki.debian.org/DebianCustomCD")
and the steps needed for the second half are in the document [http://wiki.debian.org/DebianCustomCD]("http://wiki.debian.org/DebianCustomCD")

I am currently working on 3) since debian-cd is broken in ubuntu dapper universe.  You can get the current state by using bazaar-ng

bzr get [http://www.wightman.ca/~cshore/custom-apt-cd/trunk](http://www.wightman.ca/~cshore/custom-apt-cd/trunk)

There are a few things I am trying to do with the cd set

1) provide an easy way to make an updates/addons cd (set) for high speed friends of low bandwith users
2) a way to provide a set containing build environment and sources for packages I include on a boot floppy set / cd I use for backing up windows and linux and windows rescue (I build the set using binaries installed on an ubuntu system, so this process is a way to meet gpl obligatiosn)
3) to provide a way to create debian/ubuntu derived distributions

Regards,

Daniel

---

### Post by CompShrink on 2007-04-12
Unfortunately I haven't been able to work on this project lately due to priorities in my offline life.

I was working on a similar project to C Short, extending from the current Addon CD. I was aiming for #1 in your list of goals, along with a couple others.

I'll send you a PM about it, I was not using debian-cd, so maybe I can help. I wasn't using germinate either, so I'll look into that. I'd probably a lot cleaner and easier than the low-level way I was hacking around in dpkg.

---

### Post by aysiu on 2007-05-22
Has there been any progress on updating this for Feisty?

I don't know much about gpg keys and authentication, but if no one else is going to do it, I could put together some kind of Feisty add-on CD (without all the authentication and such).

I've seen numerous requests for an add-on CD, and I've been able to point people to only the Dapper and Breezy ones at UbuntuPlus.

I appreciate the hard work CompShrink has put into this. Aren't there any other people interested in keeping this project up?

---

### Post by cji on 2007-08-08
Check this for ubuntu Addon CD..

**[http://imaginux.com/addoncd/](http://imaginux.com/addoncd/)**

Very Nice....:KS:KS:KS:

---

### Post by QwUo173Hy on 2007-08-08
This seems to be all that is on the Feisty CD at that address. Does that not mean that a lot of codecs are missing?

Aysiu, I don't know hot to go about this either but if you decide to try and need to offload some work, I'll do what I can.

> rtu-apps
rtu-media
sun-java6-plugin
beryl-manager
wallpapoz
trackballs
frozen-bubble
msttcorefonts-offline
w32codecs
vlc

---

### Post by offline on 2007-09-14
I've downloaded your iso file for my offline ubuntu 6.06 computer. burned to a cd , and then used the cd and recalled synaptic manager and selected add cd. Then, synaptic said something like the public  key can not be recognized.

Then I clicked one by one the packages in the cd(no synaptic), and made it possible for totem to start playing avi, wmv and dvd files(after installing some known codecs mysef). Some other applications have been installed too.

Thanks

---

### Post by alefnull on 2007-10-13
> **jarlath said:**
> This seems to be all that is on the Feisty CD at that address. Does that not mean that a lot of codecs are missing?

Aysiu, I don't know hot to go about this either but if you decide to try and need to offload some work, I'll do what I can.

jarlath: that is just a sample of the packages on the Feisty CD.. see [here]("http://imaginux.com/addoncd/addoncd_feisty_rev1") for a full list of available packages.
;) :D

---

### Post by QwUo173Hy on 2007-10-14
Thanks Alefnull, that looks amazing.

---

