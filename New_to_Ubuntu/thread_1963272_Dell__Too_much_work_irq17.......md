---
title: "Dell:  Too much work irq17......"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-22
I tried booting 11.10 on my wife's Dell desktop from USB flash and the boot froze with too much work for irq 17.

Is it too much work to correct his error?

---

### Post by Hadaka on 2012-04-22
Did you stop ALL applicstions running in the current OS? and did you do an F-12
boot selection and tell it to boot from USB? Its looks as though the IRQ is being
used by some other process still running.

---

### Post by Boyntonstu on 2012-04-22
> **Hadaka said:**
> Did you stop ALL applicstions running in the current OS? and did you do an F-12
boot selection and tell it to boot from USB? Its looks as though the IRQ is being
used by some other process still running.

I found this on the Web:

I have been using kubuntu 8.04 since 2008 and upgrading fairly often.  About a 
month ago I tried to upgrade and the machine thrashed around a while then 
started sending the message "serial8250: too much work for irq17" then 
said "changing to low-graphics mode".  It became useless.  dmesg was full of
"serial8250: too much work for irq17"

Since support for 8.04 will end soon, I decided to install 10.04.  The install was slow and resulted in lots of "serial8250: too much work for irq17".  I got the same from installing 9.10 and 10.10.  I even tried ubuntu 10.04.

I reinstalled 8.04 and it seems to be allright, even after an apt-get update and upgrade.  

A google on "too much work for irq17" found several others with the same problem, mostly with Dell 2400 series computers (like mine).  But no solutions.

Support for 8.04 runs out soon and I sure don't want to have to leave kubuntu.

Sure would appreciate some help on this.

------------------

And:

Hello, all.
> 
> I have been using kubuntu 8-04 for four years and it is running out of
> support.  For over a year I have been trying to install a later
> version, most recently, 10-4-3.  When I use the 'Try without
> installing" feature within a few minutes I get a screen full
> of  "serial I8250 too much work for irq17" and it locks up.
> 
> When I install, I see that same "too much work for IRQ17" but have> gotten it installed a few times.  But it won't run reliably, locking up with a black, blank screen within hours of startup.
> 
> The computer is a Dell 2400 series 2.4GHz desktop about six years old.
> 
> 8-04 runs 24/7 for months on end with minimal problems.  I have
> installed (or tried to install) newer versions in all three disks in the box.
> 
> Does this symptom indicate a hardware problem?  What is IRQ17?  Is > there something special about Dell computers that makes them reject Kubuntu?
> 
> Any help gladly accepted.

---------------------------------

My wife's PC?  Dell 2400!

---

### Post by Hadaka on 2012-04-22
in terminal type   dmesg | grep -i irq  it should point to what is
using this interupt level.

---

### Post by Hadaka on 2012-04-22
better still try command    dmesg | grep "IRQ 17"

you wont have to wade through all the data.

my dell ..inspiron b130 shows.

[    0.537149] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.319618] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  
Which is associated with the wireless broadcom card.

are you attempting to load via a wireless connection??

---

### Post by Boyntonstu on 2012-04-22
> **Hadaka said:**
> better still try command    dmesg | grep "IRQ 17"

you wont have to wade through all the data.

my dell ..inspiron b130 shows.

[    0.537149] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.319618] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  
Which is associated with the wireless broadcom card.

are you attempting to load via a wireless connection??

The Dell does not boot into Ubuntu to allow Terminal.

Is there a command in XP to view the interrupts?

---

### Post by Hadaka on 2012-04-22
I did a search on the Dell 2400 specs. Looks like it comes standard 
with 256 or 512 ram. If it turns out your PC does have a wireless broadcom
card and that is what you are using. Do a hard wire connect to see if you get
the same "works to hard" error for IRQ18.  If the error is IRQ18 then its most
likely a simple matter of upgrading the ram...max 2gig on the 2400. The ethernet
card and wireless card just receive incomming data and pass it down the highway
to ram and the processor. Your processor is is fine..i suspect its a ram issue. More
testing and beating with a larger hammer will determine the fault cause.  Hope this
helps.

---

### Post by Hadaka on 2012-04-22
Sorry I flushed XP and dont recall how to view IRQ...interupt levels in xp
If you click "system" control pannel  if i recall..it should at least show you 
the amount of ram you have..But as i stated above please connect to hardwire
to see if the error still happens and the IRQ number changes. I would guess
that dell uses like interupts in most of their machines...just my guess..and if
it does show the "working to hard" with a different IRQ number...(18) most likey, 
and control panel-system..shows under 512 ram..then that is probably the reason
you are having an issue.

---

### Post by Hadaka on 2012-04-22
[http://www.helpwithpcs.com/upgrading/change-irq-settings.htm](http://www.helpwithpcs.com/upgrading/change-irq-settings.htm)


This will show you the IRQ list for XP

---

### Post by Boyntonstu on 2012-04-22
> **Hadaka said:**
> I did a search on the Dell 2400 specs. Looks like it comes standard 
with 256 or 512 ram. If it turns out your PC does have a wireless broadcom
card and that is what you are using. Do a hard wire connect to see if you get
the same "works to hard" error for IRQ18.  If the error is IRQ18 then its most
likely a simple matter of upgrading the ram...max 2gig on the 2400. The ethernet
card and wireless card just receive incomming data and pass it down the highway
to ram and the processor. Your processor is is fine..i suspect its a ram issue. More
testing and beating with a larger hammer will determine the fault cause.  Hope this
helps.

O.K.  The P4 2.8 GHZ PC has 2 GB of Ram

It is hard wired to the internet.

PCI INTERRUPT 17 is shared amongst 3 devices

1> Broadcom 440x 10/100 Integrated Conroller
2> Intel 537 EP V9X DF PCI modem
3> Soundmax Integrated Digital Audio

The change interrupt setting is grayed out to automatic.

What is the Intel 537 EP V9X DF PCI modem used for?
Could it be disabled?

Do we need a larger hammer?

Thanks for all your help.

stU

---

### Post by Hadaka on 2012-04-22
No bigger hammer needed, looks like the one we are using is getting there.
The PCI modem is an Intel fax modem. as in dial a connection..pretty much 
useless these days. so yanking it out might be a good thing. you can identify
it by the smaller external jack on the back of the pc...the jack is smaller than
the one you use for internet connecting. and while you are at it..i would first
power down the pc...remove the fax modem card..and reseat the broadcom
card to clear its limited brain cells. There is no reason 11.10 should not run
smoothly on your 2400. I have 2 old dell laptops both with 11.10 and as an
experiment got it to fly with just 512 ram..slow..but everything functioned.
I am going to guess that by default ubuntu 11.10 uses IRQ17 for your broadcom
card and with other cards using that IRQ there is a conflict. so..by removing the
pci fax modem card and reseating the broadcom card..crossing your fingers it
should spring to life. also..I dont know what you know...so excuse me if i am 
giving too simplistic instructions.

---

### Post by Hadaka on 2012-04-22
also..as an after thought..and i hope its not to late...back up EVERYTHING
on the windows xp part...then go to control panel..add/remove hardware and remove the 
pci fax modem from software before removing the physical card.

---

### Post by Hadaka on 2012-04-22
or..per [http://www.helpwithpcs.com/upgrading/change-irq-settings.htm](http://www.helpwithpcs.com/upgrading/change-irq-settings.htm)

You may be just able to simply move cards to different slots and change the IRQ

---

### Post by Boyntonstu on 2012-04-22
> **Hadaka said:**
> or..per [http://www.helpwithpcs.com/upgrading/change-irq-settings.htm](http://www.helpwithpcs.com/upgrading/change-irq-settings.htm)

You may be just able to simply move cards to different slots and change the IRQ

ok

After many up-down under the desk exercise routines, I can report:

I pulled the card and I got 2 white * and OK
and a yellow* with the message:

PulseAudio configured for per-user sessions

saned disabled; edit /etc/default/saned

and a blinking _

where it stalls.

I reinserted the card and add/remove programs would not do anything.

I looked at the IRQ's and there were now only the two PCI 17's;

Broadcom 40x 10/100
Soundmax Integrated Digital Audio.

Even with Intel FAX board in!

I tried to install new hardware, and the FAX card was not recognized?


If this works out it will have been fun.

However, I am doubtful that my flash installed 11.10 will work on my wife's PC.


Do we need a sledge hammer, or should I run head first into a brick wall?

---

### Post by Hadaka on 2012-04-22
Well at least you are down to 2 IRQ17's instead of 3. Try shifting the broadcom card
to a different slot on the motherboard...see if you can get it down to 1 IRQ17
then attempt to load the ubuntu..if that doesnt work...then its time to get brave
and assign non conflicting IRQ's with the help of carefully reading the instructions
on "HOW TO" from the link i sent you. You arent going to let a stupid machine beat
you are you?

---

### Post by Boyntonstu on 2012-04-22
> **Hadaka said:**
> Well at least you are down to 2 IRQ17's instead of 3. Try shifting the broadcom card
to a different slot on the motherboard...see if you can get it down to 1 IRQ17
then attempt to load the ubuntu..if that doesnt work...then its time to get brave
and assign non conflicting IRQ's with the help of carefully reading the instructions
on "HOW TO" from the link i sent you. You arent going to let a stupid machine beat
you are you?

Great!  Thanks for the encouragement.

I changed the slot and the Intel Fax is now 18.

I do not get the "too much work" error now.

Do you know what "saned" is?

Perhaps it means 'insaned'?

---

### Post by Hadaka on 2012-04-22
Not a clue..but we will find out. Does the machine boot to windows xp ok now..im guessing yes..and more importantly can you now load 11.10?
while you are trying to load..i will research in saned

---

### Post by Boyntonstu on 2012-04-22
> **Hadaka said:**
> Not a clue..but we will find out. Does the machine boot to windows xp ok now..im guessing yes..and more importantly can you now load 11.10?
while you are trying to load..i will research in saned

Thanks,

XP is running.

I deleted the Intel Fax program.

The board is still in, but I do not believe that it is an issue with no IRQ errors.

11.10 not booting.

It freezes at:


PulseAudio configured for per-user sessions

saned disabled; edit /etc/default/saned

and a blinking _

I will PM.  OOPS!  PM not working.  

You can contact me here:  [http://www.youtube.com/watch?v=-fKyZ9v_65o](http://www.youtube.com/watch?v=-fKyZ9v_65o)

Do you Skype?

stU

---

### Post by Hadaka on 2012-04-22
this error message -> saned disabled; edit /etc/default/saned

Is comeing from ubuntu..its not an XP error message. Do you get this message 
when you attempt to load 11.10 via USB?  also..the reason you went seeing
your fax card on add/remove hardware..or programs..is because it was still there
you simply changed slots and IQR # (18) by changing slots..you didnt have to 
delete the software. I did a search on "saned disabled" and it looks a bit above
my paygrade,so i welcome anyone with experience with this error to jump in.
If not..then further research and more hammering will be required.

---

### Post by JKyleOKC on 2012-04-22
I don't know why the message, but "saned" is a daemon for the scanner interface, probably a dependency for the "simple scanner" package. If scanner use isn't planned, I think the message can safely be ignored.

---

### Post by Boyntonstu on 2012-04-23
> **JKyleOKC said:**
> I don't know why the message, but "saned" is a daemon for the scanner interface, probably a dependency for the "simple scanner" package. If scanner use isn't planned, I think the message can safely be ignored.

I would ignore the message, but the boot hung there.

---

### Post by Hadaka on 2012-04-23
Stu...You are attempting to load Kubuntu...correct?...NOT UBUNTU 11.10

---

