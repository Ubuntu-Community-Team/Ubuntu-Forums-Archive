---
title: "Blundering along..."
date: 2008-10-18
forum: New to Ubuntu
---

### Post by taiken0798 on 2008-10-18
I hope someone can give me some insight. I recently did an automatic software update, 10/14/08, on v8.04 and didn't get to rebooting my system until 10/17/08. After restarting I discovered that my rig would not boot. No screen, no POST, nothing. I tried to use the LiveCD to get back into it but all I got was a blank screen. Has anyone else had any similar problems since the last automatic software update?

---

### Post by eternalnewbee on 2008-10-18
> **taiken0798 said:**
> I hope someone can give me some insight. I recently did an automatic software update, 10/14/08, on v8.04 and didn't get to rebooting my system until 10/17/08. After restarting I discovered that my rig would not boot. No screen, no POST, nothing. I tried to use the LiveCD to get back into it but all I got was a blank screen. Has anyone else had any similar problems since the last automatic software update?

Can you boot your system in safe mode?

---

### Post by eternalnewbee on 2008-10-18
Something similar happened to me (not recently though) and I remember having shut the system down for a minute or two and then everything was working fine again....
Just thinking out loud...
Good luck.

---

### Post by steveneddy on 2008-10-18
The new kernel is giving fits to some folks.

Try waiting for GRUB while booting, hit the [COLOR=Blue]**ESC**[/COLOR] key and select the kernel ending with [COLOR=Blue]**-19**[/COLOR]

Hope that helps.

---

### Post by taiken0798 on 2008-10-18
I appreciate the quick responses. To answer the first question, no I can't boot into safe mode. It appears the machine is not even going through POST. I'll try waiting for GRUB and hit the ESC key. Then choose -19. If that works it'll all be good. I'm hoping the mobo's not fried. Again thanks for the advice. I'll update on the progress :)

---

### Post by steveneddy on 2008-10-18
> **taiken0798 said:**
> To answer the first question, no I can't boot into safe mode. **It appears the machine is not even going through POST**. 

Aw, crap. I really hate it when that happens.

Good luck.

---

### Post by ardvark71 on 2008-10-18
> **taiken0798 said:**
> I appreciate the quick responses. To answer the first question, no I can't boot into safe mode. It appears the machine is not even going through POST. I'll try waiting for GRUB and hit the ESC key. Then choose -19. If that works it'll all be good. I'm hoping the mobo's not fried. Again thanks for the advice. I'll update on the progress :)

Hi...

If your system is not even getting to POST, I highly doubt this has anything to do with Ubuntu. :(

At first glance, you may be correct as far as this being a hardware issue. It could be the motherboard, the power supply unit or memory modules.

Best Regards...

---

### Post by starcannon on 2008-10-18
I would try clearing CMOS, you'll need to get out or download the owners manual for your computers motherboard, find out which jumper is set up for that; then, assuming the magic smoke still resides in the motherboard, you should be able to run the bios setup to get things the way you like them (or just load setup defaults from last tab of most bios). If this doesn't clear up what sounds very much like a hardware issue, then you can go through the trial and error of removing devices from the machine until you either run out of things to remove, or you find the culprate.

Anyway, this is how I would tackle the issue if it were happening to me.

GL and keep us posted if you can.

---

### Post by ardvark71 on 2008-10-18
> **starcannon said:**
> I would try clearing CMOS

Hi...

I didn't think of that one, it might be worth a shot. :)

Best Regards...

---

### Post by BGrigg on 2008-10-18
> **eternalnewbee said:**
> Something similar happened to me (not recently though) and I remember having shut the system down for a minute or two and then everything was working fine again....
Just thinking out loud...
Good luck.

Yeah, same thing happened to me. Power off (and I mean shut off the power supply) and let it stay off for a couple of minutes (you won't die!). Then power back up. So far everything seems to be fine, other than that initial hiccup.

---

### Post by taiken0798 on 2008-10-18
Well...looks like the magic smoke has left the mobo. It was just weird that it tanked when I happened to do an update and reboot. Anyway, you guys have been a great help and on the bright side of things I get to invest in a new mobo :) I've pretty much given up on Windows for the past year. I use Ubuntu full time and love it. Thanks again.

---

### Post by dustint83 on 2008-10-18
all you have to do is take the battery out of your motherboard, the little round lithuim battery

wait about 10 seconds then put it back in place. turn your computer on, that will reset everything in the bios so if somethin was changed it will go back to its default setting and shoudl be able to post

if nothing happens still, you probably overheated something inside and will need to replace the faulty part

---

