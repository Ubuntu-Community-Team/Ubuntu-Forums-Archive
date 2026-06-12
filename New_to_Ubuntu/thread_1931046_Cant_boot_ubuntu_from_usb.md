---
title: "Cant boot ubuntu from usb"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by parkerskouson on 2012-02-24
ok. I am trying to install ubuntu on a new build and when i go to boot ubuntu from the first hdd from the usb it just boots into windows. im trying to do that because i cant use the normal ubuntu installer i just get the really old installer....
anyone know what the problem is
parker

---

### Post by audiomick on 2012-02-24
You say it is a new build, but there is a windows on there. I think it might help if you list exactly what you have done up to now.

---

### Post by parkerskouson on 2012-02-24
ok. i just reinstalled windows on it, then i go and try this whole 10.04 installer thing and i compleatly wipes my hdd and when i go to boot it up again is just keeps flashing an underscore and just stays there.....

---

### Post by HeroOfCanton on 2012-02-24
What do you mean it completely wipes the hdd? Is Windows gone now? Or is the problem only when trying to boot to ubuntu?

---

### Post by parkerskouson on 2012-02-24
windows is gone

---

### Post by audiomick on 2012-02-24
When you tried to install, which option did you choose from the "install beside", "use the whole disk", "something else" ?

Did it look like it had finished installing?


You could boot into the live environment (try without installing on the Ubuntu cd) and have a look at your drive from there to see what state it is in....

---

### Post by HeroOfCanton on 2012-02-24
What audiomick said...

---

### Post by parkerskouson on 2012-02-24
> **audiomick said:**
> When you tried to install, which option did you choose from the "install beside", "use the whole disk", "something else" ?

Did it look like it had finished installing?


**You could boot into the live environment** (try without installing on the Ubuntu cd) and have a look at your drive from there to see what state it is in....

that doesnt work. and i dont have the normal installer so i had to manually partition and it wiped my whole hdd

---

### Post by HeroOfCanton on 2012-02-24
Can you download and burn a proper live cd or usb from another computer? What type of installer are you using that you have to do the partitioning yourself?

---

### Post by parkerskouson on 2012-02-24
i have done both. and i am using the old 10.04 installer. for some reason thats what shows up

---

### Post by audiomick on 2012-02-24
> **parkerskouson said:**
> that doesnt work.
You should always be able to boot into the live environment.

UNLESS
>  and[COLOR=Red] i dont have the normal installer [/COLOR]so i had to manually partition and it wiped my whole hddyou have an alternate installer. Is this the case? How are you trying to install?

---

### Post by enjoijesus94 on 2012-02-24
Hello Parker.
Can You Specify Your Computer Hardware And Desktop?

Putting It In Short Terms 
Are Your Doing It On A Old Desktop? Or Laptop

---

### Post by parkerskouson on 2012-02-24
when i try to do the live "trial" it just boots to windows. i am just trying a 100gb partition with the altrenate installer. yes it is not the graphical. it flashes an underscore and when it should do grub it just stays at the flashing underscroe.

Computer Specs

Core 2 Duo 3ghz
4gb ram
asrock g31m
asus geforce 210 1 gb
250 hdd

---

### Post by audiomick on 2012-02-24
Is it a CD that the "live" doesn't work from? Or is it a USB thumb drive maybe?

Weird that you can't get into a live environment. I thought that was pretty much bullet proof.

---

### Post by HeroOfCanton on 2012-02-24
Is there a specific reason you need the alternate installer? Seems like your PC should be able to handle the standard.

Are you using something like pendrivelinux when installing from the usb?

---

### Post by parkerskouson on 2012-02-24
doesnt work on either

---

### Post by parkerskouson on 2012-02-24
and no ive got a lappy that has ubuntu that i used to do the usb and imgburn to burn the image

---

### Post by parkerskouson on 2012-02-24
> **HeroOfCanton said:**
> **Is there a specific reason you need the alternate installer? Seems like your PC should be able to handle the standard.**

Are you using something like pendrivelinux when installing from the usb?
 
im not choosing, thats just whats happening

---

### Post by westie457 on 2012-02-24
Hi somebody will correct me if I am wrong.

The alternate installer does not have a 'Live' mode so you cannot try before installing.

Also have you set the BIOS to boot from CD or USB before the hard drive?

---

### Post by parkerskouson on 2012-02-24
yep i have. if there was a way to manually choose the installer i would do that. but idk how to do that.

---

### Post by HeroOfCanton on 2012-02-24
> **parkerskouson said:**
> im not choosing, thats just whats happening

Got ya. Maybe try downloading the iso again? Like mick said the live cd is usually reliable. Sounds like when you select live it's trying to boot from the hdd. No clue why that would happen other than a bad install disk.

---

### Post by parkerskouson on 2012-02-24
ive downloader the iso 2x in both 32 and 64 bit tried the usb 3x and the cd 2x. i dont think that is the prob. could the version be the prob? cause im tryin 12.04 but that shouldnt be the prob

---

### Post by audiomick on 2012-02-24
> **parkerskouson said:**
>  if there was a way to manually choose the installer i .
There isn't. Either you have burned an image to get a Live CD (or USB pendrive, whatever...) or you have used an image for the alternate installer.


It also occurs to me to ask if you have checked the image to see if it downloaded good. You should check the MD5 sum of the file you downloaded.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by HeroOfCanton on 2012-02-24
> **parkerskouson said:**
> ive downloader the iso 2x in both 32 and 64 bit tried the usb 3x and the cd 2x. i dont think that is the prob. could the version be the prob? cause im tryin 12.04 but that shouldnt be the prob

Could be since that's not an official release yet. Maybe try with 11.10 and see if you get the same problems?

---

### Post by parkerskouson on 2012-02-24
thats all good

---

### Post by audiomick on 2012-02-24
> **parkerskouson said:**
> ... cause im tryin 12.04 but that shouldnt be the prob
no, that shouldn't be the problem.

do the MD5 sum on the image.

Given that it is a new build, try a live CD that you know is good, if you have one.

Also, even though the 12.04 should work, it isn't out yet. It is just about possible that they have put a dodgy image up. Not likely, but not impossible.

---

### Post by enjoijesus94 on 2012-02-24
Hello [parkerskouson]("http://ubuntuforums.org/member.php?u=1317220")

The Reason I Said To Specify Is Cause I Had A Recent Problem.

So You Cant Even Boot Your Usb
Have You Checked Your BIOS?

Or Run The LiveCD?:KS

---

### Post by parkerskouson on 2012-02-24
ok... ill try it but its worked before but ill give it a try

---

### Post by parkerskouson on 2012-02-24
the m5d works

---

### Post by parkerskouson on 2012-02-24
> **enjoijesus94 said:**
> Hello [parkerskouson]("http://ubuntuforums.org/member.php?u=1317220")

The Reason I Said To Specify Is Cause I Had A Recent Problem.

So You Cant Even Boot Your Usb
Have You Checked Your BIOS?

Or Run The LiveCD?:KS

bios is all good. it wont install correctly it boots to the usb fine

---

### Post by HeroOfCanton on 2012-02-24
> **parkerskouson said:**
> thats all good

Assuming 11.10 installs properly, I've got to guess it's a version thing. It SHOULDN'T be, but what else could it be if previous versions are installing okay?

Maybe report it as a bug so the developers can take a look before the official release?

---

### Post by parkerskouson on 2012-02-24
will do. thanks for the help but do you think the weird installer is a version thing?

---

### Post by enjoijesus94 on 2012-02-24
Post And Tell Us How Everything Goes.
Have Anymore Problems Just Ask Man.:guitar:

---

### Post by HeroOfCanton on 2012-02-24
> **parkerskouson said:**
> will do. thanks for the help but do you think the weird installer is a version thing?

Well, if previous versions install fine and this one screws up I just can't think of another reason. Maybe they changed the installer and created some unexpected bugs.

---

### Post by parkerskouson on 2012-02-24
ok will do

---

### Post by parkerskouson on 2012-02-24
> **HeroOfCanton said:**
> Well, if previous versions install fine and this one screws up I just can't think of another reason. Maybe they changed the installer and created some unexpected bugs.
that would make sense

---

### Post by audiomick on 2012-02-24
> **parkerskouson said:**
> that would make sense
Yeah, if I've understood everything correctly, then there is not much else that it could be, I think...

---

### Post by enjoijesus94 on 2012-02-24
Makes Sense.

---

### Post by parkerskouson on 2012-02-24
well that didnt work. i tried the trial and it just kicked my back to the normal screen. and i still have to altrienent installer. any other ideas? i tried 11.10

---

### Post by HeroOfCanton on 2012-02-24
What do you mean by kicked you back to the normal screen? The install selection menu?

---

### Post by parkerskouson on 2012-02-24
> **HeroOfCanton said:**
> What do you mean by kicked you back to the normal screen? The install selection menu?
yeah that says install and mem test etc...

---

### Post by enjoijesus94 on 2012-02-24
Hmmmm.

Have You Tried Any Previous Versions Of Ubuntu?

When I Installed 11.10 It Did The Same To Me A While Ago.

---

### Post by parkerskouson on 2012-02-24
ive got 11.04 an 10.10 i think ill try 10.10 ......... might as well

---

### Post by enjoijesus94 on 2012-02-24
Im On 10.10
and it works fine

unity desktop killed it for me.

i mean compiz
then the layout wasnt my taste 

im running BlackBuntu 10.10 on mine

---

### Post by HeroOfCanton on 2012-02-24
Try 10.10 before all of the unity additions. It could be a video driver issue and it would seem to make sense that unity would have upgrades with all of the 3d.

Another thought along that line: Maybe try k or xubuntu or anything with a non-gnome gui.

---

### Post by parkerskouson on 2012-02-24
i think it might also be my graphics card.... seeing it takes special drivers to work with windows........

---

### Post by parkerskouson on 2012-02-24
besides 10.10 is still my fav

---

### Post by enjoijesus94 on 2012-02-24
Yea try what me and [HeroOfCanton]("http://ubuntuforums.org/member.php?u=1515672") told ya.

try 10.10

i havnt had any problems with it.

if that dosnt work give me time to study up on this kind of problem.

to speak my mind i dont like all versions after 10.10

10.10 is the most stable and awesome interface for me.

---

### Post by parkerskouson on 2012-02-24
> **enjoijesus94 said:**
> Yea try what me and [HeroOfCanton]("http://ubuntuforums.org/member.php?u=1515672") told ya.

try 10.10

i havnt had any problems with it.

if that dosnt work give me time to study up on this kind of problem.

to speak my mind i dont like all versions after 10.10

10.10 is the most stable and awesome interface for me.

totaly agree with you on that one. thanks for the help

---

### Post by enjoijesus94 on 2012-02-24
> **parkerskouson said:**
> totaly agree with you on that one. thanks for the help

No Problem At All Man:popcorn:

---

### Post by parkerskouson on 2012-02-24
thats what im talking about!!!!!!! it totally worked. none of the selecting crap. straight to a good desktop!!!!! thanks so much all of ya!!!!!!!

---

### Post by HeroOfCanton on 2012-02-24
You may want to give Xubuntu a try. Switched because I'm a programmer and unity was just killing me. Ubuntu with XFCE allows me to use the newest kernels and keep my updates fresh while having a gui that feels right. I still install a bunch of gnome tools like gedit so I don't have to learn too many new things though. :D

Glad it's working though! Sounds like it was the video card after all.

---

### Post by enjoijesus94 on 2012-02-24
> **parkerskouson said:**
> thats what im talking about!!!!!!! it totally worked. none of the selecting crap. straight to a good desktop!!!!! thanks so much all of ya!!!!!!!

GOOOOOOOOD!!!!:guitar:

so glad you got it 

Welcome To Linux My Friend.

---

### Post by enjoijesus94 on 2012-02-24
> **HeroOfCanton said:**
> You may want to give Xubuntu a try. Switched because I'm a programmer and unity was just killing me. Ubuntu with XFCE allows me to use the newest kernels and keep my updates fresh while having a gui that feels right. I still install a bunch of gnome tools like gedit so I don't have to learn too many new things though. :D

Glad it's working though! Sounds like it was the video card after all.


Yes Yes 
thats smart.

im trying new distros 
and its good to try new things.

my current OS's
Ubuntu,BlackBuntu,Backtrack,Mint Linux,Puppy Linux,Kbuntu,And So Many More

---

### Post by parkerskouson on 2012-02-24
hey. while your here. i just deleted my windows partition!!! fail... but it was fresh so nothing lost. when i did this same process grub was deleted. how would i manage to get that back?

---

### Post by parkerskouson on 2012-02-24
> **HeroOfCanton said:**
> You may want to give Xubuntu a try. Switched because I'm a programmer and unity was just killing me. Ubuntu with XFCE allows me to use the newest kernels and keep my updates fresh while having a gui that feels right. I still install a bunch of gnome tools like gedit so I don't have to learn too many new things though. :D

Glad it's working though! Sounds like it was the video card after all.

i may just have to do that

---

### Post by HeroOfCanton on 2012-02-24
Grub recovery:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by parkerskouson on 2012-02-24
> **HeroOfCanton said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

thanks will mark as solved

---

### Post by enjoijesus94 on 2012-02-24
> **parkerskouson said:**
> hey. while your here. i just deleted my windows partition!!! fail... but it was fresh so nothing lost. when i did this same process grub was deleted. how would i manage to get that back?

Try This Man
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Im Doing This Right Now lol:popcorn:

---

### Post by parkerskouson on 2012-02-24
> **enjoijesus94 said:**
> Try This Man
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Im Doing This Right Now lol:popcorn:
im gonna do this and the other on when it is installed

---

### Post by enjoijesus94 on 2012-02-24
> **parkerskouson said:**
> im gonna do this and the other on when it is installed

Good Luck Man 
post if everything went good :guitar:

---

### Post by parkerskouson on 2012-02-24
for sure

---

### Post by parkerskouson on 2012-02-24
OK. Now its just blinking an underscore and it has for like 5 min

---

### Post by HeroOfCanton on 2012-02-24
> **parkerskouson said:**
> OK. Now its just blinking an underscore and it has for like 5 min

How far along are you? Are you at the first boot to the hdd?

---

### Post by parkerskouson on 2012-02-24
Yeah

---

### Post by HeroOfCanton on 2012-02-24
It's got to be that video card again. Did you install updates and 3rd party software during the install? Bet something updated and tried to load that bad driver again. :(

---

### Post by parkerskouson on 2012-02-24
I didn't. But ill try to use the stock video to get it running then install drivers....

---

### Post by enjoijesus94 on 2012-02-24
Very Important To Install The Updates At Install.

Sometimes They Help With The Kind Of Problems You Are Having:lolflag:

---

### Post by HeroOfCanton on 2012-02-24
> **parkerskouson said:**
> I didn't. But ill try to use the stock video to get it running then install drivers....

By stock do you mean an on-board card? If so, are you disabling the on-board video in BIOS when using the other card? Could be causing a conflict if you have both enabled.

---

### Post by parkerskouson on 2012-02-24
OK. I'm going to install the driver to get it running then put in the disk that came with the card.

---

### Post by enjoijesus94 on 2012-02-24
> **parkerskouson said:**
> OK. I'm going to install the driver to get it running then put in the disk that came with the card.

Give Us The Output After You Do This :P

---

### Post by parkerskouson on 2012-02-24
Will do:guitar:

---

### Post by parkerskouson on 2012-02-25
Still not working

---

### Post by HeroOfCanton on 2012-02-25
That really sucks. Thought we had this one nailed... :(

Willing to give Xubuntu a shot and see what happens? I'm out of other ideas... Not really sure if the drivers are the same or not, but what's one more download and install at this point? :D

---

### Post by parkerskouson on 2012-02-25
for sure. But prob not tonight. Ill get back to you guys tomorrow

---

### Post by parkerskouson on 2012-02-25
Well xubunut isn't working.  I'm gonna try mint now cause i like it a lot

---

### Post by parkerskouson on 2012-02-25
ok. so now it is just no ubuntu. nothing i have tried so far will install at all except windows. but i would much rather have ubuntu than any other distro so if anyone knows of a fix please share it

thanks
parker

---

### Post by enjoijesus94 on 2012-02-25
I really thought we had this one.
Hmmmm

Give Me every detail of what happens when you try to boot into ubuntu?

for example.
what does the screen look like?
The mouse?
Anything to do with the look basically 

i may know what the problem is.

Whats Your Graphics Again?;)

---

### Post by HeroOfCanton on 2012-02-25
Okay, first remove your video card. Next, hit it with a hammer until it's in powder form. Then get a new one and try again. :D:D:D J/K. We'll get this figured out eventually.

enjoi, I think it was just a flashing cursor on the first boot to the HDD after install.

Parker, were you able to get the install complete on the other distros or was it kicking you to that alt installer again? Are the problems still happening on the first HDD boot? Did you try checking the updates and 3rd party boxes this time around?

---

### Post by enjoijesus94 on 2012-02-25
> **HeroOfCanton said:**
> Okay, first remove your video card. Next, hit it with a hammer until it's in powder form. Then get a new one and try again. :D:D:D J/K. We'll get this figured out eventually.

enjoi, I think it was just a flashing cursor on the first boot to the HDD after install.

Parker, were you able to get the install complete on the other distros or was it kicking you to that alt installer again? Are the problems still happening on the first HDD boot? Did you try checking the updates and 3rd party boxes this time around?

Hero? Im thinking it might be the graphic card problem
who knows 
we have been trying to figure this out.

hmmm
im hopin he can get the nomodeset method to work?

---

### Post by parkerskouson on 2012-02-26
i just got it to work. it was the fact that i had 4 hdd connectied and it didnt know which one to boot to. Thanks so much for all of you help!!!!! saved my butt!!!!!!:guitar::popcorn::popcorn::popcorn:

---

### Post by HeroOfCanton on 2012-02-26
> **parkerskouson said:**
> i just got it to work. it was the fact that i had 4 hdd connectied and it didnt know which one to boot to. Thanks so much for all of you help!!!!! saved my butt!!!!!!:guitar::popcorn::popcorn::popcorn:

Hooray! Glad you finally got it. I kept privately thinking HDD since it installed okay, but with Windows working it didn't sit right in my mind. Didn't think about the possibility of 4 HDD's...

Should have, because my desktop has 2 SSD (one for the OS and one for misc tasks needing high rw speed like compiling programs or HD video) and two 1TB HDD's running in Win7 software RAID0. Glad to see I'm not the only one loading up a system with ridiculous configurations. :D

Don't forget to mark the thread solved.

---

### Post by parkerskouson on 2012-02-26
U sure aren't. U guys r the best

---

### Post by enjoijesus94 on 2012-02-26
> **parkerskouson said:**
> U sure aren't. U guys r the best

I Knew Something Wasnt Right.

Yes It Can DO That..

im so glad you got it working 

and were just here to help no big deal welcome to linux my friend.:popcorn:

---

