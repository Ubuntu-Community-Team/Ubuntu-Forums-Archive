---
title: "Flex development on linux"
date: 2008-11-16
forum: Programming Talk
---

### Post by tinny on 2008-11-16
Hello

So my question / discussion point is this...

Who is developing Adobe Flex applications using Linux?

Im trying too. Ive become a big fan of the ease in which Flex allows you to develop attractive user interfaces, its REALLY easy!

Over the weekend I had a play with Adobe Flex builder for Linux (alpha).

[http://labs.adobe.com/technologies/flex/flexbuilder_linux/](http://labs.adobe.com/technologies/flex/flexbuilder_linux/)

Unfortunately the GUI designer isn't supported, but apart from this its was an enjoyable experience.

Are there any other useful Flex development tools out there for linux?

Anyone tried the Netbeans Flex plugin? 

[http://sourceforge.net/projects/flexbean](http://sourceforge.net/projects/flexbean)

---

### Post by tinny on 2008-11-18
bump

So no one else is developing Flex on Ubuntu...?

---

### Post by SeanHodges on 2008-11-19
Yes I am developing Flex in Ubuntu... Flex Builder is OK, but if like me you're not a fan of Eclipse, theres always Vim:

[http://ubuntuforums.org/showthread.php?t=742981](http://ubuntuforums.org/showthread.php?t=742981)

There are lots of threads in these forums for Flex development, it's well worth a search.

It's a good idea to test your movies in Gnash, to ensure they work for the free software crowd and people using 64bit Linux, OLPC laptops, FreeBSD, etc.

Regarding Adobe's Flash player, I assume you have the debug version of the Flash plugin? [http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz)

---

### Post by tinny on 2008-11-19
Thanks for your reply.

> **SeanHodges said:**
> Yes I am developing Flex in Ubuntu... Flex Builder is OK, but if like me you're not a fan of Eclipse, theres always Vim:


Actually I am quite a fan of Eclipse, but im actually waiting with bated breath for the Netbeans Flex plugin to mature. ([here]("http://sourceforge.net/projects/flexbean")) I like the Netbeans support for the Grails web application framework and I am planning on developing Flex UI's on Grails via BlazeDS.

If this sounds interesting here are more details...

[http://ubuntuforums.org/showpost.php?p=6194424&postcount=47](http://ubuntuforums.org/showpost.php?p=6194424&postcount=47)

> **SeanHodges said:**
> 
It's a good idea to test your movies in Gnash, to ensure they work for the free software crowd and people using 64bit Linux, OLPC laptops, FreeBSD, etc.


Yeah testing with Gnash is a good tip, thanks.

> **SeanHodges said:**
> 
Regarding Adobe's Flash player, I assume you have the debug version of the Flash plugin? [http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz)

I do now :-)

---

### Post by kb3lja on 2008-12-24
Are you doing it in 64 bit or 32 bit?
I am plan on trying it on a 64 bit.

---

### Post by Ruhe on 2008-12-24
The most intllijent java IDE provides **[support for flex development]("http://www.jetbrains.com/idea/features/javascript_editor.html#Flex-ready_intention_actions")**.
But only if you have license :(

2tinny
Do you like now the mxml syntax? ;)
I remembered our discussions about lack of swing, where I cited as an example the mxml.

---

### Post by tinny on 2008-12-25
> **Ruhe said:**
> 
2tinny
Do you like now the mxml syntax? ;)
I remembered our discussions about lack of swing, where I cited as an example the mxml.

Haha, yes I do like mxml. Its very productive and maps very nicely to a visual designer.

I guess im just anti XML in java. E.g. I spend A LOT of time doing spring wiring in XML. 

But now I can admit that "SwingXML" would be good.

FYI: [Groovy SwingBuilder]("http://groovy.codehaus.org/Swing+Builder")

---

### Post by tinny on 2008-12-25
> **kb3lja said:**
> Are you doing it in 64 bit or 32 bit?
I am plan on trying it on a 64 bit.

32bit (im using the Flex Builder alpha)

---

