---
title: "Default configuartion for Python 2.7.3 in Ubuntu 12.04"
date: 2012-11-26
forum: Programming Talk
---

### Post by LotsOfStuff on 2012-11-26
I need to replace the default Python 2.7.3 installation on Ubuntu with an installation from source with --enable-shared add to the configuration options.  I've been able to reinstall, but the problem is that the new installation doesn't seem to have everything the original default one had.  Before I continue to piecemeal it all together, I thought I would ask: which configuration options are equivalent to the default install of Python 2.7.3?  If I know that, I should just be able to add --enable-shared to the end of it, and be done (I hope).

---

### Post by Bachstelze on 2012-11-26
What makes you think you need to do that? What you probably need to do is to install libpython, which is in a separate package.

---

### Post by LotsOfStuff on 2012-11-26
Bachstelze,

The original problem I am trying to solve is a python mismatch between mod_wgsi and my native python (2.7.2 vs 2.7.3) for a django application.  I'm definitely a novice, but all of the research I've done seems to indicate that the best way around this is to install python from source with the --enable-shared option, and then to install mod_wgsi from source using the new python installation.

---

### Post by Bachstelze on 2012-11-26
Can you provide links that say this? In particular, are they Ubuntu-specific? Python is a crucial part of Ubuntu, so if you want to tinker with it you should be certain it works.

---

### Post by LotsOfStuff on 2012-11-26
Thanks for taking an interest in my problem.

I've been working on this problem for a few days, and honestly can't remember everything that I tried.  But I did try to get around it without a new Python installation first.  This has been a last resort in desperation.

Some of the links that helped bring me to the conclusion that I needed a new python installation with the --enable-shared option are:

[http://stackoverflow.com/questions/11382024/ubuntu-python-version-virtualenvwrapper-and-django](http://stackoverflow.com/questions/11382024/ubuntu-python-version-virtualenvwrapper-and-django)

which points to this discussion:
[https://groups.google.com/forum/?fromgroups=#!topic/modwsgi/F5Wn4uWrQAg](https://groups.google.com/forum/?fromgroups=#!topic/modwsgi/F5Wn4uWrQAg)

There is also this:
[http://code.google.com/p/modwsgi/wiki/InstallationIssues#Python_Patch_Level_Mismatch](http://code.google.com/p/modwsgi/wiki/InstallationIssues#Python_Patch_Level_Mismatch)

And I ended up trying to follow these instructions:
[http://cysec.org/content/compiling-modwsgi-custom-python-build](http://cysec.org/content/compiling-modwsgi-custom-python-build)

A few additional points:

I am trying to run my django app in a virtualenv using virtualenvwrapper.  Also, I'm not trying to set up a second python installation, just trying to replace the original.  If there is a simpler way that works, I'm certainly willing to try it.

I was originally following these instructions for setting up a Django site on a linode:
[http://library.linode.com/frameworks/django-apache-mod-wsgi/ubuntu-10.04-lucid](http://library.linode.com/frameworks/django-apache-mod-wsgi/ubuntu-10.04-lucid)

Making slight changes because the documentation is a little old (for instance, you no longer have to create your own django.wsgi file because it produces wsgi.py for you).

Any ideas?

---

### Post by Bachstelze on 2012-11-26
And what is the problem you get when following that last link? Normally, you shouldn't get any version mismatch because all the packages in the repositories are compiled against other packages in the same repositories, so it all should fit. If it's really a version mismatch, it's probably a bug in the packages.

---

### Post by LotsOfStuff on 2012-11-26
When I made a request to the django app part of my site, my Apache error log gave me something very similar to this (I am copying and pasting from a web page, so the dates are different):

[Tue Aug 21 19:33:26 2012] [warn] mod_wsgi: Compiled for Python/2.7.2+.
[Tue Aug 21 19:33:26 2012] [warn] mod_wsgi: Runtime using Python/2.7.3.
...
[Tue Aug 21 19:33:26 2012] [error] python_init: Python version mismatch, expected '2.7.2+', found '2.7.3'.

After this, I first tried just installing mod_wsgi from source, hoping that compiling it with 2.7.3 would be enough, but strangely I got the same error afterward.

---

### Post by Bachstelze on 2012-11-26
***EDIT:*** The problem seems to be with libapache2-mod-python. Recompiling it (and not mod-wsgi) according to instruction below seems to fix it (I no longer get the "mismatch" error messages).

-------------------

If you don't need this to work urgently, what you should do is probably report this as a bug and see what the developers say. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I find it weird, though, that recompiling wsgi failed to fix the problem, so perhaps you didn't compile it properly. Try this:

1. Uninstall all wsgi related packages.
2. Get the source package with: [font=monospace]apt-get source mod-wsgi[/font]
3. Install the build dependencies with: [font=monospace]sudo apt-get build-dep mod-wsgi[/font]
4. Move into the source package dir and build the binary packages: [font=monospace]debuild[/font]

Then after a while it will create a bunch of packages, which are identical to the packages form the repositories, except that they are compiled on your machine. Try installing them and see what happens. If it still doesn't work, you have a real problem...

---

### Post by LotsOfStuff on 2012-11-26
Thank you, I will try this and report back.

Any way for me to revert back to the original ubuntu python installation?  Or do i need to start from scratch with a fresh install of ubuntu?

---

### Post by Bachstelze on 2012-11-26
See my edit. ;)

> **LotsOfStuff said:**
> 
Any way for me to revert back to the original ubuntu python installation?  Or do i need to start from scratch with a fresh install of ubuntu?

It depends what exactly you have changed, but if you can afford to start over from scratch, it is of ourse the safest way to go if you are unsure.

---

### Post by LotsOfStuff on 2012-11-27
I rebuilt my linode with a refresh 12.04 install, and redid everything, using your advice for libapache2-mod-python.  I ran into some troubles with debuild:

> 
gpg: /tmp/debsign.AP3oIkNT/libapache2-mod-python_3.3.1-9ubuntu1.dsc: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1271:
running debsign failed
)
so I ended up using:

sudo debuild -i -us -uc -b

I still get a warning in the apache error log whenever I restart apache:
> [Tue Nov 27 08:01:03 2012] [warn] mod_wsgi: Compiled for Python/2.7.2+.
[Tue Nov 27 08:01:03 2012] [warn] mod_wsgi: Runtime using Python/2.7.3.
[Tue Nov 27 08:01:03 2012] [notice] Apache/2.2.22 (Ubuntu) mod_wsgi/3.3 Python/2.7.3 configured -- resuming normal operationsBut no error.  However, my django app still does not work.  Hard to tell whether this is the issue though, since I also have other pieces installed like rabbitmq and memcached.  Lot's could go wrong, I suppose, but I don't see any errors showing up in the apache error log despite getting this on the request:

> **Internal Server Error**

 The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator, [redacted] and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.
  Apache/2.2.22 (Ubuntu) Server at [redacted].com Port 80Any ideas on how to debug this issue?  I put al little test index.html in the html root, and that loads fine, so at least apache is working.

Edit: Nevermind, I found the django log.  The issue is:

> ImportError: No module named django.core.wsgi

I can try to debug this on my own tomorrow.  Thanks!

---

### Post by Bachstelze on 2012-11-27
> **LotsOfStuff said:**
> I rebuilt my linode with a refresh 12.04 install, and redid everything, using your advice for libapache2-mod-python.  I ran into some troubles with debuild:

That is fine, you can ignore it.

> so I ended up using:

sudo debuild -i -us -uc -b

Never run debuild with sudo! (In general, never use sudo unless you are certain that you need it.)

I'm not sure what you did wrong but on mymachine after rebuilding libapache2-mod-python and installing the resulting package, I do not get those warnings anymore after restarting Apache.

---

### Post by roberthernandez on 2013-03-08
# You have to recompile mod-python and/or mod-wsgi. 


# Remove mods
apt-get remove libapache2-mod-python libapache2-mod-wsgi


# Get dependencies
apt-get build-dep libapache2-mod-python libapache2-mod-wsgi


# Build mod-python
mkdir /tmp/python
cd /tmp/python
apt-get source libapache2-mod-python
cd libapache2-mod-python-[x.x.x]
dpkg-buildpackage -rfakeroot -b


#Build mod-wsgi
mkdir /tmp/wsgi
cd /tmp/wsgi
apt-get source libapache2-mod-wsgi
cd mod-wsgi-[x.x.x]
dpkg-buildpackage -rfakeroot -b 


# Install newly compiled packages
dpkg -i /tmp/python/libapache2-mod-python-[x.x].deb /tmp/wsgi/libapache2-mod-wsgi-[x.x].deb

---

### Post by kostas.katsaros on 2013-06-08
Nice!

But you have to install fakeroot before building anything or you 're getting an error:

```
# apt-get install fakeroot
```

> **roberthernandez said:**
> # You have to recompile mod-python and/or mod-wsgi. 


# Remove mods
apt-get remove libapache2-mod-python libapache2-mod-wsgi


# Get dependencies
apt-get build-dep libapache2-mod-python libapache2-mod-wsgi


# Build mod-python
mkdir /tmp/python
cd /tmp/python
apt-get source libapache2-mod-python
cd libapache2-mod-python-[x.x.x]
dpkg-buildpackage -rfakeroot -b


#Build mod-wsgi
mkdir /tmp/wsgi
cd /tmp/wsgi
apt-get source libapache2-mod-wsgi
cd mod-wsgi-[x.x.x]
dpkg-buildpackage -rfakeroot -b 


# Install newly compiled packages
dpkg -i /tmp/python/libapache2-mod-python-[x.x].deb /tmp/wsgi/libapache2-mod-wsgi-[x.x].deb

---

