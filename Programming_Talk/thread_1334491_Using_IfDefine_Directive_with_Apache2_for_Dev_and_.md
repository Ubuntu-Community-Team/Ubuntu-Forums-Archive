---
title: "Using IfDefine Directive with Apache2 for Dev and Production Environments"
date: 2009-11-22
forum: Programming Talk
---

### Post by SuperMike on 2009-11-22
You may want to have an Apache configuration for your website where there is a difference between development and production. I mean, think of it -- one code base, but then it acts differently on URL and database connections depending on whether it is production or development. The trick can be to delineate this in your .htaccess file. You can do this with the IfDefine directive, like so:

```
<IfDefine dev>
# code goes here
</IfDefine>

<IfDefine !dev>
# code goes here
</IfDefine>
```

Trouble is, there's no clear documentation where to stick this variable assignment. 

Well, I have just solved this problem. You need to edit this file:

[FONT="Fixedsys"]/etc/apache2/envars[/FONT]

At the bottom of it, add:

[FONT="Fixedsys"]export APACHE_ARGUMENTS="-D dev"[/FONT]

Now bounce your Apache server like so:

[FONT="Fixedsys"]sudo /etc/init.d/apache2 stop[/FONT]

...wait 5 seconds

[FONT="Fixedsys"]sudo /etc/init.d/apache2 start[/FONT]

---

### Post by TariBuntu on 2010-11-29
Thank you a million, that's exactly what I've been looking for!

A small observation: the file is "envvars" (you have a typo).;)

Here's my contribution - the same thing translated into terminalese:

```
echo 'export APACHE_ARGUMENTS="-D YOUR_ENV_VAR_NAME"' | sudo tee -a /etc/apache2/envvars; sudo /etc/init.d/apache2 restart
```

---

