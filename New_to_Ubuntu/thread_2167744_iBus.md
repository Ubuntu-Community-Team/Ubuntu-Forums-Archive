---
title: "iBus"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-08-14
I use iBus for switching text input to other languages. But recently i have notices i am not able to enter non latin text in Skype. Though i can type those text in leafpad and then copy paste it in skype. This problem also occurs with some websites but Skype is the main problem area for me.

---

### Post by Irihapeti on 2013-08-15
I believe that skype uses QT. Do you have ibus-qt4 installed? If not, install that and see if it helps.

---

### Post by 3dmatrix on 2013-08-16
> **Irihapeti said:**
> I believe that skype uses QT. Do you have ibus-qt4 installed? If not, install that and see if it helps.

Sorry it did not help. In fact i noticed it was also not able to type in other language in Synaptic search bar.

---

### Post by Irihapeti on 2013-08-16
Open a terminal (ctrl-alt-t) and enter the command:
```
im-switch
```

That should open a window showing a number of choices for the input method.

Does it show the correct language/locale setting at the top of that window? If not, you may need to change that first.

Is "use IBus" selected? If not, select it and click OK.

You'll need to logout and in again (or reboot) before you can check if it's made any difference.

If this doesn't work, I'm out of ideas, unfortunately. Maybe someone else can help.

---

### Post by 3dmatrix on 2013-08-16
> **Irihapeti said:**
> Open a terminal (ctrl-alt-t) and enter the command:
```
im-switch
```

That should open a window showing a number of choices for the input method.

Does it show the correct language/locale setting at the top of that window? If not, you may need to change that first.

Is "use IBus" selected? If not, select it and click OK.

You'll need to logout and in again (or reboot) before you can check if it's made any difference.

If this doesn't work, I'm out of ideas, unfortunately. Maybe someone else can help.


This does not seems to be a solution as i can type in most of other applications. Just a few of them are not able to do so.

---

### Post by Irihapeti on 2013-08-17
It looks as though other people have been having problems with IBus and skype: [https://code.google.com/p/ibus/issues/detail?id=613](https://code.google.com/p/ibus/issues/detail?id=613)

It deals with an older version of Ubuntu but may still be helpful.

[http://askubuntu.com/questions/247339/ibus-anthy-not-working-with-skype-4-1-0-20](http://askubuntu.com/questions/247339/ibus-anthy-not-working-with-skype-4-1-0-20) may also be helpful.

---

### Post by 3dmatrix on 2013-08-17
As i see now, using i-bus i can not input non english text even in the synaptic search bar. Well i know you might ask me, why would anyone do that but technically, just like skype, it is not possible both in 12.04 and 13.04.

---

### Post by 3dmatrix on 2013-08-20
I have also noticed, i am not able to type in non-english characters in the text box of many websites.

---

