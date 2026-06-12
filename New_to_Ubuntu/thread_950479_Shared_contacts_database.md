---
title: "Shared contacts database"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by satjat on 2008-10-17
I want to setup a web accessible contacts database with something like a web mail client but without having an actual mail server.
The idea is that users can login through a browser mainly to access  the contacts database. The ability to send mail through that is not as much needed though it would be nice.
I understand that I will probably have to resort to a mail server, even if I only use mail fetching from the user's original pop3 account. Is that so? I couldn't find any simple solutions.
Setting up the sql database and creating a java UI to access it would be another option. But I am looking for something that can be deployed easily.
If there is no other option than setting up a mail server, which one is best, keeping in mind that contact management is more important than email features for this project?
Thank you all in advance

---

### Post by indytim on 2008-10-17
You might consider meandering over to say HotScripts.com ( [http://www.hotscripts.com/]("http://www.hotscripts.com/") ) to see if you can get some near-ready out of the box php scripts to meet your needs. 

IndyTim

---

### Post by greg@localhost on 2008-10-17
YOu can use PHP to send mail using mail(), you can also use imap_open() for POP3 servers - ignore the function name, although it's mainly for IMAP operations, you can also do most things with POP3 (I've used it myself). 

See: [http://uk.php.net/manual/en/function.imap-open.php](http://uk.php.net/manual/en/function.imap-open.php)

It's relatively trivial to setup an 'address book' sort of CMS affair with PHP and MySQL.

Why would you want to us a Java UI?

You would probably better off going the PHP and MySQL route, since most shared hosting providers can accomodate this. If you *really* need to use Java, then you may need to host the site on a dedictaed server.

---

### Post by satjat on 2008-10-19
Well, I am planning to host this on a local server, java is no problem. The reason I am looking for something ready is that it would be too complicated to include all functionality of something like zimbra collaboration server for example in my own project.
I am not sure if zimbra is  good for me, I have to test it out. And I don't know if there are any alternatives...

---

