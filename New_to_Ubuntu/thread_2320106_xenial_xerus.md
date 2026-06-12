---
title: "xenial xerus"
date: 2016-04-10
forum: New to Ubuntu
---

### Post by ewuntu on 2016-04-10
Howdy.
Not sure if this is the place to be but:
Downloaded **[Ubuntu 16.04 (Xenial Xerus) Beta 2]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&uact=8&ved=0ahUKEwj0-uXJ2oTMAhWLGB4KHSWEAMQQFggqMAI&url=http%3A%2F%2Freleases.ubuntu.com%2F16.04%2F&usg=AFQjCNF3WF6rNeD5fJmmlCLoBSe9MYgBzQ")**

the file has no autostart or wubi.

How to proceed?

---

### Post by howefield on 2016-04-10
Follow the links on this page [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) as to burning the image to a a DVD or USB stick and then boot from it.

Wubi is no longer included on the image.

---

### Post by ewuntu on 2016-04-10
A thousand thanks. Still in the dark ages here.

---

### Post by howefield on 2016-04-11
A thousand welcomes.

Keep updating and you will end up on the finished release.

If you want to turn that image into the finished release, use zsync which will take that which you have already downloaded keeping the unchanged bits and only downloading the difference between it and the finished release on the 21st April. Saves downloading the whole thing again. From a terminal navigate to where the image is stored..

```
sudo apt install zsync
```
```
zsync [http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync)
```

---

### Post by ewuntu on 2016-04-12
Thanks again.
Will try the new donwload site.

---

