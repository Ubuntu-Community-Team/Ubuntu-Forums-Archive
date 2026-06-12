---
title: "Problem installing Opera browser"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by WorBry on 2013-02-20
Hi, 

I installed Lubuntu 12.10 a few days back (had to install 'minimal system first and then desktop) and am trying out different browsers.  

I'm having a problem installing Opera. Since it is not in the Canonical repository, I downloaded from the Opera site (Version 12.14.1738 i386.deb).

When I open it in GDebi, it asks for my password (as usual) but then declares that the password is incorrect and to try again, with the same result - plus the 'You need to have administrative rights to install software'. 

Checked the password (same one that I chose when installing the system) and I can log-on and sudo -i as normal. Tried also installing another application and GDebi accepted the password just fine. 

Went into Users and Groups and saw that my profile was manually set as a Custom account - whatever that implies, as I had not even looked in Users and Groups before, assuming that I am the Administrator (no other Users) . So I changed it to Administrator to see it would make a difference., but still the Opera installation keeps rejecting my password. 

What to do??

---

### Post by WorBry on 2013-02-20
Found the Ubuntu documentation on Opera: 

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

and finally got it to install from the deb.opera.com repository with command line installation.

So why the password problem with the DGebi install ??

And, wouldn't you kow it, first video I open in YouTube and the flash plugin crashes. I know it's complicated by this HTML5 migration thing, is there any linux browser that doesn't have issues with Adobe flash? With Chromium it likewise crashes and with Firefox just displays a blank white frame. 

The only solution I can find is using the OpenWith plug-in in Firefox to stream the videos to VLC on desktop.

---

### Post by WorBry on 2013-02-20
I'm trying to understand this issue more completely.

Am I right in thinking it because the last supported flash player for linux-based browsers was version 11.2 and that this now does not have full compatibility with all YouTube encoded content: some play, many (H264) don't. 

The one exception, as I understand, is Google Chrome (for Linux) which has the updated Adobe 11.6 player integrated and is quite distinct from the Chromium browser that comes with the Lubuntu desktop? 

There are two open-source web flash players - Gnash and LightSpark - but (from what I've read) there is no guarantee that they will play all content.

So basically, the options are:

1. Use Google Chrome, and be tracked
2. Use another browser with Adobe Flash 11.2 for the content that it can play. 
2. Stream 'unsupported' videos to a desktop player - like VLC. 
3. Try Gnash or LightSpark. Are there any others? Tried a VLC plugin for Firefox and couldn't see it working.
4. Put up with one or more of the above options until there is full browser support for the HTML5 format - H264 videos currently unsupported in Firefox, Opera and Chromium, and probably the other linux-browsers ?

---

### Post by WorBry on 2013-02-22
Ah, I see the 'Adobe Flash Plugin Crash' issue is a path well trodden, and that a (perhaps the only) solution is to downgrade to an earlier version 11.1.102.62 [http://ubuntuforums.org/showthread.php?t=1949598](http://ubuntuforums.org/showthread.php?t=1949598) Seems a bit sad that Adobe's parting gift should be so problematic, but 11.1.102.62 seems to work OK (with added security measures). In fact, with Firefox, I find that videos play alot more smoothly in Lubuntu than in XP Pro at least on my ancient PC. That said, of the three linux-browsers I've tested, Opera seems to give the smoothest playback. I was surprised.  And so endeth my monologue

---

### Post by WorBry on 2013-03-02
An epilogue:

Came across this post explaining Adobe Flash 11.2 needs a cpu with SSE2 instruction set to work.

[http://ubuntuforums.org/showthread.php?t=2070839&p=12295295#post12295295](http://ubuntuforums.org/showthread.php?t=2070839&p=12295295#post12295295)

The AMD XP2800+ CPU on my old box lacks SSE2 (SSE only), so that would explain it.....at least in linux. But then how come Flash 11.2 and above have worked with Firefox and Opera in XP Pro, which I have running on a separate drive in the same PC?

---

### Post by sda123 on 2013-03-04
Hi here is a way to install it.

Open up a terminal and type

```
sudo passwd root
```

and hit enter, it should ask you for your password. So type it in (it wont show the password by the way). Tell me if you can't get past this stage.

Then it should ask you for a new password so type one in (this won't change your normal login password).
Then confirm it and hit return.

Then type

```
su
```

Type the new password in and press enter.

Then do

```
cd Downloads/
```

Afterwards:

```
dpkg -i opera (don't press enter here, instead press tab and then enter)
```

Press enter if it asks you anything.

Then just do CTRL-D twice and terminal should close. Opera should now be installed :D

---

