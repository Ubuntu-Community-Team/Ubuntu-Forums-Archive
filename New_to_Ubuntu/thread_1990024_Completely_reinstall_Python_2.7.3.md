---
title: "Completely reinstall Python 2.7.3"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-29
Ive come to the conclusion that my python install is dodgy. How do I completely reinstall python? Im running 12.04.

---

### Post by nipunshakya on 2012-05-29
goto software center, search for Python IDLE, download it... there are idle for version 3.2 as well...

---

### Post by Senior_Buckethead on 2012-05-29
But how do I clean out the old version of python first. I dont just want to install a new version over the top. My current dillema stems from a bad decision to download and make 2.6, which has just screwed everything up and there are several things in my system that just dont work right (or at all) now.

See when I querry python in terminal I get:
```

glenn@acer:~$ python --version
Python 2.6
glenn@acer:~$ 

```
Yet I never installed 2.6. Its supposed to be 2.7.3

---

### Post by kramer65 on 2012-05-29
Disclaimer: I'm not a Linux-guru. But these tips may possibly of help.. :-)

I'dd try to go to Synaptic, search for python, and mark all installed packages for reinstallation. If that doesn't work, try completely removing them and then installing them again. 

If that doesn't work, it may be that python 2.7 is installed properly, but that typing 'python' leads to version 2.6 which has also been installed somehow. I think you can fix that by creating a symlink to the corret executable which should be located in /usr/bin/python2.7. I *think* you then need to create a symlink from /usr/bin/python to /usr/bin/python2.7 by typing
```
ln -s /usr/bin/python /usr/bin/python2.7
```

But please, can somebody back this up?

---

### Post by Senior_Buckethead on 2012-05-29
Hey thanks for that.

I've tried using symbolic links and they just don't seem to work. I think because my install of python is broken,such links don't work.
Id love to go to synaptic and mark all packages for reinstall, but I dont know if I would be reinstalling the right packages since my botched 2.6 install might have installed the wrong packages and thus be marked in synaptic. In other words would I just be reinstalling a mistake.

---

### Post by nipunshakya on 2012-05-29
> **Senior_Buckethead said:**
>  My current dillema stems from a bad decision to download and make 2.6, which has just screwed everything up and there are several things in my system that just dont work right (or at all) now.

Yet I never installed 2.6. Its supposed to be 2.7.3

What does that mean? didn't u download and install 2.6 from software center?? 

current installations  have several dependencies over the  default Dependency package of Python as well.. due to that, somethings in your system doesn't work right...(i assme)

I **guess** your "**download and make 2.6**" changed default from 2.7.3 to 2.6...

---

### Post by nipunshakya on 2012-05-29
The Following links have similar thoughts to share...hope they might help as well:

[http://ubuntuforums.org/showthread.php?t=1576508](http://ubuntuforums.org/showthread.php?t=1576508)
[http://www.warp1337.com/content/how-change-default-python-version-ubuntu-910](http://www.warp1337.com/content/how-change-default-python-version-ubuntu-910)

---

### Post by Senior_Buckethead on 2012-05-29
Yeah,  I wanted to have python 2.6 for makehuman. makehuman wouldn't run from 2.7.3. I downloaded the source and make but didn't install, from memory because i didn't know where to put the source directory to make from, so I chickened out. But I think its screwed up my python install because now I install anything that depends on python just wont run, and I've had other issues, ubuntu-one being one of them.
> 
What does that mean? didn't u download and install 2.6 from software center?? 
I don't install a new program via. software center, once I know the package name I install via. apt. I try and use terminal where I can.
> 
I **guess** your "**download and make 2.6**" changed default from 2.7.3 to 2.6...     
You have got it in one.
Thinking now that I should download and install 2.7.3 from source. Maybe that might cure my system ills. 
I really really don't want to have to reinstall 12.04 to cure this, since it took days to get things the way I want them.
Thanks for the links. Im not wanting to change between versions, I wanting to reinstall a broken python install.

---

### Post by nipunshakya on 2012-05-29
> **Senior_Buckethead said:**
> 
I really really don't want to have to reinstall 12.04 to cure this, since it took days to get things the way I want them.
Thanks for the links. Im not wanting to change between versions, I wanting to reinstall a broken python install.


Well, you should wait for someone with a solution mate. Im out of any suggestions... Maybe someone can back u up now... 


Goodluck. 
Happy Linuxing

---

### Post by PeterP24 on 2012-05-29
in a terminal try:

python2.7 --version

to see if the python 2.7 version is present.

Then, go to synaptic (not the ubuntu software center), uninstall the 2.6 version and if the 2.7 version is not present on your system, install it. Synaptic gives you detailed information on which package and version is each. Just go directly for the versions, and ignore the generic python package. This works for me - I don't know how you managed to set up python 2.6 as the default - I have the 2.5, 2.6, 2.7 and 3.x something versions installed. Still the 2.7 version is pulled by default when I type python into terminal.

---

### Post by lukeiamyourfather on 2012-05-29
> **Senior_Buckethead said:**
> My current dillema stems from a bad decision to download and make 2.6, which has just screwed everything up and there are several things in my system that just dont work right (or at all) now.

Many things rely on Python in Ubuntu. If you installed a different version of Python from source then the system is pretty much jacked. **[COLOR="DarkRed"]Never ever install Python from source unless you absolutely must[/COLOR]**, and even then use 'make alt-install' instead of 'make install' which will prevent it from overwriting the currently installed Python.

Why did you want to install an older version to begin with? Anything that worked in Python 2.6 should work in Python 2.7 as well. Also if you need alternate versions of Python check the repositories first. For example you can install Python 3.X with the command 'sudo apt-get install python3' and that won't overwrite the currently installed Python (you get 'python' and 'python3' commands so you can work with either).

---

### Post by PeterP24 on 2012-05-29
> **lukeiamyourfather said:**
> Many things rely on Python in Ubuntu. If you installed a different version of Python from source then the system is pretty much jacked. **[COLOR="DarkRed"]Never ever install Python from source unless you absolutely must[/COLOR]**, and even then use 'make alt-install' instead of 'make install' which will prevent it from overwriting the currently installed Python.

Why did you want to install an older version to begin with? Anything that worked in Python 2.6 should work in Python 2.7 as well. Also if you need alternate versions of Python check the repositories first. For example you can install Python 3.X with the command 'sudo apt-get install python3' and that won't overwrite the currently installed Python (you get 'python' and 'python3' commands so you can work with either).

Wow - I never expected that an older python version installation to cripple the system. I reread his posts and saw that he "download and make 2.6". But 2.6 it was already in the repositories ...

---

### Post by Senior_Buckethead on 2012-05-29
Thanks Peter
Reading back over the posts you will see that although Im supposed to have 2.7.3 installed, I messed it up and now I when I type python --version I get:
```

glenn@acer:~$ python --version
Python 2.6
glenn@acer:~$ 

```Although I never installed 2.6, as described above, its still there.
Ive downloaded python3.0.tgz and am going to compile from source, to end this mucking around tweaking python versions that aren't working.

Upon reading more posts...
Oh come on fellas, stop making me rewrite stuff, I have told you that my Python Installation is broken, and why I want to reinstall python.

---

### Post by PeterP24 on 2012-05-29
> **Senior_Buckethead said:**
> Thanks Peter
Reading back over the posts you will see that although Im supposed to have 2.7.3 installed, I messed it up and now I when I type python --version I get:
```

glenn@acer:~$ python --version
Python 2.6
glenn@acer:~$ 

```Although I never installed 2.6, as described above, its still there.
Ive downloaded python3.0.tgz and am going to compile from source, to end this mucking around tweaking python versions that aren't working.

Upon reading more posts...
Oh come on fellas, stop making me rewrite stuff, I have told you that my Python Installation is broken, and why I want to reinstall python.

Ok - let me see if I got it right this time - your installation of python is broken because you have python 2.6 instead of 2.7? You tried to fix the problem by using synaptic to uninstall 2.6 and it doesn't work? Python version 2.7 doesn't exist on your system anymore? Are these correct? 

I read your last post, about going with python3.0. You know that there are small incompatibilities with the 2.7 version (actually with all 2.x versions in general)? Some python libraries were never updated to 3.x version - so you were warned about it!

---

### Post by Senior_Buckethead on 2012-05-29
> 
Ok - let me see if I got it right this time - your installation of  python is broken because you have python 2.6 instead of 2.7? You tried  to fix the problem by using synaptic to uninstall 2.6 and it doesn't  work? Python version 2.7 doesn't exist on your system anymore? Are these  correct? 
Yes, my system is screwed up because although Python 2.7.3 is installed (12.04 shipped wit 2.7.3) I stupidly made 2.6, although I never thought I installed it. Anyway, I have applications that now wont run because python is broken.

Im done with trying to fix this, Im just going to install Python 3.01 from source. If in the end i have to reinstall 12.04 then thats what Ill have to do, but im over this nonsense.

---

### Post by nipunshakya on 2012-05-29
My suggestion, dont go and make 3.01 install in your machine, go with 2.7.3. Maybe that can replace 2.6 like 2.6 replaced your default one before... 
Goodluck

---

### Post by Senior_Buckethead on 2012-05-29
yeah I think your right there.

---

### Post by lukeiamyourfather on 2012-05-30
> **Senior_Buckethead said:**
> 
Im done with trying to fix this, Im just going to install Python 3.01 from source. If in the end i have to reinstall 12.04 then thats what Ill have to do, but im over this nonsense.

If I were in your shoes I'd just reinstall Ubuntu. If you want things to work properly don't mess with the system version of Python, you're asking for trouble since so many things rely on it. Don't install Python from source because this will overwrite the system Python. If you need an alternate version of Python check to see if its in the repositories (e.g. 'sudo apt-get install python3') which will cleanly install side by side with the system version of Python instead of overwriting it.

If you absolutely must have a version of Python compiled from source use 'make alt-install' when building it which will install it side by side with the system version of Python. THe 'make alt-install' is critical to avoid breaking everything in the system that relies on Python.

---

