---
title: "How to install Apache ?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-02
Hi all,
How to install Apache ? May I configure file or text ?

---

### Post by SunnyRabbiera on 2008-05-02
you asked something similar, this is not a chatroom you know...
same thing as i suggested in your other thread, use synaptic.

---

### Post by tamoneya on 2008-05-02
have you tried stuff like this
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5)
If something there fails post the error message as best you can.

---

### Post by Zeck on 2008-05-02
> **tamoneya said:**
> have you tried stuff like this
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5)
If something there fails post the error message as best you can.

Thanks. It very helps for me.

SunnyRabbiera sorry i don't do it again. 


Regards,
Zeck

---

### Post by MaindotC on 2008-05-02
SunnyRabbiera if he does not Apache to install he may be execute!  Chenquieh!

---

### Post by Zeck on 2008-05-07
Good morning | afternoon | evening.
I have problem. I installed apache but it not work. So where can i found apache file ? And how to install it ? I'm just beginner.

---

### Post by hyper_ch on 2008-05-07
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by mmarif4u on 2008-05-07
Or can try this:
I compile a simple tutorial on my blog, how to do it.

[Link to tutorial]("http://anl4u.freeweb7.com/blog/index.php?cat=19")

Hope it will help more.

---

### Post by Zeck on 2008-05-07
Hi all,
I'm just newbie for Ubuntu. I want to workin terminal with apache. Where can i get impormation ?

---

### Post by tamoneya on 2008-05-07
im not exactly sure what you are asking for because apache doesnt really run inside terminal. I am guessing that you want a server that is running apache and that you have terminal access to.  Just use the ubuntu server CD.  It will give you CLI as well as an apache server to play with.  If this isnt what you were looking for be more descriptive and I would be glad to help you out.

---

### Post by Zeck on 2008-05-07
> **tamoneya said:**
> im not exactly sure what you are asking for because apache doesnt really run inside terminal. I am guessing that you want a server that is running apache and that you have terminal access to.  Just use the ubuntu server CD.  It will give you CLI as well as an apache server to play with.  If this isnt what you were looking for be more descriptive and I would be glad to help you out.

It's meaning for example how to start, stop, restart apache on terminal, etc.

---

### Post by mmarif4u on 2008-05-07
U already post a thread here:
[http://ubuntuforums.org/showthread.php?t=785077](http://ubuntuforums.org/showthread.php?t=785077)

please dont post same thread again.
Thanks

And read the replies there.
All what you want is here:
[Link]("http://anl4u.freeweb7.com/blog/index.php?cat=19")

---

### Post by Xiong Chiamiov on 2008-05-07
As described in [the documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP"), /etc/init.d/apache2 stop (or start or restart).  You'll have to sudo it as well.

EDIT: I almost feel I should remove the answer, since the documentation's been given to you 45 minutes ago when you asked the first time.

---

### Post by tamoneya on 2008-05-07
```
 sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/apache2 stop

```

---

### Post by Zeck on 2008-05-07
Thanks for your all advice. 
I have again one problem. I download apache source. Then extract it. So how can i install it ? Any idea ?

---

### Post by hyper_ch on 2008-05-07
why don't you install apache from the repos?

---

### Post by Zeck on 2008-05-07
> **hyper_ch said:**
> why don't you install apache from the repos?

I don't wont to it. Because I want to know it.

---

### Post by tamoneya on 2008-05-07
if you want to learn stuff you could start by searching the forums and by reading the install notes inside the tar.gz.  There are many forum posts about installing from source.  The idea of the forum is that people can learn from other peoples problems.

---

### Post by Xiong Chiamiov on 2008-05-07
[How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/"), specifically [from source]("http://monkeyblog.org/ubuntu/installing/#source")

---

### Post by mapes12 on 2008-05-07
Install the server edition of ubuntu. Running Apache with a GUI X server has inherent security risks. Checkout this [comprehensive guide]("http://www.aboutdebian.com/internet.htm").

---

### Post by Xiong Chiamiov on 2008-05-07
Unless, of course, you're just using it for web development, like I am.

With this OP, though, who knows.

---

### Post by Zeck on 2008-05-08
Good morning | afternoon | evening !
Hi, I have a prime problem. My apache not work. When i starting apache it was a error. Then next I tring to call localhost. But again error. So i checking my installs. Then i want to remove it so it is not removed. Please show my attached files. Any idea ?


Regards
Zeck

---

### Post by Monicker on 2008-05-08
The message about the fully qualified domain is to be expected in your case, and will not prevent apache from running; and as you can see, it still says "OK".  As for Firefox, I would imagine the problem is that shows as being in offline mode.  Put it back in online mode.

I don't know why apache is showing as not installed when you try to remove it.  Did you install it via Synaptic?

---

### Post by Zeck on 2008-05-08
Good morning | afternoon | evening !
Hi, I have a private problem. My apache not work. When i try starting apache it was a error. Then next I trying to call localhost. But again error. So i checking my installs. Then i want to remove it so it is not removed. Please show my attached files. Any idea ?


Regards
Zeck

---

### Post by Zeck on 2008-05-08
> **Monicker said:**
> The message about the fully qualified domain is to be expected in your case, and will not prevent apache from running; and as you can see, it still says "OK".  As for Firefox, I would imagine the problem is that shows as being in offline mode.  Put it back in online mode.

I don't know why apache is showing as not installed when you try to remove it.  Did you install it via Synaptic?

No, I'm just using terminal. I'm just newbie. And Could you give me advice for how can i full remove apache ?

---

### Post by DrPppr242 on 2008-05-08
I'm not entirely sure but I think apache2 doesn't come with any vhost on by default, you might try wither doubling checking your httpd.conf and virtualhosts.d/ files, or installing apache (or httpd) which in my opinion is a little easier to deal with

---

### Post by tamoneya on 2008-05-08
post the result of ```
ls /var/www/
``` It is normal for apache to complain about not finding fully qualified domain names.  It does that to me all the time.  I think your problem is that you do not have an index.html or index.php.  Have you changed your apache root by chance?

---

### Post by Zeck on 2008-05-08
> **tamoneya said:**
> post the result of ```
ls /var/www/
``` It is normal for apache to complain about not finding fully qualified domain names.  It does that to me all the time.  I think your problem is that you do not have an index.html or index.php.  Have you changed your apache root by chance?

Yes I changed my apache webroot. How to restore my webroot ? Could you teach me  step by step ?

---

### Post by tamoneya on 2008-05-08
i already am in a different thread.

---

### Post by hyper_ch on 2008-05-08
Just out of curiosity:

Have you tried to research any of those things you ask yourself and find an answer for it? And if so, how did you try to research it?

---

