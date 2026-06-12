---
title: "Print matched regular expression"
date: 2008-01-14
forum: Programming Talk
---

### Post by accord on 2008-01-14
I've read couple of docs on RE, but can't seem to find this. I want to extract a matched RE from a file. For example in http logs:
```
1200137262.721    209 192.168.10.180 TCP_REFRESH_HIT/304 0 GET http://69.20.5.20/menu_array.js - NONE/- -
1200137263.614    204 192.168.10.180 TCP_REFRESH_HIT/304 0 GET http://69.20.5.20/homepage_images/cart.gif - NONE/- -
1200137263.627   1049 192.168.10.180 TCP_REFRESH_HIT/304 0 GET http://69.20.5.20/webroot/sync/menu_images/arrow.gif - NONE/- -
1200137264.050    626 192.168.10.180 TCP_REFRESH_HIT/304 0 GET http://69.20.5.20/images/is_logo.gif - NONE/- -
1200137264.236    414 192.168.10.180 TCP_REFRESH_HIT/304 0 GET http://69.20.5.20/secondary_images/titlebar.jpg - NONE/- -
1200137264.861    204 192.168.10.180 TCP_REFRESH_HIT/304 0 GET http://69.20.5.20/misc-images/france.gif - NONE/- -

```

I want to match the urls of JPGs. I tried```
egrep "http://.*.(JPG|jpg)"
```but this outputs the whole line instead of just the url. How do I print JUST the string that I matched?

---

### Post by ghostdog74 on 2008-01-14
```

awk '
{
  for(i=1;i<=NF;i++){
    if ( $i ~ /http:\/\/.*[Jj][pP][gG]/ ){
        print $i   
    }
  }
}
'  "file"

```
output:
```

# ./test.sh
http://69.20.5.20/secondary_images/titlebar.jpg

```

---

### Post by amo-ej1 on 2008-01-14
or with some sed love:


```

edb@lape:/tmp$ cat log.txt | egrep "http://.*.(JPG|jpg)" | sed 's/.*\(http.*[gG]\)\ .*/\1/'
http://69.20.5.20/secondary_images/titlebar.jpg

```

---

### Post by ghostdog74 on 2008-01-14
> **amo-ej1 said:**
> or with some sed love:


```

edb@lape:/tmp$ cat log.txt | egrep "http://.*.(JPG|jpg)" | sed 's/.*\(http.*[gG]\)\ .*/\1/'
http://69.20.5.20/secondary_images/titlebar.jpg

```

there is no need to use cat (one less process). eg
```

egrep "http://.*.(JPG|jpg)" log.txt

```
Anyway,  sed can do everything
```

sed -e "/[jJ][pP][gG]/!d
        s/\(http:.*[j][pP][gG]\).*/\1/
        s/.*\(http:.*[jJ][pP][gG]\)/\1/             
       " "file"

```
output:
```

# ./test.sh
http://69.20.5.20/secondary_images/titlebar.jpg

```

---

### Post by Cappy on 2008-01-14
Another way is to use the -o option
```
egrep -o "http://.*.(JPG|jpg)"
```

---

### Post by accord on 2008-01-14
Thanks, all of your solutions worked perfectly!
Thank you for your prompt responses.

---

