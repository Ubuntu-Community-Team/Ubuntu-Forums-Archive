---
title: "Python 3 and google library problem"
date: 2018-02-08
forum: Programming Talk
---

### Post by erotavlas on 2018-02-08
Hi,
I'm using ubuntu mate 16.04 LTS with python v3.5.2 and I installed google library [https://pypi.python.org/pypi/google/2.0.1](https://pypi.python.org/pypi/google/2.0.1) via pip install google.
My problem is that with a very simple code taken from [https://breakingcode.wordpress.com/2010/06/29/google-search-python/](https://breakingcode.wordpress.com/2010/06/29/google-search-python/)
```

# Get the first 20 hits for: "Breaking Code" WordPress blog
from googlesearch import search
for url in search('"Breaking Code" WordPress blog', stop=20):
    print(url)

```
I get
```

Traceback (most recent call last):
  File "dummy.py", line 2, in <module>
    from googlesearch import search
ImportError: cannot import name 'search'

```
The same code works well with python v.2.7.12. Is there any way to use it with python v3.5?
Thank you

---

### Post by norobro on 2018-02-08
pip3 install google

You need to have the package python3-pip installed [https://packages.ubuntu.com/xenial/python3-pip](https://packages.ubuntu.com/xenial/python3-pip)

---

### Post by erotavlas on 2018-02-08
> **norobro said:**
> pip3 install google

You need to have the package python3-pip installed [https://packages.ubuntu.com/xenial/python3-pip](https://packages.ubuntu.com/xenial/python3-pip)

Hi,
of course I'm already using pip3 (pip calls pip3 as default pip 9.0.1 from /home/user/.local/lib/python3.5/site-packages (python 3.5)).
```

sudo apt-get install python3-pip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3-pip is already the newest version (8.1.1-2ubuntu0.4).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

---

### Post by spjackson on 2018-02-08
The recipe described above works perfectly for me on debian jesse. I'll try later on Ubuntu 16.04.
```

$ sudo apt-get install python3-pip
$ sudo pip3 install google
$ cat ./gsearch.py 
#!/usr/bin/env python3

from googlesearch import search
for url in search('"Breaking Code" WordPress blog', stop=20):
    print(url)
$ ./gsearch.py 
https://wordpress.org/support/topic-tag/breaking-code/
https://en.forums.wordpress.com/tags/breaking-code
https://en.forums.wordpress.com/topic/wordpress-breaking-my-embeded-html-code-why
https://breakingcode.wordpress.com/
https://breakingcode.wordpress.com/2010/06/
https://synsinger.wordpress.com/2015/04/14/breaking-code-again/
https://github.com/mAAdhaTTah/wordpress-github-sync/issues/126
https://meta.trac.wordpress.org/ticket/1428
https://blog.resellerclub.com/make-the-most-of-your-wordpress-theme-by-cleaning-house/
https://www.blogherald.com/2007/07/16/writing-and-publishing-code-in-your-wordpress-blog-posts/
https://www.kevinmuldoon.com/break-out-frames-javascript/
https://make.wordpress.org/core/page/2/
https://wstuartdhij.wordpress.com/2014/09/24/wordpress-blog-tutorial/
https://trwpconnect.wordpress.com/2016/04/17/welcome-to-make-cycle-4-making-the-code/
http://jcimoch.github.io/all-tags
https://ubuntuforums.org/showthread.php?t=2384553
https://moninagracevilla.wordpress.com/2014/02/21/on-breaking-code-and-pushing-buttons/
https://blog.puzzlenation.com/2017/10/26/unsung-tales-of-women-in-american-code-breaking/
$

```

---

### Post by norobro on 2018-02-08
Works for me in 17.10 too.

As a matter of fact, I can produce the error in python2 because the google package isn't  installed:```
[FONT=monospace][COLOR=#000000]$ python search.py  [/COLOR]
Traceback (most recent call last):
  File "search.py", line 2, in <module>
    from googlesearch import search
ImportError: No module named googlesearch

$ python3 search.py  
https://wordpress.org/support/topic-tag/breaking-code/
https://breakingcode.wordpress.com/
...[/FONT]
```

@erotavlas - Check if the google package is installed: ```
$ [FONT=monospace][COLOR=#000000]ls -nl /home/user/.local/lib/python3.6/s[/COLOR]ite-packages/
total 16
drwxrwxr-x 2 1000 1000 4096 Feb  8 11:43 [COLOR=#5454FF]**beautifulsoup4-4.6.0.dist-info**[/COLOR]
drwxrwxr-x 5 1000 1000 4096 Feb  8 11:43 [COLOR=#5454FF]**bs4**[/COLOR]
drwxrwxr-x 2 1000 1000 4096 Feb  8 11:43 [COLOR=#5454FF]**google-2.0.1.dist-info**[/COLOR]
drwxrwxr-x 3 1000 1000 4096 Feb  8 11:43 [COLOR=#5454FF]**googlesearch**[/COLOR][/FONT]
```

---

### Post by spjackson on 2018-02-08
> **spjackson said:**
> The recipe described above works perfectly for me on debian jesse. I'll try later on Ubuntu 16.04.

Yes, the same commands work just the same on Ubuntu 16.04. The default python on a fresh Ubuntu 16.04.3 desktop install is python 2.7.

---

### Post by erotavlas on 2018-02-09
> **norobro said:**
> Works for me in 17.10 too.

As a matter of fact, I can produce the error in python2 because the google package isn't  installed:```
[FONT=monospace][COLOR=#000000]$ python search.py  [/COLOR]
Traceback (most recent call last):
  File "search.py", line 2, in <module>
    from googlesearch import search
ImportError: No module named googlesearch

$ python3 search.py  
https://wordpress.org/support/topic-tag/breaking-code/
https://breakingcode.wordpress.com/
...[/FONT]
```

@erotavlas - Check if the google package is installed: ```
$ [FONT=monospace][COLOR=#000000]ls -nl /home/user/.local/lib/python3.6/s[/COLOR]ite-packages/
total 16
drwxrwxr-x 2 1000 1000 4096 Feb  8 11:43 [COLOR=#5454FF]**beautifulsoup4-4.6.0.dist-info**[/COLOR]
drwxrwxr-x 5 1000 1000 4096 Feb  8 11:43 [COLOR=#5454FF]**bs4**[/COLOR]
drwxrwxr-x 2 1000 1000 4096 Feb  8 11:43 [COLOR=#5454FF]**google-2.0.1.dist-info**[/COLOR]
drwxrwxr-x 3 1000 1000 4096 Feb  8 11:43 [COLOR=#5454FF]**googlesearch**[/COLOR][/FONT]
```

Hi,
for me
```

[FONT=monospace][FONT=monospace][COLOR=#000000]ls -nl /home/user/.local/lib/python3.6/s[/COLOR]ite-packages/[/FONT][/FONT]
ls: cannot access '/home/user/.local/lib/python3.6/site-packages/': No such file or directory

```

```

pip --version
pip 9.0.1 from /home/user/.local/lib/python3.5/site-packages (python 3.5)

```

```

pip list | grep google
DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the 
[list] section) to disable this warning.
google (2.0.1)
google-api-python-client (1.6.5)
google-search (1.0.2)
search-google (1.2.1)

```

Adding this code
```

import googlesearch
print (googlesearch.__file__)

```
gave me:
```

/home/user/miniconda3/lib/python3.5/site-packages/googlesearch/__init__.py

```

> **spjackson said:**
> Yes, the same commands work just the same on  Ubuntu 16.04. The default python on a fresh Ubuntu 16.04.3 desktop  install is python 2.7.

Hi,
I just tried with a fresh install of ubuntu 16.04 and it works.

---

