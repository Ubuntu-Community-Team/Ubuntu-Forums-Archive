---
title: "Broken Conky Weather Forecast Python Script"
date: 2011-07-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-07-02
I have been working on how to get this fixed for a couple of days now and there is a work around. This url will give you the info. 

[http://ubuntuforums.org/showpost.php?p=11005003&postcount=3317](http://ubuntuforums.org/showpost.php?p=11005003&postcount=3317)

You need to modify the /usr/share/conkyforecast/conkyForecast.py file

And then compile it.

If you have never compiled a python file before as I did not here is the steps I took after updating the conkyForecast.py file.

$ cd /usr/share/conkyforecast
$ sudo python
>>> import py_compile
>>> py_compile.compile('conkyForecast.py')
Ctrl D to get you out of python
I think I logged out and back in but if not reboot and all should be back again.

Thanks to all that helped get this working again.

And here is the result.


Bill

---

### Post by VinDSL on 2011-07-03
> **sparker256 said:**
> Thanks to all that helped get this working again.[...]
Thanks, Bill, for getting the ball rolling...

Much appreciated!  ;)

---

### Post by Quackers on 2011-07-03
Fixed mine too :-)
Thanks sparker256

---

