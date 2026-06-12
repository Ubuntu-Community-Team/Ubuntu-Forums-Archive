---
title: "Newbie with wxpython"
date: 2009-03-09
forum: Programming Talk
---

### Post by tjpren on 2009-03-09
Hi,
I'm wondering whether anyone can assist with code correction.  I'm trying to teach myself python/wxpython.

I've got some basic python code working, and am wanting some GUI around it.

Basically, I'm wanting a user to enter a two names into two textctrl's.  A button click sends the contents of the textctrl into the body of the application for some processing (thats the python part that works).  The output is then sent to another textctrl as a result.

My problem is redirecting the textctrl into the python body.

When I use the button event, the code jumps to the section where I try to read the contents of the textctrl's, but I get an error message:
[B]
NameError: global name 'basicText' is not defined[/B]

where basicText is the name of the first of the textctrl's

---

### Post by The Cog on 2009-03-09
Without code its hard to tell, but usually, for me, that error message means I forgott to put **self.** in front of the variable name.

---

### Post by tjpren on 2009-03-10
Thanks for that,

yes, i needed to put the **self** in the statement.  Also, in looking round, noticed that **self.<name>.GetValue()** would retrieve the value from the wx.textctrl, and that GetValue is case sensitive.

I've now developed my first python/wxpython app and feel pretty good about it.

I'm still a bit stumped on sizer's - I need to read up more on them.  I liked the python part a lot, but can see I'm going to struggle with the wx part.

Regards

---

