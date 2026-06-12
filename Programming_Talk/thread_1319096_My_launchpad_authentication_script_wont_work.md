---
title: "My launchpad authentication script wont work"
date: 2009-11-08
forum: Programming Talk
---

### Post by j7%&lt;RmUg on 2009-11-08
Hey guys,
All afternoon iv been fiddling around with this script trying to get it to authenticate with launchpad, now iv got it to the stage where it will open the right page in firefox and let me login but then it says that my script didnt provide enough information and that launchpad cant identify it.

I am all out of ideas as to what i may be missing, if anyone can help me on this i would be eternally grateful.

Thanks in advance.

```
#!/usr/bin/env python

import urllib2
import webbrowser

url = 'https://edge.launchpad.net/+request-token?oauth_consumer_key=pytask&oauth_signature_method=PLAINTEXT&oauth_signature=%26'

url2 = 'https://edge.launchpad.net/+authorize-token?'

req = urllib2.Request(url)
response = urllib2.urlopen(req)
token = response.read()
oauth_token = token[:32]
webbrowser.open(url2 + oauth_token)
```

---

### Post by j7%&lt;RmUg on 2009-11-09
I really could use a little help, is there no one that has any experience with launchpadlib?

---

### Post by StunnerAlpha on 2009-11-09
Mind elaborating on exactly what you are trying to do? Are you trying to make a file signature or what? It is a little vague to me.

---

### Post by j7%&lt;RmUg on 2009-11-09
Ok so this script is based off authenticating a request to allow a program to access launchpad. All its supposed to do is open a web browser window, ask you to login to staging.launchpad.net and then delegate permission to the program that asked for that permission, in this case its my script above.

---

