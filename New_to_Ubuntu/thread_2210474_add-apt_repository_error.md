---
title: "add-apt repository error"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by krust13579 on 2014-03-11
Whenever I try to add a repository, I get the following error message:

[B]Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 128, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 84, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (6, "Couldn't resolve host 'launchpad.net'")
[/B]
What should I do?
I also received an error that "add-apt repository has closed unexpectedly. If you notice further problems, try rebooting."

After rebooting, I still get the same reply in terminal.

---

### Post by deadflowr on 2014-03-11
Something in here help
[http://ubuntuforums.org/showthread.php?t=2010993](http://ubuntuforums.org/showthread.php?t=2010993)

---

### Post by krust13579 on 2014-03-12
Thanks, that helped. I had to reinstall ca-certificates.

---

