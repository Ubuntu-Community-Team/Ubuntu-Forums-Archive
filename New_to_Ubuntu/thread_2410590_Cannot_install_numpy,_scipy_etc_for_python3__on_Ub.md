---
title: "Cannot install numpy, scipy etc for python3  on Ubuntu 16.04"
date: 2019-01-17
forum: New to Ubuntu
---

### Post by Lou Reed on 2019-01-17
I am trying to install numy, scipy and a few other packages for python3. I can not and I am not sure why.

I installed Ubuntu 16.04 and they were available for python2.7. But not python3. I am using Python 3.7.2
which I installed a few days ago. Whenever, I try to install numpy, i [I]get the following response.


```

ames@james-VirtualBox:~$ sudo pip3 install numpy
[sudo] password for james: 
The directory '/home/james/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
pip is configured with locations that require TLS/SSL, however the ssl module in Python is not available.
The directory '/home/james/.cache/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting numpy
  Could not fetch URL https://pypi.python.org/simple/numpy/: There was a problem confirming the ssl certificate: Can't connect to HTTPS URL because the SSL module is not available. - skipping
  Could not find a version that satisfies the requirement numpy (from versions: )
No matching distribution found for numpy
james@james-VirtualBox:~$ 
james@james-VirtualBox:~$ 
james@james-VirtualBox:~$ sudo pip3 install scipy
The directory '/home/james/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
pip is configured with locations that require TLS/SSL, however the ssl module in Python is not available.
The directory '/home/james/.cache/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting scipy
  Could not fetch URL https://pypi.python.org/simple/scipy/: There was a problem confirming the ssl certificate: Can't connect to HTTPS URL because the SSL module is not available. - skipping
  Could not find a version that satisfies the requirement scipy (from versions: )
No matching distribution found for scipy




james@james-VirtualBox:~$ sudo -H pip3 install numpy
pip is configured with locations that require TLS/SSL, however the ssl module in Python is not available.
Collecting numpy
  Could not fetch URL https://pypi.python.org/simple/numpy/: There was a problem confirming the ssl certificate: Can't connect to HTTPS URL because the SSL module is not available. - skipping
  Could not find a version that satisfies the requirement numpy (from versions: )
No matching distribution found for numpy
james@james-VirtualBox:~$ sudo -H pip3 install scipy
pip is configured with locations that require TLS/SSL, however the ssl module in Python is not available.
Collecting scipy
  Could not fetch URL https://pypi.python.org/simple/scipy/: There was a problem confirming the ssl certificate: Can't connect to HTTPS URL because the SSL module is not available. - skipping
  Could not find a version that satisfies the requirement scipy (from versions: )
No matching distribution found for scipy
james@james-VirtualBox:~$ 

```

It states that it cannot verify the ssl certificate  when I try t install using 

sudo pip3 install numpy.

I have several version of python 3 on my hard drive, but none  of them claim to verify
the ssl certificate. 

I have tried everything. Nothing seems to work.

I believe that the ssl certificate is there, but it for some reason cannot be verified when I install numpy on say python 3.7.2

I installed python 3.7.2 as a package and I do not know how to confige it with ssl.

Any assistance appreciated. 

Respectfully,

ErnestTBass







[/I]

---

### Post by monkeybrain20122 on 2019-01-17
Are you running Ubuntu off virtualbox? Maybe you have internet problem.

---

### Post by Lou Reed on 2019-01-17
Yes, I am trying to run Ubuntu 16.04 off virtual box.I am not sure what you mean when you say,that I have an internet problem.

This has never given me any problems before.

Respectfully,

ErnestTBass

---

### Post by Lou Reed on 2019-01-18
To elaborate on my previous post, I am abe to access the internet using Ubuntu 16.004 in virtual box. 

I honestly do not think that is the problem, I believe it is something else.

I want to update openssl. I have the standard version that came with Ubuntu 16.04, this may be causing the error. 

However, the only way that I can see is do it is by source. That is my concern now.

When you compile or install from source it seems the most risky way to ugrade something.

For instance, I have this question:

1. What happens to the openssl that is installed on the laptop now. It must somehow be removed since you cannot have two openssl's (albeit different versions) on the same hard drive. 
Also, when installing from source how can I gurantee that it will install in the corrrect directories.

You start with the commmand on a tar file:

tr -xvzf   *********************.gz which unpacks it into one directory.

Then you do the configure, make, make install (although I think in the particular case you should run a make test, before make install) 

So how am I assured it will go into the correct directories? It just seems if it does not go into the correct places, that one could really
mess up what is currently installed.

Any help on this appreciated. Thankss in advance.

Respectfully,

Ernest-T-Basss

---

### Post by monkeybrain20122 on 2019-01-19
How did you install pip3? If you installed from the repo maybe uninstall it first and installan up to date version with getpip.py  (run "sudo python3 getpip.py" ) [https://pip.pypa.io/en/stable/installing/](https://pip.pypa.io/en/stable/installing/)

---

### Post by Lou Reed on 2019-01-20
I will try it.Thanks


R,

ErnestTBass.

---

### Post by Lou Reed on 2019-01-22
It worked. Thanks you very much.

Respectfully,

ErnestTBass

---

### Post by monkeybrain20122 on 2019-01-22
Hi, glad that it helped, now you can go to Thread Tools and check mark the thread as solved.

---

