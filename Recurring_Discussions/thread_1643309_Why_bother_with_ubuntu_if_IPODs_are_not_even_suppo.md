---
title: "Why bother with ubuntu if IPODs are not even supported?"
date: 2010-12-11
forum: Recurring Discussions
---

### Post by wishfullink on 2010-12-11
seriously? why am i recommending ubuntu left and right if a device as basic and widespread as the apple ipod is not supported? 

just food for thought here.

---

### Post by oldsoundguy on 2010-12-11
Because Ubuntu is an operating system for a computer.  Toys take a back seat to real working computing, and Ubuntu fits the bill.

AND, there are other players that work out of the box in Linux .. you don't have to be like every other person and have to use a iPOD and finance Apple when you want to get downloads.

---

### Post by 3rdalbum on 2010-12-11
1. iPods *are* supported.
2. There's nothing "basic" about supporting iPods. Apple designs them to be locked to the iTunes software.
3. This belongs in Cafe, not in Help.

---

### Post by slooksterpsv on 2010-12-11
Post #3 is correct, iPods do work on Ubuntu; maybe not the software update portion. But if you want to do that, just run a Virtualization of Windows XP, Vista, or Windows 7.

---

### Post by ivarn on 2010-12-11
@ #2 "toys" lol. Most things you use a pc for is toying.
But yea, iPods are fully supported and most of them will work when you plug them into the pc. In windows you have to use iTunes to sync it but here u can use basically every media program you want, (rhythmbox, songbird, banshee, atunes, ubunto one etc... ).
So yea, do some research before you complain about things.

> **3rdalbum said:**
> 1. Apple designs them to be locked to the iTunes software.
Not anymore. It was locked though.

---

### Post by Sef on 2010-12-11
Another why use X if y is not supported? Moved to Recurring discussions.

---

### Post by Spice Weasel on 2010-12-11
You should demand a refund.

I'm sorry, someone has already said what I was planning to.

> 
1. iPods *are* supported.
2. There's nothing "basic" about supporting iPods. Apple designs them to be locked to the iTunes software.


---

### Post by oldsoundguy on 2010-12-11
> **ivarn said:**
> @ #2 "toys" lol. Most things you use a pc for is toying.
But yea, iPods are fully supported and most of them will work when you plug them into the pc. In windows you have to use iTunes to sync it but here u can use basically every media program you want, (rhythmbox, songbird, banshee, atunes, ubunto one etc... ).
So yea, do some research before you complain about things.


Not anymore. It was locked though.

beg to differ, I use my computers for COMPUTING .. work of some sort.  Of courses, I am well over 16 years old and started out on computers before most here were born. (Early 1980's on an 8086 and an Apple.  We used the Apple in the studio and the 8086 in the office.)
At that time, most things done on a computer involved making a buck.
The computer is a tool for making the job easier, not just for dinking around and wasting time.

BTW, I heard Songbird is soon to be a dead issue unless it gets forked.

---

### Post by uRock on 2010-12-11
> **wishfullink said:**
> seriously? why am i recommending ubuntu left and right if a device as basic and widespread as the apple ipod is not supported? 

just food for thought here.
As many have stated, iPods are supported.

---

### Post by C0derBear on 2010-12-11
iPod / iPhone are *not* fully supported on any version of MS Windows until *after* you install iTunes, QuickTime, and the supporting drivers and service components that come with it.

I don't know, but would not be surprised if the Mac OS required additional components for full support.

If Apple chose to provide the iTunes component natively for GNU/Linux then it would be as fully supported. They don't need to do the driver component as the FOSS community has already taken care of that. ;^)

FWIW: I have an iPhone and the software upgrade via iTunes from within a virtualized Windows 7 sessions ( VirtualBox ) does *not* completely work because of how the phone reboots and becomes different USB devices. No matter how quickly I tell vbox to pass it on to the client it does not complete. I needed a native system to do that.

---

### Post by wishfullink on 2010-12-11
Thanks for the input guys :)

[LIST]
[*]virtualization doesn't work without hours of hacking.

[*]the latest ipods IOS4 are still not supported.
[/LIST]

---

### Post by wilee-nilee on 2010-12-11
I guess I will have to get a IPOD so I can get rid of this pesky open source, not sure why this hadn't occurred to me before.:popcorn:

---

### Post by KL_72_TR on 2010-12-11
> **wishfullink said:**
> seriously? why am i recommending ubuntu left and right if a device as basic and widespread as the apple ipod is not supported? 

just food for thought here.
Go to this link and you will find the answer to your problem: [https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)
Happy Linux everybody :-)

---

### Post by StephenDavison on 2010-12-11
Simple.  I guess that I wouldn't recommend Ubuntu nor any other Linux based OS if iPods and iPhones were my main concern.  In that case I'd recommend buying a Mac.  But you have to remember that iPods are not the center of the universe for many people.  There are many, many other reasons "to bother with Ubuntu."

---

### Post by slooksterpsv on 2010-12-11
> **wishfullink said:**
> Thanks for the input guys :)

[LIST]
**[*]virtualization doesn't work without hours of hacking.]**

[*]the latest ipods IOS4 are still not supported.
[/LIST]

Are you kidding me? It couldn't be simpler:

1. Visit [http://www.virtualbox.org/](http://www.virtualbox.org/) and download the latest version of VirtualBox (not the OSE, they call it PUEL, but when you go to download it goes to PUEL)

2. Install

3. Get your windows cd/iso

4. Click System -> Administration -> users and groups -> Manage Groups -> vboxusers -> properties -> put a check on your name. Then log out and log back in.

5. Open VirtualBox, create a new vm with at least the following:
XP - 512MB RAM, 20GB HDD
Vista - 1024MB RAM, 40GB HDD
7 - 1024MB RAM, 40GB HDD

6. Go to the Settings on the VM, then to USB, then, make sure to enable usb and usb 2.0 are selected, plug in iPod, click on the green + usb icon, choose Apple iPod/iPhone

7. Start the VM and load the cd or ISO.

8. Install the OS (may take a bit depending on computers configuration).

9. Install iTunes

And you're done!

That shouldn't be too difficult.

---

### Post by Spice Weasel on 2010-12-12
> **slooksterpsv said:**
> Are you kidding me? It couldn't be simpler:

1. Visit [http://www.virtualbox.org/](http://www.virtualbox.org/) and download the latest version of VirtualBox (not the OSE, they call it PUEL, but when you go to download it goes to PUEL)

2. Install

3. Get your windows cd/iso

4. Click System -> Administration -> users and groups -> Manage Groups -> vboxusers -> properties -> put a check on your name. Then log out and log back in.

5. Open VirtualBox, create a new vm with at least the following:
XP - 512MB RAM, 20GB HDD
Vista - 1024MB RAM, 40GB HDD
7 - 1024MB RAM, 40GB HDD

6. Go to the Settings on the VM, then to USB, then, make sure to enable usb and usb 2.0 are selected, plug in iPod, click on the green + usb icon, choose Apple iPod/iPhone

7. Start the VM and load the cd or ISO.

8. Install the OS (may take a bit depending on computers configuration).

9. Install iTunes

And you're done!

That shouldn't be too difficult.

You can skip steps 1 and 4 by hitting sudo apt-get install virtualbox in to a terminal.

---

### Post by Linux_junkie on 2010-12-12
How about instead of buying am ipod/iphone why not buy a digital player that supports ogg vorbis/Theora?

---

### Post by andymorton on 2010-12-12
> **wishfullink said:**
> Thanks for the input guys :)

[LIST]
[*]virtualization doesn't work without hours of hacking.

[*]the latest ipods IOS4 are still not supported.
[/LIST]

Blame Apple for being control freaks rather than Ubuntu.

---

### Post by fugazi32 on 2010-12-12
> **wishfullink said:**
> seriously? why am i recommending ubuntu left and right if a device as basic and widespread as the apple ipod is not supported? 

just food for thought here.

Erm...iPods ARE supported!!!!!!!!! I've got mine plugged in and working right now, and I don't have to use that heap of trash called iTunes to be able to use it. GTKpod all the way baby! ;)

---

### Post by rjbl on 2010-12-12
Err .... what's an iPod and why does it matter?

rjbl

---

### Post by C0derBear on 2010-12-12
> **rjbl said:**
> Err .... what's an iPod and why does it matter?

a. It's an overpriced Sony Walkman replacement.

b. dunno

---

### Post by Junosix on 2010-12-12
> **C0derBear said:**
> 

FWIW: I have an iPhone and the software upgrade via iTunes from within a virtualized Windows 7 sessions ( VirtualBox ) does *not* completely work because of how the phone reboots and becomes different USB devices. No matter how quickly I tell vbox to pass it on to the client it does not complete. I needed a native system to do that.

VirtualBox... Settings... USB...

Edit the filter for the iPhone so that the only information in there is the device name (which can be anything you like), and the vendor ID.  Delete everything else in that box.  Works a treat.

---

### Post by bouncingwilf on 2010-12-12
Perhaps "Why bother with IPods if Ubuntu not supported" would have been a more pertinent question.

Bouncingwilf

---

### Post by slooksterpsv on 2010-12-12
> **Spice Weasel said:**
> You can skip steps 1 and 4 by hitting sudo apt-get install virtualbox in to a terminal.

Eh.... I don't like doing that personally cause it's outdated. And like on 3.2.8 I believe or it could be 3.2.10, you can't install Maverick Meerkat in a VM on that version cause of a bug. So I use the latest.

---

### Post by Tibuda on 2010-12-12
Because I dont have an iPod.

---

### Post by C0derBear on 2010-12-12
> **Junosix said:**
> VirtualBox... Settings... USB...

Edit the filter for the iPhone so that the only information in there is the device name (which can be anything you like), and the vendor ID.  Delete everything else in that box.  Works a treat.

Nice tip. Changed the settings, we'll see how it goes next time. ;^)

---

### Post by jshepherd on 2010-12-12
> **Linux_junkie said:**
> How about instead of buying am ipod/iphone why not buy a digital player that supports ogg vorbis/Theora?

I have an ipod. I have an ipod because  I like them. I like Ubuntu too, that's why I use it. Why I should compromise on what I like because it doesn't conform to ideological views. I like Ubuntu and will always promote open source where I can but to be frank, almost all the other music players on the market which use a non proprietory format are unattractive to me.

But, re the original post, I dual boot with Windows 7 and sync with media monkey.

---

### Post by medic2000 on 2010-12-12
Hmm why not supporting iPod? First of all what is iPod? Oo this proprietary thing that you can not transfer music without some company's some program?

Why people buying keep buying this. There are many good and open and easy to use(general interface and you can transfer all of your music by just plugging the usb cable) and supporting more formats (including ogg and flac).

So...
Why bother with iPod?

---

### Post by weasel fierce on 2010-12-13
Why bother with ipods if Ubuntu isn't supported?

---

### Post by cascade9 on 2010-12-13
> **jshepherd said:**
> I have an ipod. I have an ipod because  I like them. I like Ubuntu too, that's why I use it. Why I should compromise on what I like because it doesn't conform to ideological views. I like Ubuntu and will always promote open source where I can but to be frank, almost all the other music players on the market which use a non proprietory format are unattractive to me.

But, re the original post, I dual boot with Windows 7 and sync with media monkey.

Whats so bad about iriver, sansa, cowon (and probably others I've forgotten about) media players?

---

### Post by ivanovnegro on 2010-12-13
> **medic2000 said:**
> Hmm why not supporting iPod? First of all what is iPod? Oo this proprietary thing that you can not transfer music without some company's some program?

Why people buying keep buying this. There are many good and open and easy to use(general interface and you can transfer all of your music by just plugging the usb cable) and supporting more formats (including ogg and flac).

So...
Why bother with iPod?

Thats it!

I can really not understand why people are buying this Apple things, its simply too expansive and not 100% compatible with other OS's or music formats.
And this iPod stuff has nothing to do with Ubuntu, its related with Apple or Macs.
I am using Ubuntu as my primary and only OS, for me Linux is an alternative, so I try to use alternative apps also that you can find in the Open Source world and also alternative devices for music.

---

### Post by jshepherd on 2010-12-13
It's not so much that *ipods* aren't supported but more that *itunes *isn't supported.

---

### Post by jshepherd on 2010-12-13
> **cascade9 said:**
> Whats so bad about iriver, sansa, cowon (and probably others I've forgotten about) media players?

I haven't tried the others but my daughter has a Sansa Fuze and that is even worse than the ipod in Ubuntu!

---

### Post by Verbeck on 2010-12-13
> **Spice Weasel said:**
> You can skip steps 1 and 4 by hitting sudo apt-get install virtualbox in to a terminal.
usb isn't supported by the one in the repos

---

### Post by cascade9 on 2010-12-13
> **jshepherd said:**
> I haven't tried the others but my daughter has a Sansa Fuze and that is even worse than the ipod in Ubuntu!

What do you mean 'worse'? 

I havent used a sansa for ages, but last time I did they mounted as a normal USB mass storage device (provided that its in MSC mode)

---

### Post by jshepherd on 2010-12-13
> **cascade9 said:**
> What do you mean 'worse'? 

I havent used a sansa for ages, but last time I did they mounted as a normal USB mass storage device (provided that its in MSC mode)

More difficult to use.

Almost anything will mount as a USB mass storage device but the difference between full support and just mounting the device is the difference between conveniently converting files and transferring to the player or having to tediously drag and drop perhaps hundreds of files.
Besides that I use my ipod for video too and to the best of my knowledge GTKPOD doesn't help in this respect.
Although I'd be extremely happy to be proved wrong.
I only really use Windows for media...and Office 2007 outlook so if I can switch to Ubuntu for media use I only need a decent office suite to dump Windows altogether.

---

### Post by Rasa1111 on 2010-12-13
Yeah you are totally right OP.

 why bother with Ubuntu if it's not compatible with an ipod! 
Makes perfect sense. 
Perfect logic. 

:rolleyes:

not everyone in the world is addicted to apple products. 

"what good is ubuntu if you can't use ipod?"

:lol:

 why not take it up with beloved apple?
itunes is your culprit. 

amazing thread.

---

### Post by RoflHaxBbq on 2010-12-14
Perhaps you should run back to some apple fanboy forums where you belong and brag about your uber 1337 apple coolness.

If you knew *anything *about computers you would know that the problem is not Ubuntu, but with the monopolization of the computer industry by apple, who have purposely "locked" iPlod to iTunes, just to hold down Linux. Why? Because Apple knows that Linux outclasses Mac in every way and need to use monopolization techniques to hold Linux down, just so they can make a buck.

---

### Post by trinitydan on 2010-12-14
> **medic2000 said:**
> Hmm why not supporting iPod? First of all what is iPod? Oo this proprietary thing that you can not transfer music without some company's some program?

Why people buying keep buying this. There are many good and open and easy to use(general interface and you can transfer all of your music by just plugging the usb cable) and supporting more formats (including ogg and flac).

So...
Why bother with iPod?

> **weasel fierce said:**
> Why bother with ipods if Ubuntu isn't supported?

Indeed.  

I am an iPod owner, but I have always been bothered by the restrictive software you have to use sync your iPod.  I am not going to buy another iPod/iPhone until Apple releases a open source linux version of iTunes (read never).  Maybe an Android device?  Whatever I get, it will not be an Apple device.

As for iPod support, I just use Rhythymbox to sync my music to my iPods (80gb and 160gb classics and an 8gb 1st gen iPod touch) and GPixPod for my pictures.  I don't watch videos on my little iPod screens so the lack of video support hasn't been an issue for me. 

You should express your grievances to Apple.  I did.

[http://www.apple.com/feedback/itunesapp.html](http://www.apple.com/feedback/itunesapp.html)

---

### Post by slackthumbz on 2010-12-14
Why bother with an ipod when most of us probably have smartphones? I just plug my n900 into my laptop via usb and drag and drop the music/movies I want. It's simple and platform independent. Not only that but my phone supports a hell of a lot more media formats than an ipod or any of the idevices.

Stand alone media players are obsolete y'all :)

---

### Post by aytech on 2010-12-14
Why bother with IPods if even Ubuntu is not supported? 
 
Actually ubuntu does have support for ipods, but i wouldnt bother anyway :wink:

---

### Post by cascade9 on 2010-12-14
> **jshepherd said:**
> More difficult to use.

Almost anything will mount as a USB mass storage device but the difference between full support and just mounting the device is the difference between conveniently converting files and transferring to the player or having to tediously drag and drop perhaps hundreds of files.


You've got a totally different style of use to me then....... Besides that, I've never found that any of the media mangment/syncing programs make life any eiser for me.

---

### Post by slackthumbz on 2010-12-14
> **cascade9 said:**
> You've got a totally different style of use to me then....... Besides that, I've never found that any of the media mangment/syncing programs make life any eiser for me.

Tedious? nah, I just drag and drop the playlist straight from rhythmbox to the device and it copies all the files for me. 

Pretty simple and easy if you ask me.

---

### Post by julio_cortez on 2010-12-14
> **ivanovnegro said:**
> I can really not understand why people are  buying this Apple things, its simply too expansive and not 100%  compatible with other OS's or music formats.Maybe they have  particular needs. When I had to choose a portable music player I went  specifically for a Walkman because of ATRAC's support to gapless  playback (thing that simple mp3s don't have).
It's not supported in Ubuntu as far as I know, but I knew I had to use SonicStage and it was a downside I accepted in order to have a player supporting gapless playback.
It's a matter of choice:
- if someone prefers Ubuntu over iPod, he/she may change his/her portable player.
- if someone prefers iPod over Ubuntu, he/she may change his/her OS (or try something suggested before like a VM, as it's proven that iPods work with Ubuntu in a way or another).

> **C0derBear said:**
> a. It's an overpriced Sony Walkman replacement.
 At least iPods DO work with Ubuntu. Both my Sont Walkmen don't.
 *Well, the fact that one of them is still a cassette-reader maybe means something..*

---

### Post by ivanovnegro on 2010-12-14
> **julio_cortez said:**
> Maybe they have  particular needs. When I had to choose a portable music player I went  specifically for a Walkman because of ATRAC's support to gapless  playback (thing that simple mp3s don't have).
It's not supported in Ubuntu as far as I know, but I knew I had to use SonicStage and it was a downside I accepted in order to have a player supporting gapless playback.
It's a matter of choice:
- if someone prefers Ubuntu over iPod, he/she may change his/her portable player.
- if someone prefers iPod over Ubuntu, he/she may change his/her OS (or try something suggested before like a VM, as it's proven that iPods work with Ubuntu in a way or another).


 

Yes, you are right, I prefer Ubuntu and thats the reason why e.g I throwed away my Creative MTP device that wasnt compatible with Ubuntu and took another device. I changed with my girlfriend because she has also XP installed.
People have the choice, I prefer Ubuntu, so I will not take an iPod.
Its true, if someone prefer to have 100 % compatibilty with iPods maybe he has to change to a Mac. But I think Linux did very much to make it work with iPods, of course not its not perfect.

---

### Post by Zlatan on 2010-12-14
> **wishfullink said:**
> seriously? why am i recommending ubuntu left and right if a device as basic and widespread as the apple ipod is not supported? 

just food for thought here.

why bother with ipod when your phone has mp3 (or even video) player?

---

### Post by cyberphrog on 2010-12-14
I don't own an iPoddy.

---

### Post by uRock on 2010-12-14
> **julio_cortez said:**
> At least iPods DO work with Ubuntu. Both my Sont Walkmen don't.
 *Well, the fact that one of them is still a cassette-reader maybe means something..*
We have two Sony Walkmans and both work without any problems. They are mounted as a USB storage. Just drag and drop, which is much faster and easier than using WMP in Windows to sync with the things.

---

### Post by philinux on 2010-12-14
Someone got itunes working.

[http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html](http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html)

---

### Post by ivanovnegro on 2010-12-14
> **uRock said:**
> We have two Sony Walkmans and both work without any problems. They are mounted as a USB storage. Just drag and drop, which is much faster and easier than using WMP in Windows to sync with the things.

And thats also true, drag and drop is much faster as to sync.
When you have tagged properly your tracks you even dont need to sync, in my experience this is too slow and it was also in Windows.

---

### Post by julio_cortez on 2010-12-14
> **uRock said:**
> We have two Sony Walkmans and both work without any problems. They are mounted as a USB storage. Just drag and drop, which is much faster and easier than using WMP in Windows to sync with the things.Can I ask you which models are you using?
Drag 'n' drop unfortunately doesn't work for me (NW-E005 here): the Walkman can be used as storage device, but the items I drag and drop in it just can't be played when I turn it on. Unfortunately this is one of the models that wrap every audio file in their proprietary format :'(

I've read that [Symphonic]("http://sourceforge.net/projects/symphonic/") can handle file transferring to my device, but I haven't tried it yet (and I wonder whether it can handle ATRAC files right, might give it a try sooner or later).

---

### Post by aysiu on 2010-12-14
> **wishfullink said:**
> seriously? why am i recommending ubuntu left and right if a device as basic and widespread as the apple ipod is not supported? 

just food for thought here.
I don't know why you're recommending Ubuntu left and right.

I don't recommend Ubuntu left and right, because almost all of my friends have an iPhone or iPod Touch.

The support for iPods in Ubuntu exists, but it is not nearly the seamless experience iTunes offers, and once the next firmware update appears for iOS, you have no idea when libimobiledevice will catch up.

You can technically use an iPod with Ubuntu, but I'd recommend against it. If you want an iPod badly, I'd recommend Mac or Windows. If you want Ubuntu badly, I'd recommend a Sandisk player or an Android phone.

---

### Post by pricetech on 2010-12-14
Dang.  I just realized I should hack my computer to pieces (literally, with an ax) just because my bluetooth adapter, which works without a hitch in Ubuntu, doesn't work in windows.

If your ipod is mission critical for you, then buy an apple computer to go with it.

Problem solved.

---

### Post by Shintek on 2010-12-14
Whats the big deal? Pods from apple suck anyway

There are thousands of packages that enable support!

---

### Post by Rasa1111 on 2010-12-15
> **Shintek said:**
> **Whats the big deal? Pods from apple suck anyway**

There are thousands of packages that enable support!


lol, right.
 I don't think there is a "big deal"..
 simply a case of OP not thinking before they posted pure rubbish. :rolleyes:

---

### Post by RiceMonster on 2010-12-15
> **weasel fierce said:**
> Why bother with ipods if Ubuntu isn't supported?

Why bother with my wireless card if Ubuntu isn't supported?
Why bother with my webcam if Ubuntu isn't supported?
Why bother with my printer if Ubuntu is supported?

> **ivanovnegro said:**
> I can really not understand why people are buying this Apple things, its simply too expansive and **not 100% compatible with other OS's or music formats.**

How many people who buy iPods do you think actually care about that?


> **slackthumbz said:**
> Why bother with an ipod when most of us probably have smartphones? I just plug my n900 into my laptop via usb and drag and drop the music/movies I want. It's simple and platform independent. Not only that but my phone supports a hell of a lot more media formats than an ipod or any of the idevices.

Stand alone media players are obsolete y'all :)

What if you've got an iPhone? Basically you're in the same situation as with an iPod.

---

### Post by arbitrarychoiceofmoniker on 2010-12-15
It doesn't boil down to lack of support.

iPod and iPhone support has been developed and chased for a long time, and we get/approach interoperability. Nothing outrageous, nothing illegal, just simple bog-standard interoperability.

What happens is Apple seems to constructively break that support with firmware updates etcetera.

For it to work, all that would have had to happen is for Apple to not bother to break it - they didn't even have to bother to develop the libs themselves!

Now if you don't care that the company you're buying something from seems to be deliberately breaking interoperability for you, and is dictating what OS/music softwares you can use on another device - and you keep buying stuff from them without saying a word, well, you get what you deserve. You're a consumer with money, you make your own choices, and you choose to reward lock-in.

Open source developers have spent time and therefore money supporting iPods and iPhones, and their efforts have been dumped on - I don't see why GNU/Linux and its developers get one iota of blame for the fact that Apple has stomped on their efforts.

Your lack of support has nothing to do with open source developers, and everything to do with Apple. You may use your computer and media player together, but only on Apple's terms. Why don't you go and ask THEM why?


> **RiceMonster said:**
> 
How many people who buy iPods do you think actually care about that?

Yeah, well if you don't care about that sort of thing you and learn your lesson, you only have yourself to blame.

Whether it's rebuying your iTunes library for stupid arbitrary reasons, not being able to put your tunes on someone else's computer for a party, or not being able to drop music on it using USB mass storage, or copy it where you like.

Life is hard, and it's the DRM and lock-in by the single hardware vendor that sucks, not the whole rest of the (sometimes-interoperable-maybe) world.

---

### Post by medic2000 on 2010-12-15
> **jshepherd said:**
> I haven't tried the others but my daughter has a Sansa Fuze and that is even worse than the ipod in Ubuntu!

This is just funny. You are misleading people. You can plug your Fuze and start copying either from device to computer either from computer to device. 

You say this is worse? Really? How this is worse? And worse than what? Compared to ipod?.What does ipod do when you plug? Oooh i think i connects your brain, understand what you want listen at that moment, then connects to internet download the music and copy it to your ipod. After that even you can not realise what is happening earings are in your and you are listening the music you imagined. Because Apple is the best.

And i wonder do you know the meaning of worse? Maybe you are trying to say "greater"?

---

### Post by ivarn on 2010-12-15
> **wishfullink said:**
> Thanks for the input guys :)

[LIST]
[*]virtualization doesn't work without hours of hacking.
[*]the latest ipods IOS4 are still not supported.
[/LIST]

Wrong, there are software out there to jailbreak the new framewire.
Ever heard of Limera1n? Here's how you run it on linux.
[http://www.youtube.com/watch?v=Rtx3qvcf4fI](http://www.youtube.com/watch?v=Rtx3qvcf4fI)

---

### Post by aytech on 2010-12-15
"I'll buy anything that's shiny and made by Apple" :lolflag:

---

### Post by ivanovnegro on 2010-12-15
> **RiceMonster said:**
> 



How many people who buy iPods do you think actually care about that?






Exactly the problem, thats why I cannot understand it, they dont care.
Why the whole world is using almost Windows? Because they also dont care.
If nobody would care about nothing the world would be even worse.

---

### Post by rg4w on 2010-12-15
> **jshepherd said:**
> I have an ipod. I have an ipod because  I like them. I like Ubuntu too, that's why I use it. Why I should compromise on what I like because it doesn't conform to ideological views.
You may want to post your question here:
[http://discussions.apple.com/category.jspa?categoryID=221](http://discussions.apple.com/category.jspa?categoryID=221)

...or here:
[http://mpa.org/contact_us/](http://mpa.org/contact_us/)

---

### Post by Zlatan on 2010-12-22
> **arbitrarychoiceofmoniker said:**
> It doesn't boil down to lack of support.

iPod and iPhone support has been developed and chased for a long time, and we get/approach interoperability. Nothing outrageous, nothing illegal, just simple bog-standard interoperability.

What happens is Apple seems to constructively break that support with firmware updates etcetera.

For it to work, all that would have had to happen is for Apple to not bother to break it - they didn't even have to bother to develop the libs themselves!

Now if you don't care that the company you're buying something from seems to be deliberately breaking interoperability for you, and is dictating what OS/music softwares you can use on another device - and you keep buying stuff from them without saying a word, well, you get what you deserve. You're a consumer with money, you make your own choices, and you choose to reward lock-in.

Open source developers have spent time and therefore money supporting iPods and iPhones, and their efforts have been dumped on - I don't see why GNU/Linux and its developers get one iota of blame for the fact that Apple has stomped on their efforts.

Your lack of support has nothing to do with open source developers, and everything to do with Apple. You may use your computer and media player together, but only on Apple's terms. Why don't you go and ask THEM why?




Yeah, well if you don't care about that sort of thing you and learn your lesson, you only have yourself to blame.

Whether it's rebuying your iTunes library for stupid arbitrary reasons, not being able to put your tunes on someone else's computer for a party, or not being able to drop music on it using USB mass storage, or copy it where you like.

Life is hard, and it's the DRM and lock-in by the single hardware vendor that sucks, not the whole rest of the (sometimes-interoperable-maybe) world.

amen

---

### Post by beew on 2010-12-22
Why bother with ipod if it is deliberately designed in such a way that it wouldn't work cross platform?

---

### Post by Roasted on 2010-12-22
> **beew said:**
> Why bother with ipod if it is deliberately designed in such a way that it wouldn't work cross platform?

This.

---

### Post by amjjawad on 2010-12-22
[B]No OS is perfect, period.
[/B]

---

### Post by NCLI on 2010-12-22
> **julio_cortez said:**
> Maybe they have  particular needs. When I had to choose a portable music player I went  specifically for a Walkman because of ATRAC's support to gapless  playback (thing that simple mp3s don't have).
All formats support gapless playback, it's a software issue. My Cowon S9 supports gapless playback for MP3, flac, wav, etc.

---

### Post by Tibuda on 2010-12-22
> **NCLI said:**
> All formats support gapless playback, it's a software issue. My Cowon S9 supports gapless playback for MP3, flac, wav, etc.

I think that by "simple mp3s" he means "simple mp3 players", not the mp3 format.

---

### Post by dondiego2 on 2010-12-22
I had an iPod before I started using Ubuntu.  I love it!  It's a 60 gig HD based model and I use it with Ubuntu.  It took me a while to figure things out and get some programs I was comfortable with, but now that I am, I would not go back to iTunes.  I tried other music players and I have a Sansa Clip but I hardly ever use it.  I keep going back to my iPod.  I love the simplistic, intuitive design and I love Ubuntu the same way.  

I use RhythmBox for music and gPodder for podcasts and I have a car radio with iPod hook-up and control.  I also have an Droid and I occasionally use it to listen to music but I keep going back to the iPod.  If I want to buy music on-line I go to Amazon mp3 downloads.  Better quality and better price.   

I suppose if my iPod broke I would use my Droid more, or the Sansa Clip, but I would miss it.  I don't hate any company and I think Apple designs some great products.  I don't understand why it gets so personal to people on this forum.  This is a capitalist society and I don't begrudge anyone for wanting to make money.  The goal is to design a product that people will like and Apple has done that with the iPod.  I would probably have an iPhone if Verizon carried them since I have been very happy with the iPod.

---

### Post by inobe on 2010-12-22
to the op, get your ipod and plug it into anything you want, if it doesn't work "for you" use what works for you.

remember, as with any operating system, individual results may vary :mrgreen:

---

