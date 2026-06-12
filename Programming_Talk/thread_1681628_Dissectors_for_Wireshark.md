---
title: "Dissectors for Wireshark"
date: 2011-02-04
forum: Programming Talk
---

### Post by Rodayo on 2011-02-04
So I want to write a dissector for wireshark that displays CDMI information for network traffic. Just to give you a rundown, CDMI works alongside HTTP. So essentially the headers for the request and response will have additional data related to CDMI that I want to display for the user.

I've been looking into it and it seems there are several different options for languages as the API is extensive. I found a guide for writing a simple one in C(which I'm not comfortable with)
[http://www.wireshark.org/docs/wsdg_html_chunked/ChDissectAdd.html](http://www.wireshark.org/docs/wsdg_html_chunked/ChDissectAdd.html)

Lua is another option and I understand wireshark has it's own lua interpretor. But apparently lua plugins will run slower(not sure why) and should be re-written in C once testing is done.

Python is another one. Personally I prefer either Lua or Python over C. I can tell now that if I were to embark on it with C there would be a lot of debugging involved and hair-pulling involved. 

So to put it formally: what should I be expecting as I move along on this project. And what language do you guys recommend I go with in order to write the plugin?

---

