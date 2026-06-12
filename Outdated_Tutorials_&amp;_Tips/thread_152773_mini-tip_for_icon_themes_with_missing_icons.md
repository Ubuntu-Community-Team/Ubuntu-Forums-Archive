---
title: "mini-tip for icon themes with missing icons"
date: 2006-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by garba on 2006-03-30
forgive me if this tip might sound paultry, but I didn't know about this and now that I do, my life is taking a turn for the better. ;) Very often that nice icon theme you've just dl'ed is missing some icons. Likewise, there might be a similar looking theme which provides icons which might be a good replacement (actually, a "filler"). Hence, do as follows: go to the theme folder and open the index.theme file and look for the "inherits" entry: add, in order of preference, the icon theme gnome should use as a fall back when some icon is missing, and you are all set (actually you have to use the folder name the icon theme you're using as fallback is stored in, and to my knowledge it gotta be either in the /usr/share/icons or ~/.icons location). I hope this little tip might come in handy for all the friends here who didn't know about this nifty trick. Regards, andre

ps i'm using Dropline Nuovo as a fallback theme for Tango, it looks good.

---

