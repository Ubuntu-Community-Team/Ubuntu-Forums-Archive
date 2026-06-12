---
title: "Multi monitor settings"
date: 2015-05-03
forum: New to Ubuntu
---

### Post by jonathan82 on 2015-05-03
Hi,

I am using lubuntu. I experience multi monitor support on lubuntu as poor. Even with Arandr I am not able to duplicate the horizontal panel bar like unity on ubuntu does automatically when extending the display by a second monitor. Can you give me tips/hints how I can achieve a similar effect on lubuntu?

Greetings

---

### Post by Rex Bouwense on 2015-05-03
To establish dual monitors with LXDE, install Arandr from Synaptics. Arandr can set-up placement, orientation and resolution for each monitor. Before saving, set up the geometry of any horizontal panels. For a bottom panel across both monitors, align the bottoms of the displays as in the image on the right; for a top panel, align the tops.
[http://lxlinux.com/#14](http://lxlinux.com/#14)

---

### Post by jonathan82 on 2015-05-05
Hi Rex,

Thanks for your quick reply! In the following you can find two pictures to emphasize what I mean with "duplicate the horizontal panel bar". I arranged the two outputs exactly as suggested on the site. What I get is in deed a horizontal panel bar across both screens; but unfortunetely the panel applets on the bar are not duplicated.


Ubuntu Default:


[[IMG]http://s6.postimg.org/jntrs2kxp/Multi_Monitor_Default_Ubuntu.jpg[/IMG]]("http://postimg.org/image/jntrs2kxp/")

Lubuntu current situation:

[[img]http://s6.postimg.org/g5hrvok1p/screenshot_horizontal_Bar_lubuntu.jpg[/img]](http://postimg.org/image/g5hrvok1p/)

---

### Post by Rex Bouwense on 2015-05-05
Misunderstood.  Can you right click the empty panel on the right monitor and make adjustments for it without effecting the left monitor panel?  Unfortunately I cannot test because I only have one monitor.

---

### Post by jonathan82 on 2015-05-12
Hi,

The panel is stretched on both screens. It behaves like one single panel. When I do adjustments (like adding a second task bar) it affects the whole panel. See this picture.

[[IMG]http://s6.postimg.org/wn5s0e7b1/lubuntu_multimonitor_problem_03.jpg[/IMG]]("http://postimg.org/image/wn5s0e7b1/")

I cannot define two panels on the bottom of the display (one for each screen) because lxde does only allow one panel per direction. See this picture.

[[IMG]http://s6.postimg.org/xqpwccry5/lubuntu_multimonitor_problem_04.jpg[/IMG]]("http://postimg.org/image/xqpwccry5/")

---

