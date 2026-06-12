---
title: "Migration to ubuntu - a second go."
date: 2018-03-01
forum: New to Ubuntu
---

### Post by chaoticbob on 2018-03-01
Hi. I've posted on here before about getting my HP laptop to run ubuntu and had lots of sound advice. I got very near the move from Win10, but wimped out towards the end - I had only the one machine which I need to use daily, and was worried about everything going horribly wrong.

I've now acquired a DELL 780 Optiplex (Intel Core duo) desktop system which I can use for experimentation - it's currently running Win7, but it doesn't matter if I trash the OS or any data on there. 

From the advice I had before I can do the basics (I think!) , ie booting ubuntu off a stick and installing over the previous OS. Assuming that goes OK the next thing will be to get wireless internet connectivity. The machine has no internal wireless, so my first question is - what should I go for? A PCI card, an external USB adaptor or perhaps an ethernet bridge?
 
Any advice would be very welcome, Rob

---

### Post by him610 on 2018-03-02
Hello chaoticbob,

My preference is to have an internal card. The only time I use an external USB adapter is when there is no space for an internal card like on my Raspberry Pi Model B.  The DELL 780 Optiplex came in several sizes and configurations. If you have the smaller size, you may need to get a low-profile card. Other than that, you are probably okay with a full size card. Open it up to see if you have a free slot then check out what is offered on Newegg and Amazon. Don't have any experience with a network bridge so can't comment  on it.

---

### Post by mörgæs on 2018-03-04
> **chaoticbob said:**
> 
From the advice I had before I can do the basics (I think!) , ie booting ubuntu off a stick and installing over the previous OS.

Good. This step should be done with wired internet access. When all updates have been applied and the system is running fine it's time for focusing on wifi.

---

### Post by chaoticbob on 2018-03-12
Thanks guys. I wasted some time poking around in the BIOS trying to persuade the Optiplex to boot from the 16.04 ISO I already had on a USB stick, but it wouldn't play, so I burned a DVD which went fine. 

I took mörgæs' advice and set up wired internet, which just worked.

him610 - it is one of the smaller versions, so I'll need a low-profile card to go wireless - opening it up I see one conventional PCI slot and one PCIe x 16 slot free, but I've yet to track down a card that fits and is advertised as Linux compatible. I'll keep looking.

No doubt there will be further questions - but for the mo I'm a happy bunny to have a stable and fast OS running at last!
Thanks again, Robin

---

### Post by mörgæs on 2018-03-13
> **chaoticbob said:**
> I've yet to track down a card that fits and is advertised as Linux compatible.

A lot of hardware is compatible though not advertised as such, especially if it's some years old.

---

### Post by leunam12 on 2018-03-13
I would use a router with DD-WRT set up in bridge mode, but it is just a personal preference.

---

### Post by wheatpenny2 on 2018-03-14
> **chaoticbob said:**
> I've yet to track down a card that fits and is advertised as Linux compatible. I'll keep looking.




I've been running Ubuntu off and on for several years and have yet to encounter any problems with hardware incompatibility. Everything I've tried it with is Linux compatible even tho most of it is not labelled as such.

---

### Post by mastablasta on 2018-03-15
lucky you. i've found that often stuff would work but not as it should and not have all the features. biggest problem is new hardware, but old is not immune as well.

i've had partial compatibility many times. 
e.g. AMD GPU chip working, just not all functions and not preserving the battery as it should.
sound working sporadically, even though chip had declared full compatibility
NvidiaGPU with declared linux compatibility would boot to blinking cursor on proprietary or stretched VGA resolution with missing functionality on opensoruce driver
a cannon printer with no linux drivers - does not work at all.
TV card - recognised but not working
old VGA cam (maybe Genius brand) not working properly (camera is upside down, picture is worse compared to windows). solved the upside down picture by turning the camera upside down.

...

---

