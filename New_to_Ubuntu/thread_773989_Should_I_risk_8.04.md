---
title: "Should I risk 8.04?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by monkeymoo on 2008-04-29
When I upgraded from feisty to gutsy (when gutsy was first released) I had the problem that the default kernel (Ubuntu 7.10, kernel 2.6.22-14-generic) would not boot. It got stuck after a while and would just flash a black screen, then nothing, just leaving me with a command line. 
I asked on these forums how to solve the problem, but I couldn't find a solution. Instead I set grub to load the other kernel (Ubuntu 7.10, kernel 2.6.20-16-generic), which worked fine, although no fancy graphics (i.e. compiz) stuff worked at all, and it would crash to log-in screen if I ever started a program using OpenGL. 

What I want to know is whether I should upgrade to 8.04. If it's possible that I won't be able to get any kernel to work after the upgrade then I don't want to risk it! On the other hand, I guess the new kernel might work fine, and all problems will be solved. 

I know it's probably tough, but any advice would be appreciated. Just ask for any more information that would be useful to you, I'll be happy to give it. I'm not sure what is relevant though. 

(I'm using 64bit if that's relevant at all.)

---

### Post by gn2 on 2008-04-29
Have a go with a Live CD to see if it likes your hardware, then decide.

---

### Post by bilal.17 on 2008-04-29
the first time i loaded after the upgrade from hardy it didnt boot with the latest kernel for some reason... but then when i installed updates in the other kernel that was also running hardy and then rebooted it worked and everything was fine...i was using the beta so ur experience will probably be much different

---

### Post by monkeymoo on 2008-04-29
> **gn2 said:**
> Have a go with a Live CD to see if it likes your hardware, then decide.
Thanks. That sounds like a good plan. Although is running from the live cd a good test of what will happen when you upgrade? As I don't want to be doing a fresh install.

---

### Post by gn2 on 2008-04-29
> **monkeymoo said:**
> Although is running from the live cd a good test of what will happen when you upgrade? As I don't want to be doing a fresh install.

It will only tell you if your hardware is compatible.

As for doing an upgrade there are many variables to consider, like any non-repo software or installer scripts you may have used that might cause problems for the upgrade.
e.g. Envy.

There's only really one sure-fire way to find out if an upgrade will work on your specific system.... which is to upgrade.

Make sure you back up all your data to removable media first.

---

### Post by billgoldberg on 2008-04-29
Do a clean install to avoid such problems.

---

### Post by Sef on 2008-04-29
> Thanks. That sounds like a good plan. Although is running from the live cd a good test of what will happen when you upgrade? As I don't want to be doing a fresh install.

A live cd will check for compatibility, if you can use the live cd without any problems, then chances are the upgrade will go ok.

---

### Post by daengbo on 2008-04-29
Upgrade can cause problems, especially if you have software from outside the repositories installed. I try to keep my /home on a separate partition and do a clean install when a new release comes out.

That said, the upgrade process has been thoroughly tested for the LTS release from both 7.10 and 6.06 so you shouldn't have trouble.

---

### Post by monkeymoo on 2008-04-29
Thanks. 
The reason I don't really want to be doing a clean install is that I have over 360GB of data on this computer which is a total pain to back up to removable media. 
I also have a 32-bit feisty chroot, which I don't want to lose/damage because I use it for vital programs that don't run in 64-bit. 

I'm downloading the iso of 8.04 anyway. I'll try the live cd, and then make a decision. 

I don't suppose anybody knows what the original problem actually is and whether it's solvable do they?

---

### Post by caravel on 2008-04-29
I ran the distribution upgrade from synaptic for the hell of it and it crashed at the point where it was asking something about importing my menu.lst, I then had to alt+f2 and reboot from the terminal.  On reboot the the new login screen game up, but after logging in there was nothing but a blank x background.  I just formatted and reinstalled from a livecd and now it's working fine.

---

### Post by martyssweb07 on 2008-04-29
realistically, if you don't care about the new features, and aren't a junkie (like most of us) which have to have the latest and greatest regardless of the consequences... (personally I upgraded two months ago, because I couldn't wait for the release)... Then your probably better off staying with gutsy for the time being.  

Usually a month or two after release (open or closed source) is when the majority of the major bugs and concerns are squashed.

just my opinion.

---

### Post by gn2 on 2008-04-29
> **monkeymoo said:**
> I have over 360GB of data on this computer which is a total pain to back up to removable media.

Better hope the hard drive(s) don't fail.....

I recommend keeping *at least* two copies of everything you need to keep on separate drives, one copy on the PC and another copy on an external drive or NAS device.

---

### Post by monkeymoo on 2008-04-29
> **gn2 said:**
> Better hope the hard drive(s) don't fail.....

I recommend keeping *at least* two copies of everything you need to keep on separate drives, one copy on the PC and another copy on an external drive or NAS device.

I have 2 internal hard drives both 500GB (so total 1TB). The 360GB I spoke about is on both these drives (so it is backed up). 

Could I therefore do a fresh install on one hard drive (leaving the other with the data on)? What would I need to copy to keep all my programs and settings from the old install? Can I keep the 32-bit chroot in tact if I copy that over and back onto the fresh install? 

---
In a way I see the sense in not risking the upgrade, but as gutsy isn't working properly anyway I'm not exactly in a great place now! Hence the temptation of Hardy Heron.

---

### Post by martyssweb07 on 2008-04-29
Well if your having problems with gutsy trying to upgrade it is probably the wrong way to go.  I personally would only suggest upgrading a system your happy with, and not upgrading hoping it fixes the problems.  Honestly, if it does great, but if it doesn't you'll just have no chance of figuring out why or how to fix it.

---

### Post by monkeymoo on 2008-04-29
I tried booting the live cd of Hardy to see if that would work and it won't even boot! 

I get this error: > isolinux: Disk error 80, AX=4280, drive 9F
I checked the md5sum of the iso before burning and it's ok. 

I guess this means I'm staying with my half-broken Gutsy. 

Anything anyone can offer is appreciated.

---

### Post by daengbo on 2008-04-29
Did you check the MD5SUM after burning?

---

### Post by monkeymoo on 2008-04-30
> **daengbo said:**
> Did you check the MD5SUM after burning?

How do I do that exactly? 

I tried this ```
md5sum -c md5sum.txt | grep -v 'OK$'
```
and all I got was this ```
md5sum: ./casper/filesystem.manifest: Input/output error
./casper/filesystem.manifest: FAILED open or read
```

Over and over, with different files each time. So I don't think I did it quite right. 

Sorry for being dumb here.

---

### Post by Tux Aubrey on 2008-04-30
Apart from your burning problem (lol - try a different ointment), I'd recommend heeding the advice from martyssweb07:

> Usually a month or two after release (open or closed source) is when the majority of the major bugs and concerns are squashed.

If you can wait, do. :(

I hate to say it, but I think Hardy has some pretty major kernel-related and networking bugs (for some people, not for others) and the devs are still off at the after-party on the French Riviera as far as I can tell.  When they get back and dry out, I'm pretty sure we'll see some pretty major bug fixes.

I have upgraded one machine and things went (fairly) fine, except for file-sharing, but I'll not risk my main work machine for a couple more weeks or a month.  But then again, Gutsy has been totally problem for me and I really don't want FireFox 3.0 until it has critical add-ons and is bug free.

---

### Post by daengbo on 2008-04-30
You can check the md5sum of a burned CD by doing
> md5sum /dev/sdc
replacing /dev/hdc with your CD drive's device.

---

### Post by MaindotC on 2008-04-30
Stick with Gutsy until Hardy's first set of updates come out.  I downloaded some updates today but I think they were proposed, not ubuntu supported.

---

### Post by monkeymoo on 2008-04-30
> **daengbo said:**
> You can check the md5sum of a burned CD by doing

replacing /dev/hdc with your CD drive's device.

OK, I did that and got this: ```
md5sum: /dev/cdrom: Input/output error

```

What does that imply? Doesn't sound good to me.

---

### Post by jimv on 2008-04-30
Upgrades scare me.  I've never had one go perfectly.  I know you don't want to do it, but your best bet is to back up anything important and do a clean install.  It's the safest way to do it, hands down.

---

### Post by monkeymoo on 2008-04-30
> **jimv said:**
> Upgrades scare me.  I've never had one go perfectly.  I know you don't want to do it, but your best bet is to back up anything important and do a clean install.  It's the safest way to do it, hands down.

At the moment I'm planning on following everyone's advice. So I'll wait a few weeks, then try the upgrade (if the live cd works), and if that is a mess I'll fresh install. 
It's not as if I take away the possibility of a clean install by doing the upgrade as I guess doing a fresh install will delete everything on my hard drive anyway... or am I wrong? 

The first problem to overcome is getting an Ubuntu CD that boots of course!

---

### Post by crjackson on 2008-04-30
> **monkeymoo said:**
> At the moment I'm planning on following everyone's advice. So I'll wait a few weeks, then try the upgrade (if the live cd works), and if that is a mess I'll fresh install. 
It's not as if I take away the possibility of a clean install by doing the upgrade as I guess doing a fresh install will delete everything on my hard drive anyway... or am I wrong? 

The first problem to overcome is getting an Ubuntu CD that boots of course!

It sounds like a good plan to me.  I have upgraded one of my machines (I still have several to go) and so far Hardy works great.  I've found a couple of small bugs but overall it works just as well as my ROCK SOLID install of Gutsy 64.

I would try burning that CD on a different brand media and at a moderate burning speed.  It sounds like it's not able to properly read the CD for booting purposes.  Try a known good bootable CD (possibly your Gutsy install CD) and varify that you don't have a drive I/O problem.

My guess is a bad burn weather media related or burner related.  Post back and let us know...

---

### Post by Tux Aubrey on 2008-05-01
> It's not as if I take away the possibility of a clean install by doing the upgrade as I guess doing a fresh install will delete everything on my hard drive anyway... or am I wrong? 

Normally, yes - If you choose to overwrite your active Gutsy partition.

But as with everything Linux, there are ways around that:

1. If you have a few gigs of spare disk space, install Hardy on another partition.  You can then dual boot Hardy and Gutsy for a while and copy whatever you need to the new partition before you switch permanently.  There are a few "gotchas" with this - especially if Hardy changes a UUID (as it did for me)or you get a kernel update for one and not the other and the grub menu.lst gets changed - but its a good way to test a new release without abandoning a working installation.

2. Plan ahead and next time you do a clean install, create a separate partition for your /home directory.  When you next do an upgrade to a newer version (or even change distros) you don't have to overwrite your files and settings.

3. There are also tutorials on the web that guide you through moving your existing /home to a new partition.

---

### Post by spacefreak86 on 2008-05-01
Eh, I've had some problems with Hardy doing upgrade method from Gutsy. I'd go ahead and try out the LiveCD and test your hardware first. I guess with any other operating system, if it isn't broke, don't fix it.

---

### Post by monkeymoo on 2008-05-01
OK. So I did md5sum on my old Feisty CD and that gave me a result. 

The new Hardy CD still gives me ```
d5sum: /dev/cdrom: Input/output error
```

So it's not my drive or anything like that, but the disc. 

Also it's not the brand of media because the two discs came from the same box! 

It's not the iso because the md5sum of that is correct on my hard drive. 

So it's the burn. 

What I need to know is how to burn better. I just used CD/DVD Creator on the slowest speed available in the drop-down menu (9.4x for a CD). Is there another way to burn the disc at a slower speed, or anything else I should be doing to make sure it'll do a good burn. Any suggestions are appreciated as I have enough coasters in my house already! 

By the way, the disc appears to be fine and it's called "Ubuntu 8.04 amd64" when you browse it in nautilus, and I can open files on it. It just won't boot or do a md5sum... don't know if that gives any clues or not but thought I'd mention it. 

Thanks

---

### Post by Myglaren on 2008-05-01
I have just (yesterday) done my second upgrade, more to see what would go wrong than for any other reason.
It was the second upgrade, the first being from Fiesty to Gutsy, so the stage was set for problems.
Of which there were none.  Just like last time, everything worked perfectly and as smooth as silk.
Almost a disappointment although I am of course delighted to find that everything was as it was supposed to be.
Haven't even had to install Flash to get YouTube working, as I expected to have to do.

---

### Post by wedgiey1 on 2008-05-01
I had trouble with my disc as well.  I was doing a clean install of 8.0.4 and it would get to about 30-50% of the install and bomb on me.  I re-burned using the iso at a lower speed (24 I think) and it worked fine the 2nd time.

This is the first time I've used Linux in any form so take my comments for what you think they're worth.

Apparently 8.0.4's kernel (is this that 'hardy' I hear people talking about?) breaks Synergy, so if you use that be forewarned.

Every time I try to restart it hangs and I have to manually power down and back up.

Seems a tad slow browsing with firefox, especially scrolling with the mouse wheel.  This could be a graphical issue though?

---

### Post by Myglaren on 2008-05-01
> **wedgiey1 said:**
> 

Seems a tad slow browsing with firefox, especially scrolling with the mouse wheel.  This could be a graphical issue though?

My experience has been the opposite.  Firefox 3 is very quick, leaves Safari miles behing (on the Vista machine) and is like lightening on this machine.

---

### Post by cartisdm on 2008-05-01
I didn't read through the pages of replies (I'm too lazy) so I might be repeating something but definitely go with a liveCD first.  You mentioned doing an upgrade, personally I've always had success with them but I have read lots of problems by other people saying it's not worth the trouble it causes.

Either way is entirely up to you.  So far the only issues I've come across in the upgrade have been wireless with the intel 3945 card so unfortunately I had to downgrade:(

---

### Post by cartisdm on 2008-05-01
double post....weird

---

### Post by monkeymoo on 2008-05-02
OK. I'm giving up on that burn as there's something clearly wrong. 

As CD/DVD Creator didn't work, I'm trying something else. 
Should this code give me a decent burn? 
```
cdrecord -v dev=0,0,0 speed=1 ubuntu-8.04-desktop-amd64.iso
```

Thanks.

---

### Post by Samhain13 on 2008-05-02
If you have a spare partition or if you'd like to make one, check this out:
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

It saved me (really!) when my CD drive broke in the middle of installing 7.10 and left my box without a working OS. With that method, you eliminate the risk of installing from a bad burn and/or with a faulty CD drive.

---

### Post by monkeymoo on 2008-05-02
> **Samhain13 said:**
> If you have a spare partition or if you'd like to make one, check this out:
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

It saved me (really!) when my CD drive broke in the middle of installing 7.10 and left my box without a working OS. With that method, you eliminate the risk of installing from a bad burn and/or with a faulty CD drive.

Thanks, I'll bear that in mind, but I'll try the live CD one more time first. Good to have so many options!

---

