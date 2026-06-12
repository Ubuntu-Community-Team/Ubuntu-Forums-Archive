---
title: "Virtualenv (python) in Ubuntu on external hard drive"
date: 2016-08-09
forum: Programming Talk
---

### Post by Nebelhom on 2016-08-09
Hi folks,

I am not 100% sure this is the right forum, but it is the closest that I could find to my problem. If a mod feels that it should be moved to a more fitting place please do so. Thank you!

I am trying to create a virtualenv on my external hard drive that I use for both my Ubuntu and my Windows installation (I have a SSD and use 2TB external hard drive for anything but PC games).

When I navigate to the place and try to create it with the commands that work on the Ubuntu drives, I get the following:

```
nebelhom@nebelhom-desktop:/media/extHDD/virt_folder$ virtualenv MyFolder
New python executable in /media/nebelhom/extHDD/virt_folder/MyFolder/bin/python
ERROR: The executable /media/nebelhom/extHDD/virt_folder/MyFolder/bin/python could not be run: [Errno 13] Permission denied
```

Running the same with "sudo" did not help either and gave the same error as above.

What I tried next is indicating the python version

```
nebelhom@nebelhom-desktop:/media/nebelhom/extHDD/virt_folder$ sudo virtualenv -p python2.7 MyFolder
Running virtualenv with interpreter /usr/bin/python2.7
New python executable in /media/nebelhom/extHDD/virt_folder/MyFolder/bin/python2.7
Not overwriting existing python script /media/nebelhom/extHDD/virt_folder/MyFolder/bin/python (you must use /media/nebelhom/extHDD/virt_folder/MyFolder/bin/python2.7)
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/virtualenv.py", line 2332, in <module>
    main()
  File "/usr/local/lib/python2.7/dist-packages/virtualenv.py", line 711, in main
    symlink=options.symlink)
  File "/usr/local/lib/python2.7/dist-packages/virtualenv.py", line 924, in create_environment
    site_packages=site_packages, clear=clear, symlink=symlink))
  File "/usr/local/lib/python2.7/dist-packages/virtualenv.py", line 1369, in install_python
    os.symlink(py_executable_base, full_pth)
OSError: [Errno 17] File exists
```

And now I am stuck :/ . Has anyone of you tried something like this before and succeeded?

Thanks :)

P.S. I am using Ubuntu 14.04 LTS

---

### Post by nargaroth_reg on 2016-08-15
Hello, perhaps it is a permissions problem? I would try setting the local user as owner of the /virt_folder/ directory and allowing execution of files first.

---

