---
title: "Add/Remove or Adept like Web interface"
date: 2009-02-01
forum: Packaging and Compiling Programs
---

### Post by shoaibi on 2009-02-01
Yesterday i was surfing and found [http://www.appnr.com](http://www.appnr.com). I need a way to develop such a web ui but without the installation part. A web ui which shows the list of latest softwares in the standard repositories and full stop.

Any idea on how could i start it?

---

### Post by tuxxy on 2009-02-01
Something like[ this?]("http://packages.ubuntu.com/")

---

### Post by shoaibi on 2009-02-01
Yup, but a little more use friendly like this doesn't show application name, it shows pakage names when you to to a specific category...
Well to start, even this would be good, any idea how to make such an interface?

---

### Post by tuxxy on 2009-02-01
hmm maybe you could do a mysql database backend with PHP used to probe the database and return items?

---

### Post by shoaibi on 2009-02-01
yup, but how would you store info in database?

---

### Post by tuxxy on 2009-02-01
heh well maybe have different tables for each category like [here]("http://packages.ubuntu.com/intrepid/") then up to you what information to store, if you want specific app search ability then manually enter the information which I wouldn't fancy doing :p or just have each category contain a list of apps which the user could search through

---

### Post by shoaibi on 2009-02-01
Say i just want to store package-name, category, and description. I think using this i can generate a categories page, app in that category and app-specifc page.

Issue is, how to get these values into database? and how to keep the updated with the latest repositories..

something like:
for i in `aptitude search * | cut -d " " -f 3` do
aptitude show "$i" >> ~/applisting
done

---

### Post by tuxxy on 2009-02-01
To enter the information to database you could make it simple by using something like PHPMyAdmin

---

### Post by shoaibi on 2009-02-01
ya, ya, i know...
What i ment was from where should i fetch it, i know how to use databases or such, what i dont know is a way to get the list of my interested values...

---

