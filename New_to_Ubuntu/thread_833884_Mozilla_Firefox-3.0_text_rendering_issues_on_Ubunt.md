---
title: "Mozilla Firefox-3.0 text rendering issues on Ubuntu 8.04"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by ctenn2ls on 2008-06-19
Alright, this is a problem that I've been having with Mozilla Firefox 3.0 on Hardy since it's been in beta.  I thought it might get fixed with the final release, but much to my frustration, it was not.  Whenever I start Firefox up, the text is rendered incorrectly, making reading a nightmare.  It seems that the spaces characters in between the words are expanded so that every sentence    looks   like   this   on    every   page, even on the text box, configuration menus, and context menu.

[IMG]http://farm4.static.flickr.com/3092/2592271512_72dc816cb2.jpg?v=0[/IMG]

Here is a screenshot of the issue.

So, I've tried everything that I can think of to resolve this problem.  I deleted v 2.0 and 3.0, have scrubbed the /usr/etc and /home directories of any traces, have used synaptic to totally remove everything related to any mozilla products, and upon a fresh install, the problem still persists.  I'm just about at wit's end, so any help would be appreciated.

I decided to post this in the ubuntu forum because the issue does not occur on my Intel Core-Duo Quad core running Vista.  However, my humble little Pentium 4 Dell with Ubuntu 8.04 on it is having all the issues.  I'm willing to do just about anything to get this working right now.

P.S. Thank you in advance for the help.  This is my first post, but I have been using these forums for help and knowledge for the last 5 months and the help has been invaluable.

---

### Post by RSingh on 2008-06-19
You can try recreating your profile but that will remove all of your firefox bookmarks and addons, so go with this only if you backed up your bookmarks etc:

Press Alt-F2
type:
```

firefox -profilemanager
```

delete your old profile and create a new default one.

---

### Post by ctenn2ls on 2008-06-19
I tried this before, and also again just now, and the problem didn't go away.

---

