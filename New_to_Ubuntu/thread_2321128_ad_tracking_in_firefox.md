---
title: "ad tracking in firefox"
date: 2016-04-20
forum: New to Ubuntu
---

### Post by rb46uk on 2016-04-20
Hi all,
I am a brand new Ubuntu user.
I was previously using Windows7. Been meaning to change to Linux for years but never got over the fear (I'm not a coder!). The constant nagging that turned into virtual bullying to upgrade to W10 finally motivated me to make the switch. I couldn't be happier with it and it was much much simpler than I had anticipated.

My question is about firefox. I was using firefox with windows with an Avast plug-in that allowed me to block most of the tracking. I got so used to it I forgot that it was a plug-in and not part of firefox.

I was aggravated to find that when I visited a National Newspaper website, I saw advertisements for a product that I had just bought on Amazon!

Is there a similar plug-in for Ubuntu Firefox that will block these ridiculous (I'd already purchased the item!) and intrusive advertisements?

Thanks in advance.

---

### Post by Habitual on 2016-04-20
> **rb46uk said:**
> Is there a similar plug-in for Ubuntu Firefox that will block these ridiculous (I'd already purchased the item!) and intrusive advertisements?
Adblock Plus and NoScript are almost requirements these days.

---

### Post by howefield on 2016-04-20
The 3 Firefox browser plugins I use are Adblock Plus, Ghostery and Noscript (Scriptsafe in Chromium).

How that compares with what you had via Avast I have no idea, but it gives me a pleasant enough browsing experience.

---

### Post by coldraven on 2016-04-20
Hi and welcome!
Don't forget to go to "System Settings" and open "Security and Privacy". On the Search tab disable "Include online search results".
The FF ad-ons that I use are
NoScript
BetterPrivacy (It deletes Flash super cookies)
Ghostery
uBlock Origin (similar to AdBlockPlus)

---

### Post by ajgreeny on 2016-04-20
Another vote here for uBlock Origin rather than Adblock; it is a lower resource add-on, but just as simple and easy to use.

I tested Noscript but I found it more annoying than useful so I removed it; I still use flashblock, having set the flashplugin to be always enabled, which then allows me to click on any single instance of flash on a web-page rather than enable flash generally on a whole page basis.

---

### Post by oldos2er on 2016-04-20
I use uBlock Origin and Privacy Badger. Noscript is great if you have the time and patience to configure it; I did not.

---

### Post by sammiev on 2016-04-20
I use uBlock Origin and set [optional tracking protection]("http://venturebeat.com/2015/05/24/firefoxs-optional-tracking-protection-reduces-load-time-for-top-news-sites-by-44/") in Firefox.

---

### Post by vasa1 on 2016-04-20
> **rb46uk said:**
> Hi all,
I am a brand new Ubuntu user.
...
Hi, it would be nice if you mention which version of Ubuntu you've installed. This is because, like Windows, one version may have features that another doesn't.

As coldraven mentioned, you may also want to check the privacy settings provided by the operating system as well. In 14.04, "online searches" are on by default. In 16.04, they're off by default. Both versions allow you to flip the settings to what you want.

---

### Post by Bucky Ball on 2016-04-20
Yep, uBlock Origin. I used to use Adblock Plus. Noscript blocks a heap, but it can be annoying depending on how you have it setup.

For getting rid of ads, though, uBlock Origin does a great job.

---

### Post by vasa1 on 2016-04-21
[uBlock Origin]("https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/") is also thoroughly documented: See [https://github.com/gorhill/uBlock/wiki](https://github.com/gorhill/uBlock/wiki) and [https://github.com/gorhill/uBlock/wiki/What-uBlock-can-and-can-not-%28currently%29-do](https://github.com/gorhill/uBlock/wiki/What-uBlock-can-and-can-not-%28currently%29-do) for starters.

If you intend installing it, make sure you install uBlock Origin and _not_ plain uBlock. There's a story behind that but it isn't really relevant here.

---

### Post by buzzingrobot on 2016-04-21
For the OP:  The "tracking" techniques used by advertisers are independent of any particular operating system.

Start with an ad blocker. Add more tools if you find it necessary.

---

### Post by SeijiSensei on 2016-04-21
Another vote for Ghostery, though you'll probably need to permit some sites like those associated with video players.

---

### Post by haplorrhine on 2016-04-21
I'm just learning.  If you're hardcore, you could try to avoid "canvas fingerprinting".  [http://cseweb.ucsd.edu/~hovav/dist/canvas.pdf](http://cseweb.ucsd.edu/~hovav/dist/canvas.pdf) 
 [NoScript can block WebGL]("https://wiki.ubuntu.com/BasicSecurity/NoScript") content, but that's one-third the battle.  You might also consider upgrading your GPU, disabling WebFonts, and/or changing your browser.

Once that cookie fingerprints you, or a persistent cookie respawns on your system, it might sync with other cookies and spill your identity to other trackers.  [https://freedom-to-tinker.com/blog/englehardt/the-hidden-perils-of-cookie-syncing/](https://freedom-to-tinker.com/blog/englehardt/the-hidden-perils-of-cookie-syncing/)

---

### Post by rb46uk on 2016-04-21
Thanks all for advice.

Have installed uBlock Origin and NoScript and very happy with the results.

Thanks again.

---

### Post by Habitual on 2016-04-21
Glad it worked out!

---

### Post by pfeiffep on 2016-04-21
I started with Adblock plus and replaced it with Ublock Origin
Ubuntu 14.04 LTS

---

### Post by haplorrhine on 2016-04-21
Does Better Privacy deserve more mentions?  It's all I know that blocks flash cookies, and it's recommended in the Ubuntu Basic Security guide.

---

### Post by coldraven on 2016-04-26
> **haplorrhine said:**
> Does Better Privacy deserve more mentions?  It's all I know that blocks flash cookies, and it's recommended in the Ubuntu Basic Security guide.

I've been using it for years, it has never caused any problems. It can be set to delete Flash cookies on FF exit along with the history, cookies etc. that you selected in the FF privacy menu. I only keep Flash cookies from the BBC in case I have to resume streaming a TV show.

---

### Post by KenUBF on 2016-05-23
I use many of the same tools that have already been mentioned but this is what I have on my system and it seems to be effective: 

AdBlock Plus 
Better Privacy 
Blur (by Abine) 
Ghostery 
HTTPS-Everywhere 
NoScript 
WOT (Web of Trust) 

Here is my advice. 

In Firefox, under Preferences/Privacy turn off third-party cookies, click the box to send Do Not Track requests and set Private Browsing mode to use Tracking Protection, and set the browser to clear all cookies on browser exit. Or you can surf in Private Browsing mode to avoid cookies altogether if you won't be logging in anywhere. Stay as far away from Google and other large search engines as possible. Use DuckDuckGo, Startpage, or Disconnect. 

In Better Privacy I like to set the app to &#8220;Delete Flash cookies on Firefox exit&#8221; so when you close the browser all cookies will be deleted. I also check &#8220;Also delete Flashplayer default cookie.&#8221; Also, &#8220;Disable Ping Tracking&#8221; and &#8220;Prevent the Firefox 'Clear Recent History' functions from handling LSO's as usual cookies.&#8221; 

In AdBlock Plus I would make sure all block lists are checked and updated. And uncheck the box that says &#8220;Allow some non-intrusive advertising.&#8221; 

In Ghostery block ALL listed trackers, etc. Do the same in Blur

In NoScript, under Options/Embeddings I have nearly everything checked except &#8220;No placeholder&#8221; and &#8220;Collapse blocked objects.&#8221; Under Advanced, I delete all default listings under the XSS tab, and in the HTTPS tab/Permissions I set it to &#8220;always forbid active content unless it comes from a secure connection.&#8221;

With WOT I always go into the Settings and uncheck the box that says Enable cookies.

With these settings and apps set to their most restrictive most tracking is disabled, however, there are other tracking methods that don't place anything on your computer at all. It is called Browser Fingerprinting and there really isn't anything you can do to stop it, even using a User Agent switcher. The best way to avoid all tracking would be to use TOR Browser, but signing in anywhere would divulge your identity. Advertisers are scum and adapt their methods to get around user's attempts at privacy but this will largely keep you from being tracked. Good luck! Oh. I just read this interesting report the other day about ad tracking that you might find helpful: [https://www.schneier.com/blog/archives/2016/05/state_of_online.html](https://www.schneier.com/blog/archives/2016/05/state_of_online.html)

You can also test your browser's fingerprintability here: [https://panopticlick.eff.org/](https://panopticlick.eff.org/)

Finally, avoid going to the Tor Project website unproxied because the NSA tracks all IP addresses that go to that site along with other privacy/security tools websites, like TAILS, etc. 

I know that's a lot but I am a bit of a privacy/security nut. :- )

---

### Post by jimmy-frydkaer on 2016-05-24
I use Adblock Plus, Ghostery and WebOf Trust WOT - I do not use NoScript due to impatience

---

### Post by haplorrhine on 2016-05-24
Apparently you can also be fingerprinted by your NoScript whitelist. The developer merely includes scripts from common domains to test whether they're allowed or not.

[http://cseweb.ucsd.edu/~hovav/papers/mbys11.html](http://cseweb.ucsd.edu/~hovav/papers/mbys11.html)
"Fingerprinting Information in Javascript Implementations"

---

### Post by KenUBF on 2016-05-25
> **haplorrhine said:**
> Apparently you can also be fingerprinted by your NoScript whitelist. The developer merely includes scripts from common domains to test whether they're allowed or not.[http://cseweb.ucsd.edu/~hovav/papers/mbys11.html](http://cseweb.ucsd.edu/~hovav/papers/mbys11.html)"Fingerprinting Information in Javascript Implementations"This looks interesting. Thanks for the link!

---

