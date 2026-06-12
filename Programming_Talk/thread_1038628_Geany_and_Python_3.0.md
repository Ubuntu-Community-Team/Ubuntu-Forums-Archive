---
title: "Geany and Python 3.0?"
date: 2009-01-13
forum: Programming Talk
---

### Post by babanner on 2009-01-13
Could you please tell me how to configure Geany to execute my python scripts with Python 3.0, rather than with the default Python 2.5.2 ? It seems i should change something in Preferences->Terminal, but i don't know what.
Thanks in advance.

---

### Post by NoBugs! on 2009-01-13
I don't know exactly, but I think it has to do with how the templates are set up. Templates for geany IDE are in home directory/.geany/templates folder.

---

### Post by garyczek on 2009-01-14
Hi, in /usr/local/share/geany/filetypes.python are saved build settings in part [build_settings]. There you can change what command will be executed.
Firstly read ~/.config/geany/filedefs/filetypes.README (OR maybe ~/.geany/filedefs/filetypes.README). Sou you should copy filetypes.python to geany's config. And then make some changes in it.
I recommend you to copy filetype_extensions.conf, filetypes.python to filetypes.python2 and to filetypes.python3 if the version could be determined by the file extension. And then set all values as needed.

Another solution:
Did you tried Edit -> Preferences -> Tools and in the Make line (or whatever) put '/usr/bin/python3 "%f" #' (I'm not sure about the path to python 3.0 binary) (do not forget # at the end)? And then to execute script press F8 (for Make line). It's not the prettiest way, but I think it will do what you  want.

---

### Post by MockY on 2009-01-14
I don't have the /usr/local/share/geany/ directory. 
And putting /usr/bin/python3.0 "%f" # in the make field did not change anything.

---

### Post by MockY on 2009-01-15
This worked for me:

replace the last 2 lines in /usr/share/geany/filetypes.python (it is **NOT** located in the /local folder) with this:
```
compiler=python3.0 -c "import py_compile; py_compile.compile('%f')"
run_cmd=python3.0 "%f"
```

---

### Post by C0pac3t1c on 2009-01-20
Thanks everyone. I was looking for a way to do this...

---

### Post by mityay on 2009-01-28
After I installed python 3.0, how can I remove python 2.5 without removing all the dependencies? Thanks

---

### Post by MockY on 2009-02-04
I don't suggest that you do since a huge amount of packages are written (as far as I understand) in python 2.* and you would most likely bork your install. I would wait until Ubuntu supports it out of the box.

---

### Post by mahela007 on 2009-02-26
> **MockY said:**
> This worked for me:

replace the last 2 lines in /usr/share/geany/filetypes.python (it is **NOT** located in the /local folder) with this:
```
compiler=python3.0 -c "import py_compile; py_compile.compile('%f')"
run_cmd=python3.0 "%f"
```

I'm havin the same problem
However I can't modify the file because it when I modify it and try to save it I get a message saying it isn't possible to save the file. I use kubuntu

---

### Post by cyfur01 on 2009-02-26
> However I can't modify the file because it when I modify it and try to save it I get a message saying it isn't possible to save the file.
Since this is in the /usr folder, you'll have to be root when editing the file. Thus, I recommend you use konsole to run "sudo kate /usr/share/geany/filetypes.python" (or replace kate with your preferred text editor).

---

### Post by mahela007 on 2009-02-26
but now I get this ugly red error (after I have saved the file and attempted to run another program in geany) in the command line window
```
Warning: Could not start program './geany_run_script.sh' with arguments './geany_run_script.sh'.

```

---

### Post by cyfur01 on 2009-02-26
What version of Geany are you running? 

The script should be created in the same directory as the python script you are trying to run. Can you verify that there is a geany_run_script.sh there? What are the ownership/permissions of the script? If all else fails, you should be able to delete the script, and have Geany auto-generate it the next time you try to run the script (providing of course that you have write access to the directory).

There was some talk of adding an option to bypass this script [here]("https://lists.uvena.de/pipermail/geany/2007-December/002379.html"), which appears to be present in Geany 0.14 (Edit->Preferences->Terminal, Check "Execute Programs in VTE" and "Don't Use Run Script"). This will launch it in the terminal embedded in the geany window.

---

