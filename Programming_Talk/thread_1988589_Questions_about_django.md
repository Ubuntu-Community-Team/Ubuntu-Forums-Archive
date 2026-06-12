---
title: "Questions about django"
date: 2012-05-27
forum: Programming Talk
---

### Post by xaegis on 2012-05-27
Hello I am running python 2.7 with django 1.4 installed.
I am having trouble creating new projects with django. Whenever I use the command:```
sudo /usr/local/lib/python2.7/dist-packages/django/bin/django-admin.py startproject cms

``` 

I get errors or permission denied messages but if I use: 
```
django-admin.py startproject cms
```

Everything seems to work correctly. I know at some point I created a sym link in:  ```
/usr/local/bin
```  but is this the proper way to do this? Should I be using the full path instead? Also, why is django found in dist-packages instead of site-packages in the python directory? The books I am using are telling me the python files should be located in site-packages.

I also noticed that django "startproject" created two directories called "cms" one nested inside the other. Is this the default behavior, and why?


Thanks in advance.

-e

---

### Post by xaegis on 2012-05-28
so part of this question is solved. I had the wrong path in the settings.py file so it would not recognize/create a database there.

```

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3', # Add 'postgresql_psycopg2', 'mysql', 'sqlite3' or 'oracle'.
        'NAME': '/home/me/Projects/Django/cms/cms.db', 

```

---

### Post by amedrano on 2012-05-28
I use Django every day and I can tell you from experience that you should always use ```
virtualenv
``` when working on these types of projects. It will save you these types of annoying problems and its considered a best practice.

Check out [http://www.virtualenv.org/en/latest/index.html](http://www.virtualenv.org/en/latest/index.html)

---

### Post by xaegis on 2012-05-28
> **amedrano said:**
> I use Django every day and I can tell you from experience that you should always use ```
virtualenv
``` when working on these types of projects. It will save you these types of annoying problems and its considered a best practice.

Check out [http://www.virtualenv.org/en/latest/index.html](http://www.virtualenv.org/en/latest/index.html)

Should I use this in my deployment or only in development?


Thanks for the info.

---

### Post by amedrano on 2012-05-28
Both.
We deploy on Ubuntu and CentOS servers. Our servers run a number of django apps and we use virtualenv to isolate the dependencies. That way we can use any version of python or a python package (ex: django 1.2 vs django1.4) for each app.

---

