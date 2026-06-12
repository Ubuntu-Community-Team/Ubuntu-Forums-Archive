---
title: "Ubuntu time and date city list"
date: 2012-01-07
forum: Programming Talk
---

### Post by falven on 2012-01-07
Hello,
I am looking for where Ubuntu keeps the list of cities it uses for it's time zones.
I know Ubuntu uses the zoneinfo database for all of the time zone information, what I am looking for specifically is the list of default allowed cities.
Thanks,
-Falven

---

### Post by Bachstelze on 2012-01-07
Look in /usr/share/zoneinfo.

---

### Post by falven on 2012-01-07
> **Bachstelze said:**
> Look in /usr/share/zoneinfo.
 
I did find that directory, just can't find where the cities are listed...

---

### Post by Bachstelze on 2012-01-07
They are sorted by area, /usr/share/zoneinfo/Europe, etc.

---

### Post by falven on 2012-01-08
> **Bachstelze said:**
> They are sorted by area, /usr/share/zoneinfo/Europe, etc.
 
Seems those files are compiled or of the sort, any pointers on how I can access the cities within each country?

---

### Post by Bachstelze on 2012-01-08
What do you mean by "accessing" and "country"? PLease describe what you want to do in more detail, because I really have no idea what it is.

---

