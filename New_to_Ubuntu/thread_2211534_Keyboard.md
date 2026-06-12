---
title: "Keyboard"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by Korkel on 2014-03-16
Hi,

I'm using Ubuntu but got a small problem with my keyboard.

When I enter a ' and then a t, the ' is not appearing. But when I use ' and then the m I get this: &#7743;. How must I setup my keyboard settings?

Thank you.

---

### Post by Vladlenin5000 on 2014-03-16
You probably selected a keyboard variant with "dead keys", a variant used for enabling the accentuated characters needed for many languages (English only needs a few for some borrowed words like the French "fiancé").
With such layout variant you need to type ' or " + space.
You can change the keyboard layout for the normal one if you feel you don't need special characters. How to do it graphically depends on the version and falvor of Ubuntu you're running. Please provide such info next time.

---

### Post by Korkel on 2014-03-16
> **Vladlenin5000 said:**
> You probably selected a keyboard variant with "dead keys", a variant used for enabling the accentuated characters needed for many languages (English only needs a few for some borrowed words like the French "fiancé").
With such layout variant you need to type ' or " + space.
You can change the keyboard layout for the normal one if you feel you don't need special characters. How to do it graphically depends on the version and falvor of Ubuntu you're running. Please provide such info next time.
Using Ubuntu 13.10. I use the special characters like ´ most of the time.

---

### Post by Vladlenin5000 on 2014-03-16
That isn't a "special character". Examples of special characters: ç á à â é È ü ...
In standard Ubuntu you can go to system setting > Keyboard. There you'll find a button that takes you to the keyboard layouts. You can add or remove layouts. As a rule you should only have the ones pertaining to the keyboards you use with that computer therefore, if you only use "US International" keyboards and you don't want that behavior, make sure that only US international is listed.


PS - Please reply to your other thread or otherwise mark it as solved if you no longer need help.

---

### Post by Korkel on 2014-03-16
But then ' show automatic... :s

---

### Post by Vladlenin5000 on 2014-03-16
> **Korkel said:**
> But then ' show automatic... :s

Sure... Isn't that what you want? And no, you can't have it both way. Either normal or with "dead keys".

---

### Post by bapoumba on 2014-03-16
Where do you get these ? In an application ? Terminal ? Please have a look at your keyboard layout or at the accessibility menus where you may have checked something by accident. What keyboard and language are you using ?
Edit : what is the output to** locale**. Here is mine for ref :
```
 locale
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=fr_FR.UTF-8
LC_TIME=fr_FR.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=fr_FR.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=fr_FR.UTF-8
LC_NAME=fr_FR.UTF-8
LC_ADDRESS=fr_FR.UTF-8
LC_TELEPHONE=fr_FR.UTF-8
LC_MEASUREMENT=fr_FR.UTF-8
LC_IDENTIFICATION=fr_FR.UTF-8
LC_ALL=

```

---

### Post by Korkel on 2014-03-16
> **bapoumba said:**
> Where do you get these ? In an application ? Terminal ? Please have a look at your keyboard layout or at the accessibility menus where you may have checked something by accident. What keyboard and language are you using ?
English, US with dead keys...

---

### Post by Vladlenin5000 on 2014-03-16
> **Korkel said:**
> English, US with dead keys...

As I said before, it's working as designed. That's exactly the expected behavior with the "dead keys" option. If you don't want it just change back to normal. You won't be able to write accentuated characters though but - again - you can't have it both ways.

---

### Post by Korkel on 2014-03-16
Hmm, I will deal with it. :'(

---

### Post by bapoumba on 2014-03-16
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

---

### Post by Korkel on 2014-03-16
Thanks, I think. :)

---

### Post by bapoumba on 2014-03-16
Please try and see if it fits your needs :)

---

### Post by Korkel on 2014-03-16
Ok. ;)

---

