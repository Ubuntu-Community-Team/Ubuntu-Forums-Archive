---
title: "Remove Menus from FF3"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by cartisdm on 2008-11-12
I just downloaded the Chrome theme for FF3 (I love it btw), but how can I remove the file menu stuff?  I don't think this question is chrome-theme specific because I didn't see a way to do it with the default theme either.  I could just be missing something simple though.  Look at my screenshot to see what I'm talking about.  In the real chrome browser there's two icons the the top right side of the browser that hold all the options the menus would hold

---

### Post by ciscosurfer on 2008-11-12
These should get you started:

[http://en.dogeno.us/2008/05/firefox-3-interface-tweaking-through-the-userchromecss-file/](http://en.dogeno.us/2008/05/firefox-3-interface-tweaking-through-the-userchromecss-file/)
[http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)
[http://eriwen.com/firefox/howto-tweak-chrome-for-a-cleaner-firefox/](http://eriwen.com/firefox/howto-tweak-chrome-for-a-cleaner-firefox/)

---

### Post by cartisdm on 2008-11-12
All the guides (including more I found on google) keep telling me about the userChrome.css.  How the heck to I get to that?!! Nothing seems to want to lay it out straight for me haha


Edit:  Nevermind, was able to find an idiot-proof guide:)

---

### Post by ciscosurfer on 2008-11-12
[http://kb.mozillazine.org/UserChrome.css](http://kb.mozillazine.org/UserChrome.css)

[http://kb.mozillazine.org/UserContent.css](http://kb.mozillazine.org/UserContent.css)

You can also look into modifying the .js files as well

Edit: Glad you found it.

---

### Post by cartisdm on 2008-11-12
I see lots of code for removing the menus, but if I remove them completely how can I access the stuff when I do need to access it?

```
#
/* Remove the Edit and Help and History menus
#
 Id's for all toplevel menus:
#
 file-menu, edit-menu, view-menu, go-menu, bookmarks-menu, tools-menu, helpMenu */ 
#
#file-menu, #helpMenu, #edit-menu, #go-menu, #bookmarks-menu { display: none !important; }
```

---

### Post by ciscosurfer on 2008-11-12
Ha.  Well, you can choose *not* to remove them.  There might be a sidebar extension that can provide most of what you need (the All-in-One Sidebar extension comes to mind). Maybe the addons site has an extension that can do what you want but retain the functionality you need.  But until they make a version for Linux, you'll have to either use Wine or Crossover to possibly get Firefox to work the way you want it to.  You can also add your name to [this list]("http://www.google.com/chrome/intl/en/linux.html") so you can be notified when the dev team at Google is ready to release Google Chrome for Linux.

---

### Post by cartisdm on 2008-11-12
True.  With the links you sent me I will be able to play around with enough things that will make the browser cleaner (which is all I really care about anyway).  Thanks for the info and I will certainly add my name to that list!

---

