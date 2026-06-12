---
title: "Django module view has no attribute?"
date: 2019-04-01
forum: Programming Talk
---

### Post by Drone4four on 2019-04-01
I’m taking a Udemy course by Nick Walter and rather than copying line by line, I’m trying to branch out and experiment on my own.  

The purpose of the website I am creating is for a small blog, with the ability to redact string input (in an HTML form) from the user. There is also a word counter for the body content of the blog.

I got Django running but as soon as I started adding the code I wrote, Django stopped running properly. 

Here is the traceback in full: [https://pastebin.com/8HtdNwPP](https://pastebin.com/8HtdNwPP) 

The main issue shows at the bottom:

> File "/home/<user>/dev/projects/python/2018-and-2019/CC_Redact_Iter2/CC_Redact_Iter2/urls.py", line 28, in <module>
[B]    path('^james/', views.posts, name='james'),
AttributeError: module 'counters.views' has no attribute 'posts’[/B]


Based on this traceback, I gather I have probably misnamed a function or a file name or template but I can’t for the life of me figure which one or where. 

My entire source code repo can be found here: [https://github.com/Angeles4four/CC_Redact_Iter2](https://github.com/Angeles4four/CC_Redact_Iter2)

Here are some of the relevant files involved.

urls.py:
```
from django.contrib import admin
from django.urls import path
# from . import views
from posts import views
from redactors import views
from counters import views
urlpatterns = [
   path('admin/', admin.site.urls),
   path('^$', views.home, name='home'),
   path('^result/', views.result, name='result'),
   path('^seth/', views.counters, name='seth'),
   path('^james/', views.posts, name='james'),
   path('^james/', views.redactors, name='simon'),
]
```


counters/views.py:
```
from django.http import HttpResponse
from django.shortcuts import render
def home(request):
   if 'ccEntry' in request.GET:
       number = request.GET['ccEntry']
       redacted_num = 'xxxx xxxx xxxx {}'.format(number[-4:])
       return render(request, 'result.html', {'number':number, 'redacted_num':redacted_num})
   else:
       return render(request, 'home.html')
def result(request):
    return render(request, 'result.html')
def counters(request):
   return render(request, 'counters/james.html')
```

Here is my file tree: [https://imgur.com/a/BUTKKEH](https://imgur.com/a/BUTKKEH)

Contents of requirements.txt:
> Django==2.0.13
Pillow==5.4.1
psycopg2==2.7.7
psycopg2-binary==2.7.7
pytz==2018.9

If there are other files in my project that if you wish to view, you can click through the file tree as it appears on GitHub (linked to above).

---

### Post by norobro on 2019-04-02
The problem is with these three lines:```
from posts import views
from redactors import views
from counters import views
```You are overwriting views with each import ending up with only the content of counters.views (home, result, counters).

Also, you need to import and use re_path() for the regex(s) [https://docs.djangoproject.com/en/2.1/ref/urls/#](https://docs.djangoproject.com/en/2.1/ref/urls/#)

Try something like this:```
from django.contrib import admin
from django.urls import path, re_path
# from . import views
from posts.views import *
from redactors.views import *
from counters.views import *
urlpatterns = [
   path('admin/', admin.site.urls),
   re_path('^$', home, name='home'),
   re_path('^result/', result, name='result'),
   re_path('^seth/', counters, name='seth'),
   re_path('^james/', posts, name='james'),
   re_path('^james/', redactors, name='simon'),
]
```

---

### Post by Drone4four on 2019-04-02
Thank you, **@norobro**!

So the way I was importing my views was the issue! I see that re_path is necessary for invoking regex url patterns. The official Django doc you shared helps.

My Django project now runs. The system check when I run my Django server now reports no issues.

These web addresses render as I expect in my web browser:
[http://localhost:8000/simon/](http://localhost:8000/simon/)
[http://localhost:8000/james/](http://localhost:8000/james/)
[http://localhost:8000/seth/](http://localhost:8000/seth/)

(I know you people can&#8217;t test these addresses because my server is running locally - - it&#8217;s not deployed in the cloud yet.)

However I am now getting a &#8216;TemplateDoesNotExist at /&#8217;. Full traceback: [https://pastebin.com/iXX1Dp2Z](https://pastebin.com/iXX1Dp2Z)

These are the key lines which jump out at me:

```
django.template.loaders.app_directories.Loader: /home/gnull/dev/projects/python/2018-and-2019/CC_Redact_Iter2/posts/templates/home.html (Source does not exist)
django.template.loaders.app_directories.Loader: /home/gnull/dev/projects/python/2018-and-2019/CC_Redact_Iter2/redactors/templates/home.html (Source does not exist)
django.template.loaders.app_directories.Loader: /home/gnull/dev/projects/python/2018-and-2019/CC_Redact_Iter2/counters/templates/home.html (Source does not exist)
```

Here is my partial understanding of what this traceback is saying: Django is trying to load the home.html template. It&#8217;s looking inside my app directories - - that is, inside redactors/templates/ but it can&#8217;t find them. I figure this is because I have placed home.html inside redactors/templates/redactors/

To test this I copied **redactors/templates/redactors/home.html** to **redactors/templates/home.html** and then presto! [http://localhost:8000/](http://localhost:8000/) loaded as I intended!! Django is now serving my homepage beautifully.

But this *isn&#8217;t quite* what I want. 

I&#8217;d like to retain my original file tree with home.html nested inside redactors/templates/redactors/. This file structure is recursive, redundant, unintuitive, and a little confusing however the Udemy instructor Nick Walter explains that in the Python world, it is best practices to include this recursive file structure. So with this in mind, I figure I have to explicitly tell Django somewhere (I&#8217;m thinking maybe in urls.py) to descend one more directory to find home.html but I am not sure where to make this change. What would you people recommend?

edit: By the way, if it helps, here is my file tree showing how I have templates nested as I describe above: [https://imgur.com/a/QaiHQtz](https://imgur.com/a/QaiHQtz)

Thanks again, **@norobro**, for you help so far.

For your reference, if interested, here is my project with recent changes pushed to my GitHub repo: [https://github.com/Angeles4four/CC_Redact_Iter2](https://github.com/Angeles4four/CC_Redact_Iter2)

---

### Post by norobro on 2019-04-02
[SIZE=2][FONT=arial]You're welcome.

Put the paths to your templates in the 'DIRS' list, under 'TEMPLATES' in settings.py. 
[https://github.com/Angeles4four/CC_Redact_Iter2/blob/master/CC_Redact_Iter2/settings.py#L60](https://github.com/Angeles4four/CC_Redact_Iter2/blob/master/CC_Redact_Iter2/settings.py#L60)[/FONT][/SIZE]

---

### Post by Drone4four on 2019-04-04
I rummaged around Google for more clues. Based on a SO question titled &#8220;[TemplateDoesNotExist at / Django?]("https://stackoverflow.com/questions/42483858/templatedoesnotexist-at-django")&#8221;. In settings.py where the TEMPLATES variable is declared as a dictionary (the line where **@norobro** drew my attention to), for the &#8216;DIRS&#8217; key, as the value I assign: os.path.join(BASE_DIR, 'redactors/templates/redactors/'). 

Now it runs perfectly!

Thanks, **@norobro**!

---

