---
title: "[SOLVED] Firefox unstable"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by pzs on 2008-11-07
Just upgraded to Intrepid. If I have a few Firefox (3.0.3) windows open and then direct one of them to a page with a lot of embedded videos like:

[http://onegoodmove.org/1gm/](http://onegoodmove.org/1gm/)

it crashes hard. If I then restart Firefox and load the page, it works fine.

---

### Post by OrangeCrate on 2008-11-07
> **pzs said:**
> Just upgraded to Intrepid. If I have a few Firefox (3.0.3) windows open and then direct one of them to a page with a lot of embedded videos like:

[http://onegoodmove.org/1gm/](http://onegoodmove.org/1gm/)

it crashes hard. If I then restart Firefox and load the page, it works fine.

I just looked at that web page. I have NoScript engaged, and it comes up just fine. Looking at what NoScript is blocking, frankly, that's one big bunch of scripts tacked on to the site. If everything else is working correctly, and apparently it is, with you stating that you have multiple windows open, I think it's the site that's causing your problem, not Firefox.

---

### Post by philinux on 2008-11-07
I agree it's a bad site. I've just had 20 tabs open with no problem on the sky news website.

That site crashes FF for me and I've got flash block installed.

---

### Post by pzs on 2008-11-10
Hmm. The site may or may not be weighed down with terrible scripting. However, given that it doesn't crash under Windows or MacOS, isn't it possible that this is a problem for Firefox on Linux?

---

### Post by pzs on 2008-11-10
OK, removed totem-mozilla and replaced with mplayer-mozilla. That fixed the problem.

I don't like Totem - it always seems to either not work or cause instabilities. I would vote for replacing it with mplayer in the default build.

---

### Post by methodmarvel on 2008-11-10
> **pzs said:**
> OK, removed totem-mozilla and replaced with mplayer-mozilla. That fixed the problem.

I don't like Totem - it always seems to either not work or cause instabilities. I would vote for replacing it with mplayer in the default build.

Mark as solved if this is the solution.

I'm surprised to find a video site not using flash video - I was going to suggest that you needed flash 10 but obviously that's not the issue for this page.

---

