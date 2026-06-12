---
title: "can't upgrade default python to v3"
date: 2016-08-23
forum: Programming Talk
---

### Post by uh-huh on 2016-08-23
When I start python I get this, even though I set ```
alias python='/usr/bin/python3'
``` in .bashrc ```
sulfasal@EKPC:~$ python
Enthought Canopy Python 2.7.11 | 64-bit | (default, Mar 18 2016, 17:34:32) 
[GCC 4.1.2 20080704 (Red Hat 4.1.2-55)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
``` This was in .bashrc too but as you can see I commented it out: ```
# Added by Canopy installer on 2016-06-10
# VIRTUAL_ENV_DISABLE_PROMPT can be set to '' to make the bash prompt show that Canopy is active, otherwise 1
#alias activate_canopy="source '/home/sulfasal/Enthought/Canopy_64bit/User/bin/activate'"
#VIRTUAL_ENV_DISABLE_PROMPT=1 source '/home/sulfasal/Enthought/Canopy_64bit/User/bin/activate'
```

Didn't change anythiing, I still get the original message when i enter python at the prompt.

---

### Post by Bashing-om on 2016-08-23
uh-huh; Hummmm ..

I be just a tad mis-directed here , As;
```

sysop@1404mini:~$ dpkg -l python3
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name            Version      Architecture Description
+++-===============-============-============-===================================
ii  python3         3.4.0-0ubunt amd64        interactive high-level object-orien


sysop@1404mini:~$ dpkg -l python
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name            Version      Architecture Description
+++-===============-============-============-===================================
ii  python          2.7.5-5ubunt amd64        interactive high-level object-orien
sysop@1404mini:~

```
both versions are installed by default .
If ya want to work with python 3 version, call python3 .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by oldfred on 2016-08-23
Do not attempt to change defaults on python, you break the system.
They have planned for years to change default to python3, but several applications which Ubuntu does not have control over have not yet converted. If you change default you will have major issues.

Just follow Bashing-om's advice and use python3.

If in a program, make this first line:
#!/usr/bin/python3

I have also seen this, but not sure which is better:
#!/usr/bin/env python3

---

### Post by uh-huh on 2016-08-23
Thanks for the tips!

---

### Post by &amp;KyT$0P# on 2016-08-23
> **oldfred said:**
> If in a program, make this first line:
#!/usr/bin/python3

I have also seen this, but not sure which is better:
#!/usr/bin/env python3
The env line doesn't require python3 installed in the very specific absolute path, basically it lets python3 reside anywhere on $PATH, including /usr/local/bin etc.  If you're writing the script for a single system (if you don't need portability) then it doesn't matter which line you pick.

---

### Post by ian-weisser on 2016-08-24
> **uh-huh said:**
> alias python='/usr/bin/python3'

You already know the current Ubuntu side of the problem: Doing that will break your system quite horribly. Py2 and Py3 are not interchangeable.

On the Python side, see [PEP394]("https://www.python.org/dev/peps/pep-0394/"): 'python' should always refer to some version of Py2, and should never refer to a version of Py3.

Several Canonical engineers and Ubuntu volunteers have been laboring for years to eliminate the Py2 dependency from future versions of Ubuntu. They would love some help.
Their May 2016 UDS meeting is at [http://summit.ubuntu.com/uos-1605/meeting/22675/finish-move-to-py3/](http://summit.ubuntu.com/uos-1605/meeting/22675/finish-move-to-py3/)

---

