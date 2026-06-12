---
title: "Shell just doesn't play ball!"
date: 2014-01-08
forum: Programming Talk
---

### Post by minerbog on 2014-01-08
Hi all,

Haven't been here for a while... Nice new look!

Anyway, I have setup a shell script to add new directories for my vps and add the necessary setup data to the Nginx config file.

Now in  my script I have the following:

```

echo "server {
listen 80;
blah blah blah
} >> /etc/nginx/conf.d/default.conf

```

Now this according to all the posts, blog, sites I have read should work. But it doesn't. It just overwrites with the latest setup.

Its driving me nuts.  Please help !!!

Regards,

Gavin.

---

### Post by Habitual on 2014-01-08
> **minerbog said:**
> Hi all,

Haven't been here for a while... Nice new look!

Anyway, I have setup a shell script to add new directories for my vps and add the necessary setup data to the Nginx config file.

Now in  my script I have the following:

```

echo "server {
listen 80;
blah blah blah
} >> /etc/nginx/conf.d/default.conf

```

Now this according to all the posts, blog, sites I have read should work. But it doesn't. It just overwrites with the latest setup.

Its driving me nuts.  Please help !!!

Regards,

Gavin.

```
vi  nginx.template
``` and add
```
server { 
listen 80; 
blah blah blah
}
```

```
cat nginx.template >> /etc/nginx/conf.d/default.conf
```

you may wish the quotes, I did not think they were needed.

---

### Post by steeldriver on 2014-01-08
For interactive input, you could also do

```

$ cat >> /etc/nginx/conf.d/default.conf
server {
listen 80;
blah blah blah
}

```

and use Ctrl-d when you're done typing. To use the equivalent in a script, use a "here file" which is basically the same but with a specific delimiter instead of Ctrl-d

```

cat >> /etc/nginx/conf.d/default.conf [COLOR=#0000ff]<<EOF[/COLOR]
server {
listen 80;
blah blah blah
}
[COLOR=#0000ff]EOF
[/COLOR]
```

see [http://en.wikipedia.org/wiki/Here_document#Unix_shells](http://en.wikipedia.org/wiki/Here_document#Unix_shells)

---

### Post by minerbog on 2014-01-08
Thanks Habitual, but I had tried that too.

I have now solved the issue and it just goes to show how staring at the same piece of code for hours makes you miss the obvious!!

A bit further up the script I backed up the old config file by using mv. Of course it moves it so there is nothing to append to!! I changed it to cp so when the append comes along there is a file there!!

God I feel so stupid now... :(

Sorry!!

---

### Post by Habitual on 2014-01-08
> **minerbog said:**
> God I feel so stupid now... :( Sorry!!


Don't apologize!
It's called "experience" now. :)

---

