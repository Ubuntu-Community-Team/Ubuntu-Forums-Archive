---
title: "problem to start a server in Django"
date: 2010-12-14
forum: Programming Talk
---

### Post by navaneethan on 2010-12-14
I want to test django application so when i created the project
"django-admin.py start project testp" and i created application python
manage.py startapp testapp

then i added in settings.py (database
postgresql_psycopg2,name,username,password) as well as i am running in
virtualenv,installed fine of(psycopg2,django 1.1)

when i ran a server i got the error
```

" (test)hirelex@hirelex-laptop:~/test/testp$ python manage.py
runserver
Validating models...
Unhandled exception in thread started by <function inner_run at
0x9f266bc>
Traceback (most recent call last):
 File "/usr/local/lib/python2.6/dist-packages/django/core/management/
commands/runserver.py", line 48, in inner_run
   self.validate(display_num_errors=True)
 File "/usr/local/lib/python2.6/dist-packages/django/core/management/
base.py", line 249, in validate
   num_errors = get_validation_errors(s, app)
 File "/usr/local/lib/python2.6/dist-packages/django/core/management/
validation.py", line 22, in get_validation_errors
   from django.db import models, connection
 File "/usr/local/lib/python2.6/dist-packages/django/db/__init__.py",
line 77, in <module>
   connection = connections[DEFAULT_DB_ALIAS]
 File "/usr/local/lib/python2.6/dist-packages/django/db/utils.py",
line 91, in __getitem__
   backend = load_backend(db['ENGINE'])
 File "/usr/local/lib/python2.6/dist-packages/django/db/utils.py",
line 22, in load_backend
   module = import_module('.base', 'django.db.backends.%s' %
backend_name)
 File "/usr/local/lib/python2.6/dist-packages/django/utils/
importlib.py", line 35, in import_module
   __import__(name)
ValueError: Empty module name
```

"

May i know the problem ?please suggest me

pip freeze

" Brlapi==0.5.4
CouchDB==0.6
Django==1.2.3
GnuPGInterface==0.3.2
Mako==0.2.5
PAM==0.4.2
PIL==1.1.7
PyOpenGL==3.0.0
Pygments==1.2.2
Twisted-Core==10.0.0
Twisted-Names==10.0.0
Twisted-Web==10.0.0
adium-theme-ubuntu==0.1
apturl==0.4.1ubuntu4
command-not-found==0.1
configglue==0.2dev
cups==1.0
distribute==0.6.10
django-tagging==0.3.1
docutils==0.6
egenix-mx-base==3.1.3
fstab==1.4
gdata.py==1.2.4
gnome-app-install==0.4.2ubuntu2
hgview==1.1.3
httplib2==0.6.0
human-theme==0.39
jockey==0.5.8
launchpadlib==1.6.0
lazr.restfulclient==0.9.11
lazr.uri==1.0.2
louis==1.7.0
lxml==2.2.4
mercurial==1.4.3
nvidia-common==0.0.0
oauth==1.0a
onboard==0.93.0
papyon==0.4.8
pexpect==2.3
protobuf==2.2.0
psycopg2==2.3.1
pyOpenSSL==0.10
pycrypto==2.0.1
pycurl==7.19.0
pyinotify==0.8.9
pyserial==2.3
python-apt==0.7.94.2ubuntu6.2
python-debian==0.1.14ubuntu2
python-launchpad-bugs==0.3.6
pyusb==0.4.2
pyxdg==0.18
rdflib==2.4.2
screen-resolution-extra==0.0.0
simplejson==2.0.9
smbc==1.0
speechd==0.3
speechd-config==0.0
system-service==0.1.6
ubuntu-gdm-themes==0.33
ubuntuone-storage-protocol==1.2.0
ufw==0.30pre1-0ubuntu2
unattended-upgrades==0.1
usb-creator==0.2.22
vboxapi==1.0
virtkey==0.01
virtualenv==1.4.5
wadllib==1.1.4
wsgiref==0.1.2
xkit==0.0.0
zope.interface==3.5.3
(test)hirelex@hirelex-laptop:~/test/testp$

---

### Post by robots.jpg on 2010-12-14
Looks like it's having trouble resolving the package name on the 'ENGINE' line of settings.py.  Does yours look like this?

```

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2', 

```

---

### Post by navaneethan on 2010-12-19
no it is wrong; to run in virtualenv we should not mention like that.i am verified

---

