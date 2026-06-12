---
title: "[SOLVED] Firfox is Misbehaving BADLY....Help..."
date: 2008-09-02
forum: New to Ubuntu
---

### Post by sillyboy on 2008-09-02
When I click on the minimize window(-)...it disappears as if I clicked on the "(x)".  Also, when I click on Tbird mail... either on the panel or from the Applications menu.  It never shows up. Help!

Thanks

---

### Post by HittingSmoke on 2008-09-02
Try running both in the Terminal to see any error output

---

### Post by sillyboy on 2008-09-02
How do I do this??

---

### Post by rossjman1 on 2008-09-02
Applications > Accesories > Terminal
The command for Firefox is "firefox"

---

### Post by sillyboy on 2008-09-02
I typed in firefox (I spelled it right this time), and it opened.  No errors showed up in the terminal.  I then clicked on the - to minimize and the window disappeared.  Then I typed in thunderbird in the terminal and nothing show up as if I clicked on the icon.  Now what??:confused:

---

### Post by mkvnmtr on 2008-09-02
OK to explain how my Firefox works in this regard. In the right hand upper corner there are three boxes. One with a X, one with a box and one with a minus sign. When I click on the X Firefox closes. When I click on the box Firefox minimizes. When I click on the minus sign the window disappears but Firefox is still open. I can click on it in the bottom bar and a window will open again. I think this is normal. Tell us where you care clicking to have these problems. I think maybe you are clicking on the minus sign.

---

### Post by sillyboy on 2008-09-02
That's just it.  When I click on the minus sign (-) Firefox disappears from everywhere.  It is NOT on the bottom panel where it used to sit waiting for me to maximize it.  It just closes as if I clicked on the (x).:confused:

I hope this is clear enough. I don't know how else to explain it.

Thanks

---

### Post by mkvnmtr on 2008-09-02
I am not sure but I seem to remember that before the 8.04.1 and the Firefox upgrade when I clicked on the minus sign I got a smaller and very short window. Maybe what we have here is a bug that should be reported. I do still have Firefox open on the bottom bar and it reopens in the same tab. I had not thoought of it as wrong until I read your post an thought about a while. Sory I don't have any idea how to fix it.

---

### Post by Madwida on 2008-09-03
Hi 

See this post: 

[http://ubuntuforums.org/showthread.php?t=909577&highlight=minimize+window](http://ubuntuforums.org/showthread.php?t=909577&highlight=minimize+window)

go to the panel; right click; add to panel; add "window list."  You will then see on the panel all of your open apps.

---

### Post by Tatty on 2008-09-03
Lets just check wether firefox is actually closing when you click minimise.

Open one instance of firefox, then click minimise to reproduce your problem.  Then click System->Administration->System Monitor, and check in the processes tab to see if "firefox" is still loaded.

When you clicked minimise after loading it from a terminal, what happened in the terminal? Did you get any messages appear?

---

