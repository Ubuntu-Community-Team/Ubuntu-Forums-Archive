---
title: "Ubuntu 11.04 natty is still very unstable"
date: 2011-05-01
forum: Recurring Discussions
---

### Post by aviramof on 2011-05-01
1.i can't enter unity without first enter ubuntu classic with no effects and install fglrx manually or from jockey.

2.installing deb files is very slow.

3.downloading files is very slow despite the fact i have 10mbit connection.

4.compiz is not working and any change to compiz make unity crash and never return. 

and countless other stabilty problems exist in this version.

---

### Post by Swagman on 2011-05-01
Which version ?

Here's an uber quick lookover I posted on another forum

I've been testing Natty out on a 16gb USB stick

64 bit one first.. Gave this error message
[[img]http://img90.imageshack.us/img90/5103/natty1screenshot.th.jpg[/img]]("http://img90.imageshack.us/i/natty1screenshot.jpg/")
Then dropped me to a login with the only login option being "Other" which obviously doesn't work cuz you don't know "Others" password !!


32 bit second
On booting into live environment it drops you into Gnome desktop. checking for hardware drivers (Nvidia) shows none available so go into Software sources and switch on Uni & Multiverses and check for and install updates.
Nvidia driver now available... Reboot

Yay.. Unity now working.
My Missus uses Epiphany browser so I install that but it didn't auto add to the dock. So I click the Ubuntu icon in the top left of the screen and in the window that opens I dragged the Epiphany icon into the dock.
Yup that worked.
Got my missus to bugger around with it and she proclaimed it IS a bit snappier.

I then installed CCSM as I like Wobbly Windows and zoom desktop.

In regard to the scroll bar... Interestingly Firefox stays traditional but Epiphany uses new style (see screengrab below)

[[img]http://img88.imageshack.us/img88/9175/natty4screenshot.th.jpg[/img]]("http://img88.imageshack.us/i/natty4screenshot.jpg/")

All in all I think I'm going to wait a month or so before clean installing new version (Separate /home partition)

---

### Post by aviramof on 2011-05-01
Ubuntu 11.04 final 32 bit via wubi and by the way it did not copied my favorites from windows 7.

---

### Post by BandD on 2011-05-01
Unity should have nothing to do with slow downloads.  It's still Gnome underneath the hood.  It's like switching form metacity to compiz as your window manager (in fact Unity basically functions as a compiz-plugin).  If your network speeds are diminished it is likely a driver/module problem.  How is your CPU usage?  How much free memory do you have?

---

### Post by aviramof on 2011-05-01
It should not be high giving the fact that i don't run anything eles and i have 2gb of memory how ever at this moment i don't think that natty is a very usable operating system considering the fact that 
i have to reinstall it every time i try to do something and then unity stop working and this is what i am going to do now i guess.

---

### Post by mgmiller on 2011-05-01
I found it's a little different running from a Live USB vs. installing it on HDD.  I recently picked up a Zotac with Nvidia ion graphics and and Atom N550.  When doing the install, you are given a choice to use proprietary codecs and drivers and such.  I checked that off and it finished the install and booted directly into Unity with the Binary Nvidia driver installed, as well as MP3 support and a few other things.

I did find in order to get smooth full screen HD video with the ion graphics, I needed to install libvdpau1.  This made a huge difference combined with the mplayer video player with vdpau enabled from its preferences.

---

### Post by werty2010 on 2011-05-01
have any of you had any kind of updates available since your install?

---

### Post by Throne777 on 2011-05-01
> **BandD said:**
> How much free memory do you have?

I have 1 gig of RAM & 128MB on my graphics card (GeForce 6600 GT). Unity makes most of it disappear without me really doing anything.
It also makes a complete mockery of my AMD Athlon 64 X2 4200+ processor.
On Windows XP I could run the original FarCry on full spec with no issues whatsoever. On Unity, my computer struggles to run Firefox & Banshee. 
Not good.

---

### Post by sdowney717 on 2011-05-01
I did an upgrade to 11.04 and system was totally hosed, slow, no video acceleration.
So I backed up /home, did a clean install and everything was good again.

---

### Post by beew on 2011-05-01
> **Throne777 said:**
> I have 1 gig of RAM & 128MB on my graphics card (GeForce 6600 GT). Unity makes most of it disappear without me really doing anything.
It also makes a complete mockery of my AMD Athlon 64 X2 4200+ processor.
On Windows XP I could run the original FarCry on full spec with no issues whatsoever. On Unity, my computer struggles to run Firefox & Banshee. 
Not good.

Strange, I run Natty on my 6 year old Dell D410 laptop with 1 G of ram and an old Intel card with no hardware acceleration (i195 driver) and Unity works fine. Even watched 720p video clips on it with Smplayer. Probably upgrading screwed up your system.

Having said that there are other things where Unity is buggy.  For example LibreOffice opens without maximize/minimize/restore/close buttons,--buttons only reappear after switching desktop and then switch back,  gnome-mplayer after minimizing doesn't restore (click icon on Unity bar only bring up a new instance while the old one still running in the background but can't bring it out)

---

### Post by pi.boy.travis on 2011-05-01
Natty runs perfectly on all of my machines, except two laptops, an Acer and a Dell, because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/740126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/740126)

It would seem as though a patch is upstream and they are working on getting it SRU'd. Ah well, just can't close the lids for a bit. . .

---

### Post by cariboo on 2011-05-02
I've got Unity running on a 7-year old Celeron with a 6600GT AGP card and 512MiB of ram, it runs quite acceptably. One thing I found during the testing cycle is that the enabling the restricted drivers rendered the system unusable. Using nouveau and libgl1-mesa-dri-experimental, makes the system much more usable than when it ran XP.

I should also add that I'm running Unity on

[LIST]
[*]Compaq Mini 110 netbook Atom 270 CPU 1GiB ram and 945 graphics
[*]Custom built System AMD X2 3600+ CPU 2GiB ram and nVidia 9400GT graphics
[*]Custom built System AMD X2 240 CPU 2GiB ram and nVidia 210GT graphics
[/LIST]

---

### Post by Johnsie on 2011-05-02
After the upgrade Unity wouldn't even start on my computer downstairs due to a bad graphics driver in the 11.04. It was previously  set to autologin so I couldn't even set it to do classic mode without doing crazy things in the terminal.

On this computer I have had several freezes with the dash, trouble multitasking and Open Office keeps opening up because the side panel appears out of nowhere and gets clicked when I'm actually trying to click something else on the screen. 

So far it has been a usability nightmare for me, so I'm going to get more involved in testing Ocelot to make sure these errors are fixed. I also require a suitable replacement for the places menu, a show desktop feature and a better way to start applications.

---

### Post by wojox on 2011-05-02
Unity 1.0 what do you people expect? Give it time to mature.

---

### Post by Johnsie on 2011-05-02
> Unity 1.0 what do you people expect? Give it time to mature. 

That's what people were saying 6 months ago.

---

### Post by charliemagiera on 2011-05-02
I tried to upgrade to 11.04, but couldn't get it to work.  I tried every suggestion in tutorials and here in the community.  Despite my machine being able to support it, I got fed up.  I was using *Ubuntu Classic* the whole time it was installed.  So, I went back to Maverick, and couldn't be happier with the decision I made.  The Unity concept is just *too* new for reliable use at this point.

---

### Post by Throne777 on 2011-05-02
> **beew said:**
> Strange, I run Natty on my 6 year old Dell D410 laptop with 1 G of ram and an old Intel card with no hardware acceleration (i195 driver) and Unity works fine. Even watched 720p video clips on it with Smplayer. Probably upgrading screwed up your system.


From what I've read from other people's experience, it seems to be luck of the draw (although undoubtedly there are some technical reasons underlying all this). Some people are claiming it's much faster than 10.10 but most seem to be claiming it's a lot slower.

---

### Post by jonathan.crouse1 on 2011-05-03
> **cariboo907 said:**
> One thing I found during the testing cycle is that the enabling the restricted drivers rendered the system unusable.


Thank you, this helped me with slow down issues during general use.  I thought I needed them enabled for my wireless (Broadcom STA) but apparently the community has added support now.  Thanks again.

Similarly I am running Unity on a HP 210 netbook.

---

### Post by Exodist on 2011-05-04
> **aviramof said:**
> 1.i can't enter unity without first enter ubuntu classic with no effects and install fglrx manually or from jockey.

2.installing deb files is very slow.

3.downloading files is very slow despite the fact i have 10mbit connection.

4.compiz is not working and any change to compiz make unity crash and never return. 

and countless other stabilty problems exist in this version.

Its a Development release. It can run great for some users, and be complete chaos for others. For this reason you would prob have better luck with 10.04LTS - Lucid Lynx until 11.10 is released.

---

### Post by rg4w on 2011-05-04
> **Exodist said:**
> Its a Development release. It can run great for some users, and be complete chaos for others. For this reason you would prob have better luck with 10.04LTS - Lucid Lynx until 11.10 is released.
Why isn't the stable release the one new users are encouraged to try at Ubuntu.com?

---

### Post by Exodist on 2011-05-04
> **rg4w said:**
> Why isn't the stable release the one new users are encouraged to try at Ubuntu.com?
To the best of my knowledge. It is..

---

### Post by tnt533 on 2011-05-19
Upgraded from 10.10 and am using Unity 3d using the open nVidia drivers installed though the restricted driver applet on an AMD dual core 2.6 and 8 gig of ram with an 8800gtx.

It don't find the entire system unstable as I have yet to run into a required system reboot situation but I regularly lose compiz functionality. The window title bars have a nasty way of going poof and requiring a window manager reload, thanks goes to Compiz Icon for making that easy, and integration with vmware unity is shakey at best. 

The actual system works well and I like the new interface other than the total lack of customizable features, hopefully added with the upcoming release of 11.10, but overall window manager / Compiz stability is too low to be used on a production machine. I don't think 11.04 was really release ready which is a shame and does soil Ubuntu's rep a bit. 

Looking forward 11.10 and seeing how everything pans out.

---

### Post by pi.boy.travis on 2011-05-19
Ubuntu releases tend to go through a cycle. Tons of polishing and refinement goes into an LTS release, then that next October things get a little riskier. The April release between LTS's is usually a little rough. I remember 9.04, the last April release between LTS, was an absolute nightmare. I only used it until Karmic's first alpha. I think 11.04 is far better than 9.04. A lot of the press and complaining is just FUD. History shows that we're sure to nail Unity this coming release. In fact, it was the problems I had with 9.04 that caused me to really get into Ubuntu testing. Unhappy with Unity? Then get involved in Onieric development!

---

### Post by Irihapeti on 2011-05-19
> **pi.boy.travis said:**
> Ubuntu releases tend to go through a cycle. Tons of polishing and refinement goes into an LTS release

That's not the impression I've got. After 10.04 and, earlier, 8.04 were released, I think that there was pretty much the same amount of commotion as currently. Lots of comments about how such a buggy release shouldn't have been allowed out the door.

That's why I'm not getting too bothered about the current reactions. Yes, I've used Unity, and I think it's neither wonderful nor terrible. If there was no other choice, I'd adapt. But I do have choices.

---

### Post by NormanFLinux on 2011-05-20
Its very stable. Its rock solid after I upgraded to the 2.6.39.0 kernel. All updates applied. I have added cardapio to restore classic start menu to the launcher and added show desktop to reveal the desktop if I run more than a single program instance. 

I run Unity 2D. It is very fast and programs launch quickly from the launcher.

---

### Post by beew on 2011-05-20
> **tnt533 said:**
> Upgraded from 10.10 and am using Unity 3d using the open nVidia drivers installed though the restricted driver applet on an AMD dual core 2.6 and 8 gig of ram with an 8800gtx.
.

Huh? The open driver doesn't need to be installed, by "restricted driver applet" I suppose you mean jockey, that installs the proprietary driver.

The nouveau driver still freezes up the system from time to time.

---

### Post by linuxyogi on 2011-10-12
Didn't read all the posts. IMHO the base itself is buggy & unstable. You touch it it & it breaks down. I have suffered a lot of harassment (reinstalls) coz of Natty.

Last week I downloaded & installed the Nvidia Binary driver from their site. It installed fine but then the PC wont boot. I have installed that driver many times so there's nothing wrong there. 

If 11.10 comes out buggy then God help us.  

One word for Natty >>> FRAGILE.](*,)[-(

---

