---
title: "Firefox, Google replaced by Ask.com, bad thing!"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xeizo on 2011-09-25
And it's not easily possible to replace Ask with Google in the search window in the upper right corner of the new Firefox. When trying to manage search engines one is directed to a page with diverse add ons instead.  Ask.com is a joke compared to Google when it comes to actually search for things, I hope this is a just a passing bug.  The least hard thing to do was to add Google as startpage instead, but a search window without a proper search engine is quite unusable so if one can't have ones search engine of choice one can as well remove the search window.

---

### Post by PaulW2U on 2011-09-25
> **xeizo said:**
> I hope this is a just a passing bug.

I'm sure it is. According to Launchpad this has happened before, bug #520682 for example.

---

### Post by batty on 2011-09-25
I hope it is just an error!

try searching for ubuntuforums using it.

Don't think this site exists according to ASK!

EDIT: doesn't seem to happen in Kubuntu version of Firefox, still can change search engines from drop list.

---

### Post by PaulW2U on 2011-09-25
Already fixed - [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/858683](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/858683)

---

### Post by grandtoubab on 2011-09-25
you can manage it
[http://mycroft.mozdev.org/](http://mycroft.mozdev.org/)

---

### Post by dino99 on 2011-09-25
> **PaulW2U said:**
> Already fixed - [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/858683](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/858683)

fix commited DONT mean fix release

its not so hard to add back your search engines preference

---

### Post by ajgreeny on 2011-09-25
Type **about:config** in FF addressbar and the use the filter for **browser.search** and you should see lines appear where you can edit your search preferences.

---

### Post by PaulW2U on 2011-09-25
> **dino99 said:**
> fix commited DONT mean fix release

My apologies, I misread the bug report. But it will be fixed and quite soon I'm sure.

---

### Post by dino99 on 2011-09-25
> **PaulW2U said:**
> My apologies, I misread the bug report. But it will be fixed and quite soon I'm sure.

sometimes there is change at all for months :( and stay stuck with "fix commited"

---

### Post by xeizo on 2011-09-25
When doing about:config it turns out that Ask.com isn't even mentioned under browser.search.* and all engines like Google, Bing etc. are where they should be. So, it is impossible to fix it by oneself. A bug it is, or a virus ...  ;)

---

### Post by dino99 on 2011-09-25
> **xeizo said:**
> When doing about:config it turns out that Ask.com isn't even mentioned under browser.search.* and all engines like Google, Bing etc. are where they should be. So, it is impossible to fix it by oneself. A bug it is, or a virus ...  ;)

no, no its a ghost :(

---

### Post by coffeecat on 2011-09-25
> **ajgreeny said:**
> Type **about:config** in FF addressbar and the use the filter for **browser.search** and you should see lines appear where you can edit your search preferences.

You'd hope so, wouldn't you? :) I'm seeing the same as xeizo - see screenshot. I'll sit this one out and wait for the bugfix.

---

### Post by dino99 on 2011-09-25
hey guys,

just follow post #5 link to install the engine(s) you want/need :)

---

### Post by kuvanito on 2011-09-25
who cares about the ask search bar,the very first thing i do after a clean install of any ubuntu version is delete the search bar and use google.com as my home page.

---

### Post by sumski on 2011-09-25
[http://bazaar.launchpad.net/~mozillateam/firefox/firefox.head/revision/865](http://bazaar.launchpad.net/~mozillateam/firefox/firefox.head/revision/865)

[http://bazaar.launchpad.net/~mozillateam/firefox/firefox.head/revision/866](http://bazaar.launchpad.net/~mozillateam/firefox/firefox.head/revision/866)

---

### Post by carltonh on 2011-09-25
Still not fixed, but post 5 fixes it.

Sadly, Ask.com doesn't even allow you to find this thread because it doesn't have an option like Google does to limit search to activity in the last 24 hours.  I had to go all the way to google.com to find this thread to fix the problem. Poor me. :)

---

### Post by sgage on 2011-09-25
> **carltonh said:**
> Still not fixed, but post 5 fixes it.

Sadly, Ask.com doesn't even allow you to find this thread because it doesn't have an option like Google does to limit search to activity in the last 24 hours.  I had to go all the way to google.com to find this thread to fix the problem. Poor me. :)

Couldn't you just have used the forum search?

---

### Post by ajgreeny on 2011-09-25
> **sgage said:**
> Couldn't you just have used the forum search?
The forum search, unfortunately, is rubbish.  Much better to use [googlubuntu]("http://www.googlubuntu.com/")

---

### Post by sgage on 2011-09-25
> **ajgreeny said:**
> The forum search, unfortunately, is rubbish.  Much better to use [googlubuntu]("http://www.googlubuntu.com/")

I just typed "firefox search" into the forum search and this thread was at the top of the list.

---

### Post by x-shaney-x on 2011-09-25
I have used mycroft to get my google search back but it still isn't allowing me to search from the address bar instead of search bar.

---

### Post by scradock on 2011-09-25
> **x-shaney-x said:**
> I have used mycroft to get my google search back but it still isn't allowing me to search from the address bar instead of search bar.
I fixed it by using the add-on to ensure that google searches use google.com instead of local googles - it's called something informative like ".com", IIRC.

---

### Post by rburkartjo on 2011-09-25
i installed firefox 8.0a2 and the default search was not changed

---

### Post by ft_ on 2011-09-25
Additionally, I lost my adress bars's search bar ability...
You have to :
type : about:config
search : keyword.URL
replace with : [http://www.google.com/search?btnG=Google+Search&q=](http://www.google.com/search?btnG=Google+Search&q=)

---

### Post by PaulW2U on 2011-09-25
Bug now showing as "Fix Released".

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/858683](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/858683)

Edit: Just downloaded update, search engines now restored.

---

### Post by Harry33 on 2011-09-25
There is new version (7.0+build2+nobinonly-0ubuntu3) building right now in order to soleve this:

> firefox (7.0+build2+nobinonly-0ubuntu3) oneiric; urgency=low

  * Fix LP: #858683 - All search engines disappear. Handle the directory ->
    symlink conversion in the postinst script
    - update debian/firefox.postinst.in


---

### Post by Rasa1111 on 2011-09-25
Soo lame.
Still don't have google back.
no updates available..
Stuck with ASK -aka Crap

---

### Post by MacUntu on 2011-09-25
It's a bug. It should have been [http://www.askubuntu.com](http://www.askubuntu.com). :P

---

### Post by effenberg0x0 on 2011-09-25
sudo killall firefox && sudo apt-get remove --purge firefox && sudo apt-get update && sudo apt-get install firefox fixes it for me. 

Regards,
Effenberg

PS: Honestly, who uses ask.com... I played with it for like 10 minutes and results were ridiculous.

---

### Post by scottstensland on 2011-09-25
This fixed both the ASK search box (back to google) as well as making 
the URL a google search

    [https://addons.mozilla.org/en-US/firefox/addon/luckybar/](https://addons.mozilla.org/en-US/firefox/addon/luckybar/)

I@m using firefox-trunk 9.0a1

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-trunk

on a related note - which uses an approach ubuntu could benefit from,
this FF addon enables addons which are disabled due to using a
super new browser release not yet sanctioned 

[https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/?src=prerelease-banner](https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/?src=prerelease-banner)

its community driven to provide end user usage feedback on viability of addons

---

### Post by x-shaney-x on 2011-09-25
I just did an apt-get update to firefox and it all seems back to normal.

Search engines ARE back and I am able to search in the address bar again.

---

### Post by Rasa1111 on 2011-09-25
I removed and reinstalled firefox, and it's back to normal.
man, that ASK rubbish is...... RUBBISH! lol O_o

---

### Post by LinuxFan999 on 2011-09-25
I agree, ask.com is terrible. Some Windows software used to force an installation of the ask.com toolbar, but now they force an installation of a Yahoo! Bar or a Bing bar. Ask.com is also outdated, when compared to Google. Mozilla should remove the option for ask.com from Firefox, especially since very few people use ask.com. Google Chrome, Opera, and Safari don't have an option for ask.com, so Firefox shouldn't have it ether.

---

### Post by kostageas on 2011-09-25
Duck Duck Go should be default, but very easy to change for personal preference.  IMO, of course.

---

### Post by sammiev on 2011-09-25
At least all is back to normal now. :)

---

### Post by Rasa1111 on 2011-09-25
> **kostageas said:**
> Duck Duck Go should be default, but very easy to change for personal preference.  IMO, of course.

 Checked out Duck Duck Go, and i like it!
thanks! :)

---

### Post by effenberg0x0 on 2011-09-25
Imagine things at ask.com today. Suddenly they started getting more and more hits, until they break the all-time record (like 100 hits). They phone their IT distributor and buy 10 blades, believing somehow people finally understood that they rock (CEO shouting WERE THE NEW GOOGLE at offices, etc).

Then a fix is released, and its all over.

---

### Post by PaulW2U on 2011-09-26
> **effenberg0x0 said:**
> Then a fix is released, and its all over.

Some users, such are myself are still affected, bug status has been moved from "Fix Released" to "Triaged". It isn't over yet. :D

*[Removing and re-installing Firefox brought back my search engines]*

---

### Post by alphacrucis2 on 2011-09-26
The latest FF update fixed it for me.

---

### Post by jbicha on 2011-09-26
Give it a few more hours. It should be fixed for good later today (Monday).

---

### Post by ft_ on 2011-09-26
The ubuntu3 version did it AGAIN. ](*,)

Ask.com and search bar / address bar issue.

---

### Post by effenberg0x0 on 2011-09-26
Go ask.com!!! If we pump hits into it a little more its net value may top bing.com!!

Ask.com search: What is ubuntu? <enter>

Second hit == Windows® 8 Dev Preview

LMAO... This is just great.
Look, this is not a bug per se. Lets make it the official Ubuntu OSs search engine. Lets endorse it. Where everyone see bug we should see business opportunity. Come on, how many linux distros have their own crappy pet search engine?

Regards,
Effenberg

---

### Post by batty on 2011-09-26
Well, Latest update has restored all search engines for me.
Did update, no need to remove and reinstall Firefox.

---

### Post by x-shaney-x on 2011-09-26
Hah! Another update this morning and the problem is back again.
Ask as search and can't search in address bar again.

---

### Post by sammiev on 2011-09-26
I changed it myself after the 1st update and it never came back. :)

---

### Post by ELD on 2011-10-06
Just confirming the problem is still here, any idea what is going on? So close to release such an odd bug to still be slipping through!

---

### Post by x-shaney-x on 2011-10-06
Well it's gone for me... along with firefox.  I'm on to chromium full-time now (not just cos of the ask problem though, many others).

I would assume this one will get sorted before release.

---

### Post by blueridgedog on 2011-10-06
> **ajgreeny said:**
> The forum search, unfortunately, is rubbish.  Much better to use [googlubuntu]("http://www.googlubuntu.com/")

Yes, the forum search is a bit cumbersome now that we are all accustomed to Google.  I generally do something like "site:ubuntuforums.org firefox search" and get results I need pretty quick.

---

### Post by VinDSL on 2011-10-06
> **x-shaney-x said:**
> Well it's gone for me... along with firefox.[...]
Bwahahahaha!  First lol of the day.  Thank you, for that!  :D

I *think* I said it above, but...

I only use Firefox for downloads (DownThemAll extension) and maintaining  bookmarks/passwords (Xmarks extension) on my own personal FTP server, e.g. I use Fx for the sake of two most-excellent extensions - that's all.  I haven't been happy with Fx since, version 3.0-ish.

Chromium is a MUCH better choice, IMO, but it's as bland as a lunar landscape.

Opera-**Next** is my browser of choice, these days.  I'm surprised more ppl don't use it.  Takes a little getting used to.  I think of it as the "Unity" of the browser world.  LoL!

I make use for all three browsers, for different purposes, but Firefox has been relegated to the back burner on my install(s).

---

### Post by kjano on 2011-10-06
> **effenberg0x0 said:**
> sudo killall firefox && sudo apt-get remove --purge firefox && sudo apt-get update && sudo apt-get install firefox fixes it for me. 


same for me, other workarounds did not work for me.

---

### Post by jbicha on 2011-10-08
This should be fixed (again) in this Firefox version in oneiric-proposed later today:
firefox (7.0.1+build1+nobinonly-0ubuntu2) oneiric-proposed; urgency=low    * We need to keep the postinst magic for the distribution.ini folder ->     symlink transition permanently to handle upgrades from Natty, as Natty     users are upgrading from the the same upstream version of Firefox as     Oneiric, and always will be. This means that we can't rely on the install     location changing during the upgrade (LP: #869311)     - update debian/firefox.postinst.in

---

### Post by OpSecShellshock on 2011-10-08
When this happened to mine last week I just navigated to the main installation directory where the XML files for the search plugins are (which I can't remember how I found just now, sorry) and found that they were all still there. So then what I did was I copied all of them, then navigated to the corresponding search plugin folder in the Firefox profile in my home directory, where they were missing, and pasted the XML files I had just copied. Then I restarted Firefox and my search engines were all back to normal. I also removed Ask, which had never been there before. Perhaps Jeeves infiltrated the development team?

---

