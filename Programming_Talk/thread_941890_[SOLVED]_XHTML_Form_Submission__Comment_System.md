---
title: "[SOLVED] XHTML Form Submission / Comment System"
date: 2008-10-08
forum: Programming Talk
---

### Post by HOLOGRAPHICpizza on 2008-10-08
I am trying to make simple a web page that will allow people to fill out a text form and have it be appended to the end of a file on the web server, or have it posted on the page like a comment. Basically just any way for the information from the text field to get to me some how other than e-mail. It doesn't matter if other people read the stuff, I just want some way for text to go from the text box and on to my screen in any way, shape, or form.

I know basic XHTML, but have never done anything with forms. Can anyone help?

---

### Post by LaRoza on 2008-10-08
I wrote something like that, it is simple.

What language are you using?

It can be done with a simple form, a file to which the commments are appended that is included into a webpage. 

There should also be some sort of authentication. I wrote mine (code long gone) to use the IP address (it echoed it on the page and had to be entered into a text field for the form to accept the data, and had to match the IP of the submitter on the server).

---

### Post by HOLOGRAPHICpizza on 2008-10-08
I don't need any authentication what so ever, its only for my local LAN. I'm pretty good with XHTML but can use PHP or JavaScript if I need to. Can you post some sample code of what you used? Just getting the text to append to a file would be great.

---

### Post by LaRoza on 2008-10-08
> **HOLOGRAPHICpizza said:**
> I don't need any authentication what so ever, its only for my local LAN. I'm pretty good with XHTML but can use PHP or JavaScript if I need to. Can you post some sample code of what you used? Just getting the text to append to a file would be great.

PHP methods here.

Open and append to a file: [http://www.php.net/fopen](http://www.php.net/fopen)

Getting form submission: [http://www.php.net/manual/en/reserved.variables.post.php](http://www.php.net/manual/en/reserved.variables.post.php)

Including files: [http://www.php.net/manual/en/function.include.php](http://www.php.net/manual/en/function.include.php)

---

### Post by HOLOGRAPHICpizza on 2008-10-08
Thanks, I'll have to take a look at that stuff.

---

### Post by HOLOGRAPHICpizza on 2008-10-09
Thanks a lot! I have the whole system up and running smoothly now!:)

---

### Post by LaRoza on 2008-10-10
> **HOLOGRAPHICpizza said:**
> Thanks a lot! I have the whole system up and running smoothly now!:)

Thats great :-)

Glad to see that "read the manual" worked :-) (Although I didn't mean it that way...)

---

