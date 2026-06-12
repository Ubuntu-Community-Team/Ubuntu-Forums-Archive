---
title: "Postfix making website for e-mail..."
date: 2008-05-11
forum: Programming Talk
---

### Post by hockey97 on 2008-05-11
Hi I am working on right now on making my own webpage that will grab the user's e-mail is this possible with php??

I don't even know if my postfix really works. I have tested it I could send mail from like aol to my e-mail server postfix but I can't send e-mail to aol servers ect.

How would I go abouts doing this??

---

### Post by CptPicard on 2008-05-11
What do you mean by "grabbing user's e-mail"?

I don't get what you're trying to do ...

---

### Post by hockey97 on 2008-05-11
ok I tested my postfix server it'a all config right and is working but I am being blacklisted in aol,msn hotmail ect. I got a link which is here: [http://postmaster.info.aol.com/errors/554rtrsc.html](http://postmaster.info.aol.com/errors/554rtrsc.html)

Other than that it's good.


What I want to do is make my own webpage for my users to go onto to check their e-mails in their mailbox.

I plan to give a free e-mail services to my users. I want to make my own webpage to display the user mail and also they can send e-mails to other people, but I want it to be created by mean so I can control every the art/looks of the page and also certain functions and be able to quickly plug-in new anti-virus/anti-spam codes or programs to run on all E-mails that are sent to my e-mail server.

---

### Post by slavik on 2008-05-11
squirrelmail

---

### Post by hockey97 on 2008-05-11
ya I know about squirrelMail  but it dosen't give off a professional look to it.

I want the theme of my website the smoothly intergrate into the e-mail page.

My website theme is cold and icy ect so I want it to have an icy look in the e-mail area.

with squirrelmail it gives off an image that you made a website yourself but then the e-mail system you grab something else and makes it look ulgy.

it's kinda like having one room  half wallpapered with bunnies and the other half wallpapered with toy airplane designs. 

Basicly what I am saying that squirrelMail has it's own looks and theme and to use that with my website gives off 2 different designs causing it look like a cut and paste look.

I am trying to make it look professional so I am saying can you imagine if aol or msn hotmail  used squirrelmail for there e-mail services, it would look horriable.

I know php I am good at php now, and I am starting to learn javascript. I know css and html good.

So I was woundering, postfix has folders of each user that uses my postfix mail can I using php  grab those folders or make a search action that when the user is opening their mail page then I would display a loading bar and  with php use some function to  grab all files that are in that folder which would be the persons e-mails that got sent to that user.

---

### Post by hockey97 on 2008-05-11
Ok I read the hotmail and aol stuff, I found later that my postfix server dosen't have the SMTP-AUTH setup properly, once I do so I will be able to send e-mail to aol, hotmail users ect.

any good place that is up to date that can give me a step to step setup  of postfix to make SMTP-AUTH be setup  in the right way.

I have generated a key a while back and so I guess I will have to start all over on getting SMTP-AUTH to be setup right.

I need some help on how to do this.

---

### Post by hockey97 on 2008-05-12
aol website refered me to a company that provides a black list of ip address which mine is on a plc or somthing like that which is normal any residential ip address is on that list.

What the company said to do to fix this is to use SMTP-AUTH  and if you have it then it must be configured wrong.

Do any of you guy's know how I can config postfix to use SMTP-AUTH  correctly???

---

### Post by hockey97 on 2008-05-12
Hi I just followed this tutorial: [http://flurdy.com/docs/postfix/#conf_auth](http://flurdy.com/docs/postfix/#conf_auth)

all the way down to the header Authentication 

I followed those steps.

The only thing I skipped was  the command used in the terminal which is this:

cd /etc/postfix openssl req -new -outform PEM \ -out postfix.cert -newkey rsa:2048 -nodes -keyout postfix.key -keyform PEM -days 999 -x509


I did try it but I get an error saying unknown -out option.

I made a key and a certificate before and had that laying around so I used those instead.

in the sasl configuration I don't understand why I had to put : sql_engine: mysql sql_hostnames: 127.0.0.1 sql_user: mail sql_passwd: apasswd sql_database: maildb sql_select: select clear from users where id='%u@%r' and enabled = 1

would courier or postfix be using mysql for information???

---

### Post by WW on 2008-05-12
> **hockey97 said:**
> 
The only thing I skipped was  the command used in the terminal which is this:

cd /etc/postfix openssl req -new -outform PEM \ -out postfix.cert -newkey rsa:2048 -nodes -keyout postfix.key -keyform PEM -days 999 -x509


I did try it but I get an error saying unknown -out option.

Take out that extraneous backslash.  I suspect the tutorial has it in there to indicate that the command is continued on the next line, but then I don't understand why the next line doesn't also have one.

Your error was probably "unknown_option__-out" and not "unknown_option_-out" (I used underscores where the spaces should be.)  By putting in the extra backslash, you 'quoted' a blank, so the openssl command saw the argument as "_-out" instead of "-out".

So the commands should be:
```

cd /etc/postfix
openssl req -new -outform PEM -out postfix.cert -newkey rsa:2048 -nodes -keyout postfix.key -keyform PEM -days 999 -x509

```

---

### Post by slavik on 2008-05-13
you can customize squirrelmail. I used this guide ([http://workaround.org/articles/ispmail-etch/](http://workaround.org/articles/ispmail-etch/)) to set up a mail server for my college club.

---

### Post by hockey97 on 2008-05-13
Thanks for the tutorial. It will come handy if I plan to go that route.

I really want to know how I can talk to postfix and make it send values to like php or javascript so I can create my own effects and looks.

The reason I want to do this is to have more control over my website.

I have my own server and made my own webpages I have bought 2 domain names which only that so far I lost control over.

the more I depend on others software the more uncontrollable I get have.

becuse most people uses squirl mail and if a hacker learns the structure of squirl mail and then finds a way to hack into it you get what I am going at.

I am currently usin md5 encryption for passwords but after all this I will create my own algorithm for it so it would be harder to hack.

So thats why I want o really do anything that is on my website or is a service so even if I do get hacked It would still be easy enough that I would know what to do ect.

Is there any programming lango that will help me talk to postfix and also php or javascript?

I am also still on that one list that prevents me from e-mailing aol users.

but aol users can e-mail me. So I have no trouble with getting mail it's just the sending part to well-known companies.


I know for  a fact that if I can get postfix to use the mysql database it would make this much easier.

---

### Post by CptPicard on 2008-05-13
You're doing it wrong...

> **hockey97 said:**
> 
the more I depend on others software the more uncontrollable I get have.

The more you depend on others' software the less work you have to do yourself and the more certain you can be that bugs have been worked out already. The more eyeballs there are looking at and using some codebase, the better it gets over time.

You're better off putting your time into learning those other pieces of software instead of rolling your own, which is a much harder proposition. Now, I just get the feeling that you feel things are getting uncontrollable because you just don't understand those pieces of software you're using...


> becuse most people uses squirl mail and if a hacker learns the structure of squirl mail and then finds a way to hack into it you get what I am going at.

This is the "[security through obscurity]("http://en.wikipedia.org/wiki/Security_through_obscurity")" argument that Microsoft for example has been pushing. It doesn't work that way. Security systems must be secure by their own merits against an adversary that has access to the source. Otherwise you'll just never know where the attack is going to come from.


> I am currently usin md5 encryption for passwords but after all this I will create my own algorithm for it so it would be harder to hack.

I suppose you've got a PhD in math and have published quite a lot in Cryptography and will be able to stand a lot of peer review from mathematicians who are going to pick apart your hash algorithm?


> So thats why I want o really do anything that is on my website or is a service so even if I do get hacked It would still be easy enough that I would know what to do ect.

Ok, if it's so easy, I'm watching with interest... :popcorn:


> I know for  a fact that if I can get postfix to use the mysql database it would make this much easier.

[First hit on Google for "postfix mysql"]("http://www.google.fi/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.postfix.org%2FMYSQL_README.html&ei=jcQpSL7tJ5PcQs3byZEK&usg=AFQjCNG5BFRuBiOtr8ZvVni21W7C0dHO2A&sig2=UQcwSEAcRDIEdbxLm1ssEA").

EDIT: The recent [Debian OpenSSL bug]("http://www.debian.org/security/2008/dsa-1571") is a great example of what happens when you start soloing with cryptosystems.

---

### Post by hockey97 on 2008-05-13
ok I been folling this tutorial [http://small.dropbear.id.au/myscripts/postfixmysql.html](http://small.dropbear.id.au/myscripts/postfixmysql.html)

I done everything but I didn't quite understand the mysql part I don't know that part. I tried to make postfix use mysql and did follow the one you posted but it failed, I got errors and I was not able to send or recieve mail so I did the default setup and I can get mail and send mail but I can't send mail to wellknown compaines like aol. It's becuse my smtp auth is not config right.

I would like to get postfix using mysql for the username and password and also the users e-mail address. So I can use that for smtp auth  as the database.

I tried many tutorials even the one you gave which is right from the website postfix.

---

