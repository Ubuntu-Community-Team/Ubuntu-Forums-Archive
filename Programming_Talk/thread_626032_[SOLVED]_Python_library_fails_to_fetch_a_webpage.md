---
title: "[SOLVED] Python library fails to fetch a webpage"
date: 2007-11-28
forum: Programming Talk
---

### Post by Majorix on 2007-11-28
I use a code that I got directly from the examples page of the Python Library Reference documentation, but it fails to fetch the whole page, it only fetches it partly.

The code I use is this:
> Use of Basic HTTP Authentication:[PHP]import urllib2
# Create an OpenerDirector with support for Basic HTTP Authentication...
auth_handler = urllib2.HTTPBasicAuthHandler()
auth_handler.add_password('realm', 'host', 'username', 'password')
opener = urllib2.build_opener(auth_handler)
# ...and install it globally so it can be used with urlopen.
urllib2.install_opener(opener)
urllib2.urlopen('http://www.example.com/login.html')[/PHP]

I make it print the fetched page to a file. But when I open it, I find out that the authentication failed (this one is my fault, I don't know what exactly to put for 'realm', 'host' and for the url in urlopen) and that the file isn't complete (this is Python's fault most likely).

I didn't know what to do, so I came here to ask. Please help me if you can. Thanks a lot.

---

### Post by skeeterbug on 2007-11-28
From 18.6 urllib2

[http://docs.python.org/lib/module-urllib2.html](http://docs.python.org/lib/module-urllib2.html)

```

class HTTPPasswordMgrWithDefaultRealm(  	)
    Keep a database of (realm, uri) -> (user, password) mappings. A realm of None is considered a catch-all realm, which is searched if no other realm fits.

```

See Also:
[http://docs.python.org/lib/http-password-mgr.html#http-password-mgr](http://docs.python.org/lib/http-password-mgr.html#http-password-mgr)

I am guessing you can set the realm to None. I don't use urllib2 with HTTPAuth though. Is there a redirect after a successful login?

---

### Post by Majorix on 2007-11-28
So are you suggesting that I use HTTPPasswordMgr() instead of HTTPBasicAuthHandler()? Can it be done by just changing the name? I see they have the same list of arguments in the same order...

---

### Post by skeeterbug on 2007-11-28
I would try 

auth_handler.add_password(None, 'host', 'username', 'password')

---

### Post by Majorix on 2007-11-28
I have tried None (without the quotes) for the realm, but I still don't know what exactly I should put for host. For example, what is the host for these forums? I tried "http://ubuntuforums.org" but it didn't log me in.

Thanks for your interest.

---

### Post by cbryn on 2007-11-28
> **Majorix said:**
> I have tried None (without the quotes) for the realm, but I still don't know what exactly I should put for host. For example, what is the host for these forums? I tried "http://ubuntuforums.org" but it didn't log me in.

Thanks for your interest.

You are not trying to do [HTTP Basic Authentication]("http://en.wikipedia.org/wiki/Basic_access_authentication")... Have a look at curl (pycurl).

[http://pycurl.sourceforge.net/]("http://pycurl.sourceforge.net/")

---

### Post by Majorix on 2007-11-28
OK I have installed the package. Could you please give an example of its usage probably? You have the time, I will be going to sleep soon so I will be checking this thread tomorrow :)

---

### Post by cwaldbieser on 2007-11-28
> **Majorix said:**
> OK I have installed the package. Could you please give an example of its usage probably? You have the time, I will be going to sleep soon so I will be checking this thread tomorrow :)

I think cbryn's point was that to log on to these forums, you don't use basic authentication that is part of the HTTP protocol.  The forums provides its own authentication at the application level.  You should be able to just figure out what data needs to be POSTed (this can be accomplished with a program like ethereal).  It is probably just a user name and password field.

---

### Post by smartbei on 2007-11-29
You can do the same thing with urllib2 - curl IMO is overkill here. Just digure out what format the forum wants to accept username/password data by post, and set it to the forum. You may also need to think about accepting and using a session key, which most forums use to indicate that you are 'logged on'

---

### Post by Majorix on 2007-12-07
I have found the source of the problem. When I read the page returned from urlopen() line by line and then wrote it to a file, it succeeded. When I changed it back to the original, it only fetched partly. I think it was a problem with my RAM and its buffer at that time, so sorry for making a problem out of it.

Solved, thanks for anyone who cared.

---

