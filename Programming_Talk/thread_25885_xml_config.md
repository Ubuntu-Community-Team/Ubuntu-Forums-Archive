---
title: "xml config"
date: 2005-04-11
forum: Programming Talk
---

### Post by oldmarti on 2005-04-11
Hi. I write a litle program for linux. I need a config file to load some options on start. I use rudeconfig ([www.rudeserver.com](www.rudeserver.com)) but source is closed ;-). In Gnome xml config files are very popular. Where  I can find some info or examples, how to make a simple xml config file? A xml editor or/and other tools will be very usefull. Thanks

---

### Post by Goshawk on 2005-04-11
Hi.. the team in which i'm in have wrote a xml parser in c++ (tiny and fast it seems) i can share the sources.
BUt let me explain what a xml file is:
A xml file is a file where informations are stored in tags (like html). In these files programmers can define their own tags then a program can read these tags and get configuration. see [http://www.w3schools.com/xml/xml_whatis.asp](http://www.w3schools.com/xml/xml_whatis.asp) for more details..
a simple xml file example is:
<?xml version="1.0" encoding="ISO-8859-1"?>
<note>
<to>Tove</to>
<from>Jani</from>
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>

You have to choose the name of the tag.

The parser that we wrote uses c++ objects example:

xml_parser configuration("path-of-the-file");
configuration.read("name-of-the-tag--it-can-be-also-a-main-tag");
then the call:
configuration.get("tag"); will return his string value and
configuration.get_int("tag") will return his int value..

say me if you want the sources.

---

### Post by oldmarti on 2005-04-11
Thanks. I'll be happy to take a look on source code. My e-mail: [email]oldmarti@mail.bg[/email].
And what about a creation and modification the config file? Need to write another program or use text editor (like vim)?

---

