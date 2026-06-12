---
title: "cx_Freeze: compile() expected string without null bytes"
date: 2010-08-23
forum: Programming Talk
---

### Post by tom66 on 2010-08-23
Trying to cross compile to .exe for a Python script using cx_Freeze, I get this error:

```

running build
running build_exe
copying /usr/lib/pymodules/python2.6/cx_Freeze/bases/Console -> build/exe.linux-x86_64-2.6/main
copying /usr/lib/libpython2.6.so.1.0 -> build/exe.linux-x86_64-2.6/libpython2.6.so.1.0
Traceback (most recent call last):
  File "setup.py", line 7, in <module>
    executables = [Executable("main.py")])
  File "/usr/lib/pymodules/python2.6/cx_Freeze/dist.py", line 278, in setup
    distutils.core.setup(**attrs)
  File "/usr/lib/python2.6/distutils/core.py", line 152, in setup
    dist.run_commands()
  File "/usr/lib/python2.6/distutils/dist.py", line 975, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.6/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.6/distutils/command/build.py", line 135, in run
    self.run_command(cmd_name)
  File "/usr/lib/python2.6/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.6/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/usr/lib/pymodules/python2.6/cx_Freeze/dist.py", line 165, in run
    freezer.Freeze()
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 410, in Freeze
    self.compress, self.copyDependentFiles)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 333, in _WriteModules
    initModule = finder.IncludeFile(initScript, "cx_Freeze__init__")
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 386, in IncludeFile
    deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 259, in _LoadModule
    module.code = compile(fp.read() + "\n", path, "exec")
TypeError: compile() expected string without null bytes

```

Does anyone know what is causing this? None of my files have any null bytes in them.

---

