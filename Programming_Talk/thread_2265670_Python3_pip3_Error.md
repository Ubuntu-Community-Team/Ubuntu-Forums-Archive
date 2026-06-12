---
title: "Python3 pip3 Error"
date: 2015-02-16
forum: Programming Talk
---

### Post by benrob0329 on 2015-02-16
I don't have very much experience in Python3. But whenever I try to install a library in pip3  get an error like this:

```

Command python setup.py egg_info failed with error code 1 in /tmp/pip_build_root/rope
Storing debug log for failure in /home/me/.pip/pip.log

```

:confused:

I have tried --upgrade setuptools, but without success. Any ideas?

---

### Post by benrob0329 on 2015-02-16
**sudo pip3 install --upgrade setuptools gives** me this:


```
Cleaning up...
Exception:
Traceback (most recent call last):
  File "/usr/local/lib/python3.4/dist-packages/distribute-0.6.39-py3.4.egg/pkg_resources.py", line 2481, in _dep_map
    return self.__dep_map
  File "/usr/local/lib/python3.4/dist-packages/distribute-0.6.39-py3.4.egg/pkg_resources.py", line 2306, in __getattr__
    raise AttributeError(attr)
AttributeError: _DistInfoDistribution__dep_map

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/pip/basecommand.py", line 122, in main
    status = self.run(options, args)
  File "/usr/lib/python3/dist-packages/pip/commands/install.py", line 278, in run
    requirement_set.prepare_files(finder, force_root_egg_info=self.bundle, bundle=self.bundle)
  File "/usr/lib/python3/dist-packages/pip/req.py", line 1265, in prepare_files
    req_to_install.extras):
  File "/usr/local/lib/python3.4/dist-packages/distribute-0.6.39-py3.4.egg/pkg_resources.py", line 2254, in requires
    dm = self._dep_map
  File "/usr/local/lib/python3.4/dist-packages/distribute-0.6.39-py3.4.egg/pkg_resources.py", line 2483, in _dep_map
    self.__dep_map = self._compute_dependencies()
  File "/usr/local/lib/python3.4/dist-packages/distribute-0.6.39-py3.4.egg/pkg_resources.py", line 2516, in _compute_dependencies
    common = frozenset(reqs_for_extra(None))
  File "/usr/local/lib/python3.4/dist-packages/distribute-0.6.39-py3.4.egg/pkg_resources.py", line 2513, in reqs_for_extra
    if req.marker_fn(override={'extra':extra}):
  File "/usr/local/lib/python3.4/dist-packages/distribute-0.6.39-py3.4.egg/_markerlib/markers.py", line 109, in marker_fn
    return eval(compiled_marker, environment)
  File "<environment marker>", line 1, in <module>
NameError: name 'sys_platform' is not defined

Storing debug log for failure in /home/me/.pip/pip.log
```

---

### Post by ofnuts on 2015-02-17
Might be a bug.... shouldn't that be [sys.platform](https://docs.python.org/2/library/sys.html#sys.platform)?

---

### Post by benrob0329 on 2015-02-17
Not shure what you mean. I'm still a noob.

---

### Post by ofnuts on 2015-02-17
The thing you are trying to use has two bugs: a first one, and then the bug catching code also has a bug. So either: 
[LIST]
[*]it's a rather buggy software (not sure you want to continue using it in that case)
[*]it's not compatible with your Python or whatever...
[*]you aren't using it properly
[/LIST]

Might be worth hunting the developers and asking questions.

---

### Post by benrob0329 on 2015-02-17
The same thing happens with setup.py scripts. That package wast rope, used by spyder3. Soya3d (compatible with python3) setup.py does the same thing as pip3 (or a very similar error.). I am using the official version of python3.4 .

---

