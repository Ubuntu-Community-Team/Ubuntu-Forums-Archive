---
title: "Netflix streaming on Linux?!"
date: 2009-03-09
forum: Recurring Discussions
---

### Post by davidryder on 2009-03-09
I got past the version check, and have [Moonlight](http://www.mono-project.com/Moonlight) (open source silverlight alternative) but I get a message saying Silverlight is not installed :( 

Does anyone have any ideas?

By the way, I used a Firefox plug-in called [Modify Headers](https://addons.mozilla.org/en-US/firefox/addon/967) to get past the OS check at Netflix.

Type: Modify
Name: User-Agent
Value: Mozilla/5.0 (compatible; MSIE 7.0; Windows NT 6.0)

I feel I am soooo close!

---

### Post by directhex on 2009-03-09
Netflix needs SL2 support, your Moonlight package only supports SL1 at the moment.

---

### Post by davidryder on 2009-03-09
Ahhh! Thanks for the reply :) Hopefully SL2 comes to Moonlight soon...

EDIT: [http://www.mono-project.com/Other_Downloads](http://www.mono-project.com/Other_Downloads)

According to that page the version # is > 2; does that correspond to the SL version also? I enabled the badgerports repo and it installed 1.9xx...

---

### Post by directhex on 2009-03-09
> **davidryder said:**
> Ahhh! Thanks for the reply :) Hopefully SL2 comes to Moonlight soon...

[http://www.mono-project.com/Roadmap#Upcoming_Releases](http://www.mono-project.com/Roadmap#Upcoming_Releases)

September for beta support for SL2

Which means a big fat MAYBE for Karmic - depending on how much love I get from the release managers

---

### Post by davidryder on 2009-03-09
Thanks for the info :D

Do you think MS/Netflix is concerned about this?

---

### Post by directhex on 2009-03-09
> **davidryder said:**
> Thanks for the info :D

Do you think MS/Netflix is concerned about this?

Define "concerned".

Microsoft want to push as many people onto Silverlight as possible, as it allows them to sell Windows Server for hosting, Expression for design, and Media Server for encoding tasks.

To achieve this, and to have ANY hope of supplanting Flash as the "rich media" framework of choice, they need to target as many systems as possible - and in the netbook age, that means they can't ignore non-Windows platforms. Even when it literally costs them money.

They've been actively helping Novell to achieve feature parity - supplying all the official test cases, answering any technical queries, and so on - but the important (symbolic) step is the codec thing.

Codecs, by and large, are covered by big nasty patents held by big nasty men. That's why most distributions don't, say, support MP3 playback out of the box ($0.75 per decoder app license fee on the codec, if you're being legit). Ever noticed the box in Totem to buy codecs? See [http://www.fluendo.com/shop/category/end-user-products/](http://www.fluendo.com/shop/category/end-user-products/) or [http://shop.canonical.com/product_info.php?products_id=242](http://shop.canonical.com/product_info.php?products_id=242) for an idea of what "licensed" codecs cost.

When Moonlight encounters some media it can't play, it'll offer to download some licensed codecs (codecs offering the same support as the Canonical link above), free of charge. Those codecs aren't free for the distributor (patents are held by many people, so many people need to get paid), so every person downloading those codecs via Moonlight is getting something free of charge which (in a world of patent licensing) has value. And the people paying those fees are Microsoft.

Microsoft are literally paying people to use Moonlight in a "legit" manner.

So are they "concerned"? I'd say so - they're concerned about proving how cross-platform Silverlight is, and how every content creator should buy lots of expensive Microsoft products to produce SL content. Netflix will be a headline item to show off, the way the Obama inauguration streams were for Moon's SL1 support

---

### Post by DavidFourer on 2009-03-10
I talked to a phone rep at Netflix who said, off the record, that they will probably switch to something Linux compatible soon.  It's been an issue.  Is there any way to campaign for this?  I think it would be a good idea if everyone using Linux called Netflix customer support and asked for Linux and Firefox support for their streaming video.  The phone number for Netflix customer support is 1-866-402-2616.  There is no email or web support.  I could not find a mailing address.  Can somebody post one?  Are there other ways of letting people at netflix know that we care?  Thanks.

---

### Post by davidryder on 2009-03-11
directhex, thanks for all the information... very informative! 

David, aside from calling and shouting on the internet I can't really think of anything useful. The more we talk about it the more our voices will be heard :)

Unfortunately things happen very slowly in the corporate world. "Soon" for them could very well be a year from now. Hopefully Moonlight supports SL2 within 6 months. If however Netflix switches to something more compatible I will be one happy camper :D

---

### Post by directhex on 2009-03-11
I'd be concerned, actually, if they switch away from SL.

Much as it's still a few months away from working, SL means support on (say) super-cheap MID devices or ARM-based netbooks, and Flash support means x86 (and beta x86-64) support only

---

### Post by JPorter on 2009-03-25
> **directhex said:**
> [http://www.mono-project.com/Roadmap#Upcoming_Releases](http://www.mono-project.com/Roadmap#Upcoming_Releases)

September for beta support for SL2

Which means a big fat MAYBE for Karmic - depending on how much love I get from the release managers

According to the Moonlight Roadmap, there should be beta support for SL2 in mid-May.

[http://www.mono-project.com/MoonlightRoadmap](http://www.mono-project.com/MoonlightRoadmap)

---

### Post by directhex on 2009-03-26
> **JPorter said:**
> According to the Moonlight Roadmap, there should be beta support for SL2 in mid-May.

[http://www.mono-project.com/MoonlightRoadmap](http://www.mono-project.com/MoonlightRoadmap)

Their alpha is late... But if I get my hands on a tarball, I'll have a first look at packaging challenges

---

### Post by lostPenguin20 on 2009-07-10
any updates?

---

### Post by directhex on 2009-07-11
> **lostPenguin20 said:**
> any updates?

Use the Firefox plugin at [http://go-mono.com/moonlight-preview](http://go-mono.com/moonlight-preview) - but remove any packages first!

I won't package it until it stops needing SVN Mono to compile.

---

### Post by mitch_77 on 2009-07-28
> **directhex said:**
> Use the Firefox plugin at [http://go-mono.com/moonlight-preview](http://go-mono.com/moonlight-preview) - but remove any packages first!

I won't package it until it stops needing SVN Mono to compile.

Hi, I installed the plugin but still no Netflix.
Is it supposed to work?

Thanks,
mitch

P.S.
I should mention that I'm on Sabayon right now but I'll give it a try on Jaunty as soon as I can.

---

### Post by directhex on 2009-07-29
> **mitch_77 said:**
> Hi, I installed the plugin but still no Netflix.
Is it supposed to work?

Thanks,
mitch

P.S.
I should mention that I'm on Sabayon right now but I'll give it a try on Jaunty as soon as I can.

Netflix is still blocked by their use of DRM. If it's important to you, then write to their support people & tell them you want to use it on Linux but can't due to DRM.

---

### Post by mitch_77 on 2009-07-29
> **directhex said:**
> Netflix is still blocked by their use of DRM. If it's important to you, then write to their support people & tell them you want to use it on Linux but can't due to DRM.

will do.

thanks,
mitch

---

### Post by xzero1 on 2009-07-29
> **directhex said:**
> Netflix is still blocked by their use of DRM. If it's important to you, then write to their support people & tell them you want to use it on Linux but can't due to DRM.

They are not going to totally remove DRM, get real. Do you think they will simply let you copy movies so *they* get sued out of business? Asking them to remove DRM is probably a bad idea. Simply ask them to support Linux!

---

### Post by directhex on 2009-07-29
> **xzero1 said:**
> They are not going to totally remove DRM, get real. Do you think they will simply let you copy movies so *they* get sued out of business? Asking them to remove DRM is probably a bad idea. Simply ask them to support Linux!

Asking them to lean on Microsoft to provide DRM support is the other way to read what I wrote. How important are they, as customers? As opposed to using Adobe DRM the way BBC iPlayer does.

---

### Post by xzero1 on 2009-07-29
> **directhex said:**
> Asking them to lean on Microsoft to provide DRM support is the other way to read what I wrote. How important are they, as customers? As opposed to using Adobe DRM the way BBC iPlayer does.

Fine, but we should just be clear to them we want to be customers, not pirates. I despise DRM in general, but there are legitimate uses for it. I think we sorely need something competitive to flash which has been so problematic.

---

### Post by WanderingSnake on 2009-10-05
> **davidryder said:**
> I got past the version check, and have [Moonlight]("http://www.mono-project.com/Moonlight") (open source silverlight alternative) but I get a message saying Silverlight is not installed :( 

Does anyone have any ideas?

By the way, I used a Firefox plug-in called [Modify Headers]("https://addons.mozilla.org/en-US/firefox/addon/967") to get past the OS check at Netflix.

Type: Modify
Name: User-Agent
Value: Mozilla/5.0 (compatible; MSIE 7.0; Windows NT 6.0)

I feel I am soooo close!

Could you tell me just how you got the Modify Headers add-on to work? Because I'm told that it's impossible without using ActiveX

---

### Post by ectospasm on 2009-10-07
As of two nights ago, Netflix requires ActiveX to run.  I called and canceled my membership because they do not support Linux, and I told them that directly.  The only reason I even signed up for Netflix was to use their streaming service, and if I can't use Linux to do so, I don't want to use it.  They marked that on my account, so if and when this does become available, I will sign back up.

I didn't use the automatic form because it didn't seem to accept a reason why I was canceling.

---

### Post by bearcharger on 2009-10-09
if you really want to stream netflix you can watch it in a virtual machine.  not ideal, but it works well enough for me stay with netflix until there is linux support.

---

### Post by beastrace91 on 2009-10-09
> **bearcharger said:**
>  me stay with netflix until there is linux support.

Yea... That will happen right after MS releases a version of Office that runs natively...

~Jeff

---

### Post by beastrace91 on 2009-10-10
> **ectospasm said:**
> If we all had that attitude Linux support would NEVER gain any traction.  I wish people like you would just shut up and go away.

I've been on the Netflix user forums - emailed the company and read lots of other threads all over the net about the subject. The likely hood of netflix support Linux is very, very, low. I want native support just as much as the next guy - but at the same time I am a realist. I also don't think you should support a company because they *might* support Linux at some point. Look how well that did for all those people (myself included) who bought UT3 with the promise of a future client... And Netflix hasn't even does THAT much.

~Jeff

---

### Post by ectospasm on 2009-10-11
> **beastrace91 said:**
> I've been on the Netflix user forums - emailed the company and read lots of other threads all over the net about the subject. The likely hood of netflix support Linux is very, very, low. I want native support just as much as the next guy - but at the same time I am a realist. I also don't think you should support a company because they *might* support Linux at some point. Look how well that did for all those people (myself included) who bought UT3 with the promise of a future client... And Netflix hasn't even does THAT much.

~Jeff

This is precisely why I canceled my Netflix account.  I told them about it, I don't know what else I can do.  If their hands are tied by the studios forcing them to use ActiveX based DRM, I understand.  But I don't have to pay for their service.

I still think your sentiment that lobbying Netflix is a waste of time is wrong.  We just need to be bigger and louder.

---

### Post by SomeGuyDude on 2009-10-24
I'd join the crusade, but I have my Netflix account hooked up to my 360 and thus the problem is somewhat averted for me.

---

### Post by lusich on 2009-10-25
Sign the petition!!!

I am not sure if this is a proper place to post this, but I thought some of you might want to add your names to this petition:

[http://linuxlock.blogspot.com/2009/05/netflix-where-art-thou.html](http://linuxlock.blogspot.com/2009/05/netflix-where-art-thou.html) (or [http://www.petitiononline.com/Linflix/petition.html](http://www.petitiononline.com/Linflix/petition.html))

I hope we get it to make an impact.

---

### Post by noxterran on 2009-11-03
> **davidryder said:**
> I got past the version check, and have [Moonlight](http://www.mono-project.com/Moonlight) (open source silverlight alternative) but I get a message saying Silverlight is not installed :( 

Does anyone have any ideas?

By the way, I used a Firefox plug-in called [Modify Headers](https://addons.mozilla.org/en-US/firefox/addon/967) to get past the OS check at Netflix.

Type: Modify
Name: User-Agent
Value: Mozilla/5.0 (compatible; MSIE 7.0; Windows NT 6.0)

I feel I am soooo close!


i see you are using modify headers, mind telling me what scripts or commands or ANY instruction on what to use to try that, the build in help is useless

---

### Post by brandondiederich on 2009-11-04
You don't need to use a plug-in to get past the OS check. In Firefox type in the address bar about:config
Agree to be careful and right-click and add a new string. Name the string:
general.useragent.override
Give the string the value:
Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 (.NET CLR 3.5.30729)
Now it will think you are running Windows... way easier and simple to reverse... just delete the string. Even with this I am unable to get Netflix to work. I have Moonlight and Netflix believes that it is Silverlight but tells me I need to upgrade.. I believe we will just have to wait for SL2 support in Moonlight.

---

### Post by cdcguard on 2009-11-13
Ok, I added the string suggested by Brandon above.  That took me to the the "you're almost ready" page wherein it told me that I needed to install Silverlight, no surprise here.  I installed the Moonlight 2 beta from here...

[http://go-mono.com/moonlight-beta/]("http://go-mono.com/moonlight-beta/")

Now, when I click on a play button on Netflix's site it acts as if it's going to play the movie for a second but then tells me I am trying to launch a Silverlight 3 application and just hangs up.  A visit to the Silverlight site indeed indicated to me that Silverlight 3 is out.  So, if I'm understanding correctly Moonlight is getting support for SL2 just in time for SL3 to come out.  

Am I wrong here?  Has anyone found a work-around for this yet?

---

### Post by directhex on 2009-11-13
[img]http://squeedlyspooch.com/images/netflix.png[/img]

**DRM IS THE BLOCKER, COMPLAIN TO NETFLIX ABOUT DRM**

---

### Post by HappyFeet on 2009-11-13
> **cdcguard said:**
> Has anyone found a work-around for this yet?

Yeah, install windows in virtualbox.

---

### Post by cdcguard on 2009-11-13
> **HappyFeet said:**
> Yeah, install windows in virtualbox.

That's not really a work around, more like admitting defeat, which is what it's looking like I'll have to do.

---

### Post by AldenIsZen on 2009-11-18
> **HappyFeet said:**
> Yeah, install windows in virtualbox.

 I did that, but it is choppy. I gave it a gig (out of my 3) of ram (128 video) in Windows 7 Release candidate. I guess I could try to update Windows 7 first though... I did also put it into performance mose so it looks like a fancy windows 98 on the task bar and window borders.

 Hey, I just had a thought. I heard that trademark concerns arise when your trademark is used like a verb and is considered "ubiquitous". Examples are coke, Xerox, Google, etc. We call GUI programs windows.. would that mean anyone could use the term "windows" in their product???

---

### Post by sgbeamer on 2009-11-26
I have gotten fairly close by using a Firefox add-in called Agent Switcher and switching to Internet Explorer 8.  I get the movie page but it says I need ActiveX installed.  I can't figure out that one. Moonlight is installed and working

---

### Post by AldenIsZen on 2009-11-27
It won't work due to Moonlight not having DRM, because Microsoft won't give it up. We need to lean on Netflix to either lean on Microsoft (not likely to be successful) or go to another codec licenser. 

  Until then, we will get the same promise from Netflix of soon, for who knows how long. Don't you think it is suspicious that everyone who calls gets the same "down low" advice to just hang on, they are working on it? I worked in a call center for 5 1/2 years, they know their agents are telling people this or their customer service would suck and the business would die.

---

### Post by x C0MMAND0 x on 2009-12-09
Perhaps this has been brought up before, but what about installing Internet Explorer in wine?  Then, you could install Silverlight and ActiveX Control...

---

### Post by AldenIsZen on 2009-12-11
> **x C0MMAND0 x said:**
> Perhaps this has been brought up before, but what about installing Internet Explorer in wine?  Then, you could install Silverlight and ActiveX Control...

 I haven't had much success with Wine, period. I did try it the other day after posting in this thread, but I couldn't get I.E. to even let me log into Netflix, I just got an error.

---

### Post by Uncle Fat on 2010-01-07
Ok, so this isn't a strictly Linux solution, but I'm currently viewing Netflix content on my Ubuntu machine (in XBMC) by running PlayOn (UPnP server) on my Windows machine.

As I said, not a strictly Linux solution, but if you've got a Windoze machine somewhere on your network; it's an option.

---

### Post by CJPrinter on 2010-01-15
What about running just DirectX 10 in wine like this:  [http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu](http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu)  

Would this work using the Firefox about:config edit that [brandondiederich]("http://ubuntuforums.org/member.php?u=888093") mentioned & Moonlight?
> 
You don't need to use a plug-in to get past the OS check. In Firefox type in the address bar about:config
Agree to be careful and right-click and add a new string. Name the string:
general.useragent.override
Give the string the value:
Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 (.NET CLR 3.5.30729)
Now it will think you are running Windows... way easier and simple to reverse... just delete the string.

---

### Post by CJPrinter on 2010-01-17
> What about running just DirectX 10 in wine like this:  [http://ubuntu-blog.com/how-to-instal...x-10-on-ubuntu]("http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu")  

Would this work using the Firefox about:config edit that [brandondiederich]("http://ubuntuforums.org/member.php?u=888093") mentioned & Moonlight?
[QUOTE]

                                                 You don't need to use a plug-in to get past the OS check. In Firefox type in the address bar about:config
Agree to be careful and right-click and add a new string. Name the string: general.useragent.override
Give the string the value:
Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 (.NET CLR 3.5.30729)
Now it will think you are running Windows... way easier and simple to reverse... just delete the string.[/QUOTE]Anyone?

---

### Post by jeremyjjbrown on 2010-01-18
> **CJPrinter said:**
> What about running just DirectX 10 in wine like this:  [http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu](http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu)  

Would this work using the Firefox about:config edit that [brandondiederich]("http://ubuntuforums.org/member.php?u=888093") mentioned & Moonlight?

CJ,

did you try this? does it work?

Cheers

---

### Post by CJPrinter on 2010-01-18
> CJ,

did you try this? does it work?

Cheers

No, I haven't tried it yet.  I was really hoping someone on this forum had.  I'm not sure I want to go through all the hassle only to find out it won't.  If I do, before I get a solid answer, I'll be sure to post how it turns out.  Problem is finding the time...

---

### Post by evgeny1978 on 2010-01-18
I got as far as possible by altering the User Agent name (past Active X is not enabled screen). First I am getting warning that I am running Silverlight 3 application, but netflix player starts nevertheless. But at the end I am getting an error: "This Silverlight application is using DRM-protected content, which Moonlight does not support". That is it. I have Moonlight 2 installed, it does not support DRM (digital rights management) yet, that means no Netflix on linux :(

---

### Post by CJPrinter on 2010-01-19
> "This Silverlight application is using DRM-protected content, which Moonlight does not support". That is it, I have Moonlight 2 installed, it does not support DRM yet, that means no Netflix in linuxThis doesn't mean "no Netflix in Linux."  This simply means you have gone as far as you are willing to go. :rolleyes::confused::rolleyes:

It's a well know hack to stream Netflix through PlayOn as a UPnP MediaServer to XBMC.  ***BUT*** some of us don't want to spend $40 to access a service we are already paying for. ](*,)

There has got to be a way to get this to work.  According to everything I have found you need three things: 

1) Internet Explorer or Firefox tweaked to report that it is IE. - This gets around the browser check.
2) DirectX 10 - Apparently needed to get Silverlight 3 to function correctly with Netflix.
3) Silverlight 3.0 - To handle the content from Netflix & unlock the bleeping DRM.

These can all theoretically be installed using Wine.  

This is not super advanced stuff!  Especially for Linix users!  I'm amazed no one has tried it yet.  Like I said before:
> 
I was really hoping someone on this forum had. I'm not sure I want to go through all the hassle only to find out it won't. If I do, before I get a solid answer, I'll be sure to post how it turns out. Problem is finding the time...

---

### Post by evgeny1978 on 2010-01-19
> **CJPrinter said:**
> This doesn't mean "no Netflix in Linux."  This simply means you have gone as far as you are willing to go. :rolleyes::confused::rolleyes:


All I wanted to say is that new Moonlight 2 does not provide NATIVE support of Netflix on Linux! There are "Tricks and workarounds" like windows in virtual machines, UPNP servers on windows, but this thread is not about them.

---

### Post by jrusso2 on 2010-01-19
Strange it runs on my mac with no Internet Explorer and no active x fine.

Pretty sure the issue is the DRM.  It seems your trying to imitate and Windows install maybe would be easier to imitate an OS X install.

---

### Post by evgeny1978 on 2010-01-19
> **jrusso2 said:**
> Strange it runs on my mac with no Internet Explorer and no active x fine.

Pretty sure the issue is the DRM.  It seems your trying to imitate and Windows install maybe would be easier to imitate an OS X install.

It is not strange. All you need is Silverlight with DRM support to make Neflix work, which exist for MAC OS. Moonlight is open source (!) implementation of Silverlight for Linux. I believe Microsoft will never open the source code of DRM! And I even doubt they'll make any time soon some kind of proprietary DRM module for Moonlight.

---

### Post by CJPrinter on 2010-01-19
It looks like [baceman007]("http://ubuntuforums.org/member.php?u=932006") was on the right path in October:

> I have been working on the Netflix/Ubuntu 9.04 problem for quite some time.
I offer the following obervations with no implied warranty.
I started with looking at the directions here 
[http://fatbuttlarry.blogspot.com/200...ix-ubuntu.html]("http://fatbuttlarry.blogspot.com/2009/02/netflix-ubuntu.html")
but since this user had the most success with 8.04 I had to keep looking. Which lead me to this forum amongst many other places. 
At any rate here's what I did after trying the moonlight 1.99.5, Coral IETab, and User Agent Switcher combinations and only getting as far as the Active X is not enabled screen. I tried ies4linux as well. 

-- At this point I can get a instant movie to load to the point that I get the black backdrop with the swirling blue loading icon on Netflix in Firefox 3.5 run using Wine 1.1.3 with Silverlight 3 and some Windows Fonts installed as explained below. 

-- I added [http://wine.buggetdedicated.com/apt](http://wine.buggetdedicated.com/apt) edgy 
to the Third-Party Software tab under System -- Administration -- Software Sources and added an authentication certificate for winehq. 
[http://ubuntuforums.org/showthread.php?t=338400](http://ubuntuforums.org/showthread.php?t=338400)
this explains getting the winehq gpg key. If you don't have it you should just get a warning when installing. Adding it should make the warning go away forever. This allows you to install the most recent versions of Wine which may not be the stable releases.

-- I then went to System -- Administration -- Synaptic -- and installed Wine 1.1.3, wine-dev 1.1.3, and wine-gecko 1.0.0. Note: In theory after you add the source and refresh the package list, when prompted, the Update Manager should tell you that there is an update for Wine, or if you use Add/Remove to add Wine and then use the Update Manager (System -- Administration -- Update Manager) it should tell you. Anyway, I just used Synaptic so whatever floats your boat. 

-- I downloaded the Windows version of Firefox 3.5 from [www.Mozilla.com/Firefox3.5]("http://www.mozilla.com/Firefox3.5"), went to Application -- Wine -- Browse C: drive and dropped the *.exe in there. I then double clicked on it and installed it. 

-- Launch Firefox 3.5 using Wine, go to Netflix and log in, then choose something to watch instantly. You will then be told to download Silverlight 3. Save the *.exe file for it and move it into your Wine C: drive as explained in the last step. 

-- Close Firefox and install Silverlight. If you go to Netflix again at this point you will get a font error stating that you must be a Crapple user if you're getting a font error. Of course you're not, but Netflix believes that people only use Windoze and OSXcrament so that's what you get. If they didn't believe this they would have just used something that already works on everyone's systems instead of painting themselves into a corner with Silverlight... I still like Netflix, but the whole Silverlight thing gets on my nerves... 

-- Anyway, to solve this font problem you need to move some Windows fonts into your Wine virtual C: drive\windows\fonts folder. I copied them from my legal copy of Windows in it's C:\Windows\Fonts folder. I have a dual boot setup so this was easy. I'm sure some linux font guru probably has a welcome substitution to this step that doesn't involve having to use Crapple or Microshaft fonts but that's what I did. 

-- Once you do this, at least for me, when I go to Netflix using Firefox 3.5 and Silverlight 3 run through Wine I get the movie to start to load, then my browser freezes and goes grey. Anyway, it's at least promising.Unfortunately there was no follow-up post that got it fully working...#-o
> 
Pretty sure the issue is the DRM. It seems your trying to imitate and Windows install maybe would be easier to imitate an OS X install.Good point [jrusso2]("http://ubuntuforums.org/member.php?u=222517")!  How hard would it be to get the OS X version of SL work in Ubuntu? :-\"

---

### Post by CJPrinter on 2010-01-19
Ok, here goes...

[SIZE=3]***Install WINE:***[/SIZE]

Go to  **System->Administration->Software Sources**.  Then select the **Other Software **tab and click **Add**.  

Then, **copy and paste one of the lines below** depending on which  version you are running.
  **For Ubuntu Karmic (9.10):**
*ppa:ubuntu-wine/ppa*
 **For Ubuntu Jaunty (9.04):**
*deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"*
 **For Ubuntu Intrepid (8.10):**
*deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"*
 **For Ubuntu Hardy (8.04):**
*deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"*

After adding the repository, you also need to add the key for the repository  to your system's list of trusted keys. Ubuntu 9.10 users may skip this step.
  For Ubuntu 9.04 and earlier, download this: [http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg](http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg) (right click -> save as) to your desktop.  Then open the **Authentication** tab, click **import key file**, and  select the key file you just saved (*Scott Ritchie.gpg*).  It is safe to  delete this file after doing this step.

Click close to finish, and then **reload the package information** when  prompted. If you have Wine installed, the system's update manager will now  inform you of the latest Wine beta release and prompt you to upgrade. If you  haven't installed Wine yet, go to Applications->Add/Remove and search for  Wine.

I just copy pasted the instructions from here:[ http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb") so you can go there if you get in trouble.

[SIZE=3]***Install Windows Fonts:***[/SIZE]
 
Download this file: [http://rs66.rapidshare.com/files/20077793/WINXP_DEFAULTFONTS.zip](http://rs66.rapidshare.com/files/20077793/WINXP_DEFAULTFONTS.zip)  Unzip the contents to the WINE virtual drive under C:->Windows->Fonts

[SIZE=3]***Install DirectX:***[/SIZE]

Follow the instructions here: [http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu](http://ubuntu-blog.com/how-to-install-directx-10-on-ubuntu)

[SIZE=3]***Install Firefox:***[/SIZE]

Windows version3.5.7 download link: [http://download.mozilla.org/?product=firefox-3.5.7&os=win&lang=en-US](http://download.mozilla.org/?product=firefox-3.5.7&os=win&lang=en-US)

Save to your desktop.

When finished downloading double click on it.  Install leaving everything as set by default.  The last step should be for the browser to open.  If all went according to plan, you should have the "Welcome to Firefox" screen.

[SIZE=3]***Go to Netflix & log in***.  [/SIZE]

Go to your instant queue & click play.  You will be prompted to install Silverlight.  Do it &  reboot.

[SIZE=3]***My results***[/SIZE] ended with the spinning blue loading icon.  After a few seconds the entire browser turns grey & locks up.  Apparently Compiz greys applications when they are not responding.  :(

Any ideas???

---

### Post by CJPrinter on 2010-01-23
> [SIZE=3]***My results***[/SIZE] ended with the spinning blue loading icon.  After a few seconds the entire browser turns grey & locks up.  Does anyone know how to track down the cause of the lock-up?  Is there an app that can log what's going on?

---

### Post by jeremyjjbrown on 2010-01-25
> **CJPrinter said:**
> Does anyone know how to track down the cause of the lock-up?  Is there an app that can log what's going on?

Launch everything from the terminal. It will log all errors and processes. This is SOP for trouble shooting. :)

---

### Post by CJPrinter on 2010-01-25
> Launch everything from the terminal. It will log all errors and processes.How would I launch WINE programs from within the terminal? I was hoping I could simply run everything in the GUI, & watch a log as everything runs.  I know the end result would be pretty much the same, but this is more what I'm used to in OS X & Windows.   I'm kind of a noob with Linux command line. :confused:

---

### Post by jeremyjjbrown on 2010-01-25
> **CJPrinter said:**
> How would I launch WINE programs from within the terminal? I was hoping I could simply run everything in the GUI, & watch a log as everything runs.  I know the end result would be pretty much the same, but this is more what I'm used to in OS X & Windows.   I'm kind of a noob with Linux command line. :confused:

wine /home/YOURACCOUNT/.wine/drive-c/Program Files/WHATEVER/THE/PATH/IS.exe

---

### Post by Thomas Garman on 2010-01-26
I just use Virtualbox with Karmic 9.10... and in my little virtual machine I have the crummiest little version of windows XP of all time and that little OS is used for nothing other than running Internet Explorer 8 with the Silverlight Plug-in with which I stream instant watcher video from Netflix while in Ubuntu.  It works just fine for me.

---

### Post by jeremyjjbrown on 2010-01-26
> **Thomas Garman said:**
> I just use Virtualbox with Karmic 9.10... and in my little virtual machine I have the crummiest little version of windows XP of all time and that little OS is used for nothing other than running Internet Explorer 8 with the Silverlight Plug-in with which I stream instant watcher video from Netflix while in Ubuntu.  It works just fine for me.

I tried this too. I worked for me but with choppy video.

---

### Post by CJPrinter on 2010-01-27
Thanks [jeremyjjbrown]("http://ubuntuforums.org/member.php?u=485065")!  I got Firefox to run from terminal in WINE, but I'm not sure what it's telling me.

Here's the code:

```
xbmc@xbmc:~/.wine/drive_c/Program Files/Mozilla Firefox$ wine firefox.exe
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32fcd4
fixme:iphlpapi:NotifyAddrChange (Handle 0x115e9ac, overlapped 0x115e990): stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject no class object {591209c7-767b-42b2-9fba-44ee4615f2c7} could be created for context 0x3
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\xbmc\\Application Data\\Mozilla\\Firefox\\Profiles\\vondqsxk.default\\sessionstore.js" 1 536870916 (nil) (nil) 0x194e44 (nil)
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\xbmc\\Local Settings\\Application Data\\Mozilla\\Firefox\\Profiles\\vondqsxk.default\\Cache.Trash\\Trash\\Cache" 1 536870916 (nil) (nil) 0x1f766c (nil)
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\xbmc\\Application Data\\Mozilla\\Firefox\\Profiles\\vondqsxk.default\\sessionstore.js" 1 536870916 (nil) (nil) 0x1d382c (nil)
err:ole:CoGetClassObject class {4125dd96-e03a-4103-8f70-e0597d803b9c} not registered
err:ole:CoGetClassObject class {4125dd96-e03a-4103-8f70-e0597d803b9c} not registered
err:ole:CoGetClassObject no class object {4125dd96-e03a-4103-8f70-e0597d803b9c} could be created for context 0x3
fixme:font:get_nearest_charset returning DEFAULT_CHARSET face->fs.fsCsb[0] = 00000000 file = /home/xbmc/.wine/dosdevices/c:/windows/Fonts/vgaoem.fon
https://www.netflix.com/Login
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\xbmc\\Application Data\\Mozilla\\Firefox\\Profiles\\vondqsxk.default\\sessionstore.js" 1 536870916 (nil) (nil) 0x1fdaec (nil)
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\xbmc\\Application Data\\Mozilla\\Firefox\\Profiles\\vondqsxk.default\\sessionstore.js" 1 536870916 (nil) (nil) 0x1ef5ec (nil)
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\xbmc\\Application Data\\Mozilla\\Firefox\\Profiles\\vondqsxk.default\\sessionstore.js" 1 536870916 (nil) (nil) 0x1f7dcc (nil)
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32ea5c (null) (null) 0x6d8b80e0
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f1a0 (null) (null) 0x6d8b80e0
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f168 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f114 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f110 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f118 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f0e8 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f0c8 (null) (null) 0x6d8b80e0
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:module:GetModuleHandleExW should pin refcount for 0x6d800000
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x32f624, cbSize=8) stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:CheckTokenMembership ((nil) 0x181db8 0x33fd90) stub!
err:ole:CoGetClassObject class {c2e88c2f-6f5b-4aaa-894b-55c847ad3a2d} not registered
err:ole:CoGetClassObject no class object {c2e88c2f-6f5b-4aaa-894b-55c847ad3a2d} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32f058,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f338 (null) (null) 0x6d8b80e0
fixme:module:GetModuleHandleExW should pin refcount for 0x6d800000
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x32f7bc, cbSize=8) stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32e838 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\xbmc\\Application Data\\Mozilla\\Firefox\\Profiles\\vondqsxk.default\\sessionstore.js" 1 536870916 (nil) (nil) 0x6dc95bc (nil)
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f770 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f814 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f760 (null) (null) 0x6d8b80e0
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f7d0 (null) (null) 0x6d8b80e0
fixme:qmgr:BITS_IBackgroundCopyJob_SetNotifyInterface Not implemented
fixme:qmgr:BITS_IBackgroundCopyJob_Cancel Not implemented
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
fixme:advapi:RegisterTraceGuidsW 0x6d84c03a (nil) 0x6d81b8f8 3 0x32f840 (null) (null) 0x6d8b80e0
fixme:urlmon:CreateURLMonikerEx ignoring flag URL_MK_UNIFORM
Killed

```Anyone know where to even begin:?:

I'd try Virtualbox, but I don't own a full XP install disk.  The two copies I have are 98 with an upgrade to XP, & the recovery media for this PC.  I'm not about to spend the money to purchase a new license of XP just to watch streaming Netflix movies. 

The box I'm trying to get this to work on is an Acer Revo Aspire, set up as a HTPC running XBMC. 

I've invested WAY too much time on this.  I hate to say it, but I'm seriously considering dropping Ubuntu & restoring it with the factory XP disk.  IDK, maybe I'll set it up to dual boot. I really hate to give up, but I feel like I'm ](*,)

---

### Post by jeremyjjbrown on 2010-01-27
> **CJPrinter said:**
> Thanks [jeremyjjbrown]("http://ubuntuforums.org/member.php?u=485065")!  I got Firefox to run from terminal in WINE, but I'm not sure what it's telling me.

I've invested WAY too much time on this.  I hate to say it, but I'm seriously considering dropping Ubuntu & restoring it with the factory XP disk.  IDK, maybe I'll set it up to dual boot. I really hate to give up, but I feel like I'm ](*,)

Why don't you just dual boot? Lot's of others do it, it's really easy with XP and any Ubuntu. That's what I am doing so we can watch netflix. It only takes a minute to reboot if you keep your windows install to a minimum. Then you can run other windows software you may need, without the nasty hacks required to use WINE. And, boot into Ubuntu when you want a secure malware free OS, and keep learning Linux.

I'm just watching this thread to someday avoid booting into XP to watch movies. I'm sure I'll never be completely free of MS.

---

### Post by snowpine on 2010-01-27
Netflix could support Linux users tomorrow, if they wanted to. Fact is, the major motion picture studios don't want a bunch of "hackers and pirates" (public perception of Linux users) stealing their movies, and Netflix has to play by their rules if they want to stay in business. I guarantee if the community finds a loophole to watch Netflix in Linux, they will patch it immediately. :)

---

### Post by jeremyjjbrown on 2010-01-28
> **snowpine said:**
> Netflix could support Linux users tomorrow, if they wanted to. Fact is, the major motion picture studios don't want a bunch of "hackers and pirates" (public perception of Linux users) stealing their movies, and Netflix has to play by their rules if they want to stay in business. I guarantee if the community finds a loophole to watch Netflix in Linux, they will patch it immediately. :)

Your probably right. But, the truth is it doesn't stop anything, it only makes it worse. It just makes people mad, who wants to crack a smeary silverlight stream with flickers and tears when you can easily crack an blueray and compress it in a much better format. I know people now who only use cracked stuff out of principle. They have the money, their just not going to give to a corporation to control them.

---

### Post by elgordo123 on 2010-01-30
> **snowpine said:**
> ..major motion picture studios don't want a bunch of "hackers and pirates" (public perception of Linux users) stealing their movies...

Since most people use windows the truth is that the majority of hackers and pirates are windows users.   That just burns me everytime I hear that!

---

### Post by AldenIsZen on 2010-01-31
> **jeremyjjbrown said:**
> Your probably right. But, the truth is it doesn't stop anything, it only makes it worse. It just makes people mad, who wants to crack a smeary silverlight stream with flickers and tears when you can easily crack an blueray and compress it in a much better format. I know people now who only use cracked stuff out of principle. They have the money, their just not going to give to a corporation to control them.
As further evidence...

[B][DRM Content Drives Availability On P2P Networks]("http://yro.slashdot.org/story/10/01/30/1436250/DRM-Content-Drives-Availability-On-P2P-Networks") [slashdot.org]
[/B]
*"The music industry once feared that going DRM-free would drive a massive explosion of copyright-infringing music availability on P2P networks. Now, a new study seems to suggest otherwise. The answer is obvious: if you can easily get inexpensive DRM-free content that works on your devices through legitimate channels, [most people won't bother with the headache of P2P networks]("http://arstechnica.com/media/news/2010/01/bittorrent-census-about-99-of-files-copyright-infringing.ars"). It appears that users largely turn to P2P to acquire DRM-free versions of content that is distributed with DRM. The MPAA, of course, will not come away from this with the obvious conclusion."*

XKCD says it best:

[IMG]http://imgs.xkcd.com/comics/steal_this_comic.png[/IMG]

---

### Post by BT1 on 2010-02-03
Netflix... eh the ol' lady who refuses to budge. It's odd that I can "instantly add to que" the movies I want to watch, but then must watch them through my Xbox 360 lol.

---

### Post by davidryder on 2010-02-08
> **BT1 said:**
> Netflix... eh the ol' lady who refuses to budge. It's odd that I can "instantly add to que" the movies I want to watch, but then must watch them through my Xbox 360 lol.

Well it looks like HTML5 has the potential to supplant at least Flash, possibly silverlight. YouTube, Vimeo, Google, and Apple are all starting to support the idea of using HTML5 for a standard for video and audio. 

It requires no plugins or codecs - it is supported by any HTML5-compliant web browser. HTML5 is still in draft phase and has some patent/licensing issues to work out but there is a lot of promise! 

If you want to get a taste of HTML5 embedded videos, check out Google Labs. 

> 
This is an opt-in experiment for HTML5 support on YouTube. If you are using a supported browser, you can choose to use the HTML5 player instead of the Flash player for most videos.

**Supported Browsers**

Right now we support browsers that support both the video tag in HTML5 and the h.264 video codec. These include:

    * Google Chrome
    * Apple Safari (version 4+)
    * Microsoft Internet Explorer with Google Chrome Frame installed (Get Google Chrome Frame)


**Updates!**

    * 1/27/2010: Fullscreen support enabled (if supported by browser).

[B]
Additional Restrictions (we are working on these!)[/B]

    * Videos with ads are not supported (they will play in the Flash player)
    * Fullscreen is not supported
    * If you've opted in to other testtube experiments, you may not get the HTML5 player (Feather is supported, though)


[http://youtube.com/html5](http://youtube.com/html5)

---

### Post by AldenIsZen on 2010-02-08
Looks like Firefox isn't planning to support HTML5 video though... bummer. I loves me Firefox. I think if I keep my Netflix account it will only be so my father can watch movies. He is never in Linux anyway since his PC isn't supported... I really need to get him a new one.

---

### Post by davidryder on 2010-02-09
> **AldenIsZen said:**
> Looks like Firefox isn't planning to support HTML5 video though... bummer. I loves me Firefox. I think if I keep my Netflix account it will only be so my father can watch movies. He is never in Linux anyway since his PC isn't supported... I really need to get him a new one.

Firefox is supporting the Ogg codec, which is open source. The H.264 codec is closed source. So that's the problem right now. But all the browsers will support the <video> tag.

---

### Post by AldenIsZen on 2010-02-09
> **davidryder said:**
> Firefox is supporting the Ogg codec, which is open source. The H.264 codec is closed source. So that's the problem right now. But all the browsers will support the <video> tag.

 Which is all fine and dandy, except by what I understand Ogg just doesn't cut it, and there is no comparable open source equivalent to H.264. But I feel it is all very complicated (even more??? lol) and that Google and Chrome are going to change things for Firefox due to this very thing.

---

### Post by ifraser on 2010-02-16
Well, in response to the original subject of this excellent thread, Moonlight 2.0 [is now available for download!]("http://www.go-mono.com/moonlight/")

---

### Post by ifraser on 2010-02-16
> **davidryder said:**
> I got past the version check, and have [Moonlight](http://www.mono-project.com/Moonlight) (open source silverlight alternative) but I get a message saying Silverlight is not installed :( 

Does anyone have any ideas?

By the way, I used a Firefox plug-in called [Modify Headers](https://addons.mozilla.org/en-US/firefox/addon/967) to get past the OS check at Netflix.

Type: Modify
Name: User-Agent
Value: Mozilla/5.0 (compatible; MSIE 7.0; Windows NT 6.0)

I feel I am soooo close!

I just logged in using the newest Moonlight and used Modify Headers to spoof a Windows machine, and everything loads just fine.  Moonlight gives a message during loading saying that Netflix is now running Silverlight 3 and users may encounter errors, blah blah.

The real problem, that which will derail your streaming right as it's about to begin, is a message saying "This stream is DRM-protected which Moonlight doesn't currently handle".  Curses.

---

### Post by Chronon on 2010-02-16
The DRM issue is the fundamental thing and that will never happen without Microsoft's help.  I gave up on the pipe dream of Netflix in Linux some months ago.

---

### Post by Simian Man on 2010-02-16
Somebody should change the title of this thread to something not so positive and excited sounding because I always keep seeing it in active topics and think that somebody has solved this :(.

---

### Post by matthewboh on 2010-02-17
Just finished talking to Netflix support and they said if they get enough people asking for it, they'll add Linux support - so I say call them!

---

### Post by Gallahhad on 2010-02-17
This is what I got:
[IMG]http://img706.imageshack.us/img706/811/netflixactivex.png[/IMG]
Using Novell Moonlight 2.99.0.2 and Firefox User Agent Switcher got me that far.

---

### Post by Gallahhad on 2010-02-17
Okay, so, I just got off the phone with Netflix Customer Service.

My Customer Service Agent was very friendly, and passed on the suggestion while I waited on hold. She said that the person she passed it on to was receptive to the idea, and that if we want it we should call and make the suggestion.

She also said it would be okay for me to post the contact information here.

Please any who are going to call, remember to be polite, courteous, and pleasant. Remember were asking them to do something for us, please do not be demanding, and do be gracious.

Here is the contact information:

[quote=Gallahhad, From The Netflix Website]
[Call Customer Service]("http://www.netflix.com/ContactUs?lnkctr=cuPh&show=true")             Phone help available 24 hours a day.                               
                                                                                
                                                                1-866-716-0414
                         For faster service, use this service code: 595 272                     
                                       
                                  Current hold time is  about 1 minute
             
[/quote]

Gallahhad

---

### Post by gplauche on 2010-02-17
Asking Netflix to restore online/email customer service would be nice too.

---

### Post by Sugi on 2010-02-22
I support this thread. :)

Calling customer service tonight.

Sugi

---

### Post by crazy_lazy_bear on 2010-03-01
>  Originally Posted by Gallahhad, From The Netflix Website
Call Customer Service Phone help available 24 hours a day.

1-866-716-0414
For faster service, use this service code: 595 272

Current hold time is about 1 minute

     Thanks!! I called, and then posted the info on Facebook and Twitter.  Grassroots, man; grassroots.

Jay

---

### Post by TracyO on 2010-03-20
Since this keeps coming up, I've called Netflix a couple times to let them know this is something Linux users would very much like!  

The first time I called (at least a year ago) I got sort of a "smile and nod" responses, but the last time I called a few months ago, the employee seemed very receptive and said they were working on it.

I have hope that it's coming sooner or later!

---

### Post by haddog on 2010-03-20
i am going to call tonight. Would be great to stream netflix in Linux.

---

### Post by goltoof on 2010-03-21
I support this.  Signed the petition and giving them a call.  This thread has around 30,000 views, I doubt that many people have phoned in.  I hope anyone reading this takes the initative and calls them.  

I'm sure they realize by now they're missing out on some serious business by cutting us out.  Still, every little voice helps.

---

### Post by Tanth on 2010-03-26
I just called Netflix tech support, and they said that Linux streaming should be up by the end of spring.

---

### Post by Naitsirhc Hsem on 2010-03-28
Are you serious, spring!  I have had to keep a windows partition on my hard drive for a year because of netflix! YAHOO :p

---

### Post by kcyanks1 on 2010-03-28
I just called and they gave a generic response that they are always trying to make Netflix available in more ways.  Then when I asked if they were specifically working on making it compatible with Linux now, they said no.

---

### Post by ray ray on 2010-03-28
Petition, Twitter, Facebook...check. Calling in the morning...

---

### Post by haddog on 2010-04-02
Let's go Netflix. Get us linux streaming support!

---

### Post by haddog on 2010-04-02
> **ray ray said:**
> petition, twitter, facebook...check. Calling in the morning...

**ditto!**

---

### Post by Sable683 on 2010-04-04
Anybody know what Roku use? They run linux and stream from netflix...

---

### Post by Naitsirhc Hsem on 2010-04-04
Roku uses linux and I think it incorporates some form of DRM provided by MicroSoft (AKA MegaSoft, there is nothing "Micro" about it).  It would be cool if you could pay for DRM for linux jost for netflix, I would not mind paying 20 bucks for it.  I am also sure microsoft would not mind making the extra money to waste on things other than developing a halfway decent operating system.

---

### Post by Sable683 on 2010-04-04
According to the Hackaday website, the DRM in the Roku player is "purely a feature of the NXP PNX8935 processor being used".

---

### Post by MrNatewood on 2010-04-04
> **Tanth said:**
> I just called Netflix tech support, and they said that Linux streaming should be up by the end of spring.

They didn't mention spring of which year is it, did they?

---

### Post by haddog on 2010-04-06
It's spring now. Maybe I'll give a call also and ask.

---

### Post by neu5eeCh on 2010-04-10
> **haddog said:**
> It's spring now. Maybe I'll give a call also and ask.

I just ran into this issue last night. Read through all the posts. Called Netflix today and the customer service rep told me (as far as he knows) Netflix has no plans to support *Instant Play* on linux. Not now. Probably not ever.

But [one blogger]("http://kaitrin.blogspot.com/2009/01/netflix-instant-play-in-ubuntu.html") **did** get Instant Play to work using Windows in Virtual Box.

I guess I'll just have to use my Win 7 Laptop for Netflix, but I may still try to get it to work on my Linux Box just 'cause I like a good puzzle.

---

### Post by ectospasm on 2010-04-11
> **VTPoet said:**
> I just ran into this issue last night. Read through all the posts. Called Netflix today and the customer service rep told me (as far as he knows) Netflix has no plans to support *Instant Play* on linux. Not now. Probably not ever.


This isn't a reason to give up hope.  Unless something like this is part of a marketing campaign, customer service representatives won't be able to keep their stories straight, since there is no official word.  We need to keep pressing on Netflix, if enough voices scream at them, they'll see value in allowing Linux users to access instant play.

---

### Post by jrusso2 on 2010-04-11
No they won't  They can't do it without DRM.

---

### Post by Frak on 2010-04-11
> **jrusso2 said:**
> No they won't  They can't do it without DRM.
They won't do it because it would require developing a Moonlight compatible player. DRM-support exists in the Linux kernel.

---

### Post by jrusso2 on 2010-04-11
Not for mono it doesn't.

---

### Post by Chronon on 2010-04-11
> **Frak said:**
> They won't do it because it would require developing a Moonlight compatible player. DRM-support exists in the Linux kernel.

DRM comes in many varieties.  It doesn't mean one specific thing.  The fact that some form of DRM support exists in the kernel doesn't provide any indication that there's support for the particular DRM scheme involved here.

---

### Post by Frak on 2010-04-11
> **jrusso2 said:**
> Not for mono it doesn't.
It could be implemented with little problems.

> **Chronon said:**
> DRM comes in many varieties.  It doesn't mean one specific thing.  The fact that some form of DRM support exists in the kernel doesn't provide any indication that there's support for the particular DRM scheme involved here.

The Mono team is working on implementing PlayReady for Moonlight. I know what DRM is.

---

### Post by yoshimitsuspeed on 2010-04-13
> **VTPoet said:**
> I just ran into this issue last night. Read through all the posts. Called Netflix today and the customer service rep told me (as far as he knows) Netflix has no plans to support *Instant Play* on linux. Not now. Probably not ever.


Same response I got a couple weeks ago.
I'm pretty pissed just because they told everyone a year ago it was going to happen soon, it was in the works etc. 

Half the reason I have kept my subscription for the last year is because of what they told me. 
I'm about one bad day from canceling.

---

### Post by jeremyjjbrown on 2010-04-13
After watching this issue I'm convinced we will have to wait until Google Chrome OS hits the market. When all of those Linux netbooks are on the out there, it will be a lot harder for any of these jerks to deny us support.

---

### Post by AldenIsZen on 2010-04-13
I think you are on to something there. Thank goodness for Google being Open Source friendly.

---

### Post by Frak on 2010-04-13
> **jeremyjjbrown said:**
> After watching this issue I'm convinced we will have to wait until Google Chrome OS hits the market. When all of those Linux netbooks are on the out there, it will be a lot harder for any of these jerks to deny us support.

> **AldenIsZen said:**
> I think you are on to something there. Thank goodness for Google being Open Source friendly.

Let's learn from history:








It won't happen.

---

### Post by AldenIsZen on 2010-04-13
> **Frak said:**
> Let's learn from history:








It won't happen.

 So you are saying that NetFlix will not follow the money and ignore their mission and goal to profit? This being of course that **jeremyjjbrown** was right and ChromeOS takes off.

---

### Post by Frak on 2010-04-13
> **AldenIsZen said:**
> So you are saying that NetFlix will not follow the money and ignore their mission and goal to profit? This being of course that **jeremyjjbrown** was right and ChromeOS takes off.
**If** ChromeOS takes off. A far too small block of users are ready to abandon Windows for a single web browser. It would cost more money to make a Linux compatible client than what they would return.

---

### Post by jeremyjjbrown on 2010-04-14
> **Frak said:**
> **If** ChromeOS takes off. A far too small block of users are ready to abandon Windows for a single web browser. It would cost more money to make a Linux compatible client than what they would return.

Don't be so negative. 

People use MS out of habit because it's what ships on their machine. I just installed Ubuntu on my friends laptop because it wouldn't work with even a clean install of MS. I told him he didn't need malware protection and it's free and he asked why everyone isn't using it. My reply, 'I don't know'. People will use what works, give them time. Gmail users are in the 100's of millions right now, and they love their web apps. Everyone I've turned on to google docs has basically stopped using MS Office. I have a fork of Chrome OS beta on my netbook and I can say that it will be perfect for the average computer user on the go. It's a cloud based os for cloud based services exactly like Netflix. If netflix doesn't support them, someone else will, I guarantee it.

---

### Post by AldenIsZen on 2010-04-14
I agree, someone, whether it is Netflix or not, someone will give the market what it wants. Unless they want to be like some in Hollywood and not smell the roses. But the fact that Netflix even exists says there are some that do.

---

### Post by Frak on 2010-04-14
> **jeremyjjbrown said:**
> Don't be so negative. 

People use MS out of habit because it's what ships on their machine. I just installed Ubuntu on my friends laptop because it wouldn't work with even a clean install of MS. I told him he didn't need malware protection and it's free and he asked why everyone isn't using it. My reply, 'I don't know'. People will use what works, give them time. Gmail users are in the 100's of millions right now, and they love their web apps. Everyone I've turned on to google docs has basically stopped using MS Office. I have a fork of Chrome OS beta on my netbook and I can say that it will be perfect for the average computer user on the go. It's a cloud based os for cloud based services exactly like Netflix. If netflix doesn't support them, someone else will, I guarantee it.
I'm not being negative, I'm being realistic. We live a capitalist world where the majority trumps the minority. Linux is the minority, and businesses will quickly oust them in favor of the majority.

Developing a Linux client would be very expensive, as Netflix would have to implement an entirely new DRM scheme for Moonlight.

---

### Post by jeremyjjbrown on 2010-04-14
If that's true then why is there a Hulu dedicated app for Linux already? With current IDE's it's not really the challenge it once was to develop for multiple targets.

---

### Post by Chronon on 2010-04-14
> **Frak said:**
> It could be implemented with little problems.



The Mono team is working on implementing PlayReady for Moonlight. I know what DRM is.

Interesting.  It seems to be listed [here](http://www.mono-project.com/Moonlight/SecurityStatus) as Unsupported rather than Partial or TODO.  Can you share where you got your information from?

---

### Post by Frak on 2010-04-15
> **Chronon said:**
> Interesting.  It seems to be listed [here](http://www.mono-project.com/Moonlight/SecurityStatus) as Unsupported rather than Partial or TODO.  Can you share where you got your information from?
They have to get permission from Microsoft beforehand.

---

### Post by toupeiro on 2010-04-15
> **Frak said:**
> I'm not being negative, I'm being realistic. We live a capitalist world where the majority trumps the minority. Linux is the minority, and businesses will quickly oust them in favor of the majority.

Developing a Linux client would be very expensive, as Netflix would have to implement an entirely new DRM scheme for Moonlight.

Linux has been growing exponentially faster in business than in the home desktop space. ... ?  Business begins to translate to residential over time, hence many of the home offices we have today, people working from home either for a company or for themselves, using a computer.  Microsoft wasn't always the majority... At one time, they were the underdog.

Finally, I fail to see how expensive its going to be..  The Wii runs a very stripped down linux kernel, and also now has the capability to do netflix streaming...  They're practically there...

---

### Post by Frak on 2010-04-15
> **toupeiro said:**
> Linux has been growing exponentially faster in business than in the home desktop space. ... ?  Business begins to translate to residential over time, hence many of the home offices we have today, people working from home either for a company or for themselves, using a computer.  Microsoft wasn't always the majority... At one time, they were the underdog.

Finally, I fail to see how expensive its going to be..  The Wii runs a very stripped down linux kernel, and also now has the capability to do netflix streaming...  They're practically there...
The Wii version simply uses a custom IOS that has the appropriate DRM scheme. I have that disc and I've been in the beta for some time. I've picked the IOSs apart, and it's no different than your normal game.

Also, if you can conjure up proof that it runs Linux, that'd be nice.

---

### Post by toupeiro on 2010-04-15
> **Frak said:**
> The Wii version simply uses a custom IOS that has the appropriate DRM scheme. I have that disc and I've been in the beta for some time. I've picked the IOSs apart, and it's no different than your normal game.

Also, if you can conjure up proof that it runs Linux, that'd be nice.

Just google it.  I came back with a handful of interviews with nintendo employees prior to its release that it runs a linux kernel.

---

### Post by aysiu on 2010-04-15
> **toupeiro said:**
> Just google it.  I came back with a handful of interviews with nintendo employees prior to its release that it runs a linux kernel.
Yeah, there's nothing about the Linux kernel itself that stops Netflix streaming. After all, the Roku box (which is designed to stream Netflix) runs on Linux. And the latest news is that Netflix is seeking Android developers to help create a Netflix Android app (and Android uses a Linux kernel).

---

### Post by toupeiro on 2010-04-15
> **aysiu said:**
> Yeah, there's nothing about the Linux kernel itself that stops Netflix streaming. After all, the Roku box (which is designed to stream Netflix) runs on Linux. And the latest news is that Netflix is seeking Android developers to help create a Netflix Android app (and Android uses a Linux kernel).

I know.  I was just bringing up the linux kernel points due to the fact that it was said it would be very expensive to do on a linux platform, when in reality they've already done it in a few cases.. (Wii, Roku, and it sounds like very soon, Android.)

---

### Post by aysiu on 2010-04-15
Links, by the way:
[Netflix Job Listing Calls For Android Developers, Instant Streaming On Nexus One Coming Soon](http://www.gadgetreview.com/2010/04/netflix-job-listing-calls-for-android-developers-instant-streaming-on-nexus-one-coming-soon.html)
[Roku Player Open Source Resources](http://www.roku.com/support/gpl_rdvp)

---

### Post by Ric_NYC on 2010-04-15
> [B]TiVo® Digital Video Recorder
[/B]Instantly watch movies & TV episodes streamed from Netflix &#8211; and record your favorite shows from cable and broadcast TV so you can watch them later at your convenience. The TiVo HD XL box saves up to 150 hours of HDTV **Netflix**.


Another Linux device that can access Netflix.

---

### Post by Frak on 2010-04-15
The conversation is about the Desktop platform, which due to the nature of the forums. The desktop client uses Silverlight, but the Moonlight client doesn't support PlayRight. (Or whatever it's called)

The cost to develop a new DRM scheme is more than the return value.

/thread

---

### Post by aysiu on 2010-04-15
> **Frak said:**
> The conversation is about the Desktop platform, which due to the nature of the forums. The desktop client uses Silverlight, but the Moonlight client doesn't support PlayRight. (Or whatever it's called)

The cost to develop a new DRM scheme is more than the return value.

/thread
I'm not trying to be cheeky here. I'm asking a sincere question here, because I am not a programmer.

From a technical standpoint, if you've developed an application for a non-desktop Linux, is it that difficult to get it to run a desktop Linux?

For example, I don't run servers, but if I want to add LAMP to my netbook installation of Ubuntu, it's a simple *apt-get* command away to add it.

My understanding is that Android runs applications as little self-contained Java sessions. If Netflix comes through on an Android app, how difficult would it be to create a Java-based client that runs on a regular Linux desktop installation?

---

### Post by Frak on 2010-04-15
> **aysiu said:**
> I'm not trying to be cheeky here. I'm asking a sincere question here, because I am not a programmer.

From a technical standpoint, if you've developed an application for a non-desktop Linux, is it that difficult to get it to run a desktop Linux?

For example, I don't run servers, but if I want to add LAMP to my netbook installation of Ubuntu, it's a simple *apt-get* command away to add it.

My understanding is that Android runs applications as little self-contained Java sessions. If Netflix comes through on an Android app, how difficult would it be to create a Java-based client that runs on a regular Linux desktop installation?
Well, it would be about the same effort. The problem lies in the device being used. Porting Netflix to iPhone or Android requires less oversight because one person cannot physically watch everything going on in the program without modifying the device itself. When publishing to a desktop platform, the user has access to a plethora of tools that can be used to break digital rights schemes. Therefore, the desktop platforms tend to be much more sophisticated than the mobile ones.

There is no current DRM scheme in Moonlight, and Netflix doesn't have a vested interest in developing alternative clients. The beauty of Silverlight is that it has a built in DRM scheme that is vetted. The desktop client can support high quality streams, and Silverlight helps the publisher ramp quality in real time. In this way, Silverlight is a dream come true for video publishers. The mobile platforms and the console platforms (excluding the PS3) use a degraded version of the videos since they cannot play the full high-def streams due to hardware demands (Wireless-G on many consoles is not as powerful as consumer laptops in many cases and video on the Wii is not the best). Netflix can ship degraded videos to these devices thus saving bandwidth on their end. Under Linux, the user could capture the stream, break the DRM, and waste precious bandwidth which is against Netflix and their respective publishers best interests. While this could also be done on Windows, it would be much more difficult. The financial cost of implementing a DRM scheme and player capable of meeting Netflix's wishes would be very costly, and they see no reason to extend the platform in that direction.

---

### Post by Chronon on 2010-04-15
I am not a programmer, per se, either but my understanding of the situation is basically this:

As the owners of the intellectual property (i.e. source code) I believe the only ones capable of porting this DRM to Linux is Microsoft.  Lacking source code, the Moonlight developers have to basically reverse engineer/hack the DRM.  If Moonlight had feature parity with Silverlight then we would be able to watch Netflix streams whether they were designed to be run in Linux or not.  

However, the DRM can't just trivially be implemented by a 3rd party so it's unlikely that we will see this on a desktop Linux system without Microsoft delivering some binary that will permit the DRM to work in Linux.  I believe that the set-top boxes (Roku, et. al.) have the DRM stuff built into the firmware of the SOCs they use.  (At least I have seen the claim forwarded on a couple of websites that the DRM is handled by the NXP PNX8935 system-on-chip used in the Roku and I find this a reasonable conjecture.)

I suppose that it wouldn't be too hard for Microsoft to port their code so that it runs in Linux (they could then supply binaries without sacrificing their intellectual property).  However, it's not clear to me that they see a desirable cost/benefit ratio in this course of action.

---

### Post by Frak on 2010-04-15
> **Chronon said:**
> I am not a programmer, per se, either but my understanding of the situation is basically this:

As the owners of the intellectual property (i.e. source code) I believe the only ones capable of porting this DRM to Linux is Microsoft.  Lacking source code, the Moonlight developers have to basically reverse engineer/hack the DRM.  If Moonlight had feature parity with Silverlight then we would be able to watch Netflix streams whether they were designed to be run in Linux or not.  

However, the DRM can't just trivially be implemented by a 3rd party so it's unlikely that we will see this on a desktop Linux system without Microsoft delivering some binary that will permit the DRM to work in Linux.  I believe that the set-top boxes (Roku, et. al.) have the DRM stuff built into the firmware of the SOCs they use.  (At least I have seen the claim forwarded on a couple of websites that the DRM is handled by the NXP PNX8935 system-on-chip used in the Roku and I find this a reasonable conjecture.)

I suppose that it wouldn't be too hard for Microsoft to port their code so that it runs in Linux (they could then supply binaries without sacrificing their intellectual property).  However, it's not clear to me that they see a desirable cost/benefit ratio in this course of action.
Correct.

---

### Post by toupeiro on 2010-04-16
> **Frak said:**
> Correct.

I just poked around NXP's website and I saw nothing so far indicating this "system-on-a-chip" (which means nothing, thats what Sun calls their UltraSPARC T-series chips.  Its marketing..) is capable of decoding encrypted WMV/WMA..  the NXP chip you referenced is an SD/HD video decoder that is used in MANY devices completely unaffiliated with roku or netflix.  Here's a [PDF]("http://www.nxp.com/acrobat_download2/literature/9397/75016106.pdf&sa=X&ei=fabIS9LOM46osgOqwpyYCw&ved=0CA4QzgQoADAA&usg=AFQjCNFZsM9z5FboCTMBknvo3FvUwl8ZIw") on this chip.


I'm not a programmer, but I am a systems administrator, and when looking at a Roku box running a commodity OS, its really not a whole lot different, **at all**, from a thin client running an embedded OS.  Having supported wyse thin clients, and various others, for the last decade running Wyse ThinOS, Windows and Linux, having a system using Non-volatile memory to store its OS and being able to keep it in a "ready only" operating mode does not imply in any form that the OS cannot be modified, in some cases rather easily.  To keep thin clients updated, you have to update the OS and software, same as the roku box.  The Roku box has packages associated with it which it runs, like any Linux OS.  In fact, issue #192 of Linux Journal talks about how you can develop custom channels for the Roku.  L.J. has written about the roku in a few different publications, [indicating that there is a DRM client which supports linux]("http://www.linuxjournal.com/content/roku%E2%80%94breaking-linux-not-invited-rule"), however its apparently not publicly available yet.  

Unless they've completely tossed DRM to the wayside (which the movie companies simply wouldn't allow), there is no way something like a Roku box would have ever seen the light of day without being able to support DRM.  By your logic, if they didn't completely reinvent a new DRM schema that supports linux, they would have to have gotten Microsoft to write a silverlight client that will run on linux. Really, all they need is something that supports encrypted WMA/WMV which is all DRM is with regard to Netflix.  It's highly unlikely Microsoft wrote a custom silverlight client for anything running a Linux OS, so my bet is on a piece of software, not necessarily open source, that supports streaming encrypted WMA/WMV, thus making it DRM compliant.

One could pretty easily begin to deduct that there is tremendous value in a linux DRM client for netflix, and in one form factor, its already delivered.  I'll stress again, if they did release a new DRM tool supportable on linux, it doesn't necessarily imply it HAS to be FOSS, which doesn't necessarily mean the source HAS to be supplied, which is why its probably not out in the open for anybody to compile.  In that context, it would be right on-par with any silverlight client on any Microsoft platform.

/re-threaded

---

### Post by Chronon on 2010-04-16
> **toupeiro said:**
> So are you implying that the content being played by a Roku box is DRM free?

I'm not a programmer, but I am a systems administrator, and when looking at a Roku box running a commodity OS, its really not a whole lot different, **at all**, from a thin client running an embedded OS.  Having supported wyse thin clients, and various others, for the last decade running Wyse ThinOS, Windows and Linux, having a system using Non-volatile memory to store its OS and being able to keep it in a "ready only" operating mode does not imply in any form that the OS cannot be modified.  To keep thin clients updated, you have to update the OS and software, same as the roku box.  The Roku box has packages associated with it which it runs, like any Linux OS.  

Unless they've completely tossed DRM to the wayside (which the movie companies simply wouldn't allow), there is no way something like a Roku box would have ever seen the light of day.  By your logic, if they didn't completely reinvent a new DRM schema that supports linux, they would have to have gotten Microsoft to write a silverlight client that will run on linux, which I think everyone knows is highly unlikely.  So, one could pretty easily begin to deduct that there is tremendous value in a linux client, and in one form factor, its already delivered.  Keep in mind, if they did release a new a DRM tool supportable on linux, it doesn't necessarily mean it HAS to be FOSS, which doesn't necessarily mean the source HAS to be supplied.  In that scenario, it would be right on-par with any silverlight clients on any Microsoft platform.

/re-threaded

Roku connects to the same Netflix streams as everyone else.  The streams bear DRM.  Roku has released all of the GPL source code related to the project.  The GPL source code doesn't contain the particular DRM handling needed.  Beyond this, it's just speculation.  We don't know the nature of any agreements that MS may have made with Roku.  We don't know who ported what.

---

### Post by toupeiro on 2010-04-16
> **Chronon said:**
> Roku connects to the same Netflix streams as everyone else.  The streams bear DRM.  Roku has released all of the GPL source code related to the project.  The GPL source code doesn't contain the particular DRM handling needed.  Beyond this, it's just speculation.  We don't know the nature of any agreements that MS may have made with Roku.  We don't know who ported what.

exactly!  Here's what we do know, however.  Roku runs linux.  Roku decodes DRM encrypted content. and from what I could find on this NXP processor, which was actually a lot, its not looking like it's by way of the piece of firmware mentioned above...  I don't really care if Microsoft wrote the tool, if its open source, proprietary, or what, but the hard fact is that there is already a functional, legal, tool that supports DRM on a Linux OS.  The arguement is that its too expensive to invent the wheel.  My point is, the wheel is already invented, and in fact rolling...

---

### Post by Frak on 2010-04-16
> **toupeiro said:**
> exactly!  Here's what we do know, however.  Roku runs linux.  Roku decodes DRM encrypted content. and from what I could find on this NXP processor, which was actually a lot, its not looking like it's by way of the piece of firmware mentioned above...  I don't really care if Microsoft wrote the tool, if its open source, proprietary, or what, but the hard fact is that there is already a functional, legal, tool that supports DRM on a Linux OS.  The arguement is that its too expensive to invent the wheel.  My point is, the wheel is already invented, and in fact rolling...
The case goes back to delivery and securing the media itself. The Roku box is nothing special (which you accused me of stating otherwise, which I didn't). The client used by Netflix uses some pretty new features in the latest Silverlight. Moonlight does not support those same features. Moonlight does not support the DRM that Silverlight does. Netflix, Novell, and Microsoft would need to enhance Moonlight with that. Microsoft sees no interest in supporting Moonlight with PlayReady.

Netflix isn't going to develop a client solely for Linux just so Linux users can watch Netflix. For the time and effort needed to build and maintain the application, along with the amount of users available, it comes out to a loss.

---

### Post by toupeiro on 2010-04-16
> **Frak said:**
> The case goes back to delivery and securing the media itself. The Roku box is nothing special (which you accused me of stating otherwise, which I didn't). The client used by Netflix uses some pretty new features in the latest Silverlight. Moonlight does not support those same features. Moonlight does not support the DRM that Silverlight does. Netflix, Novell, and Microsoft would need to enhance Moonlight with that. Microsoft sees no interest in supporting Moonlight with PlayReady.

Netflix isn't going to develop a client solely for Linux just so Linux users can watch Netflix. For the time and effort needed to build and maintain the application, along with the amount of users available, it comes out to a loss.

You're missing the point.. It's already been done, or Roku wouldn't exist!  The rest of your statement makes sense if you are using the following assumptions:

1)  The roku box is using a ported version of Silverlight
2)  Moonlight has been enhanced enough to support netflix streaming

I don't believe either of these two options is whats happened in the case of the linux based set-top device, Roku.

I'm subscribing to the idea that viewing encrypted WMA/WMV can be done, and is in fact being done, without a silverlight/moonlight client, and the software developer (person or company) who wrote the codec obtained the rights to do so legally, and partook in full MS logo compliance for their format, and in buying a roku box, you're also buying an entitlement to use the software its running.  Its been done PLENTY of times.  Theres no more or less facts out there that supports this versus Microsoft supporting silverlight on Linux based set-top devices...  I just believe, knowing microsoft and dealing extensively with Microsoft software licensing for companies I've worked for, that this is the most likely candidate.  I can always be wrong, but I dont think I am in this case.  Maybe its still being done in firmware.  By the looks of it, the NXP chip isn't the catalyst if thats the case.  Out of interest, I am still looking at anything firmware based in the Roku box that could deliver this.  So far, I'm coming up empty-handed.

---

### Post by Frak on 2010-04-16
> **toupeiro said:**
> Your statement makes sense if you are using the following assumptions:

1)  The roku box is using a ported version of Silverlight
2)  Moonlight has been enhanced enough to support netflix streaming

I don't believe either of these two options is whats happened in the case of the linux based set-top device, Roku.

**That's not what I said at all. Before responding again, re-read my post. I never said Roku used Silverlight. This is the second time you've accused me of saying something I haven't.**

---

### Post by toupeiro on 2010-04-16
> **Frak said:**
> **That's not what I said at all. Before responding again, re-read my post. I never said Roku used Silverlight. This is the second time you've accused me of saying something I haven't.**

Well then explain, exactly, what you are saying.  I've reread your posts.  No, you don't directly say its using silverlight, but you are implying that it would be too expensive to do anything else on linux DRM related, which is obviously a false statement considering it *is * being done on linux.  Try sending a clear message, and it will be interpreted more clearly.

PS. and learn what the word assumptions mean.  I never **accused** you of saying anything other than what you absolutely did say that I disagree with:

> I'm not being negative, I'm being realistic. We live a capitalist world where the majority trumps the minority. Linux is the minority, and businesses will quickly oust them in favor of the majority.



> 
The conversation is about the Desktop platform, which due to the nature of the forums. The desktop client uses Silverlight, but the Moonlight client doesn't support PlayRight. (Or whatever it's called)

The cost to develop a new DRM scheme is more than the return value.

The Microsoft developed client for **windows desktops**, and probably set-tops like the Xbox360 is silverlight.  I don't personally think they developed a new DRM schema, I'm saying that a company developed a new DRM compatible client for linux. that has format compliance with what silverlight decrypts from a DRM standpoint.  The only time I mentioned anything about a new DRM schema was in response to your statements, suggesting *possible* alternatives, not probable ones.   I don't know how to make myself any clearer than that

> Netflix doesn't have a vested interest in developing alternative clients.

> The financial cost of implementing a DRM scheme and player capable of meeting Netflix's wishes would be very costly, and they see no reason to extend the platform in that direction.

> Netflix isn't going to develop a client solely for Linux just so Linux users can watch Netflix. For the time and effort needed to build and maintain the application, along with the amount of users available, it comes out to a loss.

I argue that this work has already been done, not using existing software clients found on windows (obviously by your boldface font, we're in agreement here) but newly written DRM-supported client software to decrypt and display the content.  I've yet to find anything on the net from the chip-makers of the Roku to believe its firmware.  That doesn't mean its impossible, just undocumented from what I can tell so far.  

The reason I argue this is blatent and obvious without getting into any weeds whatsoever on the topic:  _because the Roku box, which Netflix officially does support, already runs the OS you so adamantly point out in different ways that they have no reason to, or vested interest in supporting, and they couldn't do that without a client being developed that the OS can run on the Roku box_.

The second reason is that its not in a chip manufacturers best interests not to disclose functionality of their chips and processors.  If its not in their docs, its probably not in their chips either, not something quite this significant.  Maybe I'll find that document that blows my whole position out of the water.  That would be fine with me too, but until that document materializes, my position is as good as anybodies.


The OS  doesn't become invalidated simply because one box is set-top and the other is desk-top.  You're saying they're not using silverling/moonlight, but that its also not in their interests to use/develop anything else because of costs, yet *something* is undoubtedly being used.  It seems like you're sort of making a point which .. kind of contradicts your point.  There obviously is value in developing this client, or it wouldn't have been done.  I don't care who developed it, how open it is, or how proprietary it is, in whatever form its in, it exists and functions legally within a linux operating system.

Being as I am now sounding like a broken record, If you still can't get what I'm trying to say, without thinking I'm accusing you of things I never accused you of, its doubtful we're going to get any further in trying to understand eachother on this issue.

---

### Post by Frak on 2010-04-16
> **toupeiro said:**
> Well then explain, exactly, what you are saying.  I've reread your posts.  No, you don't directly say its using silverlight, but you are implying that it would be too expensive to do anything else on linux DRM related, which is obviously a false statement considering it *is * being done on linux.  Try sending a clear message, and it will be interpreted more clearly.

We're talking about desktop Linux. If you cannot follow that, there's no point in arguing.

---

### Post by toupeiro on 2010-04-16
> **Frak said:**
> We're talking about desktop Linux. If you cannot follow that, there's no point in arguing.

And I'm saying linux is linux, what you compile it on has no weight here from a software client.  If you can't follow that, there's no point in arguing.  I've compiled linux for x86, sparc, MIPS, and several others.  It doesn't stop being linux because the platform changes, and the ability to compile source for different platforms doesn't vanish.  I've taken C code written for MIPS/IRIX and dropped it right on top of x64 linux and compiled it and I esentially ported an application from SGI to Linux in an hour.  Why is it so hard to accept that the same thing can't be done in the SAME OS and kernel on different hardware?

---

### Post by Frak on 2010-04-16
> **toupeiro said:**
> And I'm saying linux is linux, what you compile it on has no weight here from a software client.  If you can't follow that, there's no point in arguing.  I've compiled linux for x86, sparc, MIPS, and several others.  It doesn't stop being linux because the platform changes, and the ability to compile source for different platforms doesn't vanish.  I've taken C code written for MIPS/IRIX and dropped it right on top of x64 linux and compiled it and I esentially ported an application from SGI to Linux in an hour.  Why is it so hard to accept that the same thing can't be done in the SAME OS on different hardware?
But people have an easier time poking around in Desktop systems compared to embeddable systems. I can run a pretty un-secured Netflix client in an embeddable manner because nobody can poke around to get the media. Under desktop linux, the same application would be equivilent to giving a chocolate bar to a little kid. They can get off the outside wrapper, however messy they do it.

---

### Post by toupeiro on 2010-04-16
> **Frak said:**
> But people have an easier time poking around in Desktop systems compared to embeddable systems. I can run a pretty un-secured Netflix client in an embeddable manner because nobody can poke around to get the media. Under desktop linux, the same application would be equivilent to giving a chocolate bar to a little kid. They can get off the outside wrapper, however messy they do it.

Well, that is another issue altogether, not one of cost or function, but security, which I will defer to the most true thing I can think to defer to, no system or encryption is unhackable.  If a person has a will to compromise a netflix stream, embedded versus desktop is not going to be the element that thwarts them.  If that was truly a pivot point, we wouldn't have streaming to windows desktops either.  If there is a third party client, closed or open source, it had to pass Microsofts compliance to use it legally, and therefore would have to abide by the same security standards as a silverlight client.  Even if it was firmware, this would be true.  I'm not disagreeing with you that it wouldn't be easier on a desktop, I'm just saying that I don't believe thats why its on linux set-top and not on linux-desktop yet.

---

### Post by aysiu on 2010-04-16
I think what Frak is saying (please correct me if I'm misunderstanding) is that lacking DRM on an embedded Linux or appliance-like device is all right, because the vast majority of users (even most power users) won't want to go to the trouble to figure out how to pirate those streams. If you release a DRM-free Linux desktop client, there's absolutely no piracy control at all.

Whether you agree that DRM actually prevents people from pirating proprietarily-licensed media or not, the major movie studios *believe* DRM works, and so they put the pressure on Netflix to implement DRM (otherwise, no streaming movies), and so Netflix won't do Instant Watching without DRM. If the movie studios feel okay about a lack of DRM on appliances, then that's their call.

---

### Post by toupeiro on 2010-04-16
> **aysiu said:**
> I think what Frak is saying (please correct me if I'm misunderstanding) is that lacking DRM on an embedded Linux or appliance-like device is all right, because the vast majority of users (even most power users) won't want to go to the trouble to figure out how to pirate those streams. If you release a DRM-free Linux desktop client, there's absolutely no piracy control at all.

Whether you agree that DRM actually prevents people from pirating proprietarily-licensed media or not, the major movie studios *believe* DRM works, and so they put the pressure on Netflix to implement DRM (otherwise, no streaming movies), and so Netflix won't do Instant Watching without DRM. If the movie studios feel okay about a lack of DRM on appliances, then that's their call.

Then maybe I did miss the point.  I didn't gather this from what he was saying.  I think we're both of the impression that lacking DRM would violate too many agreements with movie distributors that Netflix does business with.  I think we've just got different opinion on how DRM is manifesting itself in a set-top linux solution, and whether its applicable to a desktop linux solution.  If its being delivered by firmware, thats probably a deal breaker for desktop linux, but if its not, then its strictly a matter of license and entitlement, which is what I believe is keeping the very same linux set-top client from desktop clients.

---

### Post by aysiu on 2010-04-16
I think any time there is a technical side of things and a marketing side of things, it's a bit of a tightrope walk. The important thing, as far as the studio execs are concerned, isn't whether technical implementations are consistent; it's really more about what makes them *feel* psychologically reassured that their cinematic properties are secured.

I'm not saying I know anything about how it's all implemented. Maybe there is DRM on Roku boxes. Maybe not. I don't know. I'm just saying as long as Hollywood execs think it's too difficult for people to pirate streaming movies off a Roku box, it's not necessarily true that Roku boxes have to have DRM... and I think that's what Frak is saying too. Again, not sure.

---

### Post by toupeiro on 2010-04-16
I've been burning through more of NXP's and Roku's documentation, it does look possible that they could be leveraging HDCP (High Bandwidth Digital Content Protection) which prior revsion 2.0 was limited to specific media interfaces, [however 2.0 appears to encrypt over anything]("http://en.wikipedia.org/wiki/High-bandwidth_Digital_Content_Protection"), including the HDCI and S-video interfaces on the back of the roku.  This may be sufficient enough encryption to satisfy DRM requirements, is the only thing I could find that even remotely smells like firmware DRM.  However, since the HDMI spec is now being natively incorporated into most modern desktop video cards and on-board video, this wouldn't necessarily be a showstopper for desktop linux if it were being leveraged.


EDIT:

HDCP appears to be a proprietary component of the HDMI specification and utilizing it would require a license, ergo, if a software or firmware tool were to leverage HDCP on any system, it would require a license for that client to do so.  Since Roku is a standardized offering, there is less red tape to get a device licensed as opposed to a software client meant a broad spectrum of hardware, which to me puts a little more foundation behind believing the only thing keeping it off linux desktops is license and entitlement, if I'm even close to the right page, that is..  Doesn't really matter, I guess, its all speculation.

Interesting reading up on this stuff, anyhow.


Cheers

---

### Post by jeremyjjbrown on 2010-04-17
> **aysiu said:**
>  The important thing, as far as the studio execs are concerned, isn't whether technical implementations are consistent; it's really more about what makes them *feel* psychologically reassured that their cinematic properties are secured.


Exactly and I'm saying once a critical mass of Chrome netbooks, powerful android 4G smartphones, and possibly linux touchscreen pads is reached those execs will no longer feel good about leaving money on the table. If device like the android phone is able to double or triple the number of everyday linux users (over 100,000 moto-droids sold in the first weekend), soon there will be the critical mass. At that point Fraks argument turns against him.

---

### Post by Ric_NYC on 2010-04-17
[B]2 scenarios:
[/B]

**Microsoft's Silverlight** running on Linux (Moblin):

[http://news.zdnet.com/2422-19178_22-345905.html](http://news.zdnet.com/2422-19178_22-345905.html)




Android* running on Ubuntu (Virtualbox):

[http://www.youtube.com/watch?v=0bKLibm5kME](http://www.youtube.com/watch?v=0bKLibm5kME)



"Netflix is looking for &#8220;a great engineer to help us build Instant Streaming client implementations on Android devices.&#8221; 



That could bring Netflix to Linux, I think.

---

### Post by AldenIsZen on 2010-04-18
> **Ric_NYC said:**
> [B]2 scenarios:
[/B]

**Microsoft's Silverlight** running on Linux (Moblin):

[http://news.zdnet.com/2422-19178_22-345905.html](http://news.zdnet.com/2422-19178_22-345905.html)

....



That could bring Netflix to Linux, I think.


 If Moblin is Linux, albeit on a phone, how hard would it be to port it to Ubuntu?

---

### Post by Pogeymanz on 2010-04-18
> **AldenIsZen said:**
> If Moblin is Linux, albeit on a phone, how hard would it be to port it to Ubuntu?

Knowing Microsoft, it probably checks to see if you are running Moblin and not some other Linux OS.

---

### Post by AldenIsZen on 2010-04-23
> **Pogeymanz said:**
> Knowing Microsoft, it probably checks to see if you are running Moblin and not some other Linux OS.
Is Moblin ported to PC?

---

### Post by Ric_NYC on 2010-04-23
No more "Moblin"

> Nokia and Intel are joining forces to combine their Linux-based platforms into a package called MeeGo, which is essentially Maemo and Moblin cores mashed together. (16-Feb-10)






> **Intel and Microsoft Announce Collaboration to Provide Great Experiences for Atom**


Posted in Announcement &#8226; September-23-2009 at 01:07 PM PST
As a team we are committed to continuing to extend the platform and operating system support of Silverlight to reach the broadest set of customers possible.  [B]Today, Intel announced at IDF (Intel Developer Forum) support for Silverlight 3 on their Atom-based devices. This collaboration is focused on enabling consumers to have a great out of the box experience for browsing the Web and we see Silverlight support as a key aspect of that.

These Atom-based devices run Windows 7 or Moblin, which is Intel&#8217;s preferred flavor of Linux for embedded scenarios[/B]. As part of this, Silverlight will become one of the technologies supported within Intel&#8217;s Atom Developer Program.  Developers can target Silverlight as a preferred client runtime and know they will get solid support on Atom-based devices.
 
Today, during her keynote at IDF, Renee James, Intel&#8217;s corporate vice president and general manager of Intel&#8217;s Software and Services Group and Ian Ellison-Taylor, our general manager for Client Platforms and Tools announced the collaboration. They also showed IIS Smooth Streaming on Atom-based devices running both Windows 7 and Moblin, demonstrating what developers and end users have to look forward to. 
 
**We are excited by further support of Silverlight by key industry leaders and how this collaboration delivers on Silverlight&#8217;s cross-platform, cross-browser, and cross-device promise by going beyond just the PC to allow developers to reach more endpoints for their applications and services**. We see this is a clear extension of our current efforts with Novell where we are building an open source implementation of Silverlight called &#8220;Moonlight&#8221; that is targeted at the broad range of Linux&#8211;based PCs.   
 
Now is a better time than ever to begin developing applications for Silverlight.

September 23, 2009




[http://team.silverlight.net/announcement/intel-and-microsoft-announce-collaboration-to-provide-great-experiences-for-atom/](http://team.silverlight.net/announcement/intel-and-microsoft-announce-collaboration-to-provide-great-experiences-for-atom/)

---

### Post by jeremyjjbrown on 2010-04-25
> **Ric_NYC said:**
> These Atom-based devices run Windows 7 or Moblin, which is Intel&#8217;s preferred flavor of Linux for embedded scenarios. As part of this, Silverlight will become one of the technologies supported within Intel&#8217;s Atom Developer Program. Developers can target Silverlight as a preferred client runtime and know they will get solid support on Atom-based devices.

Today, during her keynote at IDF, Renee James, Intel&#8217;s corporate vice president and general manager of Intel&#8217;s Software and Services Group and Ian Ellison-Taylor, our general manager for Client Platforms and Tools announced the collaboration. They also showed IIS Smooth Streaming on Atom-based devices running both Windows 7 and Moblin, demonstrating what developers and end users have to look forward to. 

This is impossible, Frak said so...

---

### Post by JPorter on 2010-05-11
> **jeremyjjbrown said:**
> this is impossible, frak said so...

:lol:

---

### Post by SlidingHorn on 2010-05-11
I just got off the phone with Netflix customer service.  The guy on the phone was very nice, and at first, gave me a canned response until I had **politely** explained that the company could be losing a good amount of money by not supporting linux users.  

He had basically said that there was nothing "on-the-record" to report, just a lot of hearsay in regard to whether or not they'd move to provide support.  I made sure to point out that while market share may be small at this point, new & easy to use distros like Ubuntu are out there and gaining ground every day.

He had promised to share the suggestion and information with his higher ups to pass along.

**Keep calling people!**

---

### Post by aysiu on 2010-05-11
> **SlidingHorn said:**
> I just got off the phone with Netflix customer service.  The guy on the phone was very nice, and at first, gave me a canned response until I had **politely** explained that the company could be losing a good amount of money by not supporting linux users.  

He had basically said that there was nothing "on-the-record" to report, just a lot of hearsay in regard to whether or not they'd move to provide support.  I made sure to point out that while market share may be small at this point, new & easy to use distros like Ubuntu are out there and gaining ground every day.

He had promised to share the suggestion and information with his higher ups to pass along.

**Keep calling people!**
Since there is no accurate data as to how many Linux users there are, let alone Linux users who use Netflix, the best thing to do would be to have some coordinated effort to show Netflix just how many users there are.

All you would do is tell all Linux users to cancel their Netflix service on a particular day. They can all reactivate their service the next day if they want. But if Netflix sees "Oh, wow! We felt that. All those users canceling at once!" that the Linux population is significant and, more importantly, that its lost revenue for Netflix would be significant.

---

### Post by Naitsirhc Hsem on 2010-05-11
I can see that happening, I would contribute

---

### Post by yoshimitsuspeed on 2010-05-14
> **aysiu said:**
> Since there is no accurate data as to how many Linux users there are, let alone Linux users who use Netflix, the best thing to do would be to have some coordinated effort to show Netflix just how many users there are.

All you would do is tell all Linux users to cancel their Netflix service on a particular day. They can all reactivate their service the next day if they want. But if Netflix sees "Oh, wow! We felt that. All those users canceling at once!" that the Linux population is significant and, more importantly, that its lost revenue for Netflix would be significant.

I'm in

---

### Post by jj4ester on 2010-05-14
I'd be in, too. Except that I'm piggy-backing on my mom's Netflix account. 
I did call Netflix customer service : 

                                                                1-866-716-0414
                         For faster service, use this service code: 595 272                     

The agent I talked to wasn't even sure if Linux ***wouldn't*** stream to a Linux machine. He said he has no idea if it ever would, either. He said he would pass the info on, though.

---

### Post by King of Dreams on 2010-05-18
Just curious if anyone has tried the plugin in IE running under Wine?  Performance would likely be sub-par, but I'm curious if it would work at all.

---

### Post by princemanjee on 2010-05-20
> **King of Dreams said:**
> Just curious if anyone has tried the plugin in IE running under Wine?  Performance would likely be sub-par, but I'm curious if it would work at all.

Didn't work... It was a pain just to get IE installed and when I did it required WMP which I could NOT get installed... tried everything I can think of with my limited knowledge.

Best I have been able to do in linux so far is Run a VM that has a Wintendo OS 4 GB of ram and run the VM from a Separate partition not just a *.VDI file. Video Quality is fair and audio just a hair worse but it slows down the machine so other tasks become impossible to do. This turns the machine into a TV and defeats the purpose of watching in the corner of the screen while I work.

---

### Post by lynne2009 on 2010-05-26
My understanding is that Netflix.com is not going to have streaming videos on Linux - they feel it is not in their economic interest - that we are few in number. :confused:

I have created a Yahoo Group to provide alternative TV and Movie Video Streaming sites for Ubuntu Linux OS both free and paying - please feel free to join the free Yahoo group link is below.

[http://tech.groups.yahoo.com/group/UbuntuLinux_TVMovieStreamingSites/](http://tech.groups.yahoo.com/group/UbuntuLinux_TVMovieStreamingSites/)

Have a nice day and evening! :)

Lynne

---

### Post by MooPi on 2010-05-26
Only way I get Netflix to work on my Linux box is through virtual XP. In fact I just finished watching a movie. Eventually Netflix Blockbuster or whoever survives the movie on demand transition will provide a universal or acceptable format for Linux because that is what will be running the tablets and portables that people want.

---

### Post by lynne2009 on 2010-05-26
> **MooPi said:**
> Only way I get Netflix to work on my Linux box is through virtual XP. In fact I just finished watching a movie. Eventually Netflix Blockbuster or whoever survives the movie on demand transition will provide a universal or acceptable format for Linux because that is what will be running the tablets and portables that people want.

The problem lies in April 2014 when Microsoft XP support patches end - if you can afford a new computer and upgraded Microsoft than you can continue with Netflix.com Video Streaming otherwise you might want to look into other Video Streaming resources then can run on Ubuntu Linux.  See my above post for Yahoo Group suggestions.

---

### Post by yoshimitsuspeed on 2010-05-27
> **lynne2009 said:**
> My understanding is that Netflix.com is not going to have streaming videos on Linux - they feel it is not in their economic interest - that we are few in number. :confused:

I have created a Yahoo Group to provide alternative TV and Movie Video Streaming sites for Ubuntu Linux OS both free and paying - please feel free to join the free Yahoo group link is below.

[http://tech.groups.yahoo.com/group/UbuntuLinux_TVMovieStreamingSites/](http://tech.groups.yahoo.com/group/UbuntuLinux_TVMovieStreamingSites/)

Have a nice day and evening! :)

Lynne

Why make a separate yahoo group where people have to sign up to one more thing and pay attention to one more thing when it's aimed at ubuntu and we are already using the biggest ubuntu resource right here? 
I won't sign up to yahoo groups. It's too much PITA for me and seems silly. I would follow a thread on the subject though. 
I pretty much live on Hulu right now. I have found a couple others but they seem like either rebadged Hulu or have pretty much the same shows.

A site would have to be at least as good as Netflix of Vongo for me to consider paying. Even those annoy me after a little while with the limited selections.

Maybe I should install a virtualbox again but I'd hate to do so.

---

### Post by Naitsirhc Hsem on 2010-05-27
Look at all of the posts here, it must mean something!

btw VBox as cool as it is still stinks for regular use!

---

### Post by Dr.FrankenMod on 2010-05-27
I have decide to get a RUKU.. I know somehow Microsoft is making money but  hopefully it will see me Thur until the day that we can watch Netflix on a Ubuntu box. Because we all know that Microsoft will come out with some different type codex that will make the current RUKU obsolete.
 

 Dr. FrankenMod

---

### Post by Frak on 2010-05-27
If Netflix cares, they'll port over. Until then, save your breath and find an alternative, whether it be a Roku box or running Windows in a VM.

---

### Post by dvwolfman on 2010-05-30
I love this idea, I cancelled netflix and protested the lack of Linux support...it's not like it wouldn't work, it's a tactic by partners of microsoft to kiss up to MS I think...favors for favors for money...

moonlight is a great idea, whoever though of that, you deserve a very good cup of Ubuntu from a small mountainside farm in Bolivia (best coffee I ever had) for thinking of the idea...moonlight calls it all into question really...in a way

Thanks:popcorn:

---

### Post by yoshimitsuspeed on 2010-06-04
Just canceled Netflix. I told them why and they didn't seem to give two craps I was leaving

---

### Post by ShawnX on 2010-06-13
There's a facebook group on this subject.
[http://www.facebook.com/pages/Bring-Netflix-To-Linux/128791593812850#!/pages/Bring-Netflix-To-Linux/128791593812850](http://www.facebook.com/pages/Bring-Netflix-To-Linux/128791593812850#!/pages/Bring-Netflix-To-Linux/128791593812850)

---

### Post by mwolfe on 2010-06-29
I've been doing some research on the issue to get to the bottom of how/why Windows, OSX, and these embedded linux devices can run netflix but my desktop can't -- It just didn't make sense. 

I formulated a fairly short blog here on the issue:
[http://www.wolfewebservices.com/blog/netflix-streaming-linux-ubuntu-desktop-microsoft-playready-drm-problem](http://www.wolfewebservices.com/blog/netflix-streaming-linux-ubuntu-desktop-microsoft-playready-drm-problem)


After reading this:[http://forums.silverlight.net/forums/t/94992.aspx](http://forums.silverlight.net/forums/t/94992.aspx)
(pretty long thread but very informative)

---

### Post by kmsalex on 2010-07-01
pation to get streaming
[http://www.facebook.com/topic.php?uid=6275848869&topic=15043](http://www.facebook.com/topic.php?uid=6275848869&topic=15043)

---

### Post by mwolfe on 2010-07-01
Facebook already had a petition for this here:
[http://www.facebook.com/topic.php?topic=9637&post=78352&uid=6275848869#topic_top](http://www.facebook.com/topic.php?topic=9637&post=78352&uid=6275848869#topic_top)

---

### Post by cptrohn on 2010-07-01
OK I didn't read the whole thread... but the way I understand it is NOW is that moonlight 3 is more than capable of streaming netflix right now... Netflix just won't give anyody except Apple and MS the DRM stacks to be able to play it as of now.

Now if somebody in the OS world could figure out the DRM stacks it should work.

---

### Post by Frak on 2010-07-01
> **cptrohn said:**
> OK I didn't read the whole thread... but the way I understand it is NOW is that moonlight 3 is more than capable of streaming netflix right now... Netflix just won't give anyody except Apple and MS the DRM stacks to be able to play it as of now.

Now if somebody in the OS world could figure out the DRM stacks it should work.
There are many legalities that keep DRM from being implemented. The hope is that Novell can one day get a legal permit to reproduce the DRM. We have people that can reverse engineer it, but in the United States at least, it is a breach of law.

---

### Post by JPorter on 2010-07-08
> **cptrohn said:**
> OK I didn't read the whole thread... but the way I understand it is NOW is that moonlight 3 is more than capable of streaming netflix right now... Netflix just won't give anyody except Apple and MS the DRM stacks to be able to play it as of now.

Now if somebody in the OS world could figure out the DRM stacks it should work.

It's the other way around.  Netflix isn't restricting anything, they want their service available on the maximum number of user PCs and devices.  Unfortunately, Netflix uses Microsoft's PlayReady DRM stack (inside Silverlight) for streaming authentication.

It's Microsoft that won't allow Novell to implement PlayReady DRM support in the Moonlight project.  If Moonlight had PlayReady support built-in, there would be no issue, streaming protected content would "just work" in the same way that it does in Silverlight.

That's not to suggest it's a single-issue challenge to getting full Netflix streaming working well on the Linux desktop... there are probably a number of display issues that would need to be worked out or fine-tuned, including hooks to the DRM output support in the Nvidia and ATI proprietary video drivers, but those are not really related to the streaming authentication barrier.  The lack of PlayReady support is the primary blocking issue.

---

### Post by parker.casey@gmail.com on 2010-07-15
> **JPorter said:**
> It's the other way around.  Netflix isn't restricting anything, they want their service available on the maximum number of user PCs and devices.  Unfortunately, Netflix uses Microsoft's PlayReady DRM stack (inside Silverlight) for streaming authentication.

It's Microsoft that won't allow Novell to implement PlayReady DRM support in the Moonlight project.  If Moonlight had PlayReady support built-in, there would be no issue, streaming protected content would "just work" in the same way that it does in Silverlight.

That's not to suggest it's a single-issue challenge to getting full Netflix streaming working well on the Linux desktop... there are probably a number of display issues that would need to be worked out or fine-tuned, including hooks to the DRM output support in the Nvidia and ATI proprietary video drivers, but those are not really related to the streaming authentication barrier.  The lack of PlayReady support is the primary blocking issue.

You can view that as something to blame MS for if you'd like, but the use of PlayReady was a conscious choice on Netflix's part. The people to blame are in Hollywood. The producers of movies don't want their content being streamed to anything that might not have definite DRM that they can control. Linux isn't exactly uniform, and I'm sure that scares the crap out of them.

This isn't the fault of Netflix, they are only doing business the way they can. In this economy, it would have made zero sense for them to go with no DRM (meaning only drm-free movies, which would be none or very few) or to not go with Microsoft ... which means cutting out 80% of the market. Microsoft did nothing wrong. They haven't stopped any work toward this working on Linux.

I realize most people who use linux are very similar to a girl dating a nerdy guy. You want to defend the indefensible, even when wrong. In this case ... linux and netflix aren't really meant to be. Go elsewhere.

---

### Post by mwolfe on 2010-07-15
> This isn't the fault of Netflix, they are only doing business the way they can. In this economy, it would have made zero sense for them to go with no DRM (meaning only drm-free movies, which would be none or very few) or to not go with Microsoft ... which means cutting out 80% of the market. Microsoft did nothing wrong. They haven't stopped any work toward this working on Linux.

Are you sure about this? I see several potentially false statements here. Hulu uses flash to stream video and that video is DRM protected as well. Furthermore, there are a number of linux devices out there which are able to stream netflix and I'm pretty sure they are also using PlayReady DRM.
I posted this already but I'll post it again since some people didnt read it: [http://wolfewebservices.com/blog/netflix-streaming-linux-ubuntu-desktop-microsoft-playready-drm-problem](http://wolfewebservices.com/blog/netflix-streaming-linux-ubuntu-desktop-microsoft-playready-drm-problem)
The problem is microsoft will not license the playready drm to non embedded linux devices for fear that somehow that will compromise the DRM. The PlayReady DRM works on OSX because microsoft actually builds/supports silverlight for OSX, whereas for linux microsoft just publishes some docs for novell (and some test suites I believe).  When microsoft says cross platform, all they really mean is windows/mac compatible (since thats all most people know about).

---

### Post by archeryrob on 2010-07-15
> **parker.casey@gmail.com said:**
> .... In this case ... linux and netflix aren't really meant to be. Go elsewhere.


  OK, I'm listening. what else is available?

---

### Post by jeremyjjbrown on 2010-07-22
Blockbuster streaming on Droid X has now rolled out. I saw a TV commercial today.

[http://nexus404.com/Blog/2010/06/23/motorola-droid-x-droid-x-to-stream-lots-of-video-verizon-announces-blockbuster-partnership-more/](http://nexus404.com/Blog/2010/06/23/motorola-droid-x-droid-x-to-stream-lots-of-video-verizon-announces-blockbuster-partnership-more/)

This means streaming video service on Android, which is basically a Linux distro. Another big step.

---

### Post by TracyO on 2010-07-26
I've called Netflix a few times to ask them to support Linux.  The most recent time was a few months ago, and the person I spoke to was friendly and indicated they were working on this.  Of course, it depends on the particular representative you get when you call.  Still I say, keep calling and making sure they know we're dissatisfied.

---

### Post by LordVeovis on 2010-09-06
> **Frak said:**
> There are many legalities that keep DRM from being implemented. The hope is that Novell can one day get a legal permit to reproduce the DRM. We have people that can reverse engineer it, but in the United States at least, it is a breach of law.

I just have to point out (because I am sick of your posts and how wrong you are) that once again you are wrong....

Reverse engineering software or hardware systems which is done for the purposes of interoperability (for example, to support undocumented file formats or undocumented hardware peripherals) is mostly believed to be legal, though patent owners often contest this and attempt to stifle any reverse engineering of their products for any reason.

Seeing as how this is for interoperability it can legally be RE'd.

How about you do some research and actually have some idea as to what you are talking about before making blanket statements that are wrong...

RE has been used in Linux / Linux software DOZENS of times if not HUNDREDS...  ReactOS is an entire OS designed by RE parts of windows, its legal...

Research wins arguments.

---

### Post by cklosowski on 2010-11-12
> **LordVeovis said:**
> 
Reverse engineering software or hardware systems which is done for the purposes of interoperability (for example, to support undocumented file formats or undocumented hardware peripherals) is mostly believed to be legal, though patent owners often contest this and attempt to stifle any reverse engineering of their products for any reason.

Seeing as how this is for interoperability it can legally be RE'd.

Actually, from what I have been reading recently, anything considered 'Industry Standard' and is a form of encryption (which DRM is, or at least the method of which the rights management is introduced includes a for of encryption), the publishing of a decryption method would be in violation of federal law. I just remember hearing about something like this when someone was arrested by the FBI after showing their educational content at a convention. I'd play it safe and wait ;). Story is below.

[http://www.informit.com/guides/content.aspx?g=security&seqNum=18](http://www.informit.com/guides/content.aspx?g=security&seqNum=18)

---

### Post by davidryder on 2010-11-15
> **LordVeovis said:**
> I just have to point out (because I am sick of your posts and how wrong you are) that once again you are wrong....

Reverse engineering software or hardware systems which is done for the purposes of interoperability (for example, to support undocumented file formats or undocumented hardware peripherals) is mostly believed to be legal, though patent owners often contest this and attempt to stifle any reverse engineering of their products for any reason.

Seeing as how this is for interoperability it can legally be RE'd.

How about you do some research and actually have some idea as to what you are talking about before making blanket statements that are wrong...

RE has been used in Linux / Linux software DOZENS of times if not HUNDREDS...  ReactOS is an entire OS designed by RE parts of windows, its legal...

Research wins arguments.

One thing I would have to add to this is that cracking copyright protection isn't legal. Regardless of the reason.

---

### Post by frannylee on 2010-11-15
I've called Netflix many times over the years about instant viewing for Linux OS and they are always "still working on it." I've also gotten quite a few reps who use Linux themselves (YAY!) But they aren't the techies or corporate and so have little influence. As  good a company as Netflix may be, I honestly do not think they are  working very hard to make it happen. No real pay-off I suppose.

Sometimes you just have to quit beating your head  against the wall and accept what there is for now until the change  you want becomes available or you can make it happen yourself.

[COLOR=Red][COLOR=Black]I  finally gave up[/COLOR] [/COLOR]and got "the box." I chose the Seagate - you can slide in a Seagate portable HD or connect any drive to a USB port. My dad has the simple Roku box. Both work great.
So now I watch Netflix Instant View on my  TV and even if I can't take that on the road, I have all the movies I can possibly watch at home any time I want and it was so worth doing. Don't know why I waited so darn long...I love it.
And there are a number of options besides Netflix including Youtube though I have not bothered to explore them yet.

By the way, Netflix carries a film called "Revolution OS" which is all about the development of Linux. Check it out.

---

### Post by alaukikyo on 2010-11-16
> **davidryder said:**
> One thing I would have to add to this is that cracking copyright protection isn't legal. Regardless of the reason.

legal if take in the law sense then it is legal in some countries and not legal in others.
if taken in ethical or moral sense then it is very very legal

---

### Post by HittingSmoke on 2010-11-18
I've read through this entire thread and seen not one mention of Media Center.

WMC can stream Netflix now. Is there any way to get that running on WINE? Or possibly a plugin for XMBC or MythTV using the old third party Netflix plugin before WMC implemented native support?

---

### Post by aysiu on 2010-11-18
> **HittingSmoke said:**
> I've read through this entire thread and seen not one mention of Media Center.

WMC can stream Netflix now. Is there any way to get that running on WINE? Or possibly a plugin for XMBC or MythTV using the old third party Netflix plugin before WMC implemented native support?
Windows Media Center uses Silverlight, same thing web browsers on Windows and Mac use to stream Netflix... same thing that doesn't work on Linux using Wine.

---

### Post by HittingSmoke on 2010-11-20
> **aysiu said:**
> Windows Media Center uses Silverlight, same thing web browsers on Windows and Mac use to stream Netflix... same thing that doesn't work on Linux using Wine.

Well damn, I tried :(

I'm really wanting to switch back to Ubuntu as my primary OS. I've accepted having to fight for PC gaming.

I keep my Netflix subscription just for the streaming service.

Guess I'll have to make peace with watching on my Xbox if I want my favorite OS back...

---

### Post by holiday on 2010-11-20
> **directhex said:**
> Define "concerned".

Microsoft want to push as many people onto Silverlight as possible, as it allows them to sell Windows Server for hosting, Expression for design, and Media Server for encoding tasks.

To achieve this, and to have ANY hope of supplanting Flash as the "rich media" framework of choice, they need to target as many systems as possible - and in the netbook age, that means they can't ignore non-Windows platforms. Even when it literally costs them money.

They've been actively helping Novell to achieve feature parity - supplying all the official test cases, answering any technical queries, and so on - but the important (symbolic) step is the codec thing.

Codecs, by and large, are covered by big nasty patents held by big nasty men. That's why most distributions don't, say, support MP3 playback out of the box ($0.75 per decoder app license fee on the codec, if you're being legit). Ever noticed the box in Totem to buy codecs? See [http://www.fluendo.com/shop/category/end-user-products/](http://www.fluendo.com/shop/category/end-user-products/) or [http://shop.canonical.com/product_info.php?products_id=242](http://shop.canonical.com/product_info.php?products_id=242) for an idea of what "licensed" codecs cost.

When Moonlight encounters some media it can't play, it'll offer to download some licensed codecs (codecs offering the same support as the Canonical link above), free of charge. Those codecs aren't free for the distributor (patents are held by many people, so many people need to get paid), so every person downloading those codecs via Moonlight is getting something free of charge which (in a world of patent licensing) has value. And the people paying those fees are Microsoft.

Microsoft are literally paying people to use Moonlight in a "legit" manner.

So are they "concerned"? I'd say so - they're concerned about proving how cross-platform Silverlight is, and how every content creator should buy lots of expensive Microsoft products to produce SL content. Netflix will be a headline item to show off, the way the Obama inauguration streams were for Moon's SL1 support

Good post.

---

### Post by cookiecaper on 2010-11-21
The DRM should be reverse-engineered anyway. It is definitely legal (imo, heh, not a lawyer) to reverse-engineer it and to publish technical information about the encoding. The DMCA explicitly allows reverse-engineering. The DMCA explicitly disallows distribution of tools intended to circumvent DRM (in a nutshell), but if you just write all the information needed for *someone else* not under the provisions of the DMCA to write and publish those tools, you should be clear legally.

I'm really surprised that there hasn't been a serious effort to crack this one yet. Let's stop arguing and waiting on Microsoft and take care of ourselves, as we've always done. This is getting pretty silly.

We already know that this runs fine on Linux -- Boxee runs it, TiVO runs it, both are Linux platforms. It's just a political matter with MS. When have we let that stand in our way?

---

### Post by cookiecaper on 2010-11-21
And it seems that the longer we wait on this the more we prove Microsoft's point -- the reason they oppose PlayReady DRM on the Linux desktop is the exposition to hackers that might "break" the DRM (see [http://www.wolfewebservices.com/blog/netflix-streaming-linux-ubuntu-desktop-microsoft-playready-drm-problem](http://www.wolfewebservices.com/blog/netflix-streaming-linux-ubuntu-desktop-microsoft-playready-drm-problem) ). Why doesn't someone just get this over with so that we can get the components we need?

---

### Post by czr114 on 2010-11-21
> **cookiecaper said:**
> And it seems that the longer we wait on this the more we prove Microsoft's point -- the reason they oppose PlayReady DRM on the Linux desktop is the exposition to hackers that might "break" the DRM (see [http://www.wolfewebservices.com/blog/netflix-streaming-linux-ubuntu-desktop-microsoft-playready-drm-problem](http://www.wolfewebservices.com/blog/netflix-streaming-linux-ubuntu-desktop-microsoft-playready-drm-problem) ). Why doesn't someone just get this over with so that we can get the components we need?

In all fairness, it's mainly the media companies who have their heads in the sand. For PlayReady to be viable, Microsoft salesmen have to be able to puff up its security to major copyright holders, regardless of the fact that a certain Swedish torrent site has more than Netflix, all without DRM.

It's the media companies which like to pretend that everything isn't already out there in pirate format, as they call for ever more DRM against those people who could have easily pirated the unencumbered version, but chose to try and support the artists by dealing with a mountain of technical and billing hassles.

Fortunately, copyright law all over the world is not as regressive as the DMCA, and certain jurisdictions allow people to reverse-engineer and strip DRM for scientific, artistic, or interoperability concerns. It is that latter point which will be exercised by somebody who simply wants to stream licensed content on the platform of their choice.

---

### Post by Ric_NYC on 2010-11-21
Can you still play movies on Amazon On Demand? I tried it today and it is not working. 
They have "free videos" that I could watch before.

Are they blocking Linux now?

I can play the videos on VirtualBox (Windows XP).

---

### Post by TracyO on 2010-11-23
After the Netflix rate increase for shipping DVDs, I called Netflix (again) to remind them that as a Linux user, I cannot take advantage of the instant option.

My customer service rep took the feedback and informed me that if they get enough calls about Linux and Microsoft continues to refuse to work with it, they'll switch movie players.  Apparently they've done this in the past.

I've been calling periodically for at least a year with no change yet, but I'm a big believer that they'll never change it if we don't continue reminding them that it's a problem.  Power in numbers!

Take a few minutes and give 'em a call.  1-800-715-2146

---

### Post by madjr on 2010-11-23
netflix should definitely change to flash

thank God, Hulu was not as dumb as they were.

and Voddler with a few tweaks can be made to work well too.

netflix is just another alternative, more will surely come. But i do hope they switch.

---

### Post by Legendary_Bibo on 2010-11-23
I just started using netflix for the past month and I love the service. I forgot about the incompatibilities until yesterday. You see I have a netbookish computer (It's the size of a netbook, but it has the power of a laptop, it's the only one of its kind that I found online). I've used it to watch netflix when I'm at school, or when I don't feel like dragging out my PS3 to my living room. Last night it was on the charger and unless I want to sit on the floor, I can't really use it. So for the first time in over a month I fired up my other laptop running Ubuntu and tried watching the videos on there, and I was sad to see this big apology letter instead of my movie. Hey, at least they want to support Linux, but I believe them when they say that MS won't let them. It would be very expensive and time consuming to switch to something else so we're pretty screwed. Also flash is not an option.

On a side note why is it that when you use a big *** laptop screen you don't notice its size until you use it again after using a tiny screen (netbook)?

Another side note, can someone recommend a standalone netflix player? How are the Roku boxes?

---

### Post by madjr on 2010-11-23
> **Legendary_Bibo said:**
> Hey, at least they want to support Linux, but I believe them when they say that MS won't let them. It would be very expensive and time consuming to switch to something else so we're pretty screwed. Also flash is not an option.

Another side note, can someone recommend a standalone netflix player? How are the Roku boxes?

how come flash is not an option?

if its for the drm, than thats false, its a fantasy that msft sold them. there are many ways to record/grab what ever is on your screen.

is as useless as those website scripts that "want to" forbid you from right clicking.. only the owner think its working, when in reality is annoying its users, just like this drm crap

---

### Post by Legendary_Bibo on 2010-11-23
> **madjr said:**
> how come flash is not an option?

if its for the drm, than thats false, its a fantasy that msft sold them. there are many ways to record/grab what ever is on your screen.

is as useless as those website scripts that "want to" forbid you from right clicking.. only the owner think its working, when in reality is annoying its users, just like this drm crap

Oh, I meant flash isn't an option because it doesn't work as well as silverlight. On netflix with silverlight HD videos load fast and don't stutter for me, but HD videos on something like youtube take forever to load, and the videos stutter.

---

### Post by jeremyjjbrown on 2010-11-24
> **Legendary_Bibo said:**
> Another side note, can someone recommend a standalone netflix player? How are the Roku boxes?

You can just use you PS3

[http://www.netflix.com/NRD/PS3](http://www.netflix.com/NRD/PS3)

---

### Post by jeremyjjbrown on 2010-11-24
> **Legendary_Bibo said:**
> Another side note, can someone recommend a standalone netflix player? How are the Roku boxes?

You can just use your PS3

[http://www.netflix.com/NRD/PS3](http://www.netflix.com/NRD/PS3)

---

### Post by SeijiSensei on 2010-11-24
> **Legendary_Bibo said:**
> HD videos on something like youtube take forever to load, and the videos stutter.

Are you using the "[Square]("http://labs.adobe.com/downloads/flashplayer10.html")" beta Flashplayer from Adobe?  There are both 32- and 64-bit versions.  The only time I see hiccups is when the server can't stream fast enough and the player has to wait.  

Speed of loading has as much to do with YouTube and your ISP as it does with Flashplayer. Ever try watching YouTube videos in the middle of the day when the traffic levels are lower?  They're much smoother.

---

### Post by Ric_NYC on 2010-11-24
> **Ric_NYC said:**
> Can you still play movies on Amazon On Demand? **I tried it today and it is not working**. 
They have "free videos" that I could watch before.

Are they blocking Linux now?

I can play the videos on VirtualBox (Windows XP).


**Solved**: it doesn't work on Chrome. I tried it on Firefox and it played the videos, including HD videos.


Now I need to find out why Chrome is not playing the videos.

---

### Post by anothermikemiller on 2010-12-08
Sorry to bump this thread as it has almost nothing to do with getting Netflix to work with Ubuntu.

The options are as follows:
1. Dual boot or use a virtual machine with an OS that supports Silverlight
2. Use a dedicated box
3. A bunch of hacky stuff that doesn't seem to work including Wine and Moonlight.

My issue is that I run an atom/ion platform that won't support a VM. I'm amazed with what VDPau can do, but full screen flash (or any other cpu heavy task) is barely acceptable. Do I really need to dual boot?

I canceled my Netflix citing scratched DVDs and lack of linux support (after being prompted to use the streaming function.) I've also called 2 other times to "ask" about support. This didn't go well for me. One rep confused the OS with a web browser, the other stated that it isn't supported except on OSX and Windows even after I cited the PS3, Wii, Roku, and Tivo that use linux or another OS.

Anyway, Android functionality is still being held-up due to the built-in DRM available in the OS not being stringent enough for the movie companies. This issue is that the thread has devolved into addressing. So, are there any FOSS DRM projects in the works? 

Lastly I would like to address a few loose ends.

There is linux support for Netflix, but it is proprietary and/or architecture dependant proved by the set-top boxes and internet ready TVs available.

Android and Google are not as open source friendly as most people seem to think. Android is mostly closed-source as well as most google apps (including large parts of their kernel patches and code that run the servers). I don't want to bash Google too hard as they are a positive role-model compared to most large corporations and they support the open source movement.

DRM requirements from the movie companies seem to be the real issue for Netflix, not Microsoft. They, like Hulu and others, have to appease the copyright holders to be able to offer content to platforms. All the blame (and possibly pressure) should be directed at them.

---

### Post by jadonchristensen on 2010-12-08
I keep watching this subject. Does Netflix have a future date set for making it available to Linux, beta program maybe?

---

### Post by aysiu on 2010-12-08
> **jadonchristensen said:**
> Does Netflix have a future date set for making it available to Linux, beta program maybe? No, they don't.

---

### Post by abumaia on 2010-12-08
> **jadonchristensen said:**
> I keep watching this subject. Does Netflix have a future date set for making it available to Linux, beta program maybe?
They like to say they're working on it.  In fact, they so enjoy saying it they've been saying it for the past few years now.

---

### Post by ArcticChicken on 2010-12-13
Has anyone contacted Fluendo about the possibility of viewing Netflix's streaming content on Linux?  They offer a legal WMV plugin for gstreamer.

[http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/](http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/)

---

### Post by ArcticChicken on 2010-12-13
Nevermind.  I think an entry in their FAQ covers it:

[i]Will I be able to play my DRM'ed Windows Media files with the Complete playback bundle or the Windows Media playback bundle ?

No, DRM support requires some special licensing from Microsoft and as of today they are not willing to give that license for the Linux operating system for security purpose.[/i]

---

### Post by jadonchristensen on 2010-12-16
Someone made a petition for Netflix Linux support here:
[http://www.petitiononline.com/Linflix/](http://www.petitiononline.com/Linflix/)

9573 Total Signatures as of today.

---

### Post by Frak on 2010-12-16
> **jadonchristensen said:**
> Someone made a petition for Netflix Linux support here:
[http://www.petitiononline.com/Linflix/](http://www.petitiononline.com/Linflix/)

9573 Total Signatures as of today.
That's great, I still wish you luck in getting Microsoft to care enough to release their DRM specification.

---

### Post by jadonchristensen on 2010-12-16
> **Frak said:**
> That's great, I still wish you luck in getting Microsoft to care enough to release their DRM specification.

It's already running on Linux on Roku players.

---

### Post by Frak on 2010-12-16
> **jadonchristensen said:**
> It's already running on Linux on Roku players.
That's hardware DRM decoding, though, not software.

---

### Post by mellery on 2010-12-18
[http://forums.darklordpotter.net/showthread.php?t=17530](http://forums.darklordpotter.net/showthread.php?t=17530)

These posts seem to imply you can watch instantly for netflix under wine with silverlight and a greasemonkey script.  But one or two of the instructions aren't as clear as they could be to me.  

Can people try those steps and explain what they did if it works?

I've included the steps here also, but there is more information in the above link

[http://www.crazyboomerang.com/files/blog/silverlight.js](http://www.crazyboomerang.com/files/blog/silverlight.js)

"Put that into a text document, and name it silverlight.js.

Any version of Wine will work, you might want to go with the most stable release though. After that, You install Silverlight. Copy the plugin file from the directory it creates when the plugin is installed, copy it, go to your browser of choice, go to browser:config or however you get to it on your browser, go to the plugin directory for your browser, paste it in there.

It should then work."

Also, my understanding is silverlight 2.0 is the version you want to use, I don't follow the steps about copying the plugin (what file?) to firefox's plugin directory

---

### Post by aysiu on 2010-12-18
Like all instructions I've seen for getting Netflix to run in Wine, those seem to be merely speculation. Note the phrase *should work*. I'll believe it when I see a video of it (and VirtualBox isn't the same thing--has to be Wine or strictly Linux native).

---

### Post by laldet on 2010-12-19
I know this method isn't exactly ideal for all Ubuntu users, but I will share how I stream Netflix on Ubuntu with minimal problems.

The main problem is that this requires you to have a Windows box somewhere in your house that you can install a program  called "PlayOn Media Server" ([www.playon.tv](www.playon.tv)) onto.  But I would imagine that some users, like me, do have a Windows computer somewhere in their house.

Step 1: Install PlayOn to Windows PC.
Direct Link: [http://playon.tv:8080/](http://playon.tv:8080/)
NOTE: THIS IS A 14-DAY FULLY FUNCTIONAL TRIAL  
After PlayOn is installed, open it up select the "Channels Tab" and enter your NetFlix account information in the Netflix Tab.  Click test to make sure it works then press "Apply".

That's it.  You should be done on your Windows machine.

Step 2: Install some type of UPNP supported program on Ubuntu

I am sure there are several but my personal preference is "Xbox Media Center" for Linux.  To install, refer to this guide: [http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide]("http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide")

After installed I opened up XBMC selected the "Videos" tab clicked "Add Source" selected "Browse" > clicked "UPnP Devices" and then Selected PlayOn.  

After it was added I click on PlayOn, it will then show a list of all supported channels.  From there I select Netflix and it works!

I hope this helps someone.

---

### Post by Naitsirhc Hsem on 2010-12-26
YOU WIN laldet!!

I am running playon in a minimal vbox install and using xbmc to stream to any of my computers, this is by far the best solution I have seen.  fully recommended to any other readers


thank you so much!!!

---

### Post by jerenept on 2010-12-26
> **laldet said:**
> I am sure there are several but my personal preference is "Xbox Media Center" for Linux.  To install, refer to this guide: [http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide]("http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide")

After installed I opened up XBMC selected the "Videos" tab clicked "Add Source" selected "Browse" > clicked "UPnP Devices" and then Selected PlayOn.  

I hope this helps someone.

XBMC fanboi here saying: it's XBMC Media Center, not XBOX Media Center (they abandoned the latter when they stopped supporting XBOX's.)

But this seems to be a very clever way to get Netflix support in Linux :)

---

### Post by dubie18 on 2010-12-27
Is there any way to get PlayOn to work past the 14-day trial?  Besides actually buying it, i mean.

---

### Post by parl8256 on 2010-12-28
> **lusich said:**
> Sign the petition!!!

I am not sure if this is a proper place to post this, but I thought some of you might want to add your names to this petition:

[http://linuxlock.blogspot.com/2009/05/netflix-where-art-thou.html](http://linuxlock.blogspot.com/2009/05/netflix-where-art-thou.html) (or [http://www.petitiononline.com/Linflix/petition.html](http://www.petitiononline.com/Linflix/petition.html))

I hope we get it to make an impact.

In my experience, on-line petitions are e-mail harvesters.

---

### Post by ectospasm on 2010-12-28
> **laldet said:**
> I know this method isn't exactly ideal for all Ubuntu users, but I will share how I stream Netflix on Ubuntu with minimal problems.

The main problem is that this requires you to have a Windows box somewhere in your house that you can install a program  called "PlayOn Media Server" ([www.playon.tv](www.playon.tv)) onto.  But I would imagine that some users, like me, do have a Windows computer somewhere in their house.

Step 1: Install PlayOn to Windows PC.
Direct Link: [http://playon.tv:8080/](http://playon.tv:8080/)
NOTE: THIS IS A 14-DAY FULLY FUNCTIONAL TRIAL  
After PlayOn is installed, open it up select the "Channels Tab" and enter your NetFlix account information in the Netflix Tab.  Click test to make sure it works then press "Apply".

That's it.  You should be done on your Windows machine.

Step 2: Install some type of UPNP supported program on Ubuntu

I am sure there are several but my personal preference is "Xbox Media Center" for Linux.  To install, refer to this guide: [http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide]("http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide")

After installed I opened up XBMC selected the "Videos" tab clicked "Add Source" selected "Browse" > clicked "UPnP Devices" and then Selected PlayOn.  

After it was added I click on PlayOn, it will then show a list of all supported channels.  From there I select Netflix and it works!

I hope this helps someone.

The problem with this is that it's a hack, and requires Windows *somewhere*.  I'm trying to eliminate Microsoft from my network, and this doesn't help.  We need native support for this thread to close.

---

### Post by jadonchristensen on 2011-01-10
How to run Netflix on Ubuntu Linux 01-10-2011 [ VirtualBox ]

The easiest way and the only way that I know of to get Netflix working on Linux is to use a Virtual Machine. 

-Install VirtualBox from Ubuntu Software Center
-Run Application > Accessories > VirtualBox
-Click New, accept the defaults
-Insert your Windows disk (I used XP)
-Select the new Machine that you created
-Click Start
-It should boot from the CD or press F12 to change boot
-Install Windows, Firefox, Silverlight

In XP, I take it one step further and install the Free Comodo Firewall (can limit access with password), block access to Internet Explorer, install the Firefox Add-on named Procon and block all other sites but netflix.com and related. I try to make sure that Windows VM is only used for Netflix.

Some tips for running Full Screen movies, screen resolution, etc.
-With XP running in the Virtual Machine, click Devices, Install Guest Additions (need to be XP admin)
-Guest Additions should prompt you to reboot the Windows VM when done installing
-Once Windows has started again, press RIGHT Ctrl + F, then press RIGHT Ctrl + G [this should get you full screen and automatically correct your resolution]

P.S. If you want to get rid of the annoying mini-bar at the bottom of the Full Screen VM...

-On the main VirtualBox screen
-Settings
-General
-Advanced
-deselect Mini Toolbar options
-Ok to save

---

### Post by aysiu on 2011-01-10
Seeing this: > **jadonchristensen said:**
> 
The easiest way and the only way that I know of to get Netflix working on Linux is to use a Virtual Machine. I'm just thinking this: > **ectospasm said:**
> The problem with this is that it's a hack, and requires Windows *somewhere*.  I'm trying to eliminate Microsoft from my network, and this doesn't help.  We need native support for this thread to close.

---

### Post by jadonchristensen on 2011-01-10
> **aysiu said:**
> Seeing this:  I'm just thinking this:

I agree with that, aysiu. This was just my work-around until it's native.

---

### Post by morty221 on 2011-01-12
has anyone tired finding the useragent for the roku/boxee units and modifying the UA on firefox. i had amazing success using a UA from my little sisters mac. i was stopped at the DRM screen. had the player loaded and everything.

---

### Post by ectospasm on 2011-01-12
> **morty221 said:**
> has anyone tired finding the useragent for the roku/boxee units and modifying the UA on firefox. i had amazing success using a UA from my little sisters mac. i was stopped at the DRM screen. had the player loaded and everything.

This is exactly the behavior I saw when I first tried to connect to Netflix with my Ubuntu HTPC.  Even if you could grab the UA from the Linux-based units, the DRM stack still ain't there.  This will never work natively until the powers that be decide to allow Novell (or whoever) to implement the DRM stack for Moonlight, and allow any Linux-based client to reach the Netflix service.  Or, if Netflix gets the go-ahead to ditch Silverlight for HTML5 (or whatever the intervening technology is).  This is purely a political/legal battle, not a technical one.

---

### Post by jadonchristensen on 2011-01-12
Why is there no one suing over monopoly issues. MS clearly has conspired to create a monopoly on this issue.

---

### Post by morty221 on 2011-01-13
well then what about cutting up silverlight, finding the DRM stack and coding that to work with moonlight. is there anyway to achieve this. if not then is there a way to emulate a roku box or something like that on an ubuntu platform. im kinda new to ubuntu so if im just making myself to look like an idiot please tell me now.

---

### Post by oldsoundguy on 2011-01-13
As stated over and over in this thread, it all boils down to DRM.  DRM will remain closed source as long as there is no other alternative to prevent copy/piracy of audio/video content.  
If Netflix is that important .. get a Blu-Ray set top box and use it for streaming.
It comes automatically on all new Blu-Ray players.

I know it is "not on my computer" viewing .. but I would much rather watch something on my 55" LCD with legitimate surround than on my 24" computer, even though it is cinema display with just stereo audio.
(setting up 5.1 or better on some sound cards is a hit and miss venture .. some digital outs do not work!)

---

### Post by Chronon on 2011-01-13
> **morty221 said:**
> well then what about cutting up silverlight, finding the DRM stack and coding that to work with moonlight. is there anyway to achieve this. if not then is there a way to emulate a roku box or something like that on an ubuntu platform. im kinda new to ubuntu so if im just making myself to look like an idiot please tell me now.

We don't have the code so we can't code it to work with Moonlight.

Emulating the Roku's hardware won't help us because we don't have the code that needs to run on the hardware.  (You might be able to dump the firmware from a real Roku, but it's basically the same situation as game ROMs -- it's copyrighted material and can't legally be distributed.)

---

### Post by morty221 on 2011-01-14
Is it possible to Install silverlight in wine and use it in firefox for linux. also has anyone heard about [www.silveos.com](www.silveos.com) its a website thats apparently a silverlight WebOS thats put up by microsoft. I visited it a few times but i neverget it to do anything. it doesn't try to download anything (accept silverlight itself) so its safe, i just get a white screen when i go there.

---

### Post by aysiu on 2011-01-14
> **morty221 said:**
> Is it possible to Install silverlight in wine and use it in firefox for linux. No, it's not.

---

### Post by alaukikyo on 2011-01-14
> **aysiu said:**
> No, it's not.

it is if the wine dev try to fix wine for silverlight 4.

---

### Post by ectospasm on 2011-01-14
> **morty221 said:**
> well then what about cutting up silverlight, finding the DRM stack and coding that to work with moonlight. is there anyway to achieve this. if not then is there a way to emulate a roku box or something like that on an ubuntu platform. im kinda new to ubuntu so if im just making myself to look like an idiot please tell me now.

Technically this is possible, but in the US you are inviting federal indictments for doing this, because essentially you're breaking the Digital Millennium Copyright Act (DMCA).  The same was true of deCSS for DVDs in Linux.  As I said earlier, this is a political/legal/economic battle, not a technical one.

---

### Post by Kalimol on 2011-01-14
> Why is there no one suing over monopoly issues. MS clearly has conspired to create a monopoly on this issue.

Vertical integration provisions just don't apply to computers. Even if they did, this isn't a pairing between the actual content generators (film distributors and television networks) and the hardware vendor. And it's not as if a corporation can be legally required to support every platform.

---

### Post by morty221 on 2011-03-06
Has anyone made any progress here. ive been trying for months bit i cant make anything work.

---

### Post by aysiu on 2011-03-06
> **morty221 said:**
> Has anyone made any progress here. ive been trying for months bit i cant make anything work.
No, not unless you like virtualization, remote control, or dual-boot.

---

### Post by Lynnwood on 2011-03-09
Hi, I am new to Linux and this is my first post!  I don't know if anyone posted the contact info requested, but here it is:

Netflix Corporate Office Info:

Netflix, Inc.
100 Winchester Circle
Los Gatos, California 95032

(408) 540-3700

SOURCE: SEC Filings
[http://ir.netflix.com/sec.cfm](http://ir.netflix.com/sec.cfm)

Direct your mail to one of these executives:
[http://www.netflix.com/MediaCenter](http://www.netflix.com/MediaCenter)

• Reed Hastings, Founder, Chairman and CEO
• Neil Hunt, Chief Product Officer
• David Hyman, General Counsel
• Leslie Kilgore, Chief Marketing Officer
• Patty McCord, Chief Talent Officer
• Andrew Rendich, Chief Service and Operations Officer
• Ted Sarandos, Chief Content Officer
• David Wells, Chief Financial Officer

DON'T FORGET TO _**REQUEST A REPLY**_.

---

### Post by Ric_NYC on 2011-03-17
> Amazon Launches Unlimited Streaming Service

For $79 a year, Amazon Prime members get access to 5,000 movies and TV shows.

"Amazon.com, Inc. today announced the launch of a new benefit for Amazon Prime members: unlimited, commercial-free, instant streaming of more than **5,000 movies and TV shows**. This new benefit is being added at no additional cost -- Prime membership will continue to be $79 per year. Movies and TV shows included with an Amazon Prime membership can be watched instantly on Macs, PCs and nearly 200 models of Internet-connected TVs, Blu-ray players and set-top boxes that are compatible with Amazon Instant Video."

(IFC)



Some competition?


It works on Linux:

[http://www.ainer.org/news/ubuntu-linux-mint-compatible-amazon-prime-unlimited-instant-video-streaming-now-available](http://www.ainer.org/news/ubuntu-linux-mint-compatible-amazon-prime-unlimited-instant-video-streaming-now-available)

---

### Post by fcomstoc on 2011-03-17
> **Ric_NYC said:**
> (IFC)



Some competition?


It works on Linux:

[http://www.ainer.org/news/ubuntu-linux-mint-compatible-amazon-prime-unlimited-instant-video-streaming-now-available](http://www.ainer.org/news/ubuntu-linux-mint-compatible-amazon-prime-unlimited-instant-video-streaming-now-available)


Yeah if their video list is as big as they say I might just have to cancel my netflix account and get Amizon Prime ...

---

### Post by Spartan0311 on 2011-03-18
5,000 titles? Not a bad start, and it`s cheaper. Sounds like switching might be in my future as well.

---

### Post by ectospasm on 2011-03-18
Amazon's selection is meager compared to Netflix, and many titles are $1.99 (or $2.99 for HD) for instant download, even if you have Amazon Prime (like I have had for years).  I have already complained to Amazon about this, and said they have to do better in order for me to drop Netflix.

I then called Netflix to complain about this situation again.  Not only did I get someone in customer service who claimed to be an avid Linux user themselves, when I escalated to his supervisor she claimed to be a Linux user too.  Until Amazon's "free" streaming collection rivals that of Netflix, I propose we apply pressure the only way we can.

I suggest that everyone reading this who already has a Netflix account call them and pass the message along.  I am but one voice, but if they get enough Linux users calling, they will have to use their position in the market to force Microsoft (doubtful they're the ones dragging their feet) or most likely the movie studios to let the situation change.  We do not have an audience with anyone but Netflix, let's organize for change!

---

### Post by it1013 on 2011-03-31
I agree. the pressure most come from us to netflix to act.

---

### Post by Ric_NYC on 2011-05-12
> [B]Netflix FINALLY Coming to Linux and Chrome OS
[/B]

Reports are coming in that Google and Netflix will soon be announcing the availability of a Chrome Web Store App or Extension that will enable Chrome OS and other Linux-based distros running Chrome/ium to access Netflix&#8217;s streaming movie and TV show catalog without the need for Microsoft&#8217;s Silverlight plugin. 



[http://www.ehomeupgrade.com/2011/05/10/netflix-finally-coming-to-linux-and-chrome-os/](http://www.ehomeupgrade.com/2011/05/10/netflix-finally-coming-to-linux-and-chrome-os/)

---

### Post by ectospasm on 2011-05-12
This is very good news.  Let's hope it happens.

---

### Post by davidryder on 2011-05-16
> **Ric_NYC said:**
> [http://www.ehomeupgrade.com/2011/05/10/netflix-finally-coming-to-linux-and-chrome-os/](http://www.ehomeupgrade.com/2011/05/10/netflix-finally-coming-to-linux-and-chrome-os/)

Wow... after two years! :D

---

### Post by Earsplit on 2011-05-22
I guess Transmission is going to see a lot more use from me until this gets fixed...

---

### Post by dsfitzpat on 2011-05-23
I've been quite happy with Amazon Instant Video on my Ubuntu desktop.  I think you need a Windows PC if you want to download videos and watch them offline unfortunately, but once you buy something it stays on Amazon's servers forever and you can access it from anywhere, as long as you're online.
I haven't bothered with movies yet, but it seems to be the best way to legally access Doctor Who from the US :-)  (In Canada the Space Channel streams current episodes, but not so with SyFy in the US, sadly.)
I even have access to the current season (at a premium - instead of $0.99 per episode I pay $1.89 per episode with a subscription).

---

### Post by Super_Dork_42 on 2011-05-25
I just got off the phone with a guy at netflix that uses ubuntu. He said that netflix would be open to fully support linux if somebody could write a limited version of drm that only restricted netflix so it couldn't be downloaded from the stream. By fully support, he means it just works with no backdoor programs to get around stuff. Someone NEEDS to get something like that written. That is the end-all-be-all solution. I don't code yet but I think there is at least one person on this site that has enough experience to get this done, right?

---

### Post by loaba on 2011-06-01
> **Super_Dork_42 said:**
> I just got off the phone with a guy at netflix that uses ubuntu. He said that netflix would be open to fully support linux if somebody could write a limited version of drm that only restricted netflix so it couldn't be downloaded from the stream. By fully support, he means it just works with no backdoor programs to get around stuff. Someone NEEDS to get something like that written. That is the end-all-be-all solution. I don't code yet but I think there is at least one person on this site that has enough experience to get this done, right?
I think the problem is that someone here could right the necessary code. The other side to that coin is, because of the open-source nature of Linux, someone else probably has the tools to crack that code. I could be completely wrong in my assessment...

---

### Post by Laforge129 on 2011-06-01
> **loaba said:**
> I think the problem is that someone here could right the necessary code. The other side to that coin is, because of the open-source nature of Linux, someone else probably has the tools to crack that code. I could be completely wrong in my assessment...

No your absolutely right.   Netflix is just scared if they allow streaming someone will steal the content, but my argument is if they are so worried about stealing the content there are plenty of other services available already to go watch these shows.   That is the kicker.

---

### Post by ectospasm on 2011-06-01
> I think the problem is that someone here could right the necessary code. The other side to that coin is, because of the open-source nature of Linux, someone else probably has the tools to crack that code. I could be completely wrong in my assessment...

See, that someone has to be someone(s) like Google.  The studios aren't going to let some schmo have the keys to the kingdom.  No way no how.  And it's not Netflix's bag.

> No your absolutely right. Netflix is just scared if they allow streaming someone will steal the content, but my argument is if they are so worried about stealing the content there are plenty of other services available already to go watch these shows. That is the kicker.


Like I said, it's not not Netflix's deal.  They'd love to open the content to the widest possible audience, but I think it's ultimately the studios' misconception that having Linux DRM means they'd necessarily get hacked.  I think our best bet is for Google to implement the proper DRM in ChromeOS, and by extension, Chrome browser in basic Linux.  Netflix wants this as bad as we do, but their hands are tied since Netflix is not a content owner, just a content pusher.

---

### Post by Laforge129 on 2011-06-01
> **ectospasm said:**
> Like I said, it's not not Netflix's deal.  They'd love to open the content to the widest possible audience, but I think it's ultimately the studios' misconception that having Linux DRM means they'd necessarily get hacked.  I think our best bet is for Google to implement the proper DRM in ChromeOS, and by extension, Chrome browser in basic Linux.  Netflix wants this as bad as we do, but their hands are tied since Netflix is not a content owner, just a content pusher.

They Will never truely support Linux, If you read this article you will be amazed at the discussion some had with an Netflix employee:

[http://www.techrepublic.com/blog/opensource/the-netflix-linux-conjecture-how-netflix-snubs-the-linux-community/1745](http://www.techrepublic.com/blog/opensource/the-netflix-linux-conjecture-how-netflix-snubs-the-linux-community/1745)

I'll let you decide but there would be no cost to Netflix if they let us handle the DRM. I have no problem with DRM if they would allow it on the Linux machines.   I seriously doubt they are concerned with linux just yet.   It took them forever to go the Apple Machines, it is as if they are just dragging their feet in the mud trying desperately to hold off opening it up to Linux machines!

---

### Post by ectospasm on 2011-06-01
> **Laforge129 said:**
> They Will never truely support Linux, If you read this article you will be amazed at the discussion some had with an Netflix employee:

[http://www.techrepublic.com/blog/opensource/the-netflix-linux-conjecture-how-netflix-snubs-the-linux-community/1745](http://www.techrepublic.com/blog/opensource/the-netflix-linux-conjecture-how-netflix-snubs-the-linux-community/1745)

I'll let you decide but there would be no cost to Netflix if they let us handle the DRM. I have no problem with DRM if they would allow it on the Linux machines.   I seriously doubt they are concerned with linux just yet.   It took them forever to go the Apple Machines, it is as if they are just dragging their feet in the mud trying desperately to hold off opening it up to Linux machines!

How many times do I have to scream this?  It's not Netflix dragging their feet, it's either Microsoft (due to Netflix's reliance on Silverlight) or more likely the content producers (Movie/TV studios) that won't allow the powers that be (at first Novell with Moonlight, and now Google) to implement the DRM stack in Linux.  I've called Netflix at least three times, even canceling my subscription the first time.  At least the last customer service representative I spoke with--and his manager--agreed that they were strong supporters of Netflix streaming on Linux.  They are mere foot soldiers, and could probably be paying lip service to us.  They did assure me they'd pass my complaints along to the right people, or at least up the chain.  So we need to keep up the pressure.

Maybe Google can succeed, because they're at least bigger and have more clout than Novell ever could at this stage.  I am holding my breath, but it may not happen.  If it does happen, I'd be surprised if Google writes a plugin to work with Mozilla, or any non-Chromium-based browser.  DRM is not the kind of thing that can be open-sourced completely.  Any DFSG-like nuts are crazy to expect that level of openness.

---

### Post by Laforge129 on 2011-06-03
> **ectospasm said:**
> How many times do I have to scream this?  It's not Netflix dragging their feet, it's either Microsoft (due to Netflix's reliance on Silverlight) or more likely the content producers (Movie/TV studios) that won't allow the powers that be (at first Novell with Moonlight, and now Google) to implement the DRM stack in Linux.  I've called Netflix at least three times, even canceling my subscription the first time.  At least the last customer service representative I spoke with--and his manager--agreed that they were strong supporters of Netflix streaming on Linux.  They are mere foot soldiers, and could probably be paying lip service to us.  They did assure me they'd pass my complaints along to the right people, or at least up the chain.  So we need to keep up the pressure.

Maybe Google can succeed, because they're at least bigger and have more clout than Novell ever could at this stage.  I am holding my breath, but it may not happen.  If it does happen, I'd be surprised if Google writes a plugin to work with Mozilla, or any non-Chromium-based browser.  DRM is not the kind of thing that can be open-sourced completely.  Any DFSG-like nuts are crazy to expect that level of openness.

It isn't the content providers.   If it were they wouldn't allow me to stream their shows on my Kubuntu OS.   I've already watched the Big Bang Theory from my linux machine and discovery channel clips and shows.   I must re-interate it isn't the content providers it is the license holders.   They want you to come to them not to Netflix, but that is the besides the point.   Netflix isn't pushing the issue because they are DRAGGING Their feet on this.   I know, because I have been watching all the drama.   If Netflix wanted to they could do it easily.   Afterall, The Roku is linux machine.    So yes if they are so worried about DRM they wouldn't of ported to the Roku box!

---

### Post by pbhill on 2011-06-09
> **DavidFourer said:**
> I talked to a phone rep at Netflix who said, off the record, that they will probably switch to something Linux compatible soon.

I just called them and got the exact same story... two years later!

---

### Post by Laforge129 on 2011-06-12
> **pbhill said:**
> [QUOTE=DavidFourer;6872360]I talked to a phone rep at Netflix who said, off the record, that they will probably switch to something Linux compatible soon.

I just called them and got the exact same story... two years later![/QUOTE]

Oh That sounds like they are just reading a script.   Just to have a place to almost answer the question!!

---

### Post by Thewhistlingwind on 2011-06-12
> **Laforge129 said:**
> Oh That sounds like they are just reading a script.   Just to have a place to almost answer the question!!

You didn't suspect that the FIRST time they said it?

---

### Post by v1ad on 2011-06-12
i heard that Netflix was coming to chrome OS soon. if that happens i'm pretty sure you can download the app in the  chrome store once that happens maybe we can actually use Netflix?

---

### Post by ant2ne on 2011-06-13
[http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/]("http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/")

---

### Post by hebetude on 2011-08-11
Indeed you can watch it on Linux, if your Linux is made by company packaging the right plugins err cash into Netflix's pockets.

Here's the results with latest Chrome on 11.04 or Chrome 13 beta on Ubuntu 11.04

[COLOR=#333333][FONT=arial][LEFT][FONT=arial]
[LIST]
[*]Windows
[LIST]
[*]Windows XP with Service Pack 2, Vista or Windows 7
[*]Internet Explorer 6.0 or higher; or Firefox 3 or higher; or Chrome 7 or higher
[*]1.2 GHz processor
[*]512 MB RAM
[/LIST]
 
[*]Mac
[LIST]
[*]An Intel-based Mac with OS 10.4.11 or later
[*]Safari 3 or higher; or Firefox 3 or higher
[*]1 GB RAM
[/LIST]
 
[*]Chrome OS
[LIST]
[*]A Google Chromebook with Chrome OS 13 or higher
[/LIST]
 
[/LIST]
[/FONT][/LEFT]
[/FONT][/COLOR]

---

### Post by mamamia88 on 2011-08-11
Is there a reason this is such a big deal to so many people?  When at home I would much rather watch netflix on my tv via my ps3 or my xbox 360.   Aren't linux users mostly geeks who usually have a lot of gadgets?

---

### Post by hebetude on 2011-08-11
It's not always a problem until Iron Man 2 encoding sent to PS3 was broken.  Taking my laptop around the house watching Hulu is awesome.  But Im watching Hulu since Netflix (still) is preventing Linux access.

---

### Post by aysiu on 2011-08-11
> **mamamia88 said:**
> Is there a reason this is such a big deal to so many people? It's not a *big* deal. It's just a deal. It's not no deal, and it's not a big deal... just a deal.

---

### Post by jadonchristensen on 2011-08-11
> **mamamia88 said:**
> Is there a reason this is such a big deal to so many people?  When at home I would much rather watch netflix on my tv via my ps3 or my xbox 360.   Aren't linux users mostly geeks who usually have a lot of gadgets?

Lots of reasons. It's about choice, fairness, options, etc. Netflix currently has the best streaming selection for the money, IMHO. I want to watch that on Linux without having to use Windows. Right now, I have to either dual boot or watch in a Virtual Machine. It would be much more convenient to just have it available for Linux.

---

### Post by ectospasm on 2011-08-11
> **hebetude said:**
> ...the right plugins....

Care to post a link that tells us what these "right plugins" are?

---

### Post by mamamia88 on 2011-08-11
> **jadonchristensen said:**
> Lots of reasons. It's about choice, fairness, options, etc. Netflix currently has the best streaming selection for the money, IMHO. I want to watch that on Linux without having to use Windows. Right now, I have to either dual boot or watch in a Virtual Machine. It would be much more convenient to just have it available for Linux.  very true.  i want to build an htpc soon and want it to be an all in one media box.   linux has vlc and can play pretty much any video i throw at it.    i have a ps3 and 360 that can do streaming but would love to not have to flip the channel for netflix.

---

### Post by Thewhistlingwind on 2011-08-11
> **mamamia88 said:**
> .   linux has vlc and can play pretty much any video i throw at it.

So does windows, for that matter.

Of course, thats not really what you had in mind is it?

---

### Post by Ric_NYC on 2011-08-11
It's getting exciting!

> The search giant has confirmed today that Chromebooks, (the Samsung Series 5, Acer AC700 and CR- 48 ) will finally have Netflix streaming access, a feature that was one of the most requested since the beta CR-48 devices were sent out to testers. 
...

One note for CR- 48 owners, you cannot watch HD films, only low-res. This has been verified by me.



[http://www.afterdawn.com/news/article.cfm/2011/08/10/chrome_os_finally_gets_netflix_streaming_access](http://www.afterdawn.com/news/article.cfm/2011/08/10/chrome_os_finally_gets_netflix_streaming_access)





Let me update my CR- 48 and see what happens!:popcorn:

---

