---
title: "What Happened?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by zaivala on 2008-05-15
With the latest batch of updates to Ubuntu... all of a sudden my Firefox (2 OR 3) cannot read its plugins, which include (in my case) AdBlock, AllInOne Sidebar, McAfee SiteAdvisor, FoxMarks...  maybe one or two others... so now I'm getting all the ads and everything.

I have not updated Firefox in this time (although there have been a couple updates, and I downloaded them and they would not install -- and have you ever tried to read Firefox error messages?).  So it can only (in my opinion, based on very little experience) be the Ubuntu updates.

[edited to include} Oh yeah, and my Stumble button/bar is missing, as well as my Back & Forward buttons.

Moss

---

### Post by warbread on 2008-05-15
Well, I'm using Adblock and I haven't had your problems.  Also judging by the fact that the forums aren't flooded with angry newcomers, I would say that the problem is more likely local. One of those hard to read errors would be helpful here.

---

### Post by Xiong Chiamiov on 2008-05-15
What about if you install fasterfox, swiftweasel or ice-cat?  They're all really firefox, just with slightly different toppings.

---

### Post by Living2007 on 2008-05-15
> **zaivala said:**
> With the latest batch of updates to Ubuntu... all of a sudden my Firefox (2 OR 3) cannot read its plugins, which include (in my case) AdBlock, AllInOne Sidebar, McAfee SiteAdvisor, FoxMarks... maybe one or two others... so now I'm getting all the ads and everything.
 
I have not updated Firefox in this time (although there have been a couple updates, and I downloaded them and they would not install -- and have you ever tried to read Firefox error messages?). So it can only (in my opinion, based on very little experience) be the Ubuntu updates.
 
[edited to include} Oh yeah, and my Stumble button/bar is missing, as well as my Back & Forward buttons.
 
Moss
You must have upgraded to 3 beta. I use 2.0.0.14 and use some of the plig-in mentioned
 
Because Ff 3 is still in beta, thoes plug-ins won't work untill it is out of beta.
 
Solution; don't have one just yey, but find some help through google.

---

### Post by zaivala on 2008-05-15
> **Living2007 said:**
> You must have upgraded to 3 beta. I use 2.0.0.14 and use some of the plig-in mentioned
 
Because Ff 3 is still in beta, thoes plug-ins won't work untill it is out of beta.
 
Solution; don't have one just yey, but find some help through google.

As I stated, I use both Firefox 2 (because FoxMarks is not yet available for 3) and sometimes 3 (beta 5)... I tried both, and found that none of my plugins worked in either.  And the plugins DID work in 3 Beta (again, except for FoxMarks, which refused to install as it is not yet available for 3).

Moss

---

### Post by zaivala on 2008-05-15
> **warbread said:**
> Well, I'm using Adblock and I haven't had your problems.  Also judging by the fact that the forums aren't flooded with angry newcomers, I would say that the problem is more likely local. One of those hard to read errors would be helpful here.

Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

Warning: Selector expected.  Ruleset ignored due to bad selector.
Source File: [https://www.google.com/accounts/ServiceLogin?service=mail&passive=true&rm=false&continue=https%3A%2F%2Fmail.google.com%2Fmail%2F%3Fnsr%3D1%26ui%3Dhtml%26zy%3Dl&ltmpl=default&ltmplcache=2&hl=en](https://www.google.com/accounts/ServiceLogin?service=mail&passive=true&rm=false&continue=https%3A%2F%2Fmail.google.com%2Fmail%2F%3Fnsr%3D1%26ui%3Dhtml%26zy%3Dl&ltmpl=default&ltmplcache=2&hl=en)
Line: 26

Warning: Unexpected end of file while searching for closing } of invalid rule set.
Source File: [https://www.google.com/accounts/ServiceLogin?service=mail&passive=true&rm=false&continue=https%3A%2F%2Fmail.google.com%2Fmail%2F%3Fnsr%3D1%26ui%3Dhtml%26zy%3Dl&ltmpl=default&ltmplcache=2&hl=en](https://www.google.com/accounts/ServiceLogin?service=mail&passive=true&rm=false&continue=https%3A%2F%2Fmail.google.com%2Fmail%2F%3Fnsr%3D1%26ui%3Dhtml%26zy%3Dl&ltmpl=default&ltmplcache=2&hl=en)
Line: 27

Warning: Expected declaration but found '*'.  Skipped to next declaration.
Source File: [https://a248.e.akamai.net/sec.yimg.com/lib/common/css/fonts_2.0.0-b2.css](https://a248.e.akamai.net/sec.yimg.com/lib/common/css/fonts_2.0.0-b2.css)
Line: 7

Warning: Error in parsing value for property 'display'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_important.css?v=370](http://ubuntuforums.org/clientscript/vbulletin_important.css?v=370)
Line: 46

Those are only a very few of the errors... I can't tell what is caused by which.  Maybe I'll uninstall FF2 and reinstall...

Moss

---

### Post by Xiong Chiamiov on 2008-05-15
If you're going to reinstall, I'd suggest you do a purge reinstall (which will get rid of all your configs for firefox).

---

### Post by zaivala on 2008-05-15
> **Xiong Chiamiov said:**
> If you're going to reinstall, I'd suggest you do a purge reinstall (which will get rid of all your configs for firefox).

Don't know what that is or how to do it.  I used Synaptic to do the uninstall and then Add/Remove programs to reinstall... and have the same thing.

No Back or Forward buttons, no StumbleUpon bar, no AllInOne Sidebar, and no AdBlock Plus (even though AllInOne and Adblock were included in my reinstall).

Moss

---

### Post by zaivala on 2008-05-15
I just tried to install Foxmarks again.

...error message...

Firefox could not install the file at 

[https://addons.mozilla.org/en-US/firefox/downloads/file/24763/foxmarks_bookmark_synchronizer-2.0.45-fx.xpi](https://addons.mozilla.org/en-US/firefox/downloads/file/24763/foxmarks_bookmark_synchronizer-2.0.45-fx.xpi)

because: Unexpected installation error
Review the Error Console log for more details
-203

...and in the Error Console...

Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

---

### Post by doctorbighands on 2008-05-17
I'd like to go on record and say that I'm in EXACTLY (and I mean EXACTLY) the same boat as the OP with Firefox. Clearly, then, it isn't a "local problem" as one suggested. I'd love it if someone could help us figure out how to get Firefox to work properly. I feel like it's going downhill really fast, but I digress...

After the upgrade to Hardy, I got stuck with the beta of Firefox 3. It's incredibly unstable right now and prone to frequent, random crashing, so I attempted to revert to version 2, and now I can't get any add-ons to work.

I'd really just be happy if I could get my StumbleUpon toolbar back (I admit I'm addicted. It's a fault of mine lately!).

Any ideas?

---

### Post by warbread on 2008-05-17
> **zaivala said:**
> Don't know what that is or how to do it.  I used Synaptic to do the uninstall and then Add/Remove programs to reinstall... and have the same thing.

No Back or Forward buttons, no StumbleUpon bar, no AllInOne Sidebar, and no AdBlock Plus (even though AllInOne and Adblock were included in my reinstall).

Moss

Back up any Firefox bookmarks you value and try

```
:-$ sudo apt-get remove --purge remove mozilla-firefox
```

---

### Post by warbread on 2008-05-17
> **doctorbighands said:**
> I'd like to go on record and say that I'm in EXACTLY (and I mean EXACTLY) the same boat as the OP with Firefox. Clearly, then, it isn't a "local problem" as one suggested. I'd love it if someone could help us figure out how to get Firefox to work properly. I feel like it's going downhill really fast, but I digress...


One here,

It is a local problem, as in local to your circumstances.  I'm not having this problem, and I haven't seen millions of threads asking for help on this.  My point was just that it's not a problem with Firefox, per se.

Try the suggestion above and see if that helps.  If not, we try something else.

---

### Post by zaivala on 2008-05-17
> **doctorbighands said:**
> I'd like to go on record and say that I'm in EXACTLY (and I mean EXACTLY) the same boat as the OP with Firefox. Clearly, then, it isn't a "local problem" as one suggested. I'd love it if someone could help us figure out how to get Firefox to work properly. I feel like it's going downhill really fast, but I digress...

After the upgrade to Hardy, I got stuck with the beta of Firefox 3. It's incredibly unstable right now and prone to frequent, random crashing, so I attempted to revert to version 2, and now I can't get any add-ons to work.

I'd really just be happy if I could get my StumbleUpon toolbar back (I admit I'm addicted. It's a fault of mine lately!).

Any ideas?

Well, I have a temporary fix... I downloaded SeaMonkey, which is largely the 1.5 Mozilla Firefox code with some extras, and my Back bar and most of my plugins are working... no FoxMarks, and I can't get AdBlock to install, but StumbleUpon is working great.

Glad it isn't just me.

Moss

---

### Post by zaivala on 2008-05-17
> **warbread said:**
> Back up any Firefox bookmarks you value and try

```
:-$ sudo apt-get remove --purge remove mozilla-firefox
```

OK, did that...

Reading package lists ... Done
Building dependency tree
Reading state information ... Done
E: Couldn't find package remove
:-$

---

### Post by zaivala on 2008-05-20
> **zaivala said:**
> OK, did that...

Reading package lists ... Done
Building dependency tree
Reading state information ... Done
E: Couldn't find package remove
: - $

Nobody has any information for me here?  It has been a couple days...

Moss

---

### Post by Psyker7 on 2008-05-20
code should have been
```
sudo apt-get --purge remove mozilla-firefox
```

---

### Post by zaivala on 2008-05-20
> **Psyker7 said:**
> code should have been
```
sudo apt-get --purge remove mozilla-firefox
```

Thank you, I'll try that.

Moss

---

### Post by zaivala on 2008-05-20
> **Psyker7 said:**
> code should have been
```
sudo apt-get --purge remove mozilla-firefox
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mozilla-firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 upgraded
: -$

---

### Post by zaivala on 2008-05-20
That was an amazing result, seeing as how I have Firefox2, Firefox3B5, and Seamonkey all installed, all of them using mozilla code...

---

### Post by Psyker7 on 2008-05-20
```
sudo apt-get --purge remove firefox
```
Prehaps... Not sure why mozilla-firefox was posted honestly.

---

### Post by zaivala on 2008-05-20
Well, that uninstalled Firefox2 (when I click the Firefox2 button, I get Firefox3 Beta5), reset everything that was wrong in Firefox3 Beta5, and also installed some plugins I was using in 2 that were supposedly not ready for 3... so I would say that is a successful conclusion, for which I thank you.

Moss

---

### Post by nowshining on 2008-05-20
may i suggest using a hosts file with adblockplus - that way u won't actually see any ads but only can't connect if any boxes. :) u can find mine in the link in my sig.

edit:

also download the plugin manually - change the extension to .zip any xpi and .jar files for firefox are actually .zip files - unzip - change the maxversion in the .rdf file to a higher # - save and re-package it as zip and rename it to .xpi and ctrl + o in ur browser and install.

also have a look here. [http://www.oxymoronical.com/web/firefox/nightly](http://www.oxymoronical.com/web/firefox/nightly)

---

### Post by zaivala on 2008-05-20
> **nowshining said:**
> may i suggest using a hosts file with adblockplus - that way u won't actually see any ads but only can't connect if any boxes. :) u can find mine in the link in my sig.

I was already using ABP, in fact whatever happened to alter my Firefox kept it from reading any of my plugins, which is why I wanted to fix it.  It is now fixed.  Thanks for your interest.

Moss

---

### Post by zaivala on 2008-05-20
> **nowshining said:**
> may i suggest using a hosts file with adblockplus - that way u won't actually see any ads but only can't connect if any boxes. :) u can find mine in the link in my sig.

edit:

also download the plugin manually - change the extension to .zip any xpi and .jar files for firefox are actually .zip files - unzip - change the maxversion in the .rdf file to a higher # - save and re-package it as zip and rename it to .xpi and ctrl + o in ur browser and install.

also have a look here. [http://www.oxymoronical.com/web/firefox/nightly](http://www.oxymoronical.com/web/firefox/nightly)

The link in your sig is bad, has too many http:// in it and you need to remove the quote marks.  It works fine after deleting that stuff though...

I note you're still promotion 7.01... need to update the page?

Moss

---

### Post by nowshining on 2008-05-20
lolz thanks for catching the errors :)...

and 7.01?

u mean 7.10 and I updated it to my current install.

---

### Post by nowshining on 2008-05-20
the sig should now be fixed. :) and again thanks for catching that and letting me know..-

---

### Post by warbread on 2008-05-20
> **Psyker7 said:**
> ```
sudo apt-get --purge remove firefox
```Prehaps... Not sure why mozilla-firefox was posted honestly.

That's what it used to be, not too long ago.  I was at a Windows box at the time and couldn't verify the package name.  My bad!

---

### Post by jrev on 2008-06-05
> **zaivala said:**
> I just tried to install Foxmarks again.

...error message...

Firefox could not install the file at 

[https://addons.mozilla.org/en-US/firefox/downloads/file/24763/foxmarks_bookmark_synchronizer-2.0.45-fx.xpi](https://addons.mozilla.org/en-US/firefox/downloads/file/24763/foxmarks_bookmark_synchronizer-2.0.45-fx.xpi)

because: Unexpected installation error
Review the Error Console log for more details
-203

...and in the Error Console...

Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

I installed foxmarks ok on my three PC's on a local network but I don't know how to upload the bookmarks of my first computer to synchronize it on the two others...
Cannot find any detailed explanation on the configuration of the parameters
If you got the answer I am waiting for thanks

---

### Post by zaivala on 2008-06-05
> **jrev said:**
> I installed foxmarks ok on my three PC's on a local network but I don't know how to upload the bookmarks of my first computer to synchronize it on the two others...
Cannot find any detailed explanation on the configuration of the parameters
If you got the answer I am waiting for thanks

If you have FoxMarks loaded to each of your computers, then they are (or should be) synchronized and you can re-synch on any other computer running Firefox with FoxMarks.

I did get my problem fixed -- something screwed up somewhere, and by deleting Firefox2 using Warbread's sudo instruction below, everything cleared and works again.  I'm having trouble installing things to BOTH Firefox2 and Firefox3B5, but since 3B5 is now running all my plugins, that's not a problem.

Moss

---

