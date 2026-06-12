---
title: "how to understand the structure of system files in linux?"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by pipo98 on 2013-01-18
I'm interested in learning the bowels of linux and I want to learn how the content of system files are structured. For example, /usr/share/applications/defaults.list.

I want to open .html files with sublimetext instead of chrome. So I opened defaults.list with gedit and looked for lines with html. I find things like:

text/html=sublime.desktop
application/xhtml_xml=google-chrome.desktop
application/xhtml+xml=firefox.desktop
text/xml=firefox.desktop;google-chrome.desktop
Now I could guess what it all means, but I want to read what, for example, the following means:

what do the item before and after the / mean, e.g. text/html. What does text refer to, and what does html refer to?
In the previous case it is easy to see html just refers to the extension .html, but what about in the case of xhtml+xml? What does the + here do? Why not break it into 2 lines?
Finally, what does the semi-colon ; mean in firefox.desktop;google-chrome.desktop?
As I said, my question is on two levels:

What do these mean in this particular case (defaults.list)
In general, where can I find the documentation for how system files are structured? Let's say I also want to understand how /etc/network/interfaces works - where would I get an authoritative documentation of this file, other than random googling and reading from forums?
Thank you,

Dhaval

---

### Post by lykwydchykyn on 2013-01-18
1.  These things (text/html, e.g.) are what are known as MIME types.  See:

[http://en.wikipedia.org/wiki/Internet_media_type](http://en.wikipedia.org/wiki/Internet_media_type)

2. The semicolon is just a delimiter for the list of applications associated with the MIME type.  So if one is not installed, the next one can be used, etc.

3. Often, "man" will give you information on config files, for example, the command:
```

man interfaces

```
Will show the man page for the /etc/network/interfaces file.  Of course, you can view man pages in nautilus as well, if memory serves.  Try directing it to "man:interfaces"

---

### Post by pipo98 on 2013-01-18
> **lykwydchykyn said:**
> 1.  These things (text/html, e.g.) are what are known as MIME types.  See:

[http://en.wikipedia.org/wiki/Internet_media_type](http://en.wikipedia.org/wiki/Internet_media_type)

2. The semicolon is just a delimiter for the list of applications associated with the MIME type.  So if one is not installed, the next one can be used, etc.

3. Often, "man" will give you information on config files, for example, the command:
```

man interfaces

```
Will show the man page for the /etc/network/interfaces file.  Of course, you can view man pages in nautilus as well, if memory serves.  Try directing it to "man:interfaces"
great, thank you. 

man interfaces works but not man defaults.list. in genera, if I wanted to find the documentation for defaults.list, where would I start?

Thank you for the link to MIME types. How did you learn about that? Aka where did you read about that?

thank you again!

---

### Post by Bashing-om on 2013-01-18
pipo98; Hi !

Documentation on the net is overwhelming. There exist lots of sources.
For example:
[http://articles.techrepublic.com.com/5100-10878_11-1047531.html](http://articles.techrepublic.com.com/5100-10878_11-1047531.html)
[http://www.er.uqam.ca/nobel/r10735/unixcomm.html](http://www.er.uqam.ca/nobel/r10735/unixcomm.html)
[https://help.ubuntu.com/community/Glossary](https://help.ubuntu.com/community/Glossary)
[http://ubuntulinux.co.in/community/index.php](http://ubuntulinux.co.in/community/index.php)
[http://tldp.org/HOWTO/Text-Terminal-HOWTO.html](http://tldp.org/HOWTO/Text-Terminal-HOWTO.html)
[http://www.reallylinux.com/](http://www.reallylinux.com/)

My rule od thumb ---follow your curiousity !

---

### Post by lykwydchykyn on 2013-01-19
> **pipo98 said:**
> great, thank you. 

man interfaces works but not man defaults.list. in genera, if I wanted to find the documentation for defaults.list, where would I start?


Honestly, I haven't the foggiest, apart from search engines and so forth.  You might start by using the 'dpkg -S filename' command to find out what package it's in, then seeing if that package ships any documentation.

> 
Thank you for the link to MIME types. How did you learn about that? Aka where did you read about that?

thank you again!

Don't really remember, but since I do web development it probably came about through the course of learning this.  MIME types are used by browsers and email clients to appropriately handle downloaded/attached content.

---

### Post by bab1 on 2013-01-20
> **pipo98 said:**
> ... man interfaces works but not man defaults.list. in genera[l], if I wanted to find the documentation for defaults.list, where would I start?

I think it best to first understand that Linux is really just the kernel.  Ubuntu is the distribution that includes the Linux kernel and the selected tools and applications.  The OS is not monolithic like WIndows.

So, with that in mind I found the defaults list at /etc/gnome/defaults.list.  This tell me that it is a configuration file for the desktop environment of GNOME.  

If I'm correct then the the GNOME desktop project documentation is not in the man pages but might be found at [[COLOR="Blue"]_http://library.gnome.org/users/_[/COLOR]]("http://library.gnome.org/users/").  Be advised the documentation is frustrating to go through and most likely you wont find what you are looking for easily.  Obscure references are the norm there.

---

