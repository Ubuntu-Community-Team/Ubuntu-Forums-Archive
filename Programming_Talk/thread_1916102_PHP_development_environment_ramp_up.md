---
title: "PHP development environment ramp up"
date: 2012-01-27
forum: Programming Talk
---

### Post by YigalB on 2012-01-27
What is the recommendation for a design environment for PHP on my Ubuntu machine?

I assume I would need:
1- Server. Probably mySQL & Apache.
2- PHP editor
3- Debug - how do I trace variables/break points etc

What would you recommend that would be easy to install and run?
I already have some code that can't wait to be used.


Thanks
Yigal

---

### Post by CoffeeRain on 2012-01-27
Yes. For a server, I would recommend XAMPP. It is very easy to use. This also installs and runs mySQL. For an editor, I use TextWrangler. It's basically a free version of BBEdit. It has multiple language support and changes colors so you know if you've misspelled something or left a quote open. I'm sure there are better editors though.

---

### Post by YigalB on 2012-01-27
Thanks.
How come I don't find XAMPP in Synaptic?
Will I be able to set breakpoints and trace variables values with TextWrangler or is just an editor?

---

### Post by MalcolmCowen on 2012-01-27
I'm interested in this issue.

I've been doing PHP development for several years, using the User Error Handler, which I have set up to test the IP Address and report PHP errors to the screen (if it is my IP address) or via email to me (if it's some other user).

This makes writing new scripts easier, because all my typos get displayed on my screen when I do a test run, complete with line nr and error text. And after I&#8217;ve released the site live, I also get notification of errors before even the client sees them, which makes me look good.   (I have a similar system for MySql errors).

Apparently because of security issues, the latest PHP builds (including Ubuntu) all seem to lock down user error handling, so all I get is a blank screen, or maybe an error 500. Then I have to download the error log (assuming it's available), and display the last few entries.  This is much more time consuming.

So I'd like to know what PHP Development Environment other people use?
Or is there a way round the User Error Handler lockdown?

---

### Post by Indie Media on 2012-01-28
To be sure you are up to date, install (L)AMP ( Apache, MySQL, PHP ).

---

### Post by YigalB on 2012-01-28
> **Indie Media said:**
> To be sure you are up to date, install (L)AMP ( Apache, MySQL, PHP ).
I have it all up and running.
I still don;t have an idea how to debug.

---

### Post by Indie Media on 2012-01-28
> **YigalB said:**
> I have it all up and running.
I still don;t have an idea how to debug.

Try Xdebug ( [http://xdebug.org/](http://xdebug.org/) ).

---

### Post by satanselbow on 2012-01-28
> **YigalB said:**
> Thanks.
How come I don't find XAMPP in Synaptic?


XAMPP is not in the repos as it installs a non standard configuration in non standard locations... hmmm... good a reason as any to do it properly ;)

Follow the Ubuntu community pages for LAMP ;)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

