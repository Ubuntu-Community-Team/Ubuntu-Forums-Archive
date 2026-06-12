---
title: "How to use /etc/hosts properly?"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-10
HI,

For development purposes, whenever I type in mySite.com in the browser, I would like to be redirected to 127.0.0.1.

I did a 

```
sudo vim /etc/hosts
```

and added the website next to localhost, but it doesnt work


```
127.0.0.1       localhost MySite.com
```

What am I missing?  
Thanks

---

### Post by CharlesA on 2012-06-10
That looks right.

When I doubt, add it as a new line.

---

### Post by Houmie on 2012-06-10
> **CharlesA said:**
> That looks right.

When I doubt, add it as a new line.

Ah I know whats happening, I also need to specify the port. I tried this without luck:


```
127.0.0.1:8000  MySite.com
```

---

### Post by roelforg on 2012-06-10
> **Houmie said:**
> Ah I know whats happening, I also need to specify the port. I tried this without luck:


```
127.0.0.1:8000  MySite.com
```

/etc/hosts only does name resolv, no ports.
You may want to look into namebased virtual hosts.

---

### Post by CharlesA on 2012-06-10
> **roelforg said:**
> /etc/hosts only does name resolv, no ports.
You may want to look into namebased virtual hosts.
Yep, that would do it.

---

### Post by Houmie on 2012-06-10
I see. :) Any pointers to where I setup named-Virtual hosts? I know how to do it under Apache 

```
sudo vim /etc/apache2/sites-available/siteB
```

but how to do it in the local box?

---

### Post by flemur13013 on 2012-06-10
> 127.0.0.1:8000  MySite.com

This is the format:

127.0.0.1    MySite.com
127.0.0.1    ads.MySite.com

You can't use wild-cards; the 1st line does NOT block "ads.MySite.com", but the 2nd line does. (Replace "ads" with anything other than "www").

---

### Post by CharlesA on 2012-06-10
> **Houmie said:**
> I see. :) Any pointers to where I setup named-Virtual hosts? I know how to do it under Apache 

```
sudo vim /etc/apache2/sites-available/siteB
```

but how to do it in the local box?
You would need apache set up on the local box and set the virtualhost up.

See here:
[http://ubuntuforums.org/showthread.php?t=1977192](http://ubuntuforums.org/showthread.php?t=1977192)

---

### Post by David Andersson on 2012-06-10
> **Houmie said:**
> 
```
127.0.0.1       localhost MySite.com
```


I haven't seen upper case in /etc/hosts before, and google subtly suggests it should be lower case. Try mysite.com (if should match MySite.com and even mysIte.coM)

---

### Post by CharlesA on 2012-06-10
Case shouldn't matter, but I use all lowercase if I have to add entries to /etc/hosts.

---

