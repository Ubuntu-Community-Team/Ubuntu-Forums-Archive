---
title: "python: posting to a web page (drupal)"
date: 2008-10-07
forum: Programming Talk
---

### Post by sloggerkhan on 2008-10-07
I'd like to make it so that I can run a python script to post a block of text to my personal drupal site without having to open up a browser and login, however, I find myself a bit baffled.

So far I am aware of urllib2, which I've been able to use to load the text of my webpage. However, I haven't been able to find good information about how to send the login back or navigate from the main page to posting my content.

I've also been looking at giving pykhtml a shot ([http://paul.giannaros.org/pykhtml/](http://paul.giannaros.org/pykhtml/)), though I'd rather not have the kde dependencies. 
Unfortunately, the
```

browser = pykhtml.Browser()

```
declaration seems to have an error within pykhtml itself.

So what is the best way to navigate and submit information to a website using python?

---

### Post by tomchuk on 2008-10-07
Automating logging in, and posting a new node in drupal using by scripting an embedded browser seems like an over-complicated solution to a fairly simple problem.

Drupal supports the blogger, metaWeblog and mt xmlrpc apis. Just turn on the Blog API module in drupal. Your default python install should include xmlrpclib.

Something like this should work:
```

#!/usr/bin/env python

import xmlrpclib, sys

site_url     = 'http://www.mydrupalblog.com/'
content_type = 'blog'           # The drupal content type you are creating
username     = 'username'       # Your drupal username
password     = 'password'       # Your drupal password
post_title   = 'Test blog post' # Post title
post_body    = 'Test body'      # Post body
publish      = True             # Publish this post?

try:
    server = xmlrpclib.Server(site_url + 'xmlrpc.php')
    nid = server.metaWeblog.newPost(content_type, username, password,
          {'title': post_title, 'description': post_body}, publish)
except xmlrpclib.ProtocolError, e:
    print 'XML-RPC Protocol Error:', e.errmsg
except xmlrpclib.Fault, e:
    print 'XML-RPC Fault:', e.faultString
except:
    print 'Unexpected error:', sys.exc_info()
else:
    print 'Posted: ' + site_url + 'node/' + str(nid)



```

---

### Post by sloggerkhan on 2008-10-07
wow, I never even thought of something like that. It seems obvious in retrospect that blogging APIs would be where to look.

---

