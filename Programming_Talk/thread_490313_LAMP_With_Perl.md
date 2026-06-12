---
title: "LAMP With Perl"
date: 2007-07-02
forum: Programming Talk
---

### Post by ankursethi on 2007-07-02
I want to check out LAMP under Perl instead of PHP. I've used PHP in the past, and I must say I was not very impressed. On the whole, I don't like web development a lot, but I want to build a website and I want to do most of the scripting on my own. I choose Perl. No Ruby, no Python, no PHP. Just Perl. So please don't suggest anything else ;). I'll get to those if I have time. Since I already know Perl, I don't think I'll have a problem with web scripting.

Right now I'm using Feisty. I want to install a development server using Apache, MySQL and Perl. Now, I can probably install the server through the repos, but I'd like it more if I had something like XAMPP. I can't install XAMPP because it doesn't want to go anywhere except opt and putting it in the home directory requires a lot of editing with the final result being an unstable XAMPP. I need something that can go in my home directory and have a half-functional GUI config tool to edit all those config. files.

Considering I want to install through the repos. Do I do this :```

sudo apt-get install apache2 apache2-doc libapache-mod-perl libapache-mod-perl-doc mysql-server mysql-admin
``` ?

Also suggest some good books/tutorials on using mod_perl under Apache and on overall web dev using Perl.

Thanks to anyone who helps. And thanks to anyone who manages to read this post ...

---

### Post by LaRoza on 2007-07-02
To get LAMPP:

```

sudo tasksel

```

You will be given choices, pick "LAMPP".

If you want the page to be in a different directory, you can edit the configuration for Apache to pull web pages from that directory. I have Apache pulling pages out of a different drive at the moment.

-edit Since you said not to recommend PHP or Python, I won't.

---

### Post by ankursethi on 2007-07-02
Okay, nice :-). Thanks a lot. And the tutorials?

---

### Post by LaRoza on 2007-07-02
Try this site: [http://perl.apache.org/docs/tutorials/index.html](http://perl.apache.org/docs/tutorials/index.html), sorry I can't give more, I don't use Perl.

---

### Post by tr333 on 2007-07-03
Any CGI development using Perl should probably use the [CGI.pm](http://search.cpan.org/~lds/CGI.pm-3.29/CGI.pm) module, available from CPAN.  When running Perl code as CGI, consider using the '-T' switch for perl to force it into [taint mode](http://perldoc.perl.org/perlsec.html).

---

### Post by ankursethi on 2007-07-04
Just did a :
```
sudo apt-get install apache2 libapache-mod-perl libapache-mod-perl-doc
```

Now I need help configuring Apache as a local development environment for mod_perl. httpd.conf is empty. It has (I think) been moved to apache2.conf. But I can't make head or tail of it. How do I change the root directory of the site to /home/USERNAME/www? How do I make my Perl code run properly? And what about MySQL, how to configure that? Also, I want to NOT start Apache with Ubuntu. I'd like to launch it from the script present in init.d.

Any help?

---

### Post by tr333 on 2007-07-05
> **ankursethi said:**
> Just did a :
```
sudo apt-get install apache2 libapache-mod-perl libapache-mod-perl-doc
```

Now I need help configuring Apache as a local development environment for mod_perl. httpd.conf is empty. It has (I think) been moved to apache2.conf. But I can't make head or tail of it. How do I change the root directory of the site to /home/USERNAME/www? How do I make my Perl code run properly? And what about MySQL, how to configure that? Also, I want to NOT start Apache with Ubuntu. I'd like to launch it from the script present in init.d.

Any help?

It seems you are installing the incorrect packages.  You want libapache2-mod-perl and libapache2-mod-perl-doc.  The packages you have are for apache1.3, not apache2.

To change the root directory, look in the "/etc/apache2/sites-enabled/000-default" file.  Inside the <VirtualHost *> section, it contains the line "DocumentRoot /var/www/".  This line specifies the root directory of all websites.  If you have other virtual hosts, then you can just insert another "DocumentRoot" line for each virtual host.  I have no experience with mod_perl or mysql, so I cant help on those problems.

---

### Post by LaRoza on 2007-07-05
> **ankursethi said:**
> Just did a :
```
sudo apt-get install apache2 libapache-mod-perl libapache-mod-perl-doc
```

How do I make my Perl code run properly? And what about MySQL, how to configure that?

Any help?

Did you install MySQL?

---

### Post by ankursethi on 2007-07-05
No, not yet. I was trying to get mod_perl working first. I'll install MySQL and come back here later.

I installed mod_perl for Apache 2. Doing *apache2ctl status* gives me :
```
Apache/2.2.3 (Ubuntu) mod_perl/2.0.2 Perl/v5.8.8 Server at localhost Port 80
```
so I think mod_perl is installed and usable. But when I put the index.cgi file inside the root server directory, Apache just showed me my code instead of running it. What now? I made the file executable, do I need to do something else?

Anybody have any guides on how to configure Apache 2? I've had experience with Apache 1.x so I think I'm looking for configuration files and stuff in a wrong place. Also, I'll probably need some help with MySQL as well, but I suspect there are already wiki pages for than since it's one of those things "normal" people tinker with (as opposed to me tinkering with mod_perl).

EDIT :
Done! I need to put the files in the CGI directory, and I didn't know where that was. I just followed a guide on the Gentoo wiki and edited /etc/apache2/mods-enabled/perl.conf file and added the following to the end of it :
 <Files ~ "\.(pl|cgi)$">
   SetHandler perl-script
   PerlResponseHandler ModPerl::PerlRun
   Options +ExecCGI
   PerlSendHeader On
 </Files>
This runs any Perl script without the need to house them in a special cgi-perl directory.

Yay! But Apache2 guides are still welcome :-)

---

### Post by digeratess on 2007-09-05
For the record, the correct packages for mod_perl and doc on Apache2 are
```

libapache2-mod-perl2
libapache2-mod-perl2-doc

```

---

### Post by run4flat on 2008-05-13
ankursethi, you area golden god!  I would thank you (formally) if I could, but I can't find a ribbon.

Let me be specific.  This gets my perl working:
[PHP]
<Files ~ "\.(pl|cgi)$">
	SetHandler perl-script
	PerlResponseHandler ModPerl::PerlRun
	Options +ExecCGI
	PerlSendHeader On
</Files>
[/PHP]

Thank you thank you thank you!

Problem is, as you may have guessed, this is not the most secure thing.  If somebody managed to get a malicious perl script onto your system, they would be able to run it without much trouble simply by navigating to it with their browser.

For my part, I would love to set up a perl CGI.  Problem is, I can't figure out how.  I think it should be really simple, but I've spent the past 2 hours unsuccessfully looking.  Your directive is the first one that gets any perl working for me.

Why is this not automatically set up with the mod_perl deb?  Unless my memory fails me, PHP worked out-of-the box.

---

### Post by TechZilla on 2011-06-27
resurrected from long slumber...

If you are writing new Perl based web scripts, you should strongly look at CGI::Fast

---

### Post by slavik on 2011-06-27
look into Mason (HTML::Mason), it is a very nice templating framework for Perl (I prefer it over CGI based stuff).

---

