---
title: "Hotmail does not dettect latest version of Firefox"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by theamber on 2008-11-05
Hi, i have ubuntu hardy and when I go to hotmail it tells me to upgrade my browser but I have version 3 of Firefox, now I can't reply to my messages.
Any ideas will be appreciated, thanks.

---

### Post by gandaran on 2008-11-05
just click okay or continue until you log in, after you log in the first time it won't trouble you no more

---

### Post by lemmy999 on 2008-11-05
I think your issue is the one mentioned in this thread - ([http://ubuntuforums.org/showthread.php?t=963252&highlight=hotmail](http://ubuntuforums.org/showthread.php?t=963252&highlight=hotmail))

Read and digest!!:p

And if I'm wrong please feel free to slap me!!

---

### Post by Bölvaður on 2008-11-05
We have noticed that bug for a long time.

When you log in just click "If you don't want to upgrade right now you can still _continue to Windows Live Hotmail_,"

When you click that link you will have no troubles until you sign in again and have to push continue :)

---

### Post by theamber on 2008-11-05
Thanks I did continue and it worked at first but now I can't reply to my mail and the window it looks from an old version.

---

### Post by Yashiro on 2008-11-05
In the firefox address bar, enter in:
```
about:config
```

Search for **general.useragent.vendor**
and change it's value from Ubuntu to **Firefox**.

Close the browser. Now navigate to Hotmail, it will work.

---

