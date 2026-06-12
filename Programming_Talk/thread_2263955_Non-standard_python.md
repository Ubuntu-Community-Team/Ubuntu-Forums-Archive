---
title: "Non-standard python"
date: 2015-02-04
forum: Programming Talk
---

### Post by bomastudio on 2015-02-04
I want to use this python-binding to CUDA

[https://store.continuum.io/cshop/accelerate/](https://store.continuum.io/cshop/accelerate/)

But there is a problem. As the support told me:

> [FONT=arial]Anaconda[/FONT][FONT=arial] doesn't work with your system python or your system python libraries.  [/FONT][FONT=arial]Anaconda[/FONT][FONT=arial] supersedes it.   The [/FONT][FONT=arial]Anaconda[/FONT][FONT=arial] install changes your path so when you open up a terminal and type python the first and only python and python libraries it sees are in your home directory.  (unless you are on windows, that's a different story)[/FONT][FONT=arial]
[/FONT]
[FONT=arial]All of these instructions are for linux:[/FONT]
[FONT=arial]* Install Anaconda from [continuum.io/downloads]("http://continuum.io/downloads")[/FONT]
[FONT=arial]* You can update libraries directly from the terminal by typing:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]conda install <package>[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]if that fails (as it will for pygtk because there isn't a conda package in the anaconda channel for that yet)[/FONT]
[FONT=arial]you can look on [binstar.org]("http://binstar.org/") to find the package you want built by the community.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]conda install -c [https://conda.binstar.org/ska](https://conda.binstar.org/ska) pygtk[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Pip installs also work. [/FONT]
[COLOR=inherit][FONT=Menlo]pip install <package_name>[/FONT][/COLOR]

So I would like to solve this problem...... I need the community help!!!! Many thanks!!

---

### Post by TheFu on 2015-02-04
Jsut have your python point to the binary used by anaconda ... it is somewhere in your HOME.

---

### Post by ofnuts on 2015-02-05
> **bomastudio said:**
> I want to use this python-binding to CUDA

[https://store.continuum.io/cshop/accelerate/](https://store.continuum.io/cshop/accelerate/)

But there is a problem. As the support told me:



So I would like to solve this problem...... I need the community help!!!! Many thanks!!

What problem? What are the symptoms?

---

### Post by bomastudio on 2015-02-05
> **ofnuts said:**
> What problem? What are the symptoms?

Well, installing Anaconda I can't use programs based on standard system python (such as those based on pygtk)..... for example if I have installed PyRenamer  and install then Anaconda, PyRenamer breaks (it can0t find PyGtk libs). After uninstalling Anaconda everythings returns normal and works....

So I'm questioning if there is a way (symbolic links, or what else) to install Anaconda but still use my default system python.

---

### Post by TheFu on 2015-02-05
Have you attempted to manage the python environment for these programs?  
Ruby has rbenv or rvm. Perl has Perlbrew, I'm certain that python has something similar, assuming you don't just want to manage the 2-5 environment variables yourself.

[https://stackoverflow.com/questions/2812471/is-there-a-python-equivalent-of-rubys-rvm](https://stackoverflow.com/questions/2812471/is-there-a-python-equivalent-of-rubys-rvm) - looks like PyEnv or pythonz are the suggestions now.

---

