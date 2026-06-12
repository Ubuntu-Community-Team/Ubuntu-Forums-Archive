---
title: "UEFI, Ubuntu and our rights to install whatever we want stomped?"
date: 2012-06-20
forum: Recurring Discussions
---

### Post by ndefontenay on 2012-06-20
Hi guys,

I was reading this article:

[http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270](http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270)

and I'm a bit concerned:

Is UEFI designed to:
1) Make hardware more secure and less hackable?
or
2) Try to lock us in with just one vendor dictating its will. Regardless if it's Ubuntu or Windows, I hate the idea entirely!

---

### Post by wilee-nilee on 2012-06-20
This is really old news and has been covered on the forum numerous times.

---

### Post by CharlesA on 2012-06-20
> **wilee-nilee said:**
> This is really old news and has been covered on the forum numerous times.
Yep.

[http://ubuntuforums.org/showthread.php?t=1992798](http://ubuntuforums.org/showthread.php?t=1992798)
[http://ubuntuforums.org/showthread.php?t=1999332](http://ubuntuforums.org/showthread.php?t=1999332)
[http://ubuntuforums.org/showthread.php?t=1994931](http://ubuntuforums.org/showthread.php?t=1994931)

---

### Post by jockyburns on 2012-06-20
I think you've answered your own question, really. And the true answer is going to be Number 2. Lock users down to one OS Vendor.

---

### Post by PC_load_letter on 2012-06-20
Sorry to post without reading previous threads but in my understanding this security feature can be changed from the BIOS (err...I guess it's the UEFI) setup during boot, no? 

So, if I buy a new PC, all I need to do to install Ubuntu is to turn off this feature, unless of course if Canonical pays M$ to allow the installation of Ubuntu under this feature, right? I thought Fedora already did that.

---

### Post by Elfy on 2012-06-20
*Thread moved to **Recurring Discussions**.*

---

### Post by Dragonbite on 2012-06-20
I see a lot of complaints about Fedora ponying up the keys and lamenting the issue, but has anybody heard what Canoncial/Ubuntu is going to do about it?

If they decide to go the same route as Fedora, it won't be difficult ($99 one-time fee?).

Ubuntu has slowly been getting less "friendly" to older hardware and now new hardware is being made to be "secure" with UEFI !  That leaves  the happy middle to play with for a while.

Companies like System76 and ZaReason will have this probably turned off and we'll have to wait and see what OEMs end up doing.  Dell has been selling Ubuntu systems in India just recently so they could come out as "champions of choice".

All this nuisance to the OEMs just to get a dumb little sticker they are "certified" by Microsoft. Yeesh!

Oh yeah, and if they can get away with it, Microsoft wants to make ARM vendors require the user canNOT turn off UEFI.

This may actually not be so bad either, considering Microsoft is going to be selling their own tablets. OEMs may care a little less about complying with not providing the option, since they are in direct competition in some ways.

---

### Post by jockyburns on 2012-06-20
> **PC_load_letter said:**
> Sorry to post without reading previous threads but in my understanding this security feature can be changed from the BIOS (err...I guess it's the UEFI) setup during boot, no? 



Apparently UEFI will be enabled by default, but can be turned off by the user. The user would then have to enter the BIOS and load another OS. 
But,,,,, if you buy a machine with ARM architecture, you won't be able to turn off the UEFI whatsoever, so those ARM machines unfortunately, are locked to the OS pre installed on them.

---

### Post by Dr. C on 2012-06-20
On x86/AMD64 You would be able to customize secure boot to use another OS with imported keys or diable secure boot altogether. Windows 8 will behave as Windows 7 does today and not prevent the installation of "non approved" applications. 

On ARM on the other hand not only would the end owner not be able to load another OS or disable secure boot they will also be perevented from loading an application or content that was not previously approved by Microsoft. So for example one would not be able to use LibreOffice and would have to pay for and use Microsoft Office instead. Same thing for example with VLC vs Windows Media Player, Firefox vs Internet Explorer etc.

---

### Post by MadmanRB on 2012-06-20
> **Dr. C said:**
> On x86/AMD64 You would be able to customize secure boot to use another OS with imported keys or diable secure boot altogether. Windows 8 will behave as Windows 7 does today and not prevent the installation of "non approved" applications. 

On ARM on the other hand not only would the end owner not be able to load another OS or disable secure boot they will also be perevented from loading an application or content that was not previously approved by Microsoft. So for example one would not be able to use LibreOffice and would have to pay for and use Microsoft Office instead. Same thing for example with VLC vs Windows Media Player, Firefox vs Internet Explorer etc.
This is why secure boot is bull and those who support it are Microsoft plants

---

### Post by jwbrase on 2012-06-21
> **ndefontenay said:**
> Hi guys,

I was reading this article:

[http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270](http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270)

and I'm a bit concerned:

Is UEFI designed to:
1) Make hardware more secure and less hackable?
or
2) Try to lock us in with just one vendor dictating its will. Regardless if it's Ubuntu or Windows, I hate the idea entirely!

It's *designed* to do 1). However, the UEFI specification doesn't say who gets final authority over what will boot and what won't.

If the owner of the device gets that final authority (as Canonical is requiring, and as Microsoft is requiring on x86, but not on ARM), then UEFI actually manages to accomplish 1); The settings the machine comes with as to what will boot and what won't are just defaults and the owner can change them at any time, so even if those settings only allow booting one OS, the user can change them to add whatever OS he wants, and even disallow booting the original OS. 

If the owner does *not* get that final authority (as Microsoft is requiring on ARM), then UEFI accomplishes 2) and half of 1). It is more difficult for third parties to hack the system, and it is more difficult for the owner to gain their rightful degree of control over the system (which the vendor would see as 'hacking'), but the vendor has complete control over the system (which is as bad as hacking, in that they can do things with the system without the owner's permission and are preventing the owner from doing the same things). And, of course, the owner is locked in to whatever OS's the vendor wants to allow.

In summary, for an Ubuntu UEFI system, or a Win8/x86 system, ***you*** get to decide how locked down it is and what will and won't boot.

For a Win8/ARM system, ***Microsoft*** gets to decide how locked down the system is and what will and won't boot.

---

### Post by zombifier25 on 2012-06-21
If the vendors make it clear to the users that there is Secure Boot, listing the advantages and disadvantages of secure boot, and giving step by step instructions to disable it, then I see no problem. [size=1]I hope they will, because if they won't, then it's just bad for the free market.[/size]

And the inability to disable Secure Boot on ARM devices isn't that big of a deal. Most *current* ARM devices are smart phones and tablets, and hey, last time I checked, you can't install apps outside the AppStore on an iPhone/iPad either (without jailbreaking). Of course, when ARM computers become mainstream, it will definitely be an issue, but for now, it's not.

---

### Post by CharlesA on 2012-06-21
> **zombifier25 said:**
> 
And the inability to disable Secure Boot on ARM devices isn't that big of a deal. Most *current* ARM devices are smart phones and tablets, and hey, last time I checked, you can't install apps outside the AppStore on an iPhone/iPad either (without jailbreaking). Of course, when ARM computers become mainstream, it will definitely be an issue, but for now, it's not.

I suppose the same could be said about Android, but I think you can install other software on them without rooting. I wonder why no one is raging about having vendor lock-in on iPhone/iPad/iPod/iWhatever.

---

### Post by mips on 2012-06-21
> **CharlesA said:**
> I wonder why no one is raging about having vendor lock-in on iPhone/iPad/iPod/iWhatever.

Well we know that's proprietary stuff and they have a eula dictating what you can and cannot do on their hardware (not that I reckon the eulas are fair). OSS stuff on the other hand you expect to be open and without restrictions and not to follow hardware lock downs.

---

