---
title: "Noisy fan on Dell 17r 5721 running 12.04"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2013-04-16
Hi Everyone, 
This is driving me crazy. I bought a new Dell 17r a month ago and I am generally pretty happy with it, except that the fan runs full speed all the time and is depressingly noisy. I have searched the internet and followed countless forums for what appears to be a problem with no answer. I have downloaded things to help control the fan, but nothing works. An official Dell download that has something to do with the BIOS wouldn't open in ubuntu. I probably use a fraction of the computer's potential, just writing, listening to music, photos and surfing the web and the CPUs run at a fraction of their power so I am pretty sure it is not in danger of overheating if I could get the damn fan to slow down. Canonical says that the 5721 laptop is certified for ubuntu, but surely this is a serious problem. Any suggestions or do I send it back for a refund.
Thanks in advance,
Dermot

---

### Post by mustafi05 on 2013-04-16
if you have a graphix card , you can download its driver from restricted extra . it solved the problem for me.

---

### Post by Dermot Doyle on 2013-04-16
Hi,
This is going to sound lame, but I know very little about computers. How do I know if I have a graphics card?

---

### Post by mustafi05 on 2013-04-16
there is nothing that sounds lame. just open additional driver programe and it will show you the available drivers . if you find one you needed install it. i do not know  either how to determine that a computer has a  grphics card or not either graphically or from cli command . you may check your computer configurations from site . some other may help you to do it in ubuntu by any inbuilt method.

---

### Post by mustafi05 on 2013-04-16
you can install hardware lister from ubuntu software centre that would list all your hardware. think it may help you.

---

### Post by Dermot Doyle on 2013-04-16
This is what I got from the terminal (I followed some advice from the net)

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 6601

Any suggestions as to what this means and wat to try now?

---

### Post by mustafi05 on 2013-04-16
open 'additional drivers' from dash and install avilable driver for ati device 6601. it may solve your problem.

---

### Post by docJ on 2013-04-16
> **Dermot Doyle said:**
> An official Dell download that has something to do with the BIOS wouldn't open in ubuntu. 

I know very little about Ubuntu (actually less than that), but I know Ubuntu (or any OS for that matter) cannot open the BIOS, because the BIOS loads _before_ the OS.

As soon as you start (mere seconds after hitting your power button), look for a mention that says: Press Del (delete) to enter setup
Then its only a matter of finding where to find fan speed (and/or Quiet) related settings

Please thread carefully inside the BIOS, if you do change something, change only ONE thing then F10 to save and exit, if it does not fix it, go back and put it the way it was before before doing any other change

---

### Post by Dermot Doyle on 2013-04-16
mustafi05, I downloaded the driver and rebooted, but no change
docj, I'll give it a go
Thanks to both

---

### Post by Dermot Doyle on 2013-04-16
docj, I didn't see an opportunity to press 'del' so I got into the BIOS by pressing f12 repeatedly on start up. I didn't see anything in there concerning the fan speed or quiet related settings. Any other suggestions? I have also posted this question on Dell's forum and haven't had a single reply. Doesn't sound good.

---

### Post by docJ on 2013-04-16
A few years back, I (unknowingly) had a computer that had the BIOS quiet feature turned on, & the end result was quite the opposite of quiet, it would go by itself and for no apparent reason from quiet to Space shuttle liftoff, then back to quiet.

If you are not used to going inside your Bios, there are lots of nooks and crevices in there, but I bet if you look everywhere, you will find the speed/quiet feature. A telltale sign you're closing in is when you see rpm numbers (revolution per minute of your fan). If you want to find where's the dang thing a little faster, go to Dell's support website, you should find your specific* bios pdf manual
 
*During boot, it should display the BIOS revision # you're running

---

### Post by Dermot Doyle on 2013-04-18
The latest is I got no luck from Dell's own website forum except for a rather snotty reply suggesting I hadn't looked hard enough and offering three solutions, which I had already seen and none of which worked. Because Dell they wouldn't sell me a laptop preloaded with Ubuntu I loaded it myself. Then, becase windows wouldn't allow me to partition the hard drive to duel boot it with Ubuntu I simply got rid of windows altogether. Now have voided the warranty, at least as far as software support is concerned. The upshot is I still have a fan running constantly at a noisy 5800rpm and no way to slow it down.

docj, I had another look in the BIOS and the only mention of temperatures and fan speeds is under diagnostics.

Any other suggestions? I'd go back to 10.04 which I used on my previous Dell if it would only shut the fan up.
Cheers

---

### Post by QIII on 2013-04-18
Hello!

More than likely, going to an older version will make matters worse.  In any case, do NOT manually decrease the speed of the fan.  You won't get better performance.  What you may get is a trip to the repair shop.

You have hybrid ATI/Intel graphics, for which is the industry has not given good support for Linux.  The same goes for Nvidia/Intel hybrids.

You have a couple of choices:

1.  Start [here]("http://ubuntuforums.org/showthread.php?t=1930450") and read through a very long thread for what has worked for others.

2.  Uninstall any proprietary drivers you may have installed to get back to the open source Radeon driver that is included when you install Ubuntu.  Then use vga_switcheroo as described [here]("https://help.ubuntu.com/community/HybridGraphics").

Best of luck!  This is a thorny problem.


QIII

---

### Post by Dermot Doyle on 2013-04-20
Hi QIII,
Thanks for the reply. I have to say I found the first suggestion daunting when I opened the link, the second one slightly less so. Also the first link needs to update the BIOS for which I would need windows. I have wiped windows from the computer so this is an additional problem. I have managed to achieve some success using the terminal, but I am not really very computerate and have read some stuff with people having hanging problems with switcheroo. Not something I would contemplate with great relish, considering my lack of knowledge. Just one last question, is it ridiculous to consider changing the graphics card (or whatever) to solve the problem rather than going for a software change that seems to have little success? I know as little about hardware as I do about software, but any advice would be welcome (I didn't have this problem with my last Dell inspiron running 10.04, must have had different cards).

---

### Post by Dermot Doyle on 2013-04-23
A quick update. I tried the second option (switcheroo), but got nowhere. In the terminal it just denied me permission from the second command on. Do you think I will just have to junk this computer and get one that doesn't sound like a small jet taking off in my sitting room all the time? If so, which laptops do work properly with Ubuntu? I think I've given up on Dell.

---

### Post by Dermot Doyle on 2013-04-29
Another thought i'd like feedback on, could I use another form of linux to stop my fan running full pelt all the time or will all open source operating systems run into the same problem? Does anyone here know enough about the other systems to offer advice?
Cheers

---

### Post by yxw on 2013-05-14
> **Dermot Doyle said:**
> Another thought i'd like feedback on, could I use another form of linux to stop my fan running full pelt all the time or will all open source operating systems run into the same problem? Does anyone here know enough about the other systems to offer advice?
Cheers

I'm using  [tlp]("http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html#installation") to control fan on my Dell Inspiron 15R 5521 laptop.

---

### Post by Dermot Doyle on 2013-05-19
Hi yxw,
Thanks for the reply, I had pretty much given up hope on this issue. I have downloaded tip with what seemed to be no problems. How does it control your fan speed? Is it supposed to do it automatically or is there a way of getting into it and setting it up to your specifications?

---

### Post by linrunner on 2013-05-19
Hi,

what xyw meant is: TLP is a power management tool that mitigates power consumption of your laptop. TLP does not control the fan directly, but a cooler cpu means less fan noise in most cases.

---

### Post by Dermot Doyle on 2013-05-20
Hi linrunner,
Ok, I understand. In that case I think I have simply come up again to the main problem of there being no way of overriding the BIOS controling of the fan on this machine with Ubuntu, though I appreciate the attempt to help. The fan is as fast and noisy as it ever was. The one thing that annoys me is that being not very computerate I looked up the list of Dell machines certified by canonical and the 17R was one of them. Clearly it shouldn't be on the list since an internet search shows that this is a major problem. I guess I will have to save up and buy something else. Maybe it would be worth loading it with windows and selling it for whatever I could get.

---

### Post by houseworkshy on 2013-05-20
This is just a tip which may be helpful because I read  "i do not know  either how to determine that a computer has a  grphics card or not either graphically or from cli command" . 
There is a program called " sysinfo" for Ubuntu which you can install graphically or in the terminal with "sudo apt-get install sysinfo".  After installing it open it either from the menus or with "sysinfo" entered in the terminal.  You can get your system information from there.  If you click "file" from it's top panel ( or top bar ) it 'will save a text document where ever you choose and you could attach that to posts in order to save typeing.
Another thing you could try which is none techy would be to download some live distros, puppy is small and Knoppix has a lot of drivers bundled with it. Trying one of those would help determine if the problem is hard or software based.  It's not impossible that the fans need to be running because the thing thing is dusty inside and is getting hot despite not being pushed to capacity.
To could find out how hot/cool things are in the chip by installing "lm-sensors".  To do so "sudo apt-get install lm-sensors" and, it's not a graphic utility so "sensors" entered in the terminal will output the temperature of your chips in the terminal.  Then search for your chip name ( which sysinfo will have told you ) and see if they are in their safe working temperature range.  The lm-sensors program is available for many systems, anything Debian based like Ubuntu,  and is so small it can be installed to RAM in a live session.  So you could try it in live sessions with various distros too.  If things are consistantly warm a physical clean would be the first thing to do.  If not consitant then looking for software solution isn't a waste of time,  which is worth knowing before banging your head against the problem.

---

### Post by Dermot Doyle on 2013-05-22
Hi houseworkshy,
The computer is new and has run on full fan since I bought it so I don't think cleaning it wil help. No software I have downloaded has been able to sense or control the fan. If I run the diagnostics from the BIOS I can hear the fan run perfectly at different speeds and consequently Dell simply deny there is a problem. Even when the CPUs are showing around 4% usage the fan is on full belt and cold air is pumping out of the vent. Thanks for the thoughts, but I am resigned to it being an unanswerable problem untl Dell and/or the hardware developers of the inbuilt graphics cards let opensource designers into their little secrets. 
Cheers

---

### Post by cmcanulty on 2013-05-22
if it was new a month ago try a return or warranty fix maybe the fan or it's controller is defective

---

### Post by Dermot Doyle on 2013-05-23
Hi cmcanulty,
I spoke to Dell support when trying to fix the problem and they said I had invalidated the warranty by wiping windows and installing Ubuntu. I would have kept windows, but windows 8 is designed to make it impossible (at least to me) to partition the disk to add another OS. I don't know if that should cover a hardware issue, but from what I have read on the internet it is a software problem and in their eyes I have buggered up the software myself.

---

### Post by cmcanulty on 2013-05-23
If you want the hassle I think that provision would be an illegal violation of the fair use requirement. Especially since Dell actually sells some Ubuntu installed computers

---

### Post by Dermot Doyle on 2013-05-24
In case anyone else has the same problem I have finally managed to slow the fan down using i8kctl. I will have to monitor the CPU temp (also with i8kctl), but the computer is now blissfully quiet. It was only my lack of understanding that stopped me from getting i8kctl to work. Thanks to all for the attempts to help.

---

