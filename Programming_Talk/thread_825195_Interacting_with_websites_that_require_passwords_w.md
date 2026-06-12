---
title: "Interacting with websites that require passwords with Python"
date: 2008-06-10
forum: Programming Talk
---

### Post by GammaPoint on 2008-06-10
I was curious. I know that Python can easily access web sites through the urllib module. But can Python also access websites that require a password? For example, would be be possible to write a Python script that entered my password for the Ubuntuforums.org website, then 'clicked' on 'User CP'(perhaps by simply visiting [http://ubuntuforums.org/usercp.php](http://ubuntuforums.org/usercp.php) after it had logged in?), and then grabbed some information off of that and emailed it to myself? I don't actually need to do the above mentioned thing, just using it as an example. 

Thanks.

---

### Post by Wybiral on 2008-06-10
> **GammaPoint said:**
> ...

Yes. Find the form on the site, it will have all of the input fields that you need to submit to the server. Then use the request functions from urllib, most likely a POST request ([see here]("http://docs.python.org/lib/node577.html")) to fill in the fields. Then you'll want to see where the action on the form is taking you, and send the request there. Then use a module like BeautifulSoup to parse the HTML.

---

### Post by GammaPoint on 2008-06-10
Thanks for the feedback Wybiral.  I don't need to do this now but wanted to have a general idea of how it could be done.  I've also found a section using some of these ideas in the book Programming Python that will help as well.  I just didn't know what to look for before you posted :)

---

