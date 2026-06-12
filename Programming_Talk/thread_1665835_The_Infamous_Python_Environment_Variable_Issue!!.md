---
title: "The Infamous Python Environment Variable Issue!!"
date: 2011-01-12
forum: Programming Talk
---

### Post by freesparks on 2011-01-12
Hello Ubuntu Collective, 
 
      Well I've officially given up on trying to fix my python paths,  but here are my findings.  I must have broken my blender install as it  relates to coding and launching blender in context of python3.1 from  Ubuntu's version 10.10 (Maverick).  First off, if it gives you guys any  inclination I am trying to run Komodo and other IDE's in context of  Blender.. In a tutorial that I found on-line with other people that were  having the same problem, I found that first off, a lot of users claim  that the the profile and profile.d(located in /etc/)are the files that I  should be concerned with, in terms of setting environment variables for  python. There instructions, which are primarily a culmination of a lot  of writings explained that the first thing I should do is launch python  in the linux Terminal: 
 
So, in lieu to this, after running: 
 
unset PYTHONHOME 
unset PYTHONPATH 
 
( Of course, If I don't do this, I get this: 
myname@mysystem:~$ python 
'import site' failed; use -v for traceback 
ActivePython 2.6.6.17 (ActiveState Software Inc.) based on 
Python 2.6.6 (r266:84292, Nov 23 2010, 18:36:13) 
[GCC 4.0.2 20051125 (Red Hat 4.0.2-[IMG]http://www.blender.org/forum/images/smiles/icon_cool.gif[/IMG]] on linux2 
Type "help", "copyright", "credits" or "license" for more information. 
>>> 
) 
 
I type python in the Terminal after unsetting PYTHONHOME and PYTHONPATH and I get this: 
 
(myname@mysystem:~$ python 
ActivePython 2.6.6.17 (ActiveState Software Inc.) based on 
Python 2.6.6 (r266:84292, Nov 23 2010, 18:36:13) 
[GCC 4.0.2 20051125 (Red Hat 4.0.2-[IMG]http://www.blender.org/forum/images/smiles/icon_cool.gif[/IMG]] on linux2 
Type "help", "copyright", "credits" or "license" for more information. 
>>>) 
 
So as you can see, I no longer get the error that I received above. 
 
After this the tutorial says to type python, then: 
>>> import sys 
>>> print sys.path 
 
,which gives me this: 
 
['', '/opt/ActivePython-2.6/lib/python26.zip',  '/opt/ActivePython-2.6/lib/python2.6',  '/opt/ActivePython-2.6/lib/python2.6/plat-linux2',  '/opt/ActivePython-2.6/lib/python2.6/lib-tk',  '/opt/ActivePython-2.6/lib/python2.6/lib-old',  '/opt/ActivePython-2.6/lib/python2.6/lib-dynload',  '/opt/ActivePython-2.6/lib/python2.6/site-packages',  '/opt/ActivePython-2.6/lib/python2.6/site-packages/setuptools-0.6c11-py2.6.egg-info'] 
 
I then try and copy this info to my .bashrc file in my home directory  and nothing happens, and of course I edit it so its in the correct  syntax in my .bashrc file which then looks like this: 
 
PYTHONPATH=/opt/ActivePython-2.6/lib/python26.zip;/opt/ActivePython-2.6/lib/python2.6;/opt/ActivePython-2.6/lib/python2.6/plat-linux2;/opt/ActivePython-2.6/lib/python2.6/lib-tk;/opt/ActivePython-2.6/lib/python2.6/lib-old;/opt/ActivePython-2.6/lib/python2.6/lib-dynload;/opt/ActivePython-2.6/lib/python2.6/site-packages;/opt/ActivePython-2.6/lib/python2.6/site-packages/setuptools-0.6c11-py2.6.egg-info 
 
And, this still does not work. One things for certain, however, the  profile file, located in /etc did contain /usr/lib64/python2.6 as  PYTHONPATH, which is exactly what I got prior to installing  ActiveState's version of python 3.1(which seems to have conflicted with  my working system python3 install.   Again, this is a huge learning  process for me and I thank you for all your help. Thanks so much for all  your help. I can't wait to really start coding. 
 
Best Regards,

freesparks

---

### Post by freesparks on 2011-01-12
Update,

  I actually fixed this partially.  The system python2.6, and python2.7 works.  However when I type python3 or python3.1 in my Terminal, I get this:

myname@mycomputer:~$ python3
Fatal Python error: Py_Initialize: can't initialize sys standard streams
Traceback (most recent call last):
  File "/usr/lib/python2.6/encodings/utf_8.py", line 9, in <module>
Aborted

For whatever reason, the system still seems to be pointing to Python2.6, which is the installed version that came with Ubuntu10.10(Maverick)!!  My Komodo install seems to have broken it.  Any help on this would be greatly appreciated guys, I can't wait to start programming and using Blender!!

Best Regards,

freesparks

---

### Post by freesparks on 2011-01-12
For whatever reason, the profile file located in /etc/ is what was breaking the installation.  Once I went in and erased this portion the code, which is located at the end of the file, that seemed to have taken care of everything:
 
This is what I erased:

 PATH="$PATH:/opt/blender"
 export PATH
 
 if [ -x /usr/bin/python ]; then
   PYTHONPATH=/usr/lib/python2.6:/usr/lib/python2.7:/usr/lib/python2.6/dist-packages:/opt/ActiveTcl-8.4:/opt/ActiveTcl-8.5:/usr/lib/python3.1/tkinter:/usr/lib/tk8.4:/usr/lib/tk8.5:/opt/py31:/opt/py31/bin
   PYTHONHOME=$PYTHONPATH
   export PYTHONPATH PYTHONHOME
 fi
 
 if [ -x /usr/bin/python ]; then
   PYTHONOPTIMIZE=true
   export PYTHONOPTIMIZE
 fi

What this does, I have no idea, but it sure did cause me a lot of grief.

Best Regards,

freesparks

---

