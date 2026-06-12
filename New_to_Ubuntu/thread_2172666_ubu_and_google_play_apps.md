---
title: "ubu and google play apps"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by jon12 on 2013-09-05
I just downloaded a free app from google play. It said it was compatible with my system. which is Xubuntu with xfce.
is this ok and where is the app so I can use it??its not on the desktop...

---

### Post by cariboo on 2013-09-06
Run the following commands in a terminal:

```
sudo updatedb
```

once the database has finished updating type:

```
locate <app_name>
```

where <app_name> = the name of the app you downloaded.

---

### Post by 3rdalbum on 2013-09-06
The programs on Google Play are for Android, not for Ubuntu. When it says that the program is available for your device, it is talking about the phone or tablet you have used with that Google Play account.

The program hasn't downloaded either, it is now merely associated with your Google Play account, and your phone or tablet will download it along with its usual updates.

---

### Post by tgalati4 on 2013-09-06
Go look on your phone.

---

### Post by philinux on 2013-09-06
> **tgalati4 said:**
> Go look on your phone.

I assume the OP means he used ubuntu and a web browser to download an app from the internet play store. Maybe:confused:

---

