---
title: "PHP and database programming"
date: 2009-01-24
forum: Programming Talk
---

### Post by zpzpzp on 2009-01-24
I am new to PHP and database programming. Are there any existing code for using PHP to create/manipulate MySQL databases, so I don't need to do everything from scratch?

Thanks,

Paul

---

### Post by Phristen on 2009-01-24
[phpMyAdmin]("http://www.phpmyadmin.net/home_page/index.php")?

---

### Post by zpzpzp on 2009-01-25
Thank you Phristen!

However I took a look at phpMyAdmin, and found that it is under the GPL license, which means with distribution of anything based on phpMyAdmin I have to also supply source code. What if I do not wish to disclose all source code?

Are there similar programs under a less restrictive license?

Thanks in advance!

---

### Post by escapee on 2009-01-25
:-s

I am inclined to believe you're misinterpreting the purpose of phpMyAdmin.

What exactly are you looking for?  If you simply don't want to create the database, table, etc through code yourself but wish to redistribute the database, just do it through phpMyAdmin and save the output SQL queries to perform the actions needed.

---

### Post by zpzpzp on 2009-01-25
> **escapee said:**
> :-s

I am inclined to believe you're misinterpreting the purpose of phpMyAdmin.

What exactly are you looking for?  If you simply don't want to create the database, table, etc through code yourself but wish to redistribute the database, just do it through phpMyAdmin and save the output SQL queries to perform the actions needed.

Hi Escapee,

Thanks for your reply and I will clarify this. I am making an application in php, in which database manipulation is part of what the program does. I am looking for some existing php code (similar to phpMyAdmin), which allows me to reuse the code in my application without having to disclose all my source code when being asked for.

And because phpMyAdmin is under the GPL license, if Iuse it in my application, I will have to disclose all my source code to anyone who asks for it right?

Hope I made it clear this time...:)

Paul

---

### Post by mike_g on 2009-01-25
You could try [phpminadmin](http://sourceforge.net/projects/phpminadmin/), which i prefer to myadmin as its simpler and a lot more responsive. Its got an Apache licence, not sure what that means tbh. But if its a problem the entire prog fits in one file and is not all that big, so you could always re-implement it.

---

### Post by brentoboy on 2009-01-26
Do you intend to distribute the "Code" to anyone else? or just give them access to the site?

GPL only requires that you be willing to provide source code if you distribute the product to someone else in compiled form.  Posting it on a web server is not distributing it to another party.  And the pages it serves up are not considered distributing the product (the same way distributing gifs made with Gimp don't require you to distribute the Gimp).

Do you follow.

So, unless you are writing a web control panel that you expect to resell (or offer a download) to other people to put your PHP files on their servers, the GPL is not going to be a restriction to force your code out into the wild.

The GPL gives you 100% freedom to modify and or use the code in whatever way you want with absolutely no restrictions... right up until you start to distribute a derivative program as though you wrote all the code.  You wont be distributing the program (I expect) so you can do whatever you want.

Details here:
[http://www.gnu.org/licenses/quick-guide-gplv3.html](http://www.gnu.org/licenses/quick-guide-gplv3.html)

---

### Post by zpzpzp on 2009-01-29
Hi Mike-G and BrentOBoy

Thank you for your replies.

I did some research on this, and according to 
[http://www.fsf.org/licensing/licenses/gpl-faq.html](http://www.fsf.org/licensing/licenses/gpl-faq.html)

> A company is running a modified version of a GPL'ed program on a web site. Does the GPL say they must release their modified sources?

    The GPL permits anyone to make a modified version and use it without ever distributing it to others. What this company is doing is a special case of that. Therefore, the company does not have to release the modified sources.

    It is essential for people to have the freedom to make modifications and use them privately, without ever publishing those modifications. However, putting the program on a server machine for the public to talk to is hardly &#8220;private&#8221; use, so it would be legitimate to require release of the source code in that special case.

So I guess the simple answer is that when you write anything based on a GPL program or modify a GPL program and use it on your public server, you have the obligation to give away all your code.

---

### Post by zpzpzp on 2009-01-29
And interestingly, according to the same link:
> when the organization transfers copies to other organizations or individuals, that is distribution. In particular, providing copies to contractors for use off-site is distribution. 

So basically if the thing physically leaves your premise (home or company), you also have to supply source code.

So... my interpretation is that if you develop any product derived from a GPL'd program, it must be open source if they are used by anyone not on your premise, or if the program physically leaves your premise.

Wow... a license that advocates "freedom" can be so restrictive in the mean time...

---

### Post by CptPicard on 2009-01-29
I don't quite understand why you don't just learn how to use databases from PHP like everyone else... it's a basic part of a web application. Pulling stuff out of db's into a HTML page was what the thing was invented for.

And no, just because I happen to use open-source libraries in a web application, does not mean that I need to put up the web app's source available somewhere. It may be different if I a) create a substantial derivative of one of those libs, and b) if I actually distribute whatever is there running on the server. That is, considering I'm mostly a Java guy, if I really for some reason hand out the actual .class files running on top of my Tomcat.

---

### Post by Mickeysofine1972 on 2009-01-30
I'm inclined to agree with the good captain on that one.

You simple can not make web apps without knowing the basics of database functions, whether that is Mysql, Postgres, sqlLite or what ever you decide to do.

You need to know at least how to connect, select a database and send SQL to it as a basic set of skills. and You will NEED to know at least enough SQL to insert, update and delete a record.

If you at least know that much you can get by..... at least for a while :D

Mike

---

### Post by stevescripts on 2009-01-30
Being pretty much in agreement with most of what has been said in this thread so far, a couple of more thoughts.

If you're worried about licenses, have you looked carefully at MySQL's ?

Also, as pointed out, you need to learn enough of whatever language you are using to interact with the webpage -> database transfers and vice-versa ... but one more *important* part - while you are learning be sure to learn all you can about things like sql injection and security - there are lots of folks out there who seem to have nothing better to do than try to steal or muck with your data.

Steve

---

### Post by Uchiha_madara on 2009-01-30
you can use :

1 - MySQl Front,
2 - MySqlLite
3 - Postegre
5 - Mysql Administrator and Mysql Query Bowser
6 - phpmyadmin .........

---

