---
title: "HUD doesn't see Seamonkey"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by vasa1 on 2012-07-24
Seamonkey is no longer available from the Ubuntu Software Center. I downloaded it from [http://www.seamonkey-project.org](http://www.seamonkey-project.org) and installed it in /usr/local/seamonkey/ from where it functions perfectly. Except that HUD doesn't "see" it.

In other words, while running Seamonkey, if I call up HUD and type anything, I get suggestions, if any, that are related to the indicators in the top panel.
And the Seamonkey icon that initially is present next to HUD's text box is replaced with icons of the indicators present in the top panel or that of a generic file depending on how what is being typed matches HUD's database (?).

(HUD works without problems with programs that have been installed the conventional way.)

---

### Post by Curtis6767 on 2012-07-24
Huh.

---

### Post by vasa1 on 2012-07-24
> **Curtis6767 said:**
> Huh.
Did you click on Seamonkey? What did you see then? 

I saw that as well before posting :)

---

### Post by Curtis6767 on 2012-07-24
> **vasa1 said:**
> Did you click on Seamonkey? What did you see then? 

I saw that as well before posting :)

Clicked on it and got error message, so my bad on that.

Wonder if it's available through Synaptic, which I don't have installed on 12.04.

Doesn't solve your problem, though.

---

### Post by vasa1 on 2012-07-24
> **Curtis6767 said:**
> Clicked on it and got error message, so my bad on that.

Wonder if it's available through Synaptic, which I don't have installed on 12.04.

Doesn't solve your problem, though.

No, it's not available via Synaptic either.

---

### Post by vasa1 on 2012-08-03
bump

---

### Post by Paqman on 2012-08-03
Looks like Seamonkey has indeed been [removed from the repos for Precise]("https://launchpad.net/ubuntu/precise/+source/seamonkey/2.6.1-0ubuntu1") as they can't provide support for the full LTS cycle.

I wouldn't expect anything installed from outside the Ubuntu repos to work with HUD, as HUD is an Ubuntu-only feature and apps need to be patched for it to work with them.

---

### Post by MG&amp;TL on 2012-08-03
> **Paqman said:**
> 
I wouldn't expect anything installed from outside the Ubuntu repos to work with HUD, as HUD is an Ubuntu-only feature and apps need to be patched for it to work with them.

Not so. Anything that uses Gtk, Xul (FF and Thunderbird, I think), or Qt (most of the KDE apps) for its menus should work a treat. However, others may not work so well, or at all.

---

### Post by Paqman on 2012-08-03
> **MG&TL said:**
> Not so. Anything that uses Gtk, Xul (FF and Thunderbird, I think), or Qt (most of the KDE apps) for its menus should work a treat. However, others may not work so well, or at all.

I stand corrected then. I do remember them saying that only the core of default apps had been tested and if necessary patched when Precise was released.

---

### Post by MG&amp;TL on 2012-08-03
> **Paqman said:**
> I stand corrected then. I do remember them saying that only the core of default apps had been tested and if necessary patched when Precise was released.

Yup. It's not a perfect technology, and some apps (cue LibreOffice!) are not helpful in the way they implement their menus.

Sorry if I was rude earlier.

---

### Post by Paqman on 2012-08-03
> **MG&TL said:**
> 
Sorry if I was rude earlier.

Not at all!

---

### Post by vasa1 on 2012-08-03
> **MG&TL said:**
> ... Anything that uses Gtk, Xul (FF and Thunderbird, I think), or Qt (most of the KDE apps) for its menus should work a treat. However, others may not work so well, or at all.

Well, so the point is why doesn't HUD "see" Seamonkey?

My unscientific assumption for now is that HUD won't "see" anything that hasn't been installed via the Software Center or via Synaptic or via apt-get.

In the case of Seamonkey, from the link I provided, we get a tar file, **not a .deb**, that just has to be uncompressed.

In fact, my suspicion is that the "system", not just HUD, is unaware that Seamonkey has been installed because it hasn't come in via the .deb route.

As a matter of fact, even **dpkg --get-selections** doesn't "see" Seamonkey!

---

### Post by MG&amp;TL on 2012-08-03
> **vasa1 said:**
> Well, so the point is why doesn't HUD "see" Seamonkey?

My unscientific assumption for now is that HUD won't "see" anything that hasn't been installed via the Software Center or via Synaptic or via apt-get.

In the case of Seamonkey, from the link I provided, we get a tar file, **not a .deb**, that just has to be uncompressed.

In fact, my suspicion is that the "system", not just HUD, is unaware that Seamonkey has been installed because it hasn't come in via the .deb route.

As a matter of fact, even **dpkg --get-selections** doesn't "see" Seamonkey!

I don't know why it's not picking up the HUD, but it's not because you haven't installed it via .deb. The 'system' knows it's installed because it's running. All HUD does is modify the menu system.
[I]
dpkg[/I] doesn't have SM listed in its database as it hasn't installed it.

---

### Post by vasa1 on 2012-08-03
> **MG&TL said:**
> I don't know why it's not picking up the HUD, but it's not because you haven't installed it via .deb. The 'system' knows it's installed because it's running. All HUD does is modify the menu system.
*dpkg* doesn't have SM listed in its database as it hasn't installed it.
I agree with why **dpkg** doesn't see Seamonkey.

As for the rest, maybe 12.10 will have the answer.

(BTW, I uninstalled Firefox beta from the [mozilla-team ppa]("http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu") and installed Firefox beta direct from [Mozilla]("http://www.mozilla.org/en-US/firefox/channel/"). That too comes as a tar file (firefox-15.0b2.tar.bz2). That too doesn't work with HUD.)

---

### Post by Krytarik on 2012-08-03
Seems like you all need to remember that both Firefox and Thunderbird need an add-on to integrate into the Global Menu; and no, it doesn't work with Seamonkey also, tried that.

Regards.

---

### Post by vasa1 on 2012-08-03
> **Krytarik said:**
> Seems like you all need to remember that both Firefox and Thunderbird need an add-on to integrate into the Global Menu; and no, it doesn't work with Seamonkey also, tried that.

Regards.
Good point. Marking it "solved" based on this ^^^.

---

