---
title: "What's a sudoers error? And why am I UID 1000 and not 0?"
date: 2018-10-27
forum: New to Ubuntu
---

### Post by cybervigilante on 2018-10-27
I couldn't install a python package with pip due to a permission error
 

 could not install packages due to an EnvironmentError: [Errno 13] Permission denied: '/usr/local/lib/python2.7/dist-packages/socketserver'

 Consider using the `--user` option or check the permissions.
 

 /etc/sudoers is owned by uid 1000, should be 0
 

 What is wrong with sudoers and how do I change it? I tried chown on sudoers but still got the same error:
 

 sudo chown jim /etc/sudoers worked but the pip install failed on the uid 1000, no 0 error again.p, li { white-space: pre-wrap; }

---

### Post by oldos2er on 2018-10-27
Please see [https://askubuntu.com/questions/513523/sudo-doesnt-work-etc-sudoers-is-owned-by-uid-1000-should-be-0](https://askubuntu.com/questions/513523/sudo-doesnt-work-etc-sudoers-is-owned-by-uid-1000-should-be-0)

---

