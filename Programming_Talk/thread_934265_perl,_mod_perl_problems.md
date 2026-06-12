---
title: "perl, mod_perl problems"
date: 2008-09-30
forum: Programming Talk
---

### Post by meburke on 2008-09-30
I have posted this under "General Help", but I think this may be a better place for it. Unfortunately I don't know how to move the topic from GH to here, so I'm double-posting. Please excuse me.

OK, interesting problem: I seem to have perl, mod_perl, and apache2 installed so that they work (meaning I get messages saying they are installed and active), but I cannot get perl scripts or cgi to run from a browser.

cgi is enabled, so is perl.

I believe this is a configuration problem, but I'm having trouble figuring out how to troubleshoot it. No significant messages show up in the tail of /var/log/apache2/error.log.

My httpd.conf has:

PerlModule ModPerl::Registry

ScriptAlias /perl var/www/perl/

<Location "/perl/">
SetHandler perl-script
PerlHandler ModPerl::Registry
Options +ExecCGI
</Location>

and I do have a perl directory in /var/www/perl with a couple of small test scripts. However, connecting to the url [http://XXX.XXX.XXX.XXX/perl/mperltest.pl](http://XXX.XXX.XXX.XXX/perl/mperltest.pl) gives me a message saying the url cannot be found on the server. I thought the "/perl/" in the config file became a place holder for the url. Am I misunderstanding this?

My goal is to run perl scripts through the website. Once I get mod_perl working I expect to install mason, but at this point I would be very happy just being able to run perl scripts from the cgi-bin and/or the test directory I created under /var/www.

Since I originally started this post, I found an entry that suggested I put This in my /etc/apache2/mods-enabled/perl.conf file:

<Files ~ "\.(pl|cgi)$">
SetHandler perl-script
PerlResponseHandler ModPerl::PerlRun
Options +ExecCGI
PerlSendHeader On
</Files>

This doesn't seem to help me run a perl script from the browser, but I did finally get an interesting message when I restarted Apache:

 [error] slurp_filename('/etc/apache2/var') / opening: (2) No such file or directory at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 541

The content (cat -n /usr/lib/perl5/ModPerl/RegistryCooker.pm) at line 541 is:

 541	    $self->{CODE} = eval { $self->{REQ}->slurp_filename(0) }; # untainted

There is no /etc/apache2/var file, and I don't know why it's looking for it.

Somewhere, somebody knows where there is simple, explicit step-by-step directions for configuring and testing mod_perl 2. (A lot of instruction seems to apply to earlier versions of mod_perl, and doesn't seem to work.)

Any help would be appreciated.

Thanks in advance,

Mike

---

### Post by skeeterbug on 2008-09-30
Your configuration looks fine. I do the same thing except I use vhost. Is the perl location accessible? Try commenting out the files node and drop a html file in there and try to access it.

---

### Post by meburke on 2008-09-30
I'm sorry,Skeeter, I don't understand the instruction. Can you explain in a little more detail for me?

Thanks,

Mike

---

### Post by meburke on 2008-09-30
Duh, of course I understand, now that I've read the instruction with a clear head.

Yes, an html file in that directory is accessable.

Thanks again,

Mike

---

### Post by meburke on 2008-09-30
Even duh, duh, duh...I cannot reach that directory. (Duplicate file names messed me up.) The same perl script works fine from the www directory, so I guess mod_perl is, in fact, working. I get the error message about "/etc/apache2/var" each time I try to go into the experimental perl directory under /var/www/.

So I guess this is a configuration error related to Apache.

If you have any more ideas, I'd be glad to hear them.

Thanks,

Mike

---

### Post by skeeterbug on 2008-09-30
I usually deploy using a vhost.

Shouldn't 

ScriptAlias /perl var/www/perl/

be

ScriptAlias /perl /var/www/perl/

---

### Post by meburke on 2008-10-02
Thanks for the suggestion. I changed the httpd.conf entry to read /var instead of just var. It didn't help my problem, but I believe it should be that way.

You know, everyone used to complain about sendmail, but I really like that I had a means of testing the results of various settings systematically. I need a system like that for Apache.

Thanks,

Mike

---

### Post by skeeterbug on 2008-10-02
> **meburke said:**
> Thanks for the suggestion. I changed the httpd.conf entry to read /var instead of just var. It didn't help my problem, but I believe it should be that way.

You know, everyone used to complain about sendmail, but I really like that I had a means of testing the results of various settings systematically. I need a system like that for Apache.

Thanks,

Mike

I know apache on windows has a command line program that checks the configuration and reports back any problems.

Have you tried Alias instead of ScriptAlias?

Alias /perl /var/www/perl/

<Directory "/var/www/perl">
    # Options
</Directory>

---

### Post by meburke on 2008-10-02
Hey, that worked perfectly!

Thanks. Now, on to mason....(!?!)

Mike

---

### Post by meburke on 2008-10-02
I was looking for a command-line tester like the one you mentioned for Windows, and I found this:

[http://www.perl.com/pub/a/2003/05/22/testing.html](http://www.perl.com/pub/a/2003/05/22/testing.html)

Still a reference to old docs, but interesting.

Mike

---

### Post by skeeterbug on 2008-10-02
Here is my mason configuration in my vhost.

```
PerlModule HTML::Mason::ApacheHandler

<LocationMatch "(\.html|\.txt|\.pl)$">
    SetHandler perl-script
    PerlHandler HTML::Mason::ApacheHandler
    PerlAddVar MasonAllowGlobals $dbh
</LocationMatch>
```

---

