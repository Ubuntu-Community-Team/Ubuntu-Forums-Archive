---
title: "Web development: *buntu, possible???"
date: 2008-08-23
forum: Programming Talk
---

### Post by radical3 on 2008-08-23
hey 
ive used windows for a long time, blah blah blah , 
anyway i started dual booting ubuntu some time ago, thanks to the large number of problems i had the "pleasure" of fixing i really got to know it well. however i didnt really use it for serious stuff, because i was used to all the windows stuff i already have. 
anyway eventually windows died and i had to reinstall, it wiped grub, but instead of reinstalling grub i downloaded and installed xubuntu instead (over my ubuntu) ........ and what can i say <joygasm> its [insert bad word]ing AWSOME </joygasm>
due to its awesomeness i decided i would do EVERYTHING  in xubuntu , however ive failed at the first hurdle. 

web development.
i already use quanta, it pretty much puts dreamweaver in the bin, so the actual development process, is a no brainer, the real problem is....... fixing sites broken in internet explorer.(thanks bill)
ive installed ies4linux internet explorer 6.0  and ....well... i dont think it works properly. 

ive got a whole bunch of sites (not live) that are broken in internet explorer, mainly css problems, so a few divs are out of whack. but in ies4linux some of the css doesent even show up at all.

ive been bouncing back and forth between xp and xubuntu testing sites and breaking some on purpose to see what it looks like in ies4linux, just doesent work. 


long story short 
[SIZE="4"]
SOLUTIONS, IDEAS , INPUT, ANYTHING, PLEASE[/SIZE]
thanks in advance, im gonna have to boucne back to xp now:(:(:(:(:(.

---

### Post by mike_g on 2008-08-23
I dont know how you could get ies4linux to work, but if you just want to check your page layout you could submit your page to [browsershot](http://browsershots.org/)

---

### Post by radical3 on 2008-08-23
Thats not gonna work for localhost development. i need to develop the sites locally BEFORE they go live, its also how i edit them. 

is there no way to do this on *buntu, i dont want to give up xubuntu just as ive discovered it, but like 70% of my computer time is on developing websites, 20% graphics to go on the website, and the usual 10% por... err  entertainment. 

PLEASE SOMEONE HELP

---

### Post by mujambee on 2008-08-23
Don't you know anyone who has a very old laptop they don't use?

I used to run XP on my old P-III+500Mb RAM, if it is only to check on IE you won't need much more.

P.S. : And no, I still use it so it's not available ;)

---

### Post by pfdevil on 2008-08-23
download vmware, pop a copy of windows xp on it. Test your website.

---

### Post by LaRoza on 2008-08-23
In Web Development, the best solution is testing natively in what you are testing. So if you want to test IE6 in Windows XP, you should use IE6 in Windows XP. 

A virtual machine as mentioned is a great way to do this, or dual booting or finding a computer with this browser.

---

### Post by evymetal on 2008-08-23
I'll just point out that you'd have exactly the same problem if you were using windows as your main machine - how do you know what it will look like on a Mac or on Linux without having machines running them?

In fact this is the only reason we have any windows computers where I work. All the designers and html/css people use OSX, most of the other developers use Ubuntu / Fedora, and then we have a machines that boot Vista, XP and OSX so we can test everything.

---

### Post by radical3 on 2008-08-23
Thanks everyone, im not gonna run vmware, or anything like that, but im not gonna give up xubuntu, because that OS moves faster than firefox's market share. 

im gonna build/edit everything in xubuntu using using quanta, test in firefox, then boot into windows to clean up in IE6 before sending live.  


quanta, firefox, xubuntu . i still cant believe people give this stuff away for free. 

[spam][Ext2 IFS]("http://www.fs-driver.org/"), rocks[/spam]

---

### Post by linkmaster03 on 2008-08-24
Why not use a VM? It works like a charm. I use it for all Windows testing.

---

### Post by R.Bucky on 2008-08-24
I second, third and fourth that motion. VMWare is the way to go.

---

### Post by Vadi on 2008-08-24
Virtualbox (very easy to setup and use, way easier than vmware) + windows xp installed it covers my cross-platform needs.

---

### Post by linkmaster03 on 2008-08-25
I use Virtualbox as well.

---

### Post by radical3 on 2008-09-05
why would i boot into xubuntu then > boot into windows when i could just boot into windows?????
that doesent make sense.

*hooray ive installed linux, all the free apps hooray*

*now i need to install windows, so i can use my linux???*

i built a massive customized joomla-based site in xubuntu with quanta, (since i planned to build in xubuntu [on localhost] due to speed, then fix in windows with IE) turned out the site was completely broken in IE, had to start from scratch. So i went back to using IE tab in firefox on windows for the whole thing. 

Its a shame, i wish i could use xubuntu more. i guess you cant have your speed and use it too.........sorry its: you can have your cake and eat it too.

---

### Post by LaRoza on 2008-09-05
> **radical3 said:**
> 
Its a shame, i wish i could use xubuntu more. i guess you cant have your speed and use it too.........sorry its: you can have your cake and eat it too.

I don't get it. Are you saying you are using Windows because Ubuntu is a hassle? Now how do you test in Linux? 

Virtual machines are great for testing without having to reboot.

---

### Post by radical3 on 2008-09-06
[QUOTE=LaRoza]I don't get it. Are you saying you are using Windows because Ubuntu is a hassle? Now how do you test in Linux? 

Virtual machines are great for testing without having to reboot.[/QUOTE]

If you read this thread from the start you would would be well aware that i was initially concerned that in xp i could build a site and test it on the fly with internet explorer While on localhost. However when i installed ies4linux it gave an incorrect representation of the site, so i was unable to test sites whilst on localhost in internet explorer, this means i pretty much couldn't work in xubuntu if i couldn't test the site in the most used browser. 

People responses were to use browsershots.com......NO they didnt read what i wrote either, LOCALHOST.
And now im being told to use virtualbox, meaning i will have to build on localhost in xubuntu > upload the site to the internet everytime i save > open up/switch to xp then test in internet explorer.

Or work out some sort of network between the the OS's

Or just use the virtual box's half xp to build the whole thing.

Or maybe something else, i dont know, no one actually gave a real solution just a bunch of one line posts.

Ive been using xp since my last "broken site in IE" catastrophe , havent booted into xubuntu since so i came back to the forums to probe for a solution/reasonable workaround but im guessing it doesent exist.what am i supposed to do now :confused:

---

### Post by mike_g on 2008-09-06
> People responses were to use browsershots.com......NO they didnt read what i wrote either, LOCALHOST.
I just re-read your original post, perhaps you would like to as well:
> hey
ive used windows for a long time, blah blah blah ,
anyway i started dual booting ubuntu some time ago, thanks to the large number of problems i had the "pleasure" of fixing i really got to know it well. however i didnt really use it for serious stuff, because i was used to all the windows stuff i already have.
anyway eventually windows died and i had to reinstall, it wiped grub, but instead of reinstalling grub i downloaded and installed xubuntu instead (over my ubuntu) ........ and what can i say <joygasm> its [insert bad word]ing AWSOME </joygasm>
due to its awesomeness i decided i would do EVERYTHING in xubuntu , however ive failed at the first hurdle.

web development.
i already use quanta, it pretty much puts dreamweaver in the bin, so the actual development process, is a no brainer, the real problem is....... fixing sites broken in internet explorer.(thanks bill)
ive installed ies4linux internet explorer 6.0 and ....well... i dont think it works properly.

ive got a whole bunch of sites (not live) that are broken in internet explorer, mainly css problems, so a few divs are out of whack. but in ies4linux some of the css doesent even show up at all.

ive been bouncing back and forth between xp and xubuntu testing sites and breaking some on purpose to see what it looks like in ies4linux, just doesent work.


long story short

SOLUTIONS, IDEAS , INPUT, ANYTHING, PLEASE
thanks in advance, im gonna have to boucne back to xp now.
So, where in that did you specify the LOCALHOST bit? From what I can tell you were asking for:
> SOLUTIONS, IDEAS , INPUT, ANYTHING, PLEASE
And using browser shot was my idea :) Seriously tho, chucking your dummy is not going to help here :p

---

### Post by Paul41 on 2008-09-06
I have done testing with VMware also. The reason you would want to do that instead of dual boot is that you can have Windows open and go back and forth between the 2 just like any other program you have open...no need to reboot. I have been able to test on localhost this way by using the ip address of the linux machine. No need to post it out to your live server.

---

### Post by radical3 on 2008-09-06
forget it i'll just stick to xp, from what i can tell if i use linux to build im gonna have to use xp anyway, so forget a half speed xubuntu and a half speed xp, when i can just have a full speed xubuntu. its not you guys fault, its just how it has to be.:(

---

### Post by Paul41 on 2008-09-06
Use XP if you like but have you ever actually tried vmware or virtualbox? It won't be 1/2 speed for either. If you like xubuntu why not try it before you decide its going to be slow and no good. Would there be any loss?

---

### Post by radical3 on 2008-09-06
> **Paul41 said:**
> Use XP if you like but have you ever actually tried vmware or virtualbox? It won't be 1/2 speed for either. If you like xubuntu why not try it before you decide its going to be slow and no good. Would there be any loss?

im well past the "trying" stage with *buntu ive been using x/ubuntu for months, but during those times i was concentrating on other things such as video , images and other media rather than site building, x/ubuntu performed well in those areas, but site building is a no go.I just have to deal with that.

i use vbox in windows all the time to run pcbsd, i know how to use it.

---

### Post by Vadi on 2008-09-06
I find it quite easy, but web development can mean a lot of things... but in my case, places -> connect to server is a wonder, especially that I can use the default text editor to edit files just fine on the server.

---

### Post by radical3 on 2008-09-07
> **mike_g said:**
> I just re-read your original post, perhaps you would like to as well:

So, where in that did you specify the LOCALHOST bit? From what I can tell you were asking for:

And using browser shot was my idea :) Seriously tho, chucking your dummy is not going to help here :p

after the first persons "solution" post [#3]("http://ubuntuforums.org/showpost.php?p=5648495&postcount=3")

[QUOTE=radical3]Thats not gonna work for **localhost** development. i need to develop the sites** locally BEFORE they go live**, its also how i edit them. 

is there no way to do this on *buntu, i dont want to give up xubuntu just as ive discovered it, but like 70% of my computer time is on developing websites, 20% graphics to go on the website, and the usual 10% por... err entertainment. 

PLEASE SOMEONE HELP[/QUOTE]

@vadi

[QUOTE=Vadi]I find it quite easy, **_but web development can mean a lot of things._**.. but in my case, places -> connect to server is a wonder, especially that I can use the default text editor to edit files just fine on the server.[/QUOTE]

for now it just means what i want it to mean. building sites and having a good way to test them on IE with xubuntu, so that xubuntu actually becomes a solution and i dont have to use XP, or XP in xubuntu.
thanks for the input.

---

### Post by mike_g on 2008-09-07
> after the first persons "solution" post #3
Ok, so lets clarify things here. Your original post #1 makes no mention about the site being offline. My post (#2) suggested browsershot.You replied in post #3 saying that your site is offline. You then complained that I could not read o_O Now, how was I supposed to know that at the time? >_<

---

### Post by radical3 on 2008-09-07
> **mike_g said:**
> Ok, so lets clarify things here. Your original post #1 makes no mention about the site being offline. My post (#2) suggested browsershot.You replied in post #3 saying that your site is offline. You then complained that I could not read o_O Now, how was I supposed to know that at the time? >_<

This is unnecessary, why are people here always so defensive, i just want a solution, not an argument over localhost or remote host.:(

---

### Post by mike_g on 2008-09-07
lol, first you accuse me of not being able to read, then you try to argue that you had told me, which I had to point out was after I posted. Now you are complaining that this has become an argument. If you simply had the decency to admit that you made a mistake then this would never have been an argument.

---

### Post by radical3 on 2008-09-07
> **mike_g said:**
> lol, first you accuse me of not being able to read, then you try to argue that you had told me, which I had to point out was after I posted. Now you are complaining that this has become an argument. If you simply had the decency to admit that you made a mistake then this would never have been an argument.

Im wrong you are right, you are great, all hail mike_g*libc*.=D>

ego bloated enough??? have we gone off topic enough???:) 

This doesn't change anything i still need a solution :(.

---

### Post by Joeb454 on 2008-09-07
I think we should put this back on-topic instead of arguing over what was said and making the thread get more and more off-topic

---

### Post by radical3 on 2008-09-07
> **Joeb454 said:**
> I think we should put this back on-topic instead of arguing over what was said and making the thread get more and more off-topic

Great and you solution to my dilemma is............???

---

### Post by Paul41 on 2008-09-07
> **radical3 said:**
> Great and you solution to my dilemma is............???

The only solution that I have been able to find is to use a virtual machine witch will allow you to test locally. It won't slow your machine like you think it will and it is so much more convenient than booting into Windows to test. In the end it makes testing just like having both Firefox and IE open and testing in XP. I have done this with a lot of success and it sounds like a lot of other people here are doing the same thing with success. To me it sounds like you don't understand how the virtual machine would work. That's not a knock against you, I didn't either at first but when I finally gave in and tried I was surprised at how easy it made testing.

Like I said before if you don't like this idea and you want to go back to only XP that's no problems for me. You just asked for a solution to your problem and this is a solution so take it for what it's worth :).

---

### Post by radical3 on 2008-09-07
> **Paul41 said:**
> The only solution that I have been able to find is to use a virtual machine witch will allow you to test locally. It won't slow your machine like you think it will and it is so much more convenient than booting into Windows to test. In the end it makes testing just like having both Firefox and IE open and testing in XP. I have done this with a lot of success and it sounds like a lot of other people here are doing the same thing with success. To me it sounds like you don't understand how the virtual machine would work. That's not a knock against you, I didn't either at first but when I finally gave in and tried I was surprised at how easy it made testing.

Like I said before if you don't like this idea and you want to go back to only XP that's no problems for me. You just asked for a solution to your problem and this is a solution so take it for what it's worth :).

with that solution im still using xp arent i??? i cant build in linux and finish in linux but i can build in xp and finish in xp.

as for not understanding virtualbox: new machine > give name > allocate ram > dynamically expanding harddisk (usually 8gigs) >settings > iso > usb enable > video memory 32+ >start machine. 

[i made clear im very familiar with virtual machines in this post]("http://ubuntuforums.org/showpost.php?p=5740781&postcount=20")

isnt there some sort of linux based developer tool that can warn me of an "IE broken" site.

---

### Post by Paul41 on 2008-09-07
> **radical3 said:**
> with that solution im still using xp arent i??? i cant build in linux and finish in linux but i can build in xp and finish in xp.

as for not understanding virtualbox: new machine > give name > allocate ram > dynamically expanding harddisk (usually 8gigs) >settings > iso > usb enable > video memory 32+ >start machine. 

[i made clear im very familiar with virtual machines in this post]("http://ubuntuforums.org/showpost.php?p=5740781&postcount=20")

isnt there some sort of linux based developer tool that can warn me of an "IE broken" site.

There is not tool like that that I have found. You already found ies4linux but like you I found that unreliable. Sounds like your only option is to use XP with what you want.

---

### Post by radical3 on 2008-09-07
> **Paul41 said:**
> There is not tool like that that I have found. You already found ies4linux but like you I found that unreliable. Sounds like your only option is to use XP with what you want.

**Are you sure there is absolutely no other way**:(, other than using xp(virtually or not).

---

### Post by Canis familiaris on 2008-09-07
@radical3:
Since ies4linux, there is no way I know of that you can check IE6 leave alone IE7 functionality on the LOCALHOST without using a Virtual Machine with XP, yes good old Windows XP in it.
Why? **Because there is no native Internet Explorer for Linux. **
You can try installing IE6 in Crossover though. It might just well work (though I seriously doubt it).

---

### Post by Paul41 on 2008-09-07
> **radical3 said:**
> **Are you sure there is absolutely no other way**:(, other than using xp(virtually or not).

I guess you can never be 100% sure but I searched for months and the VM was the only 100% reliable way I found. I stopped looking once I got the virtual machine set up for testing because it works perfectly. That was a couple years ago so it is possible that there is something new out there, but if so I haven't heard about it.

---

### Post by mike_g on 2008-09-07
Or you could just ignore IE and test and fix your site when its done. In IE, from what I have found, its usually one of a handful of issues that can be fixed easily when you know how.

---

### Post by radical3 on 2008-09-07
> **Anurag_panda said:**
> @radical3:
Since ies4linux, there is no way I know of that you can check IE6 leave alone IE7 functionality on the LOCALHOST without using a Virtual Machine with XP, yes good old Windows XP in it.
Why? **Because there is no native Internet Explorer for Linux. **
You can try installing IE6 in Crossover though. It might just well work (though I seriously doubt it).
ive tried installing IE6 through any means, the installer doesn't even start, i was hoping for some sort of developing tool that can tell you what is IE broken.linux has been out over a decade, surley someone has asked this question before. Even if i were to build on remote host, i would be constantly ftping every time i change in image, browsershots is so slow, its practically a hindrance.

> Or you could just ignore IE and test and fix your site when its done. In IE, from what I have found, its usually one of a handful of issues that can be fixed easily when you know how.

 read earlier posts, i did that already, build in xubuntu then test only the completed site in xp when the site was finished,  it was so broken i pretty much had to start from scratch.

---

### Post by mike_g on 2008-09-07
> read earlier posts, i did that already, build in xubuntu then test only the completed site in xp when the site was finished, it was so broken i pretty much had to start from scratch.

Yes I know, but IMHO it would be more beneficial to find and fix the problems than starting from scratch. For example I had a site that was completley screwed up in IE6. Problems included: padding being applied to css backgrounds, updating table cell inner html not working, the PNG bug, plus some other JS issues. Its a pain, but by fixing these problems you will begin to know before hand what will display correctly in IE6 and what wont.

---

### Post by radical3 on 2008-09-07
> **mike_g said:**
> Yes I know, but IMHO it would be more beneficial to find and fix the problems than starting from scratch. For example I had a site that was completley screwed up in IE6. Problems included: padding being applied to css backgrounds, updating table cell inner html not working, the PNG bug, plus some other JS issues. Its a pain, **but by fixing these problems you will begin to know before hand what will display correctly in IE6 and what wont**.

great advice i'll inconvenience myself in order to attain IE6 premonition.

---

### Post by mike_g on 2008-09-07
Well you would be doing yourself a favor in the long run. IE6 issues and work arounds are well documented on the net. But since you dont seem to have the patience to figure out whats going on you can always keep chucking random stuff into a WYSIWYG editor until by luck you come up with something that looks ok in all browsers.

---

### Post by mssever on 2008-09-07
> **radical3 said:**
> i was hoping for some sort of developing tool that can tell you what is IE broken.linux has been out over a decade, surley someone has asked this question before.Making such a tool would involve writing a bug-for-bug clone of IE. That would be really hard to do, especially since IE is closed-source, and especially since I'm sure that some of the bugs involve IE's interactions with the Windows environment, so they'd require complex workarounds to reproduce under Linux. Such a project would itself probably be bug-ridden, which would defeat the purpose. No sane person would attempt to write such a program, when there are much easier options available.

I do two things: First, I store my web development files on one machine, which I designate the server. I make those files available both by NFS and Samba, so that I can mount them locally from any machine or OS I'm running. I configured Apache to use name-based virtual hosts, and I set up a local DNS server to assign local domain names as appropriate (I could have used the hosts file, but then I would have had to synchronize changes). Because the DNS server is local, the sites are invisible to the outside world.

Now, to edit a site, I just edit the files as if they were local. No FTP or anything. To test, I just type in the domain name I've assigned. It takes a bit to set up initially, but once set up, nothing could be easier.

And, of course, I can combine that tactic with VMs to conveniently test multiple environments. After all, testing IE in Linux is just as silly as trying to test Epiphany in Windows. Test in your target environment.

---

### Post by CarlosNYB on 2008-09-07
I feel compelled... please omit any snarkiness which may offend, and try to see the points re: professional development, if you don't mind...

Whenever I do anything outside of the most basic HTML I'm always wondering whether it will look significantly different on another browser in another OS, the whole issue of Netscape v. IE differences just drove me crazy.  Yes, I started doing HTML in notepad on windows 95.  But then I'm not a graphic designer guy, so server scripts for databases and simple HTML forms served me well enough, maybe with the most basic jscript or xml in-between.  The graphics and javascripting and browser wars -- YIKES!  Hats off to anyone who has dealt with all that mess and succeeded with graphics and neat effects!

Re: development...

Knowing what you are developing FOR and ON is an ESSENTIAL PART of development.  If you are WEB DEVELOPING, then you need to know what is platform independent, what is cross-browser compliant, what works in this environment or that environment.  THERE IS NO SHORTCUT to figuring out what breaks IE, if you want to be a web developer.  Sorry.  At least things are FAR BETTER NOW than they were a decade ago!

Re: testing...

Really, let's be REALISTIC.  You can't baulk at dual-booting or using vms IF you ACTUALLY want different people in different computing environments to use your programming without bugs.... I mean, you can't be SERIOUS?  VMs have been one of the testing alternatives for MANY YEARS, I mean Jeeze.  Sure testing can be a pain.  But you set things up and do the best you can to run your program/website through the wringer, the operating systems/browsers which will be the computing enviornment.  If one environment is closed and quirky and it's causing you problems (IE) then you have to find a way to deal with it: learn what's breaking IE as best you can (a few things as others have said, are typical problems that are well documented), and for the rest there's dual-booting, vm-ing, setting things up on a server and looking at things from another box, etc.

==========

If I was in development I'd want to steer clear of things that are DOCUMENTED to be buggy in IE or not cross-platform, and bone up on that.  If I was in the testing phase working on web-sites seriously on a PC I'd want to see if I can get a hold of a mac to see what it looks like, an a linux box, and I'd want to see it in Opera and Firefox and IE, at some point.  Particualrly because, as I said, I started back when things were way less compatible than they are now anyway, I'm suspicious of assumptions that new web-development just work everywhere.

There is testing in the development phase but the development phase isn't the beta testing phase, jeeze.  I mean think about it, as RAD as you want to get, your incremental changes are for the system you are working on currently, your current rad environment.  Maybe you can easily switch to a VM (better than re-booting anyhow, RAD-wise), or as others have suggested, set up a local server.  But at some point you leave the development phase into SERIOUS testing.  At that point you DO try to see it on different machines, different os's, different browsers.

If it is breaking that badly at the development stage, you really need to learn the basics of cross-platform develment for the web, and that will make you a web developer.  Without that knowledge I'm sorry but you are missing the point.

So learn what's breaking IE, and use XP or VMware in Xubuntu or a Mac or whatever else, but learn to develop more solidly or you are screwed anyway.  You want to get to the point where early in development you don't break things that radically between IE and other browsers because you are INFORMED ENOUGH about the documented differences, and then you can check how things look in other browsers less often and still move ahead quickly.

And more power to you, dealing with the browser differences, really.  But there's no shortcut I can see.

Maybe I'm off-base on some of this, but I think my main points are valid: VMs aren't evil, they are one of the ways to do testing for different environments, and it's ESSENTIAL for you to get to know a little more about the differences between environments (browsers) anyhow.  I mean, do whatever works.  People have suggested many set-ups which work for them.

Don't assume a VM running XP/IE will make Xubuntu too slow.  For that matter, don't assume that you can't make ubuntu even quicker (there's Fluxbox, there's OpenBox w/ or w/o Pypanel, for example) and then run a VM on that.  I haven't messed with VMs much, and it was a while ago, so I can't speak to the experience of VMing with Ubuntu, unfortunately.

I hope you work something out.

---

### Post by hidarikani on 2008-09-07
I've been using Ubuntu for webdev for 1.5 years.

I used to use Eclipse Web Tools.
Last month I've downloaded Netbeans 6.5 beta PHP build and I like it a lot.

I have IEs 4 Linux installed for IE 6 testing
I use VMware server to create two Win XP virtual machines:
[LIST]
[*]one for IE 7
[*]second for IE 8 beta
[/LIST]

I've just started writing a blog about webdev on linux, because I want to convince ppl that webdev on Ubuntu is fun.

---

### Post by radical3 on 2008-09-07
> **hidarikani said:**
> I've been using Ubuntu for webdev for 1.5 years.

I used to use Eclipse Web Tools.
Last month I've downloaded Netbeans 6.5 beta PHP build and I like it a lot.

I have IEs 4 Linux installed for IE 6 testing
I use VMware server to create two Win XP virtual machines:
[LIST]
[*]one for IE 7
[*]second for IE 8 beta
[/LIST]

I've just started writing a blog about webdev on linux, because I want to convince ppl that webdev on Ubuntu is fun.

where the hell is this blog??? :confused: (no link)

---

### Post by hidarikani on 2008-09-08
> **radical3 said:**
> where the hell is this blog??? :confused: (no link)

[http://blog.hidari.lt/](http://blog.hidari.lt/)

---

### Post by radical3 on 2008-09-09
well thats the end of that

I tried to do the whole "web development under linux" thing but ive failed, heres what i did

1. installed virtualbox, installed xp in VB, ran it = fail, how? 
      becuase i cant get full screen in vbox because of the stupid xfce panel.Plus virtualbox is super slow for me, and it slows down xubuntu, i believe this is because my graphics card is not compatible so there is no hardware acceleration, simply scolling up and down is a challenge. 

2. i reinstalled xp recently after a few months of running xp, and its faster than xubuntu on my 1 gig of ram,boots faster, extracts files faster, firefox is MILES faster, its faster in every way. installed vbox in xp and installed a guest xp ran smooth without a hitch.


either way ive decided to go with [tredosoft's standalone internet explorer application]("http://tredosoft.com/IE7_standalone") to run ie6 and ie7 side by side on xp, so now i can have [IE6/7 73% firefox 19% and safari 6%]("http://en.wikipedia.org/wiki/Usage_share_of_web_browsers") all in one go without the hassle. 

now i dont know what im gonna use my xubuntu installation for, cant play games, cant do any sound related stuff (becuase linux sound is questionable) cant do any video stuff (hardware acceleration) cant browse the web coz firefox is just too slow(compared to xp fresh install). Sadly i might have to uninstall it to free up space coz i just dont know what to do with it, however i dont really want to coz ive just finally gotten used to the command line.:(

---

### Post by LaRoza on 2008-09-09
> **radical3 said:**
> 
now i dont know what im gonna use my xubuntu installation for, cant play games, cant do any sound related stuff (becuase linux sound is questionable) cant do any video stuff (hardware acceleration) cant browse the web coz firefox is just too slow(compared to xp fresh install). Sadly i might have to uninstall it to free up space coz i just dont know what to do with it, however i dont really want to coz ive just finally gotten used to the command line.:(
Sounds like incompatible hardware. You'd have a worse or equal experience in any OS with such unsupported hardware.

---

### Post by radical3 on 2008-09-09
> Sounds like incompatible hardware. You'd have a worse or equal experience in any OS with such unsupported hardware. 
most definitely.
but i never needed to run vbox in *buntu before so no hardware acceleration wasnt a prob, online and local videos played really well, but another operation system layer is a bit too much to take . 

Nevertheless well ive found a solution and it works great IE6/7 , firefox and safari all in one OS. 

 now i just need xubuntu suggestions becuase ive had ext2ifs installed from the get-go so my xubuntu /home folder may end up as a storage bin for my xp. :-k

---

### Post by an93l on 2008-10-05
I know you have made up your mind about this but did you install the guest additions within virtualbox, this helps with the driver issues within the Vmachine

---

### Post by skotos on 2008-10-06
Well, I would suggest you to start developing in Eclipse-PDT by downloading the all-in-one package and then adding some useful plugins such as sql explorer, jQuery (not JQuery!) and a JavaScript one, then start converting old JavaScript to jQuery and start using CSS templates or CSS directly created by you in jQuery for the most delicate part / patch: you will find IE running succesfully on your new revamped sites at the first try.
Eclipse will let you forget of Dreamweaver, while jQuery - as well as any other JavaScript framework - of Microsoft IE-Firefox and the rest madness / ********!

Give them a try. You will never come back!

Probably jQuery is best suited to start having a return of investment in a day or two...
But do not underestimate it... It can be tremendously awsome at whatever level you will get!

There is no way to successfully check IE readability out of Windows. You will always need a Windows scratched PC or virtual machine running the native Windows environment. And you will always need to check for different IE versions behaviors... This is the way Microsoft wants us to live on the web, at home or in the office... JavaScript frameworks just give us a neater abstraction layer we cannot live without, today.
Many of them are being developed with unit tests and are particularly affordable. That's why you need to run heavily into them asap!

---

### Post by skotos on 2009-02-26
> **skotos said:**
> Well, I would suggest you to start developing in Eclipse-PDT by downloading the all-in-one package and then adding some useful plugins such as sql explorer, jQuery (not JQuery!)...Well, *Eclipse PDT* is getting day by day more and more useful for web development. **Ganymede**, the current Eclipse version 3.4, gives you probably the best web developing environment for PHP.
It now natively integrates the debuggers features with the ***internal browser***, so that you can immediately start debugging your projects and stay in just one application that flowlessly shows you whatever you need (the first version I see providing it for free under Linux and _just out of the box_).
The *File Sync* plugin might give you a synchronization tool that Dreamweaver developers have always felt the lack of, and the *Subclipse* plugin might take you a step farther, towards team development (subversioning, while CVS is natively provided).

If *Eclipse PDT* is not interesting enough because PHP is not your choice, Eclipse is packaged to provide different languages environments: *JavaScript, Python*, *R**uby*, *P**erl* and *J**ava*, to name just those that might be used for web development.

Probably, a good starting point might be an easy *XAMPP* installation (in order to quickly run a LAMP environment that provides *Apache*, *MySQL*, *phpMyAdmin*, *pear*, *PHPUnit*, *perl*, *ftp*, ...) and the fast Eclipse installation provided for free by Pulse, (see [http://www.poweredbypulse.com](http://www.poweredbypulse.com)).

Personally, if PHP is interesting enough, I would suggest you to run the Zend framework on the server (available for free) and run XDEBUG as your favorite debugger: you will be able to debug you files in the internal browser and in Firefox as well (just look for the XDEBUG extension for Firefox).

Currently, the only reason to have Windows installed in a virtual machine is Flash Pro (to build dynamic eye catching material) and - alas! - Internet Explorer.

While you might simply get rid of Flash Pro by running other tools (like free javascript snippets and flash compilers as well) or - for instance - php libraries (look at one of the installed XAMPP samples), unfortunately you cannot say the same for M$IE.

Said this, the reasons not to definetely switch to Linux for web development should be zeroed: there is enough to satisfy and astonish every object oriented lover, amateur and pro, working alone or in team.
And if you are not a pro, or simply not interested in OOP or Agile programming (possible nowadays?), do not be afraid: other tools, simpler, can be run as well: just search in the repositories.

But, if you are serious on web development and still you do not want to abandon Windows, simply run Ganymede and XAMPP on it: they just works out of the box and you will be able to switch to Linux (I should have said _**Ubuntu!**_) in no time, after verifying their functionalities and add-ons! This is ***cross-platform development*** indeed!

---

### Post by tom66 on 2009-02-26
Have you installed msttcorefonts? This installs Windows fonts, and it could be the cause of all the div's going out of wack because the div's are using the closest match which isn't close enough.

---

### Post by ktmom on 2009-03-06
Thanks to everyone who posted in this thread.  As a *very* new user of Ubuntu, and migrating all of my WinXP apps to open source, this has been very helpful.  I wasn't aware of ie4linux and it is better than anything I had to use before.  Much more convenient.  Now to decide what to replace Dreamweaver with.  So many choices.

It's a shame the original poster is less than pleased, I am getting more thrilled with the Ubuntu platform every day.

---

