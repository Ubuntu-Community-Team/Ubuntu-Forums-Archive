---
title: "Software  Center"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by amberfrog on 2012-02-27
Hi 
I just updated software on Ubuntu 11.10 running on AMD Opteron 64 Bit, and now I get the error
 
E: Line 2 too long in source list /etc/apt/sources.list.
E: The list of sources could not be read.

I found a similar problem and tried the commands sudo rm/var/lib/apt/list/* which seemed to work for someone with the same prob, but I can't replicate that solution

Many thanks

---

### Post by mörgæs on 2012-02-27
Hi, welcome to the fora.

So, how does line 2 in your sources.list look?

---

### Post by amberfrog on 2012-02-27
Thank you for the reply. I do not know even how to FIND my sources list, being handicapped by many years of Windows

---

### Post by nothingspecial on 2012-02-27
Press Alt-F2

Type ```
gedit /etc/apt/sources.list
```

Copy and paste the contents of the file in a new post here.

Put the pasted content in code tags. To do this click the # in the formatting options at the top of the posting box and paste in between.

---

### Post by amberfrog on 2012-02-27
Hi
I get :There was a problem opening the file /etc/apt/sources.list. then lots of 00/00/00
then deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner #Added by software-center 

Tried a different encoding but same result

Opening sources list from command line also tells me that I do not have permission

Best

Pete

---

### Post by cortman on 2012-02-27
nothingspecial forgot

```
gksu gedit /etc/apt/sources.list
```

gksu runs the following command with root permissions.

---

### Post by nothingspecial on 2012-02-27
You don't need (gk)sudo to view the file. Only to change it.

---

### Post by forrestcupp on 2012-02-27
> **cortman said:**
> nothingspecial forgot

```
gksu gedit /etc/apt/sources.list
```

gksu runs the following command with root permissions.

Still doesn't make sense, though. Usually you can open a file without gksu and have read-only permission.

---

### Post by audiomick on 2012-02-27
Yep, nothingspecial's command worked for me.

Sounds a lot like the sources.list is corrupted... :-k

---

### Post by cortman on 2012-02-27
> **nothingspecial said:**
> You don't need (gk)sudo to view the file. Only to change it.

Yes, I know you don't need gksu to view it. I guess I automatically thought you were asking the OP to edit it. My mistake!
And yes, that sounds like a corrupted file alright.

---

