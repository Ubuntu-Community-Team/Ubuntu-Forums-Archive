---
title: "problem with ADB commands"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by charitosha on 2014-04-05
Hello everyone!):P
I have a small problem with using adb commands....
i have done all the steps from: [http://askubuntu.com/questions/318246/complete-installation-guide-for-android-sdk-adt-bundle-on-ubuntu](http://askubuntu.com/questions/318246/complete-installation-guide-for-android-sdk-adt-bundle-on-ubuntu)
at **step5** where i have to open gedit and write the paths, i saved that file in the sdk folder don't know whether i had to saved it elsewhere
(i cannot see the .pam_enviroment file, unless i open gedit and see that i actually saved it there -actually why this happens?)
so i wanted to check i did everything  correctly so i typed the command: adb version just to check and i got adb:command not found.
Can somebody give me a suggestion on what to do? #-o

---

### Post by mcduck on 2014-04-05
you need to save the file in your home directory. (the command they give you tells you to edit "~/.pam_environment", the "~/" part in the path is your home.)

Also any file with the name starting with a "." is a hidden file, you can toggle displaying hidden files in your file browser buy presshig Ctrl+H.

---

### Post by charitosha on 2014-04-05
mcduck, thank you for your reply,
so i did save it in the home directory, i can see it if i type ls -a, so that is ok.
i also have downloaded the jdk but i still can't use adb commands... 
why is that???

---

### Post by sikander3786 on 2014-04-05
If all you want to do is to run "adb" commands, you just need to install "android-tools-adb" package:

```
sudo apt-get install android-tools-adb
```

---

### Post by charitosha on 2014-04-06
Ok i don't understand something.
From Android SDK Manager i installed all the tool/build-tools/platform-tools under the Toolls forlder but still i couldn't use the adb commands.
when i typed: sudo apt-get install android-tools-adb, as sikander said, i was able to use the adb commands.
but now i'm affraid that i still cannot use commands from other usefull tool, i guess i have to load them manually...

So can somebody tell me how can install other tools e.g. when i tried to use am (activity manager) commands - i got that am: command not found. So i typed sudo apt-get install android-tools-am (am for activity manager) i got the respond that it was unable to locate the package.

---

### Post by mcduck on 2014-04-06
Make sure your .pam_environment file really has the correct full path to where you extracted the tools package.

It's quite easy to test, if you can execute any of the tools from any directory, using the full path, then the path is correct.

(also you probably should be using ~/.profile instead of ~/.pam_environment, .profile works more or less the same way but is never overwritten by any other system so it's a better place for your own configurations and things...)

---

### Post by charitosha on 2014-04-06
Both of the paths start from the home directory and both of them are correct. Also the .pam_environment is saved into the user(under home folder) folder.
So i don't really know what's wrong and i was wondering if it's possible to download via the terminal all the other tools that i might need, with the apt-get install. But i don't know how to call them because all the time i get the respond that it was unable to locate the package...

p.s. i don't understand why i have this issue because in the Android SDK Manager i installed all the tool/build-tools/platform-tools under the Tools forlder

---

### Post by mcduck on 2014-04-06
well, there's your problem, the paths need to be *full paths* (starting from the root of the filesystem, /), not from your home directory.

---

### Post by charitosha on 2014-04-06
excuse me, but correct me if i'm wrong.
isn't the following the full path to a folder : /home/haris/adt_bundle/adt-bundle-linux-x86-20140321/sdk/tools

---

### Post by mcduck on 2014-04-06
yes, that's a full path. I was confused since you said you had a path "starting from home".

Anyway, can you run the tools using that full path in your command? If not, make sure the files have execute permission.

I still recommend using the ~/.profile file instead of ~/.pam_environment, and in either case you might have to log out and back again before the changes in the file take effect.

---

### Post by charitosha on 2014-04-06
ok i deleted and wrote again .pam_environment with the full paths, i didn't want to use the .profile because it already existed and it had some code in it.
anyway after i rewrote it the adb commands work just fine! 
thx for the help!

---

