---
title: "Ubuntu Firefox Modifications"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Michael.B on 2008-06-12
Just really curious to know what the extension "ubuntu firefox modifications" does?

---

### Post by MmmmJoel on 2008-06-12
> **Michael.B said:**
> Just really curious to know what the extension "ubuntu firefox modifications" does?
It allows users to install Firefox add-ons through the Ubuntu package manager.

---

### Post by uvdevnull on 2008-08-28
> **MmmmJoel said:**
> It allows users to install Firefox add-ons through the Ubuntu package manager.

Joel, is that really all it does?

---

### Post by SunnyRabbiera on 2008-08-28
> **uvdevnull said:**
> Joel, is that really all it does?

I think it also helps the update process

---

### Post by pi.boy.travis on 2008-08-28
It helps with integrating Fx with the rest of the system.  Correct me if I'm wrong, but I believe it is also responsible for GNOME-ish looking UI.

---

### Post by frankvw on 2009-02-22
> **uvdevnull said:**
> Joel, is that really all it does?
No. It also breaks the toolbars of certain extensions, or combinations thereof. A good example is Tab Mix Plus and the Web Developer Toolbar; the buttons on the Web Developer Toolbar disappear and cannot be restored until the Ubuntu Firefox Modifications extension is disabled. :(

// Frank

---

### Post by HungryMan on 2009-02-24
The annoying "switch page direction" feature

---

### Post by rootsonwings on 2009-03-11
Nevermind, i installed the mozilla version.

---

### Post by natrik on 2009-04-24
> **frankvw said:**
> No. It also breaks the toolbars of certain extensions, or combinations thereof. A good example is Tab Mix Plus and the Web Developer Toolbar; the buttons on the Web Developer Toolbar disappear and cannot be restored until the Ubuntu Firefox Modifications extension is disabled. :( 

// Frank


I found the same thing on my system, just after doing a recent (Mid-April 2009) distribution upgrade from Hardy to Intrepid.  (Ugh, and now Jaunty is released!)

Anyway, I was like WHERE DID ALL MY BUTTONS GO?  ...  I couldn't access any of my Firefox extensions.  I got lucky enough to start at the bottom of the plugins list disabling things, and found out that way.   My "text formatting toolbar" (for bbcode etc) and Web Developer toolbars were available, but had NO BUTTONS.   

Also, I could not get to ANY of my extensions' icons in the window you get from <right click menubar> -> Customize.  

SO WHY THE UBUNTU MODIFICATIONS IN THE FIRST PLACE?

It's my understanding that this plugin integrates the Ubuntu repositories with the "Help > Check for updates" menu item in Firefox, which is now grayed out on my system.  
**If it has other functions, community please advise!**

I DID just now get a notice from Update Manager that a new version of Firefox is available.  It upgraded just fine - I'm using it now to type this.

Disabling the Ubuntu modifications, I got back my:
AdBlock Plus
NoScript
Tabs Mix Plus
Web Developer Toolbar
Text Formatting Toolbar
Forecastbar Enhanced (a better Forecastfox)
Greasemonkey et al.
DownThemAll
DownloadHelper
and possibly others.

--Nate

---

### Post by wyth on 2009-07-03
Just in case anyone is still looking for an answer to what Ubuntu Firefox Modifications are --

The package is called [ubufox]("http://packages.ubuntu.com/jaunty/ubufox"), and it's in the repositories.  It just serves to provide a little tighter integration, including apt support (apturl), but isn't absolutely necessary.  I came across this thread when looking for why the add-on/package doesn't work with the ppa version of Firefox 3.5, and I've learned that it isn't a problem if it isn't installed.

Here's the description from the packages page:

>           **Ubuntu Firefox specific configuration defaults and apt support**

      Extension package for Firefox provides ubuntu specific configuration defaults as well as apt support for firefox plugins/extensions. 

 You can uninstall this package if you prefer to use a pristine firefox install.       



---

### Post by Andy06 on 2009-07-04
Apparently also Spell checking. My Firefox install allows me to spell check in many different variations of the English Language without any dictionaries installed. Since I have no extensions on this profile, it must be Ubufox. [Although there is the Firefox-en under languages, an addon window section that does not exist in windows, so I don't know what that does]

---

### Post by uvdevnull on 2009-07-06
> **wyth said:**
> Just in case anyone is still looking for an answer to what Ubuntu Firefox Modifications are --

The package is called [ubufox]("http://packages.ubuntu.com/jaunty/ubufox"), and it's in the repositories.  It just serves to provide a little tighter integration, including apt support (apturl), but isn't absolutely necessary.



Good find, thanks!

---

### Post by uvdevnull on 2009-07-06
> **Andy06 said:**
> Apparently also Spell checking. My Firefox install allows me to spell check in many different variations of the English Language without any dictionaries installed. Since I have no extensions on this profile, it must be Ubufox. [Although there is the Firefox-en under languages, an addon window section that does not exist in windows, so I don't know what that does]

Firefox has a spell checker built in, doesn't it?

---

### Post by philinux on 2009-07-06
I have it disabled. Also apt url works just fine without it.

---

### Post by Andy06 on 2009-07-08
> Firefox has a spell checker built in, doesn't it? 

As far as I know, it relies of external dictionaries. On windows, until you install a dictionary, firefox is linguistically challenged. Sometimes it prompts you to install automatically when you check the spell check in options. Other times it doesn't.

In Ubuntu, it seems to have support for more than just a couple of languages, on my computer it can correct me in all sorts of English (pity no Jamacain English dictionary). I don't know where all these dictionaries came from? Ubufox? Ubuntu's customised build of firefox? Would love to know.

---

### Post by Andy06 on 2009-07-08
Wait a min, if apt works without it as well like the posted 2 posts above said and its not the one disabling "check for updates" and it doesn't provide dictionaries. What the hell DOES it do? :D

---

### Post by the.dark.lord on 2009-09-12
> **Andy06 said:**
> Wait a min, if apt works without it as well like the posted 2 posts above said and its not the one disabling "check for updates" and it doesn't provide dictionaries. What the hell DOES it do? :D

I just wondered the same thing. Anybody got answers?

---

### Post by Darktrax on 2009-09-12
I had hoped it would take care of the strange huge font in Google's search input box - but it does not :|

---

### Post by the.dark.lord on 2009-09-12
> **Darktrax said:**
> I had hoped it would take care of the strange huge font in Google's search input box - but it does not :|

I read somewhere that change was made by Google themselves. I don't like it either!

---

### Post by philinux on 2009-09-12
All it does is provide apt support for extensions and addons.

---

### Post by the.dark.lord on 2009-09-15
> **philinux said:**
> All it does is provide apt support for extensions and addons.

Ah, thanks!

---

### Post by SirYes on 2009-09-22
Actually after listing files installed by ubufox package, one can get these (grep pattern is for finding files only instead of directories):

```
$ dpkg -L ubufox | grep '.*\..*'
/.
/etc/firefox-3.0
/etc/firefox-3.0/pref
/etc/firefox-3.0/pref/ubufox.js
/usr/share/ubufox/defaults/preferences/ubufox-pfs.js
/usr/share/ubufox/defaults/preferences/ubufox.js
/usr/share/ubufox/defaults/preferences/ubuntu-mods.js
/usr/share/ubufox/chrome/ubufox.jar
/usr/share/ubufox/chrome.manifest
/usr/share/ubufox/components/pluginGlue.js
/usr/share/ubufox/install.rdf
/usr/share/ubufox/searchplugins/ask.xml
/usr/share/doc/ubufox/example-homepage.properties
/usr/share/doc/ubufox/changelog.Debian.gz
/usr/share/ubufox/defaults/preferences/000system.js
/usr/lib/mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/ubufox@ubuntu.com

```Checking the contents of above files confirm the plugin is rather harmless (although it may interference with some other Firefox extensions, like reported here by other commenters):

[LIST]
[*]/usr/share/ubufox/defaults/preferences/ubufox-pfs.js enables usage of Ubuntu plugin finder service
[*]/usr/share/ubufox/defaults/preferences/ubufox.js allows localization of extension descriptions
[*]/usr/share/ubufox/defaults/preferences/ubuntu-mods.js (perhaps the most interesting) sets several browser defaults, like printing, look-and-feel, disables checking for default browser, locale matching with OS, etc.
[*]/usr/share/ubufox/searchplugins/ask.xml adds Ask.com search plugin
[/LIST]
Recommended is reading /usr/share/doc/ubufox/changelog.Debian.gz for a list of recent changes in ubufox.

---

### Post by Bufeu on 2012-07-19
Excuse me for the bump, but what exactly does the add-on do? Does it disable Firefox's own update service? Does it affect Unity? Does Ubuntu Firefox Modifications and Global Menu Bar integration affect each other? This topic is kind of old, and things may have been changed.
The add-on have only caused me problems and I wonder what I will lose if I remove the whole package.
By the way, disabling "Global Menu Bar" will only affect Firefox, and no other programs?

---

### Post by oldos2er on 2012-07-19
Please start a new thread for your question.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

