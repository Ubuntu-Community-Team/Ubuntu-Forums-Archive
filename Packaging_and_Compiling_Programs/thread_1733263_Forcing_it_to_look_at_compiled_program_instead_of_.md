---
title: "Forcing it to look at compiled program instead of the one installed from the Repo"
date: 2011-04-19
forum: Packaging and Compiling Programs
---

### Post by excetara2 on 2011-04-19
I am trying to install numpy from source but the one from the repo keeps causing havoc. Can I have it look for the one built from source while still having both of them installed??

How do I do this?

---

### Post by Tclarkie on 2011-04-19
[http://www.scipy.org/Installing_SciPy/Linux](http://www.scipy.org/Installing_SciPy/Linux)
it shouldn't be looking at the reps, can you give further info

---

### Post by excetara2 on 2011-04-19
That was a terrible description of my issue. I had installed numpy completely fine. That is where the first issue was caused. I tried installing scipy from source but it looks in /usr/lib apparently before /usr/local/lib. I assume this is a PATH or PYTHONPATH issue but just ended up removing the python-numpy from the repos because easier. Then the /usr/lib numpy was gone so looked for the one I built in /usr/local/lib. I had updated PYTHONPATH to point to /usr/local/lib before /usr/local but can't remember if this was before or after this. At this point had both of them installed correctly.

Now the issue came with installing mayavi2. The same thing ocurred that it made me reinstall python-numpy from the repos. Then when I started Ipython it would pull up the old numpy. I ended up removing all the repos programs again and downloading the mayavi2 source to install that way which worked fine. I had it all going but was very non-ideal.

Now, I am mainly curious why Ipython or where I can force it to look for /usr/local/lib before /usr/lib. This was nowhere in the ipythonrc settings so I'm not sure where it tells it what packages to load first. I had changed the PYTHONPATH already unless this wasn't done properly. This is where I think it would search first. If it doesn't use PYTHONPATH with Ipython does it just use the regular PATH variable.

Any clear up of the last paragraph would be great. Curious how to set the PYTHONPATH correctly permanently. If it is just export PYTHONPATH=

Thanks,
Jeff

 Would this need to be changed in the PATH variable or I tried in the PYTHONPATH variable with no luck. It definitely does look for it first when running the setup. I can get the scipy to build and run.

---

### Post by excetara2 on 2011-04-19
I think I had the path wrong or something in the PYTHONPATH because I downloaded python-numpy and placed PYTHONPATH to /usr/local/lib in the .bashrc to use the numpy compiled from source. I was smooth sailing this time when this same thing I had done before with no luck.

I am assuming this was my issue also with installing scipy. I think there would have been no hook-ups if this was set as it should have found the right numpy. I am going to test real quick anyway to see if it uses PATH or PYTHONPATH within all the build scripts. They should use PYTHONPATH but I'll double check.

---

### Post by excetara2 on 2011-04-19
Even with the PYTHONPATH set right this is the error I get:

  File "/usr/lib/python2.6/dist-packages/numpy/distutils/misc_util.py", line 835, in get_subpackage
    caller_level = caller_level + 1)
  File "/usr/lib/python2.6/dist-packages/numpy/distutils/misc_util.py", line 782, in _get_configuration_from_setup_py
    config = setup_module.configuration(*args)
  File "scipy/setup.py", line 20, in configuration
    config.add_subpackage('special')
  File "/usr/lib/python2.6/dist-packages/numpy/distutils/misc_util.py", line 852, in add_subpackage
    caller_level = 2)
  File "/usr/lib/python2.6/dist-packages/numpy/distutils/misc_util.py", line 835, in get_subpackage
    caller_level = caller_level + 1)
  File "/usr/lib/python2.6/dist-packages/numpy/distutils/misc_util.py", line 767, in _get_configuration_from_setup_py
    ('.py', 'U', 1))
  File "scipy/special/setup.py", line 14, in <module>
    (numpy.__version__, numpy.__file__))
ValueError: numpy >= 1.4 is required (detected 1.3.0 from /usr/lib/python2.6/dist-packages/numpy/__init__.pyc)

---

