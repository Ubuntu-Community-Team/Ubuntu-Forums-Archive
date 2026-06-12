---
title: "Problem with petsc4py when reading importing it from a python file..."
date: 2012-11-14
forum: New to Ubuntu
---

### Post by astriedinger on 2012-11-14
I run a python program and I get :


s117555@ubuntu:~/SUmb_2/sumb/python/examples$ python nk_test.py
Traceback (most recent call last):
  File "nk_test.py", line 17, in <module>
    import petsc4py 
ImportError: No module named petsc4py
s117555@ubuntu:~/SUmb_2/sumb/python/examples$ 

BUt I know I have petsc4py already since when I write sudo easy_install petsc4py I get the following:

s117555@ubuntu:~/SUmb_2/sumb/python/examples$ sudo easy_install petsc4py
[sudo] password for s117555: 
Searching for petsc4py
Best match: petsc4py 3.3
petsc4py 3.3 is already the active version in easy-install.pth

Using /usr/local/lib/python2.7/dist-packages
Processing dependencies for petsc4py
Finished processing dependencies for petsc4py
s117555@ubuntu:~/SUmb_2/sumb/python/examples$ 

SO I realy dont know what is going on..? WHy is is not in my python library?? is it like that or I am getting confused..

---

### Post by drmrgd on 2012-11-14
It looks like easy_install may have installed the modules to a location that's not part of your $PYTHONPATH somehow.  Is this  your first time using easy_install, and can you confirm that you configured it correctly?  Here's some docs on configuring just in case:

[http://packages.python.org/distribute/easy_install.html#custom-installation-locations](http://packages.python.org/distribute/easy_install.html#custom-installation-locations)

---

### Post by astriedinger on 2012-11-14
Hey, I dont know that, I will read it, but its funny when I type cd ${PYTHONPATH} THE TERMINAL gets me to home reight away... that shouldnt be right???

---

### Post by astriedinger on 2012-11-14
Actualy when I got python I did not specified which folder or user or anything, so he may just have installe dit in a default place right???

WHat happends is in my .bschr file I have an 
export PYTHONPATH=${PYTHONPATH}:${HOME}/SUmb_2/mdo_import_helper

Becasue I need to export it for an aplication, according to my teacher... could have this damaged the path petsc4py was installed

---

### Post by drmrgd on 2012-11-14
The line you've added to .bashrc just appends the directory '${HOME}/SUmb_2/mdo_import_helpe' to the current Python path.  So that shouldn't break anything as far as I can tell. 

$PYTHONPATH is not a bash environmental variable.  So, if you try to 'cd $PYTHONPATH' it's the same as just typing 'cd' (which is a shortcut to go to your $HOME directory) as $PYTHONPATH is null.  You can test this by typing:

```
echo $PYTHONPATH
``` 

which won't return anything.

I have not used easy_install before myself, I don't know the specifics of the configuration file and where it installed modules by default.  Perhaps someone with a little more experience would know.  But, as it stands now, your $PYTHONPATH looks to be the standard $PYTHONPATH plus ${HOME}/SUmb_2/mdo_import_helper.  If you want to check, launch python from the terminal and run these two commands:

```
import sys
print sys.path
```

Note, the syntax is a little different if you're running Python 3.

What you need to do is make sure the configuration of easy_installer is correct (to save future headaches!), find out where the petsc4py module was installed, and make sure that the location of that module is part of your $PYTHONPATH.  

Hope that makes sense

---

### Post by astriedinger on 2012-11-14
Thanks man I will try that, in the mean while, when I run echo $PYTHONPATH, I do get something...

s117555@ubuntu:~$ echo $PYTHONPATH
:/home/s117555/SUmb_2/mdo_import_helper

For some reason I wrote before in the PYTHONPATH =  to the actual directory of my python,.. but then erase it but kept the line of export....

Now I run the python, and ..
s117555@ubuntu:~$ python
Python 2.7.3 (default, Nov  9 2012, 14:40:22) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.path
['', '/home/s117555', '/home/s117555/SUmb_2/mdo_import_helper', '/usr/local/lib/python27.zip', '/usr/local/lib/python2.7', '/usr/local/lib/python2.7/plat-linux2', '/usr/local/lib/python2.7/lib-tk', '/usr/local/lib/python2.7/lib-old', '/usr/local/lib/python2.7/lib-dynload', '/home/s117555/.local/lib/python2.7/site-packages', '/usr/local/lib/python2.7/site-packages']
>>> 

The location where my petsc4py is not there cuz I cheked and it is :

/usr/local/lib/python2.7/dist-packages

But since my location in the SUmb_2 directory actualy appear I am going to try if by adding the previous directory as 
export PYTHONPATH=${PYTHONPATH}:/usr/local/lib/python2.7/dist-packages

adds the directory and lets see if it i solved.... thansk for helping me understand man.. =) I will keep checking

---

### Post by drmrgd on 2012-11-14
> **astriedinger said:**
> Thanks man I will try that, in the mean while, when I run echo $PYTHONPATH, I do get something...

s117555@ubuntu:~$ echo $PYTHONPATH
:/home/s117555/SUmb_2/mdo_import_helper

For some reason I wrote before in the PYTHONPATH =  to the actual directory of my python,.. but then erase it but kept the line of export....



Whoops!  Sorry about that; I forgot for a second you added the the export command to .bashrc.  In that case, $PYTHONPATH does associate with the bash environmental variables and will give a result.  The original syntax you had in your .bashrc file is correct I believe.  So, no need to change that.  And, if you add the line you proposed, that should add that directory to $PYTHONPATH, and you should now be able to import your module.

---

### Post by astriedinger on 2012-11-14
Yes indeed, I think that part solved it , thanks a lot bro. NOw I am stuck finding the  name MPI

the file i use is trying to impor MPI I guess is the same as having openmpi since I had to install it in order to compile the program I am runing now... irony in live... But I am not able to find the path for this MPI,,,I went to the system manager to install it, so I look for MPI and install some, but it still didnt help.... I t seems I will get more import errors like this.


Yuk, this is for working with private files from another damn computer in the US...who knows what they added to their paths and dont remember now.

---

