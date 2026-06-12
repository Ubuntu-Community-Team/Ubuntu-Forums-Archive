---
title: "Python mechanize recursion error"
date: 2007-12-19
forum: Programming Talk
---

### Post by twisted_steel on 2007-12-19
This is the code I am trying to run:

```
#!/usr/bin/python

from mechanize import Browser

br = Browser()
br.open('http://live.xbox.com/en-US/profile/Friends.aspx')
```

I can open URLs such as 'http://www.google.com' without a problem, but for some reason, on this one, I get the following error at the end of a traceback:

[I]RuntimeError: maximum recursion depth exceeded in cmp
[/I]
I am running Ubuntu 7.10 (Gutsy) using python2.5 2.5.1-5ubuntu5 and python-mechanize 0.1.6b-1.

Any ideas why this wouldn't work?

---

### Post by rchille on 2008-01-24
*Bump*

I'm having the same trouble. Did you find a solution/workaround?

Thanks

Rob

---

### Post by rchille on 2008-01-24
Okay, 
Not sure why this worked for me, but here is what I did:

```
import mechanize
mech = mechanize.Browser()
mech.set_handle_robots(False)
```

Not sure why ignoring robots.txt stops the recursion by it seemed to work for me. (Any Web Gurus out there have an explanation?)

I hope this helps,
Rob

---

### Post by twisted_steel on 2008-01-25
Are you using the same URL that I am?  I emailed someone else who developed a script using the method I tried and it works fine for him.  However, he is using the latest from SVN (as of around Dec. 20th or so), so I imagine there were some fixes that aren't in the Gutsy version.

I personally just rewrote my script using urllib2 and cookielib instead just because I didn't want to have a dependency on a non-released version.

---

