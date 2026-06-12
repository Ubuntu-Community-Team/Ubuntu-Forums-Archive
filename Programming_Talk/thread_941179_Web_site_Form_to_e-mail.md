---
title: "Web site Form to e-mail"
date: 2008-10-07
forum: Programming Talk
---

### Post by TreeFinger on 2008-10-07
Hello, I am working on a web site project and I am wondering what the best way to implement an 'e-mail form' would be.

Client would like a form on his web site that will just send a simple e-mail to his e-mail account.

What would be the best way to do this? Any tutorials some people could point me to?

I am not sure if the web site will be hosted on a windows or *nix box, not sure if that will make a difference.

---

### Post by tomchuk on 2008-10-07
You're going to need to figure out what the server supports first. perl, php, asp, etc. This is a fairly trivial script to write, but very hard to write in a secure fashion, a quick google for formmail should give you some background on that.

What ends up happening is if you don't handle user input correctly, you open the server up to all sorts of injection of mail headers. [This article](http://www.w3schools.com/php/php_secure_mail.asp) is probably a good starting point.

---

### Post by LaRoza on 2008-10-07
[http://allforms.mailjol.net/panel.php](http://allforms.mailjol.net/panel.php)

I just used that service after searching for my own needs.

It is free, no ads, and it is more flexible than most.

I designed the form myself, and just did the dialogs on that site.

---

### Post by TreeFinger on 2008-10-07
> **tomchuk said:**
> You're going to need to figure out what the server supports first. perl, php, asp, etc. This is a fairly trivial script to write, but very hard to write in a secure fashion, a quick google for formmail should give you some background on that.

What ends up happening is if you don't handle user input correctly, you open the server up to all sorts of injection of mail headers. [This article](http://www.w3schools.com/php/php_secure_mail.asp) is probably a good starting point.


Thank, you. My team was hoping to set up a test server for testing and when the web site was ready for production we would get a web host and upload the site there. What would be the most widely supported? PHP?

---

### Post by LaRoza on 2008-10-07
> **TreeFinger said:**
> Thank, you. My team was hoping to set up a test server for development and when the web site was ready for production we would get a web host and upload the site there. What would be the most widely supported? PHP?

You can use a service like I mentioned. You then don't have to worry about the language (as you just have the form's "action" set to what they tell you).

Naturally, you can find services that are not free and you get more features. The service I linked to is the best free one that I found.

The advantages of a service: 

[list]
[*] No configuring or hassle on your end
[*] Quite inexpensive (or free)
[*] They deal with the anti-spam measures
[*] Lets you focus on your site
[/list]

---

### Post by TreeFinger on 2008-10-07
> **LaRoza said:**
> You can use a service like I mentioned. You then don't have to worry about the language (as you just have the form's "action" set to what they tell you).

Naturally, you can find services that are not free and you get more features. The service I linked to is the best free one that I found.

The advantages of a service: 

[list]
[*] No configuring or hassle on your end
[*] Quite inexpensive (or free)
[*] They deal with the anti-spam measures
[*] Lets you focus on your site
[/list]

I am a little confused on how these e-mail forms work. They have to connect to an SMTP server, correct? Doesn't that require password access? Do we need to be looking at hosting providers that provide an SMTP server?

---

### Post by LaRoza on 2008-10-07
> **TreeFinger said:**
> I am a little confused on how these e-mail forms work. They have to connect to an SMTP server, correct? Doesn't that require password access? Do we need to be looking at hosting providers that provide an SMTP server?

No, that site for example, lets you configure it on their site, and gives you the form information, <form method="post" action="">

The action is what is unique and their server will use your settings.

So you don't have to do any coding at all. They even have a way to design the form there (and I presume it gives you the code) but I didn't want that.

So, you give it the email you want the information sent to and a few other preferences, and it does the rest.

---

### Post by TreeFinger on 2008-10-07
> **LaRoza said:**
> No, that site for example, lets you configure it on their site, and gives you the form information, <form method="post" action="">

The action is what is unique and their server will use your settings.

So you don't have to do any coding at all. They even have a way to design the form there (and I presume it gives you the code) but I didn't want that.

So, you give it the email you want the information sent to and a few other preferences, and it does the rest.

Well, we have many many members on this project and only one person designing the web site, so I'd like to have something for other people to do. PHP the best choice?

---

### Post by LaRoza on 2008-10-07
> **TreeFinger said:**
> Well, we have many many members on this project and only one person designing the web site, so I'd like to have something for other people to do. PHP the best choice?

If it is the best choice it is the best choice :-)

Hard to answer.

It would depend on what everyone knows and the requirements of the project.

It could possibly not require any scripting and just static xhtml.

PHP is not an optimal language, although it is widely supported and extremely popular.

---

### Post by TreeFinger on 2008-10-07
> **LaRoza said:**
> If it is the best choice it is the best choice :-)

Hard to answer.

It would depend on what everyone knows and the requirements of the project.

It could possibly not require any scripting and just static xhtml.

PHP is not an optimal language, although it is widely supported and extremely popular.

Well the deliverable for this project is just a simple way for users of a web page to send an e-mail to one specified e-mail address. Simpler, the better, of course :)

Client does not want the user to have to load up 'Outlook' or anything program outside the browser.

---

### Post by LaRoza on 2008-10-07
> **TreeFinger said:**
> Well the deliverable for this project is just a simple way for users of a web page to send an e-mail to one specified e-mail address. Simpler, the better, of course :)

Um, I could do that for any site, in about 10 minutes. 

(In fact, I just did, it was only by chance this thread came up again after I did it)

---

### Post by TreeFinger on 2008-10-07
> **LaRoza said:**
> Um, I could do that for any site, in about 10 minutes. 

(In fact, I just did, it was only by chance this thread came up again after I did it)

Well, I don't want to use that service you posted, if that is what you are talking about. Knowledge of what subjects is required for this simple e-mail from web page deliverable?

---

### Post by LaRoza on 2008-10-07
> **TreeFinger said:**
> Well, I don't want to use that service you posted, if that is what you are talking about. Knowledge of what subjects is required for this simple e-mail from web page deliverable?

Ok, you need a programming language (PHP is what I would use, because I know it best for this), and a mail server and a web server.

PHP has to be configured to use that server.

Exactly how depends on the servers being used.

That is just for sending mail.

You will also need validation and spam protection to prevent abuse.

---

### Post by TreeFinger on 2008-10-07
> **LaRoza said:**
> Ok, you need a programming language (PHP is what I would use, because I know it best for this), and a mail server and a web server.

PHP has to be configured to use that server.

Exactly how depends on the servers being used.

That is just for sending mail.

You will also need validation and spam protection to prevent abuse.

What do you mean by, "PHP has to be configured to use that server."?

The mail server, or the web server?

And do you mean the PHP script needs to be configured? Or the PHP installation on the server?

---

### Post by LaRoza on 2008-10-07
> **TreeFinger said:**
> What do you mean by, "PHP has to be configured to use that server."?

The mail server, or the web server?

The mail server. It will be using the same function regardless of the server being used.

The web server has to be configured to use PHP.

---

### Post by TreeFinger on 2008-10-07
> **LaRoza said:**
> The mail server. It will be using the same function regardless of the server being used.

The web server has to be configured to use PHP.

OK, so if I were to set up a test environment for this web site, I would need to set up an SMTP server for this to work? and then set up PHP to utilize that SMTP server?

---

### Post by LaRoza on 2008-10-07
> **TreeFinger said:**
> OK, so if I were to set up a test environment for this web site, I would need to set up an SMTP server for this to work? and then set up PHP to utilize that SMTP server?

Yes.

---

### Post by TreeFinger on 2008-10-07
> **LaRoza said:**
> Yes.

seems like this: [http://us3.php.net/mail](http://us3.php.net/mail) would be a good place to start, for me.

Thank, you. Seems like I opened a whole can of worms here, and I have trouble trusting some group mates to get anything accomplished. :)

---

### Post by haydnc on 2008-10-07
Sounds very much like a project I had to do at University. Sadly I can't help as I wasn't the one doing the mail-form... but it would certainly explain why you can't just use a webform off the net. Lecturers (also known as the client) just love it when they can make you re-invent the wheel.
:)

---

