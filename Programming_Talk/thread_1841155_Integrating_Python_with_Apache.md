---
title: "Integrating Python with Apache"
date: 2011-09-08
forum: Programming Talk
---

### Post by ifben on 2011-09-08
Hello,

I am running Ubuntu 10.04 LTS. I would like to configure Python so that it can run on any of my websites (without having to specify a directory) and without any file headers the way PHP does. For example, I want a configuration that allows me to put a Python file with the contents, " print 'hi' ", in any of my websites' directories that shows a page with, "hi", when I open it in a web browser. I can currently do this with a PHP file that has the contents, " echo 'hi'; ".

Is such a thing possible?

I've got execution of Python scripts with CGI working, but this involves keeping all Python files in one directory and requires file headers such as #usr/bin/python and print "Content-Type: text/html".

I wasn't able to get mod_python to work, but I've heard it's deprecated in favor of mod_wsgi. Besides, based on [this guide]("http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch"),  it looks like your Python scripts are still confined to one directory.

And finally there's mod_wsgi, but looking at their [configuration guide]("http://code.google.com/p/modwsgi/wiki/QuickConfigurationGuide"), it looks like the most common configuration not only involves putting all Python scripts in one directory, but restarting Apache everytime a change is made to a script!

I don't understand how Python can be such an unclear nuisance and PHP was so seamlessly integrated into the environment. I didn't need to do anything to get PHP to work.

Any help is much appreciated!

Ben

---

### Post by Pynalysis on 2011-10-05
> **ifben said:**
> Hello,

I am running Ubuntu 10.04 LTS. I would like to configure Python so that it can run on any of my websites (without having to specify a directory) and without any file headers the way PHP does. For example, I want a configuration that allows me to put a Python file with the contents, " print 'hi' ", in any of my websites' directories that shows a page with, "hi", when I open it in a web browser. I can currently do this with a PHP file that has the contents, " echo 'hi'; ".

Is such a thing possible?

I've got execution of Python scripts with CGI working, but this involves keeping all Python files in one directory and requires file headers such as #usr/bin/python and print "Content-Type: text/html".

I wasn't able to get mod_python to work, but I've heard it's deprecated in favor of mod_wsgi. Besides, based on [this guide]("http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch"),  it looks like your Python scripts are still confined to one directory.

And finally there's mod_wsgi, but looking at their [configuration guide]("http://code.google.com/p/modwsgi/wiki/QuickConfigurationGuide"), it looks like the most common configuration not only involves putting all Python scripts in one directory, but restarting Apache everytime a change is made to a script!

I don't understand how Python can be such an unclear nuisance and PHP was so seamlessly integrated into the environment. I didn't need to do anything to get PHP to work.

Any help is much appreciated!

Ben

Django, a web framework written in Python, may be what you are looking for.

[https://www.djangoproject.com/](https://www.djangoproject.com/)

---

