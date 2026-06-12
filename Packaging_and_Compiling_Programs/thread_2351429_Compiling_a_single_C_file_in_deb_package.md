---
title: "Compiling a single C file in deb package"
date: 2017-02-03
forum: Packaging and Compiling Programs
---

### Post by luvshines on 2017-02-03
Hi all

I am stuck in tricky situation. Have been working with RPM building from source, but now have to build a deb package for Ubuntu server 16.04

**The source primarily contains python code. However there is a singular C code which produces a binary, when compiled, and installs it in /usr/bin**

I used following to build my RPM
```
python setup.py bdist_rpm
```
The setup.py has following code to build C code
```
[COLOR=#101094][FONT=Consolas]try[/FONT][/COLOR][COLOR=#303336][FONT=Consolas]:
[/FONT][/COLOR][COLOR=#303336]    compiler [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#2B91AF]UnixCCompiler[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]verbose[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#7D2727]1[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336]
    compiler[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]compile[/COLOR][COLOR=#303336]([[/COLOR][COLOR=#7D2727]'cutility/chown_sudo.c'[/COLOR][COLOR=#303336]])[/COLOR][COLOR=#303336]
    compiler[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]link_executable[/COLOR][COLOR=#303336](([[/COLOR][COLOR=#7D2727]'cutility/chown_sudo.o'[/COLOR][COLOR=#303336]]),[/COLOR][COLOR=#7D2727]'bin/sudoown'[/COLOR][COLOR=#303336])[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#101094]except[/COLOR][COLOR=#2B91AF]CompileError[/COLOR][COLOR=#101094]as[/COLOR][COLOR=#303336] compileError[/COLOR][COLOR=#303336]:[/COLOR][COLOR=#303336]
    [/COLOR][COLOR=#101094]print[/COLOR][COLOR=#7D2727]"Failed to compile the binary file."
[/COLOR]    raise
```[COLOR=#222222][FONT=Verdana]
How to accommodate this compilation in a deb package ?

I am trying 'bdist_deb' from stdeb package but that ignores this piece of code from setup.py[/FONT][/COLOR]

---

### Post by luvshines on 2017-02-07
Ah !! Found the issue

The piece of code I posted above was within a if...else which was checking startswith('bdist'), only then executing the code

The bdist_deb calls the script as 'build'. So simply added an OR statement startswith('build') which resolved it. Now moving further :)

---

