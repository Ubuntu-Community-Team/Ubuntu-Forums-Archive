---
title: "Error Installing Flexget"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by murbancic on 2013-07-05
[FONT=Arial]I was getting an error while trying to upgrade Flexget. I atempted to uninstall the program and reinstall and am still getting an error. Below is the output I get when trying to install.

[/FONT]```
root@openmediavault:~# pip install flexgetDownloading/unpacking flexget
  Running setup.py egg_info for package flexget
    /usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'install_requires'
      warnings.warn(msg)
    /usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'zip_safe'
      warnings.warn(msg)
    /usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'test_suite'
      warnings.warn(msg)
    /usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'entry_points'
      warnings.warn(msg)
    /usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'extras_require'
      warnings.warn(msg)
    Build failed: Unknown task: egg_info
    Complete output from command python setup.py egg_info:
    /usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'install_requires'


  warnings.warn(msg)


/usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'zip_safe'


  warnings.warn(msg)


/usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'test_suite'


  warnings.warn(msg)


/usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'entry_points'


  warnings.warn(msg)


/usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'extras_require'


  warnings.warn(msg)


Build failed: Unknown task: egg_info


----------------------------------------
Command python setup.py egg_info failed with error code 1

Storing complete log in /root/.pip/pip.log

```

[FONT=Arial]Any ideas on how to fix this? I am completely lost.[/FONT]

---

### Post by Rolandmaffia on 2013-07-06
Confirmed, and reported as a Flexget issue: [https://github.com/Flexget/Flexget/issues/61](https://github.com/Flexget/Flexget/issues/61)

---

