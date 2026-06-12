---
title: "Command Line install of a python script"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by unibroker on 2012-02-16
I've downloaded a tar and unpacked it from the command line.  The package contains a setup python script that I'm having all sorts of trouble installing.  I've chmod'ed the file to the highest privileges (a+x) but when I go to issue the install command it returns "permission denied".  I follow that by putting a sudo command at the beginning of the line and then it returns no such file or directory.

Ideas?

---

### Post by drmrgd on 2012-02-16
Would you give us an:

```
ls -la
```

of the directory where the python script is?  Also, how are you executing the file?  Like this:

```
./pythonscript.py
```

or like this:

```
python pythonscript.py
```

---

### Post by ajgreeny on 2012-02-16
More details please.

What script are you trying to run?
What exact commands did you use to run it?
Did you actually run it with python, or did you just try the normal "./" from the script's own folder to do that?

---

### Post by unibroker on 2012-02-16
chmod a+x filename

#from that directory
./setup.py install

#Does it need "python" to be invoked before the ./?  

Thanks.  I know enough to be dangerous and destructive.

---

### Post by ajgreeny on 2012-02-16
You do not need the ./ in the command at all, just ```
python scriptname.py
```

---

### Post by unibroker on 2012-02-16
> **ajgreeny said:**
> You do not need the ./ in the command at all, just ```
python scriptname.py
```
Your suggestion returned an error so I added "install".  It ran several processes but finally returned "Permission denied".

chmod a+x gdata-2.0.16
python setup.py install
/usr/local/lib/python2.7/distutils/dist.py:267: UserWarning: Unknown distribution option: 'install_requires'
  warnings.warn(msg)
running install
running build
running build_py
creating build
creating build/lib
creating build/lib/atom
(#many lines of processes)......finally
Removing /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info
error: /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info: Permission denied

I then run tests to see if the script ran properly and they fail.

---

### Post by drmrgd on 2012-02-16
> **unibroker said:**
> Your suggestion returned an error so I added "install".  It ran several processes but finally returned "Permission denied".

chmod a+x gdata-2.0.16
python setup.py install
/usr/local/lib/python2.7/distutils/dist.py:267: UserWarning: Unknown distribution option: 'install_requires'
  warnings.warn(msg)
running install
running build
running build_py
creating build
creating build/lib
creating build/lib/atom
(#many lines of processes)......finally
Removing /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info
error: /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info: Permission denied

I then run tests to see if the script ran properly and they fail.

As you need elevated privileges to alter files in /usr, which the script seems to want to do (remove gdata-2.0.16-py2.7.egg-info), you will probably need to add sudo in front of the script in order to run it. Try:

```
sudo python setup.py install
```

---

### Post by unibroker on 2012-02-16
> **drmrgd said:**
> As you need elevated privileges to alter files in /usr, which the script seems to want to do (remove gdata-2.0.16-py2.7.egg-info), you will probably need to add sudo in front of the script in order to run it. Try:

```
sudo python setup.py install
```
Thanks.  This is what is returned.

/Downloads/gdata-2.0.16$ sudo python setup.py install
/usr/local/lib/python2.7/distutils/dist.py:267: UserWarning: Unknown distribution option: 'install_requires'
  warnings.warn(msg)
running install
running build
running build_py
running install_lib
running install_egg_info
Removing /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info
Writing /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info

---

### Post by drmrgd on 2012-02-17
> **unibroker said:**
> Thanks.  This is what is returned.

/Downloads/gdata-2.0.16$ sudo python setup.py install
/usr/local/lib/python2.7/distutils/dist.py:267: UserWarning: Unknown distribution option: 'install_requires'
  warnings.warn(msg)
running install
running build
running build_py
running install_lib
running install_egg_info
Removing /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info
Writing /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info

So, it looks like it completed with no errors then.  Did it install what you wanted?  Is the problem solved?

---

### Post by unibroker on 2012-02-17
> **drmrgd said:**
> So, it looks like it completed with no errors then.  Did it install what you wanted?  Is the problem solved?
I'm sorry for being unclear.  It did not.  The tests recommended to see if it installed properly failed again.

I'm new to this forum but will mark this (SOLVED) when I either receive a rec that works or find the solution on my own.

---

### Post by ikt on 2012-02-17
Got a link to the script/program? I want to have a play with it :>

---

### Post by unibroker on 2012-02-17
> **ikt said:**
> Got a link to the script/program? I want to have a play with it :>
Here are the instructions I'm following (go to Installing the Google Library)  [http://code.google.com/apis/gdata/articles/python_client_lib.html#library](http://code.google.com/apis/gdata/articles/python_client_lib.html#library)

The problem is I'm a novice in command line use so I probably didn't state the question properly.

---

### Post by drmrgd on 2012-02-17
> **unibroker said:**
> I'm sorry for being unclear.  It did not.  The tests recommended to see if it installed properly failed again.

I'm new to this forum but will mark this (SOLVED) when I either receive a rec that works or find the solution on my own.

No problem.  I just couldn't tell if you got it working or not, since the output you gave didn't report any errors.  

You say that the tests fail.  But, I think it would be informative to actually see the output (in CODE tags please) so that we could troubleshoot.  

I did download and install the script without problem on my computer.  After the initial setup:

```
sudo python setup.py install
```

I got a stream of output that concluded like what you posted.  Looks good.  Then I ran the test they recommend:

```
./tests/run_data_tests.py
```

This took a couple minutes and resulted in a string of tests that all reported OK.  For example:

```
Running all tests in module gdata_tests.webmastertools_test
.............................
----------------------------------------------------------------------
Ran 29 tests in 0.009s

OK
```

How does your output differ?  What errors are you getting?

---

### Post by unibroker on 2012-02-17
> **drmrgd said:**
> No problem.  I just couldn't tell if you got it working or not, since the output you gave didn't report any errors.  

You say that the tests fail.  But, I think it would be informative to actually see the output (in CODE tags please) so that we could troubleshoot.  

I did download and install the script without problem on my computer.  After the initial setup:

```
sudo python setup.py install
```

I got a stream of output that concluded like what you posted.  Looks good.  Then I ran the test they recommend:

```
./tests/run_data_tests.py
```

This took a couple minutes and resulted in a string of tests that all reported OK.  For example:

```
Running all tests in module gdata_tests.webmastertools_test
.............................
----------------------------------------------------------------------
Ran 29 tests in 0.009s

OK
```

How does your output differ?  What errors are you getting?
Have to learn how you post later.  In the interim; the first line and the line before "Traceback" are my input.  The rest is output.


sudo python setup.py install
[sudo] password for **(intentionally edited out)**: 
/usr/local/lib/python2.7/distutils/dist.py:267: UserWarning: Unknown distribution option: 'install_requires'
  warnings.warn(msg)
running install
running build
running build_py
running install_lib
running install_egg_info
Removing /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info
Writing /usr/local/lib/python2.7/site-packages/gdata-2.0.16-py2.7.egg-info
**(intentionally edited out)**:~/Downloads/gdata-2.0.16$ ./tests/run_data_tests.py
Traceback (most recent call last):
  File "./tests/run_data_tests.py", line 9, in <module>
    import gdata_test
  File "/home/**(intentionally edited out)**/Downloads/gdata-2.0.16/tests/gdata_test.py", line 26, in <module>
    import gdata
ImportError: No module named gdata

---

