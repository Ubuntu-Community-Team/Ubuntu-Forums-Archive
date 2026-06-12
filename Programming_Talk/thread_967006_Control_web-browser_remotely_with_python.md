---
title: "Control web-browser remotely with python"
date: 2008-11-01
forum: Programming Talk
---

### Post by alberto ferreira on 2008-11-01
1-My cell phone operator allows me to send 30 SMS freely per month. But I have to login in the site then fill the message and the recipient then press the submit button, then I'm redirected to another page and I have to press submit once again to authorize the sending of the message.

Is there a way in python to create a script that does this for me (asking only for the message and the recipient)?

2-I had once upon a time made a script in bash to download youtube videos but I had to manually input the URL in the script. Is there a way in python to find the current open pages in my web browser(firefox)?

I've seen the module **[COLOR=Teal]webbrowser[/COLOR]** but from what I understand it only allows you to open new pages, not find the ones that are already opened.

I would really appreciate your help,
Thanks

---

### Post by ghostdog74 on 2008-11-01
you need to use modules such as urllib2,urllib,httplib. Take a look at the docs to see how they are used to gather information from web pages.

---

### Post by alberto ferreira on 2008-11-02
Ok, I've searched in python's documentation and those libraries only allow me to retrieve data IF i know the URL, but i just want to know the current opened URL's in my web-browser so that I can then retrive the data.

Help!

---

