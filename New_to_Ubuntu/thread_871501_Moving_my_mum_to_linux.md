---
title: "Moving my mum to linux"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by kman14 on 2008-07-27
I want to move my mum from XP to Ubuntu and need a little help.
She has very little computer knowledge and only uses her computer for email, a little browsing and taking and storing photos from her digital camera.

The main thing is getting her email (contacts and mail) from outlook(xp) into thunderbird(ubuntu).
I'm not sure how to do this.

The other thing would be to plug her camera in and take the photos off it as simply as possible. Is the default program ubuntu uses easy enough or is there something better, (and how would i make it default)?

I have a 320gig western digital external usb hard drive that i was going to save the photos and email etc. on before transfering them, but I formatted it as EXT3 - does that work with windows?

Any help or pointing to relevant threads would be great.

Cheers.

---

### Post by jordanmthomas on 2008-07-27
[http://www.fs-driver.org](http://www.fs-driver.org) for ext3 in windows

Importing Outlook to Thunderbird is possible.  (A quick google suggests such anyway)

If your mom can use explorer to get pictures off her camera, she'll be fine in Ubuntu (assuming the camera works right)

---

### Post by boblemur on 2008-07-27
easiest way to do this is to install thunderbird on xp and then export all your data from outlook then import into thunderbird on xp and then you can just copy your datafiles (my dad did this, and it worked for him, but im a littly hasy on the exact details, google will know)

im not sure about the photo thing the most complicated bit would be make sure it auto mounts the camera because that is something your mum probably cant do without linux knowlege

---

### Post by mikedemario17 on 2008-07-27
keep her on windows...linux is used mostly for useing more code ...hacking and expermenting pcs...but she should stick with what she knows

---

### Post by jordanmthomas on 2008-07-27
> **mikedemario17 said:**
> keep her on windows...linux is used mostly for useing more code ...hacking and expermenting pcs...but she should stick with what she knows

I think I disagree here.  It's great for that **and** great for those who do nothing more than browse the web, check e-mail, and listen to music.

Windows "power users" are typically the ones who have the hardest time switching to Linux.

---

### Post by ad_267 on 2008-07-27
In outlook you can export the contacts as an xml file then evolution can import this, haven't tried with thunderbird but should be the same.

F-spot works great for managing and importing photos from a camera.

---

### Post by boblemur on 2008-07-27
> **mikedemario17 said:**
> keep her on windows...linux is used mostly for useing more code ...hacking and expermenting pcs...but she should stick with what she knows

i completly dissagree, ubuntu if a good alternative if all people do is use e-mail and surf the web, it works perfectly and alot faster than windows xp, some thing you could do would be:

make only one workspace so she cant get lost...

add quick launchers for all the programs she will need...

make sure you test everything first... using linux usualy dosent require that much know how its more setting it up and debugging thats hard...

---

### Post by kman14 on 2008-07-27
Thanks for the quick replies.

boblemur - i was thinking of doing something along those lines....thanks.

jordanmthomas - i agree with your disagreement. My mum is no power user.
when she first got her computer she said "i understand the screen thingy and the keyboard, but what's that big box for?"
i can set up her desktop with launch icons for the things she needs.
i'm not worried about that at all.

ad_267 - thanks for that; I'll check it out.

---

### Post by lynlow on 2008-07-27
Yeah i have just done the same thing at home for mum and dad, the only thing is you must check every thing is working first and that all the codecs are installed thats the only problem i had switching them. oh and the printer that annoyed dad the most i think my bad i forgot about that lol.

---

### Post by kman14 on 2008-07-27
sorry the replies are coming so quick.

Boblemur - single desktop is a great idea.

i've been with ubuntu for about 2 years and i've saved most of the interesting tweaks and fixes, so i can make sure everything works before i hand the computer back.

i would want to let updates install themselves automatically in the background so she wouldn't have to worry about it at all. I'm guessing that it's just an option in "update manager".

again thanks for the replies.
this forum is one of the main reasons i stick with ubuntu.

---

### Post by oneporter on 2008-07-27
My suggestions:
  1. Put a few icons on the desktop, stretch them really large (Firefox, Evolution or Thunderbird, A link to all her pictures..).  Make them single click launchable.
  2. Encourage her to ask questions (I tried to move my grand parents to linux, but they wouldn't ask any questions.  So they sat around dissatisfied and wanting windows back (oh the shame), when I could've shown them how to do whatever it was in a couple of seconds.  I sat down in front of their Windows PC today for the first time in ages and something nasty has hijacked their account.. it's awful

---

### Post by crackedparadigm on 2008-07-27
> **kman14 said:**
> 
The other thing would be to plug her camera in and take the photos off it as simply as possible. Is the default program ubuntu uses easy enough or is there something better, (and how would i make it default)?


Picasa is a great, easy to use, photo program.
[http://picasa.google.com/linux/download.html]("http://picasa.google.com/linux/download.html")

---

### Post by boblemur on 2008-07-27
> **kman14 said:**
> 
i would want to let updates install themselves automatically in the background so she wouldn't have to worry about it at all. I'm guessing that it's just an option in "update manager".


one problem with this is that im not sure that it can do this (because of the need for it to assume sudo) 

you can turn this off... but then your mum can change things and i know it dosent seem likley but you would be suprised what they can do by accident :p so maybe if you have a little script to ssh in from your computer and get it to install the updates(using your own account)

also if they are on the internet disabeling password prompt for sudo defeats alot of linux's security...

---

### Post by barbedsaber on 2008-07-27
> **mikedemario17 said:**
> keep her on windows...linux is used mostly for useing more code ...hacking and expermenting pcs...but she should stick with what she knows

That is a joke right?

The idea of installing thunderbird on windows, and using fancy import tools sounds good, and make sure you show her where everything is. The other thing is, explain the this is not windows, things are different, and she will have to keep and open mind for a little while, and accustom to a new environment. If you can get it to boot, you might want to have a look at  [linpus]("http://www.linpus.com/xampp/modules/cjaycontent/")(there is no alternative install cd, so if the computer is a bit, old, this probably won't work. Good luck.

---

### Post by kman14 on 2008-07-28
A couple of problems.

My mum's computer was given to her second hand and there is a password on the bios(?) screen that no one knows and is preventing me from changing the boot order - so i can't boot from the ubuntu cd.
is there a way around this?

The other problem is that when i plug my ethernet cable into my linux computer - i'm instantly connected. When i plug it into the windows box - i get nothing.
Is there something stupid i'm missing?

Thanks.

---

### Post by jordanmthomas on 2008-07-28
You can usually remove the BIOS password by taking out the small battery on the motherboard (looks like a watch / caculator battery) for 10 minutes or so.

---

### Post by Sef on 2008-07-28
> The other problem is that when i plug my ethernet cable into my linux computer - i'm instantly connected. When i plug it into the windows box - i get nothing.
Is there something stupid i'm missing?


You are not missing anything.  Windows is missing something. The network might have to be set up on windows.

---

### Post by darthmob on 2008-07-28
> **jordanmthomas said:**
> You can usually remove the BIOS password by taking out the small battery on the motherboard (looks like a watch / caculator battery) for 10 minutes or so. but you have to keep in mind, that this resets all settings in the bios to default. I would advice to backup them before, but I have no idea how you can do that without actually getting into it.

PS: it is an interesting idea to set up ubuntu for basic work. it should indeed work a lot better than windows. I'm used to visit my grandparents on a more or less regular basis to fix all those problems which come with windows when being used by inexperienced users. I doubt it is that easy to change their minds, but I will keep it in mind when I have to set up a new computer for anyone else.

---

### Post by billgoldberg on 2008-07-28
> **mikedemario17 said:**
> keep her on windows...linux is used mostly for useing more code ...hacking and expermenting pcs...but she should stick with what she knows

fud

---

### Post by WRDN on 2008-07-28
> **jordanmthomas said:**
> You can usually remove the BIOS password by taking out the small battery on the motherboard (looks like a watch / caculator battery) for 10 minutes or so.

You can also remove the password jumper from the motherboard and put it back again. This will reset the BIOS. The jumper can be seen in this [diagram]("http://support.dell.com/support/edocs/systems/xps400/sm/techov13.jpg"), with the label "password jumper (PSWD)".

---

### Post by MrWES on 2008-07-28
+1 for Picasa

---

### Post by Orlsend on 2008-07-28
I also cant agree with you...

Ubuntu its easier then windows.Also its easier to keep update and protected... my parents get thir computer all screwed because of viruses....

---

### Post by stevoo on 2008-07-28
> **kman14 said:**
> I want to move my mum from XP to Ubuntu and need a little help.
She has very little computer knowledge and only uses her computer for email,
The main thing is getting her email (contacts and mail) from outlook(xp) into thunderbird(ubuntu).
I'm not sure how to do this.

>>> Install thunderbird for her to get all the mails there, or bookmark her address in firefox.
Just change all the setting that outlook has into thunderbird. Create new account and set the setting of her email provider/

> **kman14 said:**
>  a little browsing 
Well Firefox 3 is already there. You may wanna install flash support for her. 

> **kman14 said:**
> and taking and storing photos from her digital camera.

The other thing would be to plug her camera in and take the photos off it as simply as possible. Is the default program ubuntu uses easy enough or is there something better, (and how would i make it default)?
[quote] 
>> I reccomend Picasa Google Album. It is very good. 

[QUOTE=kman14;5466237]
I have a 320gig western digital external usb hard drive that i was going to save the photos and email etc. on before transfering them, but I formatted it as EXT3 - does that work with windows?
Cheers.
EXT3 is not directly used by windows. Youll need to install something else in windows to support it, maybe reformat as FAT32....

---

### Post by Nitrolinken on 2008-07-28
A good resource for ideas regarding setting up linux in general for your parents or anyone who aren't going to need all the fancy stuff:
[http://video.google.com/videoplay?docid=1156740962439607466](http://video.google.com/videoplay?docid=1156740962439607466)

I highly recommend watching it, loads of good advice and tips.

Also, most important, make sure there's nothing left to configure / install. Streamlined and simple, straight forward. Keeping it obvious and clear for the new users is usually a good idea. (Which is why people sometimes think Ubuntu (or linux in general) needs to be dumb'd down a bit for the general masses.)

Oh, and if you want the same thing in text, [http://thelinuxbox.org/?p=21](http://thelinuxbox.org/?p=21)

---

### Post by Lorin Ricker on 2008-07-30
Re: post #3 above, I agree with the approach, having used (most of) it for two XP->Linux conversions.  For more help, xref see also:

[http://ubuntuforums.org/showthread.php?p=5486424#post5486424](http://ubuntuforums.org/showthread.php?p=5486424#post5486424)

(my post #5 in that thread) which points to Mozilla-definitive HowTo pages on this topic.

---

