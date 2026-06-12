---
title: "how to store a web page as a zip???"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by rrsk on 2011-09-19
i want to store java docs permanently
because i want to read them when offline,,,,
please help to do this and also tell me how to recover such stored java docs page

---

### Post by SavageWolf on 2011-09-19
If it's just the "normal" java docs, you can just install "openjdk-6-doc" or the like, and navigate to "file:///usr/share/doc/openjdk-6-jre-headless/api/index.html".

---

### Post by Lisiano on 2011-09-19
By Jaca docs you mean Documentation right?
If so, if you use Firefox, just right click on the page and press Save As.
If you don't use Firefox, use this command. ```
mkdir ~/Documentation
cd ~/Documentation
mkdir Java
cd Java
wget -E -H -k -K -p http://example.com/page.html
```
Replace [http://example.com/page.html](http://example.com/page.html) with a actual URL though.


Or do what SavageWolf said

---

### Post by rrsk on 2011-09-19
thank u guys
i can access java docs even wen am offline....
but help me to take any such pages as a zip or store such website(like documentation page) to permanent storage(local file system)??

---

### Post by pretty_whistle on 2011-09-19
> **rrsk said:**
> thank u guys
i can access java docs even wen am offline....
but help me to take any such pages as a zip or store such website(like documentation page) to permanent storage(local file system)??

Right-click the main folder and choose 'compress'.  This brings up a smaller window where you can choose the compression type.  Click on where it says 'tar.gz' or whatever and you'll get a drop down menu with zip listed on it.  Choose zip.  Click 'create'.  You're done.

---

### Post by rrsk on 2011-09-19
> **SavageWolf said:**
> If it's just the "normal" java docs, you can just install "openjdk-6-doc" or the like, and navigate to "file:///usr/share/doc/openjdk-6-jre-headless/api/index.html".
thank u....its very useful

---

### Post by Paddy Landau on 2011-09-19
[LIST=1]
[*]When you are viewing your page in Firefox, choose the menu option File > Save Page As...
[*]When saving, choose "Web Page, complete". It will save the page as a *.html* file along with a folder.
[*]Zip both the file and the folder.
[/LIST]

The above method may not store the page properly.

An alternative is to install the Firefox add-on [Mozilla Archive Format, with MHT and Faithful Save]("https://addons.mozilla.org/en-US/firefox/addon/mozilla-archive-format/"). It allows you to save the page as a single file, usually properly. You can, if you wish, zip the resulting page, but it's not necessary.

---

### Post by Deborah277 on 2011-09-19
as long as u use firefox its very easy to store almsot anything on your local file system..   i m using it for almost any page i have to compress on my laptop. :)

---

### Post by rrsk on 2011-09-19
> **pretty_whistle said:**
> Right-click the main folder and choose 'compress'.  This brings up a smaller window where you can choose the compression type.  Click on where it says 'tar.gz' or whatever and you'll get a drop down menu with zip listed on it.  Choose zip.  Click 'create'.  You're done.
i want to store a webpage(including all links inside that site Eg:documentation) in a permanent storage.....

---

### Post by sakibmoon on 2011-09-19
Is it possible to save a complete website on my local disk? I want to save a complete site so that I can access the tutorials of that site even when I am offline. It is not possible to save every single page as there are thousands of pages on that site.

Let me know if it is possible?

---

