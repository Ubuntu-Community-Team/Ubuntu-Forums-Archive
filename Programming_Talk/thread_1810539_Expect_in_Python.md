---
title: "Expect in Python"
date: 2011-07-23
forum: Programming Talk
---

### Post by cguy on 2011-07-23
Is there such a thing like Tcl's expect in Python, that is _still maintained_?

For Python 2.6? 3?

Should I just learn Tcl? :)

---

### Post by diesch on 2011-07-23
Do you have any issues with Pexpect?

---

### Post by ziekfiguur on 2011-07-23
What exactly do you want to do with it? I'm having the feeling that most uses for pexpect could quite easily be custom made using the subprocess module.

---

### Post by cguy on 2011-07-23
> **diesch said:**
> Do you have any issues with Pexpect?
Is it still maintained? Does it work with Python 2.6?

> **ziekfiguur said:**
> What exactly do you want to do with it? I'm having the feeling that most uses for pexpect could quite easily be custom made using the subprocess module.
I want to automate the testing of a module at work:

1. connect through a serial console to a switch
2. issue specific commands through that serial console interface
3. read the output of those commands and extract the interesting part(s)
4. send remote, equivalent commands to the same switch (SNMP)
5. read the output of those SNMP queries and process it
6. compare the data at pt. 3 with the data at pt. 5

---

### Post by diesch on 2011-07-23
> **cguy said:**
> Is it still maintained? Does it work with Python 2.6?

It's part of the Ubuntu default installation so I expect ;-) it to get bug fixes and to work at least with the default Python version (which is 2.7.1 in 11.04).

---

### Post by ziekfiguur on 2011-07-24
> **cguy said:**
> Is it still maintained? Does it work with Python 2.6?
Well, as far as i can see the laterst update was in 2008, so either there were no bugs reported or it's not maintained anymore. However, python 2.x versions are supposed to be backward compatible, so as long as it's not made for 1.x it should work with python2.6
> **cguy said:**
> I want to automate the testing of a module at work:

1. connect through a serial console to a switch
2. issue specific commands through that serial console interface
3. read the output of those commands and extract the interesting part(s)
4. send remote, equivalent commands to the same switch (SNMP)
5. read the output of those SNMP queries and process it
6. compare the data at pt. 3 with the data at pt. 5
You're right, you probably don't want to do that yourself. Have you actually tried pexpect? if it works, theres no reason not to use it. otherwise you might need to learn tcl.

---

