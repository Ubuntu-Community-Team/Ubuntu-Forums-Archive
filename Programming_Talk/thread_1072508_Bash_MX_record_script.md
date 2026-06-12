---
title: "Bash MX record script"
date: 2009-02-17
forum: Programming Talk
---

### Post by aliahsan81 on 2009-02-17
I need a bash script for MX record monitoring It will be grate if some one provide me with ideas/small script.It will be grate.IF any one give me idea how we can it with dig nslookup or any other because the provide extra information

Thanks

---

### Post by mikewu on 2009-02-17
Not really sure what you mean by MX record monitoring. Some more specifics would be nice. 

To look up the mx server of a site in general 

nslookup -type=mx ip_addr/site_name

if you wanted that to repeat to a log, make an entry in crontab for it to repeat and redirect the output

#! /bin/sh

nslookup -type=mx ip_address >> /home/user/mx_log

Extra information and specifics will help us to provide you with more accurate and useful information.

---

### Post by aliahsan81 on 2009-02-17
Thanks for your quick reply.I will provide details shortly

---

### Post by aliahsan81 on 2009-02-17
Hi

That i want to do

I have file that contain all domain name.But i need to filter out these domain name because there is some extra info.So need help with sed and awk.And i am making script in bash.Below are the entries.


```


_ax_somename__info__Uptime_days	19	G	2009-02-17T14:36:12-05
_ax_xyz__info__Uptime_days	5	G	2009-02-17T14:35:07-05
_ax_test__info__Uptime_days	14	G	2009-02-17T14:36:06-05
_ax_hello__info__Uptime_days	20	G	2009-02-17T14:36:02-05

```

So what is need is only somename,xyz,test,hello.Need to use sed and awk.So kindly guide me.Then after i got these domain name then i will use dig or nslookup to check what ever there MX record is.

---

### Post by aliahsan81 on 2009-02-17
Hi Again

I have figured out a way to do this but i am stuck on last thing you can help me now i am sure


```


cat data.txt  | awk -F" " '{print $1  }' | sed 's/[ __info__Uptime_days ]*$//'


```

This will give me some thing like this

```

_ax_urname
_ax_123
_ax_test
_ax_hello



```

Last thing what i need is to remove _ax_ can any one do this with sed.

---

### Post by ghostdog74 on 2009-02-17
no need to use that many tools. and don't use cat unnecessarily
```

# awk -F"_" '{print $3}' file
somename
xyz
test
hello


```

---

### Post by digitalvectorz on 2009-02-17
Why not just do another sed...
```

sed -i "/_ax_//"

```

Thus giving something like...
```

cat data.txt  | awk -F" " '{print $1  }' | sed 's/[ __info__Uptime_days ]*$//' | sed -i 's/_ax_//'

```

Granted ghostdog does have a point...I was just continuing your thought process.

---

### Post by ghostdog74 on 2009-02-17
> **digitalvectorz said:**
> 

Thus giving something like...
```

cat data.txt  | awk -F" " '{print $1  }' | sed 's/[ __info__Uptime_days ]*$//' | sed -i 's/_ax_//'

```


awk does the job of tools such as sed/grep/cut/wc/ etc as it is a programming language by itself. lots of beginners doesn't know and use it only for one liners such as this.

---

### Post by aliahsan81 on 2009-02-17
You All are very help full.I am very thank full to you all.That works like a dream.

---

