---
title: "Can't run Cocos2d Python on Ubuntu 16.10"
date: 2016-12-24
forum: Programming Talk
---

### Post by anixon604 on 2016-12-24
Hi guys,

just installed cocos2d python on 16.10 and everytime i try to run a program I get the following error. Any ideas?

```
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
Traceback (most recent call last):
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/pyglet-1.2.4-py3.5.egg/pyglet/__init__.py", line 351, in __getattr__
AttributeError: 'NoneType' object has no attribute 'TextureRegion'

```

During handling of the above exception, another exception occurred:


```
Traceback (most recent call last):
  File "/home/anthony/PycharmProjects/SamePop/src/SamePop.py", line 5, in <module>
    from cocos import director
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/cocos2d-0.6.4-py3.5.egg/cocos/__init__.py", line 107, in <module>
    from cocos import cocosnode
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/cocos2d-0.6.4-py3.5.egg/cocos/cocosnode.py", line 51, in <module>
    from cocos.director import director
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/cocos2d-0.6.4-py3.5.egg/cocos/director.py", line 134, in <module>
    import cocos.fps
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/cocos2d-0.6.4-py3.5.egg/cocos/fps.py", line 57, in <module>
    import pyglet.font
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 664, in _load_unlocked
  File "<frozen importlib._bootstrap>", line 634, in _load_backward_compatible
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/pyglet-1.2.4-py3.5.egg/pyglet/font/__init__.py", line 585, in <module>
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
Unexpected error loading library libgdk-x11-2.0.so.0: /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0: undefined symbol: FcWeightToOpenType
  File "<frozen importlib._bootstrap>", line 664, in _load_unlocked
  File "<frozen importlib._bootstrap>", line 634, in _load_backward_compatible
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/pyglet-1.2.4-py3.5.egg/pyglet/font/freetype.py", line 40, in <module>
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 664, in _load_unlocked
  File "<frozen importlib._bootstrap>", line 634, in _load_backward_compatible
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/pyglet-1.2.4-py3.5.egg/pyglet/font/base.py", line 141, in <module>
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/pyglet-1.2.4-py3.5.egg/pyglet/__init__.py", line 357, in __getattr__
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 664, in _load_unlocked
  File "<frozen importlib._bootstrap>", line 634, in _load_backward_compatible
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/pyglet-1.2.4-py3.5.egg/pyglet/image/__init__.py", line 2582, in <module>
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/pyglet-1.2.4-py3.5.egg/pyglet/image/codecs/__init__.py", line 214, in add_default_image_codecs
  File "<frozen importlib._bootstrap>", line 969, in _find_and_load
  File "<frozen importlib._bootstrap>", line 958, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 664, in _load_unlocked
  File "<frozen importlib._bootstrap>", line 634, in _load_backward_compatible
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/pyglet-1.2.4-py3.5.egg/pyglet/image/codecs/gdkpixbuf2.py", line 45, in <module>
  File "/home/anthony/anaconda3/lib/python3.5/site-packages/pyglet-1.2.4-py3.5.egg/pyglet/lib.py", line 135, in load_library
  File "/home/anthony/anaconda3/lib/python3.5/ctypes/__init__.py", line 425, in LoadLibrary
    return self._dlltype(name)
  File "/home/anthony/anaconda3/lib/python3.5/ctypes/__init__.py", line 347, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0: undefined symbol: FcWeightToOpenType
```

---

### Post by wildmanne39 on 2016-12-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by anixon604 on 2016-12-24
Wow that's so clean! Thanks for helping me with my post.

---

