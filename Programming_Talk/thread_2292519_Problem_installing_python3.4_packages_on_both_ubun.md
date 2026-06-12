---
title: "Problem installing python3.4 packages on both ubuntu and windows"
date: 2015-08-28
forum: Programming Talk
---

### Post by lance bermudez on 2015-08-28
I'm using python 3 because it can be used on both windows and Ununtu. I use it to secure files on ubuntu but now need it to do the same thing on windows
I have a program to use gnugpg on ubuntu but having trouble using it on windows. I have [http://www.lfd.uci.edu/~gohlke/pythonlibs](http://www.lfd.uci.edu/~gohlke/pythonlibs) vcredist_x86 installed so I do not know what I'm doing wrong.

<code>
C:\Python34>python -m pip install pygpgme
Collecting pygpgme
  Using cached pygpgme-0.3.tar.gz
Installing collected packages: pygpgme
  Running setup.py install for pygpgme
    Complete output from command C:\Python34\python.exe -c "import setuptools, t
okenize;__file__='C:\\Users\\leanne\\AppData\\Local\\Temp\\pip-build-bjacs5f0\\p
ygpgme\\setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().
replace('\r\n', '\n'), __file__, 'exec'))" install --record C:\Users\leanne\AppD
ata\Local\Temp\pip-_3q4r51c-record\install-record.txt --single-version-externall
y-managed --compile:
    running install
    running build
    running build_py
    creating build
    creating build\lib.win32-3.4
    creating build\lib.win32-3.4\gpgme
    copying gpgme\editutil.py -> build\lib.win32-3.4\gpgme
    copying gpgme\__init__.py -> build\lib.win32-3.4\gpgme
    running build_ext
    building 'gpgme._gpgme' extension
    error: Microsoft Visual C++ 10.0 is required (Unable to find vcvarsall.bat).


    ----------------------------------------
Command "C:\Python34\python.exe -c "import setuptools, tokenize;__file__='C:\\Us
ers\\leanne\\AppData\\Local\\Temp\\pip-build-bjacs5f0\\pygpgme\\setup.py';exec(c
ompile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), _
_file__, 'exec'))" install --record C:\Users\leanne\AppData\Local\Temp\pip-_3q4r
51c-record\install-record.txt --single-version-externally-managed --compile" fai
led with error code 1 in C:\Users\leanne\AppData\Local\Temp\pip-build-bjacs5f0\p
ygpgme
</code>

---

### Post by flaymond on 2015-08-29
Hi,

From the error log, you need vcvarsall to build the module/program.

I found a question  about this error - [http://stackoverflow.com/questions/27670365/python-pip-install-error-unable-to-find-vcvarsall-bat-tried-all-solutions](http://stackoverflow.com/questions/27670365/python-pip-install-error-unable-to-find-vcvarsall-bat-tried-all-solutions)

and another one - [https://support.enthought.com/hc/en-us/articles/204469210-Windows-Unable-to-find-vcvarsall-bat-cython-other-c-extensions-](https://support.enthought.com/hc/en-us/articles/204469210-Windows-Unable-to-find-vcvarsall-bat-cython-other-c-extensions-)

---

### Post by lance bermudez on 2015-09-03
install  Visual C++ 2010 Express from [http://download.microsoft.com/download/1/D/9/1D9A6C0E-FC89-43EE-9658-B9F0E3A76983/vc_web.exe](http://download.microsoft.com/download/1/D/9/1D9A6C0E-FC89-43EE-9658-B9F0E3A76983/vc_web.exe)
from [http://blog.ionelmc.ro/2014/12/21/compiling-python-extensions-on-windows/](http://blog.ionelmc.ro/2014/12/21/compiling-python-extensions-on-windows/)

and I was able to install packages with

python -m easy_install pycrypto 

did not get any errors like from before

---

