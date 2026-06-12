---
title: "What does Ubuntu Firefox Modifications exactly do?"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Bufeu on 2012-07-23
Quoting myself from the locked topic:> **Bufeu said:**
> What exactly does the add-on do? Does it disable [Firefox's own update  service]("http://support.mozilla.org/en-US/kb/settings-network-updates-and-encryption#w_update-tab")? Does it affect Unity? Does Ubuntu Firefox Modifications and  Global Menu Bar integration affect each other?
The add-on have only caused me problems and I wonder what I will lose if I remove the whole package (ubufox).
By the way, disabling "Global Menu Bar" will only affect Firefox, and no other programs?

---

### Post by Krytarik on 2012-07-23
> Adds Ubuntu-specific modifications to Firefox.
Integrates the browser with Ubuntu to:

[LIST]
[*]     Enable searching for missing plugins from Ubuntu software catalog
[*]     Add the following options to the Help menu
[*]     Get help on-line
[*]     Help translating Firefox
[*]     Ubuntu Release Notes
[*]     Set homepage to Ubuntu Start Page
[*]     Display a restart notification after upgrading Firefox
[*]     Add ask.com to the search engines. You can uninstall this if you prefer to use a pristine Firefox install.
[/LIST]
Source: [https://apps.ubuntu.com/cat/applications/xul-ext-ubufox/](https://apps.ubuntu.com/cat/applications/xul-ext-ubufox/)

Regards.

---

### Post by Bufeu on 2012-07-23
Uninstalled the package (using apt-get purge), but the [Update Tab]("http://support.mozilla.org/en-US/kb/settings-network-updates-and-encryption#w_update-tab") in Firefox still only displays "Search engines".

[IMG]http://i.imgur.com/H45RZ.png[/IMG]

*(If you wonder what language it is, it's Swedish.)*

---

### Post by Bufeu on 2012-07-25
I would be grateful if someone could solve this riddle foe me.

---

### Post by Zill on 2012-07-25
> **Bufeu said:**
> ...The add-on have only caused me problems and I wonder what I will lose if I remove the whole package...
What problems do you think are caused by the Ubufox extension?

I currently run Ubuntu 10.04 with Firefox 14.0.1 and have *never* experienced any problems with this extension.  My Firefox "Update Tab" shows the same as yours (i.e. only the "Search Engine" checkbox is shown) but this is because, in Ubuntu, Firefox should be updated via the normal apt-get repos, rather than directly from Mozilla such as with Windows machines.

AIUI, the Ubufox modifications simply tweak the Mozilla default settings to make them more consistent with Ubuntu and its package management system.

Note that, as with all add-ons/extensions, you can disable this within Firefox *without* needing to uninstall the package. See Tools/Add-ons/Extensions.

---

### Post by vasa1 on 2012-07-25
> **Krytarik said:**
> Source: [https://apps.ubuntu.com/cat/applications/xul-ext-ubufox/](https://apps.ubuntu.com/cat/applications/xul-ext-ubufox/)

Regards.

Interesting to see:
> Add **ask.com** to the search engines.

---

### Post by Bufeu on 2012-07-25
> **Zill said:**
> What problems do you think are caused by the Ubufox extension?

I currently run Ubuntu 10.04 with Firefox 14.0.1 and have *never* experienced any problems with this extension.  My Firefox "Update Tab" shows the same as yours (i.e. only the "Search Engine" checkbox is shown)** but this is because, in Ubuntu, Firefox should be updated via the normal apt-get repos, rather than directly from Mozilla such as with Windows machines.**

AIUI, the Ubufox modifications simply tweak the Mozilla default settings to make them more consistent with Ubuntu and its package management system.

Note that, as with all add-ons/extensions, you can disable this within Firefox *without* needing to uninstall the package. See Tools/Add-ons/Extensions.I see no problem with that at all, I just don't want it to update automatically. I want to update manually.

---

### Post by vasa1 on 2012-07-25
> **Bufeu said:**
> I see no problem with that at all, I just don't want it to update automatically. I want to update manually.
Well, you did write: "The add-on have only caused me problems"

So Zill may have asking about what you meant.

If you don't want a particular software to update, you can lock the version: [http://askubuntu.com/questions/9607/what-does-lock-version-do](http://askubuntu.com/questions/9607/what-does-lock-version-do)

(I **haven't** tried it and don't know if it will blow up your machine.)

---

### Post by uRock on 2012-07-25
> **Bufeu said:**
> I would be grateful if someone could solve this riddle foe me.

Firefox in ubuntu is not the same as it is in Windows. Firefox gets updates via ubuntu's Update Manager, whereas Firefox in Windows has to be updated on its own. When newer versions of Firefox are installed, Firefox will check for newer verions of the add-ons you've installed.

---

### Post by Zill on 2012-07-25
> **Bufeu said:**
> I see no problem with that at all, I just don't want it to update automatically. I want to update manually.
Firefox should be updated in exactly the same way as the other deb packages on your system.  You always have full control of exactly which packages are updated at any given time.

---

### Post by vasa1 on 2012-07-25
> **Zill said:**
> ... You always have full control of exactly which packages are updated at any given time.
Could you please elaborate?

---

### Post by Bufeu on 2012-07-25
> **Zill said:**
> Firefox should be updated in exactly the same way as the other deb packages on your system.  You always have full control of exactly which packages are updated at any given time.Well, for me, when a new version releases, Ubuntu installs the new version and the message "Firefox has been updated and needs to restart" popups.

---

### Post by Zill on 2012-07-25
vasa1/Bufeu:  See [PinningHowto]("https://help.ubuntu.com/community/PinningHowto")

Regarding update frequency you are, of course, free to choose how often updates are applied - this does *not* need to be automatic nor immediately they are released!

---

### Post by Bufeu on 2012-07-25
> **Zill said:**
> vasa1/Bufeu:  See [PinningHowto]("https://help.ubuntu.com/community/PinningHowto")

Regarding update frequency you are, of course, free to choose how often updates are applied - this does *not* need to be automatic nor immediately they are released!Well, on my system it seems to that packages updates by themself when a new version releases.

---

### Post by vasa1 on 2012-07-25
> **Bufeu said:**
> Well, on my system it seems to that packages updates by themself when a new version releases.

Allowing or restricting package updates are unrelated to "What does Ubuntu Firefox Modifications exactly do?"

Just to put things another way, the extension referred to has nothing to do with Firefox updates.

There are additional changes made to the Firefox versions supplied by Canonical to remove the updating mechanism employed by Mozilla. That is why the "update tab" you included in an earlier post does not look like this:

---

### Post by Bufeu on 2012-07-25
> **vasa1 said:**
> Allowing or restricting package updates are unrelated to "What does Ubuntu Firefox Modifications exactly do?"

Just to put things another way, the extension referred to has nothing to do with Firefox updates.

There are additional changes made to the Firefox versions supplied by Canonical to remove the updating mechanism employed by Mozilla. That is why the "update tab" you included in an earlier post does not look like this:So if I download FF from Mozilla's website, the Update Tab will look "normal"?

---

### Post by vasa1 on 2012-07-25
> **Bufeu said:**
> So if I download FF from Mozilla's website, the Update Tab will look "normal"?

Yes, but whether it's advisable or not is the question.

---

### Post by Bufeu on 2012-07-25
> **vasa1 said:**
> Yes, but whether it's advisable or not is the question.Thanks, I think I'll mark this topic as "Solved".

---

