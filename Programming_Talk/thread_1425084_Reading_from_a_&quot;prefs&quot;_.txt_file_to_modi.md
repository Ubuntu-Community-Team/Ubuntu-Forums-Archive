---
title: "Reading from a &quot;prefs&quot; .txt file to modify algorithm -- Python"
date: 2010-03-08
forum: Programming Talk
---

### Post by Khufucius on 2010-03-08
A project I'm working on requires that the program reads a setting from a "preferences" text file, and, based on what it finds there, changes a variable inside the "main algorithm."

Right now I'm stuck at """
open("preferences.txt", r)
"""
Sorry I'm such a newb, but how do I parse the preferences.txt file for a certain string and then use that string to modify what's happening inside the main portion of my program?

That is, how can I "remember" and transfer data between files that my program is manipulating?  This is the programming equivalent of copy-and-paste, as far as I can tell.

Thanks in advance,

-K

---

### Post by memilanuk on 2010-03-08
Rather than muck it up (being another newbie myself)... does this help any?

[http://docs.python.org/tutorial/inputoutput.html#reading-and-writing-files](http://docs.python.org/tutorial/inputoutput.html#reading-and-writing-files)

---

### Post by lykwydchykyn on 2010-03-08
You might want to have a look at the configparser library:
[http://docs.python.org/library/configparser.html](http://docs.python.org/library/configparser.html)

---

### Post by Can+~ on 2010-03-08
I suggest that, even though the libraries mentioned above do the job, is better to write your own ad-hoc method to understand better, since, it seems that you have a wrong concept about variables.

Something as simple as:

```
variable=value
```

config file, can do the trick in your case.

Now, as for "copy-pasting", you should understand that variables declared on the python script, yes, whenever the interpreter reaches that point on execution, the variable will be set to that value, and that value is recorded in memory. To "preserve" the data is what the hard disk (the file in abstract sense) is for.

You should use variables like "foo = bar" inside the python script whenever there's no preference file, something like the "default value". If the file exists, parse it, obtain the value and store it as a variable temporary. When execution finishes, store the updated variables inside the config file .

Example (Python 3/2.6.x):

[PHP]#!/usr/bin/env python3

def readconfig(filename="config.ini"):
	
	# Empty config dictionary
	config = {}
	
	# Open the file and
	with open("config.ini") as configfile:
		for line in configfile:
			
			try:
				#split each of it's line into a key, value pair
				key, value = line.split("=", 2)
				
				# Store in a dictionary
				config[key] = value.strip()
			except ValueError:
				pass
	
	return config

config = readconfig()
print(config)[/PHP]

For the file config.ini:

```
variable=value
foo=bar

hello=world
```

Produces:

[PHP]{'variable': 'value', 'foo': 'bar', 'hello': 'world'}[/PHP]

---

### Post by km0r3 on 2010-03-08
```
open("preferences.txt", r)
```

**First off, it has to be:**
```
open("preferences.txt","r")
``` or if you just want to read-access it simply forget the "r" argument.

Why don't make your settings file a Python file, e.g. settings.py ?

You simply import your settings.py and read the variables' values defined in the settings.py.

Note that best practice for defining "static variables" in Python is writing them UPPERCASE.

Take for example an untouched [Django]("http://djangoproject.com") settings.py:

```
# Django settings for testfd project.

DEBUG = True
TEMPLATE_DEBUG = DEBUG

ADMINS = (
    # ('Your Name', 'your_email@domain.com'),
)

MANAGERS = ADMINS

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.', # Add 'postgresql_psycopg2', 'postgresql', 'mysql', 'sqlite3' or 'oracle'.
        'NAME': '',                      # Or path to database file if using sqlite3.
        'USER': '',                      # Not used with sqlite3.
        'PASSWORD': '',                  # Not used with sqlite3.
        'HOST': '',                      # Set to empty string for localhost. Not used with sqlite3.
        'PORT': '',                      # Set to empty string for default. Not used with sqlite3.
    }
}

# Local time zone for this installation. Choices can be found here:
# http://en.wikipedia.org/wiki/List_of_tz_zones_by_name
# although not all choices may be available on all operating systems.
# On Unix systems, a value of None will cause Django to use the same
# timezone as the operating system.
# If running in a Windows environment this must be set to the same as your
# system time zone.
TIME_ZONE = 'America/Chicago'

# Language code for this installation. All choices can be found here:
# http://www.i18nguy.com/unicode/language-identifiers.html
LANGUAGE_CODE = 'en-us'

SITE_ID = 1

# If you set this to False, Django will make some optimizations so as not
# to load the internationalization machinery.
USE_I18N = True

# Absolute path to the directory that holds media.
# Example: "/home/media/media.lawrence.com/"
MEDIA_ROOT = ''

# URL that handles the media served from MEDIA_ROOT. Make sure to use a
# trailing slash if there is a path component (optional in other cases).
# Examples: "http://media.lawrence.com", "http://example.com/media/"
MEDIA_URL = ''

# URL prefix for admin media -- CSS, JavaScript and images. Make sure to use a
# trailing slash.
# Examples: "http://foo.com/media/", "/media/".
ADMIN_MEDIA_PREFIX = '/media/'

# Make this unique, and don't share it with anybody.
SECRET_KEY = '+-krq16jq_=1#rwnc8-p%*kqp(0!_b$73^!mzddrpc8_&tq(8r'

# List of callables that know how to import templates from various sources.
TEMPLATE_LOADERS = (
    'django.template.loaders.filesystem.Loader',
    'django.template.loaders.app_directories.Loader',
#     'django.template.loaders.eggs.Loader',
)

MIDDLEWARE_CLASSES = (
    'django.middleware.common.CommonMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
)

ROOT_URLCONF = 'testfd.urls'

TEMPLATE_DIRS = (
    # Put strings here, like "/home/html/django_templates" or "C:/www/django/templates".
    # Always use forward slashes, even on Windows.
    # Don't forget to use absolute paths, not relative paths.
)

INSTALLED_APPS = (
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.sites',
    'django.contrib.messages',
    # Uncomment the next line to enable the admin:
    # 'django.contrib.admin',
)

```

Note that all "static" variables are written uppercase. 
How would I access the values?

```
import settings

# Assigning the DATABASES dictionary to a variable
x = settings.DATABASES

# Read items of key 'default'
x['default']
```

You could achieve the same using something like a Mark-Up language, like XML, HTML, YAML, etc.

You can choose anything you'd like or write your own "language".

Feel free to leave comments.

---

### Post by memilanuk on 2010-03-08
Thanks Kenny & Can+~... that was extremely helpful, for me at least!

---

### Post by Khufucius on 2010-03-08
Thanks so much, this makes much more sense now.

The libraries mentioned will be interesting to look at as well, although for now I'll try composing something myself.  That sounds like the best way to learn this on a deep level.

I really appreciate the effort you've all put into your replies; this is a fantastic forum!

-K

---

