---
title: "Java and calendar database"
date: 2009-07-07
forum: Programming Talk
---

### Post by Boondoklife on 2009-07-07
Ok I am getting ready to start a project that will have a calendar in it and will need to hold appointments. Now normally I would use an SQL database with this type of stuff, but it is going to be a standalone app so no database servers.

The question is how would you recommend storing and accessing these entries since a real database is not an option.

Thanks for the suggestions.

---

### Post by Volt9000 on 2009-07-07
How about an XML file? There should be plenty of libraries that can give you XML parsing support.

Granted an XML file is not the most efficient way, as you will (probably) have to read in the entire file and parse through it to find what you need, but it's a nice simple way for storing simple text.

---

### Post by cph05a on 2009-07-07
Have looked into Java DB (derby)? It works great with stand alone apps.

---

### Post by Boondoklife on 2009-07-07
I was thinking a random access file and having the index be the dat in a yearmonthday form. Does this sound like a good idea or no? I was thinking about xml but then this would leave the data in a ready to read form and this would not suit the needs of the app.

---

### Post by Boondoklife on 2009-07-07
> **cph05a said:**
> Have looked into Java DB (derby)? It works great with stand alone apps.

No I have not, I will look into it now. Does this require a server to run derby or can this just be packaged with the installer? I ask as what I am looking to create is a distributable app but most of the users will not have the know-how to setup a database server or configure the connection.

---

### Post by myrtle1908 on 2009-07-07
> **Boondoklife said:**
> No I have not, I will look into it now. Does this require a server to run derby or can this just be packaged with the installer? I ask as what I am looking to create is a distributable app but most of the users will not have the know-how to setup a database server or configure the connection.

You can run Apache Derby in embedded mode.

**Embedded**

"Refers to Derby being started by a simple single-user Java application. With this option Derby runs in the same Java virtual machine (JVM) as the application. Derby can be almost invisible to the end user because it is started and stopped by the application and often requires no administration."

Quoted from [http://db.apache.org/derby/docs/dev/getstart/](http://db.apache.org/derby/docs/dev/getstart/)

---

### Post by Boondoklife on 2009-07-07
On that same page reading now, this looks promising thanks!

---

