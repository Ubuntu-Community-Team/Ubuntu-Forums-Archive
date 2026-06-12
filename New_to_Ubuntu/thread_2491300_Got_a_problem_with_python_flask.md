---
title: "Got a problem with python flask"
date: 2023-10-03
forum: New to Ubuntu
---

### Post by dikh2 on 2023-10-03
Good day.
I'm very new to Ubuntu, so I try to install pip3 flask mysqldb and it ended with error:
```

flowuser@devslax-server:/usr/include/mysql$ pip3 install flask-mysqldb
Defaulting to user installation because normal site-packages is not writeable
Collecting flask-mysqldb
  Using cached Flask-MySQLdb-1.0.1.tar.gz (4.3 kB)
  Preparing metadata (setup.py) ... done
Requirement already satisfied: Flask>=0.12.4 in /usr/local/lib/python3.10/dist-packages (from flask-mysqldb) (2.3.3)
Collecting mysqlclient>=1.3.7 (from flask-mysqldb)
  Using cached mysqlclient-2.2.0.tar.gz (89 kB)
  Installing build dependencies ... done
  Getting requirements to build wheel ... error
  error: subprocess-exited-with-error
  
  × Getting requirements to build wheel did not run successfully.
  &#9474; exit code: 1
  &#9584;&#9472;> [24 lines of output]
      /bin/sh: 1: pkg-config: not found
      /bin/sh: 1: pkg-config: not found
      Trying pkg-config --exists mysqlclient
      Command 'pkg-config --exists mysqlclient' returned non-zero exit status 127.
      Trying pkg-config --exists mariadb
      Command 'pkg-config --exists mariadb' returned non-zero exit status 127.
      Traceback (most recent call last):
        File "/home/flowuser/.local/lib/python3.10/site-packages/pip/_vendor/pyproject_hooks/_in_process/_in_process.py", line 353, in <module>
          main()
        File "/home/flowuser/.local/lib/python3.10/site-packages/pip/_vendor/pyproject_hooks/_in_process/_in_process.py", line 335, in main
          json_out['return_val'] = hook(**hook_input['kwargs'])
        File "/home/flowuser/.local/lib/python3.10/site-packages/pip/_vendor/pyproject_hooks/_in_process/_in_process.py", line 118, in get_requires_for_build_wheel
          return hook(config_settings)
        File "/tmp/pip-build-env-2cnzfwmg/overlay/local/lib/python3.10/dist-packages/setuptools/build_meta.py", line 355, in get_requires_for_build_wheel
          return self._get_build_requires(config_settings, requirements=['wheel'])
        File "/tmp/pip-build-env-2cnzfwmg/overlay/local/lib/python3.10/dist-packages/setuptools/build_meta.py", line 325, in _get_build_requires
          self.run_setup()
        File "/tmp/pip-build-env-2cnzfwmg/overlay/local/lib/python3.10/dist-packages/setuptools/build_meta.py", line 341, in run_setup
          exec(code, locals())
        File "<string>", line 154, in <module>
        File "<string>", line 48, in get_config_posix
        File "<string>", line 27, in find_package_name
      Exception: Can not find valid pkg-config name.
      Specify MYSQLCLIENT_CFLAGS and MYSQLCLIENT_LDFLAGS env vars manually
      [end of output]
  
  note: This error originates from a subprocess, and is likely not a problem with pip.
error: subprocess-exited-with-error


× Getting requirements to build wheel did not run successfully.
&#9474; exit code: 1
&#9584;&#9472;> See above for output.


note: This error originates from a subprocess, and is likely not a problem with pip.



```

Any way to deal with this error? Thanks in advance)

---

### Post by Xian on 2023-10-04
You are likely missing a few compile needed packages. 
Make sure those shown below are installed and then try the build again.

$ sudo apt-get install python3-dev default-libmysqlclient-dev build-essential

---

### Post by dikh2 on 2023-10-04
> **Xian said:**
> You are likely missing a few compile needed packages. 
Make sure those shown below are installed and then try the build again.

$ sudo apt-get install python3-dev default-libmysqlclient-dev build-essential
Thanks for advice, this command works just fine, but I got same replay from "$ pip3 install flask-mysqldb"(

---

### Post by dikh2 on 2023-10-04
No words, maybe some newbies like me will be face same problem - this magic command fix the bag:
 ```
sudo apt install pkg-config
```

---

