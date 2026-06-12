---
title: "Ubuntu beginner here. Swapping from windows."
date: 2012-02-27
forum: New to Ubuntu
---

### Post by jordanball33 on 2012-02-27
Downloading the latest version of Ubuntu to run on my laptop. I have some kind of error where I cant connect to the internet on windows. So instead of spending money on a new OS to get it all squared away. I thought I would give Ubuntu a try. Any tips or tricks for a first timer would be great. Thanks,
Jordan

---

### Post by audiomick on 2012-02-27
I would suggest trying the live environment before you actually install. When you boot with the CD in, choose "try without changing". Make sure everything works properly. That will help you avoid installing and then discovering that something critical is giving you troulble..

Oh yeah, and backup anything that is important before you start messing around with the machine. ;)

---

### Post by snowpine on 2012-02-27
My best recommendation is to create an Ubuntu Live CD or Live USB and test-drive it in Live mode (without installing to your computer) for a couple of days or even weeks. 

If the problem with your internet connection is hardware-based then switching to Ubuntu will not solve the problem.

---

### Post by jordanball33 on 2012-02-27
i am going to run it from a usb first to try it out. 
and the internet started as a hardware problem. but after adding an external usb wifi thing, everthing worked for a year or more. got a bug somewhere and it is blocking my connection to local only. not many windows people out there willing to help. so im hoping i can just do away with it and run ubuntu on that laptop. im eager to learn somethign new anyways.

---

### Post by snowpine on 2012-02-27
I'm impressed by your courage to jump right in and replace Windows entirely. Make absolutely sure that all your favorite applications, websites, games, etc. work well in Linux before you make that leap. I am a 4-year Linux veteran and I still "dual boot" with Windows for Adobe Creative Suite, Netflix, and certain games.

---

### Post by audiomick on 2012-02-27
Yes, boot into the Live environment from USB and see if the wireless works there. If it does, problem solved. If not, post the problem here. Maybe someone can help.

---

### Post by jordanball33 on 2012-02-27
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
downloaded the second two to a flash drive. im on another computer at work. will be using this on my home laptop. of course ill back upu everything on my external hard drive. but i havent used the laptop much in the past year due to the wifi issues.

---

### Post by audiomick on 2012-02-27
I'd suggest the "Try it with USB" option. If your windows install is a bit flaky, then the Wubi install might give you grief too, I think.

---

### Post by cbanakis on 2012-02-27
Everyone is saying proceed with caution.
Try a live session.
Dual Boot.
Etc...

I'm not going to disagree with any of those thoughts.

But I just dove right in.

I used Windows, and only Windows for my whole life.

Erased Windows, and started using Ubuntu about 3 years ago.
And I never looked back.

Sure I had some trouble adjusting, but the fact is...

When you dual boot, or have a dedicated Ubuntu box setup to play around with, it just ends up being a hobby, and you learn very very slowly.

If your trying to use Ubuntu on a dedicated box or partition, its really easy to just run back to windows whenever you hit a snag.

But if you don't have windows anymore, you kinda force yourself to adjust, speeding up the process.

The advice of everyone else is probably the most intelligent and safest course.
But like I said, I just dove right into the deep end, and it worked out great for me.

---

### Post by jordanball33 on 2012-02-27
so say that ubuntu works fine and i choose to use it. 
i know that my laptop has hardware problems with the wifi. 
i know it will work with a usb network adapter dongle.
since im 99 percent sure its a software problem (verified by my computer guy, he just wanted to re install windows, which would cost money) 
im hoping i can get ubuntu and use the usb dongle for the wifi. or the usb tethering on my iphone 4s(jailbroken) 
should i get another usb dongle that is trusted to work with ubuntu? or go with what i have and try and make it work. either way the internet will be coming from my iphone. from either a usb cord or wifi transmitted form it. 

hope this is all not to confusing.

---

### Post by cbanakis on 2012-02-27
First, it should not cost you money to re-install Windows.
(Not sure why it would)

I also wanted to ask, are you 100% positive that you have a hardware problem with your wifi?

wifi adapters do break, but most of the time its just a driver issue.

As far as "trusted" hardware goes...
In my experience, it either works, or it doesn't.

If you boot to a live session, and everything works, you should be good.

If your usb wifi, and your on-board wifi do not work, then you have the option of either getting your hands dirty trying to find and install a driver in Ubuntu, or you can do some homework, and buy one that you know will work.

---

### Post by snowpine on 2012-02-27
As all of us have unanimously suggested so far: try it and see. :)

---

### Post by mastablasta on 2012-02-27
> **jordanball33 said:**
> 
should i get another usb dongle that is trusted to work with ubuntu? .

like they said try it live first to see if it all works. in linux drivers are (for the most part) part of kenrel and you USB might just work as soon as you plug it in. but you own't knwo that unless you try it. if it doesn't work then torubleshooting starts. first to see what the chip brand is then if there are any drivers out there (maybe the system will find them and offer them to download - need wired conneciton for that) or you might end up using widnows drivers with special *wrapper. *

or it might not work at all in which case you will indeed need a new one :-D

---

### Post by audiomick on 2012-02-27
I don't want to give the impression that diving in to Ubuntu is in any way dangerous. As cbanakis said, if you just "try it out", there is a danger that you will never make the jump.

I still think it is a good plan to try the live environment first. You occasionally see posts here about people who have installed only to discover that the graphics card just doesn't work or some such. Have a quick look, make sure the monitor, mouse and keyboard work, and go ahead and install. If you can determine that your wireless works in the live environment before you install, you are ahead of the game.

As far as the dongle goes, I think you can safely assume it will work. If it doesn't, you can still go off and look for another one. 

Be optimistic. :)

---

### Post by josephmills on 2012-02-27
there are alot of ways to "skin a cat". this is just my suggestion. but either way you are going to need a live something for this. 
boot the live cd/dvd/usb/network_boot/whatever I would also stay away from wubi. but that is just me. and Pick try.
then you are going to open up your terminal (ctrl+alt+t)or in the menu. then enter in these command.
for CPU info 
```
cat /proc/cpuinfo 
```
for harddisk  onfo 
```
sudo fdisk -l 
```   
for ram info 
```
free -m 
```
pci cards that are attached to the motherboard 
```
lspci -nn 
```
all usb's
```
lsusb
```

If you like then you can paste all that stuff here and we can give you some more information. This will make it so I can give you a  better anwser then I can give you now. thanks 
I hope that this helps 
Also Welcome to ubuntu forums! glade to see that you made it :)

---

### Post by cbanakis on 2012-02-27
> **audiomick said:**
> I don't want to give the impression that diving in to Ubuntu is in any way dangerous. As cbanakis said, if you just "try it out", there is a danger that you will never make the jump.

I still think it is a good plan to try the live environment first. You occasionally see posts here about people who have installed only to discover that the graphics card just doesn't work or some such. Have a quick look, make sure the monitor, mouse and keyboard work, and go ahead and install. If you can determine that your wireless works in the live environment before you install, you are ahead of the game.

As far as the dongle goes, I think you can safely assume it will work. If it doesn't, you can still go off and look for another one. 

Be optimistic. :)

Yeah, my buddy seemed very interested in Ubuntu after knowing I was using it for a couple years, and he planned to install it on an old computer he had laying around, so he could "Mess with it".

After I yelled at him, and explained how he would never use it that way, I convinced him to jump in.

It was easier for him, because he knew me, and was not limited to forums.

But he's glad he did it.

---

### Post by cbanakis on 2012-02-27
Way to scare off the newbie.

> **josephmills said:**
> there are alot of ways to "skin a cat". this is just my suggestion. but either way you are going to need a live something for this. 
boot the live cd/dvd/usb/network_boot/whatever I would also stay away from wubi. but that is just me. and Pick try.
then you are going to open up your terminal (ctrl+alt+t)or in the menu. then enter in these command.
for CPU info 
```
cat /proc/cpuinfo 
```for harddisk  onfo 
```
sudo fdisk -l 
```for ram info 
```
free -m 
```pci cards that are attached to the motherboard 
```
lspci -nn 
```all usb's
```
lsusb
```If you like then you can paste all that stuff here and we can give you some more information. This will make it so I can give you a  better anwser then I can give you now. thanks 
I hope that this helps 
Also Welcome to ubuntu forums! glade to see that you made it :)

---

### Post by snowpine on 2012-02-27
> **cbanakis said:**
> Way to scare off the newbie.

You may be projecting your own insecurities regarding the command line; I thought that josephmills' offer to help was very kind and generous. :)

---

### Post by jordanball33 on 2012-02-27
code dosent scare me off. i took a C++ programming course. been working with html to design websites. so ill definately give it a try and see what happens.

---

### Post by cbanakis on 2012-02-27
> **snowpine said:**
> You may be projecting your own insecurities regarding the command line; I thought that josephmills' offer to help was very kind and generous. :)

He is definitely not wrong.

And I did not want to give that impression.

I just want to try and keep it simple, at least until we know if the command line is necessary.

Odds are, Jordanball33 will not run into any issues.  IMO

As far as the average user goes.  (Just using internet and want not)

Ubuntu usually just works, with a few exceptions...

Maybe the volume keys on his laptop wont work.  (for example)

---

### Post by audiomick on 2012-02-27
> **jordanball33 said:**
> code dosent scare me off. i took a C++ programming course. been working with html to design websites. so ill definately give it a try and see what happens.
That's the spirit. All of those commands are to find out about the hardware on your computer.

If you post output here, be sure to use the code tags. That's the # button above the post window. That puts it in a nice box with a scroll bar on the side when it is a lot of text.

---

### Post by josephmills on 2012-02-27
> **cbanakis said:**
> He is definitely not wrong.

And I did not want to give that impression.

I just want to try and keep it simple, at least until we know if the command line is necessary.

Odds are, Jordanball33 will not run into any issues.  IMO

As far as the average user goes.  (Just using internet and want not)

Ubuntu usually just works, with a few exceptions...

Maybe the volume keys on his laptop wont work.  (for example)

No one can give you a "great answer" with-out knowing the question. Your question is Will ubuntu work with my computer and it's extras that I have. Well what kinda computer what kinda cpu ram wireless ect.. Until I know /see any of that I can not give you a honest answer. what if you only have enough ram for lubuntu ? what if VGA card is closed source ? what if you need to compile  a compat wireless for your usb? I will never know until we know your hardware. That is it sorry if I scared you off. That was not my intention. As One of the only things that I would like to see is other get the same great experience that I have gotten from this great OS. I hope that this  clears the air.

---

### Post by cbanakis on 2012-02-27
> **jordanball33 said:**
> code dosent scare me off. i took a C++ programming course. been working with html to design websites. so ill definately give it a try and see what happens.

Good for you.

As your experience, and needs progress, the command line will become a very useful tool.

But one of the reasons why Linux has gained so much momentum in the last 5-10 years, is that the need for command line has been drastically reduced.

Also, when you do your live session, be sure to check out the Ubuntu Software Center.

Its a very nice way to browse, and install applications, and just about everything you need can be found there.

If you end up going through with the switch, I recommend getting "wine" from the software center.

It allows you to install and run many windows programs in Ubuntu.

Wine does have its limitations, but in my experience, most older programs work fine, and newer small apps too.

For example, Microsoft Office 2003 installs and works the same way that it would in windows, as does Adobe Photoshop CS2.

But Office 2007 needs some tweaking, and has some minor glitches.
And Photoshop CS5 needs a lot of tweaking (Needs to be manually installed by copying from a windows install) And has some minor glitches.

---

### Post by cbanakis on 2012-02-27
> **audiomick said:**
> That's the spirit. All of those commands are to find out about the hardware on your computer.

If you post output here, be sure to use the code tags. That's the # button above the post window. That puts it in a nice box with a scroll bar on the side when it is a lot of text.

LOL, I was actively using Ubuntu, and posting on Ubuntu Forums for like 2 years before I figured out how create a code box in a post.

But it only took me like a month to figure out how to mark a thread as "Solved"

:)

---

### Post by Mark Phelps on 2012-02-29
You're NOT "Swapping from windows" if you install Wine and then remain tied to Window apps -- like Office.

To really switch, you need to be willing the learn new WAYS of doing things, otherwise, all you're really looking for is a free VERSION of Windows -- which is not Linux.

Also, the ONLY way you will know if ANY machine runs Linux well is to try it.  Perhaps someone here will have already tried the Linux distro you want on exactly the same machine -- but they may not be running the same apps.

That is why LiveCD approach was invented -- to let you try it out before making the switch.

---

### Post by cbanakis on 2012-02-29
> **Mark Phelps said:**
> You're NOT "Swapping from windows" if you install Wine and then remain tied to Window apps -- like Office.

To really switch, you need to be willing the learn new WAYS of doing things, otherwise, all you're really looking for is a free VERSION of Windows -- which is not Linux.

Also, the ONLY way you will know if ANY machine runs Linux well is to try it.  Perhaps someone here will have already tried the Linux distro you want on exactly the same machine -- but they may not be running the same apps.

That is why LiveCD approach was invented -- to let you try it out before making the switch.


Sorry, but I need to go ahead, and completely disagree with you.
There are a lot of windows applications, that simply do not have viable alternatives for Linux.  Thats why Wine exists.

Yes, there are plenty of alternatives, but there are several cases, where you NEED either Windows or Wine, depending on what you use a computer for.

I use my system for work.  (Printing company)

Gimp, and Ink-scape are great programs, but unfortunately, they don't always cut it.
(ie Photoshop and Illustrator are required)

One example would be Gimp's complete lack of cmyk color support.
And yes, Gimp reads Photoshop files, but if they are layered, and designed in CMYK, it cannot open the file.  Making it impossible for me to even open the file, so how am I going to print it?

For me, personally, if Adobe began to support Linux, I would not need Wine.

Also, I need Office 2007 on occasion, because Excel has more formulas than libre, or Open.

For the average person, there is no need for Wine, but that does not mean nobody needs it.

---

### Post by audiomick on 2012-02-29
I use a few programs that I am not even going to try in wine, or even in a Virtual Machine. They are programs for running Digital Audio Equipment, and an Acoustic Analyser program. It's a pain, but there is no way around a Windows install for that.

---

