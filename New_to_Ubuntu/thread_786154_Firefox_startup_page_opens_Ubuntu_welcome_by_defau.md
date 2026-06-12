---
title: "Firefox startup page opens Ubuntu welcome by default"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by zhanglini on 2008-05-07
Hey all,
My Firefox startup page opens Ubuntu welcome page by default.  Even though I have set my yahoo page as my home page, Firefox still opens both.  I don't really want to see Ubuntu page forever.
How do I get rid of it?
Thanks

---

### Post by daimaru on 2008-05-07
you should be able to solve that by firefox menu edit->preferences general tab. if you want 2 or 3 or so on pages to open just delimit them by the pipe symbol " | "  eg:
[www.google.de|www.yahoo.com|www.ubuntu.com](www.google.de|www.yahoo.com|www.ubuntu.com). My guess is that yours says something like [www.yahoo.com|file://somepath/to/ubuntu/start/page](www.yahoo.com|file://somepath/to/ubuntu/start/page)

---

### Post by zhanglini on 2008-05-07
That is the opposite of what I want.
Currently in my home page setting I have my.yahoo.com, but when I open Firefox, it loads both yahoo AND Ubuntu welcome page.   
I want to get rid of the Ubuntu page and don't know how.
Thanks

---

### Post by ablinkin on 2008-05-07
change [http://my.yahoo.com|file://somepath...ntu/start/page](http://my.yahoo.com|file://somepath...ntu/start/page)
to
[http://my.yahoo.com](http://my.yahoo.com) in your firefox preferences

---

### Post by daimaru on 2008-05-07
> **ablinkin said:**
> change [http://my.yahoo.com|file://somepath...ntu/start/page]("http://my.yahoo.com%7Cfile://somepath...ntu/start/page")
to
[http://my.yahoo.com](http://my.yahoo.com) in your firefox preferences
thought so too, but i guess he has only [www.yahoo.com](www.yahoo.com) in there and somehow it still opens two tabs. which is kinda weird and sorry zhanglini but I never encountered this problem. maybe if it persists you should try a remove --purge and reinstall of firefox.

---

### Post by zhanglini on 2008-05-08
Yeah, I will reinstall Firefox when the official 3 is out.
Thanks

---

### Post by zhanglini on 2008-05-09
Ok, I reinstalled Firefox, and got rid of the Ubuntu Welcome page.
Now this Firefox Welcome page is bugging me, and starts everytime, along with my yahoo page.
I feel welcomed everywhere!!!

---

### Post by Tex786 on 2008-05-09
> **zhanglini said:**
> That is the opposite of what I want.
Currently in my home page setting I have my.yahoo.com, but when I open Firefox, it loads both yahoo AND Ubuntu welcome page.   
I want to get rid of the Ubuntu page and don't know how.
Thanks

This is really simple! I'll show you how to do this.

you know how next to an address in the URL box there is a logo to the left of the address? all you have to do is click and hold it while dragging it to the home icon within firefox. 

I went into the settings too when i started to use firefox but it did not work. This drag and drop worked fine. Let me know if this helps~

have a good weekend.

---

### Post by Tex786 on 2008-05-09
> **zhanglini said:**
> Ok, I reinstalled Firefox, and got rid of the Ubuntu Welcome page.
Now this Firefox Welcome page is bugging me, and starts everytime, along with my yahoo page.
I feel welcomed everywhere!!!

Go into your settings and type in the website you want to come up, after that drag and drop the icon fromthe address bar to the home icon.

You have to do two things but it has worked for me.

---

### Post by zhanglini on 2008-05-09
> **Tex786 said:**
> Go into your settings and type in the website you want to come up, after that drag and drop the icon fromthe address bar to the home icon.

You have to do two things but it has worked for me.
Works like a charm thanks Tex786.

---

