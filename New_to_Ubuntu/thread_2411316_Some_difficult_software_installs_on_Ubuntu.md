---
title: "Some difficult software installs on Ubuntu"
date: 2019-01-28
forum: New to Ubuntu
---

### Post by Lou Reed on 2019-01-28
I have a new install of ubuntu 16.04. I want to installl nltk on the system. How do I do that?

It does work install when I type :

pip3 install ntlk

There has to be more. I do not want to install it beginning a tar file since that require using something like checkinstall  to install it
and which would be needed to uninstall it. I want to be able to easily uninstall a program and initially tar install is not the way to do it.

Finally, I want to install Anaconda. I aware of the benifts of using the Anaconda software. Howver, I have only seen it install as a 
*.sh file. Again, I am worried about installing a software app thta way since it seems it would be difficult to install.

Respectfully,

ErnestTBass

---

### Post by monkeybrain20122 on 2019-01-28
> **James_M._Yunker said:**
> I have a new install of ubuntu 16.04. I want to installl nltk on the system. How do I do that?

It does work install when I type :

pip3 install ntlk

There has to be more. 


So where is it installed? You need sudo if you install it in the default location /usr/local/lib/python3.5/dist-packages
if you run pip3 without sudo you need the --user option
```
pip3 install -U nltk --user
```
This would install in ~/.local/lib/python3.5/site-packages

You can check where your modules are installed from python with .__file__, for example
```
$python3 
Python 3.5.2 (default, Nov 12 2018, 13:43:14) 
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import nltk
>>> nltk.__file__
'/usr/local/lib/python3.5/dist-packages/nltk/__init__.py'
>>> 
```
> 
I do not want to install it beginning a tar file since that require using something like checkinstall  to install it
pip isntalls a binary. 

> Finally, I want to install Anaconda. I aware of the benifts of using the  Anaconda software. Howver, I have only seen it install as a 
*.sh file. Again, I am worried about installing a software app thta way since it seems it would be difficult to install.


The .sh file is an install script. It installs the anaconda packages in a subdirectory (called anaconda3 IIRC) in your $HOME.
There is one tricky part when you install anaconda. It asks to add a line like 
```
export PATH="/home/your_username/anaconda3/bin:$PATH"
``` to your .bashrc so that the system can find the anaconda packages. 
**SAY NO **and instead add a line like this to .bashrc manually
```
export PATH="$PATH:/home/your_username/anaconda3/bin"
```
The difference is that you don't want the anaconda packages to replace your system defaults, that will most likely screw up your system somehow, you only want them to be available. So $PATH comes first.

---

### Post by Lou Reed on 2019-01-28
```

pip3 install -U nltk --user
Collecting nltk
  Downloading https://files.pythonhosted.org/packages/6f/ed/9c755d357d33bc1931e157f537721efb5b88d2c583fe593cc09603076cc3/nltk-3.4.zip (1.4MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 1.4MB 5.5MB/s 
Requirement already satisfied, skipping upgrade: six in /usr/lib/python3/dist-packages (from nltk) (1.10.0)
Collecting singledispatch (from nltk)
  Downloading https://files.pythonhosted.org/packages/c5/10/369f50bcd4621b263927b0a1519987a04383d4a98fb10438042ad410cf88/singledispatch-3.4.0.3-py2.py3-none-any.whl
Building wheels for collected packages: nltk
  Building wheel for nltk (setup.py) ... done
  Stored in directory: /home/james/.cache/pip/wheels/4b/c8/24/b2343664bcceb7147efeb21c0b23703a05b23fcfeaceaa2a1e
Successfully built nltk
Installing collected packages: singledispatch, nltk
Successfully installed nltk-3.4 singledispatch-3.4.0.3
james@james-VirtualBox:~$ 
james@james-VirtualBox:~$ 
james@james-VirtualBox:~$ 
james@james-VirtualBox:~$ python3
Python 3.5.2 (default, Nov 12 2018, 13:43:14) 
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import ntlk
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named 'ntlk'

```


As you can see the method that you showed me worked in the install line. Then when I typed python3
and import ntlk it gave me an error.

I have seen this error before. it is the one I got when I initially tried to install ntlk typing

pip3 install ntlk

or 

sudo pip3 install ntlk

How do I get rid of it?

Respectfully,

ErnestTBass

---

### Post by monkeybrain20122 on 2019-01-28
It is nltk, not ntlk. You misspelled in your import.

---

### Post by Lou Reed on 2019-01-28
I sand corrected you are correct.

Sorry about the misstep. My bad.

Thanks.

Respectfully,

ErnestTBasss

---

### Post by Lou Reed on 2019-01-28
One question about installing Anaconda.Since I am purposely being very careful about software installs. By that I mean I will not install anything that cannot be easily reversed and uninstalled. It has been awhile since I used a *.sh fie to install. 

My question is can this be easily uninstalled? Can this install with a *.sh file be reversed? I am reluctant to install Anaconda, unless I can easily uninstall it.  

ErnestTBass

---

### Post by monkeybrain20122 on 2019-01-28
> **James_M._Yunker said:**
> One question about installing Anaconda.Since I am purposely being very careful about software installs. By that I mean I will not install anything that cannot be easily reversed and uninstalled. It has been awhile since I used a *.sh fie to install. 

My question is can this be easily uninstalled? Can this install with a *.sh file be reversed? I am reluctant to install Anaconda, unless I can easily uninstall it.  

ErnestTBass


It is very clean and easy.To "uninstall" just delete the anaconda3 (something like that)  folder in your $HOME and edit .bashrc to remove the export PATH=... line I mentioned earlier. 

P.S The .sh file is just an install script, that it is a .sh file doesn't really tell you how hard or easy to uninstall, it depends on actual program.

---

### Post by Lou Reed on 2019-01-29
Okay, which version of Anaconda should I install? I have Python 3.5.2 and there are some versions of Anaconda that only work with Python 3.6 or higher. Clearly that type version is not for me. I also am using Ubuntu 16.04, 64 bit linux.

Respectfully,

ErnestTBass

---

### Post by monkeybrain20122 on 2019-01-29
I think it means the Anaconda's python is 3,6 or higher. Anaconda is a kind of virtual environment that allows you to run multiple versions of python and independent of your system's (3.5.2) Anyway I don't use Anaconda, so read the instructions for more details.

---

### Post by Topsiho on 2019-02-01
In synaptic I see the correct package names are python-nltk and python3-nltk

Topsiho

---

