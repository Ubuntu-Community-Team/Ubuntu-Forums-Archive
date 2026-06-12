---
title: "Cannot type in inkscape"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by snowguy on 2012-09-10
When I open inkscape I can't type any characters. For example if I select the text tool, then click somewhere with the mouse, then click the letter e, instead of showing an "e" on the page, it opens the Edit menu. 

Another example: If I choose File Save As. Then click to rename the file and then type a letter it uses the letter to change the directory. If for example I type "d", rather than putting a "d" in the file name, as I'd expect, it changes me to the Desktop folder. 

I don't see others out there with this problem so I assume it is something simple on my part, but I can't figure out what. Any help?

---

### Post by snowguy on 2012-09-10
Is there anyone who has a minute to help me test this one? Ideally it would be someone running 12.04 64 bit normal install with all updates applied. 

Here's what I need help for someone to test...

1 Install inkscape (unless you already have it). 
2 Click on the text icon on the toolbar on the left (13th down from the top).  
3 Click anywhere on the page. (You should see a blinking cursor where you clicked). 
4 Try typing something (e.g. the letter e) and see if your letters go on the page (as they should) or if they are being used to control the menus.

Obviously I can't get any work done in inkscape if I can't use the keyboard. I may go ahead and reinstall my ubuntu on this laptop,  but I'd love to find out first from someone out there whether the problem is specific to me, or whether it came with some recent update. 

thanks,

---

### Post by GreatDanton on 2012-09-10
It's working fine here. I have tested it also on Development release. You can try removing Inkscape with ```
sudo apt-get purge inkscape
``` and then installing again.

---

### Post by snowguy on 2012-09-10
:( purging and reinstalling didn't solve the problem. Restarting didn't solve the problem. Taking out my USB keyboard and just using the one built into the laptop didn't solve the problem. 

Next up I'll try the live CD. If that works, i guess I'll do a fresh install and see what I may have installed that is causing this issue.

GreatDanton, thanks for taking the time to test for me. It is very helpful to know that it is something about my setup specifically.

---

