---
title: "How do I install python 2.7 in lucid?"
date: 2010-07-12
forum: Programming Talk
---

### Post by donatell0 on 2010-07-12
I am about to start writing code for a new software project. I want to use python 2.7. What is the recommended way to install python 2.7 on lucid? Do I just download the software from the Python website and install it or should I do some extra things on Lucid?

---

### Post by Yarui on 2010-07-12
Go to

[http://www.python.org/](http://www.python.org/)

Click on "Source Distribution" under "Quick Links (2.7)" on the left.  Extract the Downloaded file into a new folder.  In the README file read the Build instructions.  It will probably soon be available in synaptic too.

---

### Post by Bachstelze on 2010-07-12
> **Yarui said:**
> It will probably soon be available in synaptic too.

I don't know the exact plans for MAverick, but right now Python 2.7 is not in it, so it might not appear in the repos until at least Maverick+1.

---

### Post by davidism on 2010-07-14
Download the source from here:
[http://python.org/ftp/python/2.7/Python-2.7.tgz](http://python.org/ftp/python/2.7/Python-2.7.tgz)

```
tar xzf Python-2.7.tgz
cd Python-2.7
./configure
make
sudo make altinstall
```

Note that it is make altinstall, not make install.  The altinstall makes sure you don't clobber the OS installed version.

---

### Post by jgomo3 on 2010-08-26
It is needed that libsqlite3-dev package to be installed for python installer make the pysqlite2 module.

Instead, the Python2.6 ubuntu packge install this module.

So, it is not as easy as you want to make it see.

I would be great if one could install a Python2.7 ubuntu package from 10.10

I think it is possible. how could it be done?

---

### Post by tripzilch on 2010-09-14
> **davidism said:**
> Note that it is make altinstall, not make install.  The altinstall makes sure you don't clobber the OS installed version.

What do you mean clobber? Not replacing Ubuntu's Python 2.6.5 with the latest 2.7?

Why not, will things break? I thought Python 2.7 was supposed to be fully backwards compatible? Did anyone try this?

If I don't replace it and do the altinstall as you suggest, will I have to type "python27" (or something) every time I want to use the latest Python version instead of the old one?

---

### Post by Bachstelze on 2010-09-14
> **tripzilch said:**
> What do you mean clobber? Not replacing Ubuntu's Python 2.6.5 with the latest 2.7?

Why not, will things break? I thought Python 2.7 was supposed to be fully backwards compatible? Did anyone try this?


It's not a matter of compatibility between versions. The package manager installs Python 2.6. If you replace it with 2.7 without telling it, it will be confused.

---

### Post by ssam on 2010-09-14
python 2.x programs are generally 1 way compatible with each other (a python program written for 2.0 should work on 2.7), apart from a few small changes ('with' became a keyword and can't be used as a variable name any more). but for things that interact more deeply like python modules, more changes are needed. so if you use any 3rd party python modules, you will need a newer version that is compatible with 2.7.

most linux distros can manage multiple python versions. each is installed as python2.5, python2.6 and then a python symlink points to the default one. so check the install options to make sure it does not make 2.7 the default.

you may also want to set the prefix to something like /opt/python2.7 when configuring, and run it from /opt/python2.7/bin/python

---

### Post by mongoose_za on 2010-11-16
> **davidism said:**
> Download the source from here:
[http://python.org/ftp/python/2.7/Python-2.7.tgz](http://python.org/ftp/python/2.7/Python-2.7.tgz)

```
tar xzf Python-2.7.tgz
cd Python-2.7
./configure
make
sudo make altinstall
```

Note that it is make altinstall, not make install.  The altinstall makes sure you don't clobber the OS installed version.

Hi I did the altinstall but don't see any benefit because everything is still just running through python 2.6. Should I remove 2.6 in my Synaptic Package Manager? 

For interest how do I uninstall the python 2.7 to have my environment like it was before the altinstall?

Thanks.

---

### Post by Vox754 on 2010-11-16
> **mongoose_za said:**
> Hi I did the altinstall but **don't see any benefit** because everything is still just running through python 2.6. Should I remove 2.6 in my Synaptic Package Manager? 


Well, in general, there is no benefit in running a newer Python just because it is newer.

Your Ubuntu 10.10 system is designed to use Python 2.6, so if you attempt to use an older or newer version, it will most probably cause you problems.

The only valid reason to have multiple Python (Perl, Tcl, Bash, or other) interpreters is:
1. if you really know what you are doing, and
2. you know you need the features specific versions provide, for example, if you need to develop and support a legacy application.

The original poster presumably had a valid reason to install Python 2.7, because he wanted to use newer features that are not available yet in the current version.

You should not attempt to remove Python 2.6, because a lot of things in Ubuntu will break. Also, the Python installed from source, is not registered in the package manager. If you are successful in removing the old one, you will break lots of dependencies. Although it may be possible to force the newer installation, what will happen when you try to upgrade to the newest Ubuntu 11.04? How is the package manager supposed to know? It will reinstall Python 2.6 and then continue upgrading to the newer Python anyway. So in summary, it's a mess.

What I'm trying to say is, you can force your way and install everything you like, but be conscious that versions, regular Ubuntu releases, package managers, etc. are there for a reason.

> 
For interest how do I uninstall the python 2.7 to have my environment like it was before the altinstall?

Thanks.

Python is notoriously difficult to remove from source.

As in any program in Linux, you may just delete all the directories and files created by the installation, and that is equivalent to removing it.

Your environment is not changed. As all programs by default use "/usr/bin/python", and this symlink points to "/usr/bin/python2.6", you should be fine.

Actually, that you have to call "python2.7" manually is a good thing, because then you can choose to run your programs with a stable, distribution-provided Python 2.6, or your installed 2.7.

Again, you can install everything you like, but if you don't understand very well what you are doing you should probably not attempt it in the first place.

My experience with this is that I actually helped someone who had this exact problem, a few weeks ago, on the IRC channel #ubuntu. He installed 2.7 and naturally his system was borked. I was a saint that day, and I helped him for an hour to get his system back. I actually recommended this same thread to him.

My advice is don't do it. Don't manually install new things just for the sake of it.

And let this thread rest in piece, so that others may find good advice in the future, instead of polluting it with unnecessary comments.

---

### Post by Stardust85 on 2011-02-06
If you only need a few features of 2.7, you can install them from pypi too. For example OrderedDict is here [http://pypi.python.org/pypi/ordereddict/](http://pypi.python.org/pypi/ordereddict/)

how to install:
tar -xcvf ordereddict*gz
cd ordereddict*
sudo python setup install
[enter password]

That's all!

---

### Post by leonbravo on 2011-03-13
Hey, what about dependecies? 

I am installing a program (gns3 0.7.3), in the process it checks dependencies.

I can install with all altinstall but would it be update dependencies?

or better going for the source and make install of gns3.

cheers.

---

### Post by amont on 2011-03-22
> **Vox754 said:**
> Well, in general, there is no benefit in running a newer Python just because it is newer.

(...)

My advice is don't do it. Don't manually install new things just for the sake of it.

And let this thread rest in piece, so that others may find good advice in the future, instead of polluting it with unnecessary comments.

Thank-you very much, Vox754, 4 months later, your helpful post has avoided me a lot of problems. :)

---

### Post by ashwoods on 2011-05-03
There are many reasons why somebody would want python 2.7 :)
In lucid, you might want to try using pythonbrew:
[https://github.com/utahta/pythonbrew](https://github.com/utahta/pythonbrew)

Kind of like a virtualenv for python interpreters.
(And you should be using virtualenv and maybe virtualenvwrapper)
[http://pypi.python.org/pypi/virtualenv](http://pypi.python.org/pypi/virtualenv)

happy python coding.
ash

---

### Post by wmcbrine on 2011-05-03
Or, at this point, you could just switch to Ubuntu 11.04 and get Python 2.7 with it...

---

### Post by pythonprog on 2011-07-23
Hi,

I am using Ubuntu 10.04 and Python v 2.6. Python v 2.6 does not support a particular import statement (from collections import Counter). So I installed Python v 2.7. I intend to use MySQL database along with Python. My 2.6v is connected to MySQL with the help of apt-get install mysql-python. How do I do the same with Python v 2.7 and get it support MySQL?

---

### Post by d3v1150m471c on 2011-09-18
LOL, been using python2.7 for a long time now with the following:
```

#this may or may not be safe. use at your own risk, but it works for me.
sudo bash
cp /etc/apt/sources.list /etc/apt/sources.bak
sed -i 's/lucid/maverick/g' /etc/apt/sources.list
apt-get update
apt-get install python2.7
sed -i 's/maverick/lucid/g' /etc/apt/sources.list
apt-get update

```

it's a good habit to keep backups if you use hacks like this but most of the time i don't encounter problems.

---

### Post by kbos on 2011-10-05
Use PPA. This explained in [http://askubuntu.com/questions/17841/will-python2-7-be-available-for-10-04-in-the-future](http://askubuntu.com/questions/17841/will-python2-7-be-available-for-10-04-in-the-future)

---

### Post by d3v1150m471c on 2011-10-08
You can also install the source of python2.7 on 10.04 LTS
```

./configure --with-pydebug

``````

sudo bash
make install

```I haven't come across complications with this. it "just works" :-)

```

# "Safer" install from link posted above:
make altinstall

```Don't blame me if you break something though :-p

---

### Post by bharatj on 2012-07-10
I think you can download and install latest version python from [http://python.org/download/](http://python.org/download/)
But i think it is not a good idea to upgrade python on lucid. As ubuntu (In lucid case, as i have tried on it only) always recommend to have default python version. 
You can have both default and new version, by managing  symbolic links. But i messed up with both python versions. 
Result : I had to reinstall ubuntu again.

Since default version : 2.6.5, i too want to upgrade to 2.7. But right now i m not taking that risk. If anyone knows something which works perfectly on their machine without system getting unstable.Let me know.

---

### Post by manif on 2012-07-18
> **davidism said:**
> Download the source from here:
[http://python.org/ftp/python/2.7/Python-2.7.tgz](http://python.org/ftp/python/2.7/Python-2.7.tgz)

```
tar xzf Python-2.7.tgz
cd Python-2.7
./configure
make
sudo make altinstall
```

Note that it is make altinstall, not make install.  The altinstall makes sure you don't clobber the OS installed version.

i altinstalled python2.7 on my ubuntu(10.04) but i dont know how to activate(or something like that) python 2.7 for a specific software(which dependency's python2.7) to install or use.

---

