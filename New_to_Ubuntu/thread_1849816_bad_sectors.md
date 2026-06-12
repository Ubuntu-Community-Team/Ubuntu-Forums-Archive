---
title: "bad sectors"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by CMorgan2k10 on 2011-09-25
Sorry if this is in the wrong category, but i am a beginner to Ubuntu, any way the story is my Windows 7 was working perfectly but then some how it was corrupted, i did a lot of CHKDSK scans but they said there was no bad sectors or file system errors, but i've installed Ubuntu now and it says i have 26 bad sectors, so please help if you know any thing about this :(

---

### Post by Paqman on 2011-09-25
26 bad sectors isn't good, but it isn't quite crisis territory, unless they happen to be in really crucial parts of the disk (it sounds like some of them might ave been critical to your Windows install). In Ubuntu, take a look in Disk Utility in the SMART data and see how many sectors are also sitting under "pending reallocation" or "offline uncorrectable". If there's more sectors in those, or your "reallocated" sectors count goes up, you're in big trouble.

Either way, your disk is gasping and may be about to die completely. You need to back up all your data right now. You can back up your data from Windows using Ubuntu. Open up the file browser and look for an entry in the menu on the left that says XXGB Volume (or however many GB it is). This is your Windows partition, and you can copy any files you want to back up onto some kind of external storage (USB hard drive, DVDs, USB stick, etc)

BTW: using a more descriptive title than "Please help!" will help people to give you the right advice. Something like "Please help, I have bad sectors!" would be fine.

---

### Post by MG&amp;TL on 2011-09-25
How old is your computer? If it's new, it probably shouldn't be doing that.

+1 for backing up data.

---

### Post by CMorgan2k10 on 2011-09-25
[SIZE=2]Thanks for the quick reply, I was really hopping it wouldn&#8217;t come to replacing my HDD, last time it happened it costed £80 to repair, is their any chance that the test was wrong i used the disk utility on Ubuntu, in windows 7 the chkdsk came up with no errors, im going to be reinstalling 7 soon, i replaced 7 with Ubuntu when it was corrupted, but Ubuntu said it had errors weeks ago i didn't have any problems till recently until 7 messed up.

P.S is there anyway I could fix these sectors, my car just got damaged and that going to cost money to fix.
[/SIZE]

---

### Post by MG&amp;TL on 2011-09-25
Nope. Backup your data, see how long it lasts. Mine caused a kernel panic (general bad thing in linux), but I then took it out then replaced it, and it's been going fine (fingers crossed!) for two months now.

---

### Post by CMorgan2k10 on 2011-09-25
> **MG&TL said:**
> How old is your computer? If it's new, it probably shouldn't be doing that.

+1 for backing up data.

Its like a year old it messed up before and I replaced the HDD, and its been a couple of months since I and i don't remember dropping it or anything.

---

### Post by CMorgan2k10 on 2011-09-25
> **Paqman said:**
> 26 bad sectors isn't good, but it isn't quite crisis territory, unless they happen to be in really crucial parts of the disk (it sounds like some of them might ave been critical to your Windows install). In Ubuntu, take a look in Disk Utility in the SMART data and see how many sectors are also sitting under "pending reallocation" or "offline uncorrectable". If there's more sectors in those, or your "reallocated" sectors count goes up, you're in big trouble.

Either way, your disk is gasping and may be about to die completely. You need to back up all your data right now. You can back up your data from Windows using Ubuntu. Open up the file browser and look for an entry in the menu on the left that says XXGB Volume (or however many GB it is). This is your Windows partition, and you can copy any files you want to back up onto some kind of external storage (USB hard drive, DVDs, USB stick, etc)

BTW: using a more descriptive title than "Please help!" will help people to give you the right advice. Something like "Please help, I have bad sectors!" would be fine.

[SIZE=2]Thanks for the quick reply, I was really hopping it  wouldn’t come to replacing my HDD, last time it happened it costed £80  to repair, is their any chance that the test was wrong i used the disk  utility on Ubuntu, in windows 7 the chkdsk came up with no errors, im  going to be reinstalling 7 soon, i replaced 7 with Ubuntu when it was  corrupted, but Ubuntu said it had errors weeks ago i didn't have any  problems till recently until 7 messed up.

P.S is there anyway I could fix these sectors, my car just got damaged and that going to cost money to fix.[/SIZE]

---

### Post by CMorgan2k10 on 2011-09-25
[SIZE=2]Thanks for all you're help guys :) but last time i had bad sectors found by Ubuntu I did a bootable [/SIZE]HDD scanner recommended by samsung (producer of my HDD) and they give me the all clear saying nothing was wrong, and nothing happened so i think im going to do that again, but like i said thanks for the help anyways.

---

### Post by Paqman on 2011-09-25
If the machine is newish the drive will be under warranty. It should cost you nothing to send it back to the manufacturer for a replacement. SMART data doesn't lie, did you check the SMART stuff in Disk Utility that I mentioned? You want to look at:
[LIST=1]
[*]Reallocated sector count
[*]Pending reallocation
[*]Offline uncorrectable
[/LIST]
Or if you like, just post up a screenshot of everything for us and we'll take a look at it for you.

---

### Post by madjr on 2011-09-25
£80 ? wow what a rip off...

you can get hard drives for a lot less and just install them yourself.

in fact is the easiest part.

---

### Post by kmsalex on 2011-09-25
Are you pron to doing things that foster the growth of bad sectors... like holding the power button to turn it off... they say not to do that for a reson you know [-X

---

### Post by CMorgan2k10 on 2011-09-25
> **madjr said:**
> £80 ? wow what a rip off...

you can get hard drives for a lot less and just install them yourself.

in fact is the easiest part.

Well im 13 years old, im pretty good at computers but replacing a HDD is pretty advanced stuff.

---

### Post by CMorgan2k10 on 2011-09-25
> **Paqman said:**
> If the machine is newish the drive will be under warranty. It should cost you nothing to send it back to the manufacturer for a replacement. SMART data doesn't lie, did you check the SMART stuff in Disk Utility that I mentioned? You want to look at:
[LIST=1]
[*]Reallocated sector count
[*]Pending reallocation
[*]Offline uncorrectable
[/LIST]
Or if you like, just post up a screenshot of everything for us and we'll take a look at it for you.

But you know could you tell me about the difference, when i saw that ubuntu had errors a couple of weeks ago, the SMART check said bad sectors, i ran a bootable HDD scanner recommended by samsung and it came up clean, and so did chkdsk, i'll post a snap shot, but im not going to be completely sure until i run that HDD scanner again. Sorry about asking you to check, im pretty good with windows XP,Vista and 7, but not with Ubuntu :/
P.s I'll run that bootable HDD scanner tomorrow and tell you the results, tell me if thats the right stuff if not i'll take some more, and some times i hold the power button down :/
[ATTACH]202937[/ATTACH]

[ATTACH]202938[/ATTACH]

---

### Post by mörgæs on 2011-09-25
> **Paqman said:**
> 
Using a more descriptive title than "Please help!" will help people to give you the right advice. Something like "Please help, I have bad sectors!" would be fine.

Done. I don't like the 'please help'-wording, though. It could be added to every post.

---

### Post by MG&amp;TL on 2011-09-25
> **CMorgan2k10 said:**
> Well im 13 years old, im pretty good at computers but replacing a HDD is pretty advanced stuff.

..not really.

1. Shut down pc. Take side/top/edge/case/panel off..
2. Take out power lead out of the back. Ground yourself before touching anything. (touch something metal, or use an anti-static wrist-strap.
3. Remove old HDD.
4. Replace with new one.
5. Install OS.
6. Reboot.

Although I must admit I'm really pleased I'm into software, not hardware. Cheaper and more comfortable. :)
The only difficult bit is making sure the jumpers are set right.
I'm 15, btw. Hail fellow young computer nerds.

---

### Post by CMorgan2k10 on 2011-09-25
[SIZE=2]I think I’ve only lost 2 gigs in HDD space, is their any way to stop them spreading?[/SIZE]

---

### Post by CMorgan2k10 on 2011-09-25
> **MG&TL said:**
> ..not really.

1. Shut down pc. Take side/top/edge/case/panel off..
2. Take out power lead out of the back. Ground yourself before touching anything. (touch something metal, or use an anti-static wrist-strap.
3. Remove old HDD.
4. Replace with new one.
5. Install OS.
6. Reboot.

Although I must admit I'm really pleased I'm into software, not hardware. Cheaper and more comfortable. :)
The only difficult bit is making sure the jumpers are set right.
I'm 15, btw. Hail fellow young computer nerds.

Im pretty sure its harder than that, and do you think my laptop would last 3 weeks, thats how long it would take to save up, £10 a weeks you see :L my mam can't pay because some things happened to our car and thats more important, so it would take me 3-4 weeks to safe up and if any thing does happened there is the house computer but thats slow, if i buy a HDD i suppose my uncle could do it for me, he makes PC's and stuff

---

### Post by CMorgan2k10 on 2011-09-25
[SIZE=2]Incase you need to know my HDD is a samsung 320gb, i don't know about the specific details i can find out if their really important. Ubuntu says its got 318gb of space and 2x2gb partions for something else, i thought Bad sectors take up gb's so woulden't I lost some HDD space because of them? [/SIZE]

---

### Post by MG&amp;TL on 2011-09-25
I've done it myself.

See here:

[http://pcsupport.about.com/od/upgrades/f/replace-hard-drive.htm]("http://pcsupport.about.com/od/upgrades/f/replace-hard-drive.htm")

If you don't believe me. :)

But hey, I appreciate your concerns. I don't like hardware either.

...well...my pc's still going strong, two months later. But it could go now, or later. Nobody knows.

---

### Post by MG&amp;TL on 2011-09-25
If the cable's wide and flat, with separate ribbons, follow the PATA guide.

If it's in a laptop, follow the laptop guide.

If it's not either, and it's got some sort of thicker cable, use the SATA one.

Just make sure you get the cable the right way around.

---

### Post by CMorgan2k10 on 2011-09-25
> **MG&TL said:**
> If the cable's wide and flat, with separate ribbons, follow the PATA guide.

If it's in a laptop, follow the laptop guide.

If it's not either, and it's got some sort of thicker cable, use the SATA one.

Just make sure you get the cable the right way around.

Tbh i think it will be safer if a buy a HDD then let my uncle sought it out, thanks for the concern, nay help about how i could stop it or how the chkdsk didn't pick it up would help though.

---

### Post by MG&amp;TL on 2011-09-25
Avoid excessive disk activity. Don't resize the partitions, don't reinstall anything, make a huge backup or download to the HDD. As to why windows didn't pick it up, IDK.

See if you're missing an updated version of whatever windows uses to check the SMART data.

---

### Post by Paqman on 2011-09-25
> **CMorgan2k10 said:**
> [SIZE=2]I think I’ve only lost 2 gigs in HDD space, is their any way to stop them spreading?[/SIZE]

Nope. The fact that they "pending reallocation" isn't good. Do you know how many are in the "reallocated sectors" count? Pending reallocation means that the drive has noticed that they're bad, but it hasn't been able to shut them down safely.

Once a drive notices a sector is bad it tries to save the data to a new, safe location and lock the bad one out of use forever (it becomes "reallocated"). If it can't do that it might be because it no longer has enough spare sectors to put the data into and the old bad ones end up sitting in the "pending" pile forever. That's not good for the integrity of your data. I'm pretty sure the drive will still avoid writing to those sectors, but the issue is that whatever caused the bad sectors in the first place (eg: dodgy heads) could still be wrecking more sectors every time you use the disk. That means you're likely to continue to get more bad sectors and more corrupted data.

You won't have to pay a penny if the drive or machine is under warranty. Back up your data and send it off as a warranty replacement pronto.

---

### Post by madjr on 2011-09-25
> **CMorgan2k10 said:**
> Well im 13 years old, im pretty good at computers but replacing a HDD is pretty advanced stuff.

i replaced my first hd at 12 :D

(note am 29 right now and it was harder back then, there was no "auto detection", you had to do a bunch of stuff manually)

now is just connecting 2 cables..

laptops are even easier

sadly todays youth (generally speaking) seems to be afraid of learning (even if things are easier than before), they want everything done for them..

and about the price, i can get 2 drives for 80

dont be afraid trying it yourself first is not going to get messed up trust me.

---

### Post by CMorgan2k10 on 2011-09-25
> **Paqman said:**
> Nope. The fact that they "pending reallocation" isn't good. Do you know how many are in the "reallocated sectors" count? Pending reallocation means that the drive has noticed that they're bad, but it hasn't been able to shut them down safely.

Once a drive notices a sector is bad it tries to save the data to a new, safe location and lock the bad one out of use forever (it becomes "reallocated"). If it can't do that it might be because it no longer has enough spare sectors to put the data into and the old bad ones end up sitting in the "pending" pile forever. That's not good for the integrity of your data. I'm pretty sure the drive will still avoid writing to those sectors, but the issue is that whatever caused the bad sectors in the first place (eg: dodgy heads) could still be wrecking more sectors every time you use the disk. That means you're likely to continue to get more bad sectors and more corrupted data.

You won't have to pay a penny if the drive or machine is under warranty. Back up your data and send it off as a warranty replacement pronto.

We got it from a guy who owns his own PC repair shop, so i don't know anything about warranty's with the drive, and how do i find out about the relocation details, if you could tell me where to find it i could send you a snapshot tomorrow.

---

### Post by MG&amp;TL on 2011-09-25
My first HDD was at 13. But I found and replaced in its case the BIOS battery when I was twelve. :p

Damn thing keeps falling out.

---

### Post by Rasa1111 on 2011-09-25
It is not difficult at all to install a new HDD.

also..
you are 13 years old, and need to 'fix your car"?

Really?

---

### Post by MG&amp;TL on 2011-09-25
> **Rasa1111 said:**
> It is not difficult at all to install a new HDD.

also..
you are 13 years old, and need to 'fix your car"?

Really?

It happens in some places. I live in a farming area of the UK, and most of the farmers' sons/daughters go out and help pick the crops, and most of them know exactly how an engine works. We have a sort of deal going. I do their computers, and anything that involves academia, they do my physical stuff.

---

### Post by Paqman on 2011-09-26
> **CMorgan2k10 said:**
> We got it from a guy who owns his own PC repair shop, so i don't know anything about warranty's with the drive

The drive's manufacturer (eg: Seagate, Hitachi, etc) will handle a warranty claim for it.

> 
and how do i find out about the relocation details, if you could tell me where to find it i could send you a snapshot tomorrow.

It's all in the SMART data that Disk Utility can give you.

---

### Post by MartyBuntu on 2011-09-26
> **Rasa1111 said:**
> 
you are 13 years old, and need to 'fix your car"?

Really?


Post #17

His mom's car.

---

### Post by CMorgan2k10 on 2011-09-26
> **Rasa1111 said:**
> It is not difficult at all to install a new HDD.

also..
you are 13 years old, and need to 'fix your car"?

Really?

NO! Its just my Mam is giving up her job because she's not happy with her boss, and she has to pay to fix the car, soooo.....quit job.........money to fix car :/ And last time it was expensive to fix the drive, and thanks to the people who used common sense and pointed out that i said my Mam's car, and does any body know a place where i could get cheap HDD's, im not being lazy when i say i don't wanna replace my drive, its just i think i might damage it beyond the point of repair :( And then my Mam would have to pay for a new laptop :(

And thanks guys i didn't think this many people would try and help me :D

---

### Post by CMorgan2k10 on 2011-09-26
[SIZE=2]So guys i wont be responding for about 2 hours im doing a massive bootable HDD scan, fingers crossed :/


[/SIZE]

---

### Post by lightwarrior on 2011-09-26
Well, I'm too late, but anyway:
Bad sectors on a new HDD is really bad news.
Before even trying anything more, as soon as you can do a backup, the better.
Usually these errors come from debris on platters (which will continue damaging the platters) or bad HDD head positioning control system (chip, sensor, actuator).
None of those failed components may get fixed by software.

---

### Post by CMorgan2k10 on 2011-09-26
[SIZE=2]I've done a HDD scan, and sadly it says that its found errors, and now its gone up to 28, is there any thing i could do, software of hardware wise, maybe open it up and see if i could put it back into place, please im desperate.

P.S i don't know how to explain this to my mum, what should i say, due to the current events she isn't going to be happy :( 
[/SIZE]

---

### Post by CMorgan2k10 on 2011-09-26
> **CMorgan2k10 said:**
> [SIZE=2]I've done a HDD scan, and sadly it says that its found errors, and now its gone up to 28, is there any thing i could do, software of hardware wise, maybe open it up and see if i could put it back into place, please im desperate.

P.S i don't know how to explain this to my mum, what should i say, due to the current events she isn't going to be happy :( 
[/SIZE]

[SIZE=3]Any way I thought Ubuntu came with a program to try and fix bad sectors?
Or I've heard a lot about a program called bad blocks what about that will it work, i know its mostly down to Hardware but i could give it a try?
[/SIZE]

---

### Post by CMorgan2k10 on 2011-09-26
[SIZE=4]And extra info, the HDD tool recommended that i format the HDD, then re-run the test, could this bring about any results?
 [/SIZE]

---

### Post by wildmanne39 on 2011-09-26
Hi, when you reformat it will wipe out everything on the driver, but it will block those bad sectors so they are not used anymore but it will not fix the bad sectors, and you will have to keep a check on the bad sectors after you reinstall because they might continue to grow.

28 is not a large amount, you can backup your data daily an keep and eye on them since money is an issue.
Thank you

---

### Post by MartyBuntu on 2011-09-26
> **CMorgan2k10 said:**
> [SIZE=3]Any way I thought Ubuntu came with a program to try and fix bad sectors?
[/SIZE]


Walk away from this and don't invest any more time in "magical" software solutions. The drive is done.

If you can't afford a new hard drive, perhaps you can run Puppy Linux off a disk so you can save sessions until you can buy a new drive.

---

### Post by CMorgan2k10 on 2011-09-26
[SIZE=3]So my best bet would be to format, ok i guess i'll try that if it does not work after that i guess i'll have to buy a cheapy HDD and ask my Uncle to put it in for me, im going to try HDD REgenerator first many people said it has helped them before, may aswell because i don't have any other idea's.[/SIZE]

---

### Post by CMorgan2k10 on 2011-09-26
[SIZE=4]Also i have a external HDD, i know windows cant do it but could i run Ubuntu off that?[/SIZE]

---

### Post by CMorgan2k10 on 2011-09-26
[SIZE=3]Has anybody had any luck with bad blocks and the numerous other tool I've been talking about?
I don't know if im allowd to post other links but if im not just say and i'll stop but look at what these guys said [http://forums.techarena.in/hardware-peripherals/1092536.htm](http://forums.techarena.in/hardware-peripherals/1092536.htm) ? Problem is Wine does not seem to be working >:(
[/SIZE]

---

### Post by wildmanne39 on 2011-09-26
Hi, first please use normal fonts.

If your computer has an option in the bios to boot from usb device then yes you can use an external hard drive to run ubuntu.

I personally have not tried any programs to repair bad sectors, I think you run a higher risk of crashing the disk trying a repair program on it then it is worth considering it only has 28 bad sectors in my opinion.
Thank you

---

### Post by CMorgan2k10 on 2011-09-26
> **wildmanne39 said:**
> Hi, first please use normal fonts.

If your computer has an option in the bios to boot from usb device then yes you can use an external hard drive to run ubuntu.

I personally have not tried any programs to repair bad sectors, I think you run a higher risk of crashing the disk trying a repair program on it then it is worth considering it only has 28 bad sectors in my opinion.
Thank you

But i did have 26 so its obviously spread, some one told me that the only way to stop them spreading is to not do major activities, im guessing the think that did for me was the scan, but im 13 games today are like 2-5gb.

---

### Post by CMorgan2k10 on 2011-09-26
And has anybody in this chat got a small number of bad sectors atm, i if you have does it bother you as long as it does not spread?

---

### Post by CMorgan2k10 on 2011-09-26
> **Paqman said:**
> Nope. The fact that they "pending reallocation" isn't good. Do you know how many are in the "reallocated sectors" count? Pending reallocation means that the drive has noticed that they're bad, but it hasn't been able to shut them down safely.

Once a drive notices a sector is bad it tries to save the data to a new, safe location and lock the bad one out of use forever (it becomes "reallocated"). If it can't do that it might be because it no longer has enough spare sectors to put the data into and the old bad ones end up sitting in the "pending" pile forever. That's not good for the integrity of your data. I'm pretty sure the drive will still avoid writing to those sectors, but the issue is that whatever caused the bad sectors in the first place (eg: dodgy heads) could still be wrecking more sectors every time you use the disk. That means you're likely to continue to get more bad sectors and more corrupted data.

You won't have to pay a penny if the drive or machine is under warranty. Back up your data and send it off as a warranty replacement pronto.

And hears a Snapshot of the reallocation thing.TBH i don't really get any thing on it, it says the assessment is good, thats a relief right?  

[ATTACH]203005[/ATTACH]

---

### Post by MG&amp;TL on 2011-09-26
Yes, you can run Ubuntu off an external hard drive, providing it's a USB one and your computer's BIOS supports booting from USB.

As for how to tell your parent, I suggest sticking it out until it DIES totally, then pressing the power button in a useless way, saying something like, "I think the hard drive's gone". Then, presumably, money will be less of an issue, as your HDD should last for a while longer yet. Therefore she will probably call in your uncle. Problem solved. Although I don't know your family or circumstances, so I can't really comment. 

Good luck.

---

### Post by CMorgan2k10 on 2011-09-26
[SIZE=1]Kinda knew that the end was not that near yet, but i was wondering did you take a look at the snap shot, some guy said it was really important, sorry for asking you but i don't know what it means.[/SIZE]

---

### Post by westie457 on 2011-09-26
Hi have only just found this thread.
Looking at your screen shot the few bad sectors would not normally be a concern however taking the warning at the top about the has failed IS A CONCERN.
In the last week I have had to replace a HDD that had some bad sectors and they were all very close to the MBR area of the drive. Because of that no operating system could be installed even after a low-level format. The only cure was a new hard drive for around £30 + Postage from a local company.


PM me for the link to their web site.

---

### Post by CMorgan2k10 on 2011-09-26
> **MG&TL said:**
> Yes, you can run Ubuntu off an external hard drive, providing it's a USB one and your computer's BIOS supports booting from USB.

As for how to tell your parent, I suggest sticking it out until it DIES totally, then pressing the power button in a useless way, saying something like, "I think the hard drive's gone". Then, presumably, money will be less of an issue, as your HDD should last for a while longer yet. Therefore she will probably call in your uncle. Problem solved. Although I don't know your family or circumstances, so I can't really comment. 

Good luck.

And LOL, you opened up a new idea to me, im just going to wait until it dies completely but i forget she docent have to pay £80 then just £30 then my uncle can put it in free of charge, but the guy said it might be ok as long as the "relocation" stuff is OK.

---

### Post by MG&amp;TL on 2011-09-26
The disk self-test failed the 'read' section of the test. Can't tell you any more than that.

---

### Post by CMorgan2k10 on 2011-09-26
What is the most durable make of HDD's, at the moment i have Samsung so please don't say the samsung one's are. :p

---

### Post by MG&amp;TL on 2011-09-26
I've never heard of samsung HD's-so presumably they're not.

I had a Seagate drive for AGES (+8 years) , hasn't failed yet.

---

### Post by CMorgan2k10 on 2011-09-26
> **MG&TL said:**
> I've never heard of samsung HD's-so presumably they're not.

I had a Seagate drive for AGES (+8 years) , hasn't failed yet.

How expensive are they i was hoping for a 320gb-500gb, i suppose i could drop to a 250gb

---

### Post by MG&amp;TL on 2011-09-26
First hit in Google, NOT spamming:

[http://www.amazon.co.uk/gp/search/ref=sr_nr_i_0?rh=k%3Aide+320gb%2Ci%3Acomputers&keywords=ide+320gb&ie=UTF8&qid=1317064738#/ref=sr_nr_p_4_2?rh=k%3Aide+320gb%2Cn%3A340831031%2Cp_4%3ASeagate&bbn=340831031&keywords=ide+320gb&ie=UTF8&qid=1317064748&rnid=419150031](http://www.amazon.co.uk/gp/search/ref=sr_nr_i_0?rh=k%3Aide+320gb%2Ci%3Acomputers&keywords=ide+320gb&ie=UTF8&qid=1317064738#/ref=sr_nr_p_4_2?rh=k%3Aide+320gb%2Cn%3A340831031%2Cp_4%3ASeagate&bbn=340831031&keywords=ide+320gb&ie=UTF8&qid=1317064748&rnid=419150031)

---

### Post by CMorgan2k10 on 2011-09-26
Ok sorry didn't relies £50 thats decent i guess, could you have a look at that relocating this please, some guy said if it was ok it could mean that my HDD would be ok!
And im happy i found a seagate 1TB HDD for £50. :)

---

### Post by madjr on 2011-09-26
> **CMorgan2k10 said:**
> NO! Its just my Mam is giving up her job because she's not happy with her boss, and she has to pay to fix the car, soooo.....quit job.........money to fix car :/ And last time it was expensive to fix the drive, and thanks to the people who used common sense and pointed out that i said my Mam's car, and does any body know a place where i could get cheap HDD's, **im not being lazy when i say i don't wanna replace my drive, its just i think i might damage it beyond the point of repair** :( And then my Mam would have to pay for a new laptop :(

And thanks guys i didn't think this many people would try and help me :D

like i said on my [earlier post]("http://ubuntuforums.org/showpost.php?p=11285076&postcount=24"), there is no way you can damage it (unless you throw the thing across the room).

Also if you let your uncle replace it, you should be present so you see how is done.

Am sure you will be saying **"*wow, how could i've been afraid of doing this, it was so easy*"**

:)

---

### Post by CMorgan2k10 on 2011-09-26
> **madjr said:**
> like i said on my [earlier post]("http://ubuntuforums.org/showpost.php?p=11285076&postcount=24"), there is no way you can damage it.

Also if you let your uncle replace it, you should be present so you see how is done.

Am sure you will be saying **"*wow, how could i've been afraid of doing this, it was so easy*"**

:)

Ok i will try and be there when he does it, thanks for all the help you given me, still annoyed tbh i don't see how it could be me, my friend chucks his laptop about, and it most overheat at lease 5 times a day and his his working okay :(

---

### Post by MG&amp;TL on 2011-09-26
'relocate this' what do you want doing again?

---

### Post by CMorgan2k10 on 2011-09-26
> **Paqman said:**
> Nope. The fact that they "pending reallocation" isn't good. Do you know how many are in the "reallocated sectors" count? Pending reallocation means that the drive has noticed that they're bad, but it hasn't been able to shut them down safely.

Once a drive notices a sector is bad it tries to save the data to a new, safe location and lock the bad one out of use forever (it becomes "reallocated"). If it can't do that it might be because it no longer has enough spare sectors to put the data into and the old bad ones end up sitting in the "pending" pile forever. That's not good for the integrity of your data. I'm pretty sure the drive will still avoid writing to those sectors, but the issue is that whatever caused the bad sectors in the first place (eg: dodgy heads) could still be wrecking more sectors every time you use the disk. That means you're likely to continue to get more bad sectors and more corrupted data.

You won't have to pay a penny if the drive or machine is under warranty. Back up your data and send it off as a warranty replacement pronto.

This is the relocation thing im about this guy said it would be pretty importiant

---

### Post by CMorgan2k10 on 2011-09-26
And their is a snap shot on page 5.

---

### Post by Paqman on 2011-09-26
> **CMorgan2k10 said:**
> And hears a Snapshot of the reallocation thing.TBH i don't really get any thing on it, it says the assessment is good, thats a relief right?  

[ATTACH]203005[/ATTACH]

That's actually not good. For some reason your drive is not remapping the bad sectors properly. And the number is going up, also not good, that means you've got a fault in your drive which is actively killing sectors. Have you backed up the data yet?

As for what to say, easy: "Mum, this hard drive is dying, but don't worry it's only a year old, so it'll be replaced free of charge by the manufacturer". The only thing you have to do is fit it, which is really not hard. If you know anybody even remotely tech savvy they could do it for you in five minutes.

> **CMorgan2k10 said:**
> What is the most durable make of HDD's, at the moment i have Samsung so please don't say the samsung one's are. :p

They're all about the same. Price, speed and size are more important factors than brand.

---

### Post by madjr on 2011-09-26
> **CMorgan2k10 said:**
> Ok i will try and be there when he does it, thanks for all the help you given me, still annoyed tbh i don't see how it could be me, my friend chucks his laptop about, and it most overheat at lease 5 times a day and his his working okay :(

well laptops usually overheat more than usual because they have lots of dust buildup in the fan area.

When your uncle is placing the new drive also tell him if he can take the fan out to undust it.

this should be done **at least twice a year** (or depending how dusty your environment is). Again it should be easy enough that you wont need his help (or bother him :p) once you see how is done.

---

### Post by oldos2er on 2011-09-26
> **CMorgan2k10 said:**
> What is the most durable make of HDD's, at the moment i have Samsung so please don't say the samsung one's are. :p

Sooner or later they all fail. Find something with a decent warranty (actually I think most warranties are similar, but something to be aware of.)

---

### Post by Kixtosh on 2011-09-26
There are two things that I would like to share with you (and my conclusion, from reading your thread so far):

[COLOR=DarkRed]**1. Using Your Machine With a Bad Drive.**[/COLOR]

If you want to keep using your machine with a bad drive, I would _refrain  from storing any of your files on the hard drive_. Install an _external  drive instead_, such as a USB stick, SD card, or even an external hard drive that  is not solid state (flash memory, with no moving parts).

In this way, your failing hard drive will only contain the operating system, not any of your data. 

[COLOR=DarkRed]**Puppy Linux**[/COLOR] was mentioned earlier, and this would limit use of your hard drive even further, since _it runs only from RAM and boots from a CD_ or other external device. In fact, _you don't even need a hard drive_ to be installed at all to use Puppy normally. In this case, you should again use some form of external memory to store the small files that Puppy uses for your compacted saved personal files that you will create during usage, as well as small system files (even if Puppy is running from a CD), to speed up future boot times. Puppy Linux seems like a fantastic option for you to wait out your hard drive failure to me, with only minimal loss of your laptop's usability. Installing it on a flash drive would be best, for convenience and speed especially, and you could even add a swap partition of twice the size of your installed RAM to make Puppy run even better, if the drive is big enough for that.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

Personally, I think that this is what you should do, without delay.

**[COLOR=DarkRed]2. Data Rescue[/COLOR]**

Are there any files on this failing drive that you need, or want to retrieve?

I have rescued data from a failing hard drive using SpinRite software. It's mentioned in that link you posted to a TechArena thread (posted again below), but it's not free.

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)
[http://forums.techarena.in/hardware-peripherals/1092536.htm](http://forums.techarena.in/hardware-peripherals/1092536.htm)

My hard drive was badly damaged (after being dropped while turned on and in the process of shutting down). Windows would not boot (BSOD messages every time). When I tried to copy important files to an external drive using data recovery software, I encountered "cyclic redundancy check" errors, meaning the files could not be copied successfully. This is explained here, if you are interested:

[http://en.wikipedia.org/wiki/Cyclic_redundancy_check](http://en.wikipedia.org/wiki/Cyclic_redundancy_check)

After running SpinRite for days, twice over, I was able to boot Windows normally and rescue 99% of my data.

There are also Linux tools for hard drive management that are available free of charge, but I am not familiar with them or what, exactly, is the extent of what they can do to "repair" a failing drive.

This information is only to suggest that, in the event of lost data that is important to you, there are some tools that may help you recover the lost data, but you haven't mentioned any concerns about that in your thread so far. This may not, therefore, be an issue for you at all.

**[COLOR=DarkRed]3. Conclusion.[/COLOR]**

In any event, I would probably never fully "trust" any failing hard drive, whether it was recovered or not, so in my opinion, you should replace the drive as soon as you are able.

I would certainly use Puppy on some form of USB flash device. Even 1GB will probably be enough, depending on how much swap space you need (this depends on your RAM, but you can consider 2GB as a maximum).

Puppy can do just about everything you are probably likely to need and it's probably the easiest OS there is to try and use. You don't even have to install it if you don't want to: simply use a CD instead. 


[LIST]
[*] Puppy CD in during boot = Puppy starts and loads in RAM; the hard drive is not active.
[*] Puppy CD out during boot = Windows, or other HDD O.S. starts instead, and the hard drive is used normally.
[/LIST]

---

### Post by Denver Dave on 2011-09-26
I don't claim to know as much as the people giving the replies you have received, but I have a somewhat different opinion.

If your disk is continuing to develop lots of new bad sectors, then I agree you have an ongoing problem and you probably need a new disk.  At the very least make extra efforts to back your disk up.

However, I believe that some bad sectors are normal and can be flagged as such by the windows chkdsk utility if the right options are selected.  After backing your stuff up, might be worth a try.  I recommend a scandisk (does the chkdsk) and defrag once a month for light to moderate users.   

Not sure about an ubuntu equivalent, but might be fscl (sounds like something that might goof your drive up, so backup):
[http://superuser.com/questions/15916/is-there-a-chkdsk-equivalent-available-for-ubuntu](http://superuser.com/questions/15916/is-there-a-chkdsk-equivalent-available-for-ubuntu)

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

Please report back.

---

### Post by Kixtosh on 2011-09-26
> **Denver Dave said:**
> ...  I recommend a scandisk (does the chkdsk) and defrag once a month for light to moderate users.   

Not sure about an ubuntu equivalent, but might be fscl (sounds like something that might goof your drive up, so backup):
[http://superuser.com/questions/15916/is-there-a-chkdsk-equivalent-available-for-ubuntu](http://superuser.com/questions/15916/is-there-a-chkdsk-equivalent-available-for-ubuntu)

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

Please report back.
Denver Dave, using the disk defragmentation tool will also be likely to accelerate any deterioration dramatically, in my opinion (because it examines and manipulates the drive over an extended period of time). I personally would _never_ use it on a failing drive, so that's something to bear in mind.

---

### Post by 1991sudarshan on 2011-09-26
Check this thread 

[http://ubuntuforums.org/showthread.php?t=1741291](http://ubuntuforums.org/showthread.php?t=1741291)

I think you must replace your hard disk! I too faced the same problem !

---

### Post by CMorgan2k10 on 2011-09-27
[SIZE=2]Ok guys i have a external HDD, but i don't really store anything important o[/SIZE]n my main HDD except games that i can redownload , all my course work i back up on a USB and external HDD, just a quick not my IT teacher (Who's teaching my GCSE IT) recommended defragmenting and formating my HDD, and the count only went up after i did a major HDD scan.

---

### Post by CMorgan2k10 on 2011-09-27
And btw my laptop runs normally, no weird noises or clicking sounds.

---

### Post by CMorgan2k10 on 2011-09-27
> **1991sudarshan said:**
> Check this thread 

[http://ubuntuforums.org/showthread.php?t=1741291](http://ubuntuforums.org/showthread.php?t=1741291)

I think you must replace your hard disk! I too faced the same problem !

Yes but i have 28 not 4000+

---

### Post by westie457 on 2011-09-27
> **CMorgan2k10 said:**
> Yes but i have 28 not 4000+

I recently (in the last 2 weeks) had to replace a hard drive. That had 37 bad sectors and Windows Blue screening and/or failing to start. The Windows repair disk did not work. When I ran SMART Diagnostics for the drive it showed 37 sectors as bad however some of these were in the MBR area of the drive. Nothing could be installed. After trying twice I hooked the drive via USB to my laptop and checked for badblocks. This time the count went to 130. A big difference. Then I installed the drive in the laptop and used a Live CD. This time the check for badblocks never did finish because I stopped after 4 hours. Anyway I then used Disc Utility to check the drive. I did not bother running SMART tools as there was already a warning about bad sectors and the drive failing. This count was 2024.

See how quickly the amount went up from some to a lot.

Now the advice is **replace the drive** as soon as possible.

If it is still in warranty it will be free.
If out of warranty a replacement 250GB drive can be bought for around £30.

---

### Post by CMorgan2k10 on 2011-09-27
My IT teachers who's obviously pretty good a PC's recommended defrag and if  needed format, would this help in any way?

And i plan to wait it out until my HDD fully dies.

Been a day or two and its still on 28, and just downloaded a 800mb file, i might try and do the Ubuntu version of chkdsk

---

### Post by madjr on 2011-09-27
> **CMorgan2k10 said:**
> My IT teachers who's obviously pretty good a PC's recommended defrag and if  needed format, would this help in any way?

And i plan to wait it out until my HDD fully dies.

Been a day or two and its still on 28, and just downloaded a 800mb file, i might try and do the Ubuntu version of chkdsk

good at pc's with just windows or good at everything? ;)

---

### Post by CMorgan2k10 on 2011-09-27
> **madjr said:**
> good at pc's with just windows or good at everything? ;)

Don't know but some people said formatting has a small change of helping, if my HDD goes soon my external HDD is actually a laptop HDD in a external case, so i could take the risk and put that in there

---

### Post by Paqman on 2011-09-27
> **CMorgan2k10 said:**
> My IT teachers who's obviously pretty good a PC's recommended defrag and if  needed format, would this help in any way?


Nope. Defrags and formatting only affect the filesystem. Your problem is the actual disk itself, not the software sitting on it. It's a bit like asking if trying a different channel would help when someone's put a brick through your TV.

---

### Post by madjr on 2011-09-27
> **Paqman said:**
> Nope. Defrags and formatting only affect the filesystem. Your problem is the actual disk itself, not the software sitting on it. It's a bit like asking if trying a different channel would help when someone's put a brick through your TV.

exactly.

And IT teachers usually dont know as much as they want you to think they do. Specially in high school one thinks they'rt hacker Gods! :P

---

### Post by Kixtosh on 2011-09-27
Well, I'm going to repeat myself a little bit here, but anyway ... Defragmenting the disk and then formating it for a fresh installation is probably excellent advice if you are running Windows, and want to keep things running smoothly, but I still think it is a VERY BAD IDEA on a failing drive. If your drive has problems, they may indeed multiply tenfold (or worse) just by doing this. On the other hand, if you really _want_ to know whether or not your drive is failing, or otherwise, then I would go right ahead and do exactly that! You already have an external drive for your data, so the risk is minimal, and the results might be useful in determining what you need to do next.

Otherwise, remember that Puppy Linux will run _without your hard drive at all_. Maybe you could install it on your external hard drive, but it will be faster (especially for boot times) if you install it on a USB solid state flash drive of some kind, such as a USB stick.

---

### Post by Rasa1111 on 2011-09-27
but puppy linux sucks soo bad! lol :P

---

### Post by LinuxFan999 on 2011-09-27
> **Rasa1111 said:**
> but puppy linux sucks soo bad! lol :P
I agree, puppy Linux does suck. I once tried it on an old laptop, and it failed to install, while other distributions installed successfully. Puppy Linux also only has the root user, which is not good.

---

### Post by CMorgan2k10 on 2011-09-27
Um guys i just formatted my HDD and the smart data says that my disk is healthy, instead of this drive has some bad sectors, i only did a short test but i'll do a long one tomorrow, trying not to get my hopes up but maybe my HDD had spare sectors and when i formatted it they kicked in.

---

### Post by CMorgan2k10 on 2011-09-27
> **Kixtosh said:**
> Well, I'm going to repeat myself a little bit here, but anyway ... Defragmenting the disk and then formating it for a fresh installation is probably excellent advice if you are running Windows, and want to keep things running smoothly, but I still think it is a VERY BAD IDEA on a failing drive. If your drive has problems, they may indeed multiply tenfold (or worse) just by doing this. On the other hand, if you really _want_ to know whether or not your drive is failing, or otherwise, then I would go right ahead and do exactly that! You already have an external drive for your data, so the risk is minimal, and the results might be useful in determining what you need to do next.

Otherwise, remember that Puppy Linux will run _without your hard drive at all_. Maybe you could install it on your external hard drive, but it will be faster (especially for boot times) if you install it on a USB solid state flash drive of some kind, such as a USB stick.

Thanks for the detailed answer but i just reinstalled Ubuntu and went on disk utility and done a short scan and it came up clean :) when i first installed ubuntu it said straight away i had bad sectors i didn't even need to scan :(

---

### Post by CMorgan2k10 on 2011-09-27
Could Ubuntu just have made a mistake? Or did formatting my HDD fix it with spare sectors or something which I've been hearing about?

---

### Post by MG&amp;TL on 2011-09-27
Hey, don't knock the puppy. <yap, yap> Great for file recovery. And systems without a HD. ;) The root user thing doesn't bother me, but the lack of installing does.

---

### Post by CMorgan2k10 on 2011-09-28
Hey guys, i formated my HDD and so far i havent found any signs of bad sectors, I've done a long SMART scan on the disk utility, and the bad sector count just says N/A, so is that good or bad, any way the status says this disk is healthy, should i re do that bootable HDD scan to make sure

---

### Post by madjr on 2011-09-28
> **CMorgan2k10 said:**
> Hey guys, i formated my HDD and so far i havent found any signs of bad sectors, I've done a long SMART scan on the disk utility, and the bad sector count just says N/A, so is that good or bad, any way the status says this disk is healthy, should i re do that bootable HDD scan to make sure

not sure, if you already installed ubuntu on it, then use it for a few weeks see if everything goes well and you dont notice anything strange with it.

But always have backups of your important stuff (ubuntu-one and/or separate partition or usb drives).

Good luck and hope things go well for you! (if not let us know) :)

ps. i think this has been a good learning experience and you'll be almost on par with your IT teacher soon ! :p

---

### Post by CMorgan2k10 on 2011-09-28
> **madjr said:**
> not sure, if you already installed ubuntu on it, then use it for a few weeks see if everything goes well and you dont notice anything strange with it.

But always have backups of your important stuff (ubuntu-one and/or separate partition or usb drives).

Good luck and hope things go well for you! (if not let us know) :)

ps. i think this has been a good learning experience and you'll be almost on par with your IT teacher soon ! :p

Thanks you for all your help, and every body else, I'll do what you said hopefully it will run ok, the disk utility said the disk was healthy

---

### Post by mörgæs on 2011-09-29
That was quite a struggle. I am happy to finally say:

If the problem is solved, please mark the thread so using 'thread tools'.

---

### Post by Kixtosh on 2011-09-29
> **Rasa1111 said:**
> but puppy linux sucks soo bad! lol :P

> **LinuxFan999 said:**
> I agree, puppy Linux does suck. I once tried it on an old laptop, and it failed to install, while other distributions installed successfully. Puppy Linux also only has the root user, which is not good.
I don't think so, but it's a bit off topic now for this thread.

Just for the benefit of anyone reading this, for older laptops, use Wary Puppy, not normal Puppy. On one recent installation, Wary Puppy was able to detect and use an obscure wireless card that it took me quite some time and effort to get working with Ubuntu.

Puppy is also much more friendly now that there is access to the Ubuntu software packages. It is frequently in the top ten of distrowatch, and is nearly always the most popular of all the lightweight distributions.

It's main advantages, as I see them, are:

[LIST=1]
[*]You can run it completely independently of the hard drive (which is why it is even relevant here). In fact, you don't even need a hard drive installed to use it.
[*]There's no GRUB to install or manage, no dual booting to figure out (making it a delight for those that aren't ready to mess with Windows yet, or can't shrink their Windows partition).
[*]Firefox and Chromium are both available as browsers and so is LibreOffice, as well as almost any other popular bit of software you might want.
[*]Despite the comment, and a few grumblings here or there, about being "root" in Puppy, it is generally recognized as completely secure, from what I have read and/or experienced.
[*]It will run much faster from a CD than any Live CD of most other Linux distros, so it's certainly the easiest way (and one of only a few) to get a _fully functional_ operating system running from only a CD or USB flash memory, and a small amount of RAM.
[*]It requires less RAM than most other distributions.
[*]It has a far more active community than most of the other lightweight distributions.
[/LIST]

It's main disadvantages, in my view, are:

[LIST=1]
[*]It's a bit "quirky" in feel, usage and appearance in general.
[*]It's not really intended for hard drive installation, for those that want that, although it can easily be done.
[*]If you have 512MB of RAM or more, I find that any LXDE (lightweight desktop environment) Ubuntu based distribution, or even Ubuntu itself with Gnome (desktop environment) will work just as efficiently as Puppy.
[/LIST]

Good luck to CMorgan2k10 in his new venture!

---

### Post by ex_isp on 2011-10-01
CMorgan2k10,

I have been doing hardware for 25 years.  I believe that you are being lucky.  Count on it.  Once a drive starts to fail, it's on the way.  Period.  You may get a week or two, you may get several months.

Bottom line, don't trust the drive.  I'm happy it's working for you now but it is on the way out.

Example,  Your car is smoking and using oil.  Yes, a bunch of STP wax will help limit that, but your rings are still shot and the engine still needs an overhaul.  I would not take that car on a long trip.  Does that analogy make sense for you?

Best of luck!

Ex

---

