---
title: "video color problem"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by feedmeh8 on 2008-07-29
color in videos played in VLC,Kaffene,Totem,Mplayer are all distorted. But strangely enough, if i open a video and then open the same video again, having them both run consecutively, the second video is perfect .. no problems at all. Any help appreciated :D ...May seem like a minor inconvenience, but having to run the video twice to get normal colors is getting a little too annoying :(

---

### Post by PmDematagoda on 2008-07-29
What are the specifications of the PC you are using(especially the VGA card)?

---

### Post by feedmeh8 on 2008-07-29
using lenovo t61 with intel chipset. I actually found a thread on another forum on fixing this exact problem .. and cannot find it again:(  ... fixed it a few weeks back but it seems to be something that reoccurs. frustrating :p

---

### Post by ThrowThermalPod on 2008-08-07
I'm having the same problem.  It looks like reds and blues are switched.  I'm not sure if this is related, but I installed some video codecs from Medibuntu a few hours before I noticed the video color problem.  The actual problem started when I tried to watch an AVI file that VLC listed as "broken."  VLC tried to repair the file, and when it came up to start playing, the colors were biffed.

I guess I'll try re-installing the NVIDIA video driver.  I'm running an NVIDIA 8800 video card.

---

### Post by Kane_of_NOD on 2008-08-30
i have the same problem,...

i  was making a presentation about Linux and open source.... and when I open a video file.. the colors were all fuc**d up... really...

i was  =|  completely astonished wtf?.. and of course, all windows fanboys started to laugh..


i tried:
totem, vlc, gxine, smplayer, mplayer, gnome mplayer...    :(

now what my friends?:confused:

---

### Post by rvm4000 on 2008-08-30
Have you tried to change the video output? x11 or opengl (gl/gl2 in mplayer) instead of xv.

---

### Post by falconac on 2008-09-21
Anybody ever figure this out?  All of a sudden my videos all look desaturated no matter what video player I use.  I never would have thought to open it twice, but when I did, the second video looked great.  I tried this as somebody suggested elsewhere
```
sudo aptitude install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine
``` but to no avail.

---

### Post by Mats Halldin on 2008-09-24
I had the same problem - colours got inverted in all video players.  I'm new to Linux, so I was sure this must be a simple problem.  I finally found the colour settings (V key in Kaffeine, Ctrl+U in VLC) where I reset to default values.

I still can't understand why the colours got inverted in the first place though.

In Kaffeine I still can't use the Xine engine; Kaffeine then wants to install a codec repeatedly only to conclude that it is already installed - The only way to stop it is to close Kaffeine and start all over.

/ Mats

---

### Post by practic on 2008-10-07
If you are using Totem, try Edit->Preferences->Display tab.  Crank the Hue up all the way and see if that helps.  I had to do that on a few of my systems...not sure why.

I also use the Gnome Movie Player, and it has a video output control that can be set to XV, X11, or GL.  X11 is the one that works best for me...XV can sometimes cause these color problems.  But I don't know any way to change the video output in Totem.

---

### Post by bobpur on 2008-10-07
Nobody has mentioned yellow yet, so I'm not sure I have the same problem. Everything on the video looks like your watching through yellow tinted sunglasses.

---

### Post by spawn. on 2008-10-14
I had similar issues a few minutes ago with MPlayer. All I did was go into preferences and tinker around with the settings. Sometimes the simplest answer is the solution.

---

### Post by zenzike on 2008-11-08
I had this problem too, after a fresh Ibex install. All the colours looked strange, with red turning out blue. The answer was to change the hue settings in Totem to be on maximum.

---

### Post by celsdogg on 2008-11-09
thanks practic, turning up the hue in totem fixed the video across all my players. i was having the same issue.

it is quite odd. it was fine prior to my upgrade to 8.10.

---

### Post by psychok9 on 2008-12-19
I've the same problem with 1 DivX video using Xv output.
I've tried SMPlayer with GL/GL2 output and it works fine.
The problem is with **Xv output** and normal players... how can we fix it?

---

### Post by rupert160 on 2009-01-02
My solution after a variety of problems including colour was to install SMPlayer. 

I had a basic install of MPlayer(Gstreamer) but with a large green line across the image tried to install some alternatives including MPlayer(Xine) and VLC

No success was achieved so I installed libdvdcss2 and ubuntu-restricted-extras through "add/remove" programs. This caused the colour distortion discussed above.

Finally SMPlayer installation provided perfect .avi file viewing.

---

### Post by krungthep on 2009-01-02
The problems appeared all of a sudden in my computer yesterday, after I added two new users. I don't know what caused the problem, but now all the video players I have installed (totem, mplayer, vlc, dragon and also TVtime) show the colours' hue off by 180 degrees. One avi file also shows a green vertical band and the three basic colours of the image with a different offset (ghosting).Changing the video output from "default" or "Xv" to X11 in vlc and smplayer results in perfect video. I don't know how to change the output in the other applications, but adjusting the hue to 0/360 degrees in totem or 180 degrees in the nVidia X server settings fixes the colours in most videos, but not the green band and the ghosting in that one avi file.

There are a couple of bug reports opened [here]("https://bugs.launchpad.net/debian/+source/xserver-xorg-video-intel/+bug/160866"), [here]("http://fixunix.com/mandriva/515819-inverted-video.html") and [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963"), but apparently no one knows what causes this problem nor how to fix it yet.

---

### Post by mnmus on 2009-02-06
*sigh* I do tire of this kind of stuff. Months and months of inexplicable resets (to "No longer works" status) of various sound features, video driver--*poof!* some Ubuntu update decudes I no longer *want* my nVidia card and 22" 1680X1150 resolution monitor and I have to reset them all over again--and now this: between yesterday and today, without any change in my system or warning of any kind, the #@*& video play is screwed up.

Sure, just like fixing the sound issues and the driver/monitor issues, the fix is a fairly simple kludge, but this kind of crap is a completely unnecessary waste of my time (and the primary reason I've started looking at the Windows 7 beta; surely not even Me$$y$oft could screw up basic configurations this badly).

I'm enough of a masochist that I actually like Ubuntu despite these kinds of stupid tricks it pulls, but even my masochism has its limits...

Another day, another Ubuntu kludge.

---

### Post by psychok9 on 2009-02-06
> **krungthep said:**
> The problems appeared all of a sudden in my computer yesterday, after I added two new users. I don't know what caused the problem, but now all the video players I have installed (totem, mplayer, vlc, dragon and also TVtime) show the colours' hue off by 180 degrees. One avi file also shows a green vertical band and the three basic colours of the image with a different offset (ghosting).Changing the video output from "default" or "Xv" to X11 in vlc and smplayer results in perfect video. I don't know how to change the output in the other applications, but adjusting the hue to 0/360 degrees in totem or 180 degrees in the nVidia X server settings fixes the colours in most videos, but not the green band and the ghosting in that one avi file.

There are a couple of bug reports opened [here]("https://bugs.launchpad.net/debian/+source/xserver-xorg-video-intel/+bug/160866"), [here]("http://fixunix.com/mandriva/515819-inverted-video.html") and [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963"), but apparently no one knows what causes this problem nor how to fix it yet.

I've solved with this simple actions: remove totem-gstreamer, install totem-xine (from synaptic) ;)

---

### Post by psychok9 on 2009-02-06
> **mnmus said:**
> *sigh* I do tire of this kind of stuff. Months and months of inexplicable resets (to "No longer works" status) of various sound features, video driver--*poof!* some Ubuntu update decudes I no longer *want* my nVidia card and 22" 1680X1150 resolution monitor and I have to reset them all over again--and now this: between yesterday and today, without any change in my system or warning of any kind, the #@*& video play is screwed up.

Sure, just like fixing the sound issues and the driver/monitor issues, the fix is a fairly simple kludge, but this kind of crap is a completely unnecessary waste of my time (and the primary reason I've started looking at the Windows 7 beta; surely not even Me$$y$oft could screw up basic configurations this badly).

I'm enough of a masochist that I actually like Ubuntu despite these kinds of stupid tricks it pulls, but even my masochism has its limits...

Another day, another Ubuntu kludge.

Have you modified your sources.list/repository of synaptic?
Default updates of intrepid are very stable... and often only with external/unstable updates Ubuntu can going unstable...
nVidia driver are official/stable 180.27 or more stable 177.82?
Ubuntu it's a very solid OS, but is sensitive to overclock/hardware problems.

---

### Post by mnmus on 2009-02-06
> **psychok9 said:**
> Have you modified your sources.list/repository of synaptic?
Default updates of intrepid are very stable... and often only with external/unstable updates Ubuntu can going unstable...
nVidia driver are official/stable 180.27 or more stable 177.82?
Ubuntu it's a very solid OS, but is sensitive to overclock/hardware problems.


My repo list consists of the repos available for selection in the Admin>Software Sources list. If these are causing

a. the repeated (though sporadic) sound issues
b. the repeated (though slightly less often than "a.") video driver/monitor issues and the (new today!--for me)
c. color values issue in video playback

then it's still an Ubuntu problem.

I've checked my driver version--the one Ubuntu has repeatedly reset to "doesn't exist! Go away or use a crappy 640X480 resolution on your 1680X1150 monitor"--and it' the right one, Ubuntu just randomly decides on sporadic updates to reset it to the default (This is total crap!" driver.

And none of this explains WHY Ubuntu decided to reset JUST the "hues" settings in EVERY media player.

And so far, in this thread, I've seen no explanation of WHY and HOW this occured, nor is there any evidence that this is actually being addressed by those who write the code--and note how long back this thread goes. 

Yes, Ubuntu is a solid OS, but in media matters (video, display adapters, sound) it's not yet as good as Windows Muppet Edition was (Me), and that was one of the crappiest things Me$$y$oft put out.

As long as I use Ubuntu for web cruising, office-style apps, and email, it's fine (once I got used to Flash Player getting screwed up from time to time--and that's largely an Adobe issue). When the media issues are all ironed out, it works better than any Windows I've used (and I've missed using few Windows versions since 3.0), but media portions break far, far too often and take far too much "fiddling time" and downright kludges to keep working right.

I'm using my Ubuntu box to write this. It's my main computer. I'm giving it every chance I can to persuade me. But things like this video playback issue--kludged for now--make selling the OS to others a difficult proposition, besides making my committment to give it a year or more as my "mostly exclusive" OS difficult to keep. Eight months gone, and so far not ONE month has gone by without either sound or video being screwed up, and now this lil gem. 

OTOH, I regularly recommend Puppy Linux. Very solid. Very nimble. Simple to set up (there almost isn't any setup). All the media stuff just works, right off, first thing. (Well, except getting the Flash plugin working in Opera. A very little bit of configuring there.) Never once had the kinds of issues that are ongoing with Ubuntu, beginning with my installation on this "everyday box" of 8.04 and continuing through 8.10.

So, anyone found the solution to this color change in video problem, or is it just kludge around?

---

### Post by psychok9 on 2009-02-07
Sorry, but your informations are very vague and confused to me.
I can't understand if:
1) You have added EXTERNALS repository/updates (out of the Canonical site)
2) You have enabled testing repository: some problems come with "intrepid-proposed" and "intrepid-backports" updates that are only for testing machine (very unstable).
3) What are your hardware specifications? Motherboard, soundcard, videocard etc.

p.s. Have you tried a fresh install Intrepid 8.10 with default settings? Have you tried any other distribution?

---

### Post by mnmus on 2009-02-08
> **psychok9 said:**
> Sorry, but your informations are very vague and confused to me.
I can't understand if:
1) You have added EXTERNALS repository/updates (out of the Canonical site)
2) You have enabled testing repository: some problems come with "intrepid-proposed" and "intrepid-backports" updates that are only for testing machine (very unstable).
3) What are your hardware specifications? Motherboard, soundcard, videocard etc.

p.s. Have you tried a fresh install Intrepid 8.10 with default settings? Have you tried any other distribution?

1.) No
2.) No
3.) Mobo: Asus M2N68-LA (HP Narra2-GL8E); AMD 64X2 5200+ processor; sound: nVidia onboard (*since Ubuntu had trouble "remembering" the SBLive! PCI card* *sigh*); Video: EVGA 01G-P3-N959-TR (nVidia) 9500GT 1G DDR2 (*onboard NVIDIA GeForce 6150SE disabled in BIOS*); 4GiB DDR2 PC2-6400 memory; 400GiB (nominal) Seagate HDD; Hauppauge 1800 TV Tuner (*nominally, semi-functional--no IR remote functionality, of course* *sigh*); anything else? 

"[F]resh install?"

And a fresh install of Intrepid would serve me how, exactly, I mean appart from having to reinstall apps, etc., and waste an enormous amount of time (building a list of packages I want reinstalled with the fresh install, etc., etc.) in order to get the OS to work the way it ought to have from the beginning?

Heck, if I wanted to have to start all over every six to eight months I could just use Windows.

Oh, yes, "tried any other distro"?

Yes, as a matter of fact. Started this computer on 8.04. 8.10 was a pain: video, sound, etc., of course. Suse Linux 10 (installed in a VM) was less trouble on media (video/sound) issues. Puppy Linux just works. Every Windows version I've installed in VMs has had fewer problems with video issues than the Ubuntu host. Go figure. (And yes, I've used other Ubuntu distros back to Warty Warthog on occasional use machines.)

I'll continue this trial of Ubuntu 8.X on my main computing system through the entire year I had planned to give it, regardless. But. I also plan to install Windows 7 in a dual boot config next week on this machine, so I can do a head-to-head: Microsoft *betaware* vs. Canonical "*shrinkwrap*". The video/sound issues will be a big point of comparison.

Now, I know I've strayed from the original point of this thread, and for that I apologize. Yes, the lousy video color problem is "solved" (by the kludge of having to go into configuration settings and correct what Ubuntu broke), but the point is that I should not have had to fix what wasn't broken until some update or other config in the OS/GUI/whatever broke itself. Not on something so basic as hue configurations in video playback reproduction.

And no one--apparently--has any idea why the thing broke. It's almost like asking Me$$y$oft for guideance when an update screws up. Almost. *heh*

If I weren't such a tightwad, I'd probably be looking at Apples, now. (And I'd find they had their own intractctable issues--just probably not in video/sound, where Apple is strong.)

---

### Post by psychok9 on 2009-02-08
VM isn't correct for test a better compatibility of others distribution: the virtual hardware is totally **virtual**.
Often nVidia have released some drivers (closed, not Canonical/Ubuntu responsability) not stables... Windows & Linux included. I know, I have a nVidia card, and a laptop with nVidia GPU that have the famous bug hardware of production. I've seen 177.82 on the laptop (8600M GT) and 180.27 (8800 GT) is stable for me, but some video cards with some drivers haves stability strange problem... but i can't understand if you have the same problem with the default nvidia driver of the Canonical I'm reading very few informations from your post, I understand your **unsatisfaction**, but you don't want help?
Your hue problem is very easy... and with totem-xine is totaly vanished.
The previous totem-gstreamer have, of-default, correct configuration (only if you modify the hue or click on the app reset to defaults go to wrong value).
If you need help, and I can help you, we are here ;)

The strong (or the weak point) of the Apple is a default hardware configuration. Use always the same hardware. Windows and Ubuntu have more compatibility problems (Windows is more supported from hardware company but isn't perfect because often the same company support the drivers only for the launch of the product) because need compatibility with a more and large hardware platforms.
Sorry for my bad english.

---

### Post by mnmus on 2009-02-09
> **psychok9 said:**
> VM isn't correct for test a better compatibility of others distribution: the virtual hardware is totally **virtual**.

Exactly. The VMWare virtual implementation is better than the Ubuntu host'ss NATIVE implementation. That ought to speak volumes.

> Often nVidia have released some drivers (closed, not Canonical/Ubuntu responsability) not stables... Windows & Linux included. I know, I have a nVidia card, and a laptop with nVidia GPU that have the famous bug hardware of production. I've seen 177.82 on the laptop (8600M GT) and 180.27 (8800 GT) is stable for me, but some video cards with some drivers haves stability strange problem... but i can't understand if you have the same problem with the default nvidia driver of the Canonical I'm reading very few informations from your post, I understand your **unsatisfaction**, but you don't want help?
Your hue problem is very easy... and with totem-xine is totaly vanished.
The previous totem-gstreamer have, of-default, correct configuration (only if you modify the hue or click on the app reset to defaults go to wrong value).
If you need help, and I can help you, we are here ;)

Thanks, I recognize that and appreciate it. The hue issue is simple: one day, working fine and the next, all screwed up. What changed? Nothing by me, AFAIK/can tell. Oh, yeh, I know. I accepted the updates Ubuntu suggested. Having to fiddle with resetting values because *someone else* screwed them up is Not Good. Interesting thing: in 15 years of Windows use, nothing like that ever happened to me (or anyone I knew). Just like I never had to reset ALL my sound configuration just because of updates from Me$$y$oft. How can I recommend this OS to all the "Aunt Tillys" out there when I have to lose several hours a month resetting configurations that updates Should Not Touch?

> The strong (or the weak point) of the Apple is a default hardware configuration. Use always the same hardware. Windows and Ubuntu have more compatibility problems (Windows is more supported from hardware company but isn't perfect because often the same company support the drivers only for the launch of the product) because need compatibility with a more and large hardware platforms.
Sorry for my bad english.

Aside: Your English is fine. My last year teaching in public schools (AKA Prisons for Kids), I could have wished for more students whose English was as good as yours.

I hear you on the Apple platform woes. I've said similar things for years. My foray into "One Year of Ubuntu" on my daily use computer was compelled by 

a. dissatisfaction with the way Me$$y$oft had taken Windows (e.g., Vista)
b. the issues you raise about Apple (and more)
c. just general contrariness: didn't like both Me$$y$oft and Apple dictating certain things (DRM madness, among others)

Unfortunately, I've discovered that Linux in general, and Ubuntu in particular, is still not quite prime time ready, as witness this aggravation with video playback--an issue that has plagued folks since at least July of 2008 but which still has no resolution apart from a kludge. Now, I didn't experience it in July of last year, nor in any of the intervening months. Since no one has yet explained just HOW this issue is caused, then obviously it's not yet been dealt with.

That's like being back in the bad old days of Windows 3.0--not even the days of 3.1.

I appreciate the fact that--now, with the kludge--my videos look right (you have no idea how shocking, shocking I say! Lou Dobbs looks as a Smurf :-)), but I do not find it a net positive that the issue

a. occurred to begin with--it never should have
b. has no genuine resolution, just a kludge, that may or may not resolve the issue (the issue is not resolved until it is SOLVED--that is, someone addresses its *cause*).

Please do not take me amiss. I like Ubuntu better than, say, Windows 95 or Windows Me ("Muppet Edition") and even in some ways than Windows XP. It's not as stable, media friendly and unintrusive (not in need of constant maintenance) as Windows 2000, but not bad. The media issues are simply a constant pain in the tuches.

---

### Post by practic on 2009-05-03
A few months ago, someone mentioned a problem with "green band and the ghosting in that one avi file."  I just wanted to mention that this can be caused by having video dimensions that are not evenly divisible by 8. I've seen this effect even on Windows, although not all media players will show the problem. 

Programs like AVIDemux will warn you if you try to crop a video into dimensions that can't be divided by 8. If you have such an AVI file, you can load it into AVIDemux and use the Crop filter to fix it. That will get rid of the banding and ghosting.

---

### Post by dlangeliers on 2010-04-02
Just an FYI for those having this issue. It has occurred on my system a few times so far, and I think it's related to opening up MKV files with totem.

I never have the issue with divx, xvid, or other types. It only seems to happen when I open up MKV files in totem. But then the problem occurs in all video players afterwards.

To fix I opened totem display preferences, and sure enough the hue had been set all the way down... which is weird. It's like the files are setting the hue themselves. After hitting the reset button on the options which defaulted all of the controls back to the center position, everything works fine again.

Cheers!
-Dave

---

### Post by ningke on 2010-10-30
The "Hue Up" method worked for me like a charm!!! In Totem player, do Edit -> Preference -> Display, Under Color Balance do "Reset to Defaults" fixed it up. (The "Hue" was all the way to the left for some reason...)

---

### Post by OzzyFrank on 2011-10-20
In **Totem Movie Player**, moving the **_Hue from 50% to full_** did the trick. In my case, it wasn't all the way to 0%, as I've seen reported, but was a "default" mid-point value like the other settings (which I actually figured it should be, but seems I am wrong).
[B]
GNOME MPlayer[/B], which I didn't even notice I had till now, was without issue.

**SMPlayer**... well, had nothing but trouble with that since upgrading to 11.10, which is a shame as it is my preferred video player. First it would go to play a clip, then freeze the whole system; then it would play the sound, and would only crash after I started clicking on it. Tried reinstalling to no avail, and then totally purging it and reinstalling it seemed to not fix it, but now seems to have settled.

One thing I am pretty sure of is Totem actually played fine after the upgrade, but after reinstalling Medibuntu to see if I could fix SMPlayer, the colour problems began (that was evidenced in SMPlayer at the same time, which I could see for a couple of seconds before it froze my system).

---

