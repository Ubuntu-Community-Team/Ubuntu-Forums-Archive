---
title: "External Display"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by Nu2ubun on 2012-03-06
I'm trying to hook my TV up to my laptop and when i was on windows it worked no problem. Now when i hook up using ubuntu it tells me that it is not compatible i went to the displays and it comes up as a 20" sharp TV and says something about it only supports 19 by 19 or something of that sort any ideas of what i can do to fix this problem?

---

### Post by Mark Phelps on 2012-03-07
First thing you can do is tell us the make and model video chipset you're using.  Since you may not know that, open a terminal and enter "lspci" and look for the line containing "VGA".  Post that information back here.

The problem is almost certainly a lack of video driver extensions, and once we know the video chipset info, we can tell you if a newer driver is available.

---

