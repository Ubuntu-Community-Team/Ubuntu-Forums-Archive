---
title: "Kivy easy_install problem"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by r3bol on 2012-05-01
I'm having a problem installing kivy on Ubuntu 12.04. I've installed Cython [as instructed]("http://kivy.org/docs/installation/installation-linux.html") and then tried...
sudo easy_install kivy

error:
```
[sudo] password for asdf: 
Searching for kivy
Reading http://pypi.python.org/simple/kivy/
Best match: Kivy 1.2.0
Downloading http://pypi.python.org/packages/source/K/Kivy/Kivy-1.2.0.tar.gz#md5=468da8a353c2ea4936eb92d71403c960
Processing Kivy-1.2.0.tar.gz
Running Kivy-1.2.0/setup.py -q bdist_egg --dist-dir /tmp/easy_install-6_dj0o/Kivy-1.2.0/egg-dist-tmp-vCKZig
[INFO   ] Kivy v1.2.0
WARNING: GLES 2.0 headers are not found
Fallback to Desktop opengl headers.
Build configuration is:
 * use_opengl_es2  =  False
 * use_glew  =  False
 * use_opengl_debug  =  False
 * use_mesagl  =  False
Generate config.h
Generate config.pxi
/tmp/easy_install-6_dj0o/Kivy-1.2.0/kivy/graphics/texture.c:4:20: fatal error: Python.h: No such file or directory
compilation terminated.
 error: Setup script exited with error: command 'gcc' failed with exit status 1
asdf@asdf:~$ 
```

Any ideas?
Thanks.

---

### Post by datenhalde on 2012-05-01
I don't even know, what kivy is, but the error complaining about not finding python.h looks like you might be missing a *-dev package.
Maybe sudo apt-get install python-dev will help.

---

### Post by silmaril8n on 2012-11-26
I just ran across this myself (it's still an issue). You just need to install the rest of the deps for kivy.

```
sudo apt-get install python-setuptools python-pygame python-opengl \
  python-gst0.10 python-enchant gstreamer0.10-plugins-good cython python-dev \
  build-essential libgl1-mesa-dev libgles2-mesa-dev
```

```
sudo pip install kivy
```

[http://kivy.org/docs/installation/installation-ubuntu.html]("http://kivy.org/docs/installation/installation-ubuntu.html")

---

