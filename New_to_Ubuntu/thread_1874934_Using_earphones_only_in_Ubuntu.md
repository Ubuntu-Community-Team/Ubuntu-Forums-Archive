---
title: "Using earphones only in Ubuntu"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by adrianvz on 2011-11-04
Hi,
When I plug my earphones into my laptop they work but the laptops speakers doesn't stop playing. How do I set it up so that it only plays through my earphones. I recently upgraded to Ubuntu 11.10 before I was able to get it to work by changing the sound settings, but not since I've upgraded.

---

### Post by MrLeek on 2011-11-04
Just recently upgraded to 11.10 myself but it works just fine for me:

Go System Settings -> Sound -> Output. Change the output device to your headset (I'm assuming it's displayed?) and it should work. Tested it using random youtube video's.

Other thought I've had is that you can set Ventrillo to play game music via the speakers, but hear people talking through the headset (ideal for when I was leading raids in WoW). Maybe an application is set to play sound though the speakers regardless?

---

### Post by adrianvz on 2011-11-04
Nope my earphones aren't displayed in sound settings but they work its just that I don't want to play with my laptops speakers. I do understand what you are saying though with Ubuntu 11.04 I just changed the settings to my headset, but can't now. Also I've never changed any other settings for games etc.

---

### Post by laithbsoul on 2011-11-04
I don't ever use headphones so I may be of no help but you could try opening the terminal and using the command ```
alsamixer
``` then turning on "Headphone Jack Sense"

---

### Post by MrLeek on 2011-11-04
Maybe try and get Ubuntu to "see" the headset again? 

I'm having issues with my USB headset at the moment - it works quite happily if I connect it via an USB point on the front of the system. But if I connect it to the back it refuses to work. My theory now is to switch off, plug the headset in at the back then switch back on - working on the assumption that the USB connection get's picked up.

Real basic theory as I'm still quite new to Ubuntu :)

---

### Post by adrianvz on 2011-11-04
My laptop does sense the headphone jack it just plays through both the earphones and laptop and I don't have the option to select the default device, but at least with alsamixer  I can turn down the laptops sound and the earphones up so it helps but doesn't solve the problem completely. I've also shutdown more than once and I've moved the earphones to both jacks no luck there as well. But I guess I could live with alsamixer if there is no other solution.:smile:

---

