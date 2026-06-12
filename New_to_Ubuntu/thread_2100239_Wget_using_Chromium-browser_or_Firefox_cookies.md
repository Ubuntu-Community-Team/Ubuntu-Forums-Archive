---
title: "Wget using Chromium-browser or Firefox cookies?"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by honeybear on 2013-01-01
Hi,

I have an account on a website, that I have a Login/Password, and I would like regularly using crontab do some wget.

Would you know if it is possible to use the configuration (i.e. cookies of either firefox or chromium) for this?

thanks

Happy New Year!

---

### Post by Cheesemill on 2013-01-01
Yes it is, have a look at 'man wget' and look at the --user --password and --load-cookies options.

[http://manpages.ubuntu.com/manpages/precise/man1/wget.1.html](http://manpages.ubuntu.com/manpages/precise/man1/wget.1.html)

---

