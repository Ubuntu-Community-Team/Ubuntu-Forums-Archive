---
title: "AttributeError: module 'posts.views' has no attribute 'home'"
date: 2019-03-29
forum: Programming Talk
---

### Post by Drone4four on 2019-03-29
Learning from a Udemy course I am taking by Nick Walter on Django, I am writing my own &#8220;Credit Card Redaction&#8221; app. The basic functionality is in place. But now I am trying to add a blog post app to go with it. I successfully initiated the app using $ python3 manage.py startapp posts. But as soon as I started filling in the urls.py, template and sub-views, my server has stopped running. I get:

> File "/home//dev/projects/python/2018-and-2019/CC_Redact/CC_Redact/urls.py", line 10, in url(r'^$', views.home, name='home'),
AttributeError: module 'posts.views' has no attribute 'home'

This is Django 2.0 with Python 3.6 using the built in test server (no where near production environment yet). I&#8217;m running my code inside an activated virtual environment. These are the contents of my requirements.txt:

```
Django==2.0.13
Pillow==5.4.1
psycopg2==2.7.7
psycopg2-binary==2.7.7
pytz==2018.9
```

Pretty basic, right?

**urls.py** in my primary project folder:

```
from django.contrib import admin
from django.urls import path
from . import views
from posts import views


urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^$', views.home, name='home'),
    url(r'^result/', views.result, name='result'),
    url(r'^james/', views.posts, name='james'), 
```

**views.py** (in app folder):

```
from django.shortcuts import render

# Create your views here.

def james(request):
    return render(request, 'posts/james.html')
As you can see, I've named my function "james", as well as my template.
```

Here is **posts/templates/posts/james.htm**l:

```
from django.shortcuts import render

# Create your views here.

def james(request):
    return render(request, 'posts/james.html')
```

Finally, here is my file tree and directory structure: [file tree]("https://i.imgur.com/j8ZS9wS.jpg").

When running the sever, I am expecting to see "You are in James' posts!" in bold text when navigating to localhost:8000/posts. Instead I am receiving:

> $ python manage.py runserver     
Performing system checks...
Unhandled exception in thread started by <function check_errors.<locals>.wrapper at 0x7f41c70286a8>
Traceback (most recent call last):
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/utils/autoreload.py", line 225, in wrapper
    fn(*args, **kwargs)
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/core/management/commands/runserver.py", line 120, in inner_run
    self.check(display_num_errors=True)
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/core/management/base.py", line 364, in check
    include_deployment_checks=include_deployment_checks,
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/core/management/base.py", line 351, in _run_checks
    return checks.run_checks(**kwargs)
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/core/checks/registry.py", line 73, in run_checks
    new_errors = check(app_configs=app_configs)
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/core/checks/urls.py", line 13, in check_url_config
    return check_resolver(resolver)
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/core/checks/urls.py", line 23, in check_resolver
    return check_method()
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/urls/resolvers.py", line 399, in check
    for pattern in self.url_patterns:
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/utils/functional.py", line 36, in __get__
    res = instance.__dict__[self.name] = self.func(instance)
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/urls/resolvers.py", line 540, in url_patterns
    patterns = getattr(self.urlconf_module, "urlpatterns", self.urlconf_module)
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/utils/functional.py", line 36, in __get__
    res = instance.__dict__[self.name] = self.func(instance)
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/site-packages/django/urls/resolvers.py", line 533, in urlconf_module
    return import_module(self.urlconf_name)
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/venv/lib/python3.6/importlib/__init__.py", line 126, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "<frozen importlib._bootstrap>", line 994, in _gcd_import
  File "<frozen importlib._bootstrap>", line 971, in _find_and_load
  File "<frozen importlib._bootstrap>", line 955, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 665, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 678, in exec_module
  File "<frozen importlib._bootstrap>", line 219, in _call_with_frames_removed
  File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact/CC_Redact/urls.py", line 10, in <module>
    url(r'^$', views.home, name='home'),
AttributeError: module 'posts.views' has no attribute 'home'

edit: btw: [Here is my project on GitHub]("https://github.com/Angeles4four/CC_Redact"). I am accepting pull requests.

---

### Post by Drone4four on 2019-04-14
I changed **def james(request)** to **def posts(request)**. I also then defined both the **home** and **result** functions inside **posts.views**. My server runs successfully now. :cool:

---

