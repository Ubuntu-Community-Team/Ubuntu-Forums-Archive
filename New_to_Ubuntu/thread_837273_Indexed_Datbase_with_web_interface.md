---
title: "Indexed Datbase with web interface"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by rgotten on 2008-06-22
i have build my server 8.04 and in working nice, i need the following:

3 windows computers conected to my ubuntu server.they comunicate thru samba. , i am a doctor ( even thougth what i need  can be aply to offices, etc) and this is what i need:

1)thru a web interface be able to search for a name, last name or custumer number from my windows computers. if it does not exist, then to be able to create a new one. When the person is found or created, then it will have folders (ie: documents, copies of bills, copies of lab reports (in pdf format), chart documents (in word format), pictures (jpg. 

I heard that this should be thru indexing so is ligther. 

Can anybody help

rgotten

---

### Post by The Cog on 2008-06-22
Do you have an existing ddatabase with all this medical info in it, or are you planning to create your own?

This could turn out to be a very big project. You may be far better off looking at this list of open-source software and seeing if anything fits your needs:
[http://en.wikipedia.org/wiki/List_of_open_source_healthcare_software](http://en.wikipedia.org/wiki/List_of_open_source_healthcare_software)

---

### Post by rgotten on 2008-06-22
Just forget i am a doctor for a sec, i jsut need to find or create for example new clients with first an last name, and a record number, if i create a new record it will automatic create lets say 5 folders: client bills, client description, client info. Each one of this folder is were i am going to place file documets that are in eiterh word format, jpd format or pdf format, so b asically that i get the person information in a piece of paper and scan it and save it on pdf format, or i take a picture and sabe it on a folder as jpg.

Is this a big project still?

---

### Post by the_doc on 2008-06-22
You're going to need to set up a web server, the web front end, and the database etc.  So yeah, it is a large project, in terms of time as well as sophistication.

The link posted above that lists OS healthcare software may be a better way to go.

---

### Post by indytim on 2008-06-22
Without going through the whole effort of "re-inventing the wheel", suggest that you swing over to "HotScripts.com" at [http://www.hotscripts.com/]("http://www.hotscripts.com/"),  While there go to the php scripts section and do a search.  You may find something ready-made to fit most of your needs.  At a minimum, as was stated by another responder, you will need a LAMP installation (Linux-Apache-MySQL-PHP) to get things rolling.
IndyTim

---

### Post by Xerp on 2008-06-22
You'll need:

Linux - The OS (Ubuntu)
Apache - Web Server
MySQL - the database
PHP - For programming

Programming this up from scratch (assuming you already have good PHP and MySQL skills) should take about 2 weeks for a working prototype. You can build on it from there, and after a few months it should be pretty close to working how you'd like.

The other alternative would be to see if there is similar software available. Most of the time it wouldn't do exactly what you want in the way that you want it done though.

---

### Post by rgotten on 2008-06-22
how should i sear for it as medical databgase or database for folders?

---

