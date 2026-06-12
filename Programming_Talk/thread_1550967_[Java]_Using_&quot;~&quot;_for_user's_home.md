---
title: "[Java] Using &quot;~&quot; for user's home"
date: 2010-08-11
forum: Programming Talk
---

### Post by KdotJ on 2010-08-11
Hey everyone, 
How can I refer to the user's home folder in java? 
For example, the following:

```
File f = new File("~/Documents/test.txt");
```

Will compile fine but when run, it doesn't work and throws a FileNotFoundException. It does however work if I replace the "~" with "/home/username" but obviously I can't hard code the username into the source.

Thanks in advance

---

### Post by interval1066 on 2010-08-11
> **KdotJ said:**
> Hey everyone, 
How can I refer to the user's home folder in java? 
For example, the following:

```
File f = new File("~/Documents/test.txt");
```

Will compile fine but when run, it doesn't work and throws a FileNotFoundException. It does however work if I replace the "~" with "/home/username" but obviously I can't hard code the username into the source.

Thanks in advance

Of course you're have problems, the twiddle character means different things based on the context; and has no place in a C program except as a char literal maybe... you want to use the C runtime apis to read shell variable maybe or; if you're doing what I do, which is a lot of gnome programming gtk+ has its own api for getting different directory paths.

For what you're doing I think you want to look to see if $HOME is populated via clib's getenv on linux. Could be different things on other unix-ish libraries.

---

### Post by KdotJ on 2010-08-11
Thank for the reply, I assumed that Java was just reading it as a literal but thought I'd try anyway. I'll have to have a look for variables tat hold that value, the libs you speak of are for C, but I will research. Thanks

---

### Post by issih on 2010-08-11
Not guaranteeing this will work but give this a try:

```
System.getProperty("user.home");
```

Have a look here for some more info:

[http://download.oracle.com/javase/1.5.0/docs/api/java/lang/System.html#getProperty%28java.lang.String,%20java.lang.String%29](http://download.oracle.com/javase/1.5.0/docs/api/java/lang/System.html#getProperty%28java.lang.String,%20java.lang.String%29)

Hope that helps

Issih

---

### Post by interval1066 on 2010-08-11
> **KdotJ said:**
> Thank for the reply, I assumed that Java was just reading it as a literal but thought I'd try anyway. I'll have to have a look for variables tat hold that value, the libs you speak of are for C, but I will research. Thanks

Woops, didn't realize you were doing java. Do what issih suggests, it'll be a virtual machine property.

---

### Post by KdotJ on 2010-08-11
> **issih said:**
> Not guaranteeing this will work but give this a try:

```
System.getProperty("user.home");
```

Have a look here for some more info:

[http://download.oracle.com/javase/1.5.0/docs/api/java/lang/System.html#getProperty%28java.lang.String,%20java.lang.String%29](http://download.oracle.com/javase/1.5.0/docs/api/java/lang/System.html#getProperty%28java.lang.String,%20java.lang.String%29)

Hope that helps

Issih

That's the one!
Thanks both of you for your help, I love this place

---

