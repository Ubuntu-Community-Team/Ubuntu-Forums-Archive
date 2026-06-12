---
title: "[SOLVED] Bluefish - External Browser"
date: 2009-01-09
forum: Programming Talk
---

### Post by ricardo_78 on 2009-01-09
I have installed Bluefish and it looks pretty good.

I am tryingto set up external browser support to view php files root /opt/lampp/htdocs/

 
The following:
```

firefox -new-window http://localhost/%s&

```
gives me a newwindow with http:/localhost/opt/lampp/htdocs/myfile.php where the file I wantto view is myfile.php.

Almost there but I need to remove /opt/lampp/htdocs/.  I understand 
```

sed s /opt/lampp/htdocs/

```
is part of the answer but I am not sure how to apply it...

Can anyone throw me a bone on this one?

---

### Post by Peter76 on 2009-01-09
I guess what you want is to actually see how myfile.php is rendered in your browser. This is not possible the way you are trying now; you need a server to process the php and feed it to your browser. So you either have to install a LAMP stack or upload the file to a webserver.

Good luck

---

### Post by ricardo_78 on 2009-01-09
I have got a lamp stack installed and php working in directory

/opt/lampp/htdocs/

---

### Post by Peter76 on 2009-01-09
If you installed your LAMP stack from the Ubuntu repositories ( which you should ), you should put your files in /var/www . When you point your browser to localhost then, your page should turn up

---

### Post by johnl on 2009-01-09
```

firefox -new-window `echo "http://localhost/%s" | sed s/"opt\/lampp\/htdocs\/"/""/`

```

I think this might do what you are asking.  Depending on whether or not bluefish supports backticks in this context.

---

### Post by ricardo_78 on 2009-01-09
Peter 76: Agree that would be neater way of organising things.

Johnl: Brilliant works with only proviso not opening a new window in foreground.....many thanks

---

