---
title: "PHP file_get_contents issue - I have tried the obvious!"
date: 2007-08-16
forum: Programming Talk
---

### Post by p_c_nixon on 2007-08-16
Hi,
We're running a new webserver with Ubuntu 7.04 installed.  Everything has exceeded our expectation but we have had only one persistent problem that despite hours searching and tweaking we cannot resolve.

The problem lies around PHP's file_get_contents function, now before I explain further let me quickly say I have:

1) Checked allow_url_fopen and allow_url_include are On.
2) Tried setting manually the user agent.
3) Tried executing the PHP  script from the command line (same problem)
4) Checked I am able to access the resource via other methods.

The problem is that trying to retrieve URL's via this function results in:
Warning: file_get_contents([http://www.test.com/index.php):](http://www.test.com/index.php):) failed to open stream: HTTP request failed! 

We have tried connecting the machine to a dedicated ADSL connection and the problem disappears, the problem only occurs through our leased line and firewall system the whole business connects to.

You would therefore assume that perhaps it's a problem with the firewall settings, however we have even tried changing the IP address of the new server to the same as the old Windows box (that worked fine) and still the problem persists.  The curious thing is if we use fsockopen to open a socket we can easily connect and retrieve the data, so PHP is definitely able to see the net.  Nothing else on the box seems to display any internet connectivity issues through the firewall and I'm able to retrieve the file using wget.

I have installed XAMPP on the box which runs independently and the problem can be replicated with it's version of Apache & PHP (4 and 5).

It seems this only affects file_get_contents and fopen.  Has anyone got any suggestions? I have run out of steam with this and I just don't know where to look next :(

Our firewall/proxy system is managed by 7 Global (who maintain there should be no reason why we can't get through) and our proxy server is SonicWALL.

I hope someone can shed some light on this problem, I've exhausted my limited knowledge and need some expert advice!

---

### Post by monquixote on 2008-09-24
I am having the exact same problem.

I wrote the PHP on a Windows box which works fine and moved it to my Ubuntu server and it suddenly stopped working.
My server is also behind sonicwall so I am wondering if this is the problem.

Again I can get the file from the command line using wget or by running the script on my Windows desktop but when running it on my server it doesn't work.

Anyone have any ideas?

---

### Post by Reiger on 2008-09-26
Hmm. I am not at all sure but I ran into trouble with my Apache & PHP combo when I wanted to do file uploads. It turned out to be caused by the fact that the default upload/temp dir of Apache on Ubuntu is only RWX by root (the folder is /tmp). Rather than changing permissions (and possibly breaking stuff, say security) I uncommented a directive (can't recall, but it's listed on the PHP file upload tutorial) and specified a dedicated folder (in my case /var/www/php5/tmp).

Now I am by no means an Apache/PHP expert, but you may find assigning dedicated dirs for PHP5 to operate on/in solves your problem too?

---

### Post by monquixote on 2008-09-26
I ended up rewriting the code to use fsockopen rather than fgets which is working arround the problem rather than fixing it.
I found a post on the PHP forums which referenced the issue and I am going to get IT to make some changes next week so I will let you know if that fixes anything.

[http://bugs.php.net/bug.php?id=40197](http://bugs.php.net/bug.php?id=40197)

---

### Post by Bachstelze on 2008-09-26
> **Reiger said:**
> It turned out to be caused by the fact that the default upload/temp dir of Apache on Ubuntu is only RWX by root (the folder is /tmp). Rather than changing permissions (and possibly breaking stuff, say security) I uncommented a directive (can't recall, but it's listed on the PHP file upload tutorial) and specified a dedicated folder (in my case /var/www/php5/tmp).

/tmp is supposed to be read-writable by everyone and have the sticky bit on (mode 1777). If it's not, more problems will happen sooner or later. I strongly advise you to fix that.

---

### Post by monquixote on 2008-10-06
I'm happy to say that I got IT to change the firewall setting as detailed in the link and it now works.

[http://bugs.php.net/bug.php?id=40197](http://bugs.php.net/bug.php?id=40197)

The setting was "Enforce Host Tag Search with for CFS"

Weirldly it only seems to affect fgets on PHP 5 running on Linux other platforms and other PHP generated HTTP requests are unaffected.

---

