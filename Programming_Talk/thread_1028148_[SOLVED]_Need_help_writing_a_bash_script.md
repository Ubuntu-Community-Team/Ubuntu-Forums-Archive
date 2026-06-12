---
title: "[SOLVED] Need help writing a bash script"
date: 2009-01-02
forum: Programming Talk
---

### Post by Stochastic on 2009-01-02
Hey, I've never written a bash script before but I'm pretty sure it's the ticket I need to make my news-getting easier.

I'd like to be able to run the script, and have it
  -figure out which day it is (day of the week)
  -visit: [http://vancouver.24hrs.ca/PDF/](http://vancouver.24hrs.ca/PDF/)
  -download the appropriate .pdf to a specified folder (the folder can be hard specified into the script, not dynamic)

Anyone think they have what it takes to help me write this?  Or just do it for me ;)

I figure for the downloading of the correct link, a simple cat <webpage> | grep Wednesday will give the line that has the correct link.  Then it's just a matter of parsing the line to find the [http://*.pdf](http://*.pdf) portion.  Then a simple wget call should do the trick.

---

### Post by The Cog on 2009-01-02
This will retrieve the line you want:
```
GET [http://vancouver.24hrs.ca/PDF/](http://vancouver.24hrs.ca/PDF/) | grep \>$(date +%A)\<
```
but I'm not sure about picking the URL out of that. Some creative use of sed or awk should do it.

---

### Post by mali2297 on 2009-01-02
Try this
```

#!/bin/sh

day=$( date '+%A' )
url=$( wget -q -O - 'http://vancouver.24hrs.ca/PDF/' | grep "\.pdf.*$day" | cut -d\" -f2 )
wget $url

```

I have assumed a certain pattern that might not always be right.

---

### Post by Stochastic on 2009-01-02
> **mali2297 said:**
> Try this
```

#!/bin/sh

day=$( date '+%A' )
url=$( wget -q -O - 'http://vancouver.24hrs.ca/PDF/' | grep "\.pdf.*$day" | cut -d\" -f2 )
wget $url

```

I have assumed a certain pattern that might not always be right.

Well that seems to work.  Thank you.

Can you explain what pattern you've assumed?  What does ```
cut -d\" -f2
``` do exactly?

Next challenge would be to adopt this script to work on weekends to grab the weekend edition (though I really don't need that functionality, I just though you might enjoy the challenge and it could help teach me bash).

---

### Post by mali2297 on 2009-01-02
> **Stochastic said:**
> 
Can you explain what pattern you've assumed?  What does ```
cut -d\" -f2
``` do exactly?


I have assumed that the url is in a line of the form
```

[some text without quotes]"[url].pdf"[some text][Weekday][some text]

```
The command *cut -d\" -f2* reads the line and writes the second field separated by quotes. That is, everything between the first and the second '"'.

---

