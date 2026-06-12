---
title: "Xubuntu 11.10  and firefox"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by senorian on 2012-10-20
How do I *permanently* remove the 9 little windows that keep on appearing.
I have tried setting the start page to "blank" but that seems only to work once. (the button is greyed  out)
Perhaps if I knew what FF calls this page I could find the answer in FF
many thanks

---

### Post by Merrattic on 2012-10-20
What 9 little windows ? Need a bit more information about what is happening when you open FF.

If you open FF and go: File > Preferences > General

Select "When Firefox Starts" > "Show my Homepage"
and
Set Home Page as > [www.google.com](www.google.com)  (or your own preference)

It could be you are set to open up all your previous tabs?

---

### Post by mike555 on 2012-10-20
When you start Firefox look in the right top of the window, you will see a little icon , click it .

---

### Post by critin on 2012-10-20
Are you talking about the bookmark / quickdial page?  You don't like that?  
On the top right corner of that page, you'll see a tiny icon of the nine blocks, (very tiny)
Hold the curser over that and it should say 'hide the new tab page'.  Click it to hide the page.

edit:  oops, darn typo!  Mike beat me to it.

---

### Post by Cheesemill on 2012-10-20
Click on the icon that's a group of 9  squares (3x3) in the top right of that page.

This icon toggles display of the new tab page.

---

### Post by Michael Dooley on 2012-10-20
The latest update (Firefox 13) introduced a new tab feature that displays browser history. I didn't like it. To change this behavior, do the following: type "about:config" in the address bar. After an amusing warning appears, agree and you'll see a bunch of firefox settings.

Type the following 'settings':
browser.newtabpage.enabled - toggle to false - new tab may behave as before. However,
browser.newtab.url should also be changed to something other than the feature default (about:newtab)
I set the value to [http://images.google.com/](http://images.google.com/)

This changes the nine little windows to something of your choosing.

Good luck senorian.

double oops. please see above answers.

---

### Post by vasa1 on 2012-10-20
> **Michael Dooley said:**
> ... However,
browser.newtab.url should also be changed to something other than the feature default (about:newtab)
I set the value to [http://images.google.com/](http://images.google.com/)
...
I use a local home page of my regularly visited sites instead of an external link. Or, one could just change about:newtab to about:blank to get a blank page.

---

### Post by senorian on 2012-10-21
many thanks Critin
the icon is so small that ,untill you pointed it out, I didn't see it.
Many thanks to all who offered help

---

