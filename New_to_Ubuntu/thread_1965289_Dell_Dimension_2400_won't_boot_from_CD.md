---
title: "Dell Dimension 2400 won't boot from CD"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-25
Dell Dimension XP SP-2 P4 2 Gig ram.

Burned 11.10 ISO on it to create Live CD.

Will not boot.  Get the press f1 message.

Take the same CD to other PC, boots fine.

Took another live CD created on other PC and tried Dell boot again, fail.

Took working 11.10 USB and Plop, tried booting Dell, no go.

Any ideas why the Dell 2400 will not boot?

I have spent about 20 hours on this craziness.

---

### Post by Mark Phelps on 2012-04-25
Don't have a Dell, but I've heard that some of them have built-in  "protection" that prevents you booting from other than the hard drive.  You should check your BIOS, specifically the Boot info, to see if there is anything like that.

Also, our forums have a Dell section.  You should check there.

---

### Post by Peter09 on 2012-04-25
Could be a couple of things
 
[LIST=1]
[*]The boot up process is not even looking at your CD - go into the bios and make sure its the first option in the boot sequence (or try F8 or F12) during boot for options.
[*]It may be that your CD reader/writer is on its limits (is it old?)
[/LIST] 
Other than that try using a usb flashdrive as a boot medium (create one using startup disk creator on another PC running the Live CD)

---

### Post by ravinfy on 2012-04-25
I recall reading another post here with a similar problem - The user did everything right but still couldn`t get Ubuntu to start installing from BIOS. 
He finally figured that there were some additional options in BIOS that were not compatible with the Ubuntu installation and had to disable them (He did this the trial and error way)

Read the following link to see if it has some solution to your problem: 
[https://help.ubuntu.com/8.04/installation-guide/i386/pre-install-bios-setup.html]("https://help.ubuntu.com/8.04/installation-guide/i386/pre-install-bios-setup.html")

Also, 
- How about initiating the install after logging into your Windows XP? 

If your problem persists, would you please post more details on what exactly you are seeing after you change your boot sequence to CD ROM and reboot? 

Sorry for being so generic with some solutions provided. Thought we can work thru after I gave you some initial ideas. 

Ravi

---

### Post by Boyntonstu on 2012-04-25
"Took working 11.10 USB and Plop, tried booting Dell, no go.

Any ideas why the Dell 2400 will not boot?"

Bios and f12 allows boot from CD.

Anything else?

Remember that the Dell produced a working Live CD.

---

### Post by Boyntonstu on 2012-04-25
> **ravinfy said:**
> I recall reading another post here with a similar problem - The user did everything right but still couldn`t get Ubuntu to start installing from BIOS. 
He finally figured that there were some additional options in BIOS that were not compatible with the Ubuntu installation and had to disable them (He did this the trial and error way)

Read the following link to see if it has some solution to your problem: 
[https://help.ubuntu.com/8.04/installation-guide/i386/pre-install-bios-setup.html]("https://help.ubuntu.com/8.04/installation-guide/i386/pre-install-bios-setup.html")

Also, 
- How about initiating the install after logging into your Windows XP? 

If your problem persists, would you please post more details on what exactly you are seeing after you change your boot sequence to CD ROM and reboot? 

Sorry for being so generic with some solutions provided. Thought we can work thru after I gave you some initial ideas. 

Ravi

Thanks, I will check the thread.

How about initiating the install after logging into your Windows XP? 

"Dell Dimension XP SP-2 P4 2 Gig ram.

Burned 11.10 ISO on it to create Live CD."

Done that.

what exactly you are seeing after you change your boot sequence to CD ROM and reboot? 

Press f1

---

### Post by ravinfy on 2012-04-25
Umm.. what exactly is happening when you initiate the installation from with in Windows XP? 
The installation reboots your computer and you are stuck at that F1 thing again?? 

It seems more like the other problem I mentioned with disabling some features in BIOS while installing - i`l come back and post a more helpful link if I find one. 
Meanwhile, you could try reading my previous link to see if it has some ideas you could use. 

Ravi

---

### Post by ravinfy on 2012-04-25
Ok! I found what I was looking for: 

See the "Changing the CD's Default Boot Options" section in the following link for various options 
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

There is a mention about special requirements for DELL hardware. That might be all you want: 
> F1, then F7: Kernel parameters for Adaptec, BusLogic and certain Dell hardware.

Please let us know if this does help! 

Ravi

---

### Post by Boyntonstu on 2012-04-25
> **ravinfy said:**
> Ok! I found what I was looking for: 

See the "Changing the CD's Default Boot Options" section in the following link for various options 
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

There is a mention about special requirements for DELL hardware. That might be all you want: 


Please let us know if this does help! 

Ravi

SOLVED!  Edit:   Not yet.

Not by brains, but by trial and error.

I Pressed F2 and changed every BIOS setting and tried to boot the Live CD.

Finally, I turned OFF Diskette.

That's what made the Live CD boot!   

I then tried Plop and a good USB with a working 11.10 and it stalled on boot.

I retried the Live Cd and nor it will not boot again.

The BIOS is the same as it was when it booted the Live CD.

Close, but no cigar.

Thoughts?


--------------------

Finally got the Live CD to boot.

Got it 3/4 into install 11.10 onto USB flash.

Then it gave me a read error on the CD.


Suggested that I record at lower speed.

What a struggle!

The CD burner drive E: has been flawless t this event.

The CD player D: has never failed till this event.

Thoughts?

---

### Post by ravinfy on 2012-04-26
Ah! So near yet so far..! :) 

So, I am understanding that you have overcome the original problem with getting your CD to boot. You are stuck in between installation because it requests you to burn your disk at a slower speed? 

I really dont know a lot about burning speeds or what else you could try to get it to work (especially when you confirmed that the same disk IS working on your friends machine..? ) 

But, i`m thinking, now that you figured you should turn off your diskette to proceed with installation, how about trying the same stuff with your "Bootable USB"? 

If installing by CD is your only option, we might have to wait for some other, more knowledgeable forum member to help you out! Sorry! 

(Sorry you are going thru all this.. everything with Ubuntu has been butter smooth in MY 2 months of use... 
anyways, I see brighter days are just a step away for you :) Hang in there...)

Ravi

---

