---
title: "How can I undo updates in Lubuntu"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by wim12 on 2013-06-16
yesterdag I installed an automatic update, including an update of flashplayer.
This morning I discovered that Flash plugin crashes 'all the time'.
I therefor would like to undo the update regarding flashplayer.

How can I do that?

---

### Post by NikTh on 2013-06-16
You can ls (list) all the previous versions inside apt cache. (if any)

```
ls /var/cache/apt/archives | grep -i flash
```

if you see the older version of flash player there .. you can connect to that directory and install it.. FIRST remove the current version. 

```
cd /var/cache/apt/archives/ 
sudo apt-get purge adobe-* 
sudo dpkg -i adobe-flashplugin_........deb
``` 

If things goes good and flash plugin not crash anymore, then you can hold the package from being updated in future. 

```
echo "adobe-flashplugin" hold | sudo dpkg --set-selections
``` 

Thanks

---

### Post by wim12 on 2013-06-16
Thanks NikTh, 
it works again and now I hold the package from being updated. Hope also this works.

---

### Post by NikTh on 2013-06-16
Please mark the thread as solved (see my signature on how to) 

Thanks

---

### Post by wim12 on 2013-06-16
hi NikTh,
I tried that before, but when i open Thread tools there is no option 'mark this thread as solved', as in your signature.
It only shows: [h=6][View First Unread]("http://ubuntuforums.org/showthread.php?t=2154852#post12693603")[/h]
[h=6]Thread Tools[/h]
[LIST]
[*][Show Printable Version]("http://ubuntuforums.org/printthread.php?t=2154852&pp=10&page=1")
[*][Email this Page&#8230;]("http://ubuntuforums.org/sendmessage.php?do=sendtofriend&t=2154852")
[*][Unsubscribe from this Thread]("http://ubuntuforums.org/subscription.php?do=removesubscription&t=2154852")
[/LIST]

---

