---
title: "Django symbolic link not working"
date: 2010-12-19
forum: Programming Talk
---

### Post by duvalfan25 on 2010-12-19
I am trying to set up django in Ubuntu 10.04 and i am trying to creat symbolic links to the /usr/local/bin folder so i dont have to type in the whole path and can just type "django_admin.py" etc. My project is located in a subdirectory of /home/<username> folder called django_projects. I have done the following to get myself set up:

[COLOR=#C20CB9]**ln**[/COLOR] [COLOR=#660033]-s[/COLOR] [COLOR=#000000]**`**[/COLOR][COLOR=#7A0874]**pwd**[/COLOR][COLOR=#000000]**`/**[/COLOR]django_src[COLOR=#000000]**/**[/COLOR]django /usr/lib/python2.6/dist-packages[COLOR=#000000]**/**[/COLOR]django
 
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**cp**[/COLOR] ~[COLOR=#000000]**/**[/COLOR]django_src[COLOR=#000000]**/**[/COLOR]django[COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR]django-admin.py [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]local[COLOR=#000000]**/**[/COLOR]bin

[COLOR=#7A0874]**cd**[/COLOR] ~[COLOR=#000000]**/**[/COLOR]
 
[COLOR=#C20CB9]**mkdir**[/COLOR] django_projects
 
[COLOR=#C20CB9]**mkdir**[/COLOR] django_templates
 
[COLOR=#C20CB9]**mkdir**[/COLOR] media

[COLOR=#7A0874]**cd**[/COLOR] [COLOR=#000000]**/**[/COLOR]var[COLOR=#000000]**/**[/COLOR]www
 
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**ln**[/COLOR] [COLOR=#660033]-s[/COLOR]  ~[COLOR=#000000]**/**[/COLOR]media media
 
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**ln**[/COLOR] [COLOR=#660033]-s[/COLOR] ~[COLOR=#000000]**/**[/COLOR]django_src[COLOR=#000000]**/**[/COLOR]django[COLOR=#000000]**/**[/COLOR]contrib[COLOR=#000000]**/**[/COLOR]admin[COLOR=#000000]**/**[/COLOR]media admin_media

but then when i try to do the following:
[COLOR=#7A0874]**cd**[/COLOR] ~[COLOR=#000000]**/**[/COLOR]django_projects
 
django-admin.py startproject myproject

I get this: 
Traceback (most recent call last):
  File "/usr/local/bin/django-admin.py", line 2, in <module>
    from django.core import management
ImportError: No module named django.core

Please help.. I need to get this started up relatively quick and I am somewhat a 
Linux noob.. Thanks!

---

