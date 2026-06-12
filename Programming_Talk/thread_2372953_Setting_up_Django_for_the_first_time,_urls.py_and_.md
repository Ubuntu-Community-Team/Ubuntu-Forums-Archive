---
title: "Setting up Django for the first time, urls.py and settings.py"
date: 2017-09-30
forum: Programming Talk
---

### Post by Drone4four on 2017-09-30
I&#8217;m playing with Django for the first time.  I am using a guide called, &#8220;[Python from Scratch - Creating a Dynamic Website]("https://www.youtube.com/watch?v=bRnm8f6Wavk")&#8221;  by **Tuts+ Code** from YouTube.  It&#8217;s kinda old.  It was first posted in November 2011 and Django has evolved considerably.  I&#8217;ve had to try different commands, like &#8216;syncdb&#8217; is no longer used.  Now it&#8217;s &#8216;migrate&#8217;. Yes, Tuts+ Code is over 6 years old, but it&#8217;s the best Django tutorial on the web in terms of explanations and teaching style. Anyways.

I&#8217;m getting an error saying there is something wrong with my settings.py:```

$ python ../manage.py runserver
Performing system checks...

Unhandled exception in thread started by <function wrapper at 0x7fe4876e76e0>
Traceback (most recent call last):
  File "/home/gnull/.local/lib/python2.7/site-packages/django/utils/autoreload.py", line 228, in wrapper
    fn(*args, **kwargs)
  File "/home/gnull/.local/lib/python2.7/site-packages/django/core/management/commands/runserver.py", line 125, in inner_run
    self.check(display_num_errors=True)
  File "/home/gnull/.local/lib/python2.7/site-packages/django/core/management/base.py", line 359, in check
    include_deployment_checks=include_deployment_checks,
  File "/home/gnull/.local/lib/python2.7/site-packages/django/core/management/base.py", line 346, in _run_checks
    return checks.run_checks(**kwargs)
  File "/home/gnull/.local/lib/python2.7/site-packages/django/core/checks/registry.py", line 81, in run_checks
    new_errors = check(app_configs=app_configs)
  File "/home/gnull/.local/lib/python2.7/site-packages/django/core/checks/urls.py", line 16, in check_url_config
    return check_resolver(resolver)
  File "/home/gnull/.local/lib/python2.7/site-packages/django/core/checks/urls.py", line 26, in check_resolver
    return check_method()
  File "/home/gnull/.local/lib/python2.7/site-packages/django/urls/resolvers.py", line 254, in check
    for pattern in self.url_patterns:
  File "/home/gnull/.local/lib/python2.7/site-packages/django/utils/functional.py", line 35, in __get__
    res = instance.__dict__[self.name] = self.func(instance)
  File "/home/gnull/.local/lib/python2.7/site-packages/django/urls/resolvers.py", line 405, in url_patterns
    patterns = getattr(self.urlconf_module, "urlpatterns", self.urlconf_module)
  File "/home/gnull/.local/lib/python2.7/site-packages/django/utils/functional.py", line 35, in __get__
    res = instance.__dict__[self.name] = self.func(instance)
  File "/home/gnull/.local/lib/python2.7/site-packages/django/urls/resolvers.py", line 398, in urlconf_module
    return import_module(self.urlconf_name)
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/home/gnull/Dropbox/TECH/python/2017/beginning-Django/G_Thomas/G_Thomas/urls.py", line 21, in <module>
    url(r'^$', 'blog.views.home', name='home')
  File "/home/gnull/.local/lib/python2.7/site-packages/django/conf/urls/__init__.py", line 85, in url
    raise TypeError('view must be a callable or a list/tuple in the case of include().')
TypeError: view must be a callable or a list/tuple in the case of include().

```
Those last couple of lines in this error message are instructive. I&#8217;m not sure about the case of include() in urls.py but my url declaration indeed is a tuple.  Why is my shell telling me there is something wrong with my tuple when it should be a tuple?  I also swapped out the parentheses with square brackets to see if it would take a list as it says it can.  Either way, same error.

Here are the contents of my urls.py:

```
from django.conf.urls import *
from django.contrib import admin
admin.autodiscover()

urlpatterns = ['',
     # url(r'^admin/', admin.site.urls),
	url(r'^$', 'blog.views.home', name='home')
]

```
Take note of the square brackets and lack of the patterns function (as compared to the presence of the function in the code from the teacher below). Also commented out above is the default urlpattern that came with Django 1.11.  

So the urlpattern in Tuts+ Code&#8217;s actually looks like this:

```
from django.conf.urls.defaults import patterns, include, url
from django.contrib import admin

urlpatterns = patterns (&#8216;&#8217;,
	url(r'^$', &#8216;FirstBlog.views.home&#8217;, name='home'),
)

```
Addressing a related issue with importing the name pattern in urls.py for Django, some folks over [on stackoverflow describe their Djanog urls.py]("https://stackoverflow.com/questions/8074955/cannot-import-name-patterns") configuration file use a simple variable declaration for urlpatterns and don&#8217;t bother with the function patterns() the way the YouTuber explains that it should look like.  Like, the YouTuber uses: &#8216;urlpatterns = patterns( ... )&#8217; whereas the stackoverflow people set it as: &#8216;urlpatterns = [ &#8216;&#8217;, ...].  

I get the sense that I am slightly off in my understanding of the issue. Based on what you see in the traceback, what could be going on with  my scripts?

Is there any other information I could provide?

Thanks in advance.

---

### Post by 3djake on 2017-10-01
You might have better luck following the same steps but using python3 instead of python2.7

---

