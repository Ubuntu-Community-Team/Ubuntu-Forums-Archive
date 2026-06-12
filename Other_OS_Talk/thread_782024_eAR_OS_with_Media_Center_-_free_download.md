---
title: "eAR OS with Media Center - free download"
date: 2008-05-04
forum: Other OS Talk
---

### Post by earos.dk on 2008-05-04
Do you want a media center that is working out-of-the-box with no configuration files or other complicated user setup?

If yes, the answer is here:

eAR OS is a complete Operating System, which is using the Ubuntu 8.04 repositories, but nothing more that this.

With eAR OS you can watch and record digital TV programs, rip your CD's to FLAC, listen to radio while watching your photo collection, and much more.

Everything works out-of-the-box.

The ISO can be downloaded here: [www.earos.dk](www.earos.dk)

Enjoy :-)

---

### Post by chris4585 on 2008-05-04
Does it rip to mp3 if i want "out of the box"?  I'd much rather have mp3's than flacs

---

### Post by earos.dk on 2008-05-05
You need to open up a terminal/console and write:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

(the password is earmusic).

Insert a CD and before pressing Extract, then change the preferences to MP3

and here you go :guitar:

---

### Post by wolfen69 on 2008-05-05
is this a live cd?

---

### Post by earos.dk on 2008-05-05
Yes, it is a live-CD.

Therefore you can check if your hardware is supported before you install it.

The installer is as simple as when installing Ubuntu, because it is using ubiquity.

It is not Ubuntu, but you can do anything that Ubuntu can offer, and more, because it is using the repositories from Hardy Heron 8.04 LTS. 

Also the proprietary hardware driver installer is similar. This is the reason why I converted it to use 8.04 repositories. Previously, it was using Debian repositories.

---

### Post by chris4585 on 2008-05-05
> **earos.dk said:**
> You need to open up a terminal/console and write:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

(the password is earmusic).

Insert a CD and before pressing Extract, then change the preferences to MP3

and here you go :guitar:

That wasn't the question, I know how to get mp3's to work, but does it support mp3's out of the box is what I was asking.  By your response I suppose no mp3 support out of the box?

---

### Post by earos.dk on 2008-05-05
The current version supports MP3 playback out-of-the-box, but that may be an error.

As you can see it is extremely easy to add the MP3 ripping feature and  I have to investigate the legal rights to add that simple line to the distro.

Actually, I am seriously condering to make a first-run-wizard and let people themself install libdvdcss2 for dvd playback and codecs for ripping and playing mp3's. In that way it will work out-of-the-box after running the first-run-wizard. The user only have to answer yes or no to the questions :-)

Nice we got this issue up for discussion.

---

### Post by chris4585 on 2008-05-05
> **earos.dk said:**
> The current version supports MP3 playback out-of-the-box, but that may be an error.

As you can see it is extremely easy to add the MP3 ripping feature and  I have to investigate the legal rights to add that simple line to the distro.

Actually, I am seriously condering to make a first-run-wizard and let people themself install libdvdcss2 for dvd playback and codecs for ripping and playing mp3's. In that way it will work out-of-the-box after running the first-run-wizard. The user only have to answer yes or no to the questions :-)

Nice we got this issue up for discussion.

nice, good idea.

---

### Post by kostkon on 2008-05-06
> **earos.dk said:**
> Do you want a media center that is working out-of-the-box with no configuration files or other complicated user setup?

If yes, the answer is here:

eAR OS is a complete Operating System, which is using the Ubuntu 8.04 repositories, but nothing more that this.

With eAR OS you can watch and record digital TV programs, rip your CD's to FLAC, listen to radio while watching your photo collection, and much more.

Everything works out-of-the-box.

The ISO can be downloaded here: [www.earos.dk](www.earos.dk)

Enjoy :-)
Interesting project, thanks for sharing.

---

### Post by wolfen69 on 2008-05-06
thanks but no thanks. after trying out the live cd, i found the free edition to be too limiting. sure, i could pay for the "full version", but if i wanted to pay for an os, i would be using windows. plus, mythtv (truly free) gives all the functionality of earos and more. i appreciate the effort behind this, but it is not for me. good luck.

---

### Post by earos.dk on 2008-05-06
The MP3 ripping feature will be included in the next version, because there is no software patents in Europe.
Therefore the first-run-wizard isn't necessary.

---

### Post by dynobot on 2008-05-08
I downloaded eAR on my computer.

Was not able to load graphics driver for ATI graphics card

Could not hear sound via my sound card - Creative Labs 

DVD would not play
CD would not play via eAR media center

Do I have to install Wine to get these products to work?
It would be nice to be able to select objects in the eAR Media Center GUI with a mouse and/or keyboard.

I would also like to play an internet radio station that is not on the pre-made list of stations....is there a way to add my own?

---

### Post by earos.dk on 2008-05-09
I have heard about many that have success with the current version, and others that don't have.

Tomorrow, I do expect to release version 1.06.

This time I am pretty sure it has all the hardware support that 8.04 LST has.

The coming 1.06 is also faster than version 1.05 and 512MB RAM should be more than enough.

If the hardware isn't supported with coming version 1.06, then I can't help.

BTW: 
Click on the hardware icon in the upper panel for installing restricted hardware drivers, for example to nVidia, ATI and proprietary wireless drivers.

The DVD should play if you check your /etc/fstab file and put that name into the kaffeine xine setup parameters for you media device.

Internet radios that are not listed: The media center is using shoutcast. If you want to play others, then use the Firefox browser and let a media player do it for you.


Wait for eAR OS Free Edition version 1.06. It is coming very soon.

Kind regards,
earos.dk

---

### Post by dynobot on 2008-05-09
I tried installing restricted hardware...my graphics card is a ATI 9600 series.  The installer ran and when finished prompted me for a restart so that the change could take affect.  Once it booted back up I got nothing but a white screen after the login window.  I had to re-install the whole OS.

Do you have any Beta testers?  I'm really interested in this OS and would like to see it work with my hardware.  My graphics card and sound card are both typical PC products.

---

### Post by Ripfox on 2008-05-10
Nice website but I will just use Elisa...it's free. ;-)

(and in the repos)

---

### Post by earos.dk on 2008-05-10
@dynobot,

You should press Escape, when the hidden Grub menu is starting (you have 2 seconds to do that). Then you should boot in rescue mode and run the following command: sudo dpkg-reconfigure -phigh xserver-xorg (the password is earmusic).

If that doesn't help, then reboot again in rescue mode by pressing ESC.
Then you need to edit the /etc/X11/xorg.conf file and change the driver to "vesa" and then restart X and then use the restricted driver mananger.

However, way too much work.

Wait for the new version 1.06.
It is uploading to the server right now and should be ready for download within 3 hours. It comes with hardware support, that should be similar to 8.04 LST.

Version 1.06 comes with build-in high-quality Internet TV too. Yes, I know you can't watch the Danish TV in h264, because it is limited to IP addresses inside Denmark, but currently 10 other high-quality Internet TV programs are build-in. Also a High Definition 720x1280 is there. If you live in the UK then you can change the DR programs to the BBC programs. Only one of the programs is transmitting in less than 1 mega-bit per second. 
In the future the number of Internet TV programs will grow. I do hope the users will help to find the high qquality programs and then the programs will be included in future releases.
 
Kind regards,
earos.dk

---

### Post by earos.dk on 2008-05-10
The new release 1.07 is available for download.
I really do hope this release will support your hardware.
I tried with three different ATI GPU's and the restricted drivers can be used now, but it is not necessary with this release.

Edit: I forgot [www.earos.dk](www.earos.dk)

---

### Post by earos.dk on 2008-05-13
BTW: The new 1.07 release runs much faster than previous releases.

---

### Post by scxtt on 2008-05-13
i tried this (v1.06) out, actually liked it, but the "Install" icon seems to disappear from my desktop when the live session starts up ...

it did inspire me to install Hardy at least :)

---

### Post by earos.dk on 2008-05-14
The "Install" icon will disappear, if you press exit inside the Media Center.
It is because after install to hd it will still be there after the first boot.
The first time you exit it will be removed.

How to install:  Just click once inside the media center and then click the install icon :)

BTW: 
Version 1.07 is very fast.
It can run with just 256MB RAM.

---

### Post by scxtt on 2008-05-14
ok, wouldn't have thought of that ~ but i think i didn't notice that behavior my 1st couple times in the Live environment where i'd try to use the mouse to navigate the Media Center (it'd shrink to the task bar, i'd see the desktop and the install icon would persist) ... i have a feeling i'll revisit this OS later (just installed Hardy and it's working out fine) and might put it on my gf's laptop when i get my hands on it ...

thanks! :)

---

### Post by volkswagner on 2008-05-14
> **earos.dk said:**
> Do you want a media center that is working out-of-the-box with no configuration files or other complicated user setup?

If yes, the answer is here:

eAR OS is a complete Operating System, which is using the Ubuntu 8.04 repositories, but nothing more that this.

With eAR OS you can watch and record digital TV programs, rip your CD's to FLAC, listen to radio while watching your photo collection, and much more.

Everything works out-of-the-box.

The ISO can be downloaded here: [www.earos.dk](www.earos.dk)

Enjoy :-)

I have several analog tuners.  Why no support for them?

---

### Post by earos.dk on 2008-05-14
Because next year they are turning off analog TV here in Denmark.

Furthermore, many analog TV cards have problems with sound. Typically you need to use arecord and aplay to get it to work. Therefore it is not easy to make a general script that will work with most analog tv cards. That is easier with DVB-T and DVB-S.

Anyway, you can add that feature yourself:

sudo apt-get install tvtime

Make a startup bash script for tvtime to let it start in full screen and to let it route the sound correctly. You may need to modprobe some modules for your TV card too.
The name of the script can for example be analog-tv.sh 
Place the script in /home/earmusic/.ear

Check the script is working from a console.

Edit /home/earmusic/.ear/digital-analog-tv.sh

Mask out digital-tv.sh with #
and add your analog-tv.sh script.

Then you can get analog TV to work for playback only.

Best regards,
[www.earos.dk](www.earos.dk)

---

### Post by ninekit on 2008-05-14
Hi, I am very interested in your eAR OS, and am in the process of backing up my WinXP HDD for it. 

May I ask how to add the permission to enable real-time audio streaming with the eAR free edition? And in what way real-time will improve the sonic performance? 

Thanks and regards,
ninekit

---

### Post by Thundera on 2008-05-14
Very Mac Like :p

---

### Post by earos.dk on 2008-05-15
It is already running real-time when using for example a default alsa sound device, but when using for example IEEE1394 Firewire audio devices the sound is routed via jackd in the Enterprice Edition. In the qjackctl panel it is only possible to enable RT audio if all security and permissions are correctly setup. That is  really not for newbies to setup this feature and therefore it is default setup to work out-of-the-box in the Enterprice Edition, which I will not talk about here since it has not much to do with the Free Edition.

----

Next build:

I discovered that sometimes the dockbar from the Ubuntu 8.04 repository will crash. Therefore I have to make a new build where the newest version of the dockbar is compiled here. It will also have four workspaces, the current build only use one workspace, because the dockbar from the repository was not available to more than one workspace. The new dockbar is available on all workspaces and more features have been added to this very low RAM consuming dockbar.

The new version will have a kind of a media center recovery script too. If for example a power failure ocur the database and options files could be damaged. In case that happens it will be possible to recover without running the live CD again. It will just require a restart of X.

I do hope it can be on the download server within 36- to 48 hours.

And then eAR OS is finally ready to distrowatch.com

Best regards,
[www.earos.dk](www.earos.dk)

---

### Post by Swarms on 2008-05-15
earos.dk, where are the sourcecode for your Enterprise edition? It seems to me that you are violating the GPL, by mixing GPL licensed code with your own, and still charging money for it.

---

### Post by earos.dk on 2008-05-15
The source code that can't be downloaded by using 
apt-get source packagename 
is on the eAR RT-OS Enterprice Edition Live DVD :)

---

### Post by Swarms on 2008-05-15
And for claiming your live DVD I have to pay you correct?

---

### Post by earos.dk on 2008-05-15
This is correct that you have to pay the cost to make Live DVD, the time to go to the post office and since my office lady will not write the invoices and put them into the account for free you have to pay for her work. Oh, my god :(
But that is similar what other do.

---

### Post by Swarms on 2008-05-15
If you refer to companies like Red Hat, they do it right by offering the source code for downloading through FTP.
They are earning their money on support, just like Canonical.
If what you say is true, you are not giving access to it without paying you in return, and that is a violation.

Guys, who am I to report this to?

---

### Post by earos.dk on 2008-05-15
I do also hope to ear money on suport, but this is not yet possible.

There is not a single minor coin in making this DVD, but actually it is costing me money. Think about that!

---

### Post by Swarms on 2008-05-15
But you are still selling software that should be free, its OPEN SOURCE!
You cant just steal code, close your product and sell it. There is an easy solution, offer the code by download, or you are still violating the license.

Btw., 49 euros for just for a burned dvd + delivery, seems a little strange.

---

### Post by earos.dk on 2008-05-15
It is certainly free and open source, but free and open source does not mean that it is gratis to get it! 
Furthermore, the enterprice contain not-free and not-open source that has nothing to do with the GPL, and for example I can't give you the source to some not-gpl programs that I do not own the source code to.

If you have a problem with that, then it is not my fault.

---

### Post by earos.dk on 2008-05-15
Deleted, because of double post.

---

### Post by Swarms on 2008-05-15
[QUOTE=http://en.wikipedia.org/wiki/GPL#Terms_and_conditions"]The GPL additionally states that a distributor may not impose "further restrictions on the rights granted by the GPL". This forbids activities such as distributing of the software under a non-disclosure agreement or contract. Distributors under the GPL also grant a license for any of their patents practiced by the software, to practice those patents in GPL software.[/QUOTE]

Right now, you are charging money for both the unfree software and the software OTHERS have coded and distributed under the GPL license, in other words you are stealing from others charity.

And if its Open Source then it HAS to be available to the public, its not up to you to redefine it to fit your businessmodel.

Stop stealing, and open your code.

---

### Post by earos.dk on 2008-05-15
Sorry to dissapoint you, but I am pretty sure I can get space to the source code, that is not available by the 

apt-get source packagename

command on the next release.
:lolflag:

Swarms, you can't stop me from working, regardless how hard you ever try :lolflag:

---

### Post by toupeiro on 2008-05-15
Swarms, hate to break it to you, but if he/she is supplying the source-code for anything GPL'ed in his/her distro, then he/she is well within limits to sell it.

---

### Post by Swarms on 2008-05-15
Sorry to bother then, just thought it was illegal to sell something others coded under the GPL license, without providing the sourcecode.

---

### Post by earos.dk on 2008-05-15
I am providing the source code of GPL programs, period.

And it is certainty legal to retail GPL programs as long as the customer can obtain the source code, but this is not similar to get the source code without paying the cost to obtain it. The cost of time and materials and account costs should be paid, if the provider wants that.

And BTW:
The price for the Enterprice Edition is EURO 39 --- and  plus VAT, for customers living inside Europe. With this amount it is not possible to burn a DVD, to pay the office lady, to pay the account holder, to pay the house rent, to pay the Internet provider, to pay the download server and to pay for the time to ship it. Sorry, but this is simply completely impossible in Denmark. Therefore I loose a lot of money on this project, but I like it.

---

### Post by Swarms on 2008-05-15
So from what I understand, your enterprise edition only has extra programs that are not under the GPL license, and all those programs under the GPL license is found on the free cd?

And why don't you just make a torrent with the sourcecode for the enterprise edition? Then it wouldn't cost you anything. :)

---

### Post by earos.dk on 2008-05-15
Because I am not stupid.

---

### Post by Swarms on 2008-05-15
Right before you said you were losing money on it, and you did it because you "like" it. So you are losing money because you like it, and think it would be a stupid move to offer it over torrent instead?

---

### Post by earos.dk on 2008-05-15
Sorry, but You don't get it.

I have to ignore future posts from you. Not that I am saying you are a troll, but it will not change my decisions.

---

### Post by Swarms on 2008-05-15
No I don't get it, instead of shutting me off, you should answer my simple questions, you must have a logical answer that will make me understand, I would appreciate that.

---

### Post by earos.dk on 2008-05-15
Swarms, I will not discuss with you anymore, neither with other MS Gold Certified persons.

--

Now you can see I sponsored Distrowatch.com

This is just the beginning. In the nearest future this project will grow - I do hope so.  And it is FREE,  like Ubuntu.

In the future the whole media center idea will be changed to a new principle, but not for now.

Tonight, I will make the "final" release to be ready for download tomorrow.

--

If one is willing to pay enough for support then the small amount of shipping handling the eAR Enterprice Edition Live DVD may be removed too, but that requires enough of customers, that are willing to pay for support. I am not a billionaire, unfortunately.

---

### Post by Swarms on 2008-05-15
I am a "MS Gold Certified person", for criticizing your product? That just shows your easy ways of communicating, just like on recordere.dk and hifi-musik.dk (Danish hifi enthusiast foras), as soon people wanted help, they got told by you that they were stupid, called other names and you said you wouldn't be there anymore to answer questions, kinda like you are now.

You still have a product that has GPL licensed code, hidden under an enterprise edition, the way of getting your sourcecode is by ordering your dvd for 49 euros, that by your claims don't even cover your expenses. (That means no pay for you.)
But for making it easier for you, you could just release the sourcecode through an torrent that would eliminate your cost. But you say that is stupid, so I figure that you have some financial ulterior motives. But that is untrue according to your claims, either you are lying, or you just need to fit the last pieces into the puzzle for me?

Until we find out, people, you should pick a media center solution that has a wide user base, a wide developer base (not just one, this Peter Thomsen), and free of cost like Linux Media Center 2008.

---

### Post by earos.dk on 2008-05-15
> 

I am a "MS Gold Certified person", for criticizing your product? That just shows your easy ways of communicating, just like on recordere.dk and hifi-musik.dk (Danish hifi enthusiast foras), as soon people wanted help, they got told by you that they were stupid, called other names and you said you wouldn't be there anymore to answer questions, kinda like you are now.

You still have a product that has GPL licensed code, hidden under an enterprise edition, the way of getting your sourcecode is by ordering your dvd for 49 euros, that by your claims don't even cover your expenses. (That means no pay for you.)
But for making it easier for you, you could just release the sourcecode through an torrent that would eliminate your cost. But you say that is stupid, so I figure that you have some financial ulterior motives. But that is untrue according to your claims, either you are lying, or you just need to fit the last pieces into the puzzle for me?

Until we find out, people, you should pick a media center solution that has a wide user base, a wide developer base (not just one, this Peter Thomsen), and free of cost like Linux Media Center 2008.



Oh, I thought it was you :lolflag:

---

### Post by Swarms on 2008-05-15
Don't count on it being an individual.

---

### Post by earos.dk on 2008-05-15
Sure you hate me and so does MS, and this is fine with me.

A long time ago I said the Linux kernel is out-performing anything ever seen from MS. That is still the truth and I don't believe they will ever make it.

That sentence gave a lot of shoot against me, and it still does.

---

### Post by Swarms on 2008-05-15
What are you on about? I have nothing to do with Windows, except I used it before Ubuntu which I find superior.

---

### Post by earos.dk on 2008-05-15
Look at yourself - MS employee - I will not write dirty words at a forum, sorry.

Well, now it is time to make the next build :popcorn:

---

### Post by Steveway on 2008-05-15
I think swarms just didn't get it completely.
So to make it short (I'm annoyed of this) :
Ear OS maker (Sorry forgot your name), do your closed source programs you are distributing contain any GPL or similar licensed code or are based of it? If the answer is no (what I assume) then there is no problem.
Good luck with your project, didn't test it yet and greetings from a little bit southwards (I'm from Schleswig-Holstein).

---

### Post by earos.dk on 2008-05-15
Everything that is GPL is this and all on the Free Edition is GPL. Therefore you can distribute it as you want. Also the source code that will be on the next Live CD to a single program which you can't fetch with the command: 
apt-get source packagename
will be there.
Trademarks and Logos are similar to the rules always seen. They are a property of their owners.

( The FUD from MS did not help :-)

---

### Post by Swarms on 2008-05-15
> **earos.dk said:**
> Look at yourself - MS employee - I will not write dirty words at a forum, sorry.

Well, now it is time to make the next build :popcorn:

Sigh... Aren't you interested in giving a picture of the staff behind your OS being mature and professional, now you are just sounding like a little child... Employee of MS, is that the best you can come up with, Jesus. 

Steveway, that has been what I have been trying to find out all day, realising that some parts of this whole company just stinks. His support and his attitude towards other people.

Edit: but nice to see you finally answered to my first question, it damn took a while.

---

### Post by earos.dk on 2008-05-15
nt.

---

### Post by Swarms on 2008-05-15
> **earos.dk said:**
> You are ill and should consult a doctor, immediately.

Keep them coming.

---

### Post by Barrucadu on 2008-05-15
> **earos.dk said:**
> You are ill and should consult a doctor, immediately.
What on *Earth* are you talking about? Nobody here mentioned anyone working for MS.

---

### Post by wolfen69 on 2008-05-15
the following is not intended towards anyone here.
```
never argue with an idiot. they drag you down to their level and beat you with experience
```

---

### Post by Swarms on 2008-05-15
> **wolfen69 said:**
> the following is not intended towards anyone here.
```
never argue with an idiot. they drag you down to their level and beat you with experience
```

Yeah I fell into the trap, didn't I.

---

### Post by earos.dk on 2008-05-15
Clever words, wolfen69
Never talk to that kind of people whos only goal in life is to damage others life.

See you another day. Now it is time to code.

---

### Post by Steveway on 2008-05-15
> **earos.dk said:**
> Everything that is GPL is this and all on the Free Edition is GPL. Therefore you can distribute it as you want. Also the source code that will be on the next Live CD to a single program which you can't fetch with the command: 
apt-get source packagename
will be there.
Trademarks and Logos are similar to the rules always seen. They are a property of their owners.

( The FUD from MS did not help :-)

That sounds allright to me and I don't see any reason not to belive you.
Could we continue with the thread normally?
Also @ swarm: If you really wanted to know that then why didn't you ask directly? Could have saved everyone a lot of hassles.

---

### Post by Swarms on 2008-05-15
I did, multiple times, but is kinda hard to talk to him, when he suddenly accuses me for trying to hurt him.
earOS.dk, I came with some criticism to your work, I don't know what you think, but usually companies tries to meet the demands to get the income, instead you call names, saying that I need treatment etc., I hope you later will realize this is not the way to make business with other humans.

---

### Post by BlueSkyNIS on 2008-05-15
huh this thread didn't start off nicely as it could...
:confused:

---

### Post by earos.dk on 2008-05-15
Next time we just completely ignore the Swarms from MS.

Now it is really time to get the "final" Live CD out, see you.

---

### Post by Barrucadu on 2008-05-15
Can you please explain where you got the idea that Swarms works for MS?

---

### Post by BlueSkyNIS on 2008-05-15
lol :lolflag: You guys are arguing just like children :)

---

### Post by earos.dk on 2008-05-15
I got it, 
Swarms feel that I am a competitor.
 I have another mind than him.

Here is his website and he is MS Gold Certified :-)

[www.cta.dk](www.cta.dk)

You may believe whatever you want!

But now I got it!

---

### Post by Swarms on 2008-05-15
My name is Bjørn Sivertsen, not Christian M. Andersen...
Don't know who that bloke is.

---

### Post by earos.dk on 2008-05-15
so, you have many names and you don't know which one belongs to you anymore?

---

### Post by earos.dk on 2008-05-15
Hey, we are all waiting for your answer!

---

### Post by Swarms on 2008-05-15
So you have a better idea who I am, than myself?
Damn, impressive!

---

### Post by earos.dk on 2008-05-15
Because now I know who you are.

Anyway, this threat is closed from my comment,
 
and next time Christian M. Andersen, now alias name Bjørn Sivertsen,

there is no answer to you.

Then you need to find another new name.

BTW: I can't understand how MS does accept your behaviour?

---

### Post by Swarms on 2008-05-15
You say you won't comment me anymore, but then again you have done that twice, and broke your promise every time, you are quite the untrustworthy guy right? :)

No I have no relations to that dude, but if you are so scared of the world, that you have to make conspiracies for it to make sense to you, then be my guest. :)

---

### Post by earos.dk on 2008-05-15
You also called my cell phone three times tonight, but it is closed for secret numbers.

Don't worry, a new release is coming out, and nobody can stop it!

---

### Post by Swarms on 2008-05-15
Now you did it again!
Its as simple as I saw your ad on recordere.dk, gave some input, got sweared at, and you left,
Now I saw your ad at ubuntuforums and wanted to have another go.
Heck, I don't even have money to prank call.

Damn I love silly arguments at late night.

---

### Post by earos.dk on 2008-05-15
I know who you are and that's it.

Well, now I will close down this computer and forget about Swarms, alias a ton of names.
Else I do continue to answer and nothing will be made.

Can't stop it, just the power button can :-)

---

### Post by bigbrovar on 2008-05-15
earos.dk u sure have the wrong attitude .. Swarms was just trying to seek clarification on some important issues .. instead u call him all sort of names .. its really sad mahn and am very disappointed with ur attitude ..i expected a bit more maturity .. nobody in Life is above being questioned .. 

BTW ur project is awesome and it shows gpl and making money are not in contradiction .. keep it up ..

---

### Post by Swarms on 2008-05-15
Ok, you got me, my real name is Steven Seagal, Bjørn Sivertsen is just a character  have created to hide from the IRS. But don't know who this Mr. Microsoft Tomboy is.

Sleep tight.

---

### Post by earos.dk on 2008-05-15
bigbrovar,

it is no secret that I don't like the business model of MS -- no name.

NOW: The power button is pressed :)

Sleep well,

while I will go down and make the "final" for this time.

---

### Post by earos.dk on 2008-05-15
I am very close to prove who this MS troll is.

Roger all over :-)

---

### Post by p_quarles on 2008-05-15
Thread closed. Ubuntu Forums has conduct guidelines which have been repeatedly broken throughout this thread.

---

