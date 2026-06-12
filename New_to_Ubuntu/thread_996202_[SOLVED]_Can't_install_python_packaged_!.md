---
title: "[SOLVED] Can't install python packaged ?!"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by drsyntax on 2008-11-28
Hello,
i am a totally new user to python and linux, and i wanted to install pyParallel package as i need to make a program using python that uses parallel port for I/O , but when i try to install it i am getting this error : ( iam using the ubuntu 8.10 desktop version live cd )

```
ubuntu@ubuntu:~/Desktop/pyparallel-0.2$ sudo python setup.py install
running install
running build
running build_py
Traceback (most recent call last):
  File "setup.py", line 19, in <module>
    package_data = data_files
  File "/usr/lib/python2.5/distutils/core.py", line 151, in setup
    dist.run_commands()
  File "/usr/lib/python2.5/distutils/dist.py", line 974, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.5/distutils/dist.py", line 994, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.5/distutils/command/install.py", line 506, in run
    self.run_command('build')
  File "/usr/lib/python2.5/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.5/distutils/dist.py", line 994, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.5/distutils/command/build.py", line 113, in run
    self.run_command(cmd_name)
  File "/usr/lib/python2.5/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.5/distutils/dist.py", line 993, in run_command
    cmd_obj.ensure_finalized()
  File "/usr/lib/python2.5/distutils/cmd.py", line 117, in ensure_finalized
    self.finalize_options()
  File "/usr/lib/python2.5/distutils/command/build_py.py", line 60, in finalize_options
    self.data_files = self.get_data_files()
  File "/usr/lib/python2.5/distutils/command/build_py.py", line 123, in get_data_files
    file[plen:] for file in self.find_data_files(package, src_dir)
  File "/usr/lib/python2.5/distutils/command/build_py.py", line 130, in find_data_files
    globs = (self.package_data.get('', [])
AttributeError: 'NoneType' object has no attribute 'get'

```

Any one can figure out what is the problem ?!

Thank you,
Tamer

---

### Post by unutbu on 2008-11-28
There is a package in the official repositories call python-parallel ([http://packages.ubuntu.com/intrepid/python-parallel](http://packages.ubuntu.com/intrepid/python-parallel))

The version number of the package is 0.2, which looks to be the same version that you are trying to install manually. 

Therefore, I believe the easiest way to install pyparallel would be 
```

sudo apt-get install python-parallel
```

---

### Post by drsyntax on 2008-11-28
> **unutbu said:**
> There is a package in the official repositories call python-parallel ([http://packages.ubuntu.com/intrepid/python-parallel](http://packages.ubuntu.com/intrepid/python-parallel))

The version number of the package is 0.2, which looks to be the same version that you are trying to install manually. 

Therefore, I believe the easiest way to install pyparallel would be 
```

sudo apt-get install python-parallel
```

thanks for your help, it works now.

---

