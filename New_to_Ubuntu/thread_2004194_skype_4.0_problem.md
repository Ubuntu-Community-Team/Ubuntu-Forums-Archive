---
title: "skype 4.0 problem"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by werty2010 on 2012-06-15
i downloaded and installed the official release of skype 4.0 from the official site after i removed the older version with these commands(because i had an error poping out every time i tried to install the new one):
```

sudo apt-get remove skype
sudo apt-get remove skype-bin
sudo apt-get autoremove

```

so far im not sure if texting/calling really works but im facing another problem:
it launches/runs ok but it doesnt show up in the unity panel, although it is running.
so every time i want to see a contact or quit skype i have to "relaunch" it

any ideas for a solution?

---

### Post by Azdour on 2012-06-15
Hi,

I have not used it myself but there is a skype-wrapper to help integration in Unity:

[http://www.makeuseof.com/tag/skype-wrapper-better-integrate-skype-with-the-ubuntu-desktop/](http://www.makeuseof.com/tag/skype-wrapper-better-integrate-skype-with-the-ubuntu-desktop/)

or:

[http://www.omgubuntu.co.uk/tag/skype-wrapper](http://www.omgubuntu.co.uk/tag/skype-wrapper)

---

### Post by werty2010 on 2012-06-15
it worked but id like to know also how to make the "default" way  work

---

### Post by Paddy Landau on 2012-06-19
When you remove the old Skype, you need to purge instead of remove. Use the following command:
```
 sudo apt-get purge skype skype-bin skype-common skype-bin:i386
```The autoremove command will make no difference to the running of Skype.

EDIT: Also, you need to reboot after installing the new Skype. I know that's a bit unusual for Linux, but Skype is a bit different.

---

