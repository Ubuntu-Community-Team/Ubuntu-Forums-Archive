---
title: "Firefox 7 beta1"
date: 2011-08-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-19
There is a new FF version 7 available from the Oneiric repos now.
And of course really some changes:

> firefox (7.0~b1+build1+nobinonly-0ubuntu1) oneiric; urgency=low

  * New upstream release from the beta channel (FIREFOX_7_0b1_BUILD1)

  * Rewrite the apport hook to be more useful
    - update debian/apport/firefox.py.in
  * Update the apport blacklist file now that the binary name has changed
    - update debian/apport/firefox.in
  * Dropped patches which are obsolete/fixed upstream
    - remove debian/patches/cairo-lcd-filter.patch
    - remove debian/patches/fix-sdk-bin-install.patch
    - update debian/patches/series
  * Refresh patches
    - update debian/patches/firefox-kde.patch
    - update debian/patches/mozilla-kde.patch
    - update debian/patches/reload-new-plugins.patch
  * Look in the correct location for the staged langpack xpi's. They moved
    from dist/install to dist/linux-$(DEB_HOST_GNU_CPU)
    - update debian/rules
  * Ensure we use DEB_BUILD_* and DEB_HOST_* consistently so that cross-
    compiling works
    - update debian/rules
    - update debian/mozconfig.in
    - update debian/firefox-dev.install.in
  * Improve the description for unavailable language packs
    - update debian/control.langpacks.unavail
  * Simplify firefox-dev.install a bit by installing everything in
    /usr/include
    - update debian/firefox-dev.install.in
  * Use $(MOZ_DISTDIR) rather than $(MOZ_OBJDIR)/dist in debian/rules.
    - update debian/rules
  * Handle video/webm mimetypes
    - update debian/firefox.desktop.in
  * Fix check-sync-dirs.py test failure - ensure config/system-headers and
    js/src/config/system-headers are kept in sync
    - update debian/patches/unity-globalmenu-build-support-patch
  * Fix browserGlue_distribution.js and browserGlue_smartBookmarks.js xpcshell
    test failures. Update DEFAULT_BOOKMARKS_ON_MENU with the correct number of
    default bookmarks
    - update debian/patches/ubuntu-bookmarks.patch
  * Fix jsreftest failures by setting the correct timezone and locale
    - update debian/testsuite.mk
  * Switch off debian/patches/fix-selection-drag-autoscroll.patch for now. It
    doesn't apply and needs a rethink
    - update debian/patches/series
  * Fix "format not a string literal and no format arguments" error
   - add debian/patches/printf-fix.patch
   - update debian/patches/series
  * Update for the binary name change
    - update debian/firefox.install.in
    - update debian/firefox.sh.in
  * Ensure we install dependentlibs.list so that Firefox knows which libs
    to dlopen before libxul
    - update debian/firefox.install.in
  * Get rid of some more hanging IPC xpcshell tests
    - update debian/testsuite.mk
  * Now Firefox lazy loads libxul, drop the LD_LIBRARY_PATH hack from the
    shell wrapper (LP: #561124)
    - update debian/firefox.sh.in
  * Refresh shipped locales for beta
    - refresh debian/locales.shipped
    - refresh debian/locales.unavailable
    - refresh debian/control
  * Ship a file in /etc/apport/native-origins.d to enable bug reporting
    on PPA branches
    - add debian/apport/native-origins.in
    - rename debian/apport/firefox.in => debian/apport/blacklist.in
    - update debian/rules
    - update debian/firefox.install.in
    - update debian/firefox.dirs.in

---

### Post by aeronutt on 2011-08-19
A few of my 6.0 plugins that I REALLY like don't work in 7.0. Is there a way to revert to 6.0?

---

### Post by x-shaney-x on 2011-08-19
Might be worth checking websites or the extension authors to see if they have updated versions?

Regarding changes in FF 7, the changelog is only describing packaging changes, any changes in firefox itself?

---

### Post by Harry33 on 2011-08-19
> **x-shaney-x said:**
> Might be worth checking websites or the extension authors to see if they have updated versions?

Regarding changes in FF 7, the changelog is only describing packaging changes, any changes in firefox itself?

You may find more info from the mozilla's website.

---

### Post by Harry33 on 2011-08-19
> **aeronutt said:**
> A few of my 6.0 plugins that I REALLY like don't work in 7.0. Is there a way to revert to 6.0?

Yes there is.
You can remove the firefox packages first (like firefox, firefox-gnome-support, firefox-branding)
Then install FF 6 b5 (the same files) from Oneiric repos.
Here: 
[https://launchpad.net/ubuntu/+source/firefox/6.0~b5+build1+nobinonly-0ubuntu3](https://launchpad.net/ubuntu/+source/firefox/6.0~b5+build1+nobinonly-0ubuntu3)

---

### Post by ventrical on 2011-08-19
> **aeronutt said:**
> A few of my 6.0 plugins that I REALLY like don't work in 7.0. Is there a way to revert to 6.0?

Unistall FF7 , go to synaptic , type firefox and the 6.0x packet is there. Thats if the uninstall goes ok. Never tried it .. just assuming.

---

### Post by ventrical on 2011-08-19
> **ventrical said:**
> Unistall FF7 , go to synaptic , type firefox and the 6.0x packet is there. Thats if the uninstall goes ok. Never tried it .. just assuming.

It was there until I now have FF7!

doh!

---

### Post by aeronutt on 2011-08-19
> **Harry33 said:**
> Yes there is.
You can remove the firefox packages first (like firefox, firefox-gnome-support, firefox-branding)
Then install FF 6 b5 (the same files) from Oneiric repos.
Here: 
[https://launchpad.net/ubuntu/+source/firefox/6.0~b5+build1+nobinonly-0ubuntu3](https://launchpad.net/ubuntu/+source/firefox/6.0~b5+build1+nobinonly-0ubuntu3)

Awesome, I'll give this a try, thanks.
EDIT: downloaded .deb from here, and all is well, 6.0 loaded and working. Thanks again!
(Oneiric has become my goto load!)
[https://launchpad.net/ubuntu/oneiric/amd64/firefox/6.0~b5+build1+nobinonly-0ubuntu3](https://launchpad.net/ubuntu/oneiric/amd64/firefox/6.0~b5+build1+nobinonly-0ubuntu3)

---

### Post by rburkartjo on 2011-08-19
will give ff 7 a try usually use chromium

---

### Post by xebian on 2011-08-19
> **aeronutt said:**
> Awesome, I'll give this a try, thanks.
EDIT: downloaded .deb from here, and all is well, 6.0 loaded and working. Thanks again!
(Oneiric has become my goto load!)
[https://launchpad.net/ubuntu/oneiric/amd64/firefox/6.0~b5+build1+nobinonly-0ubuntu3](https://launchpad.net/ubuntu/oneiric/amd64/firefox/6.0~b5+build1+nobinonly-0ubuntu3)

BUt once you do update it will be replaced again by v7* unless you pin it.

You can download directly the tar files from Mozilla and extratc to /opt and then create a symlink to /opt/firefox/firefox in  /usr/bin

---

### Post by jbicha on 2011-08-19
> **Harry33 said:**
> There is a new FF version 7 available from the Oneiric repos now.
And of course really some changes

Firefox 7 will be the Firefox version shipping in Oneiric (until a month later when Firefox 8 is released).

---

### Post by ventrical on 2011-08-20
Turns out FF7 isn't all that bad.

---

### Post by yooozy on 2011-08-20
Guys, isn't like Firefox is moving ahead too fast in a crazy way!?
I think it's hard for users to catch up with new versions and features! 
what about addons compatibility! they're always legging behind, IMO

Anyway, I like to try new things but I'm still grasping changes on firefox 5 
 however firefox is still my number one choice nothing can replace it:)




~yooozy

---

### Post by PhantmKllr on 2011-08-20
> **yooozy said:**
> Guys, isn't like Firefox is moving ahead too fast in a crazy way!?
I think it's hard for users to catch up with new versions and features! 
what about addons compatibility! they're always legging behind, IMO

Anyway, I like to try new things but I'm still grasping changes on firefox 5 
 however firefox is still my number one choice nothing can replace it:)




~yooozy
First thing I do from a fresh Ubuntu install: delete Firefox.

Google Chrome is the future.

---

### Post by VinDSL on 2011-08-20
> **ventrical said:**
> Turns out FF7 isn't all that bad.
Heh!  Read between the lines, yes?  :D

The only reason I keep Fx around is for sync'ing my bookmarks, et cetera, with Xmarks - and DownThemAll (downloads).

Anybody know if these extensions still work in Firefox 7 beta 1?

---

### Post by VinDSL on 2011-08-20
> **PhantmKllr said:**
> First thing I do from a fresh Ubuntu install: delete Firefox.

Google Chrome is the future.
Bwahahaha!  Well, I was thinking that way - but you said it.

I'm too paranoid to use Google Chrome.  Chromium is a close second.

And, I've essentially replaced Firefox with Opera Next pre-alpha.

So, Opera Next, Chromium, and Firefox are currently my picks, in that order.

Actually, I have uses for all three...  ;)

---

### Post by PhantmKllr on 2011-08-20
Well, you're definitely more adventurous than I am.

I'd never use more than one browser at a time. Brand purism is a way of life.

---

### Post by VinDSL on 2011-08-20
> **PhantmKllr said:**
> Well, you're definitely more adventurous than I am.

I'd never use more than one browser at a time. Brand purism is a way of life.
In a catholic sense (with a small "c") I only run "one browser at a time", but...

I have three browsers on hand, for different purposes.

None of them do everything equally well, so...

---

### Post by PhantmKllr on 2011-08-20
I never have more than one browser installed at any given time; was the intended message.

You know what I meant, GAWD. :lolflag:

---

### Post by VinDSL on 2011-08-20
I've been using Firefox 7.0 for the past hour, and it's very well behaved!

Actually, I forgot I was using it... which is a good thing.  LoL!

Xmarks & DownThemAll are supported, so it's a keeper.  ;)

---

### Post by aeronutt on 2011-08-20
FF7 isn't compatible with 'Hide Title Bar Plus' yet, which does this (saves vertical screen space by getting rid of the title bar).

[IMG]http://i.imgur.com/JOn4g.png[/IMG]

---

### Post by xerosis on 2011-08-20
FF7 was giving me loads of 'script is not responding' errors so I had to go back to 6 for the time being.

---

### Post by Sennaista on 2011-08-20
Gmail doesn't load properly, freezes the browser.

---

### Post by sgage on 2011-08-20
> **Sennaista said:**
> Gmail doesn't load properly, freezes the browser.

Gmail works fine here. I haven't had a single issue with FF 7 (yet), but I don't use a lot of extensions - just Adblock Plus really.

---

### Post by Sennaista on 2011-08-20
> **sgage said:**
> Gmail works fine here. I haven't had a single issue with FF 7 (yet), but I don't use a lot of extensions - just Adblock Plus really.

I disabled and enabled all the add-ons and it works now. Strange. :confused:

---

### Post by Sennaista on 2011-08-20
I think my problem was flash related. Tried to reinstall the 32bit version but there was an error during the installation so ended up installing the 64bit version by following these [instructions]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins"). All's good now.

---

### Post by lovinglinux on 2011-08-20
> **yooozy said:**
> Guys, isn't like Firefox is moving ahead too fast in a crazy way!?
I think it's hard for users to catch up with new versions and features! 
what about addons compatibility! they're always legging behind, IMO..

In fact, it is better for add-ons compatibility. I am not considering Firefox 7, because it is still beta, but Firefox 6 was released four days ago an only one of all my 64 add-ons doesn't work by default, which is a miracle.

To know why or to discuss the rapid release cycle, see [this thread]("http://ubuntuforums.org/showthread.php?t=1818283").

For add-on compatibility support, see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

