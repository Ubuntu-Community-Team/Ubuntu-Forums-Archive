---
title: "Firefox problem loading page"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by richardselby on 2012-11-24
So it seems like every fifth time I try loading a page in Firefox, it tells me "problem loading page," even though I'm clearly connected to my wifi connection.

Help?

---

### Post by richardselby on 2012-11-25
This just happened when I tried to load [http://www.students.towson.edu](http://www.students.towson.edu)

```

XML Parsing Error: unexpected parser state
Location: jar:file:///usr/lib/firefox/omni.ja!/chrome/toolkit/content/global/netError.xhtml
Line Number 305, Column 54:        <div id="ed_netTimeout">&netTimeout.longDesc;</div>
-----------------------------------------------------^

```

---

### Post by richardselby on 2012-11-25
Can anyone help?

This same problem's popping up today.

---

### Post by richardselby on 2012-11-26
Help please?

The problem keeps happening =/

---

### Post by richardselby on 2012-11-27
I sometimes get those prompts, but other times, I get just Firefox telling me that it just cannot load the page

---

### Post by LuciferRex on 2012-11-27
Not trying to insult your intelligence, but did you try clearing cookies?

---

### Post by richardselby on 2012-11-27
> **LuciferRex said:**
> Not trying to insult your intelligence, but did you try clearing cookies?

Hey, good idea. I just tried that right now and I restarted my computer. I'll try seeing how this turns out.

---

### Post by richardselby on 2012-11-27
It's still having that problem again (kind of). It took me three tries to just load this forum and random pictures just don't load.

Awkwarrrrrrrrrrd

---

### Post by richardselby on 2012-11-27
Yeah, so I tried loading a website and this happened. Again.

```

XML Parsing Error: unexpected parser state
Location: jar:file:///usr/lib/firefox/omni.ja!/chrome/toolkit/content/global/netError.xhtml
Line Number 304, Column 68:        <div id="ed_connectionFailure">&connectionFailure.longDesc;</div>
-------------------------------------------------------------------^
```

---

### Post by wildmanne39 on 2012-11-27
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by Zelbo on 2013-02-24
Here's my file. 
Please help. I hope you can help. 
I cleared cache cookies, everything. 

Thanks so much.

---

