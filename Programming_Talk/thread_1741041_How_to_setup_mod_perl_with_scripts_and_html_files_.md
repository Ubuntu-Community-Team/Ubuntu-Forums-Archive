---
title: "How to setup mod_perl with scripts and html files in the same directory?"
date: 2011-04-27
forum: Programming Talk
---

### Post by apollothethird on 2011-04-27
I have mod_cgi working perfectly.  However, it turns out there are features of mod_perl that I'm trying to use.  I have followed all the documentation I can find on using Ubuntu's mod_perl install with Apache2.  There seems to be some type of problems with the mod_perl's documentation, as it doesn't work as it's defined.  However, I found a modification to make it work, but only is designated directories.  If I tried to use in a directory with my other HTML files the regular HTML files will fail.

Using these steps (but using apt-get's install rather than compiling the tar ball). I did as follows:

( [http://perl.apache.org/docs/2.0/user/intro/start_fast.html](http://perl.apache.org/docs/2.0/user/intro/start_fast.html) )

placed this in the httpd.conf file (which was basically the same as "a2enmod perl".

httpd.conf line:

```
LoadModule perl_module /usr/lib/apache2/modules/mod_perl.so

Alias /perl/ /home/web/perl/

  <Directory /home/web/perl>
      SetHandler perl-script
      PerlResponseHandler ModPerl::Registry
      PerlOptions +ParseHeaders
      Options +ExecCGI
      Order allow,deny
      Allow from all 
  </Directory>
```

Now a perl script called using the /perl/ alias will work as long as it's in the alias directory.  If I add those lines that makes the /perl/ alias directory work to my root directory so that I can have my scripts integrated in the same directories as HTML files will allow .pl and .cgi files to work but the html files will fail.

What I really want to do is configure the system so that the scripts will work in the userdir area so that anyone that has his own public_html files and work on programming independently.  Also, I prefer using my userdir for my programming and testing.

By the way, the docs use " <Location" rather than "<Directory" to specify the area.  The location won't do anything on the system.  When that's used rather than "<Directory" the *.cgi scripts will be opened in the browser as text.  The *.pl files will cause the browse to prompt for downloading.

Thanks in advance for anyone having knowledge or insight on how to use mod_perl in directories that can be integrated with both scripts and html files.  If I can do it from the main server, I'm sure I'll be able to do the same thing in the userdir area.

By the way, the key might be finding a way to make the "<Location" specification work.  That way the area can have both a "<Location" and "<Directory" with "<Location" proving support for the *cgi and *.pl files and the "<Directory" specification proving support for the other option directives.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by slavik on 2011-04-27
you forgot to add the type that .pl and .cgi scripts are mimetype of cgi, search apache httpd docs for addtype

---

### Post by apollothethird on 2011-04-28
> **slavik said:**
> you forgot to add the type that .pl and .cgi scripts are mimetype of cgi, search apache httpd docs for addtype

Hi, Slavik.  Thanks for the input and hint.  However, I didn't forget the mimetype support.  I had actually added it and tested many variations in an attempt to get it working.

I always knew I could get it working if I went outside of the Ubuntu configuration environment.  But I'm trying to use Ubuntu and the accessory tools according to the design of the Ubuntu team so that my experience and feedback on using the resources can contribute to the stability and standard of the distro.

I tested the cgi (LoadModule cgi_module /usr/lib/apache2/modules/mod_cgi.so) which works perfectly by default.  But the perl module (LoadModule perl_module /usr/lib/apache2/modules/mod_perl.so) doesn't.  The *.cgi *.pl is uncommented by default in the mime module which is already loaded.  The parameter is: AddHandler cgi-script .cgi .pl

And yes, I had added it to the httpd.conf just to make sure.  I also added it to all the directory blocks which didn't affect what was already loaded in the default mime file.  I even tried other variations of the command in the httpd.conf file including using "perl-script" instead of "cgi-script" which would cause the Apache2 startup to fail.

I had spent many hours testing before posting my message and another many hours since your post.

Mod_perl appears not to use the "AddHandler" directive.

For others who might be having problems making mod_perl work with the Ubuntu default distribution, it turns out the <File> directive block will activate it.  Adding the following cold to the httpd.conf file turned on the support.

```
<Files ~ "\.(pl|cgi)$">
    SetHandler perl-script
    PerlResponseHandler ModPerl::PerlRun
    Options +ExecCGI
    PerlSendHeader On
 </Files>
```

It took me forever to find this.  I hope this information will spare others who might want to use the many features of mod_perl a lot of time.

Slavik, I really appreciate your taking the time to give input.  I also appreciate the time anyone else has spent on this thread trying to identify what might have been missing (by default) to activate the support for mod_perl in this case.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

