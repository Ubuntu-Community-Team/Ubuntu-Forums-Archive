---
title: "Windows Live Hotmail (the new one) not working"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by manilaph on 2008-10-30
Hello,

Before anyone says that it works... there are 3 versions of Windows Live Hotmail right now (all at the same time) due to the slow roll-out of the very latest version of Windows Live Hotmail.

I have 2 hotmail accounts, one is on the very new (Oct 2008) version and one is on the older version.

The very new version does not work with Linux I believe but the older one still does.

There is even the Windows Live Hotmail classic which also works.

And so, it is the very latest one that does not work. Not all people or hotmail users are on the latest version yet. You will know what I mean when you reach the new version.

I opened an account with Gmail which works with any browser or OS.

But I still want to know why the new Windows Live Hotmail does not work with Linux.

Some references:
[http://blog.iconcertina.com/archive/hotmail-and-windows-live-rebrand/](http://blog.iconcertina.com/archive/hotmail-and-windows-live-rebrand/)

[http://www.bizkitpark.com/2008/10/new-hotmail-layout.html](http://www.bizkitpark.com/2008/10/new-hotmail-layout.html)

[http://www.simonives.info/blog/2008/october/how_check_your_hotmail_or_windows_live_account_ubuntu_with_evolution](http://www.simonives.info/blog/2008/october/how_check_your_hotmail_or_windows_live_account_ubuntu_with_evolution)

---

### Post by chewit on 2008-10-30
I had the same problem. To solve it, you need to download a Firefox add-on. Its called User Agent Switcher. It makes websites think your using a different browser and operating system to the one actually are using.

---

### Post by manilaph on 2008-10-30
chewit, thank you for the super fast reply. this is the greatest linux community and it just gets better.

where do i find this add-on/plug-in. 

I am using 8.10 RC and i love it.

thanks

---

### Post by chewit on 2008-10-30
In Firefox, go to Tools > Add-ons.

In the add-ons window, much sure your on the 'get add-ons' tab and in the search box type User Agent Switcher

When i did it, it didn't come up on the list, so scroll down and click on 'See all results (10)'.

This will open a new web page. 

For me, User Agent Switcher was the 6th add-on, on the list. Then click on 'Add to Firefox'.

Install it! Restart Firefox!

When you are back on Firefox, go to Tools > User Agent Switcher and select any of those browsers from the list. I would recommend Internet Explorer 7 (Windows Vista).

When you go to hotmail.com, you will be able to access your emails now.

Hope this helps.

---

### Post by ginestre on 2008-10-30
Am I paranoid, or is this a clear case of FUD marketing by Redmond? So the browser works fine with Hotmail as long as Hotmail thinks its internet explorer? No other changes necessary, just a change of badge? If that's the case it's truly scandalous.

---

### Post by Jammy4041 on 2008-10-30
> **ginestre said:**
> Am I paranoid, or is this a clear case of FUD marketing by Redmond? So the browser works fine with Hotmail as long as Hotmail thinks its internet explorer? No other changes necessary, just a change of badge? If that's the case it's truly scandalous.

I can't believe you need a Firefox add-on just to check a simple email!!! It is scandalous. Once again. microsoft has left linux users out in the cold. Nice One micro$oft!!!.

---

### Post by Kevbert on 2008-10-30
Thanks chewit. I'm surprised that this isn't there by default in Firefox. In the default Kubuntu browser, this function is built-in.

---

### Post by billgoldberg on 2008-10-30
> **ginestre said:**
> Am I paranoid, or is this a clear case of FUD marketing by Redmond? So the browser works fine with Hotmail as long as Hotmail thinks its internet explorer? No other changes necessary, just a change of badge? If that's the case it's truly scandalous.

I don't find this that bad.

They sell an OS and if you like to use their free services they would like you to use their products.

There are loads of websites that require you to use Firefox or they won't work properly (some even deny access to non firefox browsers).

---

### Post by Toufik on 2008-10-30
Instead of tweaking YOUR browser, send a bug report to hotmail. I do it once a week since one month, you just need one minute. If everybody do it, maybe, they'll hear us!! :)

For bug reporting, click on "comments" (or something similar depending on your language) on the bottom right.

---

### Post by LowSky on 2008-10-30
> **billgoldberg said:**
> 

There are loads of websites that require you to use Firefox or they won't work properly (some even deny access to non firefox browsers).

I havent seen that ever. I have seen MS IE required, and I've seen website say "Your web browser is not supported please use _______ (an older version with no recent security updates)

---

### Post by dx9ss on 2008-11-03
I am afraid to point out the obvious -- but the "NEW" Hotmail interface not working with Linux versions of Firefox is by design!

It is a more hideous plan and the proof is quite easy to see foryourself!

I've got several machines and have several versions of Firefox installed ... On one Firefox 2.x and 3.x (linux binary AND win32 under WINE)! I've also installed the user agent add-on to "switch" the various agent strings (what is sent via HTTP and available via javascript) ... and guess what... in EVERY CASE, when the browser advertised windows -- it work / every time it advertises Linux (version of Firefox) it has big problems with the new Live Hotmail.

I am not making this up. I even put up a video on youtube (youtube.com/dx9s).

Install the User Agent and create a profile: (if you are using Firefox 3.x on Linux)

Descriptiong: Firefox 3.x (WinXP)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
App name: Mozilla Firefox
App Version: 5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
Platform: Win32
Vendor: {leave blank}
Vendor Sub: {leave blank}

and you'll be able to use the new Live Hotmail just fine! You'll even skip the dialog page that ask you to upgrade to IE, FireFox, etc..

I think this proves that Microsoft has intentionally gone out of their way AGAIN! need I say more?


--Doug

P.S.> if you are using Firefox 2.x on Linux:
Description: Firefox 2.x (Win2K)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.8.1.17) Gecko/20080829 Firefox/2.0.0.17
App Name: Mozilla Firefox
App version: 5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.8.1.17) Gecko/20080829 Firefox/2.0.0.17
Platform: Win32

and if you are sick, go ahead and lie to Live Hotmail on a Windows machine using Firefox 2.x/3.x but claim you are on Linux .. and you'll be unable to use Live Hotmail correctly!

change the Platform to Linux and the Agent to "Mozzila/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.17) Gecko/20080922 Ubuntu/7.10 (gutsy) Firefox/2.0.0.17" (and app version to the "5.0 (X11 ..." part) and Platform to Linux!

(or equiv for Firefox 3.x which I won't bother to post)

---

### Post by handydan918 on 2008-11-05
> **billgoldberg said:**
> I don't find this that bad.

They sell an OS and if you like to use their free services they would like you to use their products.

There are loads of websites that require you to use Firefox or they won't work properly (some even deny access to non firefox browsers).

links?

---

### Post by theamber on 2008-11-05
> **dx9ss said:**
> I am afraid to point out the obvious -- but the "NEW" Hotmail interface not working with Linux versions of Firefox is by design!

It is a more hideous plan and the proof is quite easy to see foryourself!

I've got several machines and have several versions of Firefox installed ... On one Firefox 2.x and 3.x (linux binary AND win32 under WINE)! I've also installed the user agent add-on to "switch" the various agent strings (what is sent via HTTP and available via javascript) ... and guess what... in EVERY CASE, when the browser advertised windows -- it work / every time it advertises Linux (version of Firefox) it has big problems with the new Live Hotmail.

I am not making this up. I even put up a video on youtube (youtube.com/dx9s).

Install the User Agent and create a profile: (if you are using Firefox 3.x on Linux)

Descriptiong: Firefox 3.x (WinXP)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
App name: Mozilla Firefox
App Version: 5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
Platform: Win32
Vendor: {leave blank}
Vendor Sub: {leave blank}

and you'll be able to use the new Live Hotmail just fine! You'll even skip the dialog page that ask you to upgrade to IE, FireFox, etc..

I think this proves that Microsoft has intentionally gone out of their way AGAIN! need I say more?


--Doug

P.S.> if you are using Firefox 2.x on Linux:
Description: Firefox 2.x (Win2K)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.8.1.17) Gecko/20080829 Firefox/2.0.0.17
App Name: Mozilla Firefox
App version: 5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.8.1.17) Gecko/20080829 Firefox/2.0.0.17
Platform: Win32

and if you are sick, go ahead and lie to Live Hotmail on a Windows machine using Firefox 2.x/3.x but claim you are on Linux .. and you'll be unable to use Live Hotmail correctly!

change the Platform to Linux and the Agent to "Mozzila/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.17) Gecko/20080922 Ubuntu/7.10 (gutsy) Firefox/2.0.0.17" (and app version to the "5.0 (X11 ..." part) and Platform to Linux!

(or equiv for Firefox 3.x which I won't bother to post)

Thanks... this really WORKS! This kind of aptitud by Microsoft shows the level of panic that they are and their better days are over I was thinking in changing my hotmail email address. no matter what they do even if Windows becames free I WILL NOT USE IT! because of this level of mono polio and because I never like Windows I did not even like their version of Dos and it was almost the same as the IBM's.

---

### Post by CoreyB. on 2008-11-05
> **theamber said:**
> Thanks... this really WORKS! This kind of aptitud by Microsoft shows the level of panic that they are and their better days are over I was thinking in changing my hotmail email address. no matter what they do even if Windows becames free I WILL NOT USE IT! because of this level of mono polio and because I never like Windows I did not even like their version of Dos and it was almost the same as the IBM's.

Calm down.  I read on a similar thread, Yashiro said to go to about:config and change the general.useragent.vender to Firefox from Ubuntu, then restart Firefox.  It works perfectly.  The problem isn't Microsoft restricting the site to IE, it is that it doesn't recognize a browser called "Ubuntu".  Firefox on Windows works fine without changing anything.  The problem lies with Ubuntu modifying Firefox because websites don't recognize it as Firefox.

---

### Post by philinux on 2008-11-05
> **CoreyB. said:**
> Calm down.  I read on a similar thread, Yashiro said to go to about:config and change the general.useragent.vender to Firefox from Ubuntu, then restart Firefox.  It works perfectly.  The problem isn't Microsoft restricting the site to IE, it is that it doesn't recognize a browser called "Ubuntu".  Firefox on Windows works fine without changing anything.  The problem lies with Ubuntu modifying Firefox because websites don't recognize it as Firefox.

Yep I tried this but it dont stick it reverts back to ubuntu on reboot.

---

### Post by philinux on 2008-11-05
> **CoreyB. said:**
> Calm down.  I read on a similar thread, Yashiro said to go to about:config and change the general.useragent.vender to Firefox from Ubuntu, then restart Firefox.  It works perfectly.  The problem isn't Microsoft restricting the site to IE, it is that it doesn't recognize a browser called "Ubuntu".  Firefox on Windows works fine without changing anything.  The problem lies with Ubuntu modifying Firefox because websites don't recognize it as Firefox.

Yep I tried this but it dont stick it reverts back to ubuntu

---

### Post by matchstich on 2008-11-05
i can not use hotmail with firefox.  but, have no problem using hotmail with opera.

i can get to hotmail.  open it  it and all but can not send email with
firefox.

opera has no problem with that.

---

### Post by CoreyB. on 2008-11-05
> **philinux said:**
> Yep I tried this but it dont stick it reverts back to ubuntu

Thats odd, I rebooted and it still says Firefox, I've only rebooted once though.

---

### Post by Darthape on 2008-11-05
I tied logging in and it hung on authenticating me. Is this the same problem you were having?

---

### Post by pirattrev on 2008-11-05
MS is Evil, here's my of it if you like.  [proof]("http://ubuntuforums.org/showthread.php?p=6021240#post6021240")

My solution, make your own email server! haha, but no, seriously, Microsoft can be jerks and block linux, but there's no reason they can't and if they want you to use their OS, then that's cool. It is a free service. What I'm curious about is whether it works on OSX. If it does, then MS is even more evil, if they don't, then everyone is being treated the same. 

My question: why would you _want_ to use Live Hotmail?

---

### Post by Darthape on 2008-11-05
Works on MacOS 10.5. Logged on our schools macs today with out a hitch and was able to do everything I could do in XP.

---

### Post by battles33 on 2008-11-05
> **dx9ss said:**
> I am afraid to point out the obvious -- but the 
It is a more hideous plan and the proof is quite easy to see foryourself!


your solution did it for me. thank you so much. this was bothering me a lot. microsoft is disgusting. i still think apple is more disgusting, but this made microsoft just a touch worse now.

---

### Post by Weevil on 2008-11-06
Well installing the [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59") plugin did the trick for me on FF3... but I guess it's time to abandon ship. Anyone has some viable alternatives besides Gmail?

---

### Post by jtayl22 on 2008-11-06
Yet another act of an illegal monopoly. Has anyone notified the Department of Justice? (antitrust.complaints@usdoj.gov) The European Union?

---

### Post by Mr_JMM on 2008-11-06
> **pirattrev said:**
> MS is Evil...

...

My question: why would you _want_ to use Live Hotmail?


The best question on this thread.

Ubuntu is about freedom. There are many free email providers that work cross platform, cross browser etc.

Be free. Hotmail is a spam inducing, virus ridden cancer of the internet.

Is that too harsh?

---

### Post by manilaph on 2008-11-06
I stopped using Hotmail and moved to GMail.

Gmail is simply much better than hotmail.

---

### Post by dizzy1kenobi on 2008-11-06
> **chewit said:**
> In Firefox, go to Tools > Add-ons.

In the add-ons window, much sure your on the 'get add-ons' tab and in the search box type User Agent Switcher

When i did it, it didn't come up on the list, so scroll down and click on 'See all results (10)'.

This will open a new web page. 

For me, User Agent Switcher was the 6th add-on, on the list. Then click on 'Add to Firefox'.

Install it! Restart Firefox!

When you are back on Firefox, go to Tools > User Agent Switcher and select any of those browsers from the list. I would recommend Internet Explorer 7 (Windows Vista).

When you go to hotmail.com, you will be able to access your emails now.

Hope this helps.

It did not work for me.  I am getting absolutely nothing.  I can't even open them with the switcher.

---

### Post by dizzy1kenobi on 2008-11-06
> **Mr_JMM said:**
> The best question on this thread.

Ubuntu is about freedom. There are many free email providers that work cross platform, cross browser etc.

Be free. Hotmail is a spam inducing, virus ridden cancer of the internet.

Is that too harsh?

I have had very little spam since I have had my hotmail account and never a virus.

---

### Post by Deb_user2000 on 2008-11-07
You do not need to change agent to say windows OS.

I changed mine from (which did not work on new hotmail):

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.17) Gecko/20080827 Iceweasel/2.0.0.17 (Debian-2.0.0.17-0etch1)


To (which does work):

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.17) Gecko/20080827 Firefox/2.0.0.17

And still have full functionality in the New Hotmail.  In fact I used it to sign up for this forum account.

So M$ will see that I am running Linux every time I log into Hotmail.

---

### Post by Deb_user2000 on 2008-11-07
site to check your user agent:

[http://whatsmyuseragent.com/]("http://whatsmyuseragent.com/")

---

### Post by john_spiral on 2008-11-07
I can also confirm

The "enter about:config in address bar & change vendor from Ubuntu to Firefox" does work, no need for plugins.

If I remember correctly "general.useragent.vendor" is the string you need to change to Firefox <-- case sensitive

You will need to restart Firefox once the change has been made, use the [http://whatsmyuseragent.com/](http://whatsmyuseragent.com/) to check the change is working.

I suspect it's just sloppy coding/testing, something Microsoft is notorious for.

---

### Post by z1000000 on 2008-11-07
> **john_spiral said:**
> I can also confirm

The "enter about:config in address bar & change vendor from Ubuntu to Firefox" does work, no need for plugins.

If I remember correctly "general.useragent.vendor" is the string you need to change to Firefox <-- case sensitive

You will need to restart Firefox once the change has been made, use the [http://whatsmyuseragent.com/](http://whatsmyuseragent.com/) to check the change is working.

I suspect it's just sloppy coding/testing, something Microsoft is notorious for.

Sorry to be slow, I've been less than 24 hours with Linux. Where / how do I get to the "enter about:config" bit at the top? I want a permanent fix for this, not something I have to do every time I fire up Ubuntu! Thanks.

---

### Post by CoreyB. on 2008-11-07
> **z1000000 said:**
> Sorry to be slow, I've been less than 24 hours with Linux. Where / how do I get to the "enter about:config" bit at the top? I want a permanent fix for this, not something I have to do every time I fire up Ubuntu! Thanks.

Just open up Firefox and in the address bar type about:config, then promise you won't break anything, then navigate to the location mentioned above and replace Ubuntu with Firefox.  This fix, as far as I know, is permanent.  I haven't had to retype it in every time.

---

### Post by kuriooo on 2008-11-07
Just wanted to say that entering the specific info into the UserAgentSwitcher fixed my issue with Hotmail. 

I had tried the about:config fix, along with some others but this piece of info did it, thanks!

---

### Post by jtayl22 on 2008-11-07
The "user agent switcher" enabled plain-text replies, but now I can't "attach" a file to my reply. 

While I understand the point that some are making, just use another mail provider, it's not so easy when you have been using a handle for years and everybody you've known or met has your old e-mail address.

This is clearly an act of an illegal monopoly. Has anyone notified the Department of Justice? (antitrust.complaints@usdoj.gov) The European Union?

---

### Post by dizzy1kenobi on 2008-11-07
> **john_spiral said:**
> I can also confirm

The "enter about:config in address bar & change vendor from Ubuntu to Firefox" does work, no need for plugins.

If I remember correctly "general.useragent.vendor" is the string you need to change to Firefox <-- case sensitive

You will need to restart Firefox once the change has been made, use the [http://whatsmyuseragent.com/](http://whatsmyuseragent.com/) to check the change is working.

I suspect it's just sloppy coding/testing, something Microsoft is notorious for.

This solution worked nicely thank you.

---

### Post by john_spiral on 2008-11-08
> **jtayl22 said:**
> The "user agent switcher" enabled plain-text replies, but now I can't "attach" a file to my reply. 

While I understand the point that some are making, just use another mail provider, it's not so easy when you have been using a handle for years and everybody you've known or met has your old e-mail address.

This is clearly an act of an illegal monopoly. Has anyone notified the Department of Justice? (antitrust.complaints@usdoj.gov) The European Union?

Hi jtayl22,

I'm able to send email with formatted text (bold, different text sizes..) and attachments.

Close Firefox, pop into a terminal and:

mv .mozilla .mozilla-old

(The above command will rename the existing hidden Mozilla preferences folder.)

On relaunching Firefox you will get fresh preferences set then try the
"about:config" fix.

You will need to re-bookmark your stuff in the .mozilla-old folder.

John

---

### Post by manilaph on 2008-11-09
Just check this out guys...

[http://stuff.techwhack.com/5675-microsoft-live-hotmail-2](http://stuff.techwhack.com/5675-microsoft-live-hotmail-2)

please note that not all people are using the same "newest hotmail version" and therefore some guys think that there is nothing wrong with their hotmail.

more...

[http://www.linux-watch.com/news/NS6023147333.html](http://www.linux-watch.com/news/NS6023147333.html)

---

### Post by glibdud on 2008-11-09
> **john_spiral said:**
> Close Firefox, pop into a terminal and:

mv .mozilla .mozilla-old

(The above command will rename the existing hidden Mozilla preferences folder.)

On relaunching Firefox you will get fresh preferences set then try the
"about:config" fix.

Thanks, I was having the same issue with attachments as the other fellow, and this fixed it. I may try playing around with selectively killing bits of the .mozilla directory to see if I can figure out what exactly is the problem (so people don't have to blow away their preferences to get Hotmail to work). Know of anyone who has done anything like that already?

---

### Post by buckeyered80 on 2008-11-09
I also changed the general.useragent.vendor value in the about:config settings for Firefox.  I am using 3.0.3, so I changed the value to Firefox/3.0.3.  That also works.  Thanks for the fix, whoever came up with that one.

---

### Post by matchstich on 2008-11-09
> **handydan918 said:**
> links?

northern tool and caribou coffee web sites both say must 'upgrade' to 
a windows OS or  IE to use their sites.

---

### Post by matchstich on 2008-11-26
do not know what happened but i can forward mail or write mail in hot mail now using fire fox

 do not have to use opera any more.

---

### Post by manilaph on 2008-11-26
Yes you are correct.

Most likely, there were changes on the part of Windows Live Hotmail to make peace the angered linux community.

Windows Live Hotmail is fully-functional right now with Linux but I am sure that there are users who switched to the more linux-friendly and more efficient (in my opinion) GMail.

Cheers!

---

### Post by matchstich on 2008-11-27
just got a gmail account.  waited till gmail got away from having to have 
a invite to get one.
thanks

but will keep using my hotmail accounts.

---

