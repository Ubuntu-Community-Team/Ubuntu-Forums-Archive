---
title: "ubuntu slow or won't install"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by gmonck311 on 2013-12-14
I am brand new to ubuntu. I am trying to install on my laptop. I have created the bootable usb and it boots. I have tried to install multiple times. The farthest i have gotten is to end of the install process.(clicking install and having the warning message come up telling me it will format my hard drive) It then sat idle for over an hour without the status bar moving. I turned off my laptop and attempted to install again and can not get to that point. It seems to continue to freeze. Every thing i have read says that it should not take longer than 30-60 minutes to install. Has any one else had this problem? Any suggestions?

Thanks

---

### Post by DuckHook on 2013-12-15
Hello gmonck311 and welcome to Ubuntu and the forums.

We will need far more info before we even know where to begin.

1. What flavour and version are you trying to install? And is it the desktop or alternate image?
2. What are your complete HW specs? Need everything: make. model, CPU, amount of RAM, video chipset, VRAM, USB version (1.1, 2, 3?), HDD size, tell us if SSD and size, plus anything else you can think of.
3. Did you check md5 hash of image after downloading?
4. How did you download? HTML, FTP or torrent?
5. Are you using unetbootin?
6. Dual booting? If so, what is other OS?
7. Have you tried running in LiveUSB mode? If so, does it work?
8. Is it a Windows 8 computer? Did you turn off secure boot and fast boot before installing?
9. Is it UEFI or BIOS?
10. Is HDD/SSD partitioned with MBR or GPT?

As you can see, with more complete info and background it is much easier to help. Turning in for the night now, but others here are more than willing to lend a hand.

---

### Post by Bucky Ball on 2013-12-15
Welcome. As above and try this. When you get to 'Try' 'Install' options screen hit F6 and choose 'nomodset' from the popup list of options. Then proceed as normal.

A punt, but if that works then it will avoid having to delve any deeper. It could be that simple.

(PS: Yes, weather fine in Aus, Duckhook. It is going to be 41C on Wednesday!)

---

### Post by DuckHook on 2013-12-15
Love punts. Some guru said that it was lazy guys finding ways to do things with no effort that were the source of all progress.

It got down to -31°C here last week. Oh well. One can but dream and pine for the magical land of Oz. Try not to get too much sun! :P

---

### Post by gmonck311 on 2013-12-16
Sorry for my newness.  I found that the laptop I'm trying to install in only had 265mb of ram. This was the problem. I ordered more ram and will install when  I get it.  Thanks for the responses. I will read more in the meantime to educate myself.

---

### Post by DuckHook on 2013-12-16
If your laptop is that low on RAM, it is unlikely to have the CPU or video horsepower needed to run Ubuntu. You may be better off with a lighter flavour. If you like, we can further advise you on options, but still need the previously requested info.

---

### Post by gmonck311 on 2013-12-16
Is there some way I can find all this information in one place? I mean on my computer specs. I am trying to install Ubuntu 12.04 desktop download throughout Ubuntu website. I want to run Ubuntu alone. It is running xp for now. The comp info I know is as follows: 2gb ram(soon)  40g hhd 1800mhz amd processer 32mb processor ati express graphics

---

### Post by DuckHook on 2013-12-16
Now that it's pretty obvious what borked your last install attempt, it isn't necessary to provide much else except HW info. If you Google make/model or have your user's manual, it should give you the HW info needed to for us to guide you. This forum is filled with threads dealing with the best options for old or underpowered HW. You can search through them too if you like.

---

### Post by gmonck311 on 2013-12-16
From the above specs what would you recommend. I am trying to run a very basic machine. Surfing Web, streaming video, xbmc w/ addons live TV/pvr/ddr functions, Netflix air play to my raspberry pi.

---

### Post by DuckHook on 2013-12-16
What you're trying to do is not a low-spec set of activities and is not really running a basic machine. In particular, it needs some video chops, which it seems that your HW may not be up to.

The critical info is actual CPU spec and Video chipset which is not included in your repply. Without more specific info, I'm shooting in the dark, but here is my educated guess—you appear to have an old and/or limited laptop with very low-end CPU and video. Such machines are generally quite capable of streaming, file server, print server, torrent slave, and like activities that are server in nature and restricted to sending out data to more high-powered clients. The moment you want to do things like XBMC or even web surfing, you are into more modern machines that have the resources to run a GUI and encode/decode audio/video data. These are resource-heavy requirements for your specs.

There's no harm in trying your intended uses, but don't expect good results. My guesstimate is that the lightest two distros in the 'buntu-derived universe would be best for your specs: either Lubuntu, or Bodhi. Bodhi is a derivation not officially supported by Ubuntu, but it is even lighter than Lubuntu and uses the same repos. If willing to go outside the 'buntus, then I would suggest, in order of diminishing resource requirements, CrunchBang, Puppy, Vector, SLiTaz and Tiny Core. If the CPU is really old and can only run on the 2.4.x kernel, then Damn Small Linux, which has the drawback of being basically frozen in development and something of a zombie (but that's why it's still on the 2.4.x kernel).

The nice thing about Linux is that you can try all of these distros without laying out a dime. Let us know what you settle on and good luck!

---

### Post by Bucky Ball on 2013-12-17
This thread has been marked as solved. It is etiquette to let the community know how you either solved or resolved your issues. Please advise. Thanks.

---

### Post by gmonck311 on 2013-12-17
I am waiting for the additional ram I ordered to be delivered. I marked it as solved because the problem was with the insufficient ram. When I figure out what will work I will post it.

---

### Post by gmonck311 on 2013-12-18
I am writing this reply using the "try ubuntu" feature of the 12.04.3 LTS I think i am going to install it now. I am tired of how windows is completely bogged down and im running Xp wich will not be supported after 4/14. I beileve it is time to make the switch.

---

### Post by DuckHook on 2013-12-18
> **gmonck311 said:**
> I am writing this reply using the "try ubuntu" feature of the 12.04.3 LTS I think i am going to install it now. I am tired of how windows is completely bogged down and im running Xp wich will not be supported after 4/14. I beileve it is time to make the switch.I repeat my recommendation to install Lubuntu rather than Ubuntu. Ubuntu will likely be far too slow for your old XP machine. Lubuntu can be run as a LiveCD/USB too for you to try out first. If you find Ubuntu too slow, then don't give up on the Distro altogether, but try out something else that is much lighter and designed for old hardware with limited resources.

---

### Post by gmonck311 on 2013-12-18
Thanks for the advice!  I do appreciate it. I am currently installing Ubuntu with 10min to go. If I find that this runs slow or has unwanted actions I will definitely try lubuntu. I like so far how Ubuntu was on the trial.  I may have other questions about things if I can't find the answers already posted. Again  thank you for the support.

---

### Post by gmonck311 on 2013-12-18
Well my stubborn nature has caused me problems once again. The install for ubuntu was taking an extremely long time to download the languages.(over 5hrs) I let it run hoping that the time would come down and it didn't. I am now downloading lubuntu and going to give that a try. I really wish i would heed the warnings of people who know what they are talking about. If you have any other advice I am NOW willing to listen.

---

### Post by Bucky Ball on 2013-12-18
Langauges? How many language packs were you downloading?

Anyways, see how it goes with Lubuntu. If that is also too slow you may want to try a minimal install. Bit of planning but worth it.

---

### Post by gmonck311 on 2013-12-18
As far as i know only English. I didn't check any others that i know of. I am downloading Lubuntu now from a torrent file and then will flash the SD card that I am using. I will try out the standard install and see how it goes.

---

### Post by DuckHook on 2013-12-18
> **gmonck311 said:**
> ...If you have any other advice I am NOW willing to listen....no problem at all. Don't beat yourself up. Linux is cool precisely because it allows us to experiment.

I'm an old-hardware hound. Like tinkering with ancient boxes and bringing them back to life. They all present different problems. You still haven't given us the info needed to make a true determination of the limits of your HW (this is not criticism—I know that sometimes it isn't easy finding such info—especially with hand-me-downs), and in the absence of such, it's only guess-and-golly. I can't give you any better advice than was already given in post #10. To recap:

1. Try Lubuntu and/or Bodhi. If they are still too heavy...
2. Try CrunchBang. If still too heavy...
3. Try Puppy or Vector. If still too heavy...
4. Try Tiny Core or SliTaz. These last two are the lightest modern distros that are still regularly maintained (read: safe and secure).
5. The only further place to go after these last two Distros is the stark command line—no GUI. This is not a real option for normal people. It works for hard-core geeks and old-HW hounds, but it's a very rewarding option if used the right way.

Be aware that as you move down the list, you gain speed, responsiveness and free up resources at the expense of functionality. Lighter distros come with limited selection of apps that in turn are of limited functionality.

The important thing to learn about Linux is that it's all out there for you to try. Every one of these distros is yours for the price of a download (i.e. free). Try them out until you find the one that works for you.

---

### Post by gmonck311 on 2013-12-18
Well i am passed the point of no return. When i originally tried to install Ubuntu 12.04 i formatted the HD. This means that i will be running some linux distro. I tried foolishly to run Lubuntu 64 and my comp was not compatible. I now flashed lubuntu 386 and am now going to try and install that. I am glad that i formatted the HD so i have to follow through with this. XP was slowly killing me and will not be supported soon. I'll let you know how it turns out.

---

### Post by gmonck311 on 2013-12-19
ok so i am installing lubuntu 386 and am at the retrieving file process. I've seen this before with ubuntu. It is saying that file 12 of 57 has 30 min remaining is this normal? I am installing from an SD card

---

### Post by gmonck311 on 2013-12-19
Well I have sucessfully installed lubuntu. I am posting from my laptop. I did receive an error message upon booting. I will post more tomorrow. I need sleep now. Thanks for all your help.

---

### Post by gmonck311 on 2013-12-19
Just wanted to come and say thanks for all the help. I am running lubuntu. The error message went away when i updated my drivers. This also solved my Wifi problems. The system is running much quicker than XP and it is all FREE!!! I have some other learning curves but I like to learn and love free stuff. Keep up the great work guys! I may have given up if it wasnt for you.:KS

---

### Post by DuckHook on 2013-12-20
> **gmonck311 said:**
> ...I may have given up if it wasnt for you.:KSThis is an incredibly nice thing to say, and it's a better reward than anything I can imagine.

Good luck and Happy Lubuntuing!

---

### Post by Bucky Ball on 2013-12-20
Good news! Enjoy the learning curve, the OS and the forums. ;)

---

