---
title: "Wget with cookies of chromium-browser?"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by honeybear on 2012-12-08
Hi,

The cookies might or not be into ~/.config/chromium
but I could not find them.

Here it tells how to plugin to get them. However for using with wget with --load-cookies, it is far to be explained.
[http://stackoverflow.com/questions/913296/how-to-see-cookie-information-of-chrome-browser](http://stackoverflow.com/questions/913296/how-to-see-cookie-information-of-chrome-browser)

Would you know this basic wget operation?

thanks

---

### Post by Frogs Hair on 2012-12-08
From the GUI cookies in Chrome can be viewed in the following location unless cleaned . I don't if Chromium is identical or not. 

Settings > Advanced Settings > Content Settings >  Cookies . There are two settings , Manage Exceptions and  All Cookies and Site Data.

> Would you know this basic wget operation? I have used wget and from the command line and don't really understand the question.

---

### Post by Pletched on 2012-12-08
This is how to load cookies with wget; The = is important.

```
wget --load-cookies=file.cookie [URL]
```

---

