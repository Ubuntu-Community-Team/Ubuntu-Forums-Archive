---
title: "Installing Python 3.x modules"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by Neutronst4r on 2013-05-18
Hello,
I have big problems installing python 3 modules. Specifically I need Matplotlib,Scipy and Numpy.  The later is already installed. I downloaded the Sourcecode files from Sourceforge and tried
```
sudo python3 setup.py
```
inside the unpacked directory of the module. Of course I get an error message because I have no ******* idea what I am actually doing. I understand that many ubuntu applications need an older version of python to run (~2.7) but I want to use python 3+.

I read thing about virtual environment and all that stuff, but I dont understand it. I am going to use Ecplise for programming and it is working fine so far. I can also do
```
python3
```
in console and I enter python 3.3.1 in interactive mode:
```
neutronst4r@nibbler:~$ python3
Python 3.3.1 (default, Apr 17 2013, 22:30:32) 
[GCC 4.7.3] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>

```

I need to know how to install modules for a specific python version. Please help me!

---

### Post by Cheesemill on 2013-05-18
No need to download anything manually they are already in the repositories, just use the Ubuntu package management system like you would for any other piece of software. Either search for them in [Synaptic]("apt://synaptic") if you want to use a GUI or run the following command to install them from the terminal.
```
sudo apt-get install python3-matplotlib python3-scipy python3-numpy
```

---

### Post by Neutronst4r on 2013-05-18
I feel very dumb now. Thank you very much!

---

