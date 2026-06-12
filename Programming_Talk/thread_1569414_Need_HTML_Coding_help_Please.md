---
title: "Need HTML Coding help Please?"
date: 2010-09-06
forum: Programming Talk
---

### Post by ericdumond on 2010-09-06
Hello guys,
 
I apologize if I am posting this in the wrong area. If this is not the correct place please let me know. Here is my question. I curently have a WinXP machine that has a ton of movies on it and I am building a little web site so I dont have to use SAMBA or map a shared drive. I have tried coding the HTML like this:

<a href="[file:////<name of pc here>/Movies/Movies/Action/](file:////<name of pc here>/Movies/Movies/Action/)movie.avi>. The problem is this works fine from a windows machine but using my Ubuntu workstation it does not work at all. It shows the hyperlink as [http://ipaddress/\movie\movie\action\movie.avi](http://ipaddress/\movie\movie\action\movie.avi). I have tried several searches but have not had any luck coding this corectly. Would someone mind telling me what I am doing wrong here? 
 
Thanks for looking,

---

### Post by Joeb454 on 2010-09-06
Without delving into it too much - is the movie file located in a publicly accessible directory? I'd check that first.

---

### Post by alan8 on 2010-09-06
Hi,

You can't use 
```

<a href="[file:////]("file:////%3Cname%20of%20pc%20here%3E/Movies/Movies/Action/")....

```syntax, as it will work correctly on your WinXP box only.

What you will have to do is:

1. Move all your movies you want to access on your Ubuntu box to directory accessible by your web server on WinXP machine. For example:
```

c:\wwwroot
    |_ HtmlFiles
         |_ index.html
         |_ media
              |_Movie1.avi
              |_Movie2.avi

```2. Use the following syntax for your links:
```

<a href="media/Movie1.avi">Movie1.avi</a>
<a href="media/Movie2.avi">Movie2.avi</a>

```Good luck!

---

### Post by ericdumond on 2010-09-06
> **alan8 said:**
> Hi,

You can't use 
```

<a href="[file:////]("file:////%3Cname%20of%20pc%20here%3E/Movies/Movies/Action/")....

```syntax, as it will work correctly on your WinXP box only.

What you will have to do is:

1. Move all your movies you want to access on your Ubuntu box to directory accessible by your web server on WinXP machine. For example:
```

c:\wwwroot
    |_ HtmlFiles
         |_ index.html
         |_ media
              |_Movie1.avi
              |_Movie2.avi

```2. Use the following syntax for your links:
```

<a href="media/Movie1.avi">Movie1.avi</a>
<a href="media/Movie2.avi">Movie2.avi</a>

```Good luck!


Thanks for the guidance I appreciate the help.. I'll try this approach.

---

### Post by ericdumond on 2010-09-06
Update,

I used the mod alias directive and all is good in the world.

Thanks Guys!!!

---

