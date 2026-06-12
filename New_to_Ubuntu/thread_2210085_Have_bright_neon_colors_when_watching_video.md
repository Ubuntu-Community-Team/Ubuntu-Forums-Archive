---
title: "Have bright neon colors when watching video"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by gregg3 on 2014-03-08
I'm new. I'm running Xubuntu 13.10 in an old Dell Optiplex 170L Desktop PC. I attached a couple of screenshots from Sysinfo if that helps. Whenever I watch video (see the third screenshot) these wild disotred neon-like colors are on the screen. And often the sidebars of other screens (when I'm not watching video) are the same distorted colors and often flickering. (Even when what's in the sidebar, although a digital image, is not video.) I've uninstalled and reinstalled the Adobe Flash Plugin. But that made no difference. I've seen that a few others have had this problem but their solutions have not worked for me. Any suggestions?

---

### Post by mörgæs on 2014-03-08
Hi, welcome to the fora.

Many of the old Optiplex have Intel 8xx graphics cards. If that's the case for you here's a solution:
[https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html)

---

### Post by gregg3 on 2014-03-09
Thanks very much for replying but it's beyond my skill level to implement this tip:

[I]try UXA again according to this tip

Edit (or create) /etc/X11/xorg.conf as follows: (ugh, can't format,
should be a tab before each line except the first and the last).

Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection[/I]

If it were broken down in a step-by-step process I could do it.

---

### Post by gregg3 on 2014-03-13
I've been trying to figure out this problem of glaring neon-like colors when I play videos (see screenshot). I've tried uninstalling and then reinstalling the Adobe Flash player. I've tried upping the screen size by hitting F11 and then right clicking on the video, choosing "settings" and then hoping to uncheck "enable hardware acceleration" but it would not let me uncheck it. Someone helped me go into the nano editor and add 

EnableLinuxHWVideoDecode=0

to the Adobe file. That didn't work either. My latest thought was to try to force install the latest Adobe Flash Player in the Synaptic Manager but then I got warnings that I might damage dependencies. 

I'm not a big video watcher but every now and then there's a video tutorial on learning Ubuntu that would really help me. So, anybody got any ideas? Thanks!

---

### Post by 3rdalbum on 2014-03-13
What's your graphics card and what driver are you using?

If you have VLC, and you change the video output module in VLC's preferences, does it replicate the problem?

I've seen a similar type of problem caused by Nvidia drivers not working well with a particular video output module. Using a different version of Nvidia drivers fixed the problem for certain cards and introduced it for others. You might just need to change driver version.

---

### Post by Frogs Hair on 2014-03-13
***Threads Merged***

---

### Post by gregg3 on 2014-03-13
> **3rdalbum said:**
> What's your graphics card and what driver are you using?

If you have VLC, and you change the video output module in VLC's preferences, does it replicate the problem?

I've seen a similar type of problem caused by Nvidia drivers not working well with a particular video output module. Using a different version of Nvidia drivers fixed the problem for certain cards and introduced it for others. You might just need to change driver version.

Thanks for responding, 3rdalbum. As far as I can tell my graphics card is: VGA compatible controller, which I assume is Intel. And my driver is i915, which I again assume is Intel. I've attached a screenshot from the terminal. I wouldn't know how to change video output modules or drivers so I would need pretty detailed instructions to do that. Thanks again.

---

### Post by mörgæs on 2014-03-14
Yes, you have the old Intel graphics as I thought. 
What exactly went wrong when you tried the xorg solution?

---

### Post by gregg3 on 2014-03-15
> **mörgæs said:**
> Yes, you have the old Intel graphics as I thought. 
What exactly went wrong when you tried the xorg solution?

Thanks morgaes. I didn't try the xorg solution. It just seemed too complicated back then. Now I am a little more familiar with the terminal and feel I could attempt it, but I would appreciate it if it could be made clearer. I really need a step-by-step approach to it. So many people, although wonderful in their desire to help, assume that newbies know more than they do. Thanks.

---

### Post by gregg3 on 2014-03-15
Morgaes, I found a way to get the video to work in Firefox. It's using the Firefox add-on for the HTML 5 Video Player. Here's the link: [https://addons.mozilla.org/en-US/fir...ube-all-html5/]("https://addons.mozilla.org/en-US/firefox/addon/youtube-all-html5/")  And just installing the add-on was not enough. I had to go into the html 5 Player's "preferences" (see 97 screenshot) and check "Disable Flash on Youtube." That did it. 

So if anybody needs to do this. 1) Go to the link 2)Click on the "Add to Firefox" green button (see 99 screenshot) 3)Click on "Tools" in the toolbar uptop.  A drop-down menu falls open. 4) Choose Add-ons  5) If "extensions" isn't open, click on it (on the left) 6)find the html 5 player extension and 7)click on "preferences" button 8)Check the box "Disable Flash on Youtube" (again, see screenshot 97). 9) X out of the screen. You're done. No need to reboot. Just test a video.

If you're having the same problem I was, this was a quick easy solution.

---

### Post by bdotfife on 2014-03-24
Thanks gregg3! This method fixed my colors while viewing youtube vids (vids were also compressed horizontally).

Must be a Flash problem, right?
Now I need to figure out why colors are reversed (negative, like OP's "neon" effect) while viewing videos offline.
Same effect in Movie Player or VLC media player.
Recently installed Ubuntu 12.04 LTS.
I have installed Adobe Flash plugin but that only effects Firefox (and didn't help).
Also have installed "Ubuntu restricted-extras package" from Ubuntu Service Center.

I wonder if these viewers are using Flash, and whether I can disable it?

Thanks again from a new Ubuntu fanatic.

edit: I can't get a screenshot, when the cursor crosses the border of the window 
the video goes black, still running audio.

---

### Post by bdotfife on 2014-03-24
UPDATE: 
Today I clicked on a email link to a video that was on another site (not youtube),
the problem still exists. Need to figure out how to keep Flash from being used
on other sites. A setting in Firefox maybe?

As far as the offline viewing, I found that the saturation, hue, etc. settings
in Movie Player and VLC were screwy, took a while to adjust but they are 
working now!
I had several posts about this problem in askubuntu and linux forums, 
with a few answers, nothing seemed to work.
Thanks again...B.

EDIT: that was easy, in Firefox selected Tools, Addons, Plugins, and 
set Shockwave Flash to "never activate". Vids from other sites
work fine now.

---

