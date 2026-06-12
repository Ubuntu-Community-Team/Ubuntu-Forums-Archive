---
title: "Trim file name from FTP monitor output"
date: 2011-10-19
forum: Programming Talk
---

### Post by kainalu on 2011-10-19
Hey all,

I have a media center that is running an ProFTP backend for serving the media. When a movie is playing, I currently have an conky indicator that I programmed with a shell script that will tell me the service is in use. I would like to be able to have it tell me the movie that is playing, but don't know how to trim the output. 

I would like to take this command's output


```
ps aux | grep proftpd | egrep "RETR"
```

which looks like :

```
proftpd: anon - ::ffff:192.168.2.109: anonymous/: RETR 10,000 BC (2008).avi
```


and trim it to look like :

```
10,000 BC (2008)
```

The movie may be any movie, so it is hard for me to wrap my head around figuring out how to program the script to cut it up. Anyone can please help?

Thanks!
Kainalu

---

### Post by papibe on 2011-10-19
Hi kainalu,

This works with your example:
```
$ ps aux | grep proftpd | egrep "RETR" |** sed 's/^.*RETR\ //'**
```
Which basically removes everything from the beginning of the string to the pattern "RETR ".

Unfortunately I don't use or have ProFTP, so may be further tests would be needed.

Hope it helps, tell us how it goes.
Regards.

---

### Post by kainalu on 2011-10-19
That gives me $: command not found


Minor typo?

I figured this out...

```
 ps aux | grep proftpd | egrep "RETR" | awk '{ print $17, $18, $19, $20, $21 }' | cut -d'.' -f1
```

It is very ugly, but strangely effective

---

### Post by papibe on 2011-10-19
> **kainalu said:**
> That gives me $: command not found
That's represent the bash prompt, to test that code just don't paste the initial $.

Regards.

---

### Post by kainalu on 2011-10-19
Crap... 

Stupid mistake. Thanks!

---

