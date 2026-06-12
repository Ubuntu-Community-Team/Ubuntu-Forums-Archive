---
title: "Feisty Speed Up"
date: 2007-04-29
forum: Other OS Talk
---

### Post by GaryH on 2007-04-29
To CS majors everywhere,
I would like to speed up my GUI's window dragging and resizing and one of the suggestions is to use a CPU specific kernel. In my case that would be a 686 kernel. It appears I'll have to build the kernel myself as one doesn't exist in repositories. I'm trying to determine in advance if running a 686 kernel will really speed up my GUI. I suspect that the 686 kernel won't run that much faster (25%) than the generic and that the kernel won't run that often (10% kernel, 90% application) and so the net speed up will be minimal (2.5%). 

**That being said, will window dragging and resizing speed get noticeably faster if I use the 686 kernel?**

---

### Post by mips on 2007-04-29
I think it would be pretty safe to say "No". There might be an improvement but it will be very small if noticeable at all.  Sorting your GFX driver out will yield much better results.

What CPU, RAM & GFX do you have ?

---

### Post by 3rdalbum on 2007-04-29
Anecdotal: I switched from the 386 kernel to the K7 kernel (my processor is a K8). I didn't see any speed improvement, so I doubt you'd see a speed improvement through using a 686 rather than a 386.

However, you may see an improvement through actually compiling your own kernel. If you start doing that for speed reasons though, you begin to get into the Gentoo territory.

---

### Post by RTrev on 2007-04-29
> **GaryH said:**
> To CS majors everywhere,
I would like to speed up my GUI's window dragging and resizing and one of the suggestions is to use a CPU specific kernel. In my case that would be a 686 kernel. It appears I'll have to build the kernel myself as one doesn't exist in repositories. I'm trying to determine in advance if running a 686 kernel will really speed up my GUI. I suspect that the 686 kernel won't run that much faster (25%) than the generic and that the kernel won't run that often (10% kernel, 90% application) and so the net speed up will be minimal (2.5%). 

**That being said, will window dragging and resizing speed get noticeably faster if I use the 686 kernel?**

I believe that most of what you're looking for is to be found in your graphics card(s) and the associated drivers.  While I've moved back and forth between various systems, including Pentium 4, AMD dual core, 32 and 64 bit operating systems, etc, graphics performance has never changed much.  Right now, I'm running 64-bit Ubuntu Feisty on an AMD X2 3800+, with dual digital flat panel displays and an Nvidia GeForce 7300 GT graphics card with dual digital outputs and 512M of DDR2 RAM on the graphics card (1.5 G of RAM on the system).  I experienced what I always do -- the graphics performance was terrible until I got the correct video driver for the card installed and teaked properly.

During most graphics operations it's not your main CPU(s) doing the heavy lifting.. it's the graphics card itself.

I don't know if you're an Nvidia guy, but there's a common and easy little test that many of us run to measure our graphics performance; "gllxgears -info".  When I got this system first installed, but without the correct video driver, I got a value of about 300 to 400 frames per second.  Installing the correct NVidia driver bround that up to a bit over 5000.  Dragging windows around is now limited only by how quickly I can move the mouse.  It's effortless, clean, and fast as lightning.

So, forget about your main CPU.. concentrate on a decent graphics card and the right drivers.  My 7300 GT card was only about $100.. which may seem like a lot but it's at the low end of the price range of good cards.  The card you choose will be dictated by things like what monitor(s) you use, and what kind of motherboard slots are available to plug it in to.  You might want to check your PSU (power supply) to make sure it's adequate.. as it's going to be having to power all of this.  My graphics card recommends a minimum of a 400 watt power supply, for example.

I hope this helps!

Regards,
Bob

---

### Post by GaryH on 2007-04-29
Thanks everybody for all the fine advice. 

I'm trying to understand why my IBM T20 GUI runs slower with Feisty than with the previous OS, Microsoft Windows 2000. The T20 has a savage graphics chip set and the Feisty installer picked the savage driver so I assume the graphics are running as fast as practical. 

Thanks for the tip on glxgears and it runs at 306 fps and I agree; recompiling the kernel for the T20's PIII Coppermine isn't the answer.

Not sure what to try next.](*,) 

Peace,
GaryH

---

### Post by RTrev on 2007-04-29
> **GaryH said:**
> Thanks everybody for all the fine advice. 

I'm trying to understand why my IBM T20 GUI runs slower with Feisty than with the previous OS, Microsoft Windows 2000. The T20 has a savage graphics chip set and the Feisty installer picked the savage driver so I assume the graphics are running as fast as practical. 

Thanks for the tip on glxgears and it runs at 306 fps and I agree; recompiling the kernel for the T20's PIII Coppermine isn't the answer.

Not sure what to try next.](*,) 

Peace,
GaryH

Hi Gary,

Oh, I wouldn't assume that just having a Savage driver means it's either the correct one or that it's set up correctly.

Do a quick Google on IBM T20 and you'll find a bunch or article about getting the graphics running better.  One guy posted his XF86CONFIG file, and perhaps you can do some tweaking based on his ideas:

[http://linuxfocus.org/~guido/gentoo-tpt20/](http://linuxfocus.org/~guido/gentoo-tpt20/)

Scroll down to the bottom for the part about getting X11 running better and the link to his file.

I notice that people seem to agree that the video is one of the toughest parts of getting Linux running on these machines:

[http://mr.uue.org/gnulinux/t20/](http://mr.uue.org/gnulinux/t20/)

And, I should add that although Feisty chose a driver that worked in my case, it was by no means acceptable.  I had to go and download the latest one of the non-free drivers before I had even a chance of it working right.  Part of the problem is of course that nobody has yet written open source drivers that work as well as the ones written by the people who designed the hardware -- and until we can come up with a solution for that we either have to "taint" the kernel with non-free stuff or live with sub-optimal performance.  Not a good situation, at least at the moment.  As Microsoft slowly dies, we'll be known as "early adopters" of superior systems -- but looking at it from this point in time it can be a royal pain to get everything working right.  

Good luck, and I hope some of this helps.

---

### Post by GaryH on 2007-04-30
Thanks Bob,
Now that I have an objective metric I can tune my graphics for speed. Naturally I'll post my findings to help other T20/(savage chip set) owners.
Thanks again.

Peace
GaryH

---

### Post by GaryH on 2007-05-02
Hi Everybody,

Surf's up. :lolflag: 

Hours and hours of surfing later, I'm pleased to report that Feisty's GUI is now running acceptably fast. All my research reduced to two fixes.
First I told gnome that my hardware was slow: 
> gconftool-2 --set /apps/metacity/general/reduced_resources --type=bool true
and then I reconfigured the savage portion of xorg.conf:
> Section "Device"
        Identifier      "savage"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        Option          "SWCursor" "on"
        Option          "AccelMethod" "XAA"
        Option          "ShadowStatus" "on"
        Option          "DMAMode" "Any"
        Option          "AGPMode" "1"
        Option          "AGPSize" "8"
        Option          "DmaType" "AGP"
        Option          "BusType" "AGP"
EndSection
glxgears is now screaming at 406 fps and windows drag and resize as fast as I can move the old mouse.

**[COLOR="Sienna"]Warning:[/COLOR]** Don't get aboard this speed-up train unless you're okay with wireframe drags & resizes, rebooting in recovery, and doing the following without a GUI: reading the savage manual page, and editing xorg.conf. 

There is a bug which is related to AGP vs. PCI configure settings: Using PCI (306 fps), X always starts up after either a cold boot or a restart. Using AGP (406 fps) X always starts after a restart. Using AGP (406 fps) X fails to start 60-75% of the time after a cold boot.


Peace,
GaryH

---

### Post by RTrev on 2007-05-02
:D :D :D 

Glad you got it working!  And yes, it's kind of messy sometimes to roll up our sleeves and dig into this stuff.  There's nothing like that sinking feeling you get when you have it all tweaked, reboot, and X crashes and lands you in terminal mode.  I'm sure you know the feeling!  Then you have to go and read the Xorg log file and see what it's complaining about this time.  ;-)

This is the kind of thing that makes it hard for Linux to gain wider acceptance.  How many non-geeks would, or could, have done what you just did?  Just getting acceptable performance for normal use should be the very least we expect of an out-of-the-box OS.   And hardcore gamers with high end equipment should be able to do what they want also.  

But, there is good news.  Here's a snippet of a conversation from another group:

> 
> Dell is trying a second time to sell personal computers with Linux 
> preinstalled, this time using the up-and-coming Ubuntu version of the 
> open-source operating system.

This is big. It will force the hardware manufacturers that want to do 
business with Dell to provide Linux drivers. And I suspect that would be 
damn near all of 'em.


We're at the point where we are about to break through to the big time, I hope.  If the big boys like Dell begin shipping machines with pre-installed Linux, they're going to want them to run right.  And if the hardware manufacturers don't play ball, Dell will just find some that will.  If, for example, ATI refused to supply appropriate drivers, then Dell would just pick another manufacturer to buy video hardware from.

It's a tribute to the developers that they are able to make Linux work at all, without this kind of support from the hardware folks that Windows has always enjoyed.  If a basically broken OS like Windows can configure itself to run or whatever hardware it finds, just imagine what the Linux developers will be able to do once they have the same kind of resources.  I expect that future versions of Ubuntu will do the kind of things we've just had to do manually.. and will do it as part of the initial setup/install.  It will say "Please wait a moment while we test and optimize your hardware."  Then it will download whatever it needs, run tests to see which settings work best on the given hardware, etc.

I think the computer world has a rosy future, once it breaks free from the stranglehold Microsoft has held everybody in for the last few decades.

Warning.  If you start reading the following link for a couple of chapters, you'll be hooked and won't be able to stop until you've finished it.  And it's long.  It details about everything there is to say about MS.. which is a lot.

[http://www.vanwensveen.nl/rants/microsoft/IhateMS_intro.html](http://www.vanwensveen.nl/rants/microsoft/IhateMS_intro.html)

Any amount of work is worth it to be free to use our computers the way we want to, and not the way we're forced to.  "It's MY computer!" -- Steve Gibson

Really glad you were able to tweak things as well as you did!  Way to go!  Now we just need to help others out until people aren't willing to settle for Windows anymore.   ;-)

---

### Post by GaryH on 2007-05-02
Bob,

Thanks for the link. I just emailed it to our Corporate King of IT. 

You're right, I did get hooked. I've always thought that Microsoft products were all show and no go and that Bill Gates' was a ruthless businessman disguised as a naive geek. F.W. van Wensveen confirmed it. I wonder who F.W. van Wensveen hates more, Microsoft or all the ignorant people that keep them in business.

Do you think the inevitable global dominance of Linux will first become noticeable in China?     

Again, thanks for the link.

Peace,
GaryH

Another viewpoint: [http://www.glaven.org/archives/2005/03/why_i_hate_linu_1.html](http://www.glaven.org/archives/2005/03/why_i_hate_linu_1.html)

---

### Post by RTrev on 2007-05-02
> **GaryH said:**
> Bob,

Thanks for the link. I just emailed it to our Corporate King of IT. 

You're right, I did get hooked. I've always thought that Microsoft products were all show and no go and that Bill Gates' was a ruthless businessman disguised as a naive geek. F.W. van Wensveen confirmed it. I wonder who F.W. van Wensveen hates more, Microsoft or all the ignorant people that keep them in business.

Do you think the inevitable global dominance of Linux will first become noticeable in China?     

Again, thanks for the link.

Peace,
GaryH

Another viewpoint: [http://www.glaven.org/archives/2005/03/why_i_hate_linu_1.html](http://www.glaven.org/archives/2005/03/why_i_hate_linu_1.html)

Another interesting read.. thanks.  As for China, actually I'm very hopeful that the U.S. will embrace Linux as soon as Dell starts shipping machines with a viable alternative to Vista.  I consider Feisty very viable, but I'm not sure I'm typical.  I guess all we can do is hope.

This whole issue of the video cards is really interesting to me.  If the companies who are manufacturing these cards were to release the drivers as open source, it's my understanding that they would be violating the law by essentially publishing the way to crack the DRM protection.

The funny thing about all of this is that the DRM fiasco can't possibly work.  There's simply no way they can come up with a system that won't be cracked.. but they persist in this nonsense despite all the best security people telling them how hopeless it is.

We live in interesting times.  :)

---

### Post by Jhongy on 2007-05-05
> **GaryH said:**
> 

Do you think the inevitable global dominance of Linux will first become noticeable in China?     



No -- I've lived in China for about a decade and have seen no evidence, other than in the Western media, to support this. Everyone uses Windows -- no-one outside of major businesses actually pays for it though.

The young generation here are very computer savvy -- but most are tied to Windows programs. For example, Taobao, the hugely popular auction website, which has put eBay out of business here, uses a merchant payment system that requires an IE ActiveX control.

Millions of people use QQ chat and various QQ/Tencent online games. While QQ can be accessed through a Linux client, all of the subsidiary programs/games are Windows-only. 

ISPs install Windows-only clients as part of the 'service'. A fledgling government website that accepts payments for utility bills requires an IE ActiveX control... the most popular online city mapping system balks if you're not on IE.

This is just the tip of the iceberg -- but the point is that since no-one has paid for off-the-shelf Windows, it is practically ubiquitous, particularly since Macs have only recently entered the market. 

I've seen lots of talk in the press about Red Flag Linux and the like, but like most things about China in the Western press, it is somewhat disconnected from reality.

---

### Post by GaryH on 2007-05-05
Of course you are in a position to know but how about in 10 or 15 years when the very young are grown up? Aren't the kids in China using very robust, low cost Linux laptops such as the Longmeng? Isn't the state sponsoring low cost Linux laptops for the very young, rich and poor alike in a effort to have the next generation very computer savy?

Thanks,
GaryH

---

### Post by Jhongy on 2007-05-05
> **GaryH said:**
> Of course you are in a position to know but how about in 10 or 15 years when the very young are grown up? Aren't the kids in China using very robust, low cost Linux laptops such as the Longmeng? Isn't the state sponsoring low cost Linux laptops for the very young, rich and poor alike in a effort to have the next generation very computer savvy?

Thanks,
GaryH

The overwhelming majority of  kids are using Windows. As in other countries, what the state sponsors will end up having little bearing on what people actually choose for themselves. Especially here where the state are particularly fond of choosing for other people. Besides, even state-owned bank ATMs and the post offices patently use Windows.

I'd go as far to say that Microsoft probably  enjoys a much larger market share here than in the West, albeit a  non-paying one.

However, despite arguments to the contrary, I don't think this amounts to much brand loyalty in the long run.

J

---

### Post by GaryH on 2007-05-06
> The overwhelming majority of kids are using Windows.

I'm disappointed to hear that Jhongy. I hope that someday there will be free communication for everybody on the planet with the WWW and between each other too. I thought maybe it was beginning in China today with free Linux and state sponsored laptops for children.

Peace,
GaryH

---

