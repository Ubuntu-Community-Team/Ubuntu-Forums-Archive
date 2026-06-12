---
title: "Moving from Ubuntu to Debian"
date: 2008-08-24
forum: Other OS Talk
---

### Post by TheSlipstream on 2008-08-24
So I've been all Linux-y for about four months now, and my Ubuntu is tweaked, configured and wonderful. But as much as I've learned simply from Ubuntu, I need more to make myself feel all knowledgeable, and to know that I've been at a more "pure" distro. Also for the geek cred of using a very historical and stable and original OS. Also, rolling release. Sweet.

So I'm in it for the rolling release and learning. I wouldn't mind a good checklist of what I should understand and what I'll be facing in Debian that Ubuntu never demanded on me.

Thanks for your advice!

---

### Post by sameerds on 2008-08-24
> **TheSlipstream said:**
> So I'm in it for the rolling release and learning. I wouldn't mind a good checklist of what I should understand and what I'll be facing in Debian that Ubuntu never demanded on me.

Ummm, I don't really understand what you mean by "rolling release". I used to run Debian unstable (Sid) most of the time. It is not a release, it is just the "current" state of the Debian archive. Anyway, one day I decided that I have had enough of bleeding edge "learning" for this lifetime, and hence shifted to Ubuntu for the sheer peace of mind. (I had started out with Red Hat 5.2, btw ... and shifted to Debian when Potato came out.)

I don't know if there's much difference between Ubuntu and Debian unstable/testing. I suppose you will notice that the polish is a bit less, and nobody molly-coddles you if you have a problem. You just have to figure things out the hard way. Other than that, I think you might face a few issues with drivers for some specific hardware. Ah, yes, and one thing ... you need to run a mail server, and setup a local mail account ... because the system will actually notify you about important events through email!

---

### Post by TheSlipstream on 2008-08-24
> **sameerds said:**
> Ah, yes, and one thing ... you need to run a mail server, and setup a local mail account ... because the system will actually notify you about important events through email!

Y-you're serious? That's probably the stupidest thing I've ever heard in Linux. Can I use Gmail and Thunderbird or something? Also, by rolling-release, I mean the packages in the repos are constantly being updated. Btw, will constantly getting new packages break things very often? I'm all for the lack of polish and the idea of doing it myself, but having to regularly fix things in the system because it's in it's nature to break isn't exactly attractive.

To be sure, I'll keep a dual boot. ;)

Edit: I'm also thinking of Arch Linux. I managed a command line install in Virtual Box (unsure if it was actually a good install) but because it didn't detect my wireless card (is that just to be expected from Virtual Box, or should it actually have picked it up?) I was unable to install X, and therefore didn't get the hardest part done. My wireless card is a Broadcom Air Force One, supposedly supported in the new kernel. If I do I real Arch install, will it be picked up?

---

### Post by sameerds on 2008-08-24
> **TheSlipstream said:**
> Y-you're serious? That's probably the stupidest thing I've ever heard in Linux. Can I use Gmail and Thunderbird or something?

Hahaha! It's not that bad. I just mentioned it as something to be aware of ... a mail server gets installed by default ... exim3, I think. It will even ask you which user on the system should get notification mails. And then you can use a client like Thunderbird to check your local inbox, or maybe even forward all these mails to our gmail account.

It's more of a culture difference rather than a technical difficulty. And no, it's not stupid at all. Debian does not assume any kind of desktop since it is not focussed on either desktop or server as a platform. So email is the only way to guarantee that the system can send notifications to the admin!

> **TheSlipstream said:**
> Also, by rolling-release, I mean the packages in the repos are constantly being updated.

That's what you get if you are running Debian testing or unstable. It's not a release ... that is current Debian stable.

> **TheSlipstream said:**
> Btw, will constantly getting new packages break things very often? I'm all for the lack of polish and the idea of doing it myself, but having to regularly fix things in the system because it's in it's nature to break isn't exactly attractive.

It's like this: Debian unstable (which is always called Sid) is, well, unstable. Anything can happen, although normally its not too painful. Debian testing is the "next" release. Packages in unstable that satisfy certain tests automatically get promoted to testing, unless it is currently frozen due to a release cycle. So testing is kinda more stable than unstable, but no promises are made.

I for one always ran unstable on my desktop. I did shoot myself in the foot a couple of times, though. One piece of advice: whenever you do an "apt-get dist-upgrade", look out for packages that are scheduled to be uninstalled. If you think those packages should not be uninstalled, then hit "no" and try "apt-get upgrade" instead! ;)

About Arch Linux, Virtual Box and Broadcom cards ... sorry, no knowledge of any of these!

---

### Post by mips on 2008-08-24
> **TheSlipstream said:**
> 
So I'm in it for the rolling release and learning.


In that case I would recommend Arch Linux.

Edit: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by Bachstelze on 2008-08-24
> **mips said:**
> In that case I would recommend Arch Linux.

Yup, or Gentoo. You won't learn much more with Debian than with Ubuntu, and neither is it more stable or "purer" (whatever the heck that is supposed to mean).

---

### Post by kerry_s on 2008-08-24
> **TheSlipstream said:**
> So I've been all Linux-y for about four months now, and my Ubuntu is tweaked, configured and wonderful. But as much as I've learned simply from Ubuntu, I need more to make myself feel all knowledgeable, and to know that I've been at a more "pure" distro. Also for the geek cred of using a very historical and stable and original OS. Also, rolling release. Sweet.

So I'm in it for the rolling release and learning. I wouldn't mind a good checklist of what I should understand and what I'll be facing in Debian that Ubuntu never demanded on me.

Thanks for your advice!

just go for it:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

---

### Post by habtool on 2008-08-24
From what i have read and my limited experience with Debian, which I enjoy along with the others I run on several partitions :Ubuntu, Kubuntu-kde4, arch, sidux and Debian testing and finally Mint)

If you like kde then I can highly recommend sidux:
[http://sidux.com/](http://sidux.com/)

If you into gnome and want debain, then i would advise on Debian Testing, as i have heard gnome sid/unstable can have some bad breakages (but this is only from reading sidux forums and the reason they wont yet support Gnome, until at least two developers agree to support gnome)
So for debian testing/lenny:
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)
[http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/](http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/)
 or
[http://cdimage.debian.org/cdimage/lenny_di_beta2/amd64/iso-cd/](http://cdimage.debian.org/cdimage/lenny_di_beta2/amd64/iso-cd/)

Currently seems to be little advantage going 64 bit, unless you have more than 4G ram

What i have found works well is running Debian testing and then with apt-pinning and preferences file you can get any packages from Debian unstable.
You can google these concepts later when the need arises

Any way good luck

---

### Post by habtool on 2008-08-24
> **mips said:**
> In that case I would recommend Arch Linux.

Edit: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

This is a great distro to learn from, I'll second this one too :)

---

### Post by habtool on 2008-08-24
Antoher idea,

if you have space on your HDD, then dont wipe out your current Ubuntu install.

Make up several partitions and run a few different distros, you can chainload them via grub on the MBR.
google this concept.

This way if you running debian sid/unstable and it breaks badly and you cant recover easily, you can then boot into another distro. from that distro you can then research how to fix debian sid and visa versa.

It is also fun tracking a few distros at the same time, even keep one partition spare to track the ubuntu development one as the alphas and betas some out.

Again Good Luck and do play with other distros, its a lot of fun esp if you have the time to spare

---

### Post by TheSlipstream on 2008-08-24
So Debian Testing and Arch Linux. I'll make sure to try 'em both. But could one of the Arch experts here tell me if my Wireless will work on a real install? Unfortunately I only have this one machine to install on, so wireless is quite important. Debian is starting to lose it's appeal after reading your opinions, but I'd still like to try. I'll still have Ubuntu, anyway.

Cheers!

---

### Post by Barrucadu on 2008-08-24
Well, if the wireless works in any other distro, it'll work in Arch. I've only used Intel wifi cards, so I can't tell you how easy getting it to work will be though, sorry. However, if it's supported in the kernel, it'll work fine in Arch.

---

### Post by Bachstelze on 2008-08-24
> **TheSlipstream said:**
> Debian is starting to lose it's appeal after reading your opinions, but I'd still like to try.

Well, it's certainly worth trying, maybe you'll like it better than Ubuntu. Just don't expect anything spectacular ;)

---

### Post by habtool on 2008-08-24
> **TheSlipstream said:**
> So Debian Testing and Arch Linux. I'll make sure to try 'em both. But could one of the Arch experts here tell me if my Wireless will work on a real install? Unfortunately I only have this one machine to install on, so wireless is quite important. Debian is starting to lose it's appeal after reading your opinions, but I'd still like to try. I'll still have Ubuntu, anyway.

Cheers!

Virtualbox uses the 'hosts' network connection, so that should not have been a indication of Arch not supporting your wireless card.

I would say it probably would be supported, but hit arch forums and search for your card and see if they have issues with it. I cant see it not working if it works in Ubuntu.

Arch is a lot more hands on during the install and you need to edit some files manually to get networking and other daemons running at boot time.
A lot of this is handled by this file:
/etc/rc.conf

also look at:
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

---

### Post by mips on 2008-08-24
> **TheSlipstream said:**
> But could one of the Arch experts here tell me if my Wireless will work on a real install? Unfortunately I only have this one machine to install on, so wireless is quite important. 

What wireless card do you have, brand & model please?

Do you have a normal ethernet wired connection available to install with?

I have never used wireless though but the above should help others answer your querstions.

[http://wiki.archlinux.org/index.php/Wireless_Setup](http://wiki.archlinux.org/index.php/Wireless_Setup)
[http://wiki.archlinux.org/index.php/Wireless_Setup#If_you_have_only_wireless_internet_available](http://wiki.archlinux.org/index.php/Wireless_Setup#If_you_have_only_wireless_internet_available)

---

### Post by TheSlipstream on 2008-08-24
My Wireless card is a Broadcom Air Force One (man, I type that so often my fingers are beginning to act like I'm typing my password). It is supported in the kernel by the bcm4xxx driver or something. I was simply wondering if it was possible to use it while the system is a bare bash command script run install, so that I don't need to connect to Ethernet in order to download all the required files. The only reason I'm not sure is because I don't exactly understand the nature of Virtual Box, and it wasn't able to detect it.

Based of the comments here, I'm pretty sure it'll work. I'll make sure to attempt the Arch install sometime soon. Not sure about the Debian one, though, I'm one step away from exceeding my downloads and getting dial up speed internet. 

I just want to thank everyone who answered my topic. No matter which distro I'm ultimately with, I'ma stick around here. Wonderful community! :D

---

### Post by mips on 2008-08-24
> **TheSlipstream said:**
> I'll make sure to attempt the Arch install sometime soon. Not sure about the Debian one, though, I'm one step away from exceeding my downloads and getting dial up speed internet. 


In your case I would NOT recommend a ftp install, rather use the CORE iso image file.

---

### Post by sameerds on 2008-08-24
> **HymnToLife said:**
> Yup, or Gentoo. You won't learn much more with Debian than with Ubuntu, and neither is it more stable or "purer" (whatever the heck that is supposed to mean).

Wow! It's amazing to see a rant coming from the forum staff member! If you don't think Debian is "purer" (and I agree that it never mattered to me) you can definitely say it better than making oblique comments about other people's opinions.

---

### Post by habtool on 2008-08-24
Ubuntu forums are indeed a fun mostly cordial place.
I also stick around even when I am using other distros.

Always nice to be able to give something small back when one can help.

Have fun and good luck
Ciao

---

### Post by Bachstelze on 2008-08-24
> **sameerds said:**
> Wow! It's amazing to see a rant coming from the forum staff member! If you don't think Debian is "purer" (and I agree that it never mattered to me) you can definitely say it better than making oblique comments about other people's opinions.

What the heck is that? Since when does being a mod mean you can't express your opinions? I really don't think I was disrespectful to anyone in this message...

---

### Post by habtool on 2008-08-24
> **HymnToLife said:**
> What the heck is that? Since when does being a mod mean you can't express your opinions? I really don't think I was disrespectful to anyone in this message...

I don't think anyone is offended :)

I personally cant see why a mod cant voice an opinion.

As  long as no one is rude, then its all fair play

---

### Post by sameerds on 2008-08-24
> **TheSlipstream said:**
> I just want to thank everyone who answered my topic. No matter which distro I'm ultimately with, I'ma stick around here. Wonderful community! :D

All the best, then. Fare thee well!

But there's one thing I have been thinking ... what is so great about exploring distributions, actually? I am really curious about that. I used Debian because back then we needed something better than rpm to manage our servers better, and using apt and its cousins was (still is) the way to go.

Would it be more interesting to try Kubuntu and Xubuntu in parallel with Ubuntu? Experiencing a different desktop might expose you to ideas that might not be present in Gnome. And if the idea is to simply get "more Linux-y", you could just explore the innards of the Ubuntu system more ... installing services, hacking at scripts to automate things on your system, etc. Maybe even get LAMP working and integrate that with a mail server.

Another possibility is to volunteer as a tester for the next release. You could actually try to learn how packages are built and how things get fixed in them!

---

### Post by Flyingjester on 2008-08-24
> **hymntolife said:**
> yup, or gentoo. You won't learn much more with debian than with ubuntu, and neither is it more stable or "purer" (whatever the heck that is supposed to mean).

+1

---

### Post by habtool on 2008-08-24
> **sameerds said:**
> 

But there's one thing I have been thinking ... what is so great about exploring distributions, actually? I am really curious about that. I used Debian because back then we needed something better than rpm to manage our servers better, and using apt and its cousins was (still is) the way to go.

!

For some of us it is fun to watch how different distos develop over time. Each time I try a new distro i found or learn something I did not know before, so its fun to do.

Suppose all depends what one wants to get out of it and do with ones time in Linux

---

### Post by habtool on 2008-08-24
> **Flyingjester said:**
> +1

Ubuntu, is really a snapshot of debain unstable/sid every 6 months and then worked on to make it as stable as possible before release, that much I think is a fact.
(incl adding some GUI's etc)

And you are both saying that debian SID = a Ubuntu release is as stable as debian stable.

Surely not, you have got to be joking!

:)

---

### Post by Bachstelze on 2008-08-24
> **habtool said:**
> And you are both saying that debian SID = a Ubuntu release is as stable as debian stable.

Surely not, you have got to be joking!

I've been running Debian since 1999, I think I know what I'm talking about.

However, we have to compare what it comparable. When I say that Debian is no more stable than Ubuntu, that means with the *exact* same set of packages installed. Otherwise, the comparison is void, any problem you might encounter could very well be caused by some bad package, not by the system itself.

---

### Post by habtool on 2008-08-24
> **HymnToLife said:**
> I've been running Debian since 1999, I think I know what I'm talking about.

However, we have to compare what it comparable. When I say that Debian is no more stable than Ubuntu, that means with the *exact* same set of packages installed. Otherwise, the comparison is void, any problem you might encounter could very well be caused by some bad package, not by the system itself.

I agree with this:
However, we have to compare what it comparable. When I say that Debian is no more stable than Ubuntu, that means with the exact same set of packages installed. Otherwise, the comparison is void,.

If one wants to play close to the latest and greatest then Ubuntu and Debian Sid are the way to go, however if one is looking for stable, then very little will beat Debian stable.

Also take the up coming Debian stable release being lenny, that will NOT have the unstable/alpha pulseaudio in it, or KDE4 for that matter, which again shows that Debian releases are after stability vs Ubuntu releases that try for the cutting edge, which is always at the expense of stability.

That's why I think its true to say that 'Debian RELEASES' are more stable than 'Ubuntu RELEASES, that is again in my view a fact.

Ubuntu tires to be bleeding edge and Debian tries to be stable, there cant be much argument in this logic.

This is very much a Red Hat is more stable than Fedora concept, for anyone to say Fedora is more stable than Red Hat would be incorrect.

So i Say Debian Stable releases are like Red Hat releases.
Ubuntu releases are like Fedora releases.
(Remember Debian testing and Debian Unstable are NOT releases, but development environments used to finally make Debian stable, which is the only release that Debian makes every 2-3 years.

I am NOT knocking Ubuntu, just highlighting that Ubuntu exist for a reason, being faster releases than Debian, and then add the GUI's etc. So by its very nature Debian RELEASES will always be more stable than Ubuntu RELEASES.

Hope this makes sense, it does to me :)

---

### Post by swoll1980 on 2008-08-24
> **HymnToLife said:**
> I've been running Debian since 1999, I think I know what I'm talking about.

However, we have to compare what it comparable. When I say that Debian is no more stable than Ubuntu, that means with the *exact* same set of packages installed. Otherwise, the comparison is void, any problem you might encounter could very well be caused by some bad package, not by the system itself.

That's a silly way to make a comparison IMO. Most comparisons are done as is. If I'm doing an article comparing two sports cars, I do the comparison based on how the cars are when they are new and untampered with. I definitely wouldn't say "car a" was faster than the "car b" (when it is obvious that it was not) then defend my absurd statement by saying well that's if you take the engine out of "car B", and put it in "car a" so that I could make a fair comparison. No?

---

### Post by mike1234 on 2008-08-24
I have Debian 4.0 on 3 DVD's. I like that aspect over a live cd distro. You can install anything you want right out of the box without an Internet connection. I have used Lenny as well. But leaving Ubuntu for Debian? I think you'll be dissappointed to say the least. No firefox or thunderbird. Sources are ancient compared to Ubuntu. Flash. Java, and nvidia 3D is a pain to configure. GTK is only version 8 or so. You'll need 12 I believe to run FF3. Of course you can use Iceweasel (what a name) if it's not too embarassing. Try calling up your GF and ask if she wants to try out your iceweasel. I installed it (FF3) locally as opposed to system wide. (again a pain). Lenny is better than etch I think but it's not going to be the same experience you'll find with Ubuntu. One reason I like live distros is I can try it to see if I like it. I don't believe Debian has a live cd. I like Debian but it's just too much of a hassle. Creating symbolic links and all for FF, not to mention redoing it when you update FF. Take a look at some of the Debian "how to's" or the Debian way installs.  See where I'm going? Good luck! I'm trying Kubuntu 8.04.1 on a live cd right now. Get a distro on live cd to "play" with. No way I'm going to delete Ubuntu. It works just fine!

M.

---

### Post by tel93 on 2008-08-24
> **sameerds said:**
> Other than that, I think you might face a few issues with drivers for some specific hardware. Ah, yes, and one thing ... you need to run a mail server, and setup a local mail account ... because the system will actually notify you about important events through email!
I never do that. Does anyone?

---

### Post by sameerds on 2008-08-25
> **tel93 said:**
> I never do that. Does anyone?

Hmmm ... you're right! I was bit hasty in mentioning an email server ... you don't really _need_ one, unless you are very interested in the  low priority questions from debconf. I am just completely used to having an MTA running so that all my own scripts can send in notifications. No wonder I got such an unexpected reaction from the original poster when I mentioned the email server!

---

### Post by sameerds on 2008-08-25
> **habtool said:**
> For some of us it is fun to watch how different distos develop over time. Each time I try a new distro i found or learn something I did not know before, so its fun to do.

Right. In that case, the original poster wouldn't gain much by trying Debian. Ubuntu is very closely related to Debian, but with different audiences in mind. Would be much more interesting to try other distros that have nothing or very little in common instead. Or even go for one of the BSDs or OpenSolaris!

---

### Post by TheSlipstream on 2008-08-25
Apparently this driver for my card is pretty awful. I mean, it didn't work, just generally speaking. In Arch, would it be possible for me to set up past the core stage with Ethernet, and then install the Ndiswrapper driver once I have a working system? I've tried this driver in Ubuntu, it also doesn't work, so it really is broken.

Can I use Ndiswrapper in Arch?

---

### Post by Bachstelze on 2008-08-25
> **TheSlipstream said:**
> 
Can I use Ndiswrapper in Arch?

Yes, why not? It is a Linux thing so can be used on any Linux.

---

### Post by mips on 2008-08-25
> **TheSlipstream said:**
> Apparently this driver for my card is pretty awful. I mean, it didn't work, just generally speaking. In Arch, would it be possible for me to set up past the core stage with Ethernet, and then install the Ndiswrapper driver once I have a working system?

Yes. The base install on the cd's also contain wireless tools with several drivers so you can try and get it going that way first. The kernel includes the b43 module, current kernel version is 2.6.26.2-1 from the repos.
If that does not succeed just use your normal ethernet. You could do either or, the choice is really yours.

> **TheSlipstream said:**
> 
Can I use Ndiswrapper in Arch?

Yes.

---

