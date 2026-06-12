---
title: "Ubuntu eee on Aspire one: LED fix and other tweaks?"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by spaceholiday on 2008-10-25
I've just got my Aspire One and have installed Ubuntu eee on it: very easy for an absolute beginner such as myself!  Now, though I've searched, I can't seem to find how to get the wireless LED working again.  I've tried the instructions [on the community docs]("https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10(Alpha6)%20on%20the%20Acer%20Aspire%20One") but they didn't work; I got a message saying I don't have permission to change the file.  Is this because those instructions are for Hardy and not Ubuntu eee?  I thought the eee version was Hardy underneath.

I'd also appreciate any suggestions about recommended tweaks for this system on the 180g HDD Aspire One.

Keep it simple, please!  I am a complete newb at this.  Thanks to all!

---

### Post by spaceholiday on 2008-10-26
Bumpity bump, because my sound is also very quiet even at max volume, both through speakers and in headphones.

I do appreciate any help/suggestions anyone can give.  :)

---

### Post by scorchgeek on 2008-10-26
I had the same problem you did with the volume. It's actually really simple: Just open the volume control by the clock (double-click) and raise the Front volume.

---

### Post by teaker1s on 2008-10-26
upgrade to intrepid and set alsa model to acer:popcorn:

---

### Post by spaceholiday on 2008-10-28
teaker1s: I plan on upgrading soon, but in the meantime, I've discovered how to change the file.  I was pleased as punch when I found that out, but unfortunately, the lines I've entered don't seem to do anything.  

The community doc says this:
[INDENT]WIRELESS LED:

To get your awesome wireless led to blink for you based on traffic, put these lines in /etc/rc.local, just above the string exit 0 (below doesn't work).

    * Note: The 2.6.27 kernel does not appear to have these options anymore (earlier kernels do). 

sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1

The led on the front will now do the association blink, as well as blink based on wireless traffic.

rc.local may not be executable so

sudo chmod a+x /etc/rc.local 

The wifi kill switch uses these keycodes (also to use in rc.local):

/usr/bin/setkeycodes e055 159
/usr/bin/setkeycodes e056 158[/INDENT]

I entered the lines in their proper places (before exit 0), rebooted, and no wifi light.  I can now disconnect from a wifi network using the kill switch, but to be honest I don't know how much I'll use that.  I checked the kernel after reading the note (see above), and that's not the issue.  So the question remains: where did I go wrong?

---

### Post by teaker1s on 2008-10-31
depending on your editor-try saving as, weird as it is sometimes the save tab isn't enough

---

### Post by bobnutfield on 2008-10-31
You may be interested to know that there is a reasonably active user forum for the AAO, and it includes a forum devoted to just Ubuntu installs.  It is here:

[http://www.aspireoneuser.com/forum/]("http://www.aspireoneuser.com/forum/")

This forum has gotten me through a ton of trouble.  There is also a version which is complied especially for netbooks.  Take a look at it here:

[http://cdimage.ubuntu.com/releases/8.10/release/]("http://cdimage.ubuntu.com/releases/8.10/release/")

---

### Post by spaceholiday on 2008-10-31
Thanks, Bob.  I've been lurking in the aa1 forums concurrently with my browsing over here.  I hadn't known about the other link, though - it's strugging to open in another tab as we speak.  :)

---

### Post by bobnutfield on 2008-10-31
Look for the "Ubuntu-8.10-umpc-pc-USB" download.  I have tried it on a USB stick and it works quite well.  But, be aware that this version will not allow you save your settings if you use it as a live USB desktop, and the ath5k wireless module is not present (the module that runs the wireless in Ubuntu.)  If you decide to install it, the wireless is easily fixed by installing Linux-backports.

---

### Post by spaceholiday on 2008-10-31
Well, that page isn't working for me now ("load error") so I'll try it later.  And if I need to fix linux-backports, you can be sure I'll be running to the forums crying for help first.

Thanks again.

---

### Post by Tic-Tac on 2008-11-20
> **scorchgeek said:**
> I had the same problem you did with the volume. It's actually really simple: Just open the volume control by the clock (double-click) and raise the Front volume.

I istaled too the ubuntu eee on my aspireOne but the system dont recognise the ehternet card. i'm sorry for my inglish I'm Portguese. I'm very, very new on Linux Plese Help me.

---

### Post by Thorndog on 2008-11-21
Bobnutfield, any chance you could explain exactly what "installing Linux back ports" might be in this case. I want to install Ubuntu on this little toy but don't want to get myself into a battle. I'm not totally nu B but I do need explicit commands to get anything much done.
Any help would be appreciated.

---

