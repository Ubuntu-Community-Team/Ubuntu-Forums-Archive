---
title: "terminal closes immediatly upon opening"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by HeMann on 2013-04-25
Following this tutorial [http://www.youtube.com/watch?v=lWdXZPWzMB8](http://www.youtube.com/watch?v=lWdXZPWzMB8)
I get as far as "run in the terminal", when the terminal opens for half a second, writes some text and then closes.

I can open the terminal for general use, but if I try to run _any_ programs through it it closes immediatly.
How can I fix this. Thanks

---

### Post by ibjsb4 on 2013-04-25
Are you running Lucid 10.04?  It reaches end of life in a couple of weeks.

---

### Post by Impavidus on 2013-04-25
When you open a terminal by choosing "Run in terminal", a terminal is opened just for running the script. As soon as the script terminates the terminal is closed. This script is not supposed to terminate at once, so it probably encounters an error.

The best thing to do is to open a terminal, navigate to ~/Desktop/Macbuntu-10.04 (or wherever you saved the package) and run the script with **./install.sh**. The terminal will stay open after the script terminates, so you may be able to read any error messages.

But indeed, if you use 10.04 it's better to upgrade now instead of doing some tweaks that will be undone as soon as you upgrade, especially if the tweaks aren't going easy. And it may very well be that this script (or this whole tweak package to make your Ubuntu look like a mac) doesn't work on 12.04 or 13.04. On the other hand, I think the Unity interface is more like mac than the old gnome2 interface.

---

