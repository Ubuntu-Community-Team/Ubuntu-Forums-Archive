---
title: "HOW To: IE6 with wine 20050725"
date: 2005-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by humanity_to_others on 2005-08-21
Let's install wine package, first:
> Add wine repository to sources:
 ```
sudo gedit /etc/apt/sources.list
```
 ```
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```
Installation:
```
sudo apt-get update
sudo apt-get install wine
```

Then you can try Sidenet Wine Configuration Utility [here](http://sidenet.ddo.jp/winetips/config.html). I think this is easier and better than winetools. You can install Ie in many languages including:
> Arabic(ar) Blazilian Portuguese(br) Czech(cs)
Simplified Chinese(cn) Traditional Chinese(tw)
Danish(da) Dutch(nl) English(en) Finnish(fi) French(fr)
German(de) Greek(el) Hebrew(he) Hungarian(hu) Itarian(it)
Nihongo(ja) Korean(ko) Norwegian(no) Polish(pl)
Portuguese(pt) Russian(ru) Spanish(es) Swedish(sv) Turkish(tr) with Windows Media Player 7.1 and if you have Windows98 licence, you can install DCOM98, too.

---

### Post by nad on 2005-08-21
Why?

---

### Post by audax321 on 2005-08-21
[QUOTE=nad]Why?[/QUOTE]

Well IE6 sucks and everything, but some websites actually require it. For example the application for medical school at [www.amcas.org](www.amcas.org) actually requires that the application be filled out on Internet Explorer or Netscape. It's a sad reality.

---

### Post by sneax on 2005-08-21
Also some applications that run in Wine use IE as embedded browser solution. Steam for example.

---

### Post by traherom on 2005-08-21
It's actually 'wine IEXPLORE.EXE'

But nice guide... now I just have to figure out why it crashs on me the moment it starts up. ;)

--EDIT--
It always fails with:
> fixme:actctx:CreateActCtxW stub!
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:advpack:create_tmp_ini_file Unable to create temp ini file
fixme:shell:NTSHChangeNotifyRegister (0x40106,0x00008003,0x0003f5f4,0x00000410,0x00000001,0x7b98eaa0):semi stub.
fixme:shell:SignalFileOpen (0x00000000):stub.
fixme:mlang:fnIMultiLanguage_GetLcidFromRfc1766
fixme:imm:ImmGetContext (0x4010a): stub
fixme:mlang:fnIMultiLanguage_GetLcidFromRfc1766
fixme:mlang:fnIMultiLanguage_GetLcidFromRfc1766
fixme:mlang:fnIMultiLanguage_GetLcidFromRfc1766
fixme:msvcrt:_abnormal_termination (void)stub
fixme:msvcrt:_abnormal_termination (void)stub
fixme:mlang:fnIMultiLanguage_GetLcidFromRfc1766
fixme:actctx:CreateActCtxW stub!
fixme:atl:AtlModuleInit SEMI-STUB (0x35c74be0 0x35c74000 0x35c50000)
fixme:atl:AtlModuleUpdateRegistryFromResourceD stub 0x35c50000 (L"C:\\Windows\\System\\DXTRANS.DLL"), #0069, 1, (nil), (nil)
fixme:imm:ImmDisableIME (-1): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub


It appears that the advpack thing didn't work... maybe? I don't know.

---

### Post by traherom on 2005-08-22
Ok, got it fixed, sorta. Here's how I have it working:

The first time you start IE, run it with some address like [www.google.com](www.google.com).
```
wine ~/.wine/drive_c/Program\ Files/Internet\ Explorer/IEXPLORE.EXE www.google.com
```

Then, change your homepage to something such as, say, [www.google.com](www.google.com) and you can launch it the normal way from then on! :D

---

### Post by tom-ubuntu on 2005-08-22
[QUOTE=audax321]Well IE6 sucks and everything, but some websites actually require it. For example the application for medical school at [www.amcas.org](www.amcas.org) actually requires that the application be filled out on Internet Explorer or Netscape. It's a sad reality.[/QUOTE]
Email them, telling them a lot are using Firefox, and also a few Linux or Mac. I hate this, if a webpage requires a certain browser, just because the webmaster/developer was not able to be standart compliant.

---

### Post by gammyhand on 2005-08-22
[QUOTE=joeuser]Email them, telling them a lot are using Firefox, and also a few Linux or Mac. I hate this, if a webpage requires a certain browser, just because the webmaster/developer was not able to be standart compliant.[/QUOTE]
 To answer the "why" question from a technical point of view....

I am a web developer. We NEED (if we are any good) to test cross-browser. We can't use an OS that won't let us test our products in a commercial environment. A main reason I held off installing linux while I was working from home.

---

### Post by SirKalten on 2005-08-22
:: coughs ::

Netscape, Safari or Internet explorer are the common ones.  As sad as it is, even though FF is similar enough to Netscapes core (Gecko power) it doesn't reg...

Why they require IE I suppose I'll never know.  Done some web design here and there with PHP & MySQL but I don't see any realistic need to restrict it to a single browser...  Nevertheless, its how it is I suppose...  As for IE 6, if you have Wine, and I'm assuming you're dual booting, just boot into windows... 

Just my 2 cents =)

---

### Post by gammyhand on 2005-08-23
I didn't say it should be limited to one browser. I said it had to work cross-browser. Like it or not, most of the free world uses IE. You would have to be pretty arrogant to ignore it.

---

### Post by AndyAWS on 2005-08-23
And as someone who has done a bit of web developement I can say that it isn't that hard to keep a web site cross-browser and multi OS complient, unless you use Front Page as your DE or any Active-X stuff, which isn't really nessessary for anything these days.

As a web developer I always had the latest IE, Netscape, Mozilla and Opera browsers available for testing, it's just common sense. And I mainly used Macromedia's products for page development. 

Developers that go the quick and easy route with, Front Page and templates, are the ones that will end up with IE only pages.

It is also arrogant and ignorant to ignore that there are other browsers that are being used.

---

### Post by gammyhand on 2005-08-23
[QUOTE=AndyAWS]And as someone who has done a bit of web developement I can say that it isn't that hard to keep a web site cross-browser and multi OS complient, unless you use Front Page as your DE or any Active-X stuff, which isn't really nessessary for anything these days.

As a web developer I always had the latest IE, Netscape, Mozilla and Opera browsers available for testing, it's just common sense. And I mainly used Macromedia's products for page development. 

Developers that go the quick and easy route with, Front Page and templates, are the ones that will end up with IE only pages.

It is also arrogant and ignorant to ignore that there are other browsers that are being used.[/QUOTE]
 Sorry, and I don't want to cause offence with what I say, but a professional developer would not use frontpage anyway. And it is ***not*** easy to make sites work cross browser successfully. Macromedia dreamweaver (I presume that is what you use for coding) is a design tool and not a development tool. It handles the visual layout and is backed up with the ability to edit markup.

Zend Studio is a development environment (IDE - Integrated Development Environment) which is used for web development in PHP / MySQL. A lot of people confuse a web designers role with a web developers. And in a lot of companies the two are mixed. I tend to do a lot of html markup and client side scripting as well as my "official" role as a web developer.

CSS for starters... IE is not standards complient. So you have to write CSS that works on a standards complient browser, and then use a lot of hacks so it works on IE.

XHTML (or HTML) is pretty easy. If it validates in one it will validate in most.

Client side scripts also need to have server side equivalents in case client side scripting is disabled.

Our test machine at work has IE6, Netscape 7.2, Firefox1.04 as critical browsers where full functionality is required and is mission critical. Then we have IE5. Netscape 6, and Opera where there should be no visual irregularities but a few interaction issues can be overlooked. And then we have IE4, Opera 6 and Netscape 4.8 which must render a legible page. 

Obviously all pages are validated to W3C standards.

---

### Post by AndyAWS on 2005-08-23
I agree...CSS does complicate cross-browser compatability. At the time I was creating web pages I really didn't mess with XML much, it was fairly new. But even using Javascript with DHTML you had to be careful because of differences in IE and Mozilla/Netscape (Firefox wasn't out back then). I never had any issues with PHP and MySQL. And yes I used Dreamweaver as my main editor, although I also used Flash, and Fireworks for some flashy things and Image mapping.

And I didn't say it was easy, I said it's not *that* hard  ;-) 
You just have to be careful.
But it does take time and I was probably under a lot less time constraint as I was working from home in my spare time, and mainly for a small online gaming site, and some personal web sites (No Big-Business interests).

I would like to say that I manage to do 99% of my browsing with Firefox (and sometimes Epiphany), but for that 1% I still keep Wine and IE installed. ](*,) 
So the Web Developers out there are doing most things right.

---

### Post by gammyhand on 2005-08-23
> **AndyAWS]I agree...CSS does complicate cross-browser compatability. At the time I was creating web pages I really didn't mess with XML much, it was fairly new. But even using Javascript with DHTML you had to be careful because of differences in IE and Mozilla/Netscape (Firefox wasn't out back then). I never had any issues with PHP and MySQL. And yes I used Dreamweaver as my main editor, although I also used Flash, and Fireworks for some flashy things and Image mapping.

And I didn't say it was easy, I said it's not *that* hard   said:**
> (*,) 
So the Web Developers out there are doing most things right.
 Well as a professional web developer I would say that our biggest headache is making cross browser sites that are accessible :)

---

### Post by arunsub on 2005-09-23
I installed Wine and sidenet. How do i run MSN messenger?

---

### Post by kingbilly on 2005-09-24
i'd like to add to the WHY question.

I used this, and failed, to get MyMathLab to work for my online math at college.  I still have to dual boot and go into windows.  It upsets me that they can't release their special plugin on other OS's.

A bit off topic, but since i'm already ranting about commercial software...  My math class requires me to download quicktime to watch .mov files ever so often with the my mathlab.  So i have to download the windows quicktime and it come with Itunes.   I'm not sure if Itunes still has spyware, but this makes me upset too.  I want to ask the head of the distance learning department why i have to install music software on my computer just to take the class.  Math140 = Itunes... WHAT?

---

### Post by jacksbox on 2005-09-27
[QUOTE=kingbilly]I'm not sure if Itunes still has spyware[/QUOTE]

Nope, no spyware with iTunes.

---

### Post by PatrickMay16 on 2005-10-05
[QUOTE=SirKalten]As for IE 6, if you have Wine, and I'm assuming you're dual booting, just boot into windows...[/QUOTE]
Aww... But that's no fun!

EDIT: Oops... I bumped an old topic without realising it... Sorry.

---

