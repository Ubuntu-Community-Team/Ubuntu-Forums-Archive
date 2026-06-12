---
title: "Error: ndk-build: command not found"
date: 2015-11-17
forum: Programming Talk
---

### Post by Omer_Danish on 2015-11-17
I want to build an example in NDK here is the link: [http://odroid.com/dokuwiki/doku.php?id=en:c1_enhancement_gpio40_on_android](http://odroid.com/dokuwiki/doku.php?id=en:c1_enhancement_gpio40_on_android)
I have downloaded and extracted latest NDK

It asks to do this
[B] Insert this line into your ~/.bashrc file. 
[/B]

**export NDK_PATH=/home/xxx/android-ndk-r10d**
when I try to use the ndk-build command it shows error
[B]ndk-build: command not found

[/B]NDK and the WiringPi example Folders are in the Downloads Directory /home/omer/Downloads

What should I do???

---

### Post by ian-weisser on 2015-11-18
Does the export path match the actual path to NDK?
Or did you really export "/home/xxx/"? (which leads to the non-existent user 'xxx')

---

### Post by Rocket2DMn on 2015-11-20
After you make changes to your .bashrc file, you must source it for the changes to take effect in your current session.
```

source ~/.bashrc

```
Alternatively, open a new terminal (or log out and back in if you're in a TTY).

---

