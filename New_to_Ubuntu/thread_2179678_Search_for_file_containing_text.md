---
title: "Search for file containing text"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by deleyd-y on 2013-10-09
How do I search the whole hard drive for a file name, containing a certain text word? e.g. search for all "index.html" containing "xyzzy".

I tried installing: "sudo apt-get install gnome-search-tool"

The instructions then said, "[COLOR=#333333][FONT=UbuntuRegular]Open [/FONT][/COLOR]Search for files[COLOR=#333333][FONT=UbuntuRegular] select [/FONT][/COLOR]Select More Options"
and I've no idea how to do that.

---

### Post by steeldriver on 2013-10-09
You don't need to install any special tools - the standard 'find' and 'grep' command line utilities will do that for you e.g.

```
find / -name 'index.html' -exec grep -H 'xyzzy' {} + 2>/dev/null
```

The '2>/dev/null' is not essential, it just stops the output getting buried in lots of permission errors. If you think the file may be somewhere an ordinary user does not have read access you can run it with 'sudo'

```
sudo find / -name 'index.html' -exec grep -H 'xyzzy' {} + 
```

You can also make the grep case insensitive (-i) and/or restrict it to complete word matches (-w) - type **man grep** for more info

---

