---
title: "hashpling question"
date: 2005-12-06
forum: Programming Talk
---

### Post by Xoctor on 2005-12-06
Can someone help me with a little problem I'm having running python cgi scripts?

My program, test.py has its executable bit set for all users, and works from the command line when I type ./test.py, but wont work as a CGI with apache 2 with the normal hashpling of #!/usr/bin/env python, however it does work with a hashpling of #!/usr/bin/python.

Its a pain because I'm testing on my local Ubuntu machine, but production is an OpenBSD box where #!/usr/bin/python wont work.

Xoc

---

### Post by gord on 2005-12-06
have you considered using mod-python instead? its very good

---

### Post by Xoctor on 2005-12-06
mod_python is a bit tricky to install on OpenBSD - you've got to recompile python with threading turned off. The performance hit of using CGI will never be a problem in this case, so it seems a very big workaround.

Surely there must be a way to make the hashpling work under apache?

---

