---
title: "[SOLVED] My partition"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Georgia boy on 2008-08-14
Hi. I've gotten the Live CD for Ubuntu 8.04. I really like what I have seen and been playing with so far. Thinking about doing a dual boot with my Windows XP. I've watched a few videos and read several tutorials on doing this. On all of their examples they always show their partitions as Windows NFTS. 
I did a check on my hard drive set up with the live CD and below is what I found:

Partition
	File System
	Label
	Size
	Used
	Unused
	Flags
/dev/sda1
	NFTS
	Hp Pavilion
	224.33 GB
	21.91 GB
	202.42 GB
	Boot
Unallocated
	Unallocated
	
	7.84Mlb
	...
	...
	
/dev/sda2
	Fat32
	
	8.55 GB
	8.10 GB
	456.02MLB
	lba

	
Does this look like there might be a conflict with the installation of Ubuntu? I mean when I looked at the examples of using the first choice of installation it comes back with a slider bar to adjust for how much space you want for Windows and how much you want for Ubuntu. Will all of the above show as under the one spot for Windows? 
Will Ubuntu try to go into the Fat32> That is where my HP has set up their recovery partition of the hard drive. 
I know, stupid questions but I need to know. I want to have all of the ducks lined up in my mind when I do the dual boot installation. I don't want to mess something up by accident. 
Looks like I have plenty of space to give both Windows and Ubuntu plenty of room to grow in.
All advice and help is greatly appreciated. 
I thank you all in advance.
Tom

---

### Post by Elfy on 2008-08-14
It will only install on the small drive if you tell it to do so. The partition editor should see 2 partitions sda1 and sda2, you wnat to install to sda1.

Make sure you degrag a couple of times before you try to resize the partition with the installer.

---

### Post by Georgia boy on 2008-08-14
I've defraged the hard drive and also did the check disk for errors. So, when I do the installation I should clck on the first type of install and let Ubuntu do it's own check right? Then it'll show just two partitons with the NFTS on one side and then the free spot with the slider to adjust for the  sizing of the partitions? Or, will it show the NFTS, FAT32 and then the free space to install the Ubuntu and use the slider to determine the size of gigabyte I want to asssign the Windows and Ubuntu? I know, it seems dumb but I get kind of confused at times when reading and watching the videos. Last time I did anything other than Windows was back in the early ninities when I took a Works course using DOS. Right after that I learned Windows 3.0 and had been with Windows since then. But, I'm always reading and trying to learn new things. I use open source when possible. I use Firefox, Thunderbird, OpenOffice.org and other open source when possible. I'm trying to wean myself off of Windows and learn a better and more secure product. I enjoy learning things like that and transfering over. I have learned a lot from Forums and the kind people who take their time to help someone like me. 
Please bear with me on my stumbling through this proccess. As I stated before, I want to do everything right and not do something dumb to my system by overlooking stuff during installation etc. 
Again, I thank everyone in advance for all of the help.
Tom

---

### Post by Elfy on 2008-08-14
Hi - questions are a lot easier to answer before we get to "I think windows is gone" ones lol.

It's a long time since I used the 'auto' methods, but if you look at aysiu's page on [partitioning]("http://www.psychocats.net/ubuntu/installing#partitioning") it should help you - ideally you have more control doing it manually, but if you have never done so it can be a bit daunting.

I used the Guided resize and use freed space option if I remember correctly. Check out the whole of the aysiu installation page - [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) - well worth the time.

> Please bear with me on my stumbling through this proccess.There is no rush - and it's better to stumble than fall.

One last thing could you put a bit more white space in your threads if there is a lot of text, there are a lot of people here who's first language isn't english so it can help them understand when you have problems.

Good luck - and come back if you have more questions.

---

### Post by Paqman on 2008-08-14
With the latest version of Ubuntu you've also got the option to skip disk partitioning altogether.

The Wubi installer can create a virtual hard drive on an existing partition, and install the system there. More info on the [Wubi site](http://wubi-installer.org/). You can migrate a Wubi-installed copy of Ubuntu to it's own partition at a later date if you want.

If you've got a LiveCD, just pop it in the drive while running Windows to start the installer.

---

### Post by Georgia boy on 2008-08-14
Thanks. Sorry about the spacing between the lines. I'm so used

to just start typing and keep on going. I'm using the 8.04 Hardy 

Live CD. ForestPixie, thanks for the idea of Aysiu's page. I 

have been there reading a lot on that site. It is a very useful 

site indeed.I've had someone 

else mention about the manual instead of doing the first choice 

listed for installation also. I figure that would be the most 

likely place for me to do the most

damage to myself. But, who knows? I could probable just as easy 

do that anyway you go if I don't pay attention right?

Paqman, thanks for the suggestion of the Wubi also. That is also 

one of the things I have been reading about. Got that infomartion

from an email that CNet.com sends to me. Very interesting 

article on that. I enjoy reading on the various things that are 

happening. It's just when I start to get my feet wet I don't 

want to find cement boots attached to my feet to sink me in. :)

I always enjoy the help that I get from people in the forums. I 

know that it is the voice of experience that is talking to me 

here. Whenever I have been in any forum for things that I have 

been converting to I have always received the upmost 

professional and kind help. Have never been slammed or talked 

down to. This means a lot to me when I am trying to learn a new 

system and ask what must appear to be kind of dumb questions to 

some individuals. But, it is the knowledge that is bestowed on  

me by individuals such as yourselves that has helped a lot in my 

being able to break away from some of the mainstream things.

Paqman, what do you mean by skipping partitioning all together? 

You lost me there. Please explain. All I can remember from the 

Live CD  is the Guided Resize first choice, Guided using entire 

disk, Guided using the largest space and then Manual. Most of 

the tutorials and videos I've seen say to use the Guided Resize 

selection. Then to use the slider bar to give ample room for 

operating systems. Gets kind of confusing at times don't it?

Again, all help and advice is greatly appreciated to keep those 

cement blocks off my feet.:lolflag:

Thanks in advance for all kind help.

Tom

---

### Post by Elfy on 2008-08-14
lol that's not quite what I meant - I meant use paragraphs to break it up a bit.

What Paqman is alluding to is the wubi install - if you put the disc in when running windows - it will install ubuntu inside windows, which can be removed by using the  Add/Remove in control panel.


> This means a lot to me when I am trying to learn a new system and ask what must appear to be kind of dumb questionsI know what you mean - friendly bunch here - I had to ask what bump meant...


TBH the manual option is quite painfree if you are familiar with partitioning.

---

### Post by Paqman on 2008-08-15
> **Georgia boy said:**
> 
Paqman, what do you mean by skipping partitioning all together? 


Forestpixie had it right, but i'd like to clarify.

Normally you would install Ubuntu on to a disk partition that you've created (or allowed the Ubuntu installer to create). Using Wubi  means you don't have to create any partitions. The installer runs from within Windows, and instead of creating actual physical partitions it creates virtual partitions (which are basically just files on your existing Windows partition)

Once you're installed Wubi is almost exactly the same as a traditional install. The only thing it won't do the same is that it can't hibernate and doesn't like power cuts. It isn't an emulator, and doesn't require Windows to operate. It's a proper dual-boot setup. The advantage is that you don't need to worry about doing any partitioning. All you do is tell Wubi how big the virtual partition should be and it does everything.

The [Wubi FAQ](http://wubi-installer.org/faq.php) has some good info, and if you want more in-depth stuff try the [Wubi Guide](https://wiki.ubuntu.com/WubiGuide) on the Ubuntu Wiki.

---

### Post by Georgia boy on 2008-08-15
Thanks for the information. I really appreciate it. I went to the Wubi sites and did some reading on it. I noticed where it mentinons about becoming slow and dragging over time. Defraging will make it faster again right? 

It won't attach itself into the FAT32 will it? That was set up by HP as it's own "D" drive section for recovery. Only 8.55 gigs and most of it is used up already. Can't even do a defrag on it due to not enough room for it to manuver into.:)

Just go to the Wubi site and download it to Windows or how does that work?

Do you actually get the full blown version of Ubuntu or will somethings be left out and you get them when you do the acutal install. Will you have to do an uninstall then install from the Live CD when you go full blown? 

I'll try to do one of them this weekend. Keeping my fingers crossed that I don't do any mess ups. Looks like Wubi might be the way to go at first then do the full blown. 

What does it mean by not doing hibernation? Do you even want something to hibernate? I think I uncheck that option for my computer to go into hibernation anyway. 

How am I doing on my writing now? :lolflag:

Well, again thank you for all of your help. I grately appreciate it. Yes, I'm a newbi who is constantly learning what I can and ask questions when something don't make any sense when not able to find the information by reading. Always willing to tackle something new. 

Wish me luck.

---

### Post by Elfy on 2008-08-15
> How am I doing on my writing now?well it's black on white, but yea much more readable lol

Not actually going to be able to answer the wubi questions though - other than if you have downloaded the ubuntu iso then I think the wubi installer is there already. Putting the disc in when you are runinng windows will prompt you to install I think.

As far as wher it installs I assume it would just do the normal windows thing and install it on C:.

I think it is a full installation, but not sure about the ins and outs of it as I've never used it... haven't had a windows to try it on for a long time.

---

### Post by Georgia boy on 2008-08-16
Hi. Going to stick my feet in the water this weekend. :)
Deciding to go ahead and do the automatic download from the CD. Keeping my fingers crossed. When you hear someone yelling come running with full steam ahead!!! :lolflag:

On the Windows side I'm going to have to remove and reinstall my free AVG. Says a .bin file is missing from the Update Manager. Don't know what happened between yesterday morning and today. Didn't do anything. Going to take care of that first then do the Ubuntu full install from the CD. 

I have greatly appreciated all of the help that I have been receiving. From you, Paqman and even Aysiu from the psychocat.net site. All of you have been so friendly and helpful. Pass that on to Aysiu for me please. This I greatly appreciate believe you me. 

I think for the time being that I'll give the Windows 55% and Ubuntu 45% each for their position of the hard drive. That should do the trick right? 

Again, thank you for everything you have told me. Guess you could call me an old goat but I'm always young at heart and in the mind and always trying to learn something new. As I have mentioned before, I have seen where some people were treated kind of rough and rude even but I have always been lucky and have been treated very well in all forums that I have been to. I've been to places like Openoffice.org, here, AVG, and others. Always have been treated well and had things explained to me where I could understand. Not over my head or felt put down. It's people like you and the others that make forums a wonderful place to come and learn and ask without fear of being ridiculed and put down for asking. I'm sure you have seen things like I'm talking about in some of the forums. 

Well, must take care of that AVG problem and then do the install of Ubuntu. If lucky I'll be telling you the good news and probably have something else to ask. :)

Thanks guys.

---

### Post by Elfy on 2008-08-17
You're more than welcome, if you want to than aysiu - tack it on here I'm sure he won't mind.
[http://ubuntuforums.org/showthread.php?p=5595228#post5595228](http://ubuntuforums.org/showthread.php?p=5595228#post5595228)

---

### Post by Georgia boy on 2008-08-17
I did it!!!!!!!!!
Hey guys, thanks a bunch for all of the encouragement and help that you have given me!!!!!


I installed it last night. Had trouble with the Thunderbird and Evolution for a while until I realized that I had misspelled SMTP I had it as SMPT. No damn wonder I could only receive mail but not send. :redface:

Anyhow, I just wanted to say thank you for bearing with me on all of my questions and for talking me through all of this. 

I started a new thread on being able to listen and watch what my family and friends have sent me. They use Windows. So, I'll need some help on that also. Check it out and let me know what you think.
Can't miss it. Georgia boy sent it.

Again, thanks for all of the help. I got my feet wet and no cement boots!!!!!:lolflag:

Tom

---

