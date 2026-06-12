---
title: "Google Desktop on Ubuntu?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by maxinquaye on 2008-08-22
Hello all,

I would like to know if google desktop is supported under Ubuntu. Thanks for your help!

---

### Post by y-lee on 2008-08-22
I don't use it but it appears yes there is a linux version, [http://desktop.google.com/linux/index.html]("http://desktop.google.com/linux/index.html")

---

### Post by kpkeerthi on 2008-08-22
[http://code.google.com/p/google-gadgets-for-linux/](http://code.google.com/p/google-gadgets-for-linux/)

---

### Post by Oldsoldier2003 on 2008-08-22
you can also add the google repos to your sources list.

```

deb http://dl.google.com/linux/deb/ stable non-free

```

If you are a little braver google also has a testing repo
```
deb http://dl.google.com/linux/deb/ testing non-free
```

---

### Post by maxinquaye on 2008-08-22
Thank you. Indeed I'd rather not install it if I knew there is an equivalent native indexing/tracking/searching system on Ubuntu. What do you use for that purpose?

---

### Post by qamelian on 2008-08-22
> **maxinquaye said:**
> Thank you. Indeed I'd rather not install it if I knew there is an equivalent native indexing/tracking/searching system on Ubuntu. What do you use for that purpose?
Tracker fits the bill and is installed by default. Other alternatives, such as Strigi and Beagle are also in the Ubuntu repos.

---

### Post by Oldsoldier2003 on 2008-08-22
I have just installed Google desktop for searching, I used to use Beagle, then Tracker but found that they were not good enough for me. Tracker turned out to be a bit of a hog and fairly unreliable (IMHO). It is getting better but at this point I'll evaluate Google desktop as my personal solution. Later I'll switch back to tracker and see if it is getting better but for now its just not good enough.

---

### Post by puthut on 2009-03-29
Dont forget to do this first

```

wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
apt-get update

```

ref. [http://www.google.com/linuxrepositories/apt.html]("http://www.google.com/linuxrepositories/apt.html")

---

### Post by hyper_ch on 2009-03-29
have a look my sig for more repos (incl. google one).

Although I have to say I don't want google to search my stuff :)

---

### Post by mkvnmtr on 2009-03-29
hyper_ch I have to agree. I don't mind using Google but I don't want them using me.

---

