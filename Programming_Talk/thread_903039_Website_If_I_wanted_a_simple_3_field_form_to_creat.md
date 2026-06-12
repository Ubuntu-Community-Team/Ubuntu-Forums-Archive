---
title: "Website: If I wanted a simple 3 field form to create a text file, could you help?"
date: 2008-08-27
forum: Programming Talk
---

### Post by ddixonr on 2008-08-27
I have been a member of these forums for a while now, and everyone has been very helpful. I probably wouldn't still be using Ubuntu if it wasn't for this valuable resource. With that said, here's my request: (skip next paragraph for actual question)

Very simple website coded in plain old html. All static pages of course with nothing fancy. I have done my best to make it look professional, but informal. My need to learn new things constantly grows, and while programming classes are to be attended soon. I'd like to keep it simple for as long as I can.

**Can I create a simple three field form (Name, Email, Message) to place on a web page that will create (and save) text files with the information for each visitor who completes it?**

Keep in mind, I have tons of PC troubleshooting skills, but no programming experience whatsoever. If it isn't absolutely required, or end with -pache, assume it is not installed or configured yet. Thanks.

---

### Post by kjohansen on 2008-08-27
this can be done in so many lanauges.  if you are using apache the most common choice would probably be PHP. 

if you decide on a language and get it installed on the server the php you would need to learn to do this would be minimal.

---

### Post by ddixonr on 2008-08-27
Could you, or anyone else, point me in the right direction for clear and easy to understand directions?

---

### Post by Reiger on 2008-08-28
Oh yes:

If you want to do it in PHP:
W3C schools;
PHP manual.

Can be easily retrieved with a Google search: "PHP manual" and "W3C schools PHP" should retrieve those.

You'd be looking for:
A) Installing PHP with your webserver;
B) (X)HTML forms
C) Explanation of the $_POST & $_GET superglobals
D) PHP's functions that handle file I/0.

EDIT: Myself, I only use the PHP manual but if you're doing stuff in (X)HTML (which you will be) and you don't know that yet you will find the W3C schools a lifesaver, methinks.

---

### Post by Zugzwang on 2008-08-28
> **ddixonr said:**
> Could you, or anyone else, point me in the right direction for clear and easy to understand directions?

Ok, the point here is: This *cannot* be done using simple static web pages. There has to be some kind of dynamic language support installed on the web server yours pages are on. And how to solve this depends on what is installed.

Look out for the following buzz-words when examining your web space:
**cgi-bin, perl, PHP, asp, jsp** Less commonly used are **Python** and **ruby**. 

If your web hoster just provides static web-hosting without frills, you will need to look somewhere else to get this support.

After you got the answer to this question, we can point out what to do next (it depends on the answer).

---

