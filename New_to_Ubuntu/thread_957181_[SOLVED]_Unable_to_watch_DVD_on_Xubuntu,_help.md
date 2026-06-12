---
title: "[SOLVED] Unable to watch DVD on Xubuntu, help"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by GumpTron on 2008-10-24
Hello,

I have installed Xubuntu on my old notebook. After installing it fresh I am unable to play a dvd. The movie is "death note", and is fairly new. Totem doesnt seem to be able to play it. Can anyone recommend appropriate software that is easy to install? Thank you.

---

### Post by fr.theo on 2008-10-24
make sure you install all codecs from your >Application >add/remove do a search for gstreemer this will allow you to listen to MP3.


for dvd's codecs run this in terminal sudo apt-get install libdvdcss2


give that a go and good luck.

---

### Post by GumpTron on 2008-10-24
> **fr.theo said:**
> make sure you install all codecs from your >Application >add/remove do a search for gstreemer this will allow you to listen to MP3.


for dvd's codecs run this in terminal sudo apt-get install libdvdcss2


give that a go and good luck.

thanks. but it says I already have the newest version.

---

### Post by fr.theo on 2008-10-24
ok, try this site: [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)


just follow the instructions see if that will work, it also took me a while to get mine working.

good luck.

---

### Post by hyper_ch on 2008-10-24
did you also run
```

sudo apt-get install ubuntu-restricted-extra

```?

---

### Post by GumpTron on 2008-10-24
'Kaffeine' works great and my dvd's are playing! I found it in the add/remove programs.

---

