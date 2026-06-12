---
title: "Edit HTML source?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by CinemaScope on 2008-11-20
Hey,I have a little guide on my machine which has my notes about how to do stuff. For easy access it's written in HTML. When I invoke it, Firefox is automatically brought up to display it. When I check the code (View --> Page source) I can't edit it and save the changes. Why is this? 

Another problem: on Windows I created a desktop shortcut to the guide so I don't have to go through the menus to get it, but when I did this with Ubuntu, the link doesn't work. I have successfully made desktop links to folders, but not to an HTML file...
Thanks in advance.

---

### Post by billgoldberg on 2008-11-20
> **CinemaScope said:**
> Hey,I have a little guide on my machine which has my notes about how to do stuff. For easy access it's written in HTML. When I invoke it, Firefox is automatically brought up to display it. When I check the code (View --> Page source) I can't edit it and save the changes. Why is this? 

Another problem: on Windows I created a desktop shortcut to the guide so I don't have to go through the menus to get it, but when I did this with Ubuntu, the link doesn't work. I have successfully made desktop links to folders, but not to an HTML file...
Thanks in advance.

Because firefox isn't an html editor.

Right-click the html file and choose to open it with gedit (could be called "Text Editor").

---

### Post by CinemaScope on 2008-11-20
Thanks for the quick reply -- yes that's it. I'm used to windows in which the default browser allows you to also edit HTML source code.

My other problem is still a mystery: I make a link to the "main page" of my HTML guide in it's folder, then drag the shortcut to the desktop. When I click it, I do get the main page (displayed in Firefox), but when I click on any of the links, they don't work. I get a warning saying: "File not found. Please check the location and try again...Do you have sufficient access permissions to request item?"

---

### Post by pennacook on 2008-11-20
> I get a warning saying: "File not found. Please check the location and try again...Do you have sufficient access permissions to request item?"
It is likely that there are hardcoded directory references in your link paths. Since you are in a different directory, it now can't find them.

---

### Post by CinemaScope on 2008-11-20
pennacook -- would that not also be true of the "main page" which _does_ display?

---

### Post by The Cog on 2008-11-20
> **CinemaScope said:**
> Thanks for the quick reply -- yes that's it. I'm used to windows in which the default browser allows you to also edit HTML source code.
IE is also an HTML editor? Or do I misunderstand you?
> My other problem is still a mystery: I make a link to the "main page" of my HTML guide in it's folder, then drag the shortcut to the desktop. When I click it, I do get the main page (displayed in Firefox), but when I click on any of the links, they don't work. I get a warning saying: "File not found. Please check the location and try again...Do you have sufficient access permissions to request item?"
You mean href links in the main page to other html pages don't work? This will be because a symbolic link in Linux doesn't make the user change directory - let me try and explain:

Suppose your collection of html files is in ~/notes. Your main file is ~/notes/index.html. And it contains a relative reference to note1.html - another file in the same directory. 

Now you make a link to ~/notes/index.html in ~/index.html and open this in Firefox. The relative href in the document is for note1.html in the same directory - ~/note1.html. But it ain't there. You need to either fix the href to notes/note1.html, or also make links to all the other files. 

Better still, open the file in its real location and stop trying to fool the browser. A desktop launcher containing the command firefox ~/notes/index.html should  do the trick.

---

### Post by jamesrl on 2008-11-20
Try adding this firefox add-on, to open page source with an external editor.
This is the same as internet explorer launching notepad to look at page source.
[https://addons.mozilla.org/en-US/firefox/addon/394](https://addons.mozilla.org/en-US/firefox/addon/394)

---

