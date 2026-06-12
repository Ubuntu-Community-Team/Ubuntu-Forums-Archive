---
title: "or a FireFox bug?  I'm not sure"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by webbdawg on 2008-06-09
When I visit some forums (sailing site not porn) and there are images posted that are displayed in a reduced size by the forum software.

When I click them to get the full sized image it opens in a new window that completely takes over the monitor. There are no menus, toolbars or buttons to close the window. But my bookmarked links tool bar shows up at the top (weird). The only way to close the window is the keyboard short cut (ctrl shft w).

Here is the [link to the image]("http://forums.sailinganarchy.com/index.php?showtopic=73812&pid=1736195&st=0&#entry1736195") I recently looked at. FF does it with all images that you click to view full size.

It took a while for me to figure out I needed to remember the keyboard short cut for closing a window.

I do have my browser set to open links in tabs but images seem to pup up in new windows(that take over the screen). But a link to a new page pops up in tabs.??

Thanks
Dave

---

### Post by webbdawg on 2008-06-09
Just an FYI, Nothing like this happens with my FF/windows machine. So I don't know if it is a function of the way Ubuntu handles new windows or FF.

Thanks
Dave

---

### Post by Myglaren on 2008-06-09
Same her (Ff 3/Vista)  They open in the same tab.
Clicking on them just increases the size in the same tab.

Off to check on the Ubuntu machine.

---

### Post by cariboo on 2008-06-09
Just out of curiosity what happens when you right click on the link and ask it to open link in new tab.

I tried the links out and they automagically open in a new tab.

It probably is a misconfiguration in Firefox. The thing I would check it if you go into Edit-->Preferences, click the tab icon and make sure  New pages should be opened in: a new tab is selected.

Jim

---

### Post by Myglaren on 2008-06-09
No, just the same with Firefox on 8.04.
All contained within the normal window dimensions ( I wish I could say the same of some of my photo's)

This is just a bit of guesswork on my part and likely complete hokum but in the address bar type abouf:config.
Go down the listing to: 
browser.chrome.image_icons.max_size;1024
and see if it is 1024 or some other size.

---

### Post by webbdawg on 2008-06-09
> **cariboo907 said:**
> Just out of curiosity what happens when you right click on the link and ask it to open link in new tab.

I tried the links out and they automagically open in a new tab.

It probably is a misconfiguration in Firefox. The thing I would check it if you go into Edit-->Preferences, click the tab icon and make sure  New pages should be opened in: a new tab is selected.

Jim
Please try the link in my orginal post. Then open then click the header of the image to open it full size.

My browser is set to open links in a new tab and that is what happens when I click a link.

I am beginning to think that the forum software (Invision Power Board) overrides the tab setting and opens it in a new window. When I do a right click on the image or the header of the image I do not get the context menu with the choice to open the link in a new tab.

But I am still wondering why FF opens the window with no menu or the window(minimize, maximize or close) controls?

Very odd.

Thanks
Dave

---

### Post by webbdawg on 2008-06-09
> **Myglaren said:**
> No, just the same with Firefox on 8.04.
All contained within the normal window dimensions ( I wish I could say the same of some of my photo's)

This is just a bit of guesswork on my part and likely complete hokum but in the address bar type abouf:config.
Go down the listing to: 
browser.chrome.image_icons.max_size;1024
and see if it is 1024 or some other size.

It is set to 1024.

Which is the resolution of this monitor. It is an older 17" crt. 

Should I set the setting to something smaller??

---

### Post by Myglaren on 2008-06-09
> **webbdawg said:**
> It is set to 1024.

Which is the resolution of this monitor. It is an older 17" crt. 

Should I set the setting to something smaller??

I don't think so, I have a 19" CRT and that is the setting for it, seems to work with everything Firefox related.

I have the same settings for the laptop, 15" widescreen and it all worked OK there too.
Someone more knowledgeable will probably come along and shoot my theories down in flames but those settings didn't come close to going beyond the screen, no scroll bars were generated.

---

