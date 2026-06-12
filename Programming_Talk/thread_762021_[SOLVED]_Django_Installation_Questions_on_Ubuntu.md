---
title: "[SOLVED] Django Installation Questions on Ubuntu"
date: 2008-04-21
forum: Programming Talk
---

### Post by khayman218 on 2008-04-21
I have installed Apache, modpython and Django via apt-get.  Apache and modpython are working (I can serve normal files and python script output).  However, I am unable to serve the initial Django project.  

Here is the httpd.conf:

```
<Location "/organik/">
        SetHandler python-program
        PythonHandler django.core.handlers.modpython
        SetEnv DJANGO_SETTINGS_MODULE settings.py
        PythonDebug On
        PythonPath "['/var/www/secure_html' , '/home/khayman218/python'] + sys.path"
</Location>
```

The code for the project is in /home/khayman218/python/organik:

```
khayman218@Khayserv:/var/www/secure_html/organik$ ls /home/khayman218/python/organik/ -l
total 20
-rw-r--r-- 1 khayman218 khayman218    0 Apr 21 13:17 __init__.py
-rw-r--r-- 1 khayman218 khayman218  141 Apr 21 13:18 __init__.pyc
-rwxr-xr-x 1 khayman218 khayman218  542 Apr 21 13:17 manage.py
-rw-r--r-- 1 khayman218 khayman218 2842 Apr 21 13:29 settings.py
-rw-r--r-- 1 khayman218 khayman218 1807 Apr 21 13:29 settings.pyc
-rw-r--r-- 1 khayman218 khayman218  227 Apr 21 13:17 urls.py
```

When I attempt to access the /organik url, I get the following error:
[HTML]MOD_PYTHON ERROR

ProcessId:      9380
Interpreter:    '127.0.0.1'

ServerName:     '127.0.0.1'
DocumentRoot:   '/var/www/secure_html'

URI:            '/organik/'
Location:       '/organik/'
Directory:      None
Filename:       '/var/www/secure_html/organik/'
PathInfo:       ''

Phase:          'PythonHandler'
Handler:        'django.core.handlers.modpython'

Traceback (most recent call last):

  File "/usr/lib/python2.5/site-packages/mod_python/importer.py", line 1537, in HandlerDispatch
    default=default_handler, arg=req, silent=hlist.silent)

  File "/usr/lib/python2.5/site-packages/mod_python/importer.py", line 1229, in _process_target
    result = _execute_target(config, req, object, arg)

  File "/usr/lib/python2.5/site-packages/mod_python/importer.py", line 1128, in _execute_target
    result = object(arg)

  File "/var/lib/python-support/python2.5/django/core/handlers/modpython.py", line 177, in handler
    return ModPythonHandler()(req)

  File "/var/lib/python-support/python2.5/django/core/handlers/modpython.py", line 145, in __call__
    self.load_middleware()

  File "/var/lib/python-support/python2.5/django/core/handlers/base.py", line 22, in load_middleware
    for middleware_path in settings.MIDDLEWARE_CLASSES:

  File "/var/lib/python-support/python2.5/django/conf/__init__.py", line 28, in __getattr__
    self._import_settings()

  File "/var/lib/python-support/python2.5/django/conf/__init__.py", line 55, in _import_settings
    self._target = Settings(settings_module)

  File "/var/lib/python-support/python2.5/django/conf/__init__.py", line 83, in __init__
    raise EnvironmentError, "Could not import settings '%s' (Is it on sys.path? Does it have syntax errors?): %s" % (self.SETTINGS_MODULE, e)

EnvironmentError: Could not import settings 'settings.py' (Is it on sys.path? Does it have syntax errors?): No module named settings.py
[/HTML]

From what I have been able to find on the intarweb, it looks like settings.py simply isn't being found.  I have put every variation of diretories in the PythonPath (in httpd.conf) and it still cannot find it.  

Any ideas on what I am missing?

Thanks.

---

### Post by ruy_lopez on 2008-04-21
A few weeks ago I spent hours trying the same. In the end I gave up. Sorry, I know that's probably not what you want to hear.

I think it has something to do with Apache not having privileges to access the Django project folder (which, like mine was, is in your home folder). The intricacies of Apache's configuration is a mystery to me.

---

### Post by khayman218 on 2008-04-21
> **ruy_lopez said:**
> I think it has something to do with Apache not having privileges to access the Django project folder (which, like mine was, is in your home folder). The intricacies of Apache's configuration is a mystery to me.

I thought the same thing.  I copied that diretory into a new one under Apache's root directory (and modified the httpd.conf accordingly), but got the same error.  

In the example on the django site, they have the settings.py in a directory under the www root while the django app is in a directory outside of the www root.  Does the project config need to be in the www dir, with the rest of the python app outside?

---

### Post by ruy_lopez on 2008-04-21
> **khayman218 said:**
> Does the project config need to be in the www dir, with the rest of the python app outside?

I tried that too. Give it a go. You might have better luck than I did.

Incidentally, I was playing with TurboGears (a similar framework) yesterday. The TurboGears website advises against setting up the framework with Apache and mod_python. Instead, it advises using mod_proxy (or something like that) to redirect requests for an Apache directory to the TurboGears default server. I imagine something like that could work for Django too. I think (?) TurboGears and Django both use the same lightweight http server.

See the note at the bottom of [this page.]("http://docs.turbogears.org/1.0/mod_python")

---

### Post by skeeterbug on 2008-04-21
Look at the error you are getting. The application can't locate the settings.py file. Add it to your path!

Working example on my dev server:

> <VirtualHost *>
       SetHandler python-program
       PythonHandler django.core.handlers.modpython
       PythonPath "[r'/home/jbest/src'] + sys.path"
       SetEnv DJANGO_SETTINGS_MODULE myproject.settings
       PythonDebug On
       <Location "/media">
               SetHandler None
       </Location>
</VirtualHost>


/home/jbest/src/myproject/settings.py is the location of my project settings file.

EDIT*

See also: [http://www.djangoproject.com/documentation/modpython/]("http://www.djangoproject.com/documentation/modpython/")

"Also, if your Django project is not on the default PYTHONPATH for your computer, you&#8217;ll have to tell mod_python where your project can be found:"

---

### Post by khayman218 on 2008-04-21
> **skeeterbug said:**
> Look at the error you are getting. The application can't locate the settings.py file. Add it to your path!

It was correctly added to the path (since eventually I had added almost the entire machine ;) ); however, I was naming it incorrectly in the httpd.conf file.  I had "settings.py" (the literal filename) when I should have had "organik.settings."  Or, "[projectname].settings" as you said.  I misunderstood the documentation when it said "change the name to match your settings file."

Thanks for the help everyone!

---

### Post by skeeterbug on 2008-04-21
> **khayman218 said:**
> It was correctly added to the path (since eventually I had added almost the entire machine ;) ); however, I was naming it incorrectly in the httpd.conf file.  I had "settings.py" (the literal filename) when I should have had "organik.settings."  Or, "[projectname].settings" as you said.  I misunderstood the documentation when it said "change the name to match your settings file."

Thanks for the help everyone!

Enjoy the install! :)

---

