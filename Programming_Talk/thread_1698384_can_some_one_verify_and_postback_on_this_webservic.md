---
title: "can some one verify and postback on this webservice xml"
date: 2011-03-02
forum: Programming Talk
---

### Post by sdowney717 on 2011-03-02
home and libya are missing many records, you can scroll down to see lots of elements with no data, however dog returns with full data

search for home
[http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22home%22&startRecord=1&maximumRecords=20](http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22home%22&startRecord=1&maximumRecords=20)

search libya
[http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22libya%22&startRecord=21&maximumRecords=20](http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22libya%22&startRecord=21&maximumRecords=20)

search for dog
[http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22dog%22&startRecord=1&maximumRecords=20](http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22dog%22&startRecord=1&maximumRecords=20)

the LOC emailed me back and gave me a new server  at
[http://lx2.loc.gov:210/LCDB?version=1.1&operation=searchRetrieve](http://lx2.loc.gov:210/LCDB?version=1.1&operation=searchRetrieve)

which is aware of the unicode, but I will need a function to handle it

 $raw_xml = file_get_contents($request);

this is too slow to be useful.

---

### Post by Arndt on 2011-03-02
> **sdowney717 said:**
> home and libya are missing many records, you can scroll down to see lots of elements with no data, however dog returns with full data

search for home
[http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22home%22&startRecord=1&maximumRecords=20](http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22home%22&startRecord=1&maximumRecords=20)

search libya
[http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22libya%22&startRecord=21&maximumRecords=20](http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22libya%22&startRecord=21&maximumRecords=20)

search for dog
[http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22dog%22&startRecord=1&maximumRecords=20](http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=%20%22dog%22&startRecord=1&maximumRecords=20)

the LOC emailed me back and gave me a new server  at
[http://lx2.loc.gov:210/LCDB?version=1.1&operation=searchRetrieve](http://lx2.loc.gov:210/LCDB?version=1.1&operation=searchRetrieve)

which is aware of the unicode, but I will need a function to handle it

 $raw_xml = file_get_contents($request);

this is too slow to be useful.

What kind of help are you asking for, here? I can't make head or tail of it.

---

