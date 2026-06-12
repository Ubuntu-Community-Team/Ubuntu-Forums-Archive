---
title: "Google says my Firefox is out of date"
date: 2014-11-26
forum: New to Ubuntu
---

### Post by LizzyJean on 2014-11-26
I updated ubuntu to 14.10 when it came out, and ever since then, Google tells me on my gmail page that my Firefox browser is out of date.  But the package manager doesn't offer me any new upgrades of Firefox and neither does the "About Firefox" window. Right now, I'm on Firefox 33.0

Is Google wrong?

---

### Post by carl4926 on 2014-11-26
33 is correct

I don't have this happen

Show us a screen of it

---

### Post by LizzyJean on 2014-11-26
Um.  Can't figure out how to paste a screenshot here so that you can see it.  But it's a yellow strip across the top of my screen that says:
"This version of Firefox is no longer supported. Please upgrade to a [COLOR=#0000cd]supported browser[/COLOR]. [COLOR=#0000cd]Dismiss[/COLOR]"

The "supported browser" link goes to:
[https://support.google.com/mail/answer/6557?hl=en](https://support.google.com/mail/answer/6557?hl=en)
which lists supported browers.  if I click to download Firefox, I get this page:
[https://www.mozilla.org/en-US/firefox/new/](https://www.mozilla.org/en-US/firefox/new/)
which says "looks like you're using an older version of Firefox", but I don't know if that's specific to me
when I click on "free download" it offers to download this file:  firefox-33.1.1.tar.bz2

Hope that's enough info.  Thanks for your help.

---

### Post by carl4926 on 2014-11-26
This is what I see
I can't see your screen
[http://paste.opensuse.org/48266562](http://paste.opensuse.org/48266562)

What version of Ubuntu are you using?

---

### Post by vasa1 on 2014-11-26
Interesting that the repo is still offering Firefox 33.0. I wonder whether the repos of other (non-Ubuntu-dependent) distros are doing the same thing. I've been on 33.1.1 direct from Mozilla since Nov 14. Still, Google shouldn't be making a fuss about 33.0 unless some serious security issue is at stake.

OP, could this be your issue?
> If you're using a supported browser, but see a message in Gmail that your browser is unsupported, you may be using an extension that interferes with browser detection. Try disabling your browser extensions to resolve the problem.
[https://support.google.com/mail/answer/6557?hl=en](https://support.google.com/mail/answer/6557?hl=en)

---

### Post by vasa1 on 2014-11-26
> **LizzyJean said:**
> I updated ubuntu to 14.10 when it came out, and ever since then, Google tells me on my gmail page that my Firefox browser is out of date.  But the package manager doesn't offer me any new upgrades of Firefox and neither does the "About Firefox" window. Right now, I'm on Firefox 33.0

Is Google wrong?As I've pointed out in the post above, it's possible some extension of yours is responsible for Google thinking your Firefox is outdated. Please try [with all extensions disabled]("support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode") or [with a new profile]("support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles").

On the other hand, 33.0 is **not** the latest: 33.1.1 is. The standard Ubuntu repo is still offering 33.0. The output of **apt-cache policy firefox** has```
  Candidate: 33.0+build2-0ubuntu0.14.04.1

```

Re. the "About Firefox" window, you won't see updated software being offered that way if your Firefox is from the Software Center so that is normal.

---

### Post by philinux on 2014-11-26
I just logged in to my gmail account and got no errors at all.

I'm on 14.10 and Firefox about says 33.0 (Installed: 33.0+build2-0ubuntu0.14.10.1).

I have a few extensions installed. See screenshot. Maybe OP can use Firefox safe mode to see if it is an extension causing error.

---

### Post by vasa1 on 2014-11-26
> **philinux said:**
> ...
I have a few extensions installed. See screenshot. Maybe OP can use Firefox safe mode to see if it is an extension causing error.
Yes, safe mode is an easy first step. Re. Adblock Plus and NoScript, it's quite possible for two users to see different results depending on what is allowed or blocked.

---

### Post by Dennis N on 2014-11-26
I saw the "outdated" message from Google a few weeks ago, but that OS was on FF 29 at the time. Yes, FF 33.1.1 is the latest, direct from Mozilla. FF 33.1 is the first version that pushes ads to your new tab page by default.

[http://www.computerworld.com/article/2847727/mozilla-plunks-ads-into-firefox.html](http://www.computerworld.com/article/2847727/mozilla-plunks-ads-into-firefox.html)

---

### Post by vasa1 on 2014-11-26
> **Dennis N said:**
> ... FF 33.1 is the first version that pushes ads to your new tab page by default.
...
I didn't notice that because I have```
browser.newtab.url file:///home/vasa1/Dropbox/MyLinks.html"
```

---

### Post by monkeybrain20122 on 2014-11-26
What is your system's time and date? Did you change that by any chance?

---

