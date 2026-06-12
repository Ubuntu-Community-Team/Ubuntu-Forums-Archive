---
title: "Google brings up UK site"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by AgDon92 on 2008-05-25
Hello,
I am very new to Ubuntu, and have a quick (hopefully) question.  When I go to Google for a search, it seems to send me to the UK search site.  I also went to HP for some printer drivers and it also mentioned "UK English". Where do I change this? I am from the States.

Thanks.

Don

---

### Post by drs305 on 2008-05-25
First, you can type this in terminal to see what you have:
```
locale
```

I am using US english, so I get:
```
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE=C
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

If your's doesn't look like this and you want to change to US english: go to System, Administration, Language Support. You will probably have to download the US english locale libraries, and select us english as your preferred language. You may have to reboot before the changes take effect.

---

### Post by Joeb454 on 2008-05-25
Go to Google.com and then make sure you are on classic home.

Then under the search bar there is an option to make it send you to the US site every time :) It relys on a cookie I think :)

---

