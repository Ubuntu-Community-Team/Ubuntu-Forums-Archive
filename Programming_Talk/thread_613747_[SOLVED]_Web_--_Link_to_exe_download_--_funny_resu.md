---
title: "[SOLVED] Web -- Link to exe download -- funny result"
date: 2007-11-15
forum: Programming Talk
---

### Post by WinterWeaver on 2007-11-15
Hi guys, 

I created a website, and the client wants to have a windows executable as a download on his website.

On my local box, I click on the link and it does all the normal stuff to download the file.

However, when we have the site live, and click on the link, a page opens and just gives us tons of garbage text.

What is the reason for this, and how can I fix it?

Could it be happening because its a direct exe? Should we zip the file?

Any assistance would be great.

Thanks,

WW

---

### Post by Jussi Kukkonen on 2007-11-15
Sounds like a web site/host problem. Ask the admin to check mime types: often they're configured with MIME type "text/plain" for unknown content types... 
I'm guessing *"application/octet-stream exe"* is what should be added.

---

### Post by geirha on 2007-11-15
When a browser requests this exe file, the web server also sends with it some metadata explaining what type of file it is - the mime type. [http://en.wikipedia.org/wiki/Mime_type](http://en.wikipedia.org/wiki/Mime_type)

Sounds like your friend's server don't supply the correct mime type for the exe-file (which should be application/octet-stream I believe), and instead, the browser interprets it as a text-file apparently. Don't remember how to configure this properly, but it should give you an idea of what to look for in the configuration files.

---

### Post by LaRoza on 2007-11-15
Right click the link, and choose to download or save the file. It is a MIME issue, but no big deal.

---

### Post by WinterWeaver on 2007-11-15
Thanks for that explanation guys :)

I'll get in contact with the host and have a chat with them.

and in the process I learnt a bit more ^_^

Hope you all have a great day forward!! (or evening depending on your local time ;P )

WW

---

