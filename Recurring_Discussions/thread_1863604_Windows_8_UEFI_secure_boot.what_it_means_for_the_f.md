---
title: "Windows 8 UEFI secure boot.what it means for the future of linux?"
date: 2011-10-18
forum: Recurring Discussions
---

### Post by BigAluk on 2011-10-18
Below is a link to the article in full. Your thoughts and feedback is appreciated 


[http://www.guardian.co.uk/technology/blog/2011/sep/28/windows-8-secure-boot-worry](http://www.guardian.co.uk/technology/blog/2011/sep/28/windows-8-secure-boot-worry)




as a new convert to ubuntu 10.10 some months ago i feel a lot happier now than i did when i used windows for many years way back in days of 3.1 thru to win7.

The idea of open source appealed to me and the fact that is was said to me more secure from malware and viruses. 

When i started using it i was even more pleased with the product. User interface is intuitive and simple to pick up .. everything was just smoother and less stressful.. happy days :) 

I realise that i have turned up late to the party so imagine my concern when i read the following, extracts below; 


"Why the Windows 8 UEFI secure boot thing has me worried
UEFI is designed to replace the old-school BIOS subsystem that can be found in every computer. (The BIOS is used to prepare the ground for loading the full-on operating system that you might have installed on your computer – eg, Linux, Mac OS X, Windows or a mixture.)

UEFI is not a particularly new idea. Like everything in our industry, things change, evolve and improve and UEFI looks to fill in some gaps and make the pre-OS environment more flexible, maintainable and manageable. Why it's become relevant in the press recently is that Microsoft has stated that in order to get certification (ie, a logo) for any boxes shipped with Windows 8 pre-installed, a feature called "secure boot" has to be enabled.

The problem with this arrangement is that it ties a machine that once had Windows 8 on it in such a way that it can only run Windows 8, Windows 9, Windows 10 and so on. If you want to install Linux on it, or create a Hackintosh, or make up your own operating system with secure boot enabled, your boot will fail"

---

### Post by MonolithImmortal on 2011-10-18
Not this again.

---

### Post by Captain Smiley Pants on 2011-10-18
Really seems like a non issue and people are just scared for the sake of being scared.

If a manufacturer doesn't allow you to turn it off, they are asking for lost sales and are obviously stupid.

The sky is not falling, chill out.

---

### Post by sffvba[e0rt on 2011-10-18
*Thread moved to **Recurring Discussions**.*


404

---

### Post by beew on 2011-10-18
> **Captain Smiley Pants said:**
> Really seems like a non issue and people are just scared for the sake of being scared.

If a manufacturer doesn't allow you to turn it off, they are asking for lost sales and are obviously stupid.

The sky is not falling, chill out.

I am wondering how much market share do we have that you can be so confident. "If manufacturer doesn't allow you to turn off Optimus they are asking for lost sales and are obviously stupid". Well most don't.

---

### Post by alexan on 2011-10-18
The problem is not Microsoft which make rules for their business... but the hardware manufacturer who accept them!

I mean: look what's doing Apple to Samsung... if this battle were on desktop pc Microsoft didn't need even to sue them: they had just plainly the power to shut their business off with few "OS Update".

---

### Post by sadaruwan12 on 2011-10-18
To all community members who value freedom and believe that the hardware or software after we buy it we have to be able to use it the way we want I found this on DistrWatch weekly but after reading this it scared me 'cos what if this happens and our machines lock down on us what will happen to us.

Please I plea to the community let's get together  and do something about this secure boot issue the article is below.

> In case some of our readers aren't familiar with this topic, let me provide a little background. A few weeks ago Matthew Garrett, an employee at Red Hat, made a blog posting in which he raised concerns about Microsoft's Windows 8 logo program. That is, the program which allows OEMs to attach a "Designed for Windows 8" sticker on the machines they sell. One of the requirements in the new logo program is that computers displaying the logo and shipping with a client version of Windows 8 pre-installed must also have secure boot enabled. What is secure boot? Basically computers will be shipped with signing keys installed into their firmware. When the secure boot feature is enabled executable programs and drivers cannot be run unless they're signed by one of these keys. In theory this would prevent malware from installing itself on a computer in such a way that would allow the malware to be run before the operating system. However, while this may be an attractive security feature, Matthew Garrett points out such a feature would also prevent alternative operating systems, such as Linux, from being installed.

There are a few points which further complicate things. There is no central signing authority, so it's not a simple matter of getting one set of keys that will work everywhere, each vendor will have their own keys and getting executables signed will probably require striking a deal with each vendor. Another issue is that GRUB2, which is used in many big name Linux distributions, is prevented from using such keys due to the GPLv3 license. Linux distributions will have to roll back to GRUB Legacy, LILO or some other boot loader if they wish to support secure booting.

It's understandable this news has raised concerns in the Linux community that the next generation of hardware may prevent installing Linux. However, I personally don't think we need to worry yet. For one thing OEMs will probably include the ability to disable secure boot. Just because machines shipping with Windows 8 (client) need to have the feature enabled doesn't mean users will be blocked from turning it off. In fact OEMs would be shooting themselves in the foot, would probably shoot both feet clean off, if they didn't include an option to disable secure booting. The European Union tends to keep a close eye on these sorts of things and they are likely to demand hardware can be unlocked. Even if the EU doesn't some companies, like Dell, have found it's profitable to sell Linux boxes and don't show any sign of leaving that customer base behind. It's likely many machines will ship without the logo and without secure booting enabled. After all, it's not just Linux users who aren't going to want to wrestle with secure booting, the IT departments of medium and large companies, places that roll out standard images to a variety of hardware, are not going to want to manually disable secure booting on each machine. Even Matthew Garrett, who raised the issue, points out it's "not worth panicking yet".

However, just because there isn't cause to panic doesn't mean we should sit quietly on the sidelines and wait. This is a good time to get in touch with the companies you may be purchasing computers from in the future and let them know what you think. Dell, HP, Toshiba, IBM, Acer and the rest have contact pages just for moments like this. Tell them which is more important to you, the sticker or the ability to use your computer the way you want. You may also wish to sign the Free Software Foundation's statement urging computer makers to implement secure booting in such a way that will allow alternative operating systems to be installed.

Please, let's send as much messages we can to hardware vendors not to do this and community we have to save our selfs no big company going to come to the rescue we've to be the soldiers who protect what we helped to build so lets fight.

Are you Game ?

---

### Post by sffvba[e0rt on 2011-10-18
***Threads merged.***


404

---

### Post by Mikeb85 on 2011-10-18
Microsoft would be asking for trouble if they pushed this.  Alot of corporations use Linux boxes, and most new PC sales come from corporations (home PCs aren't upgraded frequently, and mobile devices/laptops make up most of the new consumer sales).  Not to mention, they'd be begging for a new round of antitrust lawsuits.

---

### Post by Lars Noodén on 2011-10-19
The FSF has recently made a statement on UEFI: [Will your computer's "Secure Boot" turn out to be "Restricted Boot"?](http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot)  

Even before the FSF's statement, the potential for problems for Linux with "Secure Boot" is obvious.  Even now as Linux, and AFAIK Ubuntu, are growing on the desktop, it does not have enough pull to get in on the OEMs.  A quick check of most any OEM will not show the option of Ubuntu or any other Linux distro pre-installed.  What is Canonical's position on the proposed "Secure Boot"?

Waiting the decade or so for anti-trust action to wend its way through the courts will be too late.  For example, the [Novel v Microsoft](http://www.groklaw.net/article.php?story=20111018190335196) trial is just getting started even though the incidents are from 1995.  Action, proactive effort, can be taken now.

---

### Post by beew on 2011-10-19
This stunt will actually affect more than just Linux users. Windows users will get into problems with unsigned hardware, they won't be able to upgrade or downgrade their Windows OS, they won't be able to boot from rescue CDs etc. The way that this is implemented (allow the OEMs and MS to control the key signing) is just anti-user, period, whether you use Linux or Windows. 

Most Windows users don't see that coming because mostly when they have problems (like when their OS is infected to an extent that requires a reinstallation) they go to some fix it guy to get their problem solved, but with secure boot chances are the fix it guy wouldn't be able to fix it anymore.

These points have to be highlighted.Somehow Windows users have to be brought on side for us to have a chance to fight this.

---

### Post by Meelad on 2011-10-19
I don't think Microsoft can push this (legally).. They can introduce it, but they have to leave an option for people who don't want it.. They can convert SOME PCs to be their own (like Apple did) but they can't convert ALL PCs to be theirs (like Apple can't do).

---

### Post by bobsageek on 2011-10-26
I wouldn't be so sure that MS can't take a passive appearance on this and still do some damage. They are requiring that any product to be considered "Windows 8" certified and logo'd have secure boot enabled by default with no option for user control/shut-off required. OEMs always take the path of least resistance and will toe the line, do a quick search and you can find some anecdotal evidence that HP already applied this to the latest round of S-series desktops and people cannot get Linux installed. Do a quick search for UEFI on Newegg and you'll see pages of motherboards showing it, those OEMs will scramble to make sure they get that certified for Win 8 logo. I don't think it's reason to panic, but we should take it seriously.

[B]Some good news, I asked Todd Finch from Dell (Linux Product Marketing Manager who is active in Linux discussion groups on LinkedIn.com) the following...

Q:Todd, here's a big concern that Dell should get in front of right away, what are the plans regarding UEFI and Secure Boot? [http://mjg59.dreamwidth.org/5850.html](http://mjg59.dreamwidth.org/5850.html)

I'd suggest and early and clear statement from Dell that they will be transparent about this is key, HP is already shipping some new S series desktops that won't boot a Linux image (anecdotal but more than one source). I've always been able to find a Dell I can work with but this genuinely has me concerned.

A:  UEFI & Secure Boot: Bob--We're aware of this issue. For Dell w/ Linux, I promise you Secure Boot will either be compatible with Linux, or at a minimum be turned off in the BIOS. For Dell w/ Windows, I *think* the user can disable Secure Boot in the BIOS. The Windows Product Mkt Mgrs sit 10 feet from me, so I know who to harass. : ) 

And my last reply to Todd...

Good news Todd, you guys should really publicize this fact, the Linux community is concerned and you could get some serious good will out of making this public.

And Todd's reply to me...

 Bob--just got confirmation from my Windows counterpart that the plan is 1) to enable Secure Boot and 2) to allow the user to turn off Secure Boot in the BIOS. So, wiping Windows and installing Linux (or dual-boot) should not be a problem regarding Secure Boot.[/B]

---

### Post by sffvba[e0rt on 2011-10-28
[White Paper: Secure Boot impact on Linux ]("http://blog.canonical.com/2011/10/28/white-paper-secure-boot-impact-on-linux/")


404

---

### Post by Dry Lips on 2011-10-28
> **not found said:**
> [White Paper: Secure Boot impact on Linux ]("http://blog.canonical.com/2011/10/28/white-paper-secure-boot-impact-on-linux/")


404

Note that Canonical is essentially recommending that that the hardware 
manufacturers do just what FSF urges them to do in their petition... 
In other words, Canonicals take on this issue is identical to FSFs.

**Canonical:**> 
This is why** we recommend that systems manufacturers include a mechanism for configuring your own list of approved software**. This will allow you to run Windows 8 and Linux at the same time in your PC with Secure Boot &#8220;**ON**&#8221;. 
[...]
**we recommend that  PCs include a User Interface to easily enable or disable Secure Boot **and allow the user to chose to change their operating system.[http://blog.canonical.com/2011/10/28/white-paper-secure-boot-impact-on-linux/](http://blog.canonical.com/2011/10/28/white-paper-secure-boot-impact-on-linux/)



**FSF-petition:**
> We, the undersigned, urge all computer makers implementing UEFI's so-called "Secure Boot" to do it in a way that allows free software operating systems to be installed. To respect user freedom and truly protect user security, **manufacturers must either allow computer owners to disable the boot restrictions, or provide a sure-fire way for them to install and run a free software operating system of their choice**. We commit that we will neither purchase nor recommend computers that strip users of this critical freedom, and we will actively urge people in our communities to avoid such jailed systems.
[http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement](http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement)

---

### Post by Dr. C on 2011-10-28
> **Dry Lips said:**
> Note that Canonical is essentially recommending that that the hardware 
manufacturers do just what FSF urges them to do in their petition... 
In other words, Canonicals take on this issue is identical to FSFs.

**Canonical:**[http://blog.canonical.com/2011/10/28/white-paper-secure-boot-impact-on-linux/](http://blog.canonical.com/2011/10/28/white-paper-secure-boot-impact-on-linux/)

**FSF-petition:**
[http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement](http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement)

The positions are not identical. The Canonical / Redhat position goes a lot further than the FSF petition in protecting Free Software by placing key authorization and revocation in the hands of the owner of the hardware. This allows the use of a 100% Free Software Operating such as gNewSense with secure boot while at the same time revoking the keys for a propriety operating system such a Microsoft Windows 8, thereby preventing it from booting. The FSF petition only calls for allowing the Free Operating system to boot in a non secure fashion. Big difference.

I do by the way continue to urge the signing of the FSF petition.

---

### Post by KiwiNZ on 2011-10-28
> **Dr. C said:**
> The positions are not identical. The Canonical / Redhat position goes a lot further than the FSF petition in protecting Free Software by placing key authorization and revocation in the hands of the owner of the hardware. This allows the use of a 100% Free Software Operating such as gNewSense with secure boot while at the same time revoking the keys for a propriety operating system such a Microsoft Windows 8, thereby preventing it from booting. The FSF petition only calls for allowing the Free Operating system to boot in a non secure fashion. Big difference.

I do by the way continue to urge the signing of the FSF petition.

Quote from Canonical....

"This is why we recommend that systems manufacturers include a mechanism for configuring your own list of approved software. **This will allow you to run Windows 8 and Linux at the same time in your PC with Secure Boot “ON”.** This should also include you being able to try new software from a USB stick or DVD."

---

### Post by Dr. C on 2011-10-28
> **KiwiNZ said:**
> Quote from Canonical....

"This is why we recommend that systems manufacturers include a mechanism for configuring your own list of approved software. **This will allow you to run Windows 8 and Linux at the same time in your PC with Secure Boot “ON”.** This should also include you being able to try new software from a USB stick or DVD."

There are many valid and possible scenarios such as a dual boot system with GNU / Linux and Microsoft Windows with both operating systems using secure boot. The Canonical / Redhat White Paper [Secure Boot Impact on Linux]("http://ozlabs.org/docs/uefi-secure-boot-impact-on-linux.pdf") recommendations address all of these possible scenarios. The recommendations are in Section 6 > 6. Recommendations
Secure boot technology can be beneficial for increasing the security of Linux installations. Linux distributions should gain secure boot compatibility in order to increase protection against malware and disk encryption circumvention, provided that users’ freedoms are protected. Unfortunately, the current implementation recommended for secure boot makes installation of Linux more difficult and may prevent users from modifying their own systems. 

So, we recommend that secure boot implementations are designed around the hardware owner having full control of the security restrictions.

We recommend that all OEMs allow secure boot to be easily disabled and enabled through a firmware configuration interface 

It is essential that users are able to remove secure boot restrictions, and boot the software of their choice on the devices that they own. Furthermore, the interface to configure this option should be easily accessible by non-technical users. 

Of course, this option should only be available to users with physical access to the hardware, and not be accessible via programmatic means.
We recommend that OEMs (with assistance from BIOS vendors) provide a standardised mechanism for configuring keys in system firmware

For secure boot to be useful in a user-controlled environment, it must be possible for users to add custom keys (KEK, db and dbx entries) to the system firmware. Keys may then be shipped with an operating system or generated by the user. This allows the user to maintain control of the code run on their systems without giving up the benefits of secure boot. 

For support purposes, the mechanism provided for key management must be consistent across platforms, and provide a simple method of booting custom software, including from removable media. A suggested implementation may be to scan removable media for signing keys and prompt
the user for their installation, or using the specification-defined setup mode to allow key reconfiguration.

We recommend that hardware ship in setup mode, with the operating system taking responsibility for initial key installation.

Shipping hardware in setup mode allows key policy to be determined by the operating system vendor or end user. Pre-installed operating systems could then install their own signing keys on first boot. This permits the user to avoid the situation where pre-installed signing keys do not match the user's desired security policy. 

---

### Post by Duncan_Macdonald on 2011-10-29
As UEFI is only in control until the OS loader is started, it seems to me that the only bit of Linux that would need to be signed is the bootloader (GRUB or its successor). As this is very infrequently updated (compared to the Linux kernel) having it signed should not be too difficult. (If Microsoft tried to prevent the Linux bootloader from being signed then they would lay themselves open for a lawsuit.)

---

### Post by Dr. C on 2011-10-29
> **Duncan_Macdonald said:**
> As UEFI is only in control until the OS loader is started, it seems to me that the only bit of Linux that would need to be signed is the bootloader (GRUB or its successor). As this is very infrequently updated (compared to the Linux kernel) having it signed should not be too difficult. (If Microsoft tried to prevent the Linux bootloader from being signed then they would lay themselves open for a lawsuit.)

This kind of approach, using a signed bootloader to launch unsigned code,  was suggested by various columnists but is doomed to failure. since it effectively defeats secure boot. A Windows malware writer could use such a bootloader to launch a Windows root kit instead of GNU / Linux. Furthermore this approach has already being tried with a 64bit Windows Vista/7 driver that launched an unsigned driver and Microsoft went out of its way to revoke the signature. 

The [Canonical / Redhat White Paper]("http://ozlabs.org/docs/uefi-secure-boot-impact-on-linux.pdf") provides a viable solution. The Linux Foundation has also released [Making UEFI Secure Boot Work With Open Platforms]("https://www.linuxfoundation.org/sites/main/files/lf_uefi_secure_boot_open_platforms.pdf") with a similar recommendations to the Canonical / Redhat White Paper. It is also very important to sign the [FSF Petition]("http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement") in order to keep the pressure up.

---

### Post by beew on 2011-10-29
> **Duncan_Macdonald said:**
> As UEFI is only in control until the OS loader is started, it seems to me that the only bit of Linux that would need to be signed is the bootloader (GRUB or its successor). As this is very infrequently updated (compared to the Linux kernel) having it signed should not be too difficult. (If Microsoft tried to prevent the Linux bootloader from being signed then they would lay themselves open for a lawsuit.)


The point is not whether you can sign the bootloader, but why should you need the OEM and MS's permission to boot Linux (or anything for that matter) in the first place?

A lawsuit would probably take 10 years to resolve. It is a last resort but it is far from ideal. 

Now the Linux foundation has come up with very concrete recommendations in their white paper they should invite MS to respond and the spot light would be on them. If they are indeed only trying to make WIndows more secure, if they are as innocent as the MS apologists insist, then they should add their endorsement to the white paper. That would clear things up.

In the meantime we must keep the discussion alive in the internet and elsewhere to show the OEMs and MS that some people do care so that they won't pull a fast one. 

I would urge everyone who cares about freedom to sign the FSF statement. I am circulating it among friends and quite a few Windows users are going to sign because while often depicted as a Linux issue, it will affect Winodws users as well. They don't see it because they tend to get other people to worry about trouble shooting their machines, but this will post problems to the trouble shooters as well.

Talking about generating discussions, the Canonical-Redhat whitepaper is out for only one day and in less than 12 hour it is buried in recurring discussions in UF as if to hide it. Why? This is shooting oneself on the foot.

---

### Post by Lildirt on 2011-10-30
This is personally why I rarely upgrade operating systems.
This computer came with a fresh install CD and Key of Windows 7 Ultimate.
I never installed it.
I still use Windows Vista running alongside with the good ol' Ubuntu :)

My opinion here is basically "#!@$ you Win8, you're probably just graphic updates + small backend updates like Windows 7 anyways."
Correct me if I'm wrong, but.. Isn't Windows 7 basically just more patches of Windows Vista and graphics updates?

(Just a note, Vista is NOT a 'buggy piece of @!#%'. In the fact, you need significant hardware for it, so if it works with XP, it might not work with Vista. In short: Learn2Upgrade)

Doesn't Linux merge with the computer's BIOS to boot off the Linux Partition/Directory? Or is it actually software booting before OS?

Honestly, if this went through, I bet you:
A. No one would have it.
B. No one would use Windows anymore.
C. Bill Gate's would have a nice burning house/office building.


I use Linux DAILY for my gaming needs, and some educational/business needs! I think the only thing Linux can't do is run Microsoft Office Professional Plus 2010. LibreOffice isn't the best for it :P

I think I strayed off-topic.

Long Live Linux <3

---

### Post by Dry Lips on 2011-10-31
> **Dry Lips said:**
> Note that Canonical is essentially recommending that that the hardware manufacturers do just what FSF urges them to do in their petition... 
In other words, Canonicals take on this issue is identical to FSFs.

> **Dr. C said:**
> The positions are not identical. The Canonical / Redhat position goes a lot further than the FSF petition in protecting Free Software by placing key authorization and revocation in the hands of the owner of the hardware. This allows the use of a 100% Free Software Operating such as gNewSense with secure boot while at the same time revoking the keys for a propriety operating system such a Microsoft Windows 8, thereby preventing it from booting. The FSF petition only calls for allowing the Free Operating system to boot in a non secure fashion. Big difference.

I do by the way continue to urge the signing of the FSF petition.

Okay, I only skimmed through the summary on Canonicals blog. But it's interesting
what you say about Canonical /Red Hat going further than FSF. At least it shows that
FSF have been quite careful in their response to this; to blame them of mindless FUD 
is quite unfair IMO.

So what you're saying is that perhaps the FSF don't go far enough?

---

### Post by Dr. C on 2011-11-02
> **Dry Lips said:**
> Okay, I only skimmed through the summary on Canonicals blog. But it's interesting
what you say about Canonical /Red Hat going further than FSF. At least it shows that
FSF have been quite careful in their response to this; to blame them of mindless FUD 
is quite unfair IMO.

So what you're saying is that perhaps the FSF don't go far enough?

Yes. The difference is that while the FSF petition only calls for the installation of Free Software, the Canonical / Redhat white paper goes further by requiring that the control of the signing keys be with the owner of the hardware and not with the OEMs. This is critical to ensure that a  GNU / Linux distribution using GPL v3 code can be booted using secure boot and not be in a subservient position to Microsoft Windows. The  Linux Foundation actually goes even further than the Canonical / Redhat white paper by requiring a hardware reset [https://www.linuxfoundation.org/sites/main/files/lf_uefi_secure_boot_open_platforms.pdf]("https://www.linuxfoundation.org/sites/main/files/lf_uefi_secure_boot_open_platforms.pdf"). This has a very important long term environmental benefit of allowing Windows 8 computers to be re-purposed to use GNU / Linux when Windows 8 is no longer supported by Microsoft.

---

### Post by KiwiNZ on 2011-11-02
Leaving the approval list open will open vulnerabilities that could be exploited by malware.

---

### Post by beew on 2011-11-02
> **KiwiNZ said:**
> Leaving the approval list open will open vulnerabilities that could be exploited by malware.

By that reasoning the prison would be the safest place on earth. I want my door to have locks but only if I have the keys.

BTW Windows would be a most obvious vulnerability to malware and virus.

---

### Post by KiwiNZ on 2011-11-02
> **beew said:**
> By that reasoning the prison would be the safest place on earth. I want my door to have locks but only if I have the keys.

BTW Windows would be a most obvious vulnerability to malware and virus.

That makes no logical sense at all.

---

### Post by Dr. C on 2011-11-02
> **KiwiNZ said:**
> Leaving the approval list open will open vulnerabilities that could be exploited by malware.

No it will not. This is addressed in Section 6 of the Canonical / Redhat white paper

> It is essential that users are able to remove secure boot restrictions, and boot the software of their choice on the devices that they own. Furthermore, the interface to configure this option should be easily accessible by non-technical users. Of course, this option should only be available to users with physical access to the hardware, and not be accessible via programmatic means. 

---

### Post by beew on 2011-11-02
> **KiwiNZ said:**
> That makes no logical sense at all.
If it doesn't then it is because your post which I replied to doesn't.

Unless I misunderstood you, you are saying that the only way to have a 'secure" system is to have MS and the OEM completely lock down your hardware, that is the kind of 'security' in prison. I don't want it, and I doubt that anyone would. It is as absurd as saying your house wouldn't be secure if you have the keys to the locks(and furthermore the Mafia should have them instead)

---

### Post by KiwiNZ on 2011-11-02
> **Dr. C said:**
> No it will not. This is addressed in Section 6 of the Canonical / Redhat white paper

This is where potential vulnerability is. It leaves a possible weak point back door that could be exploited.

[I]"We recommend that all OEMs allow secure boot to be easily disabled and enabled through a
firmware configuration interface
It is essential that users are able to remove secure boot restrictions, and boot the software of their
choice on the devices that they own. Furthermore, the interface to configure this option should be
easily accessible by non-technical users.
Of course, this option should only be available to users with physical access to the hardware, and
not be accessible via programmatic means.
We recommend that OEMs (with assistance from BIOS vendors) provide a standardised
mechanism for configuring keys in system firmware
For secure boot to be useful in a user-controlled environment, it must be possible for users to add
custom keys (KEK, db and dbx entries) to the system firmware. Keys may then be shipped with an
operating system or generated by the user. This allows the user to maintain control of the code run
on their systems without giving up the benefits of secure boot.
For support purposes, the mechanism provided for key management must be consistent across
platforms, and provide a simple method of booting custom software, including from removable
media. A suggested implementation may be to scan removable media for signing keys and prompt
the user for their installation, or using the specification-defined setup mode to allow key
reconfiguration.
We recommend that hardware ship in setup mode, with the operating system taking
responsibility for initial key installation
Shipping hardware in setup mode allows key policy to be determined by the operating system
vendor or end user. Pre-installed operating systems could then install their own signing keys on first
boot. This permits the user to avoid the situation where pre-installed signing keys do not match the
user's desired security policy."
[/I]

---

### Post by emiller12345 on 2011-11-02
Maybe there should be a hardware level below the UEFI layer, so that it only thinks it's pulling all the strings (if it's even possible).

---

### Post by KiwiNZ on 2011-11-02
> **beew said:**
> If it doesn't then it is because your post which I replied to doesn't.

Unless I misunderstood you, you are saying that the only way to have a 'secure" system is to have MS and the OEM completely lock down your hardware, that is the kind of 'security' in prison. I don't want it, and I doubt that anyone would. It is as absurd as saying your house wouldn't be secure if you have the keys to the locks(and furthermore the Mafia should have them instead)

Reductio ad absurdum  :rolleyes:
[B]
[/B]

---

### Post by beew on 2011-11-02
> **KiwiNZ said:**
> Reductio ad absurdum  :rolleyes:


Exactly, because your "security" argument is absurd.
[B]
EDITED:[/B] Since most security breaches happen after booting into Windows, this is not a "potential' problem but a very real and well documented one and locking down booting doesn't address it at all, the logical thing would be to get rid of Windows if security is that huge a concern.

---

### Post by KiwiNZ on 2011-11-02
> **beew said:**
> Exactly, because your "security" argument is absurd.

:rolleyes::rolleyes::rolleyes::rolleyes::rolleyes::rolleyes::rolleyes::rolleyes:

Because PC's never have exploited vulnerabilities do they ? irrespective of platform.

Here that alarm clock ?

---

### Post by KiwiNZ on 2011-11-02
> **beew said:**
> Exactly, because your "security" argument is absurd.
[B]
EDITED:[/B] Since most security breaches happen after booting into Windows, this is not a "potential' problem but a very real and well documented one and locking down booting doesn't address it at all, the logical thing would be to get rid of Windows if security is that huge a concern.

Good grief 

Why am I even having this discussion.

---

### Post by beew on 2011-11-02
> **KiwiNZ said:**
> :rolleyes::rolleyes::rolleyes::rolleyes::rolleyes::rolleyes::rolleyes::rolleyes:

Because PC's never have exploited vulnerabilities do they ? irrespective of platform.

Here that alarm clock ?

So since there are robberies and thefts you would put padlock on your door and give someone else the key for your protection??? 

Good grief indeed.

I agree with you on one thing, I am not sure why I am even needing to have this discussion.

EDIT: BTW, why not lock down the internet too so that you can only go to websites approved by MS? Obviously there are a lot of security breaches on the internet.

---

### Post by KiwiNZ on 2011-11-02
> **beew said:**
> So since there are robberies and thefts you would put padlock on your door and give someone else the key for your protection??? 

Good grief indeed.

I agree with you on one thing, I am not sure why I am even needing to have this discussion.

EDIT: BTW, why not lock down the internet too so that you can only go to websites approved by MS? Obviously there are a lot of security breaches on the internet.


You do realize that UEFI has been around for a while and it is NOT a MSFT product,design etc?

---

### Post by beew on 2011-11-02
> **KiwiNZ said:**
> You do realize that UEFI has been around for a while and it is NOT a MSFT product,design etc?
You do realize the issue is not UEFI but who should be signing the key, do you?

---

### Post by KiwiNZ on 2011-11-02
> **beew said:**
> You do realize the issue is not UEFI but who should be signing the key, do you?


No, of course not

---

### Post by Dr. C on 2011-11-02
> **emiller12345 said:**
> Maybe there should be a hardware level below the UEFI layer, so that it only thinks it's pulling all the strings (if it's even possible).

This is a simple and sensible solution. Use a hardware reset to place the UEFI in setup mode. It is in fact used by most motherboards to reset a password protected BIOS.

---

### Post by KiwiNZ on 2011-11-02
From an Enterprise perspective secure boot is a blessing for me. It allows me to have machine further locked down to help prevent unauthorized software being added to the machines and network.

---

### Post by Dr. C on 2011-11-02
> **KiwiNZ said:**
> From an Enterprise perspective secure boot is a blessing for me. It allows me to have machine further locked down to help prevent unauthorized software being added to the machines and network.

This is of course one of the benefits of secure boot. Furthermore it illustrates why it is imperative that control of the keys lie with the owner of the hardware. For example if one is running GNU / Linux in the enterprise one wants to lock out unauthorized software including Microsoft Windows.

---

### Post by KiwiNZ on 2011-11-02
> **Dr. C said:**
> This is of course one of the benefits of secure boot. Furthermore it illustrates why it is imperative that control of the keys lie with the owner of the hardware. For example if one is running GNU / Linux in the enterprise one wants to lock out unauthorized software including Microsoft Windows.

And in there lays the weakness I am referring to. If the keys are in the "wild" so to speak the security is weakened and a vulnerability created.

 keys etc can be cracked, that cracking become easier if the Keys are at large and can be analyzed.

---

### Post by Dr. C on 2011-11-03
> **KiwiNZ said:**
> And in there lays the weakness I am referring to. If the keys are in the "wild" so to speak the security is weakened and a vulnerability created.

 keys etc can be cracked, that cracking become easier if the Keys are at large and can be analyzed.

With respect there is no such vulnerability. [http://en.wikipedia.org/wiki/Public-key_cryptography]("http://en.wikipedia.org/wiki/Public-key_cryptography")

---

### Post by beew on 2011-11-03
> **KiwiNZ said:**
> From an Enterprise perspective secure boot is a blessing for me. It allows me to have machine further locked down to help prevent unauthorized software being added to the machines and network.
> And in there lays the weakness I am referring to. If the keys are in the  "wild" so to speak the security is weakened and a vulnerability  created.

 keys etc can be cracked, that cracking become easier if the Keys are at large and can be analyzed.
So to put 1 and 1 together locking down the hardware and giving the key to MS and the OEM which would result in further marginalising Linux would be a blessing for you,--the exact scenario that the "alarmists" are worrying about,-- now we all know where you stand, so please stop calling other people who try to raise awareness and resist this "spreading FUD" and undermine others' efforts.

---

### Post by KiwiNZ on 2011-11-03
> **beew said:**
> So to put 1 and 1 together locking down the hardware and giving the key to MS and the OEM which would result in further marginalising Linux would be a blessing for you,--the exact scenario that the "alarmists" are worrying about,-- now we all know where you stand, so please stop calling other people who try to raise awareness and resist this "spreading FUD" and undermine others' efforts.

The Linux Distros need to work with the OEM's to maintain their status and show them the financial benefits, activist actions is not the professional way to conduct business.

As to your last point, you have no clue as to my position.

---

### Post by beew on 2011-11-03
> **KiwiNZ said:**
> The Linux Distros need to work with the OEM's to maintain their status and show them the financial benefits, activist actions is not the professional way to conduct business.

As to your last point, you have no clue as to my position.

Yeah, hacking kernels and making a free clone to Unix are not "professional" either. If everyone has been "professional" historically by just pleading with the power that be without "activist actions" women would still have no right to vote.

---

### Post by KiwiNZ on 2011-11-03
> **beew said:**
> Yeah, hacking kernels and making a free clone to Unix are not "professional" either. If everyone has been "professional" historically by just pleading with the power that be without "activist actions" women would still have no right to vote.


it is NOT some grand social crusade it is business ...Get it.

---

### Post by beew on 2011-11-03
> **KiwiNZ said:**
> it is NOT some grand social crusade it is business ...Get it.

Same principle.

---

### Post by KiwiNZ on 2011-11-03
> **beew said:**
> Same principle.

No it is not, you do not conduct business and board room negotiations with petitions and placards.

It is done with facts and presenting fiscal data, sales potentials, cost/benefit analysis etc etc etc.

---

### Post by Dr. C on 2011-11-03
> **KiwiNZ said:**
> No it is not, you do not conduct business and board room negotiations with petitions and placards.

It is done with facts and presenting fiscal data, sales potentials, cost/benefit analysis etc etc etc.

How on earth can one make a presentation to board of an enterprise on the economic benefits of installing an operating system, any operating system for that matter, if the enterprise can not install it because they are locked out of their own hardware?

---

### Post by KiwiNZ on 2011-11-03
> **Dr. C said:**
> How on earth can one make a presentation to board of an enterprise on the economic benefits of installing an operating system, any operating system for that matter, if the enterprise can not install it because they are locked out of their own hardware?

I was referring to the OEM's

---

### Post by Dr. C on 2011-11-03
> **KiwiNZ said:**
> I was referring to the OEM's

Who depending on the source do between 95% and 99% of their business with Microsoft Products. 

Raising public awareness has to be part of equation. In any case what is so unprofessional about the actions of The Free Software Foundation, Canonical, RedHat, The Linux Foundation etc.? Raising the issue now is the professional thing to do instead of waiting for the release of Windows 8 and then having to take legal action against Microsoft and its OEM partners over anti trust violations. 

It may have to come to legal action but at least a genuine effort was made to avoid a legal situation in which nobody wins.

---

### Post by KiwiNZ on 2011-11-03
> **Dr. C said:**
> Who depending on the source do between 95% and 99% of their business with Microsoft Products. 

Raising public awareness has to be part of equation. In any case what is so unprofessional about the actions of The Free Software Foundation, Canonical, RedHat, The Linux Foundation etc.? Raising the issue now is the professional thing to do instead of waiting for the release of Windows 8 and then having to take legal action against Microsoft and its OEM partners over anti trust violations. 

It may have to come to legal action but at least a genuine effort was made to avoid a legal situation in which nobody wins.

They do 95% + due to customer demand. If the sales demand were different they would do an altered demand business mix.Legal action and protest is not they way to do it. Show them the sales benefits etc . They are there to make a profit
show them how to make greater profit and they will follow.

---

### Post by Dr. C on 2011-11-03
Legal action is what many are working very hard to avoid by raising this issue.

---

### Post by KiwiNZ on 2011-11-03
> **Dr. C said:**
> Legal action is what many are working very hard to avoid by raising this issue.

Protests and petitions are just as obnoxious as Court action. There is greater prospects for success if well researched and well presented Business cases are put in front of the OEM's.

---

### Post by Dr. C on 2011-11-03
> **KiwiNZ said:**
> Protests and petitions are just as obnoxious as Court action. There is greater prospects for success if well researched and well presented Business cases are put in front of the OEM's.

Protests and petitions are obnoxious because they work and are in many situations necessary. So is legal action. The trick is to know when to stop protesting or suing, sit down and work something out. I am not dismissing the business approach, but one must not also discount the protesters / petitioners or the threat of legal action. In many cases **all** are needed.

---

### Post by KiwiNZ on 2011-11-03
> **Dr. C said:**
> Protests and petitions are obnoxious because they work and are in many situations necessary. So is legal action. The trick is to know when to stop protesting or suing, sit down and work something out. I am not dismissing the business approach, but one must not also discount the protesters / petitioners or the threat of legal action. In many cases **all** are needed.

Off my head I can think of several very successful business cases. However I am struggling to think of a single successful petition.

---

### Post by mutley89 on 2011-11-03
> **KiwiNZ said:**
> Protests and petitions are just as obnoxious as  Court action. There is greater prospects for success if well researched  and well presented Business cases are put in front of the OEM's.
Surely the best "business case" is to demonstrate to HW manufacturers  how many potential customers they will lose if they start selling  locked down systems?  If so, how is a petition stating exactly this  obnoxious?

---

### Post by KiwiNZ on 2011-11-03
> **mutley89 said:**
> Surely the best "business case" is to demonstrate to HW manufacturers  how many potential customers they will lose if they start selling  locked down systems?  If so, how is a petition stating exactly this  obnoxious?

Petitions and protest are confrontational.Confrontation is not the way to conduct business when one is trying to engender cooperation.

 By working with the OEM's, presenting the data with regards to potential losses and conversely the potential gains of allowing 'user' to select is a better and vastly more professional approach and is more likely to bring results.

---

### Post by ##Villain on 2011-11-05
> **KiwiNZ said:**
> Petitions and protest are confrontational.Confrontation is not the way to conduct business when one is trying to engender cooperation.

 By working with the OEM's, presenting the data with regards to potential losses and conversely the potential gains of allowing 'user' to select is a better and vastly more professional approach and is more likely to bring results.

Work with them than against them?

---

### Post by dave2001 on 2011-11-07
> **KiwiNZ said:**
> Petitions and protest are confrontational.Confrontation is not the way to conduct business when one is trying to engender cooperation.

 By working with the OEM's, presenting the data with regards to potential losses and conversely the potential gains of allowing 'user' to select is a better and vastly more professional approach and is more likely to bring results.

For the vast majority of end-users, joining a petition or protest is the only viable option for communicating with OEM's. Most people do not have the time, resources, or knowledge to compile a "professional" presentation on the issue... and even if they did, how exactly are they supposed to get the OEM's to take a serious look at it? 

I'm going to have to agree with some other posters here: The bigger the outcry from the customer base, the more likely that the business's involved will rethink their plans.

P.S. Businesses don't "cooperate" in a free market economy; they compete. If they appear to cooperate, that's just because they aren't in direct competition for the same market or resources (at that time). Microsoft has been actively trying to discourage linux use (and Mac of course!) for quite a while.

---

### Post by gutterslob on 2011-11-07
> **KiwiNZ said:**
> Protests and petitions are just as obnoxious as Court action. There is greater prospects for success if well researched and well presented Business cases are put in front of the OEM's.Horse dung!!
There are many, many cases throughout history (in any genre/industry) where "well researched and well presented" alternatives/solutions were simply thrown out because of corruption/lobbying/politics (money talks, basically). In some sectors, your solution may even be light years ahead of what's currently available, but it won't matter if there's no board-member or judge to back you.

One more thing, why is everyone putting "protest" and "petition" in the same group?

---

### Post by Lars Noodén on 2011-11-07
> **dave2001 said:**
> 
I'm going to have to agree with some other posters here: The bigger the outcry from the customer base, the more likely that the business's involved will rethink their plans.


It is also a very clear way of showing that there is demand.

---

### Post by KiwiNZ on 2011-11-07
> **gutterslob said:**
> Horse dung!!
There are many, many cases throughout history (in any genre/industry) where "well researched and well presented" alternatives/solutions were simply thrown out because of corruption/lobbying/politics (money talks, basically). In some sectors, your solution may even be light years ahead of what's currently available, but it won't matter if there's no board-member or judge to back you.

One more thing, why is everyone putting "protest" and "petition" in the same group?

Businesses are free to accept the presentation that best fits their strategic goals and fiscal circumstance.

---

