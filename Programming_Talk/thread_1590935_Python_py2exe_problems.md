---
title: "Python py2exe problems"
date: 2010-10-08
forum: Programming Talk
---

### Post by MiniStephan on 2010-10-08
Hello, all!

I'm trying to create a distributable .exe form of my little python game (it's really simple and only half done, but I want to send it to a few friends to find early bugs), but I'm having a problem with py2exe.  I'm trying to use images for sprites, but when I use py2exe, it doesn't copy it over.

The error is: "Can't copy 'C:\....\MysticRevgame\sprites\crosshairs.png': doesn't exist or not a regular file"

My setup.py is as follows:
[PHP]from distutils.core import setup
import py2exe
import os

Mydata_files = []
for files in os.listdir('C:/censored/for/privacy/MysticRevGame/sprites/'):
    f1 = 'C:/censored/for/privacy/MysticRevGame/sprites/' + files
    if os.path.isfile(f1): # skip directories
        f2 = 'sprites', [f1]
        Mydata_files.append(f2)

setup(
    windows=['MysticRevGame.py'],
    data_files = Mydata_files,
    options={
        "py2exe":{
            "unbuffered": True,
            "optimize": 2,
            "excludes": ["email"]
        }
    }
)
[/PHP]Please help, I've been trying to figure this out for quite a while! I actually have another issue after this, this one only happens intermittently.....

---

