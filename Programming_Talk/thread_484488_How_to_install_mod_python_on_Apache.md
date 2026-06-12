---
title: "How to install mod_python on Apache?"
date: 2007-06-25
forum: Programming Talk
---

### Post by ablegreen on 2007-06-25
How the heck do you do this? I've been working for hours trying to figure the problem out.

I have:
apache_2.2.4-win32-x86-no_ssl.msi
python-2.5.1.msi
mod_python-3.3.1.win32-py2.5-Apache2.2.exe

I install fresh all the programs above. I follow the directions after the installation of mod_python-3.3.1.win32-py2.5-Apache2.2.exe, and all I get when testing it out was an Internal Server Error.

So I check my error log and it all the paths to the python executables and location folder is pointing to some kind of unrelevant folder (I uninstalled the xampp program, and deleted the folder). I checked my PATH variables in the system and the only thing in there is C:/Python25 (where Python is installed). Apache is in C:/programs files/Apache software foundation/apache2.2/

Heres part of the error log:
> [Mon Jun 25 17:58:16 2007] [notice] Parent: Created child process 5028
[Mon Jun 25 17:58:16 2007] [error] python_init: Python version mismatch, expected '2.5', found '2.5.1'.
[Mon Jun 25 17:58:16 2007] [error] python_init: Python executable found 'C:\\Program Files\\Apache Software Foundation\\Apache2.2\\bin\\httpd.exe'.
[Mon Jun 25 17:58:16 2007] [error] python_init: Python path being used 'C:\\WINDOWS\\system32\\python25.zip;c:\\xampp\\python\\DLLs;c:\\xampp\\python\\lib;c:\\xampp\\python\\lib\\plat-win;c:\\xampp\\python\\lib\\lib-tk;C:\\Program Files\\Apache Software Foundation\\Apache2.2\\bin'.
[Mon Jun 25 17:58:16 2007] [notice] mod_python: Creating 8 session mutexes based on 0 max processes and 250 max threads.
[Mon Jun 25 17:58:16 2007] [notice] Child 5028: Child process is running
[Mon Jun 25 17:58:16 2007] [notice] Child 5028: Acquired the start mutex.
[Mon Jun 25 17:58:16 2007] [notice] Child 5028: Starting 250 worker threads.
[Mon Jun 25 17:58:16 2007] [notice] Child 5028: Starting thread to listen on port 80.
[Mon Jun 25 17:58:20 2007] [error] make_obcallback: could not import mod_python.apache.\n
[Mon Jun 25 17:58:21 2007] [error] make_obcallback: Python path being used "['C:\\\\WINDOWS\\\\system32\\\\python25.zip', 'c:\\\\xampp\\\\python\\\\DLLs', 'c:\\\\xampp\\\\python\\\\lib', 'c:\\\\xampp\\\\python\\\\lib\\\\plat-win', 'c:\\\\xampp\\\\python\\\\lib\\\\lib-tk', 'C:\\\\Program Files\\\\Apache Software Foundation\\\\Apache2.2\\\\bin']".
[Mon Jun 25 17:58:21 2007] [error] get_interpreter: no interpreter callback found.
[Mon Jun 25 17:58:21 2007] [error] [client 127.0.0.1] python_handler: Can't get/create interpreter.
[Mon Jun 25 17:58:21 2007] [error] [client 127.0.0.1] File does not exist: C:/Program Files/Apache Software Foundation/Apache2.2/htdocs/favicon.ico
[Mon Jun 25 18:01:21 2007] [error] make_obcallback: could not import mod_python.apache.\n
[Mon Jun 25 18:01:21 2007] [error] make_obcallback: Python path being used "['C:\\\\WINDOWS\\\\system32\\\\python25.zip', 'c:\\\\xampp\\\\python\\\\DLLs', 'c:\\\\xampp\\\\python\\\\lib', 'c:\\\\xampp\\\\python\\\\lib\\\\plat-win', 'c:\\\\xampp\\\\python\\\\lib\\\\lib-tk', 'C:\\\\Program Files\\\\Apache Software Foundation\\\\Apache2.2\\\\bin']".
[Mon Jun 25 18:01:21 2007] [error] get_interpreter: no interpreter callback found.
[Mon Jun 25 18:01:21 2007] [error] [client 127.0.0.1] python_handler: Can't get/create interpreter.
[Mon Jun 25 18:01:22 2007] [error] make_obcallback: could not import mod_python.apache.\n
[Mon Jun 25 18:01:22 2007] [error] make_obcallback: Python path being used "['C:\\\\WINDOWS\\\\system32\\\\python25.zip', 'c:\\\\xampp\\\\python\\\\DLLs', 'c:\\\\xampp\\\\python\\\\lib', 'c:\\\\xampp\\\\python\\\\lib\\\\plat-win', 'c:\\\\xampp\\\\python\\\\lib\\\\lib-tk', 'C:\\\\Program Files\\\\Apache Software Foundation\\\\Apache2.2\\\\bin']".
[Mon Jun 25 18:01:22 2007] [error] get_interpreter: no interpreter callback found.
[Mon Jun 25 18:01:22 2007] [error] [client 127.0.0.1] python_handler: Can't get/create interpreter.

I already uninstalled the xampp and the folder and checked the PATH stuff again, and it still keeps pointing to the xampp folder which isn't even there.

What the heck is going on? I tried installing python in the C:/programs files/Apache software foundation/apache2.2/

Jeez this is frustrating...

---

### Post by skullmunky on 2007-06-26
i can't help you too much 'cause i only know how to do this in linux.  try, ah, installing ubuntu, and then see how that goes :p

my first guess is this:

check your version of python, see if you need to downgrade to 2.5.  

python_init: Python version mismatch, expected '2.5', found '2.5.1'.

i don't know if that bogus path comes from python, or from, apache, or from a registry value ...

---

