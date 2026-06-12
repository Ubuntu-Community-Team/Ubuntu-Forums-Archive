---
title: "ubuntu 12.04 python"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by ramadavid on 2012-09-22
Hi Friends,
I upgraded upbuntu 11.04 to 12.04  LTS on sony E series vpeb34en 64 bit system.
When I check my python version 
python -V
Python 2.5.5

I want to use python 2.7 as default
 
I want your generous help to solve the issue..


Thank you in advace..
With best wishes and regards..

---

### Post by MG&amp;TL on 2012-09-22
If you've got more than one version of python installed, I believe the command to set the preferred version is:

```
sudo update-alternatives --config python
```

---

### Post by Sef on 2012-09-22
Moved to ABT.

---

### Post by ramadavid on 2012-09-23
Hi Thank you for your reply and help
sudo update-alternatives --config python

I got following reply..
update-alternatives: error: no alternatives for python.

sudo apt-get install python2.7
it reply on screen...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.7 is already the newest version.
The following packages were automatically installed and are no longer required:
  mgltools-utpackages mgltools-volume python-simpy python-simpy-doc
  python-simpy-gui python3.2 mgltools-pyautodock mgltools-molkit
  python3-minimal python3.2-minimal mgltools-scenario2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.



but again when I gave the command
sudo update-alternatives --config python

same reply

please help me to sort out the issue..

Thank you in advance
With best wishes and regards..

---

### Post by MG&amp;TL on 2012-09-23
> **ramadavid said:**
> 

I got following reply..
update-alternatives: error: no alternatives for python.


Huh. That's weird, I see no reason why python shouldn't use the alternatives system. Oh well....

You can try what is suggested here: [http://stackoverflow.com/questions/8163018/how-can-i-use-python-2-6-in-ubuntu-11-10]("http://stackoverflow.com/questions/8163018/how-can-i-use-python-2-6-in-ubuntu-11-10")


Irritating that you have to mess around though, I believe there is a bug on this. :)

---

