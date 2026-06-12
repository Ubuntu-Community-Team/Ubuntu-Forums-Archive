---
title: "Django debug of templates and home.html"
date: 2017-11-11
forum: Programming Talk
---

### Post by Drone4four on 2017-11-11
I am having fun trying to initiate a django project with some apps.  I am taking an awesome course on udemy called, *The Ultimate Beginner's Guide to Django*. I was able to follow along and I have a basic blog up and running.  Now I am back tracking a little by starting over, this time using a supplementary Django cheat sheet.  I encountered a number of issues and resolved them but now I find myself stuck.  

When I try navigating to my new homepage, Django provides me with [this debug traceback](https://pastebin.com/QqXhgVM3). Django is telling me here that the templates directory doesn’t exist, when it clearly does.  [Here is a screenshot of Atom](https://imgur.com/a/mth7B) so you can see my project’s file tree.  As you can see my directory tree for my project, there is an folder which is called, blogitems. and within the blogitems folder is a sub-folder called, templates, then blogitems again and finally my file, home.html

It’s rather confusing.  I don’t like the redundancy and the recursive nature of all the app files and directory names. Maybe this is my problem.  Can any of your make sense of my debug output to explain why I am getting the error? Can anyone please provide some clarity here?

Here is the cheat sheet:
> 
[list=1]
**Creating a Django App**
[*]Open terminal and navigate to django project folder (where manage.py exists)
[*]django-admin startapp [app name] # use pluralised names, e.g. posts
[*]Navigate to new app folder.
[*]Create new subfolder called “templates”
[*]Navigate to new templates folder.
[*]Create new subfolder called same name as your app (e.g. posts)
[*]Go back to project folder
[*]Open project urls.py and add “from [appname] import views”. Then add url path for new view.
e.g. url(r’^$’, views.home, name=‘home’)
[*]Open views.py and add:
```
def home(request):
         return render(request, ‘posts/home.html’)
```
[*]Navigate to projectfolder\appfolder\templates\appfolder
[*]Create new file ‘home.html’
[*]Go to project folder and open settings.py. Scroll down to INSTALLED_APPs and add ‘appname’, to the end of the list of apps.
[/list]


It's this last step where I encounter the error. 

Here are the contents of urls.py: ```
from django.conf.urls import url
from django.contrib import admin
from blogitems import views

urlpatterns = [
    #initialization admin interface:
    url(r'^admin/', admin.site.urls),
    url(r’^$’, views.home, name=‘home’),
]

```

I added the app into the settings.py:
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blogitems',
]
```

Is there any other information I could provide?

Thanks for your attention.

---

