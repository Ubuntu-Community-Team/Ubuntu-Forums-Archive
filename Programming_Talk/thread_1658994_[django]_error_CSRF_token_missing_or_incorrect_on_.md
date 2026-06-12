---
title: "[django] error CSRF token missing or incorrect on POST reciever"
date: 2011-01-03
forum: Programming Talk
---

### Post by Crazedpsyc on 2011-01-03
I tried to make a quick search box for my site-in-progress and expected it to be as simple as keeping the database updated. Unfortunately I ran into the following error as soon as I POSTed a query:
>     **Forbidden (403)**

   CSRF verification failed. Request aborted.
  
     **Help**

          Reason given for failure:
         CSRF token missing or incorrect.              In general, this can occur when there is a genuine Cross Site Request Forgery, or when   [Django's   CSRF mechanism]("http://docs.djangoproject.com/en/dev/ref/contrib/csrf/#ref-contrib-csrf") has not been used correctly.  For POST forms, you need to   ensure:
    
[LIST]
[*]The view function uses [RequestContext]("http://docs.djangoproject.com/en/dev/ref/templates/api/#subclassing-context-requestcontext")     for the template, instead of Context.
[*]In the template, there is a {% csrf_token     %} template tag inside each POST form that     targets an internal URL.
[*]If you are not using CsrfViewMiddleware, then you must use     csrf_protect on any views that use the csrf_token     template tag, as well as those that accept the POST data.
[/LIST]
    You're seeing the help section of this page because you have DEBUG =   True in your Django settings file. Change that to False,   and only the initial error message will be displayed.  
    You can customize this page using the CSRF_FAILURE_VIEW setting.
 
     
I tried adding "{% csrf_token     %}" to my template, but still got the same error. I don't really know what the rest of the suggestions mean:confused:, so any translation help would be appreciated

---

### Post by Crazedpsyc on 2011-01-04
KerBUmp

---

### Post by Crazedpsyc on 2011-01-05
and a bump! No one knows? any more info needed?

---

### Post by Crazedpsyc on 2011-01-09
bump

---

### Post by Crazedpsyc on 2011-01-11
bump

---

### Post by Crazedpsyc on 2011-01-15
bump

---

### Post by Crazedpsyc on 2011-01-15
bump

---

### Post by llanitedave on 2011-01-15
Have you tried the django-users google group?

[http://groups.google.com/group/django-users]("http://groups.google.com/group/django-users")

---

### Post by Crazedpsyc on 2011-01-17
Thanks, I'll repost there ;)

---

