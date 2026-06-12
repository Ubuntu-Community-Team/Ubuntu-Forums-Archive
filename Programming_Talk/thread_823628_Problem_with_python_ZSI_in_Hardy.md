---
title: "Problem with python ZSI in Hardy"
date: 2008-06-09
forum: Programming Talk
---

### Post by nick_h on 2008-06-09
I am getting errors when trying to use the ZSI web services module in python.  I installed the package *python-zsi* and tried an import.

The errors in Hardy are as follows:
```
>>> import ZSI
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/var/lib/python-support/python2.5/ZSI/__init__.py", line 148, in <module>
    from xml.dom import Node as _Node
ImportError: No module named dom
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.5/site-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.5/site-packages/apport/report.py", line 17, in <module>
    import xml.dom, xml.dom.minidom
ImportError: No module named dom

Original exception was:
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/var/lib/python-support/python2.5/ZSI/__init__.py", line 148, in <module>
    from xml.dom import Node as _Node
ImportError: No module named dom
```

When I try the same in Gutsy the import works fine with no errors.

It looks like it can't find the XML modules, but I have got the package *python-xml* installed.

I checked that the directory /usr/lib/python2.5/xml/dom exists.  I also checked that /usr/lib/python2.5 is listed in sys.path.

There are a couple of possibly related bugs in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/zsi/+bug/199014](https://bugs.launchpad.net/ubuntu/+source/zsi/+bug/199014)
[https://bugs.launchpad.net/ubuntu/+source/zsi/+bug/208855](https://bugs.launchpad.net/ubuntu/+source/zsi/+bug/208855)

Looking at #199014, it appears that the dependency to *python-xml* was removed before ZSI was converted to use other xml libraries, but I have got *python-xml* installed.

Has anyone got any ideas how to fix this?

Is ZSI the best module to use when writing a web service client program in python?

---

### Post by Can+~ on 2008-06-09
> **nick_h said:**
> Is ZSI the best module to use when writing a web service client program in python?

Depends on what you want to do. Tell more about your project, if you want to parse xml, python already has libraries for xml parsing, also for html, or any SGML.

Check the [index of modules]("http://pydoc.org/2.5.1/"), for any suitable builtin module.

---

### Post by nick_h on 2008-06-09
I am writing a gnome panel applet to display usage and line statistics from my ADSL connection.  My ISP provides a public webservices interface.  What I really need is an easy way to generate calls to the interface based on a definition supplied in a WDSL file.

So far I have written some proof of concept code which creates a panel applet which runs code at a specified interval.  I have also investigated notifications.  For the front-end pygtk seems suitable.

For the back-end I also wrote a proof of concept for the web interface and successfully obtained data from my ISP using ZSI.  Unfortunately, although this works in Gutsy, I just tested in on Hardy and it failed.

---

### Post by nick_h on 2008-06-21
Is it just me or does it work for everyone else?
Please would someone running Hardy check this for me?

I have also noticed a similar bug in Rhythmbox similar to [bug #226493](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/226493) but I get python xml error messages for these 3 plugins.  Again the problem is with Hardy only and not Gutsy.

I have looked for other suitable modules but can't find any.

---

### Post by nick_h on 2008-06-24
I tested ZSI from a Hardy Live CD and it worked OK.

I re-installed Hardy and it fixed the problem.  I didn't find the cause of the problem but for some reason the python xml packages stopped working which broke all programs dependent on them.

---

### Post by jain.arpit6 on 2008-07-17
Hi,

I am installing some package called VOMS. However I am getting an error like this while running the script as 
File "./voms-admin", line 28, in ?
    from VOMSAdmin.VOMSCommands import supported_commands,UserCommand,parse_commands, \
  File "/opt/glite/share/voms-admin/client/VOMSAdmin/VOMSCommands.py", line 25, in ?
    from VOMSAdminService import VOMSAdmin
  File "/opt/glite/share/voms-admin/client/VOMSAdmin/VOMSAdminService.py", line 1, in ?
    from VOMSAdminService_services import *
  File "/opt/glite/share/voms-admin/client/VOMSAdmin/VOMSAdminService_services.py", line 6, in ?
    from VOMSAdminService_services_types import *
  File "/opt/glite/share/voms-admin/client/VOMSAdmin/VOMSAdminService_services_types.py", line 7, in ?
    import ZSI
ImportError: No module named ZSI

I have installed ZSI module using ZSI-2.0-1.py2.3.noarch.rpm. 

Can anyone help me in solving the error?

Thanks
Arpit

---

