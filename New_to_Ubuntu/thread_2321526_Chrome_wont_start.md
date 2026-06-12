---
title: "Chrome wont start"
date: 2016-04-22
forum: New to Ubuntu
---

### Post by bryce5 on 2016-04-22
Hello i just upgraded to the new 16.0.4 ubuntu. I tried to install google chrome but it wouldnt work and finally got the terminal to install it. Now when i  try to open it, it just gives me this in the command line which im not sure what todo.

google-chrome
[12991:12991:0422/173339:ERROR:process_singleton_posix.cc(270)] Failed to create /home/bryce/.config/google-chrome/SingletonLock: File exists
[12991:12991:0422/173339:ERROR:chrome_browser_main.cc(1379)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

---

### Post by tripp98 on 2016-04-22
it could be a few things.

open terminal
killall chrome [enter]   - that will kill chrome if its running
the try to start it again

if you receive the same message
in terminal 
cd .config/google-chrome [ enter]
mv SingletonLock SingletonLock-old  - will rename the lock file.

if it reoccures after that.  uninstall google-chrome
remove the .config/google-chrome folder
then reinstall google-chrome

---

### Post by bryce5 on 2016-04-22
Thank you very much, It did open. It says your profile could not be correctly opened. Some features are unavailable..Please Check that the profile exists and you have premission to read and write its contents. Do you know how to get rid of that message?

---

### Post by tripp98 on 2016-04-22
[COLOR=#000000]in terminal [/COLOR]
[COLOR=#000000]cd .config/google-chrome [ enter]

ls -all     - this will give you a directory listing and the owner of the files.  see if your user"[/COLOR][COLOR=#000000]bryce"[/COLOR][COLOR=#000000] is the owner on the left 
if it is root then you ran chrome as sudo chrome and root is the owner, thus you dont have rights.


if its root then make sure you are out of chrome
cd .config [enter]
sudo rm -r google-chrome       - this will delete the profile folder.  it will be recreated when you open chrome next time.


[/COLOR]

---

### Post by bryce5 on 2016-04-22
Thank you, I'm not sure exactly what you mean but they said bryce on the left. So i did the cd .config and deleted it. It seems to work good now. Thanks alot :D

Is there anyway to say its solved?

---

### Post by deadflowr on 2016-04-22
> **bryce5 said:**
> Is there anyway to say its solved?
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

