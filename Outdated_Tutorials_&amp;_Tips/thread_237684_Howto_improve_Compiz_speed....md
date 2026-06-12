---
title: "Howto: improve Compiz speed..."
date: 2006-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by atrus123 on 2006-08-16
From: [http://www.animewine.com/index.php?entry=entry060816-122616](http://www.animewine.com/index.php?entry=entry060816-122616)

Lately, I've run into real problems with Compiz running like molassis. Of course, my laptop video card is leaves much to be desired (ATI Xpress 200m), but that didn't explain the extreme degredation in performance over the past few weeks.

I adjusted the framerate and the texture quality, but this offered only a slight improvement.

My ultimate solution is a bit disappointing: I had to give up on quinnstorm. Quinn has been doing great things for the community, and I still use much of the stuff that he worked on, but for some reason the quinnstorm Compiz appears to have developed some issues, which Quinn is still trying to work out.

If you are running into a similar issue with Compiz slowdown, I suggest Ubuntu Dapper users attempt the following:

# sudo apt-get install compiz-vanilla

Perhaps that will take care of it. Not only have I seen improvement from quinnstorm, but I'm seeing significant improvement over the vanilla I used to use before switching to quinn.

However, it is unfortunate to move away from the quinnstorm builds considering that they do offer some really sweet features absent from vanilla.

I hope to return to Quinn in the near future, but for now, I'm vanilla and loving the performance.

Some other things you can do to improve performance would be to open your gconf-editor:

# gconf-editor

And navigate apps -> compiz -> general -> screen0 -> options, and lower the refresh rate to something like 30 (I think the default is 50).

Up one level to allscreens -> options, you can also adjust texture_filter to fast.

This later stuff isn't much of a fix; it only reduces animation quality, which may, in some cases, improve speed. You may want to try this before switching to Vanilla.

Sources:
Compiz.net

---

