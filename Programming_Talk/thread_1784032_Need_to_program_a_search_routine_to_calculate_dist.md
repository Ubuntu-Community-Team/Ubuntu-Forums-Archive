---
title: "Need to program a search routine to calculate distance between addresses"
date: 2011-06-16
forum: Programming Talk
---

### Post by flucoe on 2011-06-16
Hi,

I have a dataset that contains the address of vendors and the location of jobs executed by those vendors. I need to calculate the distance from the address of the vendor to the job. As I have like a thousand jobs and for each job something between 1 and 15 vendors, I need to learn to program "something" that can allow me to do this without doing it by hand. I have never programmed something like this before (my experience is just matlab), so any suggestion on software needed and how to do this would be great.

Just to give you an idea the data looks like this
Job Job_location Vendor Vendor_address
1    a             1       b
1    a             2       c
1    a             3       d
2    e             1       b
2    e             4       f

Thanks,

---

### Post by r-senior on 2011-06-16
What language are you thinking of? There are libraries around for various languages that do the geometry required to convert longitude and latitude differences into ground distance. It's not a simple calculation.

---

### Post by flucoe on 2011-06-16
As I have never done anything like this I have no idea what language to use. Basically, I don't know any programming language unless writing code in Matlab counts, so in any case I will need to learn the language that I choose.

Another point to consider is that I only have the address (say 123 N Street, City, State, and in some cases the zip code), so I don't have latitude and longitude. I would need to compute those as well.

Thanks,

---

### Post by r-senior on 2011-06-16
Sounds like the Google Maps API could be what you need?

[http://code.google.com/apis/maps/documentation/webservices/index.html](http://code.google.com/apis/maps/documentation/webservices/index.html)

---

### Post by flucoe on 2011-06-16
Eh...this is embarrassing. I didn't found that when I was looking for something useful. I'll take a look and either if it works or not, I'll post it here.
Thanks!

---

