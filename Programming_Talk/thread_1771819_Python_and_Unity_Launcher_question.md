---
title: "Python and Unity Launcher question"
date: 2011-05-30
forum: Programming Talk
---

### Post by huahe on 2011-05-30
Hello.

I am a newbie programming Python.

I am trying to develop a Thunderbird extension that takes advantage of the new Unity Launcher for showing the unread count. I checked that there is already one, but it is only for Thunderbird 3.3 Alpha.

The extensions I am developing works in the following way:

- There is a javascript program, that checks for the new messages count. This works flawlessly
- If there were new messages, I execute a Python script that use the Unity api for showing the unread count (I modified this script to do so: [https://wiki.ubuntu.com/Unity/LauncherAPI#Python Example](https://wiki.ubuntu.com/Unity/LauncherAPI#Python Example))

This script works, but when I try to close Thunderbird, it freezes (I think that is because the loop in the python keeps running). The other solution would be not having a loop, but as soon as the script dies, the unread count dissapears. 

What can I do ? Any ideas ?

Thanks.

---

### Post by hakermania on 2011-05-31
I underline that I know NOTHING about javascript and python as well..

But, i'd say the obvious thing i'd done if i was programming in bash, execute the python script with a &
I mean, i don't know do you execute the python script, but if it is from a function that sends commands to the system, you could modify it to
```
system("/path/to/the/python/executable*_**&**_*")
```Notice the '&'

this will run the executable without appending to it, it will let it run, simply


Another solution would be not to use a loop for this, but a timer, i mean, go through a function every X minutes, this is possible in C++, i don't know about javascript

---

