---
title: "lucid 10.04 python2.5 package gae"
date: 2010-05-01
forum: Programming Talk
---

### Post by junapp on 2010-05-01
Hello,
Installed 10.04 on the laptop today, went very smoothly. Noticed python2.5 is no longer available as a package. I need it for google app engine development. Anyone know of an easy way to have 2.5 available? 

Thank you.
```

~$ sudo apt-get install python2.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python2.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python2.5 has no installation candidate

```

---

### Post by P4man on 2010-05-01
You could try getting the package for karmic here:
[http://packages.ubuntu.com/karmic/python2.5](http://packages.ubuntu.com/karmic/python2.5)

but dont blame me if it bricks your system!

---

### Post by junapp on 2010-05-01
yes, I had thought about that but didn't for the reason you state - didn't want to mess up my fun of lucid on the first day. Was thinking about giving that a go in a VM. I had seen a few posts where there are some intermingling dependancies which might jack 2.6. Python being so intertwined with many things I wasn't going to just plow right in. I'll give it a whirl in virtualbox.

---

### Post by bruno.braga on 2010-05-02
It seems python2.5 is out of the package list in lucid.

[http://packages.ubuntu.com/lucid/allpackages?format=txt.gz]("http://packages.ubuntu.com/lucid/allpackages?format=txt.gz")

But it is fairly easy (to newbies) to install it from source:

[http://www.python.org/download/releases/2.5.5/](http://www.python.org/download/releases/2.5.5/)

One catch though, the installation writes a /usr/local/bin/python file (which in the $PATH is searched before /usr/bin/), meaning that the default python command will become the 2.5.5 version instead. You can either delete this file (leave just the python2.5 file), or copy from /usr/bin.

---

### Post by junapp on 2010-05-03
Have you tried this yourself? I did it in a vm which seemed to work - but didn't get to test much. I used checkinstall which left as package name python by default. Seeing a problem with that trying to redo using python2.5 as package name. Removing the previously installed checkinstall  'python' package caused some major issues. I think using 'checkinstall gae-python2.5'  or some derivative may be advisable. I'll give it another go shortly.

---

### Post by junapp on 2010-05-03
after being quite unsuccessful with attempting to get python2.5 working with Google App Engine sdk on lucid lynx, I stumbled onto 
[http://www.codigomanso.com/en/2010/05/google-app-engine-en-ubuntu-10-4-lucid-lynx/](http://www.codigomanso.com/en/2010/05/google-app-engine-en-ubuntu-10-4-lucid-lynx/)
which has this to say:
```

Lucky me, after searching for a while on  [launchpad.net]("http://www.launchpad.net/") I&#8217;ve found a  solution. There is a person that has created  [python2.4 and  python2.5 packages]("https://launchpad.net/%7Efkrull/+archive/deadsnakes") for Ubuntu Lucid Lynx.
 The only think you should do is add the  following two lines at the end of your   /etc/apt/sources.list
 deb [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu) lucid main And finally run:
 $ sudo apt-get update
$ sudo apt-get install python2.5
And that&#8217;s it, you can now run  GoogleAppEngine.


```

---

### Post by bruno.braga on 2010-05-04
For me, the recompiling worked just fine, and I am using for GAE as well.

That's how I am using it:
```

bruno@u1004lts:~$ which python
/usr/bin/python
bruno@u1004lts:~$ which python2.5
/usr/local/bin/python2.5

```

---

### Post by wisski on 2010-05-04
Unfortunately [COLOR=#000000]python2.5-setuptools was not included in the repo junapp posted. Any suggestions?
[/COLOR]

---

### Post by junapp on 2010-05-15
> **bruno.braga said:**
> For me, the recompiling worked just fine, and I am using for GAE as well.

That's how I am using it:
```

bruno@u1004lts:~$ which python
/usr/bin/python
bruno@u1004lts:~$ which python2.5
/usr/local/bin/python2.5

```
Bruno, what do you have for the first line of your dev_appserver.py?

I'm using #!/usr/bin/env python2.5 but getting this error below which at one point seemed to be able to be fixed by installing py25-socket-ssl. Did you install socket-ssl somehow?
```

  File "/home/junapp/google_appengine/google/appengine/tools/appengine_rpc.py", line 32, in <module>
    https_handler = urllib2.HTTPSHandler
AttributeError: 'module' object has no attribute 'HTTPSHandler'

```

---

### Post by gourneau on 2010-09-05
> **bruno.braga said:**
> It seems python2.5 is out of the package list in lucid.

[http://packages.ubuntu.com/lucid/allpackages?format=txt.gz]("http://packages.ubuntu.com/lucid/allpackages?format=txt.gz")

But it is fairly easy (to newbies) to install it from source:

[http://www.python.org/download/releases/2.5.5/](http://www.python.org/download/releases/2.5.5/)

One catch though, the installation writes a /usr/local/bin/python file (which in the $PATH is searched before /usr/bin/), meaning that the default python command will become the 2.5.5 version instead. You can either delete this file (leave just the python2.5 file), or copy from /usr/bin.

To avoid writing over your current Python version when install from source use ```
make altinstall
``` instead of ```
make install
```

---

