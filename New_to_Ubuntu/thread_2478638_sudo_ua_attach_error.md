---
title: "sudo ua attach error"
date: 2022-08-31
forum: New to Ubuntu
---

### Post by mnia2 on 2022-08-31
I'm getting below error when trying to attach UA token. I reinstalled python and ubuntu advantages tools but no luck. Any help is appreciated.


```
administrator@pizzastudio:~$ sudo ua attach CODE HIDDEN 
Traceback (most recent call last): File "/usr/bin/ua", line 9, in load_entry_point('ubuntu-advantage-tools==27.9', 'console_scripts', 'ubuntu-advantage')() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 489, in load_entry_point return get_distribution(dist).load_entry_point(group, name) File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2852, in load_entry_point return ep.load() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2443, in load return self.resolve() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2449, in resolve module = import(self.module_name, fromlist=['name'], level=0) File "/usr/lib/python3/dist-packages/uaclient/cli.py", line 20, in import yaml File "/usr/local/lib/python2.7/dist-packages/yaml/init.py", line 2, in from error import * ImportError: No module named 'error' Error in sys.excepthook: Traceback (most recent call last): File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook from apport.fileutils import likely_packaged, get_recent_crashes File "/usr/lib/python3/dist-packages/apport/init.py", line 5, in from apport.report import Report File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in import apport.fileutils File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 25, in from apport.packaging_impl import impl as packaging File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 23, in import apt File "/usr/local/lib/python2.7/dist-packages/apt/init.py", line 21, in import apt_pkg ImportError: /usr/local/lib/python2.7/dist-packages/apt_pkg.so: undefined symbol: _Py_ZeroStruct
Original exception was: Traceback (most recent call last): File "/usr/bin/ua", line 9, in load_entry_point('ubuntu-advantage-tools==27.9', 'console_scripts', 'ubuntu-advantage')() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 489, in load_entry_point return get_distribution(dist).load_entry_point(group, name) File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2852, in load_entry_point return ep.load() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2443, in load return self.resolve() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2449, in resolve module = import(self.module_name, fromlist=['name'], level=0) File "/usr/lib/python3/dist-packages/uaclient/cli.py", line 20, in import yaml File "/usr/local/lib/python2.7/dist-packages/yaml/init.py", line 2, in from error import * ImportError: No module named 'error'

```

---

### Post by MAFoElffen on 2022-09-06
Welcome to the Ubuntu Forums Community. Here, we are User's of Ubuntu Linux, that help other Users. Any 'Support' here is by very dedicated Volunteers. We are not employed by Canonical, nor are the volunteer members here paid by Canonical, though, the member base here has vast collective experience in resolving problems with Ubuntu. None us here are paid.

Ubuntu Advantage, is 'Paid Support' from Canonical. They provide the their own instructions and support to get you connected and started with their subscription support services...

Here are some 'RECENT' links to help with that:
[https://installati.one/ubuntu/22.04/ubuntu-advantage-tools/](https://installati.one/ubuntu/22.04/ubuntu-advantage-tools/)
[https://ubuntu.com/server/docs/install/subscription](https://ubuntu.com/server/docs/install/subscription)

Those links will help you get started using your paid Ubuntu Advantage Subscription Services with Canonical.

Some observations:
1) If you do not have a paid subscription with Ubuntu Advantage, for paid support then you do not need to install Ubuntu Advantage Tools. It would not provide you with any kinds of support if you do not have a support contract. If that is the case, then "here", on this Forum, where the Distribution mentions whereto come for help, "is" the right place to be if you need help, what to learn what to do or about Ubuntu, or to just be a part of 'The Community'...

2) Why do I say that? Because the error you posted, the back-trace off that says that it is working with Python version 2.7, which is outdated and deprecated for all supported versions of Ubuntu, so somehow you are working with some wrong, outdated pieces of the puzzle that shouldn't work with current versions of Ubuntu.

3) You shouldn't have to reinstall Python for that to install... And if you did uninstall Python 3 and install older versions of Python 2, then you now have bigger problems ahead, where you will find that most scripts of your installation are now broken.

4.) If you do, or do not have a subscription for support with Ubuntu Advantage, you can still ask questions here. One of the things we ask, it that if you post and commands or raw output, that you wrap those with [b][noparse]```
 commands/output
```[/noparse] TAGS[b]... It's easier to read, and some commands and/or raw output plays havoc with the Forum's system software.

...Again, welcome to the Community, and to your Journey with Ubuntu Linux.

---

### Post by clerk007 on 2022-09-18
> **mnia2 said:**
> [COLOR=#232629][FONT=-apple-system]I'm getting below error when trying to attach UA token. I reinstalled python and ubuntu advantages tools but no luck. Any help is appreciated.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]administrator@pizzastudio:~$ sudo ua attach CODE HIDDEN 
Traceback (most recent call last): File "/usr/bin/ua", line 9, in load_entry_point('ubuntu-advantage-tools==27.9', 'console_scripts', 'ubuntu-advantage')() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 489, in load_entry_point return get_distribution(dist).load_entry_point(group, name) File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2852, in load_entry_point return ep.load() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2443, in load return self.resolve() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2449, in resolve module = import(self.module_name, fromlist=['name'], level=0) File "/usr/lib/python3/dist-packages/uaclient/cli.py", line 20, in import yaml File "/usr/local/lib/python2.7/dist-packages/yaml/init.py", line 2, in from error import * ImportError: No module named 'error' Error in sys.excepthook: Traceback (most recent call last): File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook from apport.fileutils import likely_packaged, get_recent_crashes File "/usr/lib/python3/dist-packages/apport/init.py", line 5, in from apport.report import Report File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in import apport.fileutils File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 25, in from apport.packaging_impl import impl as packaging File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 23, in import apt File "/usr/local/lib/python2.7/dist-packages/apt/init.py", line 21, in import apt_pkg ImportError: /usr/local/lib/python2.7/dist-packages/apt_pkg.so: undefined symbol: _Py_ZeroStruct [/FONT][/COLOR][FONT=-apple-system][[COLOR=#ffffff]YOWhatsApp Apk[/COLOR]]("https://gbwamod.com/download-yowhatsapp-apk/")[/FONT][COLOR=#232629][FONT=-apple-system]
Original exception was: Traceback (most recent call last): File "/usr/bin/ua", line 9, in load_entry_point('ubuntu-advantage-tools==27.9', 'console_scripts', 'ubuntu-advantage')() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 489, in load_entry_point return get_distribution(dist).load_entry_point(group, name) File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2852, in load_entry_point return ep.load() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2443, in load return self.resolve() File "/usr/local/lib/python2.7/dist-packages/pkg_resources/init.py", line 2449, in resolve module = import(self.module_name, fromlist=['name'], level=0) File "/usr/lib/python3/dist-packages/uaclient/cli.py", line 20, in import yaml File "/usr/local/lib/python2.7/dist-packages/yaml/init.py", line 2, in from error import * ImportError: No module named 'error'[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]


I don't know why but, I am also facing the similar issue.

---

