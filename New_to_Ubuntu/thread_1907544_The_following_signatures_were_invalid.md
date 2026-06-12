---
title: "The following signatures were invalid"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by pierreyy on 2012-01-11
hey guys ive been getting a funny looking triangle in the top bar so i ran 
```
 apt-get update
```

i got two issues one was solved (thank you google) and the other is this

```
 W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures were invalid: KEYEXPIRED 1326292011 KEYEXPIRED 1326292011 KEYEXPIRED 1326292011 
```


what exactly is this and how do i solve it? thanks in advance!

---

### Post by rockachu2 on 2012-01-11
Looks like opera's signatures became invalid. 

This could be an old config issue where the key was changed, or it could be opera's fault.

If you added this into the list file directly, then that is probably the issue and you need to update the key you used or reinstall the opera dev repository using apt-add-repository (which I think auto-updates the keys).

If you didn't, chances are it's opera's problem. They can fix it. 

There is also a slight chance that the key is being served by ubuntu, and they need to update it, but talking to someone who knows more than me about this would probably be more helpful.

---

### Post by rockachu2 on 2012-01-11
Just looked at the link to the repository over http and it looks like they have two keys: one for 2011 and one for 2012. If you're using the 2011 key that would probably cause issues. 

Did this begin happening right when it became 2012?

---

### Post by pierreyy on 2012-01-11
> **rockachu2 said:**
> Just looked at the link to the repository over http and it looks like they have two keys: one for 2011 and one for 2012. If you're using the 2011 key that would probably cause issues. 

Did this begin happening right when it became 2012?



yes it did,   i will add opera to the repos. thank you so much!

---

