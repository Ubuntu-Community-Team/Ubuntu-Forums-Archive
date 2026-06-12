---
title: "Document root, virtual host, and path confusion"
date: 2015-04-04
forum: New to Ubuntu
---

### Post by rob129 on 2015-04-04
Hey Everyone!

I've an Azure account and testing several configs for a production website (Wordpress with approximately 40K custom posts and a 6.5 gb mysql) - trying WAMP on 2008 and LAMP on Ubuntu 14.04.

Using a great article on setting up an Ubuntu server for Wordpress ( [http://omaralzabir.com/how-to-setup-a-rock-solid-vm-on-windows-azure-for-your-wordpress-blogs/](http://omaralzabir.com/how-to-setup-a-rock-solid-vm-on-windows-azure-for-your-wordpress-blogs/) ) I've come to a problem I can't quite figure out.

The article was written for a slightly older version of Ubuntu - Ubuntu having changed the default document path from /var/www/public_html to /var/www/html/domain.com/public_html/    - I think?

I've created the directory - /var/www/html/domain.com/public_html - and put my test.php (info php file) in that folder. But, when I got to the Azure url - domain.cloudapp.net/test.php - I just get a blank page.

BUT if I put the test.php in the /var/www/html folder it serves up perfectly.

Can someone explain why? What I've done wrong? Do I actually need to have the /var/www/html/domain.com/public_html folders/path or can I just serve up the site via /var/www/html...?

Also - I haven't pointed my public domainname.com to Azure yet - I want to test it all first - but that shouldn't make a difference at this point, should it? I mean I could name that /domain.com/ anything at this stage, yes?

Thanks for any help!
Rob

---

### Post by SeijiSensei on 2015-04-04
The default DocumentRoot moved from /var/www to /var/www/html. If you're in control of the server, just make things relative to that.  If this is a shared hosting platform, you should ask your provider.

---

### Post by rob129 on 2015-04-04
Hello Sensei  and thank you!
I think the problem that I was having, following some very good instructions, is that those instructions had me configuring virtual hosts on the server. Am I correct that I would only need to configure that for hosting multiple sites on that server?

If I'm only hosting the one site on the server I can just put everything into the /var/www/html folder? I don't need to setup /var/www/html/domainname.com/public_html/       ?

And no, not shared, it's an MS Azure VM.

Thanks again!
Rob

---

### Post by sandyd on 2015-04-04
> **rob129 said:**
> Hello Sensei  and thank you!
I think the problem that I was having, following some very good instructions, is that those instructions had me configuring virtual hosts on the server. Am I correct that I would only need to configure that for hosting multiple sites on that server?

If I'm only hosting the one site on the server I can just put everything into the /var/www/html folder? I don't need to setup /var/www/html/domainname.com/public_html/       ?

And no, not shared, it's an MS Azure VM.

Thanks again!
Rob

If its a single site, you don't need virtual hosts.

Regards,

---

