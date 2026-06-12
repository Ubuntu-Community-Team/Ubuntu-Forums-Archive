---
title: "Python path for cgi script in Ubuntu 7.10"
date: 2008-01-29
forum: Programming Talk
---

### Post by Railsbuntu on 2008-01-29
Hi,

I was trying to make mercurial work using nginx as the http server.

Mercurial uses a cgi script written in python, here it is:
> #!/usr/bin/env python
#
# An example CGI script to use hgweb, edit as necessary

# adjust python path if not a system-wide install:
import sys
sys.path.insert(0, "/usr/lib/python2.5")

# enable importing on demand to reduce startup time
from mercurial import demandimport; demandimport.enable()

# send python tracebacks to the browser if an error occurs:
import cgitb
cgitb.enable()

# If you'd like to serve pages with UTF-8 instead of your default
# locale charset, you can do so by uncommenting the following lines.
# Note that this will cause your .hgrc files to be interpreted in
# UTF-8 and all your repo files to be displayed using UTF-8.
#
#import os
#os.environ["HGENCODING"] = "UTF-8"

from mercurial.hgweb.hgweb_mod import hgweb
import mercurial.hgweb.wsgicgi as wsgicgi

application = hgweb("/var/hg/repo1", "repository name")
wsgicgi.launch(application)

Then when I point the browser to my http server, I get the following error:
[IMG]http://img301.imageshack.us/img301/7619/pythontracedo9.png[/IMG]

I have read that it might be the
> import sys
sys.path.insert(0, "/usr/lib/python2.5")
which is not set properly, so what would that be for Ubuntu 7.10?

By the way using another mercurial cgi script (a simpler version), I was able to browse my repository, I was just lacking the ability to commit changes to the http server, so I tried this latest version of the script, and suddenly i had this error message. This means that my setup works, it is just the script that is giving troubles.

Thank you :)

---

### Post by kool_kat_os on 2008-02-05
what?!?!?!??!

---

