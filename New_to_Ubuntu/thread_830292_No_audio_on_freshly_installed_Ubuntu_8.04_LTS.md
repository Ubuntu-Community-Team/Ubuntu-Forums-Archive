---
title: "No audio on freshly installed Ubuntu 8.04 LTS"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by tobeno on 2008-06-15
I am completely new to Linux, as I installed Ubuntu 8.04 last Saturday on my computer. The installation worked without any problems, except that I don't have any sound on my system.

I have tried to find a solution in several different forums, and have tried the following measures:

1. I have checked that the internal sound card on the motherboard is disabled, to make sure that not two sound cards are active.

2. I have made sure that the alsa-utils package is installed.

3. Typing the command [FONT="Courier New"]**asoundconf list**[/FONT] in a console returns nothing. I understand I should be able to find here which parameter I should be using combined with the command [FONT="Courier New"]**asoundconf set-default-card**[/FONT]

I have a Creative Labs SB X-Fi audio card (this is recognised by my system typing [FONT="Courier New"]**lspci -v | grep -i audio**[/FONT] in the console), and I can't find a Linux driver for it at the manufacturer's website. So is my problem that this card isn't supported? If so, isn't there any other drivers available that can be used in stead?

I have become very enthusiastic about Ubuntu, and I am sure there must be a solution to this problem. Any suggestions that may help solving this matter will be warmly appreciated.

tobeno

---

### Post by impert on 2008-06-15
This thread solves most sound problems

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

(edit)
I think this is what you need to do:

> (3) Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

---

### Post by tobeno on 2008-06-15
Seems that my problem is that my sound card is unsupported. Anyway, thanks for providing this link, it's a great help to know what's missing.

Now I only have to wait for a driver to become available. :(

---

### Post by kansasnoob on 2008-06-15
Impert did a really great job, but I'd like to stress one thing:

Medibuntu keeps adding sound card support.

I'd always try installing the Medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

NOTE: remember the gpg key!

Then go to synaptic and add "alsa-firmware" and "alsa-firmware-loaders".

Of course don't use the quotation marks when you search synaptic.

I'd say my success with that is about 75%. Super easy and definitely worth a try!

---

### Post by tobeno on 2008-06-15
Thanks for letting me know about the Medibuntu repository.

I followed the steps on their website to install it, then I rebooted my system, but unfortunately it did not work out.

[FONT="Courier New"]**asoundconf list**[/FONT] still doesn't return anything. But it was surely worth the try.

---

### Post by kansasnoob on 2008-06-15
What sound card are you using?

---

### Post by kansasnoob on 2008-06-15
Sorry, head up butt syndrome!

---

### Post by kansasnoob on 2008-06-15
This does not look very good:

[http://search.yahoo.com/search;_ylt=A0geu9H2oFVI87YAOq1XNyoA?p=Creative+Labs+SB+X-Fi+ubuntu&y=Search&fr=moz2&ei=UTF-8](http://search.yahoo.com/search;_ylt=A0geu9H2oFVI87YAOq1XNyoA?p=Creative+Labs+SB+X-Fi+ubuntu&y=Search&fr=moz2&ei=UTF-8)

But not hopeless.

---

### Post by kansasnoob on 2008-06-15
This is a definite maybe:

[http://opensource.creative.com/soundcard.html#X-FI](http://opensource.creative.com/soundcard.html#X-FI)

---

### Post by tobeno on 2008-06-23
Thank you for your suggestions.

I must admit I got a bit nervous when I read that I had to recompile the kernel in order to make the beta driver working. So instead of risking to mess up completely, the solution I went for was to remove the soundcard and activate the internal one on the motherboard. The loudspeakers on my system isn't much to speak of anyway. That went like a dream, the system had a driver for this one, and now I've got sound on my system. :)

---

### Post by pablolie on 2008-06-23
strange as it may sound, i was having sound issues until i discovered that the built-in driver only supported the audio jacks on the *back* of my standard system, not the ones in the front. silly, but true. the motherboard connections seemed alright. i never verified if installing regular windows drove all jacks, because simly using the ones in the back worked for me.

which prompts the utterly silly -but in my humble experience- necessary question... did you try all the audio jacks in your system?

---

### Post by tobeno on 2008-06-25
> which prompts the utterly silly -but in my humble experience- necessary question... did you try all the audio jacks in your system?

No, I didn't try that, and I take your point - it's a good practice to rule out the very basic possibilities first. I left them untouched since they had worked under my former Windows XP installation. But all media playing software gave an error message, telling there were a missing data stream. I am not a computer expert, but I assumed this had to be caused by a poorly configured soundcard. After some googling I was able to determine the card model, and after that I found that there was only a beta-driver available, and found that I had not sufficient experience to follow its installation procedure with confidence. 

Having learned there also was an internal soundcard on the motherboard, I decided to see if this one was supported. And to my great pleasure, it worked perfectly from the moment I turned on my computer.

Now I have been using exclusively Ubuntu for a week, and I can't describe how impressed I am by it. I have been a Windows user since the 3.11 version, and MS-DOS years before that. Already now I am certain I will not return to that platform ever again.

---

