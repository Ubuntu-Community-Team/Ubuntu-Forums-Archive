---
title: "how to get the number of secs until latter time in bash script"
date: 2014-04-30
forum: Programming Talk
---

### Post by sam_baker2 on 2014-04-30
hi,
How can you get the number of seconds from current time until ( for example ) 4:25 in the morning?
( this is for a bash script )
I did this:
```

latterTime=$(date +%s --date="04:25")
currTime=$(date +%s)

```
but when I subtract the currTime from the latterTime the number is negative.
I need the number of seconds until the latterTime.

Otherwords, if I do this when the current time is 04:24, I want to get 60 seconds.
If I do this at 04:26, I want to get 24 hours worth of seconds ( minus 60 seconds )


Thanks

---

### Post by papibe on 2014-04-30
Hi sam_baker2.

I would start by checking the expressions without converting them to epoc (%s) as "4:25" may not meaning what you want.

For instance:
```
$ date
Wed Apr 30 22:06:48 CDT 2014

$ date --date="4:35"
Wed Apr 30 **04:35:00** CDT 2014

$ date --date="4:35pm"
Wed Apr 30 **16:35:00** CDT 2014

$ date --date="tomorrow 4:35"
**Thu May  1** 04:35:00 CDT 2014

```
Does that help?
Regards.

---

### Post by sam_baker2 on 2014-05-01
If the current time is somewhere between 00:00 and 04:34, then I would need
```

        do this:
        latterTime=$(date +%s --date="04:25")

```

  If the current time is somewhere between 04:25 and 23:59, then I would need 
```

       do this:
       latterTime=$(date +%s --date="tommorow 04:25")  

```


but I don't know how to check for the current time within those parameters.

---

### Post by sam_baker2 on 2014-05-01
make that :
latterTime=$(date +%s --date="tomorrow 04:25")

---

### Post by Vaphell on 2014-05-01
assuming you only want the nearest future 4:25, you could use modulo arithmetic to avoid the problem with establishing which day to use

```
$ date
Thu May  1 13:45:51 CEST 2014
$ echo $(( ($(date -d 'tomorrow 4:25' +%s)-$(date +%s))%86400 ))
52742
```

---

### Post by sam_baker2 on 2014-05-01
Thanks papibe and Vaphell.
I needed to use the "tomorrow" date option, and the modulus math was interesting
as I have just recently reading up on it as trying to learn about the pgp encryption.
Thanks guys..

---

