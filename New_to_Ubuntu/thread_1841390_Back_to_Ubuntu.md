---
title: "Back to Ubuntu"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by sarwiz on 2011-09-09
Hello all, I'm getting back into ubuntu after being away for a couple of years. Had some health probs (stroke x 2) and been dealing with windows until a few days ago. i want to get back into it like before, but cannot figure out something simple like editing the boot order in grub. I have no menu.lst file and cannot quite comprehend what exactly to do. I have 9.04, 11.04 and vista on my laptop. and want to have 9.04 as the default boot OS. The old method was easy, just navigate to /boot/grub asnd gksudo gedit menu.lst, but now it appears that I have to load a totally new program just to edit this order. Am I reading this correctly? I have many pages of instructions printed out and just plain don't really understand them. HELP

---

### Post by audiomick on 2011-09-09
Hallo. If you can't find menu.lst, then I would assume that grub 2 is in charge, rather than grub legacy, as it is now known. Grub 2 has been the boot loader since 9.10, as far as I know. If you haven't already, have a look here.

[https://help.ubuntu.com/community/Grub2/](https://help.ubuntu.com/community/Grub2/)

I haven't done all that much messing around with that stuff myself, but I believe the article is quite good and reasonably up to date.

---

### Post by sarwiz on 2011-09-09
OK, thanks, I'll read it, but it looks like I might just reinstall grub 0.97 and make my life a little easier for now.

---

### Post by audiomick on 2011-09-09
> **sarwiz said:**
> OK, thanks, I'll read it, but it looks like I might just reinstall grub 0.97 and make my life a little easier for now.
Yep, also an option. ;)

---

### Post by sarwiz on 2011-09-10
ok, I tried something simple. 
cd /boot/grub/
gksudo gedit grub.cfg
changed the default value to "4"
 saved and rebooted, IT worked. 
 (really hoping I didn't totally screw things up, but I figure if it is supposed to be difficult, it must be made by microsoft)

---

### Post by Paqman on 2011-09-10
> **sarwiz said:**
> OK, thanks, I'll read it, but it looks like I might just reinstall grub 0.97 and make my life a little easier for now.

Or even easier: install startupmanager and pick your default system from a drop down box.

---

### Post by snip3r8 on 2011-09-10
I am going to say this as a light hearted joke,please do not be offended.
Were the 2 strokes you had caused by using windows?

---

### Post by qamelian on 2011-09-10
> **sarwiz said:**
> ok, I tried something simple. 
cd /boot/grub/
gksudo gedit grub.cfg
changed the default value to "4"
 saved and rebooted, IT worked. 
 (really hoping I didn't totally screw things up, but I figure if it is supposed to be difficult, it must be made by microsoft)
You shouldn't edit that file, as your changes will be removed the next time an update triggers update-grub. Instead, make you desired changes in /etc/default/grub, then run ```
sudo update-grub
``` to apply the changes.

---

### Post by sarwiz on 2011-09-10
> **snip3r8 said:**
> I am going to say this as a light hearted joke,please do not be offended.
Were the 2 strokes you had caused by using windows?

Could be true, but no, not that I know of. But I think one was caused by a "smartphone" that has aggravated me to no end. LOL

---

### Post by sarwiz on 2011-09-10
I would like to add, for everyone, watch for any signs of " not feeling well" I have had 3 TIA's and have lost some feeling in my left hand . This last one came on while I was on my way to work on 8-6-2011 at about 6 am. I had woke up feelin " off" around 4:30 that morning, but went about my business anyway. I did take 2 aspirin about 5:30 and headed out. I had one on 4-3-2010, and the first was probably 25 years ago ( don't remeber it, but the Dr said it showed on the cat scan). I have to watch my BP and glucose, and take meds since april 2010.Typing is a bit of a challenge now, but Getting easier.

---

### Post by SavageWolf on 2011-09-10
> **snip3r8 said:**
> I am going to say this as a light hearted joke,please do not be offended.
Were the 2 strokes you had caused by using windows?

This like "Your gay!11!! LolLolOlloOlll0oll!11!! Not that theirs anything wrong with that.". If you need to explain that your "joke" is not offensive then it isn't a joke, it's just plain offensive.

---

### Post by sarwiz on 2011-09-10
Got everything pretty much figured out now that I am back home. GOt the grub default set up, firefox is synced and working, and got inkscape loaded and running. Now to tackle stuff like google earth and conky, and finish my multi boot install with W7. Thanks for all your help, I'll be back with more questions later. 

P.s. i never get offended by anything, and did not feel the question was at all inappropriate, I'm sure the microsoft blue screen of death has caused more than a few strokes. , Not that there is anything wrong with it (Really, there is, but that is just one opinion in a fecal cesspool of opinions, and ..who cares. This has been typed with one and 2/3 hands and my pinkie keeps hitting the wrong keys.
The Ubuntu Counter Project - user number # 25479

---

