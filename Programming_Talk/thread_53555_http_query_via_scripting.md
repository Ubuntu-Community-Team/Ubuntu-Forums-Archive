---
title: "http query via scripting"
date: 2005-08-01
forum: Programming Talk
---

### Post by skyboy on 2005-08-01
Hi,

I wanted to know if it is possible to create a script to be able to retrieve my IP address from [http://www.whatismyip.com](http://www.whatismyip.com)
My router's IP is dynamic and changing quite often so it would be great so I could add this script to my superkaramba theme to know my IP address as soon as it changes.

OOhh yes, my computer is connect to my router, so basically it's my router IP address I need to retreive, that is why I can't use something like
 ```
ifconfig ath0 | grep 'inet addr' | cut -d ':' -f2 | cut -d ' ' -f1 
``` 

thanks :)

---

### Post by skyboy on 2005-08-01
up :)

---

### Post by flyinglizard on 2005-08-01
w3m [www.whatismyip.com](www.whatismyip.com) -dump_source|grep "<TITLE>"|cut -d " " -f 5

---

### Post by skyboy on 2005-08-01
Wooo, no kidding, you did it !! :D
I'm amazed, i didn't know it was even possible !! 
Thank you so much !!

---

### Post by Teren on 2005-08-08
What about:

GET whatsmyip.net | grep "<TITLE>"| cut -d " " -f 7 | sed -e 's/[a-Z]//g;s/[<>\/]//g'

Hehe ;)

---

### Post by skyboy on 2005-08-09
nice too :D !!

---

