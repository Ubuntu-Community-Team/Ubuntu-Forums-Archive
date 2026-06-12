---
title: "Microsoft releases GPL driver code."
date: 2009-07-20
forum: Recurring Discussions
---

### Post by JDShu on 2009-07-20
[http://blogs.zdnet.com/microsoft/?p=3403](http://blogs.zdnet.com/microsoft/?p=3403)

What does this mean? I can't see Microsoft's motivation to do this.

---

### Post by Sealbhach on 2009-07-20
It seems to be to make virtualization work better, so you can run a virtual session of Linux better on Windows - maybe something to do with Novell. 

.

---

### Post by zekopeko on 2009-07-20
> **JDShu said:**
> [http://blogs.zdnet.com/microsoft/?p=3403](http://blogs.zdnet.com/microsoft/?p=3403)

What does this mean? I can't see Microsoft's motivation to do this.

That's probably because you didn't read the article closely.

> &#8220;Our initial goal in developing the (Linux driver) code was to enable Linux to run as a virtual machine on top of Hyper-V, Microsoft&#8217;s hypervisor and implementation of virtualization.

&#8220;The Linux device drivers we are releasing are designed so Linux can run in enlightened mode, giving it the same optimized synthetic devices as a Windows virtual machine running on top of Hyper-V. Without this driver code, Linux can run on top of Windows, but without the same high performance levels. We worked very closely with the Hyper-V team at Microsoft to make that happen.&#8221;

So that MS customers can run Linux virtual machines with the speed boost that Windows get when run as a virtual machine.
That way MS can sell their Windows Server product to companies that want to run Linux but on MS infrastructure.

> &#8220;Customers have told us that they would like to standardize on one virtualization platform, and the Linux device drivers will help customers who are running Linux to consolidate their Linux and Windows servers on a single virtualization platform, thereby reducing the complexity of their infrastructure.&#8221;

EDIT: at OP: did you even read the article past the title?!

---

### Post by doas777 on 2009-07-20
hyperV is microsofts VM Hypervisor software, which currently the industry seems to have little interest in (for reasons like it will only run windows based oses). VMware is killing them all over the marketplace, and virtualbox is prolly more widely used than MS VPC.

until they can get their hardware abstraction right for linux and other alternative Oses, they can't move forward, and risk remaining irrelevant in the VM industry.

I find it amusing that instead of fixing their hyperv to correctly emulate hardware, they choose to submit changes to the drivers in the kernel to sidestep the issue.  the whole problem is prolly their attempts to make ACPI ms only.

---

### Post by JDShu on 2009-07-20
> **zekopeko said:**
> That's probably because you didn't read the article closely.
EDIT: at OP: did you even read the article past the title?!

Yep and I'm too noob to understand it :P been looking through the other articles regarding this.

---

### Post by motang on 2009-07-20
> In an historic move, Microsoft Monday submitted driver source code for inclusion in the Linux kernel under a GPLv2 license.
The code consists of four drivers that are part of a technology called Linux Device Driver for Virtualization. The drivers, once added to the Linux kernel, will provide the hooks for any distribution of Linux to run on Windows Server 2008 and its Hyper-V hypervisor technology. Microsoft will provide ongoing maintenance of the code. 

[Rest here]("http://www.networkworld.com/news/2009/072009-microsoft-linux-source-code.html")

This is huge, I really think Microsoft has turned for the better after Bill Gates left the company. I am extremely surprised with Windows 7, and they are starting to support other browsers (not by choice ;) ) with their web services, and I haven't heard any chair throwing stores lately. ;)

---

### Post by Chemical Imbalance on 2009-07-20
Beat me to it.  Was just about to post the same thing.

This is mind-boggling.  ...And really cool.

There, of course, has to be ulterior motives however.  Microsoft *is* a business.

---

### Post by Eisenwinter on 2009-07-20
Marketing technique. You'll see, they'll use this to screw Linux over somehow.

---

### Post by bacil on 2009-07-20
Thats great, i am currious about support for this environment.

---

### Post by Bölvaður on 2009-07-20
> **Eisenwinter said:**
> Marketing technique. You'll see, they'll use this to screw Linux over somehow.
nah this is just to make sure windows will be the host. you can ration why they would do that in many different ways that in the end does not really matter.
I would be more surprised if they would give us drivers for "MS hardware".

---

### Post by Riffer on 2009-07-20
For once MS didn't bite its nose to spite its face.  Lets also look at this in the cold light of day, MS did this to make money (which is fine).  What I find very interesting is the possible whys.

From what I understand, these drivers will allow Linux desktops to exist on a Windows server.  The article also talks about VMWare and how this gives MS an advantage.  So from that one could guess that MS is willing to give up some of its Desktop Market share to protect and/or increase its market for its server.

I'm thinking that MS sees that cloud computing will be big for enterprise in the next few years.  And that where it will be able to make its money is server software.

---

### Post by Elfy on 2009-07-20
threads merged

---

### Post by NightwishFan on 2009-07-20
I do not really see Microsoft as the enemy too much anymore. We really should worry about Apple sneaking up on us. The wise thing to do is to let Apple, Microsoft, and possibly Google fight, while we watch and wait. :)

---

### Post by Merk42 on 2009-07-20
So does this mean all those people who refuse to use Mono simply because it's related in some way to "M$" will now have to stop using Linux completely?

---

### Post by RiceMonster on 2009-07-20
> **Merk42 said:**
> So does this mean all those people who refuse to use Mono simply because it's related in some way to "M$" will now have to stop using Linux completely?

Who knows, but this will likely create more conspiracy theories from boycottnovel and the like.

---

### Post by Sealbhach on 2009-07-20
> **RiceMonster said:**
> Who knows, but this will likely create more conspiracy theories from boycottnovel and the like.

I don't regard boycottnovell as conspiracy nuts, most of their articles are well referenced and well worth a read. 

.

---

### Post by froggyswamp on 2009-07-20
It is not done to make Linux better but for Microsoft to win the war against other virtualization providers (and also make their server 2008 more attractive).

---

### Post by HappinessNow on 2009-07-20
> **NightwishFan said:**
> I do not really see Microsoft as the enemy too much anymore. We really should worry about Apple sneaking up on us. 

Apple is the TRUE evil empire! ;)

> **NightwishFan said:**
> The wise thing to do is to let Apple, Microsoft, and possibly Google fight, while we watch and wait. :)

Well since Microsoft owns considerable shares in Apple, and two Google CEO's sit on the Apple board of directors, they are all sleeping together.

My hopes are in Google Chrome OS, then we will truly have another choice, since Microsoft and Apple are two sides of the same coin.

Beyond Google's Chrome OS all other Linux based distros are simply litter on the playing field.

I had honestly wished Google would have used BSD as a base instead of Linux.

---

### Post by directhex on 2009-07-20
> **froggyswamp said:**
> It is not done to make Linux better but for Microsoft to win the war against other virtualization providers (and also make their server 2008 more attractive).

Correct.

However, the "other virtualization providers" already do this (e.g. take a peek at the VMware graphics and mouse drivers supplied with X.org)

So, technically, this is an understandable step for them to compete with VMware

---

### Post by motang on 2009-07-20
> **NightwishFan said:**
> I do not really see Microsoft as the enemy too much anymore. We really should worry about Apple sneaking up on us. The wise thing to do is to let Apple, Microsoft, and possibly Google fight, while we watch and wait. :)

Yeah I know what you mean. Apple to me seems more cynical than MS, at least MS makes their own stuff even though they are half *** most of the time while Apple uses open source projects and spins it as their own.

---

### Post by Sxeptomaniac on 2009-07-20
> **directhex said:**
> Correct.

However, the "other virtualization providers" already do this (e.g. take a peek at the VMware graphics and mouse drivers supplied with X.org)

So, technically, this is an understandable step for them to compete with VMware

I was just reading last week that VMware knows that MS is out to take over the virtualization market, and is preparing for Microsoft's usual marketing maneuvers.

[http://www.forbes.com/forbes/2009/0713/technology-software-internet-vmware-arms-for-microsoft-battle.html](http://www.forbes.com/forbes/2009/0713/technology-software-internet-vmware-arms-for-microsoft-battle.html)

---

### Post by andamaru on 2009-07-20
Isn't this equivalent to Virtual box, and VMware's guest tools...

---

### Post by directhex on 2009-07-20
> **andamaru said:**
> Isn't this equivalent to Virtual box, and VMware's guest tools...

More or less, yes.

---

### Post by andrew.g on 2009-07-20
Any more gushing for Microsoft here and you would form a geyser twice that of Old Faithful.

Having said that, I do find those that give Microsoft plaudits for this most sincere of gestures any credence  (Ballmer himself described Linux as a cancer, did he not?) amusing.

---

### Post by HappinessNow on 2009-07-20
> **motang said:**
> Yeah I know what you mean. Apple to me seems more cynical than MS, at least MS makes their own stuff even though they are half *** most of the time while Apple uses open source projects and spins it as their own.

Apple is famous for; and makes a ton of money, by taking Open Source and free applications putting a slight spin on it and re-branding it with Apple's name then selling it at outrageous amounts of money to ready, willing and able participants.

---

### Post by Dr. C on 2009-07-20
What Microsoft has done here is release drivers so that Linux will run on its virtual hardware. Instead of playing games with propriety drivers and software shims as Nvidia for example does they have done it the proper way by releasing a GPL driver that can then be included in the Linux kernel. 

It is no different from any hardware company the releases Linux GPL driver code so that their devices work "out of the box" on Linux. 

By the way this is not the first time that Microsoft has distributed software under the GPL v2

---

### Post by andrew.g on 2009-07-20
> **FineE said:**
> What Microsoft has done here is release drivers so that Linux will run on its virtual hardware. Instead of playing games with propriety drivers and software shims as Nvidia for example does they have done it the proper way by releasing a GPL driver that can then be included in the Linux kernel. 

It is no different from any hardware company the releases Linux GPL driver code so that their devices work "out of the box" on Linux. 

By the way this is not the first time that Microsoft has distributed software under the GPL v2

What about GPL 3?

---

### Post by andamaru on 2009-07-20
> **directhex said:**
> More or less, yes.

Then why is everyone worried about it :S I thought this was one of the things they had to do for Novell.

---

### Post by directhex on 2009-07-20
> **andamaru said:**
> Then why is everyone worried about it :S I thought this was one of the things they had to do for Novell.

Because TEH MICRO$HAFT. Naturally.

---

### Post by andrew.g on 2009-07-20
> **directhex said:**
> Because TEH MICRO$HAFT. Naturally.

You seem to trust Microsoft implicitly, anybody else wears tinfoil hats etc. But why should we trust Microsoft, you did not elaborate. What has changed?

---

### Post by andamaru on 2009-07-20
> **andrew.g said:**
> You seem to trust Microsoft implicitly, anybody else wears tinfoil hats etc. But why should we trust Microsoft, you did not elaborate. What has changed?

We aren't trusting Microsoft, this is just standard practice done by all other Visualization software.

---

### Post by Dr. C on 2009-07-20
> **andrew.g said:**
> What about GPL 3?

To my knowledge Microsoft has not admitted to distributing software under GPL v3; however there are those that argue that the Microsoft - Novell deal places Microsoft in the position of distributing GPL v3 code as more and more GPL v3 code is added to SUSE.

---

### Post by Mehall on 2009-07-20
> **FineE said:**
> To my knowledge Microsoft has not admitted to distributing software under GPL v3; however there are those that argue that the Microsoft - Novell deal places Microsoft in the position of distributing GPL v3 code as more and more GPL v3 code is added to SUSE.



GPLv3 cannot be used for linux kernel.

The kernel accepts ONLY GPLv2

---

### Post by directhex on 2009-07-20
> **andrew.g said:**
> You seem to trust Microsoft implicitly, anybody else wears tinfoil hats etc. But why should we trust Microsoft, you did not elaborate. What has changed?

I trust them to behave in a manner which helps their profits.

Competing with VMware helps their profits.

Better Linux support helps them compete with VMware.

Make sense?

---

### Post by andrew.g on 2009-07-20
> **andamaru said:**
> We aren't trusting Microsoft, this is just standard practice done by all other Visualization software.

Amazing how so many people here do!

---

### Post by DeadSuperHero on 2009-07-20
> **Mehall said:**
> GPLv3 cannot be used for linux kernel.

The kernel accepts ONLY GPLv2

True, but I'm pretty sure v3 code can ship alongside v2 code.

---

### Post by Merk42 on 2009-07-20
> **andrew.g said:**
> Amazing how so many people here do!

Correct me if I'm wrong, but isn't the GPL made in such a way that prevents the "Embrace Extended Extinguish" Microsoft is known for?
If that's the case how exactly can Microsoft turn this into something against Linux?

They did this to compete with *VMWare* not Linux.

Other that "but in the past..." can you please illustrate how this particular move is something sneaky against Linux?

---

### Post by Dr. C on 2009-07-20
> **Mehall said:**
> GPLv3 cannot be used for linux kernel.

The kernel accepts ONLY GPLv2

GPL v2 ***or later*** can be used but not GPL v3. I doubt Microsoft would include the "or later" clause

---

### Post by andrew.g on 2009-07-20
> **directhex said:**
> I trust them to behave in a manner which helps their profits.

Competing with VMware helps their profits.

Better Linux support helps them compete with VMware.

Make sense?

Indeed, I await the spin as to how this is beneficial to Linux etc? At the very least you where obvious and honest.

---

### Post by directhex on 2009-07-20
> **andrew.g said:**
> Indeed, I await the spin as to how this is beneficial to Linux etc? At the very least you where obvious and honest.

The only way to spin it as "good for Linux" is to (correctly) comment that it helps give Linux credibility to have even its biggest competitor writing code for it. But, as pointed out, Linux is being used to fight VMware - it's not an independent act of kindness

---

### Post by Sealbhach on 2009-07-20
That's if the code is going to be included at all. It would be great if Linus demanded to know what the 235 patents were before even considering adding any drivers from Micro$oft.

.

---

### Post by Merk42 on 2009-07-20
> **Sealbhach said:**
> That's if the code is going to be included at all. It would be great if Linus demanded to know what the 235 patents were before even considering adding any drivers from Micro$oft.

.

Why? Is he too worried about losing money to lawsuits?
MOER LIEK LINU$ AM I RITE? :rolleyes:

---

### Post by doas777 on 2009-07-20
this is pretty self serving of them, as all this will do, is allow their virtualization software to correctly host linux VMs, somthing the industry demands. if they want to compete with VM ware, then they have to be able to support Linux, especially in the server market, where *nix is still dominate. 

for instance my employeer is a MS shop plain and simple. if there is a MS product to fit the bill, we'll get it over the alternative (i'm trying to teach them, but...). We however choose wisely and selected VMware as our virtualization platform, even though we don't really need to virtualize anything but windows servers. now Im showing the head server admin how to un-tar.

---

### Post by pizza-is-good on 2009-07-20
> **Eisenwinter said:**
> Marketing technique. You'll see, they'll use this to screw Linux over somehow.
 
Lets hope not. But if microsoft is good with anything, it's marketing. So yeah, probably.....

---

### Post by andrew.g on 2009-07-20
> **directhex said:**
> The only way to spin it as "good for Linux" is to (correctly) comment that it helps give Linux credibility to have even its biggest competitor writing code for it. But, as pointed out, Linux is being used to fight VMware - it's not an independent act of kindness

I did pose a similar question to other supposed more enlightened souls. Their answer was along the lines of, and I'm paraphrasing,  "because Microsoft has our best interests at heart, they would never do us any harm.". I could not believe my ears.

These are people that could take my knowledge of modern computing and play conquers with it. I was more than a little disturbed. It does not pay to worship your idles.

---

### Post by dragos240 on 2009-07-20
> **motang said:**
> [Rest here]("http://www.networkworld.com/news/2009/072009-microsoft-linux-source-code.html")

This is huge, I really think Microsoft has turned for the better after Bill Gates left the company. I am extremely surprised with Windows 7, and they are starting to support other browsers (not by choice ;) ) with their web services, and I haven't heard any chair throwing stores lately. ;)

Gates left?

---

### Post by phrostbyte on 2009-07-20
> **doas777 said:**
> this is pretty self serving of them, as all this will do, is allow their virtualization software to correctly host linux VMs, somthing the industry demands. if they want to compete with VM ware, then they have to be able to support Linux, especially in the server market, where *nix is still dominate. 

for instance my employeer is a MS shop plain and simple. if there is a MS product to fit the bill, we'll get it over the alternative (i'm trying to teach them, but...). We however choose wisely and selected VMware as our virtualization platform, even though we don't really need to virtualize anything but windows servers. now Im showing the head server admin how to un-tar.

++

However...

Now that Microsoft is a Linux kernel developer and produces GPL code I think it makes it a little harder for them to spread FUD against Linux. I don't know if this was the most well thought out decision on their part. Maybe there are people who work at Microsoft who actually like open source and realize it's potential.

But whatever. I think this shows it's possible that we can push them to release more code as open source. :)

---

### Post by zekopeko on 2009-07-20
> **phrostbyte said:**
> ++

However...

Now that Microsoft is a Linux kernel developer and produces GPL code I think it makes it a little harder for them to spread FUD against Linux. I don't know if this was the most well thought out decision on their part. **Maybe there are people who work at Microsoft who actually like open source and realize it's potential**.

But whatever. I think this shows it's possible that we can push them to release more code as open source. :)

Microsoft is a company that has ~90 000 employees. It's certain that there are MS employees that like open source. Do note that they have an Open Source Division.

---

### Post by andrew.g on 2009-07-20
> **phrostbyte said:**
> ++

However...

Now that Microsoft is a Linux kernel developer and produces GPL code I think it makes it a little harder for them to spread FUD against Linux. I don't know if this was the most well thought out decision on their part. Maybe there are people who work at Microsoft who actually like open source and realize it's potential.

But whatever. I think this shows it's possible that we can push them to release more code as open source. :)

For all we love to hate Microsoft as this all encompassing entity that eats it's own and sacrifices it's unborn offspring to the God of "those that can guarantee me a full head of hair without an obvious transplant Ballmer",  has bad press. 

Microsoft is Green, Microsoft Cares.

---

### Post by phrostbyte on 2009-07-20
> **zekopeko said:**
> Microsoft is a company that has ~90 000 employees. It's certain that there are MS employees that like open source. Do note that they have an Open Source Division.

True, but typically these kinds of employees don't have enough power to make legal decisions on behalf of the company. :) We are talking about executive level people who might be open to open source. This is new. :P

---

### Post by Delever on 2009-07-20
> **phrostbyte said:**
> True, but typically these kinds of employees don't have enough power to make legal decisions on behalf of the company. :) We are talking about executive level people who might be open to open source. This is new. :P

I think this is simply business. They got additional feature which makes windows server better as virtualization host. They might as well produce some good publicity with that. Might counterweight publicity of next strategic action :P.

---

### Post by motang on 2009-07-20
> **phrostbyte said:**
>  Maybe there are people who work at Microsoft who actually like open source and realize it's potential.

[Sam Ramji]("http://www.linkedin.com/in/sramji") is one of those guys. :)

---

### Post by Old_Grey_Wolf on 2009-07-20
Rather than add something like VirtualBox's Guest Additions to Microsoft's Hyper-V, do they want to add bloatware to the Linux Kernel?

I couldn't determine what I would need to do to get the Linux drives if it is not included in the Linux Kernal.

Do I need to install the Microsoft Linux drivers myself if I want to run Linux on the Microsoft hypervisor, or do I install them similar to the way it is done to add the VirtualBox Guest Additions?

Just reading the recent articles, I seems they want it added to the Kernel. 20,000 lines of code added to the Kernel, s**t, that's a lot of code.

---

### Post by directhex on 2009-07-20
> **Old_Gray_Wolf said:**
> Rather than add something like VirtualBox's Guest Additions to Microsoft's Hyper-V, do they want to add bloatware to the Linux Kernel?

I couldn't determine what I would need to do to get the Linux drives if it is not included in the Linux Kernal.

Do I need to install the Microsoft Linux drivers myself if I want to run Linux on the Microsoft hypervisor, or do I install them similar to the way it is done to add the VirtualBox Guest Additions?

Just reading the recent articles, I seems they want it added to the Kernel. 20,000 lines of code added to the Kernel, s**t, that's a lot of code.

Actually, 20k isn't that big

As a comparison, 2.6.28's (it's what I had lying around!) DVB stack is 112kloc. The kernel-space Bluetooth stack is about 10kloc. Audio is about half a million.

And it's not necessarily stuff that a distro would include in a main kernel package - nor something that would be compiled in for everyone (that's what modules are for)

Frankly, it sounds MUCH better to me than the VMware route, given how often I find myself unable to use VMware as their crummy drivers don't support modern kernels

---

### Post by Old_Grey_Wolf on 2009-07-20
> **directhex said:**
> Actually, 20k isn't that big

I think of it as a death by a thousand cuts. 

Many commercial hardware vendors do not provide Linux drives for their hardware; therefore, Linux has to develop drivers for their hardware, and add them to the Kernel. Now Microsoft (granted they provided the drivers) wants Linux to added the drivers to the Kernel. 

Why is it that Linux has to bear the burden of COTS vendors not supporting Linux with drivers, or in this case, Microsoft not willing to fix it on their side of the interface?

---

### Post by directhex on 2009-07-20
> **Old_Gray_Wolf said:**
> I think of it as a death by a thousand cuts. 

Many commercial hardware vendors do not provide Linux drives for their hardware; therefore, Linux has to develop drivers for their hardware, and add them to the Kernel. Now Microsoft (granted they provided the drivers) wants Linux to added the drivers to the Kernel. 

Why is it that Linux has to bear the burden of COTS vendors not supporting Linux with drivers, or in this case, Microsoft not willing to fix it on their side of the interface?

I'm not entirely sure I understand the question

Why is Linux bearing a burden, here?

---

### Post by Methuselah on 2009-07-20
> **directhex said:**
> Actually, 20k isn't that big

As a comparison, 2.6.28's (it's what I had lying around!) DVB stack is 112kloc. The kernel-space Bluetooth stack is about 10kloc. Audio is about half a million.

And it's not necessarily stuff that a distro would include in a main kernel package - nor something that would be compiled in for everyone (that's what modules are for)

Frankly, it sounds MUCH better to me than the VMware route, given how often I find myself unable to use VMware as their crummy drivers don't support modern kernels

I agree with this.
That's what we have been screaming about for so long, for drivers to be open sourced so they can be in the kernel and properly maintained.

---

### Post by zekopeko on 2009-07-20
> **directhex said:**
> I'm not entirely sure I understand the question

Why is Linux bearing a burden, here?

The poster thinks that MS is shifting the burden of code maintenance to the Linux kernel. and as the post above said it: that's what we (we being the Kernel Community) want. That way you can be sure that the particular driver will work between different kernels.

@Old_Gray_Wolf

You won't need to install the drivers if your distro compiles them in-kernel or by way of module. It will "Just Work(TM)".
The Virtualbox/VMware route is far more sucky in this regard.

EDIT: oh and the drivers are already in one of the kernel branches waiting to be merged in mainline.

---

### Post by MikeTheC on 2009-07-21
I don't believe a leopard changes its spots. When Microsoft completely changes all of its business practices and doesn't screw another single human being for the rest of its existence or the rest of my life (whichever comes first) then, the last day of my life (or the last day of Microsoft's) I'll believe they've changed. Not before.

---

### Post by phrostbyte on 2009-07-21
> **zekopeko said:**
> The poster thinks that MS is shifting the burden of code maintenance to the Linux kernel. and as the post above said it: that's what we (we being the Kernel Community) want. That way you can be sure that the particular driver will work between different kernels.

@Old_Gray_Wolf

You won't need to install the drivers if your distro compiles them in-kernel or by way of module. It will "Just Work(TM)".
The Virtualbox/VMware route is far more sucky in this regard.

EDIT: oh and the drivers are already in one of the kernel branches waiting to be merged in mainline.

I don't think they'll get merged into mainline until 2.6.31 is marked stable and work begins on 2.6.32.

This embrace-extend-extinguish was great in the 90s, but the idea will only get them into trouble today. Also, they picked a terrible license to use if that is their ultimate plan. It can be argued that they just inadvertently gave a patent grant to the Linux kernel (GPLv2 contains such patent provisions).

I don't think their motives are very evil (or intelligent) to be honest.

---

### Post by Methuselah on 2009-07-21
> 
Also, they picked a terrible license to use if that is their ultimate plan. It can be argued that they just inadvertently gave a patent grant to the Linux kernel (GPLv2 contains such patent provisions).


I thought of this too.
You don't contribute to infringing software if you want to bolster your case down the road.

---

### Post by LIB53 on 2009-07-21
I was reading tech news just like any other geek, and i found [this particular article]("http://www.informationweek.com/news/software/open_source/showArticle.jhtml?articleID=218501447") very interesting. Does anyone find it a bit weird that Microsoft is contributing to Linux?:confused:

---

### Post by SuperSonic4 on 2009-07-21
Not any more, I've long stopped caring and just used whatever works best for me

---

### Post by Swagman on 2009-07-21
About as odd as this article

[http://www.theregister.co.uk/2009/07/21/microsoft_gpl_office_server/](http://www.theregister.co.uk/2009/07/21/microsoft_gpl_office_server/)

or

[http://www.theregister.co.uk/2009/07/20/microsoft_windows_drivers_linux/](http://www.theregister.co.uk/2009/07/20/microsoft_windows_drivers_linux/)

---

### Post by LIB53 on 2009-07-21
> **Swagman said:**
> About as odd as this article

[http://www.theregister.co.uk/2009/07/21/microsoft_gpl_office_server/](http://www.theregister.co.uk/2009/07/21/microsoft_gpl_office_server/)

or

[http://www.theregister.co.uk/2009/07/20/microsoft_windows_drivers_linux/](http://www.theregister.co.uk/2009/07/20/microsoft_windows_drivers_linux/)

The second article pretty much sums up the motive. But that stills means that they obviously aren't going to do anything for desktop linux, so i don't think it's actually a big deal after reading about how it's aimed at keeping Windows Servers going. I mean, will any of that open code help with the Wine project at any rate?

---

### Post by doas777 on 2009-07-21
basically MS's virtualization software can't run linux guest OS's without this code, so they contributed it. the industry demands that virtualization platforms support linux, and at this very second their virtualization software supports only windows.

their just trying to level the playing feild with VMWare and VBox

---

### Post by shredkingj on 2009-07-21
Exactly, they don't want enterprises to have an excuse to not use HyperV for VMWare.  Microsoft is just doing what they have to, to take out VMWare.

---

### Post by bodhi.zazen on 2009-07-21
> **LIB53 said:**
> I was reading tech news just like any other geek, and i found [this particular article]("http://www.informationweek.com/news/software/open_source/showArticle.jhtml?articleID=218501447") very interesting. Does anyone find it a bit weird that Microsoft is contributing to Linux?:confused:

Threads merged. Please do not start multiple threads on the same topic (this is the third thread on the same topic in about 24 hours).

---

### Post by Sporkman on 2009-07-21
> **Meet Microsoft, the Linux Developer**

By Anders Bylund
July 21, 2009

With sufficient thrust, pigs fly just fine. And so it is that Microsoft (Nasdaq: MSFT) has submitted a big chunk of code to the open-sourced Linux kernel.

When compiled, the 20,000 lines of fresh code power Microsoft's Linux Integration Components, a toolkit that has been available for some time. The programs help Linux operating systems run faster and smoother inside Mr. Softy's virtual server environments. The fact that compiled modules have been available to do this job for months doesn't in any way lessen one simple and powerful takeaway from this announcement:

Microsoft takes Linux seriously. I mean, *really* seriously...

[http://www.fool.com/investing/value/2009/07/21/meet-microsoft-the-linux-developer.aspx](http://www.fool.com/investing/value/2009/07/21/meet-microsoft-the-linux-developer.aspx)

---

### Post by dragos240 on 2009-07-21
Already a topic.

---

### Post by .Maleficus. on 2009-07-21
There's a mega-thread of 4 merged topics on this already.

---

### Post by bodhi.zazen on 2009-07-21
> **.maleficus. said:**
> there's a mega-thread of 4 merged topics on this already.


5

---

### Post by froggyswamp on 2009-07-22
I'm wondering what Linus thinks about it. (He once said like: the day MS creates software for Linux he wins - does he think now he won?).

---

### Post by clanky on 2009-07-22
> **Sealbhach said:**
> I don't regard boycottnovell as conspiracy nuts, most of their articles are well referenced and well worth a read. 

.

I LOL'd

---

### Post by directhex on 2009-07-22
> **clanky said:**
> I LOL'd

They're very well referenced. Problem is 95% of those references are to other BN articles. Recursion isn't always a good thing.

---

### Post by froggyswamp on 2009-07-22
Their articles are  indeed well referenced (not perfect, nothing is perfect), much better than Microsoft's "get the facts", and I know there are many people who don't like when somebody is showing the exhibits from lawsuits - something that corporations a la Microsoft aren't comfortable with and of course they have to regard them as "nonsense" and "conspiracy".

---

### Post by Icehuck on 2009-07-22
> **froggyswamp said:**
> Their articles are  indeed well referenced (not perfect, nothing is perfect), much better than Microsoft's "get the facts", and I know there are many people who don't like when somebody is showing the exhibits from lawsuits - something that corporations a la Microsoft aren't comfortable with and of course they have to regard them as "nonsense" and "conspiracy".

I want whatever your smoking, because it must be some potent stuff to be able to see BN as a positive creditable site.

---

### Post by Methuselah on 2009-07-22
> 
I want whatever your smoking, because it must be some potent stuff to be able to see BN as a positive creditable site.


This doesn't address issues.
I don't know enough about BoycottNovell to make a judgment but the poster you replied to made an effort to explain why he thought BN was credible.
You did not do likewise for your assertion that it isn't.

This is what frequently annoyed me about the pro-Mono side of the Mono debates as well.
Quite frequently arguments against Mono would be presented and the Mono side would respond with claims of 'FUD!' etc. without addressing the issues raised.

I don't mean to pick on you as you're not the only offender.
However, I've heard many comments made against this site and never heard strong justifications for any of them.
Could the site's detractors be guilty of the same tactics they accuse it of?

---

### Post by RiceMonster on 2009-07-22
> **Methuselah said:**
> This doesn't address issues.
I don't know enough about BoycottNovell to make a judgment but the poster you replied to made an effort to explain why he thought BN was credible.
You did not do likewise for your assertion that it isn't.

This is what frequently annoyed me about the pro-Mono side of the Mono debates as well.
Quite frequently arguments against Mono would be presented and the Mono side would respond with claims of 'FUD!' etc. without addressing the issues raised.

I don't mean to pick on you as you're not the only offender.
However, I've heard many comments made against this site and never heard strong justifications for any of them.
Could the site's detractors be guilty of the same tactics they accuse it of?

Neither side provided evidence. How is saying "they're very well refferenced" or "they're better than Microsoft's 'get the facts' ads" any more credible than "They're very well referenced. Problem is 95% of those references are to other BN articles. Recursion isn't always a good thing." or even what Icehuck said?

---

### Post by directhex on 2009-07-22
> **RiceMonster said:**
> Neither side provided evidence. How is saying "they're very well refferenced" or "they're better than Microsoft's 'get the facts' ads" any more credible than "They're very well referenced. Problem is 95% of those references are to other BN articles. Recursion isn't always a good thing." or even what Icehuck said?

Monolith alert! Back on topic, ladies & gents, before the thread merges come for you

---

### Post by Icehuck on 2009-07-22
> **Methuselah said:**
> This doesn't address issues.
I don't know enough about BoycottNovell to make a judgment but the poster you replied to made an effort to explain why he thought BN was credible.
You did not do likewise for your assertion that it isn't.

This is what frequently annoyed me about the pro-Mono side of the Mono debates as well.
Quite frequently arguments against Mono would be presented and the Mono side would respond with claims of 'FUD!' etc. without addressing the issues raised.

I don't mean to pick on you as you're not the only offender.
However, I've heard many comments made against this site and never heard strong justifications for any of them.
Could the site's detractors be guilty of the same tactics they accuse it of?

There was an argument on digg where someone from boycott novell said it was better to let people die then take charity from Microsoft.  

Then there was the fiasco involving Roy and Ubuntu(I'm not getting banned, or the thread locked, google if you want to know more.)

You still want me to say that they are a creditable source?  

For the record I don't care about GPL or non GPL. I have better things to do in my life then worry about software.

---

### Post by bodhi.zazen on 2009-07-22
> **directhex said:**
> Monolith alert! Back on topic, ladies & gents, before the thread merges come for you

Merging this thread into Monolith is worth considering 

Thank you for the suggestion. =)

---

### Post by directhex on 2009-07-22
> **bodhi.zazen said:**
> Merging this thread into Monolith is worth considering 

Thank you for the suggestion. =)

I'd rather you didn't, given the option. It's a different topic.

Use the little "Move Posts" option under the Moderation menu, to shift the off-topic bits, if you want to move them

---

### Post by Sealbhach on 2009-07-22
> **directhex said:**
> They're very well referenced. Problem is 95% of those references are to other BN articles. Recursion isn't always a good thing.

Well yes, that's a fact but I do find links now and again to interesting articles. I like their stuff about editing of Wikipedia by Microsoft perception management activists, the Comes v Microsoft stuff, Waggoner Edstrom activities... it's all stuff I had never heard about. 

To write it all off as "conspiracy theory nuttiness" is a mistake, I think. As for the mono debate and all that, I don't really care, it doesn't bother me.

.

---

### Post by bodhi.zazen on 2009-07-22
> **directhex said:**
> It's a different topic.

So long as the conversation stays on topic, yes they are somewhat different.

As Pink floyd said -

> [FONT=Verdana][SIZE=5][FONT=Verdana][SIZE=2]Running over the same old ground. 
What have you found? The same old fears.

Wish you were here[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by directhex on 2009-07-22
> **bodhi.zazen said:**
> 
As Pink floyd said -

[/SIZE][/FONT][/SIZE][/FONT]

Ah, but they ALSO said:

> I know a mouse
And he hasn't got a house
I don't know why
I call him Gerald
He's getting rather old
But he's a good mouse 

Think about that.

---

### Post by andrew.g on 2009-07-22
> **directhex said:**
> Ah, but they ALSO said:

I know a mouse
And he hasn't got a house
I don't know why
I call him Gerald
He's getting rather old
But he's a good mouse                      

Think about that.

Was that not Syd Barret's composition?
 
They didn't do too bad without Syd as I recall. Though his passing is a great loss and regrettable.

---

### Post by bryncoles on 2009-07-23
this thread is an unweildy monolith! which i cant quite be bothered to trawl through, so apologies if [this]("http://www.theregister.co.uk/2009/07/23/microsoft_hyperv_gpl_violation/") has been seen already: 

> As revealed by Stephen Hemminger - a principal engineer with open-source network vendor Vyatta - a network driver in Microsoft's Hyper-V used open-source components licensed under the GPL and statically linked to binary parts. The GPL does not permit the mixing of closed and open-source elements.

> Hemminger said he uncovered the apparent violation and contacted Linux Driver Project lead Greg Kroah-Hartman, a Novell programmer, to resolve the problem quietly with Microsoft. Hemminger apparently hoped to leverage Novell's interoperability relationship with Microsoft.

> Neither Kroah-Hartman nor Microsoft spoke of a potential problem when announcing the code drop on Monday. Quite the opposite. Microsoft presented its embrace of the GPL as something it had done to help customers reduce the cost of deploying and managing their IT infrastructure through server consolidation, by speeding the performance of Linux on Hyper-V.

so, the release of GPL code seems to be not out of the goodness of Microsofts Cold Black Heart (tm), but because they had violated the GPL, and didnt want to get sued. which is fair enough, as that would be very embarrassing for Microsoft. naughty them for claiming it was a magnanimous act though!

---

### Post by praveesh on 2009-07-23
Why don't they release the drivers seperately without being included in the kernel? . Some thing similar to vmware guest addons. Thats what I don't understand

---

### Post by directhex on 2009-07-23
> **praveesh said:**
> Why don't they release the drivers seperately without being included in the kernel? . Some thing similar to vmware guest addons. Thats what I don't understand

Competing on the basis of ease of use.

If you're virtualizing 1000 machines, and using ESXi requires you to run an install script on every client, and HyperV doesn't, then MS can sell that missing step as making the whole thing easier for admins.

---

### Post by doas777 on 2009-07-23
ahhh Mystery solved:

[http://www.theregister.co.uk/2009/07/23/microsoft_hyperv_gpl_violation/](http://www.theregister.co.uk/2009/07/23/microsoft_hyperv_gpl_violation/)

appearently, if they didn't donate the code, they would be in violation if they included their own closed source interfaces for the drivers.

---

### Post by directhex on 2009-07-23
> **doas777 said:**
> ahhh Mystery solved:

[http://www.theregister.co.uk/2009/07/23/microsoft_hyperv_gpl_violation/](http://www.theregister.co.uk/2009/07/23/microsoft_hyperv_gpl_violation/)

appearently, if they didn't donate the code, they would be in violation if they included their own closed source interfaces for the drivers.

They could still have released them, under GPLv2, in their own way (e.g. a zip file with no instructions)

I'm not surprised by the background detail, but it's still worth noting that there were no legal obligations to submit code towards the mainline kernel rather than as its own tarball.

---

### Post by benj1 on 2009-07-23
> **directhex said:**
> They could still have released them, under GPLv2, in their own way (e.g. a zip file with no instructions)

I'm not surprised by the background detail, but it's still worth noting that there were no legal obligations to submit code towards the mainline kernel rather than as its own tarball.

true but then someone could just have taken the code and added it to the kernel, at least this way microsoft got to look like a mature and reasonable company for 5 minutes

---

### Post by uberdonkey5 on 2009-07-23
> **Chemical Imbalance said:**
> Beat me to it.  Was just about to post the same thing.

This is mind-boggling.  ...And really cool.

There, of course, has to be ulterior motives however.  Microsoft *is* a business.

Yeh, and really for 'users' its got to be good news. If more people start using linux (even as virtual software) people will become more aware of it, and more hardware support and software will be more available.

Once people then think, hang-on, I use nothing in windows anymore... they will scrap virtualisation. However, for those that still want to pay for it, they have a choice!

Wow... we are really sitting on the brink of a real change in the way people will pay for and use software.

---

### Post by bryonak on 2009-07-23
@who moved this to recurring discussions: How the hell do you justify this thread being recurring? An explanation would be nice.

Seems to me that some mods are quite touchy about anything remotely Microsoft related... especially as soon as the facts turn against the corporation, since this thread was shedding a favourable light on Microsoft for 2 days in the Cafe, but got moved within hours after revealing the fallacy.

On topic, it's a perfectly sensible business decision: since they have to release the code, why not boost their PR in the process...
I think it will benefit them outside of the FOSS community because people not following the issue closely (= most) see that they're cooperating.
As for us, many will perceive it as another "attempt at cheating" (they have violated the GPL after all), though this one isn't by far as grave as most of the others.

---

### Post by heyyy on 2009-07-23
well..pigs do fly after all..

---

### Post by donkyhotay on 2009-07-23
Looks like the start of an attempt to kill open source VM's. Give a little bit of open source code in order to improve their proprietary product and then kill the open source version once they have enough market share.

---

### Post by directhex on 2009-07-23
> **donkyhotay said:**
> Looks like the start of an attempt to kill open source VM's. Give a little bit of open source code in order to improve their proprietary product and then kill the open source version once they have enough market share.

I think VMware is the bigger worry

---

### Post by directhex on 2009-07-23
> **doas777 said:**
> ahhh Mystery solved:

[http://www.theregister.co.uk/2009/07/23/microsoft_hyperv_gpl_violation/](http://www.theregister.co.uk/2009/07/23/microsoft_hyperv_gpl_violation/)

appearently, if they didn't donate the code, they would be in violation if they included their own closed source interfaces for the drivers.

Something concerns me about El Reg's story - I took a look at the "Linux Integration Components" download, and can't actually see anything out of the ordinary. Supplying a mix of source and object files is normal - companies like Highpoint do it all the time - and the GPL allows you to distribute that kind of thing fine. What you may NOT do is distribute any compiled combined result from mixing GPL and non-GPL source - and I don't see any such mix in the Linux IC download.

---

### Post by markbuntu on 2009-07-23
The big problem is that at any time ( like when they get vmware on the ropes) Microsoft could just update their software so the gpl drivers will not work anymore or change their side so the drivers slowly deteriorate. Then all the people running linux virtual machines on their ware would be forced to buy new Microsoft proprietary drivers to get decent performance. 

They do this all the time, changing the api just enough and often enough so devs writing products that compete with MS products are unable to keep up. It got so bad with NT that the EU froze the code.

This is just a huge trap.

---

### Post by RiceMonster on 2009-07-23
> **markbuntu said:**
> The big problem is that at any time ( like when they get vmware on the ropes) Microsoft could just update their software so the gpl drivers will not work anymore or change their side so the drivers slowly deteriorate. Then all the people running linux virtual machines on their ware would be forced to buy new Microsoft proprietary drivers to get decent performance. 

They do this all the time, changing the api just enough and often enough so devs writing products that compete with MS products are unable to keep up. It got so bad with NT that the EU froze the code.

This is just a huge trap.

Or, they could just switch to VMware.

---

### Post by CJ Master on 2009-07-23
> **markbuntu said:**
> The big problem is that at any time ( like when they get vmware on the ropes) Microsoft could just update their software so the gpl drivers will not work anymore or change their side so the drivers slowly deteriorate. Then all the people running linux virtual machines on their ware would be forced to buy new Microsoft proprietary drivers to get decent performance. 

They do this all the time, changing the api just enough and often enough so devs writing products that compete with MS products are unable to keep up. It got so bad with NT that the EU froze the code.

This is just a huge trap.

[img]http://downlode.org/Creative/Writing/Notebook/Illustrations/itsatrap.jpg[/img]

---

### Post by directhex on 2009-07-23
> **CJ Master said:**
> [img]http://downlode.org/Creative/Writing/Notebook/Illustrations/itsatrap.jpg[/img]

[img]http://img.photobucket.com/albums/v220/elf_of_doriath9/non-icon%20randomness/its_a_tarp.gif[/img]

---

### Post by fakewcfrog on 2009-07-23
Yeah, I think Microsoft is being suspiciously nice here. There have GOT to be some strings attached.

---

### Post by Chame_Wizard on 2009-07-24
Seems like there is more than meets the eyes.:P

---

### Post by zekopeko on 2009-07-24
Here is a nice quote from Linus Torvalds on the issue:

> I agree that it's driven by selfish reasons, but that's how all open source code gets written! We all "scratch our own itches". It's why I started Linux, it's why I started git, and it's why I am still involved. It's the reason for everybody to end up in open source, to some degree.
So complaining about the fact that Microsoft picked a selfish area to work on is just silly. Of course they picked an area that helps them. That's the point of open source - the ability to make the code better for your particular needs, whoever the 'your' in question happens to be.

Does anybody complain when hardware companies write drivers for the hardware they produce? No. That would be crazy. Does anybody complain when IBM funds all the POWER development, and works on enterprise features because they sell into the enterprise? No. That would be insane.

So the people who complain about Microsoft writing drivers for their own virtualization model should take a long look in the mirror and ask themselves why they are being so hypocritical.

---

### Post by bryonak on 2009-07-25
@zekopeko:
I don't think you hit the topic.
People are not complaining about Microsoft releasing GPL'd code... that would be silly, don't you think?
People are complaining about being deceived by Microsoft, who portray their release as an icebreaking act of pure benevolence while they only do it because they are forced to (and after the violation happened, though that might be a honest error).

Also I think Torvalds is wrong on the "scratching ones itch" issue.
Sure it's the reason why many developers who believe in FOSS contribute to projects.
But today by far most GNU/Linux users don't go around fixing bugs that bother them or implementing features. It's a reality we have to adapt to.
Comparatively (in relative terms, not absolute) few Ubuntu (for example) users are "scratching their itch" in the Torvalds-sense.
*But not only code writers have the right to complain.*

Besides, valid reasons for contributing are also:
Not wanting to be plagued by malware / bloatware / dubious corporate decisions anymore -> using and advocating another OS by holding the opinion that "it's better".
Finding the associated idea of freedom fascinating and getting motivated to further it -> both code and non-code contributions.
Feeling the obligation to give back after having used so much free software -> helping out in some way.
Wanting to improve one's coding skills, or have a nice CV entry -> joining some project.

For example, the first three apply to myself before I started "scratching my itches" in terms of fixing bugs/missing features/missing applications ;)

---

### Post by directhex on 2009-07-25
> **bryonak said:**
> @zekopeko:
I don't think you hit the topic.
People are not complaining about Microsoft releasing GPL'd code... that would be silly, don't you think?
People are complaining about being deceived by Microsoft, who portray their release as an icebreaking act of pure benevolence while they only do it because they are forced to (and after the violation happened, though that might be a honest error).

Also I think Torvalds is wrong on the "scratching ones itch" issue.
Sure it's the reason why many developers who believe in FOSS contribute to projects.
But today by far most GNU/Linux users don't go around fixing bugs that bother them or implementing features. It's a reality we have to adapt to.
Comparatively (in relative terms, not absolute) few Ubuntu (for example) users are "scratching their itch" in the Torvalds-sense.
*But not only code writers have the right to complain.*

Besides, valid reasons for contributing are also:
Not wanting to be plagued by malware / bloatware / dubious corporate decisions anymore -> using and advocating another OS by holding the opinion that "it's better".
Finding the associated idea of freedom fascinating and getting motivated to further it -> both code and non-code contributions.
Feeling the obligation to give back after having used so much free software -> helping out in some way.
Wanting to improve one's coding skills, or have a nice CV entry -> joining some project.

For example, the first three apply to myself before I started "scratching my itches" in terms of fixing bugs/missing features/missing applications ;)

"GPL violation" debunked. Now aren't we feeling silly.

[http://www.h-online.com/open/Microsoft-and-Vyatta-rebutt-reports-of-GPL-violation--/news/113837](http://www.h-online.com/open/Microsoft-and-Vyatta-rebutt-reports-of-GPL-violation--/news/113837)

---

### Post by bryonak on 2009-07-25
> **directhex said:**
> "GPL violation" debunked.

You know that three major tech news sites reporting an issue (and Slashdot parroting it ;)) will be a strong opinion former.
You can't blame people for commenting to the best of their knowledge on what seems genuine news.

Then again, I actually can't see the claim being debunked. The violation was there, nobody said anything to the contrary.
The source was released *after* Hemminger contacted Novell.. now they might have already planned to release it, talk about strangely coincidential timing...
Yet the only thing Ramji does to is emphasize that they did it mainly for the good of the customers, community and everybody in general.

I can't help but feeling taken for a ride if I were to believe that (it would have been much more convincing if there were no violation to begin with).
You make of it what you want.


> **directhex said:**
> 
Now aren't we feeling silly.
If you refer to me personally, no why? Is there a reason?


*EDIT*
Ah I see... I've just read the Microsoft announcement before.
The Vyatta people are sending mixed signals, while the last news from Novell doesn't deny violations AFAIK.
Well, I guess we have to wait and see how this turns out.

---

### Post by directhex on 2009-07-25
> **bryonak said:**
> You know that three major tech news sites reporting an issue (and Slashdot parroting it ;)) will be a strong opinion former.
You can't blame people for commenting to the best of their knowledge on what seems genuine news.

Then again, I actually can't see the claim being debunked. The violation was there, nobody said anything to the contrary.
The source was released *after* Hemminger contacted Novell.. now they might have already planned to release it, talk about strangely coincidential timing...
Yet the only thing Ramji does to is emphasize that they did it mainly for the good of the customers, community and everybody in general.

I can't help but feeling taken for a ride if I were to believe that (it would have been much more convincing if there were no violation to begin with).
You make of it what you want.

There was insufficient evidence in the original reports to support claims of "gpl infringement", and all reports were essentially rewritings of the same sparse blog post.

I did an analysis myself, on the basis that i found it highly unlikely that microsoft would be distributing (illegally) .ko files rather than a GPL-compatible .o/.c mix, as most vendors such as NVIDIA or ATI or Highpoint do, and as it turns out they were (and whilst i missed the EXPORT_SYMBOL_GPL thing, this would be known as being a ******* & working around the kernel, something others have done before, and NOT a violation of the license). It would ALSO be very strange for them to still be distributing their "violating" package if they were concerned about legalities ([http://www.microsoft.com/downloads/details.aspx?FamilyID=AB7F4983-93C5-4A70-8C79-0642F0D59EC2](http://www.microsoft.com/downloads/details.aspx?FamilyID=AB7F4983-93C5-4A70-8C79-0642F0D59EC2))

If nothing else, distributing .ko files, as well as violating the GPL, would be more work for Microsoft (who would need to update their release for every kernel update of every supported distro), and I simply didn't think this was a likely scenario.

I posted a detailed analysis to one of the blogs talking about this topic on Planet Ubuntu, but the author's seemingly decided not to allow it past moderation because it makes him look silly.

> **bryonak said:**
> If you refer to me personally, no why? Is there a reason?

I refer to pretty much every single news site & blog reporting the "GPL violation" story as fact *without verifying the information or doing any journalism*.

---

### Post by bryonak on 2009-07-25
> **directhex said:**
> There was insufficient evidence in the original reports to support claims of "gpl infringement", and all reports were essentially rewritings of the same sparse blog post.

I did an analysis myself, on the basis that i found it highly unlikely that microsoft would be distributing (illegally) .ko files rather than a GPL-compatible .o/.c mix, as most vendors such as NVIDIA or ATI or Highpoint do, and as it turns out they were (and whilst i missed the EXPORT_SYMBOL_GPL thing, this would be known as being a ******* & working around the kernel, something others have done before, and NOT a violation of the license). It would ALSO be very strange for them to still be distributing their "violating" package if they were concerned about legalities ([http://www.microsoft.com/downloads/details.aspx?FamilyID=AB7F4983-93C5-4A70-8C79-0642F0D59EC2](http://www.microsoft.com/downloads/details.aspx?FamilyID=AB7F4983-93C5-4A70-8C79-0642F0D59EC2))

If nothing else, distributing .ko files, as well as violating the GPL, would be more work for Microsoft (who would need to update their release for every kernel update of every supported distro), and I simply didn't think this was a likely scenario.

I posted a detailed analysis to one of the blogs talking about this topic on Planet Ubuntu, but the author's seemingly decided not to allow it past moderation because it makes him look silly.


Ah good thing we have people like you digging deep into the issue. Thanks for the information :)

I'm curious how this turns out, since refuting news goes back and forth.
Time will tell though.

About your analysis... maybe you could work on the wording to make it less disparaging for that person?
Or post it here?

---

### Post by zekopeko on 2009-07-25
> **directhex said:**
> I posted a detailed analysis to one of the blogs talking about this topic on Planet Ubuntu, but the author's seemingly decided not to allow it past moderation because it makes him look silly..

Well considering that there is only one blog post on the planet..."pot calling the kettle black" comes to mind.

---

### Post by Merk42 on 2009-07-25
> **markbuntu said:**
> The big problem is that at any time ( like when they get vmware on the ropes) Microsoft could just update their software so the gpl drivers will not work anymore or change their side so the drivers slowly deteriorate. Then all the people running linux virtual machines on their ware would be forced to buy new Microsoft proprietary drivers to get decent performance.

As was said before, the user could just switch to VMWare, who Microsoft is targeting with this move, not Linux.

That aside how would your theory even work exactly?

In order to update the drivers wouldn't they have to be submitted into the kernel? If so, why wouldn't the older drivers remain?

---

### Post by markbuntu on 2009-07-25
Once the windows virtual machine is embedded deep enough in an enterprise, just switching to vmware would become extremely difficult, disruptive and expensive.

The drivers would not need to be updated and would remain but they would have nothing to drive if ms decides to move away from them. It is no different than hardware drivers.

And yes, vmware is the current target, but not the only one.

---

### Post by Sef on 2009-07-25
The Register has another article: [Microsoft GPL Violation]("http://www.theregister.co.uk/2009/07/23/microsoft_open_source_science/").

---

### Post by directhex on 2009-07-25
> **Sef said:**
> The Register has another article: [Microsoft GPL Violation]("http://www.theregister.co.uk/2009/07/23/microsoft_open_source_science/").

Yet more reposting of Hemminger's blog post without due analysis, though

If what Microsoft did isn't allowed, then neither are the ATI/Nvidia drivers which do the same thing (ship source plus closed .o files)

---

### Post by MikeTheC on 2009-07-25
Of course, at this point I feel Microsoft itself shouldn't be allowed, let alone anything they happen to do during the time they continue to exist. ;)

---

### Post by Ravernomina on 2009-07-25
Personally i believe this is the beginning of something very bad..

I think MS is trying to Patent the Linux Kernel and its source codes....

Once they do this they could stop Linux for good and any 1 trying to build a Linux kernel would well Sued.

And MS could probably do this because of all the layers... Money... And support as well

So i think this is just a test to see if it would be worth it or not by customer demand of LINUX.

Anyway if MS released a MS only kernel or took control they would lose probably half their money from people Leaving by how bad it is...

Thats my theory :l

---

### Post by Merk42 on 2009-07-25
> **markbuntu said:**
> Once the windows virtual machine is embedded deep enough in an enterprise, just switching to vmware would become extremely difficult, disruptive and expensive.

The drivers would not need to be updated and would remain but they would have nothing to drive if ms decides to move away from them. It is no different than hardware drivers.

And yes, vmware is the current target, but not the only one.

So they would update their software that intentionally breaks the very reason people bought it??

I still don't see how this particular action is something targeting Linux.

> **Ravernomina said:**
> Personally i believe this is the beginning of something very bad..

I think MS is trying to Patent the Linux Kernel and its source codes....

Um, they can't, that's the point of GPL.

---

### Post by directhex on 2009-07-26
> **Ravernomina said:**
> Personally i believe this is the beginning of something very bad..

I think MS is trying to Patent the Linux Kernel and its source codes....

Once they do this they could stop Linux for good and any 1 trying to build a Linux kernel would well Sued.

Go look up the word "estoppel"

---

### Post by bryonak on 2009-07-28
Back and forth we go, back and forth...
A recent article about how the Software Freedom Law Center holds the [opinion]("http://www.sdtimes.com/link/33641") that Microsoft indeed violated the GPL.
Although no actual news there...

Microsoft's current main foothold is the claim that they planned to release the source all along, even months *before* they were notified of the violation. It took them 5 months after the notification.


I'm not into this enough to do the research myself, but the question whether Microsoft's actions fall into the "violation" or just the "being rude/circumventing conventions" categories seems fine grained enought to require precise assessment.

---

### Post by directhex on 2009-07-28
> **bryonak said:**
> Back and forth we go, back and forth...
A recent article about how the Software Freedom Law Center holds the [opinion]("http://www.sdtimes.com/link/33641") that Microsoft indeed violated the GPL.
Although no actual news there...

Microsoft's current main foothold is the claim that they planned to release the source all along, even months *before* they were notified of the violation. It took them 5 months after the notification.


I'm not into this enough to do the research myself, but the question whether Microsoft's actions fall into the "violation" or just the "being rude/circumventing conventions" categories seems fine grained enought to require precise assessment.

The only way the SFLC analysis makes any sense is if you add this statement: "The binary-only components, blkvsc.i386 and so on, are GPL-licensed files for which the source is not provided". They're talking rubbish if you use this statement instead: "The binary-only components, blkvsc.i386 and so on, are under a proprietary license of some kind"

Pick your preferred statement

---

### Post by ToFue on 2009-08-14
This was announced at a recent MS conference I was working, and was wondering if anyone had more news on it: That MS has (or is going to) release their source code for GPL of their generic drivers to 'kernel.org?' in an effort to make virtualizing Linux more compatible for 'cloud computing' and azure and stuff.. 

   I haven't seen or read anything about it since hearing the announcement at the conference. Does anyone know anything about this? What would the impact (if any) be for Linux?

---

### Post by Tibuda on 2009-08-14
Old news.
[http://ubuntuforums.org/showthread.php?t=1218266](http://ubuntuforums.org/showthread.php?t=1218266)

---

### Post by pizmooz on 2009-08-14
From googling around a bit it looks like they are GPLing their
Hyper-V Linux Integration Components.  These are akin to vmware's vmware-tools a collection of linux modules which allows for a binary interface between the hypervisor and the VM.  Basically MS had no choice but to make these components GPL, unless the want to 'taint' the linux kernel.  I really don't view this as embracing the GPL but more complying, so that the can have a chance with there virtualization product Hyper-V (which sucks IMHO).

---

### Post by Revolutionary101 on 2009-08-14
I don't understand why MS is doing this because they are basically giving ammo to their competitors.

---

### Post by Tibuda on 2009-08-15
> **Revolutionary101 said:**
> I don't understand why MS is doing this because they are basically giving ammo to their competitors.

No, these drivers are to improve Linux performance in Microsoft virtualization software.

---

### Post by Revolutionary101 on 2009-08-15
> **danielrmt said:**
> No, these drivers are to improve Linux performance in Microsoft virtualization software.

Thanks for making me understand.

---

