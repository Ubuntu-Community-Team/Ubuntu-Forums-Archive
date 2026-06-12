---
title: "Using Boost.Process Library on Ubuntu"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Saila on 2012-06-11
Hi,
I have already installed Boost C++ Libraries and they work correctly.
But Boost.Process is not yet an official Boost library, so I must download and install it separately. As Boost.Process is header-only the two directories boost and libs in the zip archive only need to be copied to your Boost directory. ([http://www.highscore.de/boost/process/](http://www.highscore.de/boost/process/))
I'm new in Ubuntu, can anybody talk me how to do it?
I tried manualy to copy Boost.Process in Boost folder (which is located in /usr/include/boost), but this action is not enabled.

Thanks.

---

### Post by coffeecat on 2012-06-11
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by Xernie on 2012-06-11
> I tried manualy to copy Boost.Process in Boost folder (which is located in /usr/include/boost), but this action is not enabled.

What do you mean not enabled? Is it a permission thing? Your user doesn't have permissions to write in /usr/include/boost, so you need to use sudo. You can do one of two things:

[LIST=1]
[*]Open a terminal and type "sudo nautilus".
[*]Type Alt-F2 and type "gksudo nautilus".
[/LIST]

In both cases you will be prompted for your password. After that, the file browser should come up and you should be able to copy the Boost.Process directory to /usr/include/boost.

If it's not a permission thing, you need to explain what you mean by "not enabled".

---

