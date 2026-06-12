---
title: "Programming Webservices"
date: 2006-01-04
forum: Programming Talk
---

### Post by harisund on 2006-01-04
Hello

I was just looking into the del.icio.us api ([http://del.icio.us/help/api/](http://del.icio.us/help/api/)) and found that it required a HTTP-Auth for access for adding/deleting tags and so on. 

How do I do that? Could someone point out a tutorial or something like that? I couldn't find it on wikipedia either. 

I generally use PHP for other REST based stuff like the Yahoo/Google maps etc. 

Thanks !

---

### Post by Burke on 2006-01-05
This may be something completely different, but I know that when websites requre HTTP authentication, a dialog pops up that promts you for the usename and password. This can be avoided if you go to [http://user:pass@site.com](http://user:pass@site.com) . Maybe this is of help? I haven't really looked at the API, so I'm not sure.

EDIT:  oops. heh.  That should have been "user : [email]pass@site.com[/email]", only without the spaces.

---

### Post by harisund on 2006-01-05
yes indeed. thanks for that.

Actually, I got what i was looking for. php's libcurl is what is needed to query remote servers 

Almost all languages these days come with some sort of a library that allows XML RPC. libcurl for php allows that, and it has perl bindings as well. 

thanks !

---

