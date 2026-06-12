---
title: "Xubuntu USB Installation Blues"
date: 2016-08-13
forum: New to Ubuntu
---

### Post by calimer on 2016-08-13
I have successfully installed Ubuntu using my USB with no problems.  I decided I wanted to stick with xfce so I put Xubuntu on my work PC and I recieved this message the first two tries and it would just never get past that point:
A start job is running for Ubuntu live CD installer (1 min 24s/no limit)

Now I'm trying to install it on a home PC and it always displays that message and not once has it properly given me the install screen.  I've tried Xubuntu 16.04 and 16.04.1 64 bit versions.  I'm using rufus and I tried 2.8 and 2.10.  I've tried all the option variations I can think of but I'm certainly willing to try more.  Any help would be greatly appreciated!!

Just a side note, I cannot believe how amazing Xubuntu runs on the work computer!  I am running a heavily modded minetest server for my students and previously vista was on the computer and it was capping out at 100% CPU quite a bit but with Xubuntu I haven't seen it go over 30%!!  It's just so clean and smooth too, I love it.  I really hope I can get it working on the home PC so that I can experiment more!

Thank you so much for your time!
-Mike

EDIT - Update - So strangely enough I got frustrated and went and ate food for a while and returned and it was actually at the installation screen.  I can't quite remember if I had just let it go when it was at the "A start job" bit or if I had just started it again.  I'll definitely be testing.  I have let it run a while before and it never got past.  With the work computer on the 3rd try when it actually worked I never saw that "A start job" bit at all, it went straight into the install dialogue.  Weird stuff.  Also FYI the work comp is a Dell Optiplex 760 and the home PC is a 755 (both testing machines of mine that I got cheap).  If people have more insight I'd be super interested!  I have many more PCs I'd like to install this on for the kiddos.

---

### Post by sudodus on 2016-08-13
I checked the specs at [this link](http://euro.dell.com/se/sv/corp/Station%C3%A4ra-/optix_755/pd.aspx?refid=optix_755&s=corp). Is it describing your computer correctly? In that case

- the CPU should be good enough (with a margin).
- there should be at least 1 GB RAM for Xubuntu to work well.
- there might be problems with the graphics. Is there ATI or Intel graphics?

Does it help to use the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) **nomodeset**?

---

### Post by kurt18947 on 2016-08-13
> **calimer said:**
> 
............................................................
  If people have more insight I'd be super interested!  I have many more PCs I'd like to install this on for the kiddos.

Microsoft [SIZE=1](and maybe Apple)[/SIZE] DO NOT approve this message!! Students must learn only about the Microsoft ecosphere!:frown: [J/K]

Good job exposing students to the wider world of computers & IT. People need to be familiar with Microsoft software from a work/vocational standpoint but having some exposure to the larger IT world should be beneficial. Plus if you can save the school some $$ in the process they shouldn't get too upset.

---

### Post by calimer on 2016-08-13
Yes that is it!  The case is different but same specs.  It is a 3ghz dual core with intel processors and a 256MB ATI Radeon HD 2400 PRO graphics card and 8 gigs of ram.

I don't know how to set a boot option of nomodeset.  How would I do that?

Also now that it has installed the graphics look fine and it also appears on this list as fully supported:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I'd super love to be able to fix that problem for the other PCs so I don't have to keep trying it a million times though I will try just letting it go and see if it eventually goes through and if that is what made it finally install properly.

---

### Post by calimer on 2016-08-13
> **kurt18947 said:**
> Microsoft [SIZE=1](and maybe Apple)[/SIZE] DO NOT approve this message!! Students must learn only about the Microsoft ecosphere!:frown: [J/K]

Good job exposing students to the wider world of computers & IT. People need to be familiar with Microsoft software from a work/vocational standpoint but having some exposure to the larger IT world should be beneficial. Plus if you can save the school some $$ in the process they shouldn't get too upset.

Hey thanks!  I'm starting it slow by first showing them on my computer and then kids that are interested I will let use one of the other ones.  The computers are actually mine so I can do whatever I want but I'd so love to put nix on the laptops because they are archaic and have so much windows junk on them that I bet they'd fly with xubuntu.  Also I need to look into xubuntu vs lubuntu, any idea which would have lower overhead?

---

### Post by sudodus on 2016-08-13
> **calimer said:**
> ...
I don't know how to set a boot option of nomodeset.  How would I do that?
...

See the link 'Boot option' in my previous post (Post #2) :-)

**nomodeset** should give you low but usable graphics during the installation. If it does not help, I think that there is another problem.

---

### Post by sudodus on 2016-08-13
Lubuntu is ultra light with the desktop environment LXDE, and Xubuntu is medium light with the desktop environment XFCE. Both should work well on the hardware you describe. You might notice a difference when playing high definition video (that Lubuntu plays HD video better, if the hardware is not powerful enough or close to the threshold to play well). A third option is Ubuntu MATE, with the desktop environment MATE, which is also medium light, similar to Xubuntu. Try them all live and install the flavour of Ubuntu that you like best.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by calimer on 2016-08-13
Thank you so much!  Not sure how I missed your link to the boot options, whoops!!!  Thanks for the insight about Lubuntu!!  I'll definitely give it a shot!  The best part is those computers are all extra and ones I got cheap that were basically being thrown away so I can experiment all I want on them :D

EDIT, just an FYI, trying to get to that Install Screen is always the goal.  Once I get there the install works super well, it is that that message comes before that screen and is what hangs up.

---

### Post by kurt18947 on 2016-08-13
> **calimer said:**
> Hey thanks!  I'm starting it slow by first showing them on my computer and then kids that are interested I will let use one of the other ones.  The computers are actually mine so I can do whatever I want but I'd so love to put nix on the laptops because they are archaic and have so much windows junk on them that I bet they'd fly with xubuntu.**  Also I need to look into xubuntu vs lubuntu, any idea which would have lower overhead?**

I think quite a few people feel Lubuntu is lighter but IMO a midrange or better Core2Duo machine should run Xubuntu just fine and I find Xubuntu pretty stable and it's possible to alter the appearance of the desktop pretty easily. I did have Lubuntu on a netbook - single core 1.6 Ghz. Atom N270 with 1 Gb. RAM, later 2 GB. That little thing worked quite well, FAR better than the XP home it shipped with. For a 'normal' desktop machine Xubuntu is an excellent choice. I tried Ubuntu Mate but had some hardware issues - mostly USB and didn't see any benefit to Mate over Xubuntu.

---

### Post by Bucky Ball on 2016-08-13
Lubuntu has a lower overhead, not by a massive margin, but Xubuntu is more fun and easier to use (IMHO) and more easily configurable. If Xubuntu works and you prefer it, go with that. If the specs just aren't up to it you might try Xubuntu-core (see below), or try Lubuntu as last chance. If Xubuntu-core is too heavy, though, Lubuntu will be, too.

You could always install Lubuntu, install xfce4 (the desktop environment used by Xubuntu), log out and choose the xfce4 session from the session drop-down. ;)

I have resurrected many a box destined for the recyclers or landfill with Xubuntu so full credit to you and good luck with your plans. Big fan of [Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/") nowadays ([community ISOs ]("https://unit193.net/xubuntu/core/")at the bottom of that page). Be aware though, that it comes with nothing but the kernel, xfce4 and a few things from Xubuntu. You need to install everything else either through a terminal or package manager. 

Anyway, we drift off-topic and that gets confusing. How are you going with the USB install problems?

---

### Post by calimer on 2016-08-27
Wow I did not get a notification update to these great posts so sorry for the delay responding.

I have tried Lubuntu on this PC (the same one that was having trouble with the Xubuntu install) and did not encounter the same install problem.  I did find that it boots slightly faster than Xubuntu, and it does seem to be a bit more responsive, but Xubuntu is much easier to use.

I am excited to tell you all that I FINALLY got permission to put Linux on the computers!!!  I will use Lubuntu for their laptops because they need every ounce of extra juice possible, they are mostly Dell 2120s and then I have a few Lenovo Thinkpad 420e computers.  So not very good computers, especially the Dell 2120s but the school refuses to buy anything else but chromebooks.  On my main computer, which ends up being my personal computer since they wouldn't get me a desktop PC, I am just going to keep Xubuntu on since I already have it installed.  At home I think I'm going to keep Lubuntu even on my more powerful machine since I have been doing a lot of compiling and every bit of extra CPU helps.  Lubuntu has been a bit of work at times but it has also helped me to learn a bit more too so that's good.  So far I am absolutely loving it, and I did put Linux on two computers before I received official permission because the computers were in such bad shape that I figured I wouldn't get in trouble, and students love them and are actually excited to learn about and use Linux!!  So Monday I am going through an install with all of my classes :)  I've even gotten another teacher excited to learn about Linux, and he is the science teacher so I was showing him some of the cool science related Edubuntu programs.

Regarding the install problems I haven't had any more when using that same thumbdrive with other computers and haven't had to reinstall it on this one so everything has been pretty good.  I wonder why it was just that one PC having problems.

I really want to stress how much I appreciate all of the insight you all have given me!!  Please feel free to add any more tid bits you think of because it has really helped my learning process!!

Take care :)
-Mike

EDIT - I want to add that originally Windows Vista was on our Minetest server machine and that even with just one server it was frequently hitting 100% CPU.  With Linux using Xubuntu on the same PC I can host two servers, one being a massive map of NYC, and it stays around 50%.  The only time it jumps even near 100% is if with both servers running I use the computer as a client as well.  That's an insane difference from Windows!   I of course make sure to relay that to the students and even show them the System Monitor Line Graphs and explain to them which each is and they think it is so cool.  Pretty neat to see Middle Schoolers excited about anything!!!

EDIT 2 - I also did find this interesting article about Lubuntu vs Xubuntu:
[https://www.wikivs.com/wiki/Lubuntu_vs_Xubuntu](https://www.wikivs.com/wiki/Lubuntu_vs_Xubuntu)

---

### Post by sudodus on 2016-08-27
Congratulations and thanks for sharing your solution :-)

If you think that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. It will help other users find your solution.

---

