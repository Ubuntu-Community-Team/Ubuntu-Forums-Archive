---
title: "Upgraded to 12.04.1 -- sound from one speaker, only"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-08-24
Hi Ubuntu Community:

I upgraded to 12.04.1 this evening....

I'm getting sound from only 1 of my 2 stereo speakers.

How do I fix this?

Thanks!
Old Jimma

---

### Post by deadflowr on 2012-08-25
Go to the top panel and locate the speaker icon, click on it and locate the sound settings menu feature. Open sound settings and, in output, check that the highlighted card is the one you're using (if you have more the one working sound card/device) when card is determined to the right will be the balance and volume controls. Make sure the balance is centered.
If this doesn't help, then more info would probably be needed to really figure this out.

---

### Post by Old Jimma on 2012-08-25
THe highlighted card is the one I'm using and the balance is centered betweeen right and left.

---

### Post by Old Jimma on 2012-08-25
Dead Flower requested more information in response to my request for help... only one of the 2 speakers give sound after upgrading to 12.04.1

#-o

First, I should say that one of the first things I did when 12.04.1 installed was to remove Rhythmbox and Banshee. 

I did not note what else could have been removed, but perhaps important things were removed that caused my problem.

I've attached a screen shot of
[LIST]
[*]Output from alsamixer with the appropriate card selected (CMI8786), and
[*]Sound settings (upper right speaker icon > sound settings).
[/LIST]

Also, I've read and followed recommendations for getting sound to work for Ubunto ([[COLOR="Red"]**https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#**[/COLOR]]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#")

Is it possible that I'm not using alsa?? It is possible that my sound drivers are something else??

Using the recommendations at that link, I was lead to reinstall [COLOR="Red"]**libasound2**[/COLOR] with the command

> sudo apt-get install --reinstall libasound2

Then I rebooted... sound continued to play from only one speaker!

](*,)

Any help you can provide will be greatly appreciated... my computer is used primarily as a music player.

I really don't have any idea how to fix this!

:shock:

Sincerely,
Old old Jimma (post elderly)

---

### Post by phibxr on 2012-08-25
Just as a troubleshooting measure -- did you try connecting a pair of headphones instead?

---

### Post by Old Jimma on 2012-08-25
phibixr:

You are some kind of genius! I tried headphones and both sides worked perfectly!

What does this mean, and how to I get both speakers to work??

Many thanks!
old Old Jimma the Elder

---

### Post by Old Jimma on 2012-08-25
**[COLOR="Red"]Backround:[/COLOR]** Old Jimma installed 12.04 and "discovered" that music did not play through both speakers in his stereo that was connected to his computer. He queried Ubuntu Forums for a solution.

](*,)

**[COLOR="Red"]Methods:[/COLOR]** Philbxr suggested seeing whether music played through both earpiecees of a headphone to see whether it was the computer's problem.... or something else. After a sleepless night and 7 additional hours of anguish, Old Jimma decided to see if a CD player connected to his stereo worked, also.

:-k

**[COLOR="Red"]Results: [/COLOR]**Beautriful stereo music played through both earpieces of a headphone connected the 12.04.1 computer. A CD play connected to the stereo revealed that that same dang speaker wasn't playing. Tightening the screws on the speaker connections resolved the problem... both for the CD play and playing music piped from the 12.04 computer to Old Jimma's stereo.

\\:D/

[COLOR="Red"]**Conclusions:**[/COLOR] It is important to get good sleep. And then, it is even more important to be logical and not jump to conclusions about "sound problems" that 12.04.1 doesn't have. As far as Old Jimma can tell, somebody must have been sneaking into his house and loosening those screws on the back of his speakers. Extra security precautions should be taken. 

:-\"

---

### Post by phibxr on 2012-08-26
Haha, glad to hear that you've been able to figure the issue out. Now enjoy your quality sound. :)

---

