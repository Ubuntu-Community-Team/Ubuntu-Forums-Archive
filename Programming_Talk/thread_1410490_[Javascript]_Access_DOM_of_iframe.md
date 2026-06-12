---
title: "[Javascript] Access DOM of iframe"
date: 2010-02-18
forum: Programming Talk
---

### Post by j.bell730 on 2010-02-18
Is it possible to modify an iframe's DOM on a webpage, using Javascript?
More specifically, I would like to add and remove elements from the iframe. I've tried a few methods, including...
```
document.getElementById('frameArea').getElementsByTagName('h1').parentNode.removeChild(document.getElementsByTagName('h1')[0]);
```
To try and remove a heading, but that didn't work. Is there something I'm doing wrong?

Also, I should probably mention that the iframe's src is an area on the user's hard drive (i.e. /home/username...it gives the user a prompt for where to navigate by default). Will this be a problem, as well?

---

### Post by jfparis on 2010-02-20
Did you check for error message in the browser console ?

If you use firefox then to tools > error console 
Then click on the clean button and reload the page/relaunch your script. If something is not working properly you should see some error message there.

Where does the first page come from? from a web server ?

I am afraid you might be running into some cross domain scripting limitation.

---

### Post by j.bell730 on 2010-02-21
> **jfparis said:**
> Did you check for error message in the browser console ?

If you use firefox then to tools > error console 
Then click on the clean button and reload the page/relaunch your script. If something is not working properly you should see some error message there.

Where does the first page come from? from a web server ?

I am afraid you might be running into some cross domain scripting limitation.

Thanks for the help...it returns null.
I've been reading around, and, it turns out, it's not even possible with Javascript.

Thanks again.

---

