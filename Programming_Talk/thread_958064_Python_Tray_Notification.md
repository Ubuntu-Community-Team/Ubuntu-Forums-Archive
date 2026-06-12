---
title: "Python Tray Notification"
date: 2008-10-25
forum: Programming Talk
---

### Post by abeisgreat on 2008-10-25
I already have it setup so my python + pygtk app shows up in the notify area, but now I want it to pop up a message like this one

[IMG]http://www.ubuntu.com/files/u3/update-notification.png[/IMG]

except you know with my custom message.

Thanks Abe

---

### Post by imdano on 2008-10-25
You want notify-python (the Ubuntu package name is python-notify), which are python bindings for libnotify.  The project page is here: [http://www.galago-project.org/news/index.php](http://www.galago-project.org/news/index.php)

---

### Post by abeisgreat on 2008-10-25
> **imdano said:**
> You want notify-python (the Ubuntu package name is python-notify), which are python bindings for libnotify.  The project page is here: [http://www.galago-project.org/news/index.php](http://www.galago-project.org/news/index.php)

I knew that! I have seen that package around. But was never sure if that was really what I needed. Thanks anyway. 

do you know of any good tuts or examples for these packages?

Edit: I've got it up and working fine, still some good refererences would be nice

---

### Post by imdano on 2008-10-25
There isn't much documentation online that I know of (or at least there wasn't when I last checked), but there should be a bunch of examples in /usr/share/doc/python-notify/examples.

---

### Post by abeisgreat on 2008-10-25
> **imdano said:**
> There isn't much documentation online that I know of (or at least there wasn't when I last checked), but there should be a bunch of examples in /usr/share/doc/python-notify/examples.


Awesome thanks

---

### Post by loell on 2008-10-25
and one more thing, you'll gonna have to install the module before browsing the samples

[python-notify]("apt:python-notify")

---

### Post by abeisgreat on 2008-10-25
> **loell said:**
> and one more thing, you'll gonna have to install the module before browsing the samples

[python-notify]("apt:python-notify")


its included in hardy heron ;)

---

### Post by loell on 2008-10-25
> **abeisgreat said:**
> its included in hardy heron ;)

awwwts.. didn't notice that. :)

---

### Post by abeisgreat on 2008-10-25
> **abeisgreat said:**
> its included in hardy heron ;)

Ok question number 2, I need to grab an image off the web to use as the icon in the py notify, I have no issue grabbing the url of the image, but I need to know, is it possible to use the image right off the server? or do I have to store it locally then use it?

---

### Post by loell on 2008-10-25
** /usr/share/doc/python-notify/examples/test-image.py**

is the perfect example.

---

### Post by abeisgreat on 2008-10-25
> **loell said:**
> ** /usr/share/doc/python-notify/examples/test-image.py**

is the perfect example.

I can load it from a local file just fine but Id like to load it from an http:// address.

---

