---
title: "[SOLVED] Firefox won't open"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-05-20
My Firefox in Hardy Heron will not open after I added an extension from Miro to help them (they get a small donation for purchases from Amazon).  I don't know if it is strictly related to that extension but the problem started after installing it so looks suspicious! (I think it's called iheart or something like that)

To correct, must I completely uninstall FF and then reinstall?  Is there any way to remove an extension if I can't open the application itself?

(FF 3 beta 5)

thanks

---

### Post by iaculallad on 2008-05-20
Try looking at this [Mozilla]("http://kb.mozillazine.org/Firefox_:_FAQs_:_Uninstall_Extensions") page for manually uninstalling an addon. Scroll down the page until you reach the section which reads "Uninstalling an add-on manually". Hope this would help.

---

### Post by Skeet on 2008-05-20
Its most likely that the plugin you installed isn't supported by Firefox 3. Use the above post and uninstall the plugin and see if it fixes it. You might have to revert to the older Firefox 2.x if you want the plugin to be supported.

---

### Post by bilbo.san on 2008-05-20
Hey,
Open FF on safe mode and remove that 'addon', close it and reload it like you would normally do.

>>you can go to your Terminal and run (for Firefox):

((path/to/firefox))firefox **-safe-mode**
 
That should fix it.
b.

---

### Post by flyingsolo on 2008-05-20
Brilliant!  I uninstalled it via safe mode and all is golden again.  So much for trying to help out Miro!
Thanks to iaculalad & skeet & bilbo.san!
And I just learned another tool--I never knew about FF safe mode!
Thanks again.

---

### Post by bilbo.san on 2008-05-20
You are welcome Flyingsolo!

b.

---

### Post by Skeet on 2008-05-21
Not a problem.

Have fun!

---

### Post by iaculallad on 2008-05-21
You are welcome. Go Ubuntu

---

