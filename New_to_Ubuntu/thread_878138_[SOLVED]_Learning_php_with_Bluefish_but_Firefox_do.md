---
title: "[SOLVED] Learning php with Bluefish but Firefox doesn't open php files"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by madeinbrazil on 2008-08-02
Hello wonderful community,

I starting to learn php and installed Bluefish to test. I created a php file and when trying to open in Firefox it just asks me if I want to download the file, doesn't open it. Any suggestions?

I've installed the latest php and apache from Synaptic but it doesn't work. In opera I can open the file but it doesn't show the php lines that were supposed to be visible.

Thanks in advance for the help!!


BTW, I'm starting to learn php from Zend Developer Zone, any other suggestions? Also, is Bluefish a good tool to start learning with?

---

### Post by Locke_99GS on 2008-08-02
Did you configure apache for PHP, and have apache running? 

If so, make sure you are placing your test file in *htdocs*, and directing your browser to the server, not the file directly on the PC. 

Example: [http://127.0.0.1/test.php](http://127.0.0.1/test.php)

---

### Post by AndrewTheArt on 2008-08-02
Look like you don't have Apache/PHP running... Try my guide - 

[http://andrewtheart.tripod.com/linux/Ubuntu804Server.html](http://andrewtheart.tripod.com/linux/Ubuntu804Server.html)

Search for the string "**Terminal Install Method** (Recommended)" and follow from there. You'd probably want to stop at step 7...

As a general note, I use Aptana Studio (Community Edition) for web development (it's free). I recommend it. ActiveState also makes a good product called Komodo IDE that you may wish to purchase. It's expensive though. I'm using a trial and I like it.

---

### Post by madeinbrazil on 2008-08-02
Thanks for the help!!

> Look like you don't have Apache/PHP running... Try my guide -

[http://andrewtheart.tripod.com/linux...804Server.html](http://andrewtheart.tripod.com/linux...804Server.html)

As a general note, I use Aptana Studio (Community Edition) for web development (it's free). I recommend it. ActiveState also makes a good product called Komodo IDE that you may wish to purchase. It's expensive though. I'm using a trial and I like it.
Do I really need MySQL installed? I'm just testing normal php files for the moment. Thanks for the program tips! I'll try Aptana, heard other good things about it too.

> Did you configure apache for PHP, and have apache running?

If so, make sure you are placing your test file in htdocs, and directing your browser to the server, not the file directly on the PC.

Example: [http://127.0.0.1/test.php](http://127.0.0.1/test.php)

I've installed Apache and PHP but I'm not sure how to configure them. I tested localhost and it works fine. :) Do I always have to place the files in this folder for it to read the php codes?

---

### Post by Locke_99GS on 2008-08-02
One of the great things about PHP is it's ability to easily communicate with various databases. MySQL is great, and to take full advantage of PHP, you'll want a database to learn with. It's up to you, really.

PHP is a server side scripting language. PHP code is interpreted on the server side, and it's output is sent to the browser by the server. The browser itself does *not* understand PHP. The server see's the PHP code, and runs it through the interpreter, who's output it directs to the client browser. 

By default, the server will serve anything placed inside *htdocs*, and since you want PHP to be interpreted and it's output viewed on your browser, yes you will have to place them in htdocs.

Creating a symlink on your desktop pointing to htdocs may be very helpful to you.

---

### Post by madeinbrazil on 2008-08-02
Wow, thanks for all the great info Locke_99GS!

---

