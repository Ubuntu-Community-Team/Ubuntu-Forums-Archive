---
title: "EasyTag id3v2.3 tags"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by calc on 2008-09-17
How do you make EasyTag write id3v2.3 tags? I see this post in the archive:

[http://ubuntuforums.org/showpost.php?p=5336821&postcount=30]("http://ubuntuforums.org/showpost.php?p=5336821&postcount=30")

That post shows a screenshot where you can select a drop down box to choose which format to write tags in but on Ubuntu 8.04 I don't have that drop down box anymore. I think my car's cd player is only able to read id3v2.3 tags and not id3v2.4 tags since those show up as a bunch of dots.

Was this functionality broken in a more recent build than in the screenshot or am I doing something wrong on my system?

---

### Post by calc on 2008-09-17
> **calc said:**
> Was this functionality broken in a more recent build than in the screenshot or am I doing something wrong on my system?

I found out this was caused by installing easytag-aac 2.1.5 which apparently removes the ability to select which version of id3v2.x tags you are using. :confused:

The bug is documented [here]("https://bugs.launchpad.net/ubuntu/+source/easytag-aac/+bug/196089")

---

