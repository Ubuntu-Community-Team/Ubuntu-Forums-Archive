---
title: "Isolating a python environment"
date: 2009-09-07
forum: Programming Talk
---

### Post by hecato on 2009-09-07
Hi there, like you know ubuntu 9.04 come with python2.6 by default, I want to develop a gae app but I think they use python2.5 because running under 2.6 show that they use some deprecated things (hash?).

So Im trying to use app-engine-patch, but it doesnt work and the guy there, say that is because I have 2 python variants, so for isolate python2.5 I have done the next.

```
virtualenv -p python2.5 p25
source p25/bin/activate
```and it prints something like

```
(p25)tyoc@tyoc-laptop:
```If you want to see the full description [http://code.google.com/p/app-engine-patch/issues/detail?id=214](http://code.google.com/p/app-engine-patch/issues/detail?id=214)

But running again ./manage.py runserver show this






```
ERROR:root:Exception encountered handling request
Traceback (most recent call last):
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 2725, in _HandleRequest
    base_env_dict=env_dict)
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 381, in Dispatch
    base_env_dict=base_env_dict)
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 2012, in Dispatch
    self._module_dict)
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 1930, in ExecuteCGI
    reset_modules = exec_script(handler_path, cgi_path, hook)
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 1826, in ExecuteOrImportScript
    exec module_code in script_module.__dict__
  File ".../appenginepatch-sample/common/appenginepatch/main.py", line 15, in <module>
    from appenginepatcher.patch import patch_all, setup_logging
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 996, in decorate
    return func(self, *args, **kwargs)
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 1586, in load_module
    return self.FindAndLoadModule(submodule, fullname, search_path)
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 996, in decorate
    return func(self, *args, **kwargs)
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 1494, in FindAndLoadModule
    description)
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 996, in decorate
    return func(self, *args, **kwargs)
  File ".../appenginepatch-sample/common/.google_appengine/google/appengine/tools/dev_appserver.py", line 1444, in LoadModuleRestricted
    description)
  File ".../appenginepatch-sample/common/appenginepatch/appenginepatcher/patch.py", line 7, in <module>
    from google.appengine.ext import db
ImportError: No module named ext
INFO:root:"GET / HTTP/1.1" 500 -

```


By the way /bin/env python launch me to python2.5 and also from an interactive shell when active I can do 

from google.appengine.ext import db

Without problems... I will give it a shoot later today, so waiting for your tips.

---

### Post by kinggill on 2009-09-07
hey frd can you help me????i have installed ubuntu but when i restart my pc it says boot failure..plzzzz help me my email adress is [email]mostwantedgill@gmail.com[/email].......

---

### Post by wmcbrine on 2009-09-07
I think Holger's advice in that thread is nonsense. AFAICT, Ubuntu isolates multiple installations of Python perfectly well, without any need to resort to additional measures. But I'm not really familiar with app-engine-patch.

---

### Post by hecato on 2009-09-07
That is what I thinked, thought what make me "doubt" is the line that he write "And obviously your try to 'call python2.5' doesn't work as intended." I dont see how that statment can sustain itself. 

So I ask someone to try the app...   download * [http://app-engine-patch.googlecode.com/files/app-engine-patch-1.1RC.zip](http://app-engine-patch.googlecode.com/files/app-engine-patch-1.1RC.zip)
 * [http://googleappengine.googlecode.com/files/google_appengine_1.2.0.zip](http://googleappengine.googlecode.com/files/google_appengine_1.2.0.zip)


[LIST]
[*]Then unzip them
[*]move google_appengine to app-engine-patch/common/.google_appengine
[*]Inside app-engine-patch run $ ./manage.py runserver
[*]if it run, click the reset or create admin.
[/LIST]
By the way, I ask also here, because I think people here are not in the mod of "obviously". Also dont know, but if... he is the mantainer?? and dont wanting to see if this problem can be replicated... thus I'm out of look.


I will give an extra level of isolation...but later :)... in about 2 hours or so. I think if I can isolate the escenario enought he will not have sustain in said that my problem is because I have 2 pythons...

---

### Post by Druke on 2009-09-11
I do GAE work quite a bit using eclipse's pydev, using it's project manager it's easy to set which version of python you want to use for running everything...

and by hand iirc "python2.5 ./manage.py runserver" worked just fine.

---

### Post by Cerin on 2010-04-20
> **Druke said:**
> I do GAE work quite a bit using eclipse's pydev, using it's project manager it's easy to set which version of python you want to use for running everything...

and by hand iirc "python2.5 ./manage.py runserver" worked just fine.

Define "worked". Running that command doesn't immediately give me an error, but when I try and visit any page in the aep sample site, I get the error:

    from google.appengine.ext import db
ImportError: No module named ext

Has no one figured this out?

---

