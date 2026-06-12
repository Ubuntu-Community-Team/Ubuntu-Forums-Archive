---
title: "How do I use python to insert html?"
date: 2010-04-21
forum: Programming Talk
---

### Post by whackedspinach on 2010-04-21
I wrote a little python script for my blog sidebar to display last.fm recent tracks.  Basically, it sends an API requests, parses the returned XML, and then wraps the data in some html <li> elements so I can use css on them.  If I upload this to my server (CGI folder?, what should I put into my html script to execute the script and insert the returned html string from python?

---

### Post by whackedspinach on 2010-04-23
Here is what I have at the moment.  According to my webhost (webhostingpad) python is enabled on the sever.  I don't really know what they mean by that though.  I have that lastfmrecent.py script in my cgi-bin folder, since I assume it must be in python's sys.path.  I then put the following into my html, although I don't think it will work.

```
<div id="lastfm">
<% 
import lastfmrecent
get_recent_xml('whackedspinach', '8e7ae6fe7e1cdcffe0e8d8e68731270d', 5, "last_fm_cache.txt")
xml_to_html('last_fm_cache.txt') 
%>
</div>
```
What do you guys think I should do to make this work?

---

### Post by simeon87 on 2010-04-23
You should use the cgi module: [http://docs.python.org/library/cgi.html](http://docs.python.org/library/cgi.html) - I don't have experience with it but you could use: [http://www.python.org/doc/essays/ppt/sd99east/index.htm](http://www.python.org/doc/essays/ppt/sd99east/index.htm)

---

