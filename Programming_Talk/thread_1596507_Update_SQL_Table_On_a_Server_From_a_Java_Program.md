---
title: "Update SQL Table On a Server From a Java Program"
date: 2010-10-14
forum: Programming Talk
---

### Post by iampriteshdesai on 2010-10-14
I have created a Java program which scans a given folder and creates a .txt with a list of names of all the files in that folder.

I want to create a table on MYSQL server on a website and fill it with the information given in that .txt file.

How can I do that?

---

### Post by spjackson on 2010-10-14
> **iampriteshdesai said:**
> I have created a Java program which scans a given folder and creates a .txt with a list of names of all the files in that folder.

I want to create a table on MYSQL server on a website and fill it with the information given in that .txt file.

How can I do that?
A common way to populate a MySQL table from Java is with JDBC [http://download.oracle.com/javase/tutorial/jdbc/](http://download.oracle.com/javase/tutorial/jdbc/)

However, will your Java program be running on the host or network that holds the database? If you are wanting to populate a database on a webserver from a remote machine, then a more appropriate method would probably be to post the data to the webserver and have the server populate the database, using HTTP POST, or Ajax, or ftp, or some other method.

---

### Post by iampriteshdesai on 2010-10-14
> **spjackson said:**
> A common way to populate a MySQL table from Java is with JDBC [http://download.oracle.com/javase/tutorial/jdbc/](http://download.oracle.com/javase/tutorial/jdbc/)

However, will your Java program be running on the host or network that holds the database? If you are wanting to populate a database on a webserver from a remote machine, then a more appropriate method would probably be to post the data to the webserver and have the server populate the database, using HTTP POST, or Ajax, or ftp, or some other method.
Yeah, the Java program will be running on a remote machine. Thanks for suggesting the other method.
I'm using PHP on the server. I know how to send a POST request using HTML, but how can I send a POST request using Java?

---

### Post by spjackson on 2010-10-14
> **iampriteshdesai said:**
> Yeah, the Java program will be running on a remote machine. Thanks for suggesting the other method.
I'm using PHP on the server. I know how to send a POST request using HTML, but how can I send a POST request using Java?
There's a good example here [http://download.oracle.com/javase/tutorial/networking/urls/readingWriting.html](http://download.oracle.com/javase/tutorial/networking/urls/readingWriting.html) It's the section headed "Writing to a URLConnection" that you need. There shouldn't any problem posting to a php url that will do the database bit.

---

