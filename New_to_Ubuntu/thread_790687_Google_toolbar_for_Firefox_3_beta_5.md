---
title: "Google toolbar for Firefox 3 beta 5 ?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by zaifd on 2008-05-11
Would anyone know where I an download the Google Toolbar for Google toolbar for Firefox 3 beta 5 ?
If one doesn't exists for this version yet, are any other toolbars that do the same for the user recommended ? 
Also would anyone know a good FTP client ?

---

### Post by SunnyRabbiera on 2008-05-11
I dont think the google toolbar has been ported for it yet, if need be you can use firefox 2 instead...
remember firefox 3 is still new and in beta so a lot has not been ported to it yet, but getting firefox 2 on your system is very easy.

---

### Post by UnknownFear on 2008-05-11
There already is a Google toolbar in Firefox 3 Beta 5. Click on the drop-down list of the search bar and choose Google.

---

### Post by zaifd on 2008-05-11
> **SunnyRabbiera said:**
> I dont think the google toolbar has been ported for it yet, if need be you can use firefox 2 instead...
remember firefox 3 is still new and in beta so a lot has not been ported to it yet, but getting firefox 2 on your system is very easy.

Any other toolbars that will do the trick ?
I use the toolbar add on options that are embedded so that would really help me out if there are other once that I can install instead.

---

### Post by ajgreeny on 2008-05-11
Try **Googlebar Light**, a firefox add-on, which as far as I know works in FF v3 in Linux, so should be OK.  It is the googlebar that I have used in FF for quite a long time now, rather than the official google version.

---

### Post by bwphilip on 2008-05-13
Hi Zaifd, 
The solution is to turn off compatibility check for extensions by adding a boolean to about:config.
Type about:config in the URL section of firefox, right click in the list of settings that pops open after you promise to be careful, and choose to make a new boolean.  Name it 
extensions.checkCompatibility and set it to false.  Then you can install your toolbar.

I outline the way I got the official google toolbar to install from [http://toolbar.google.com/](http://toolbar.google.com/) in Firefox 3 beta 5 at my site at [http://bawnweb.com/content/get-google-toolbar-work-firefox-3](http://bawnweb.com/content/get-google-toolbar-work-firefox-3) - 

Hope this helps you.  Incidently, it's why I registered for this forum initially.  The toolbar was not designed for Firefox 3 so it may result in instability.  I have not noticed that myself, though.  Be careful with this setting, as you'll be able to install stuff that isn't compatible.  The toolbar seems to work fine.  If you turn the setting to TRUE or remove it after you install the toolbar though, the toolbar disappears.

---

