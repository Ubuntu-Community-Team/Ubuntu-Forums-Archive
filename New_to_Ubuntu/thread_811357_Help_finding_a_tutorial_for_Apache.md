---
title: "Help finding a tutorial for Apache"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by madu on 2008-05-29
Hello,

I need to find a tutorial for Apache on for Hardy Heron. All the tutorial I find on web ask for installation of the server edition.
I have already installed and working happily on a 8.04 system and want to install Apache on that.

I dont need PHP or MySQL since, at the moment, I only want to have some static HTML files. This is only for educational purposes so I dont need a complicated system.

Can somebody give me a guide that explains from installing Apache to hosting a few HTML files...
Security is also a big issue since I am not a Linux/Server geek I need some help in that department too..

Thank you heaps.

---

### Post by kesman on 2008-05-29
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5)

This is for Gutsy but works with Hardy too. Only install apache and then open [http://localhost](http://localhost) in browser to see it working.

You might need to open port 80 in your router for other people to see your server too.

/etc/apache/ has all the configuration files for apache, including the directory for your .html -files that you would like to be visible trough the server.

---

### Post by MaindotC on 2008-05-29
You can install apache by typing:
```

sudo apt-get install apache2

```
The file that contains the configuration is in /etc/apache2.conf and it is VERY well documented so you should be able to configure it following the directions in the conf file.  It's very long and some of the terms may be difficult to understand - just google them.  The file that is displayed when apache is running is in /var/www/apache2-default/index.html.  You can actually change this in the configuration file to whatever directory you want.

Once you install apache, you can see this file by starting apache:
```

/etc/init.d/apache2 start

```
Open a browser, type in the address bar "localhost" and press enter.  You should see the default web page.

---

### Post by kesman on 2008-05-29
also [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop)
this would be worth to check

---

### Post by iaculallad on 2008-05-29
You could also try visiting [Apache's documentation site]("http://httpd.apache.org/docs/"). Site includes User Guide and HowTo's.

---

### Post by MaindotC on 2008-05-29
> **kesman said:**
> also [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop)
this would be worth to check

He doesn't know how to install apache, let alone configure it, and you want him to install lamp? Did you just want to up your post count?

---

### Post by madu on 2008-05-29
Thanks a million everybody!
I guess /etc/httpd.conf is the best way to do.

Just one worry.
Suppose I install Apache and start it..do I have to take any security measures..?
Will my system be vulnerable once I started Apache? 
I mean would Apache serve files other than the one in the /var/www/apache2-default/ folder..?

Thank you.

---

### Post by kesman on 2008-05-29
> **strAlan said:**
> He doesn't know how to install apache, let alone configure it, and you want him to install lamp? Did you just want to up your post count?

Huh? I think LAMP is a package that has it all, including apache. It also comes with a web-based configuration tool for apache, which is good for starters.

---

### Post by MaindotC on 2008-05-29
Ideally apache will only serve the files in that directory.  Now someone like me who has taken a few security classes and whip out netcat or fluxay and have some fun but you're not serving anything more or less than the billion other web servers on the internet.  Kesman was going to have you install other programming environments that would have opened up more ports and services, but the main thing someone would need to really take over your system would be the root password.

Long story short, I advise you from my experience that you're fine.

---

### Post by iaculallad on 2008-05-29
> **madu said:**
> Thanks a million everybody!
I guess /etc/httpd.conf is the best way to do.

Just one worry.
Suppose I install Apache and start it..do I have to take any security measures..?
Will my system be vulnerable once I started Apache? 
I mean would Apache serve files other than the one in the /var/www/apache2-default/ folder..?

Thank you.

Nope, you don't have to worry on security measures. Options for that will be configured by you using config files and not Apache.

---

### Post by MaindotC on 2008-05-29
> **kesman said:**
> Huh? I think LAMP is a package that has it all, including apache. It also comes with a web-based configuration tool for apache, which is good for starters.

I know what lamp is. First off, his post lead us to believe he doesn't know how to install it and configure it.  Secondly, he said he didn't want anything deep, just the web server apache.  Third, if you look at his most recent post he's concerned about security from installing a web server.  No disrespect to OP, but those of us in the community would kind of chuckle at that type of question - it's cool just funny to us.

He doesn't need to install more than he wants.  He asked for a web server and how to install it so I advised him as such - not php, not mysql.

---

### Post by iaculallad on 2008-05-29
> **kesman said:**
> Huh? I think LAMP is a package that has it all, including apache. It also comes with a web-based configuration tool for apache, which is good for starters.

Actually, LAMP stands for Linux,Apache,MySQL,(Perl,Python,and PHP). Madu only needs to know about Apache so Madu does not need those extra packages for now.

---

### Post by madu on 2008-05-29
Thank you again guys!
Not needing any additional security configurations is a relief.

So it is recommended to create a new account to run Apache I guess..?

Thanks again fellows!

---

### Post by MaindotC on 2008-05-29
> **iaculallad said:**
> Nope, you don't have to worry on security measures. Options for that will be configured by you using config files and not Apache.

iaculallad you are absolutely INCORRECT.  You DO configure security settings in apache!! The apache root directory, Order allow,deny Deny from all, ServerTokens  are all important global directives that define security measures for locking down apache!!!  They typically will not apply to a beginner's installation! Please do not advise if you don't know what you're talking about - it is unfair to those of us who actually read the documentation!!!!

---

### Post by MaindotC on 2008-05-29
Hi, madu.  Apache runs as its own user unless explicity started by whoever is logged into the system.  If you go to System -> Administration -> Users & Groups you'll see a new user group created called "apache" users.  You'll see the associative security level for the group defining it's ability (which is basically nothing more than running apache).

---

### Post by iaculallad on 2008-05-29
> **strAlan said:**
> iaculallad you are absolutely INCORRECT.  You DO configure security settings in apache!! The apache root directory, Order allow,deny Deny from all, ServerTokens  are all important global directives that define security measures for locking down apache!!!  They typically will not apply to a beginner's installation! Please do not advise if you don't know what you're talking about - it is unfair to those of us who actually read the documentation!!!!

Actually, thats what I mean when I said "Options for that will be configured by you using config files and not Apache". The User (i.e: Administrator) can configure the default files used by Apache to their likings or can edit any configurations that needs to be changed.

---

### Post by MaindotC on 2008-05-29
Sure, iaculallad - that's why you edited your post.  This isn't the first time I've caught you giving people incorrect information in an absolute "I know everything" form.

---

### Post by iaculallad on 2008-05-29
> **strAlan said:**
> Sure, iaculallad - that's why you edited your post.  This isn't the first time I've caught you giving people incorrect information in an absolute "I know everything" form.

Correction: What I edited on my previous post was a misspelled word and not this post, "Nope, you don't have to worry on security measures. Options for that will be configured by you using config files and not Apache." where you commented.

> **strAlan said:**
> This isn't the first time I've caught you giving people incorrect information in an absolute

This is a forum, you could give incorrect procedures to questions. Not at least if you're right there standing beside that person that you can give/suggest the correct solution for the problem. This is where a blind leads a blind.

---

### Post by MaindotC on 2008-05-29
I won't give incorrect procedures because I back them up with the documentation that associates it.  You should do the same instead of blindly telling people to do things and not knowing what result they may have.

---

### Post by iaculallad on 2008-05-29
> **strAlan said:**
> I won't give incorrect procedures because I back them up with the documentation that associates it.  You should do the same instead of blindly telling people to do things and not knowing what result they may have.

Sure do, we back them up with documentations that associates it and even add up our experience in it. But sometimes the problem that are posted on the forum do not seems like the way that it should be. We know what we posted could be the solution but could be different for that problem. So that's how their is the blind leading the blind thing, to solve that question on a trial and error method.

---

### Post by MaindotC on 2008-05-29
I'm not wasting any more time arguing with you.  Please stop advising people unless you know what you're doing.  Unsubscribing from this thread.

---

### Post by iaculallad on 2008-05-29
> **strAlan said:**
> I'm not wasting any more time arguing with you.  Please stop advising people unless you know what you're doing.  Unsubscribing from this thread.

Amen to that? Sure do, let's end the argument here because we're just wasting our bean counts here instead of using it reasonably.

---

### Post by madu on 2008-05-29
strAlan, iaculallad thank you a million for all the help...
Migrating from XP I'm guess I'm always inclined to worry about security..:(

> **strAlan said:**
> Hi, madu.  Apache runs as its own user unless explicity started by whoever is logged into the system.  If you go to System -> Administration -> Users & Groups you'll see a new user group created called "apache" users.  You'll see the associative security level for the group defining it's ability (which is basically nothing more than running apache).

Thank you for clearing that up buddy... 
going to install Apache now.. fingers crossed... :popcorn:

Thank you again fellows...

EDIT:
I started Apache as root (sudo /etc/init.d/apache2 start) and it said that the process httpd is already running..
I can see the "IT WORKS" in localhost..
the problem is I dont see a new 'apache' user created..
Is that OK?

Thank you again...

---

