---
title: "howto: ontv and xmltv setup"
date: 2006-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by ironslave on 2006-09-19
This guide will get you through the basic setup of getting xmltv running so you can use it with ontv.

first things first... get on synaptics and get your programs.... look for ontv (applet) and xmltv (pearl script).

once installed open up a terminal and type the following:

	Britain and Ireland		tv_grab_uk_rt

	Canada and United States        tv_grab_na_dd, tv_grab_na

	Germany				tv_grab_de_tvtoday

	New Zealand			tv_grab_nz

	Finland				tv_grab_fi

	Italy				tv_grab_it

	Spain				tv_grab_es, tv_grab_es_digital

	Netherlands			tv_grab_nl, tv_grab_nl_wolf

        Denmark                         tv_grab_dk

        Hungary and Romania             tv_grab_huro

        Japan                           tv_grab_jp

        Sweden				tv_grab_se        

        France                          tv_grab_fr

        Norway                          tv_grab_no

        Portugal                        tv_grab_pt

Based on where you are type in the tv_grab command followed by --configure eg: tv_grab_na_dd --configure

this will take you through a configuration guide which will also make you register with a website to retrive the files from. 

once that is finished retype your tv_grab based on your location followed by an output file name e.g. 
tv_grab_na_dd --output (path and desired file name) eg /xmltv/listings/local.xml or listings.xml(failure to specify a path may cause the file to become unfindable)

once thats finished

you have the option of running tv_sort if your having program overlaps ect. ect. but if you have the wrong programs on all channels than you probably have the wrong area, or time zone (mine was off by an hour due to Daylight savings time) 
the command would be as follows 

tv_sort --output (name and path of output file) inputfile (replace inputfile with the path and name of the original download)

load your file in gotv and select the channeles to watch
your good to go so lets make a basic list of commands than:


tv_grab_xxxx --configure
tv_grab_xxxx --output XXXXXXXX.xml
tv_sort --output XXXXXXXX.xml XXXXXXXX.xml

this should do the trick\\:D/

---

### Post by fearpi on 2007-03-26
This tutorial was very helpful. Thanks. One thing, though - you keep referring to "gotv" in your post as opposed to "ontv" in your title... are these two different things?

---

### Post by ironslave on 2007-05-06
i should fix that. it realy is ontv.. not gotv

---

### Post by BoomShaka on 2009-05-11
When specifying the listings file, on my Jaunty (9.04) install I needed to manually create the destination folder if it did not exist.

---

