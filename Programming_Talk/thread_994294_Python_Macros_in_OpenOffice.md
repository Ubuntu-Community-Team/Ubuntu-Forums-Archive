---
title: "Python Macros in OpenOffice"
date: 2008-11-26
forum: Programming Talk
---

### Post by MickSulley on 2008-11-26
Hi,
I am trying to learn Python Macros to be able to add them to OO spreadsheets.  The info that I have found says that the share directory is /usr/lib/openoffice/share/Scripts/python , that is fine, but is also says that the user directory is ~/.openoffice.org.2.0/user/Scripts/python
and I cannot find that or anything like it.
Can anyone tell me where OpenOffice will look for user Python scripts please?

Thanks

---

### Post by pmasiar on 2008-11-26
This is rather specialized question requiring esoteric and deep knowledge of OO.O - IMHO you are better off trying to ask at dedicated OO.O forum or mailing list. Good luck!

---

### Post by rohitgoyal18 on 2011-05-18
hi.

i am replying to this so that many other users who must be having the same problem like me and you could benefit from it.
you have read it right.
share directory for Python macros  is     /usr/lib/openoffice/share/Scripts/python 
as well as                                            ~/.openoffice.org.2.0/user/Scripts/python
while the former allows you to add a macro that would be available to all the users of the system(since Linux is meant for multiuser environment), the latter allows you to add the macros that will be only available to 1 particular user(depending on who's home directry are you in).

Now, as you said, you cann't  see these directories. well, you need to create the directory.
i Hope you do know that .openoffice.org would be a hidden type. also, i have seen that the Scripts folder in second case is empty. So, you can just create a directory of name "python" and place your scripts in it. 
to make your scripts visible in the macros inside open office, you will have to put the .pyc file in the python folder otherwise it won't show the python script in executable format. PS> dont forget to make the file executable.
to make the .pyc file from the py file, use the command 
python -m compileall filename.py

And do look at the sample code of helloworld place under the /usr/lib/openoffice/share/Scripts/python directory. IT will give you a fair Idea about how the macros work inside the open office. It is much more complex than a simple helloworld program of python.

NOTE: these fact remains the same in the higher version of open office too. Just the directory under the Home is changed to the subsequent version. eg: ~/.openoffice.org/3/ user/Scripts/python

---

