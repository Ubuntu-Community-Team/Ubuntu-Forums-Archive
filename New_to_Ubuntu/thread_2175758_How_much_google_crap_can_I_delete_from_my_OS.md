---
title: "How much google crap can I delete from my OS?"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by courseinmiracles2 on 2013-09-20
I was in the package manager and I did a search "google" and was totally suprised at how google stuff was on my machine. Question is, how much of can I delete without messing up the system?

i would really like to know.

Thanks

P.S. using ubuntu 13.04

---

### Post by whatthefunk on 2013-09-20
Probably all of it, but you should post the list of Google programs so we can see what exactly youre talking about first.

---

### Post by courseinmiracles2 on 2013-09-20
plugin for AIM , GaduGadu, MSN, Google Talk (Jabber/XMPP), Facebook, Yahoo!, Salut,
Gadu-Gadu, Groupwise, ICQ and QQ. This package contains UOA account plugins for the Empathy IM application.

akonadi-kde-resource-google
aspell-ar-large
bitlbee - common, dev, libpurple,plugin-otr
blogilo
chromium-browser
chroium-chromedriver
claws-mail-gdata-plugin
clive
cloudprint
drupal6-mod-site-verify
drupal6-mod-xmlsitemap
fcitx-googlepinyin
gcalcli
gmail-notify
gmusicbrowser
google-mock
google-perftools
google-sitemapgen
googleecl
googlefontdirectory-tools
grive

just to name a few...it looks like hundreds more, can that be right?

---

### Post by deadflowr on 2013-09-20
Did you install any of those packages?

If not, then none of them should actually be installed.
But that also depends on which other packages you've installed.
Sometimes packages bring in other packages(if not flagged to not bring in other packages; ie, --no-install-recommends)

---

### Post by whatthefunk on 2013-09-21
akonadi-kde-resource-google - this is KDE specific so if youre not using KDE, you dont need this
aspell-ar-large - this is an Arabic dictionary for Aspell, made by google and can be deleted unless you use Aspell for Arabic
bitlbee - this is not a google product...it only comes up in a search because it can be used with Google products and networks
blogilo - this is not a google product...it only comes up in a search because it can be used with Google products and networks
chromium-browser - this is also not a google product, but Google Chrome is mentioned in the package details
chroium-chromedriver - this is also not a google product, but Google Chrome is mentioned in the package details
claws-mail-gdata-plugin - this is a plugin for Claws Mail so that you can access Google services and can be deleted if you dont use google services through Claws Mail

etc....

Most of these are products made by open source developers to enable users to use open source software with Google products.  If you want to delete them, Id suggest going through them all and reading the details about each package to assess whether or not you need it.

---

### Post by mörgæs on 2013-09-21
You could also choose to be happy that there's so extensive support for Google's services in Buntu, unlike Apple.

Anyway, if you want to make so radical changes to your system it will probably be faster to reinstall using the [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") approach.

After that you can descide for yourself which packages you want to add.

---

### Post by DuckHook on 2013-09-21
> **mörgæs said:**
> ...if you want to make so radical changes to your system it will probably be faster to reinstall using the [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") approach...

+ 1

mörgæs's approach will not only be faster, but yield a more stable system. It is asking for trouble to uninstall components that might serve as dependencies for some of the functionality on your current install.

---

### Post by Rob Sayer on 2013-09-21
I don't care that much about apps that can use google, but I don't like google tracking services loading with my web pages.

Installing the DoNotTrackMe firefox plugin does a pretty good job of blocking them.  Plus, web pages load significantly faster.

I think that plugin may be available for chromium but I don't have much faith that it's work nearly as well as it does in firefox.  I have chromium installed but hardly ever use it.  You can't auto delete history/cookies et al on shutdown without a plugin in chrome or chromium.  That's kind of a deal breaker for me.

---

### Post by whitesmith on 2013-09-21
As one who shares **Rob Sayer**'s mistrust of being tracked by Google, why not remove Chromium and limit your browsing to FF? That way, you might be able to delete your Google stuff. Problem is, who knows how far up s**t creek dependency issues will take you? I would certainly image my entire drive before going hog-wild with rm.

---

### Post by Jonathan Precise on 2013-09-21
> **Rob Sayer said:**
> I think that plugin may be available for chromium but I don't have much faith that it's work nearly as well as it does in firefox

The plugin is available for chrome, chromium, and firefox (please forgive me if I forgot one on the list). I use it for chrome, and it works the same as it sis with firefox.

> **Rob Sayer said:**
> I have chromium installed but hardly ever use it.

Then why not uninstall it?

> **Rob Sayer said:**
> You can't auto delete history/cookies et al on shutdown without a plugin in chrome or chromium. That's kind of a deal breaker for me.

I use chrome/chromium, and they have a setting to auto-delete cookies on exit. (No plugin!)

[HR][/HR]I also think this question could be more in the security discussions of the forum.

---

### Post by stinkeye on 2013-09-21
Applications shown when searching for google in synaptic does not mean it's all "google stuff".
Just mentioning google in the description is enough for the application to show in the search.

---

