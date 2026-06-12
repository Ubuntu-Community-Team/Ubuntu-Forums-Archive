---
title: "[SOLVED] Refresh PHP in Firefox?"
date: 2008-11-02
forum: Programming Talk
---

### Post by jesuisbenjamin on 2008-11-02
Hello Forum
Am working at learning PHP. I edit my index.php in /var/www/ with Gedit. 
After adding some data and lading the page, the page does not refresh even though i changed the script.:-k

How can i tell my browser to fetch fresh script?
Would this happen too if my page was on the web?

Cheers!

---

### Post by Delever on 2008-11-02
I used these headers in one of my pages:

[PHP]
<?php 
	header("Cache-Control: no-store, no-cache, must-revalidate"); // HTTP/1.1 
	header("Cache-Control: post-check=0, pre-check=0", false); 
	header("Cache-Control: private");
	header("Pragma: no-cache"); // HTTP/1.0
?>
[/PHP]

It should be executed before any text is printed.

Look at documentation if you need more info, I don't know why exactly those headers are like they are (found it using google (seriously, good tool, you may check it out)), I just know that it disables any caching.

Disable caching only if you need it: caching reduces server load significantly.

---

### Post by tom66 on 2008-11-02
Check Offline Mode. Strange, but sometimes in Firefox while I develop PHP using localhost, if I have no Internet connection, the page won't update, even after refreshing, it stays static.

---

### Post by jesuisbenjamin on 2008-11-03
Heeey i figured it out :)
Need to run ```
**sudo** gedit
```

#-o

---

### Post by LaRoza on 2008-11-03
You shouldn't be using root permissions to edit your personal files. I recommend having your work in your $HOME or somewhere and configuring apache to use that.

---

### Post by jesuisbenjamin on 2008-11-03
> **LaRoza said:**
> You shouldn't be using root permissions to edit your personal files. I recommend having your work in your $HOME or somewhere and configuring apache to use that.

Acch&#257;,

PHP tutorials tell me to place my file in /var/www/
I also have installed Apache and SQL but to be honest i have not 'seen' them and do not know how ton configure that.
Would you teach me how to do that? Or maybe you have a good link referring to this?

Thanks

---

### Post by LaRoza on 2008-11-03
> **jesuisbenjamin said:**
> Acch&#257;,

PHP tutorials tell me to place my file in /var/www/
I also have installed Apache and SQL but to be honest i have not 'seen' them and do not know how ton configure that.
Would you teach me how to do that? Or maybe you have a good link referring to this?

Thanks

/var/www is not in your $HOME. On *nix, permissions are important. Apache and MySQL are a server and a database server. Like everythink on *nix, you use files to configure them.

However, the easiest way to do this, if your set up is not a live server, but for testing and development would just to change the ownership of /var/www to be yours.

```

sudo chown -R $USER:$USER /var/www

```

This will make /var/www and its contents yours. I also suggest you read up on guides on using Apache and MySQL, they are not hard, and that knowledge is valuable.

---

### Post by jesuisbenjamin on 2008-11-04
> change the ownership of /var/www to be yours.
So basically it's not so bad if i use sudo but easier if i change ownership of /var/www/ ?
Can i not tell Apache directly to find the pages in whatever home folder i choose? Or does Apache ask Linux where to find the folder? In that case there are no alternative to what you just told me.

How come i cannot find Apache in my installed applications nor can i run anything called 'apache'?

I couldn't find much information on [www.apache.org](www.apache.org)...

...and i installed this a bit blindly to be honest. :oops:

---

### Post by LaRoza on 2008-11-04
> **jesuisbenjamin said:**
> So basically it's not so bad if i use sudo but easier if i change ownership of /var/www/ ?

Using sudo is bad in this case. Changing the ownership of /var/www/ is only advisable if this is only for testing, not production.

> 
Can i not tell Apache directly to find the pages in whatever home folder i choose? Or does Apache ask Linux where to find the folder? In that case there are no alternative to what you just told me.

You can configure apache using its configuration files. I suggesting reading tutorials on Apache for how to do this ;)

> 
How come i cannot find Apache in my installed applications nor can i run anything called 'apache'?

Because it is a daemon. It is automatically started.  That is why I suggested reading up on using apache ;)

Even if you did find it, it wouldn't be that helpful. (type "which apache" or "which apache2" in the terminal).

---

