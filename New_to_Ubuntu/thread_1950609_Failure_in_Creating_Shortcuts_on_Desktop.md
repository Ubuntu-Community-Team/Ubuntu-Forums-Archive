---
title: "Failure in Creating Shortcuts on Desktop"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by pras8421 on 2012-04-01
Hi,
I've ubuntu 11.10 installed in my system and I'm unable to create desktop shortcuts.
I request for proper guidance.

---

### Post by HiImTye on 2012-04-01
what error do you get when you try to create them?

---

### Post by pras8421 on 2012-04-01
I actually don't have an idea of creating it...

---

### Post by HiImTye on 2012-04-01
ah, you mean command shortcuts. the best option is to make an empty document with a .sh extension and make a bash script such as:
example.sh
```
#!/bin/bash
/path/to/command -any-switches any_other_parameters
exit
```

---

### Post by pras8421 on 2012-04-01
I didn't get it.I'm sorry!

---

### Post by HiImTye on 2012-04-01
what do you want to make a shortcut to? Ill give you an example script using that

---

### Post by pras8421 on 2012-04-01
Well,Say for example,shortcut of chromium browser or any other app.

---

### Post by HiImTye on 2012-04-01
Chromium.sh
```
#!/bin/bash
chromium-browser
exit
```
edit: right click on it on your desktop after making it and then go to the permissions tab then put a check in the check box for 'allow executing file as program'

---

### Post by pras8421 on 2012-04-01
This code just opens a new window of the browser....
What I needed was the browser's shortcut to be mounted on the desktop...

---

### Post by HiImTye on 2012-04-01
```
#!/bin/bash
chromium-browser http://your.website.com/whatever/page/you/want.html
exit
```

---

### Post by pras8421 on 2012-04-01
I don't have my website

---

### Post by HiImTye on 2012-04-01
that's where the webpage you are trying to create a link on your desktop to goes

---

### Post by pras8421 on 2012-04-01
I guess, you haven't understood my question,
I can have all apps on the sidebar on the left,but the same thing can't be mounted on the desktop

---

### Post by HiImTye on 2012-04-01
[http://windows.microsoft.com/en-US/windows/shop/download-windows-7](http://windows.microsoft.com/en-US/windows/shop/download-windows-7)

---

### Post by pras8421 on 2012-04-01
What next?

---

### Post by pras8421 on 2012-04-01
It,s all about not able to create icons on desktop of my computer .....
May i know the requirement of the particular link here?

---

### Post by Krytarik on 2012-04-01
> **pras8421 said:**
> I've ubuntu 11.10 installed in my system and I'm unable to create desktop shortcuts.
> **pras8421 said:**
> ... for example,shortcut of chromium browser or any other app.
Please see this post:

[http://www.tuxgarage.com/2011/10/creating-desktop-launchers-in-11-10.html](http://www.tuxgarage.com/2011/10/creating-desktop-launchers-in-11-10.html)

Regards.

---

### Post by Kevin McCready on 2012-04-01
I also have to say I have no idea what HiImTye is trying to say. Where do I create an sh file? How will an icon get onto the desktop etc etc. If HiImTye could slow down a bit it might help.

Meanwhile, this is what I do:

To make Desktop shortcut. Open a terminal with Ctrl-alt-t, then
```
cd Desktop
ln -s /<directory where your file or program is>/[<name of your file or program>

```

Hope this helps.

---

### Post by pras8421 on 2012-04-04
I'll try this out..thanks

---

