---
title: "bit of a tutorial on getting dvdfab running / working / copying"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by stinger30au on 2008-05-04
How to install dvdfab hd decrypter and copy encrypted dvds in ubuntu 8.04

here is what i did to achieve this... hope it works for you.

first install a standard dvd movie in the dvd drive and attempt to play it.
when i did this 8.04 had a spit and said i had to download some extra codex.
it gave me a diaglogue box and i just clicked it and off it went and downloaded what it needed.

so make sure first off you can play a standard dvd.

once you have achieved this, we can install wine. wine is a groovy bit of software that will allow a program written for windows to run inside of linux.

to install this go to system synaptic package manager, open this program and it will ask you for your password. type it in.
when synaptic starts click on settings, repository's.
put a tick in the boxes that say MAIN, Universe, Restricted, multiverse and you may have to set the server to main server. try a server closer to you but if it is anything like the server closest to me it seems to never get updates so i leave it set to main server.

now up the top you will see a search button. click on that and type in

wine

you may have to scroll down and you will see on its own 

wine

click in the box next to where it says wine and make the box go green.

now click the "apply" button.
it will connect via the internet and get you a stable copy of wine from the repos.

now we will get the newest version of wine as well. wine is undergoing a lot of updates as they are getting close to version 1 so we will visit the official home of wine and add the ubuntu wine debain package to our pc as well.

if you visit this page

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

it will step you through the process of adding wine to your pc so i can be updated everytime a new release comes out.

for those who are unsure on what to do, i will just copy/paste the info here

Adding the WineHQ APT Repository:

First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:


wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -


Next, add the repository to your system's list of APT sources:
For Ubuntu Hardy (8.04) you will need to copy/paste the below info to a terminal screen as well.Applications->Accessories->Terminal :


sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list


and again from a terminal screen copy/paste this

sudo apt-get update

after you do this you will see a orange circle appear on your taskbar with a down arrow on it. click on this once and it will open up and tell you there is a new version of wine to download and install, it will be about 9 meg in size. let it do this and we can continue on.

once wine has updated itself, we need to do a quick config of it to make sure it will do what we want.

fireup your terminal program again and type in

winecfg

click on the applications tab and set the windows version to windows 2000.

while your there, just click on the about button and you should see it will say wine version 0.9.61 (that is the current version at the time of me writing this)

click in sound drivers and make sure either the ALSA or OSS driver box is ticked and press the test sound button. on my machine i have got both tick boxes set and it works fine for me.

next click on the drives button
click the autodetect button.
this should fix up some mix matches with the drives in your pc. i know it does on mine. 

ok thats it for config of wine, now click the ok button.

next we can install the free version of dvdfab. this is a groovy bit of software that enables us to copy a protected dvd to our pc hard drive and it will remove all sorts of copy protections we dont need.

if we point our web browsers here

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

we can d/l a copy of DVDFAB HD decrypter. save this to your pc somewhere.
i created a directory on my desktop called "downloads" and dumped i there.
once it is saved there, open up that directory and double click it. wine will open it and install it.

once wine has installed dvdfab, exit fro the application.

install the dvd you want to copy. wait a little while and see if ubuntu is going to try and auto play it in a media player. if it does then just exit the media player.


you can now find it by applications-> wine ->programs -> dvdfab

with dvdfab running you can click on 

target

it is probably set to your dvd drive. we need to change this and make it dump to the hdd. i suggest you click the down arrow.
on my pc it says

c:\windows\profiles\"user name"\my documents\dvdfab

and of course "user name" will say what ever the name is you have created when you installed or configured ubuntu.

and your source with a bit of luck should be already set to the dvd drive and shows the name of the disc you inserted.

you may now click the start button down the lower right and it will copy the entire dvd to the hard drive and remove all copy protections.

when dvdfab has finished you may exit the program.

congratulations.... we are about half way thru the process now.

now we can compress the data to fit a standard single layer blank dvd.

i suggest before you go any further you test the data on the hdd now and see if it plays correctly. if it does not, theres no point burning it to dvd.

fire up natalus or konqueror and go to 

/home/"user name"/DVDFab/FullDisc

again user name is the name you have created on your pc.
in there you should find the name of the disc you copied to the hdd.

open up the directory, and with in a few seconds you will see the files load and have like a screen shot shown of the files.

if you open the first video file, probably called 

vts_01_0.vob 

you will see the main screen load up and everything should be wokring fine. if so, thats great we can continue.

there is a few ways we can go about burning this data to a disc. if you have dual layer blank discs and want to burn this info to one of them the easiest way to do it is to install K3B burning app.
K3B can me installed the same way installed wine from the repos but instead of searching on wine, we will search on k3b and click on the box next to it and make it green and install it.
once K3B is up and running you can click on "further actions" and click on "new dvd video project".

if you go to the home directory you will see dvdfab under it. open this directory and you will see "full disc" open it up and you will see the name of the movie you copied.
open that directory up and you will see 2 more directory's, open up the  "video_ts" directory.

now in the lower of the screen in k3b also double click the video_ts directory.

now copy and paste each of the files from the top video_ts directory to the one to be burnt.
after all files are copied across then hit the burn button. select burn speed as 4x.
i suggest you dont go any faster.you may burn coasters other wise.or you may find the disc will not play in all dvd players. you have been warned.

ok, for the rest of us who have single layer dvd discs there is abit of editing to do, but nothing too tough but we will also need K3B installed so go ahead and install K3B now.the procedure is back up the page a bit incase you forgot :-p

now... while we are at it we are also going to install a very groovy native dvd shrink program. it is called k9copy.
this can also be installed via synaptic same as what we did in the first place for wine. do a search on k9copy and again place the green box next to it and off we go.

k9copy is going to take the data we have copied to our hdd and "shrink" it down so it is small enough to fit to a single layer dvd disk. we will make it create an .iso file for us.

ok, click on applications, multimedia, k9copy.

up the top you will see input device. it will probably be set to you dvd drive. next to it on the right you will see a down arrow and picture of a few folders.

click the folder next to the down arrow,it will bring up a dialog box that says  

open dvd folder

navigate to the home directory, then the dvdfab directory, then to the "full disc" directory, then open the directory of the disc you saved there with dvdfab.

once done this click the ok button down the lower right.

you will be brought back to the main screen and i suggest you put a tick in the box that says "titleset 1"

now up the top of the screen you will see an icon that says

dvd and there is a green arrow pointing down towards the bottom of your screen.

press this button.

it is now asking you where to save a file. the file we are going to ave will be a compressed version of the dvd that will fit to a single layer dvd.
you can save the file pretty much where ever you like, so long as you remember where of course you saved it as we are going to burn it to a blank dvd shortly.

i suggest you click the "desktop" button and create a new folder on your desktop called "dvd-shrink" or whatever name you feel like.
and let it save the .iso file there.

depending on the size of he dvd data and your cpu, this may take up to about 20 minutes.
there will be a preview of the video showing as well on the right side of k9copy so you can keep an eye on whats going on.

there is also a progress meter in the lower right corner showing you a rough guide on how long it has to finish doing it business.

once k9copy has finished you may exit the program and fire up K3B. if you have not already installed K3B then i suggest you do so now.the instructions are included in this document and with a bit of luck you have already read this information to be this far down the document to begin with anyhow :-p

ok fireup K3B, this is done by applications-> multimedia -> K3B

on the right side you will see a button that says

Burn DVD iso image

click this button

point it back to the directory we created on the desktop called "dvd-shrink" and point it to the .iso file.

now press the speed button and set it to 4x. if the button is greyed out you probably dont have a blank disc in the drive.

once you have set the burn speed to 4x now press the start button and be prepared to be .....   AMAZED.

in a very short while you will have your own burnt copy of the protected dvd you first started with.

feel free to celebrate this occasion by watching the movie over and over again after it is finished being burnt.

hope this helps someone out.

enjoy

---

### Post by bilal.17 on 2008-05-04
I was looking for a tutorial of this sort, a while earlier, if I had found this it might have saved me some time, but at least now anyone else with the same problems, wont have to go through the same troubles I had, and can just use your tutorial.

---

### Post by tom56 on 2008-05-04
Alternatively you can use k9copy, which has all the same features

---

### Post by stinger30au on 2008-05-04
> **tom56 said:**
> Alternatively you can use k9copy, which has all the same features

or you could have just read the entire post and notice that i used k9copy in there any how, plus the fact k9copy will not copy a copy protected dvd, hence the requirement for dvdfab free

---

### Post by tom56 on 2008-05-06
> **stinger30au said:**
> or you could have just read the entire post and notice that i used k9copy in there any how, plus the fact k9copy will not copy a copy protected dvd, hence the requirement for dvdfab free

There's no need to get shirty! Besides, k9copy can do all of the above on its own, no need for DVDFab. I have never had any troubles copying from copy protected DVDs with it.

---

### Post by stinger30au on 2008-05-07
> **tom56 said:**
> There's no need to get shirty! Besides, k9copy can do all of the above on its own, no need for DVDFab. I have never had any troubles copying from copy protected DVDs with it.


sorry if i sounded a bit agro on my last post. i have tried unsuccesfully for a damn long time with K9copy to do protected dvds and no luck and it has taken me ages to find some kind of solution to this

hence the reason for my original post.

---

### Post by SlappyPappy on 2008-05-07
K9Copy is really buggy and prone to freezing or crashing.

I've been using HandBrake a lot recently. I had been having success with AcidRip but even that has been going nutty at times. 

All of these programs, other than HB seem to choke on certain DVDs and not even DVDs with encryption! I know, I've been using all of these methods.

I even tried recompiling K3b to see if I could get that to work but no love there at all!

DVD copying and ripping is NOT a smooth experience in Ubuntu. As I've said before, I've tried all of these methods. Very dodgy at best and to be honest I'm still trying to figure out the most streamlined method.  :)

---

### Post by newbeeman on 2008-05-09
I followed the instructions to "once wine has installed dvdfab, exit fro the application" by the letter down to accessing the C drive to add DVDfab, but wine failed to open the program.
applications -> wine->programs-> but no dvdfab.
Where did I go wrong?

---

### Post by stinger30au on 2008-05-09
> **newbeeman said:**
> I followed the instructions to "once wine has installed dvdfab, exit fro the application" by the letter down to accessing the C drive to add DVDfab, but wine failed to open the program.
applications -> wine->programs-> but no dvdfab.
Where did I go wrong?

do you have the newest version of wine installed?

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

install newest version of wine and reinstall dvdfab free

---

### Post by newbeeman on 2008-05-09
install newest version of wine and reinstall dvdfab free[/QUOTE]

As I mentioned in my first post, word for word via your instructions. Newest version of both wine and DVDfab. 
Wine will not open DVDfab. Tried all I know, which isn't much!!!!

---

### Post by crjackson on 2008-05-09
I'm not a big fan of wine but I'm going to backup my system and give this another try because I am a big fan of DVDFabHD Decrypter.

I don't quite understand why you install wine from the repos, then the deb, then add the wine repo.  Is there any special reason for this?  It seems you could just install the wine repo and install it from there...


**@tom56** - k9copy works pretty darn well for all the same operations when running under Gutsy64 but I haven't tried it with Hardy.  I've run into a few proggies not working well under Hardy.  Time will sort this out.

That said, k9copy doesn't work well with MANY of the newer movies that deploy the latest copy protection.  DVDFab is always on the money or updated within a few days to catch new protection schemes.  I wish they made a native Linux version, I'd be ever so happy to PAY for it, but alas they don't.

---

### Post by stinger30au on 2008-05-10
i have written what i did  and it worked.
hopefully you will have the same success

---

### Post by newbeeman on 2008-05-10
On checking I have upgraded to Wine Version 1.0? Could this be the problem?

---

### Post by stinger30au on 2008-05-10
> **newbeeman said:**
> On checking I have upgraded to Wine Version 1.0? Could this be the problem?

i doubt it.
have you tried to reinstall dvdfab?

---

### Post by hellarough on 2008-05-31
You think this would work with a windows executable of dvdfab hd not the free version?

---

### Post by crjackson on 2008-05-31
> **hellarough said:**
> You think this would work with a windows executable of dvdfab hd not the free version?

I can run the free option with no problems, but it won't accept my registration key.  I'm still working on solving that particular problem.

---

### Post by stinger30au on 2008-05-31
> **crjackson said:**
> I can run the free option with no problems, but it won't accept my registration key.  I'm still working on solving that particular problem.

out of interest what happens when you put in the rego key does it crash or say it has installed it and then when you check it has not or what???

---

### Post by crjackson on 2008-05-31
> **stinger30au said:**
> out of interest what happens when you put in the rego key does it crash or say it has installed it and then when you check it has not or what???

It says thank you for registering and it must restart.  It doesn't restart it just exits.  Then when you restart it, it's back to the free version again.

---

### Post by mc4man on 2008-05-31
the reg key is a current issue
[http://bugs.winehq.org/show_bug.cgi?id=13114](http://bugs.winehq.org/show_bug.cgi?id=13114)
if and when it's fixed you may see a post here
[http://club.cdfreaks.com/f116/dvdfab-hddecrypter-linux-220283/index5.html](http://club.cdfreaks.com/f116/dvdfab-hddecrypter-linux-220283/index5.html)

---

### Post by daitheflu08 on 2008-06-27
Great forum, thank you very much, now I have one question:  Can we turn the ISO into AVI or the DVD files into AVI instead of copying.  And how would we do this?

---

### Post by omns on 2008-07-10
I used to go through all this heartache and then one day I just gave up and decided to rip DVD's to an iso using DVDShrink in my old windows PC (It's about all it gets fired up for these days). ISO in hand on my USB drive I burn it with Brasero. I used to run DVDShrink with Wine but it was to buggy.

K9copy is buggy and kdelibs breaks glipper which I use constantly. I'm also using Mint these days so maybe I'm just getting lazy and tired in general when it comes to endlessly fiddling with things. It used to be fun but now I want solutions that just work.

---

### Post by stinger30au on 2008-07-11
> **GrantG said:**
> . It used to be fun but now I want solutions that just work.

dvdfab does run with now dramas with the latest version of wine.

get the latest version of wine here

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by freestar on 2009-08-25
I found a free dvd ripper on ubuntu no running a vm like wine!

---

### Post by stinger30au on 2009-08-25
i dont even bother with it any more to be honest

k9copy works for me finally, so i use it instead

---

