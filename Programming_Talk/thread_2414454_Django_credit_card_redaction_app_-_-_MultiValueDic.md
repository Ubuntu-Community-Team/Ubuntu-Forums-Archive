---
title: "Django credit card redaction app - - MultiValueDictKeyError"
date: 2019-03-10
forum: Programming Talk
---

### Post by Drone4four on 2019-03-10
I’m trying to run a basic Django app which redacts a 16 digit number entered by the user. I had a it running a few minutes ago. I’m not sure what I changed, but now I am getting a MultiValueDictKeyError. I’ve triple checked every variable. The only dictionary in my project is in views.py at line 7. As far as I can tell, it’s all accurate and positioned correctly. I don’t recall changing this dictionary or any other operator around this line. I’m stumped. What would you people suggest? Have a look at my setup.

Here is the error and traceback in full: [https://pastebin.com/QwSrmAJx](https://pastebin.com/QwSrmAJx)  

Here is my urls.py:
```
from django.conf.urls import  include, url
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^$', views.home, name='home'),
]
```

views.py:
```
from django.http import HttpResponse
from django.shortcuts import render

def home(request):
    number = request.GET['ccEntry']
    redacted_num = 'xxxx xxxx xxxx {}'.format(number[-4:])
    return render(request, 'home.html', {'number':number, 'redacted_num':redacted_num})

```

Template (home.html): [https://pastebin.com/S2qxzRPG](https://pastebin.com/S2qxzRPG)

(I would have included the contents of my home.html template but vBulletin gave me a 403 error.)

Here is the traceback:
```
Here is the error, traceback and Request information:

MultiValueDictKeyError at /
'ccEntry'
Request Method:
GET
Request URL:
http://127.0.0.1:8000/
Django Version:
2.0.2
Exception Type:
MultiValueDictKeyError
Exception Value:
'ccEntry'
Exception Location:
/home/<user>/.local/lib/python3.7/site-packages/django/utils/datastructures.py in __getitem__, line 79
Python Executable:
/usr/sbin/python
Python Version:
3.7.2
Python Path:
['/home/<user>/dev/projects/python/2018-and-2019/cel2fah-original_with_CC-redact-project-_Django202/first_project_attempt',
 '/usr/lib/python37.zip',
 '/usr/lib/python3.7',
 '/usr/lib/python3.7/lib-dynload',
 '/home/<user>/.local/lib/python3.7/site-packages',
 '/usr/lib/python3.7/site-packages',
 '/usr/lib/python3.7/site-packages/setuptools-40.6.2-py3.7.egg']
Server time:

Thu, 7 Mar 2019 17:39:40 +0000

Environment:
Request Method: GET
Request URL: http://127.0.0.1:8000/

Django Version: 2.0.2
Python Version: 3.7.2
Installed Applications:
['django.contrib.admin',
 'django.contrib.auth',
 'django.contrib.contenttypes',
 'django.contrib.sessions',
 'django.contrib.messages',
 'django.contrib.staticfiles']
Installed Middleware:
['django.middleware.security.SecurityMiddleware',
 'django.contrib.sessions.middleware.SessionMiddleware',
 'django.middleware.common.CommonMiddleware',
 'django.middleware.csrf.CsrfViewMiddleware',
 'django.contrib.auth.middleware.AuthenticationMiddleware',
 'django.contrib.messages.middleware.MessageMiddleware',
 'django.middleware.clickjacking.XFrameOptionsMiddleware']

Traceback:
File "/home/<user>/.local/lib/python3.7/site-packages/django/utils/datastructures.py" in __getitem__
  77.             list_ = super().__getitem__(key)

During handling of the above exception ('ccEntry'), another exception occurred:

File "/home/<user>/.local/lib/python3.7/site-packages/django/core/handlers/exception.py" in inner
  35.             response = get_response(request)

File "/home/<user>/.local/lib/python3.7/site-packages/django/core/handlers/base.py" in _get_response
  128.                 response = self.process_exception_by_middleware(e, request)

File "/home/<user>/.local/lib/python3.7/site-packages/django/core/handlers/base.py" in _get_response
  126.                 response = wrapped_callback(request, *callback_args, **callback_kwargs)

File "/home/<user>/dev/projects/python/2018-and-2019/cel2fah-original_with_CC-redact-project-_Django202/first_project_attempt/first_project_attempt/views.py" in home
  5.     number = request.GET['ccEntry']

File "/home/<user>/.local/lib/python3.7/site-packages/django/utils/datastructures.py" in __getitem__
  79.             raise MultiValueDictKeyError(key)

Exception Type: MultiValueDictKeyError at /
Exception Value: 'ccEntry'

Request information
USER
AnonymousUser
GET
No GET data
POST
No POST data
FILES
No FILES data

```

I’ve double checked to make sure that I include my data in my form element as you can see in the above template. The data is present as “ccEntry” in both home.html and in views.py.

In my home.html template, even though the instructor instructor in my Udemy course doesn’t use it, I added a method="get" attribute to my HTML form tag. This didn’t change anything.

I also looked up “[Django request.GET]("https://stackoverflow.com/questions/3500859/django-request-get")”. Based on that SO answer, In my views.py I changed the line (where I declare the number variable) from number = request.GET['ccEntry'] to number = request.GET.get['ccEntry', None]. That gives a different error (a type error this time): [https://pastebin.com/L81LVtzi](https://pastebin.com/L81LVtzi)
   

This is a long shot, but I thought I would share a link to my source code hosted on GitHub with a requirements.txt included. If any of you would like to test this out yourself, I am accepting pull requests. Here it is: [https://github.com/Angeles4four/CC_Redact](https://github.com/Angeles4four/CC_Redact)

---

### Post by norobro on 2019-03-12
[SIZE=2]I played around with your app and got it work with the following hack.

views.py: ```
from django.http import HttpResponse
from django.shortcuts import render


def home(request):
    if 'ccEntry' in request.GET:
        number = request.GET['ccEntry']
        redacted_num = 'xxxx xxxx xxxx {}'.format(number[-4:])
        return render(request, 'home.html', {'number':number, 'redacted_num':redacted_num})
    else:
        return render(request, 'home.html')
```


[/SIZE]It seems that something in your code is triggering an additional 'GET' request. [SIZE=2]I don't know enough about django to offer an explanation for this behavior. I turned on logging and took a look at the output from curl as suggested in this post ([https://groups.google.com/forum/#!msg/django-users/CRMMYWix_60/KEIkguUcqxYJ](https://groups.google.com/forum/#!msg/django-users/CRMMYWix_60/KEIkguUcqxYJ)) but did not spot anything.


HTH[/SIZE]

---

### Post by Drone4four on 2019-03-14
Howdy **@norobro**!

Eureka! This hack works! Thank you very much for taking the time to play around with my project to find a solution.  I committed and pushed my changes up to GitHub.

I know you said that you&#8217;re not an expert in Django. That's OK. :p I will ask on Django forums elsewhere  about why this condition is required for Django to execute views.py properly and then I&#8217;ll be sure to report back here with the explanation.

Thanks again, my friend!

---

### Post by Drone4four on 2019-03-14
Here’s the explanation for why this hack works the way it does. It’s simple.  If a user lands on the webpage and the ccEntry parameter is not present, it throws MultiValueDictKeyError. So the conditional checks for the presence of the parameter.

The forum member over at Django user Google group [clarifies in greater detail]("https://groups.google.com/forum/#!topic/django-users/0hOyDZnu4L0"):

> When a user requests your home page's URL the first time in order to load your home.html file, the GET request they send to your server does not contain the 'ccEntry' parameter, which raised the MultiValueDictKeyError whenever your view was executing. However, in your edited view, you take care of that by first checking whether the GET request contains 'ccEntry', which is why it is working correctly now.

---

### Post by norobro on 2019-03-14
[SIZE=2]Perusing the Mozilla Django tutorial I found this forms request flow chart: [https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms#Django_form_handling_process](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms#Django_form_handling_process)

Apparently the initial request is an empty "GET" request, i.e. no variables, which triggers your error.

Perhaps a more Djangoic (Pythonic) check would be to test if the dictionary HttpRequest.GET  or HttpRequest.content_params contain data ([https://docs.djangoproject.com/en/2.1/ref/request-response/#django.http.HttpRequest.content_params](https://docs.djangoproject.com/en/2.1/ref/request-response/#django.http.HttpRequest.content_params)): ```
def home(request):    
    if request.GET:
        number = request.GET['ccEntry']
        redacted_num = 'xxxx xxxx xxxx {}'.format(number[-4:])
        return render(request, 'home.html', {'number':number, 'redacted_num':redacted_num})
    else:
        return render(request, 'home.html')

```[/SIZE]

---

