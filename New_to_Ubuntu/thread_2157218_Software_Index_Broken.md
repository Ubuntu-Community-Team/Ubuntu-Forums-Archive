---
title: "Software Index Broken"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by sixsamuraisoldier on 2013-06-24
Whenever I try to use chrome or firefox, it doesnt open. Now, I know you're going to say use sudo apt-get update and sudo apt-get install -f , but they don't work.

---

### Post by Cheesehead on 2013-06-24
Try opening applications in a terminal window. Paste the complete error message here.

If apt is not working, that's a separate problem. Post a complete failed session, including all output, here.

---

### Post by sixsamuraisoldier on 2013-06-24
> **Cheesehead said:**
> Try opening applications in a terminal window. Paste the complete error message here.

If apt is not working, that's a separate problem. Post a complete failed session, including all output, here.

When opening in terminal:
~/Desktop $

When apt-get update:
E: Type 'https://launchpad.net/~s-elser/+archive/winelol' is not known on line 1 in source list /etc/apt/sources.list.d/additional-repositories.list
E: The list of sources could not be read.

When sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

PLEASE help :(

---

### Post by MidnightGrey on 2013-06-24
Well your apt-get is working properly.
What happens when you type 
```
firefox
```
or 
```
chrome
```
in the terminal?

---

### Post by sixsamuraisoldier on 2013-06-25
when firefox:
(process:9630): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed

 when chrome:
chrome: command not found
PLEASE help, im getting distressed, i NEED chrome

---

### Post by MidnightGrey on 2013-06-25
edit: my bad i dont really use chrome so i didnt know it's CLI name.

look at monkeybrain's post.

---

### Post by MidnightGrey on 2013-06-25
And what Ubuntu are you running?

---

### Post by monkeybrain2012 on 2013-06-25
> when chrome:
chrome: command not found
PLEASE help, im getting distressed, i NEED chrome                 .


The command to start chrome is 
```
google-chrome
```

---

### Post by claracc on 2013-06-25
> **sixsamuraisoldier said:**
> When opening in terminal:
~/Desktop $

When apt-get update:
E: Type 'https://launchpad.net/~s-elser/+archive/winelol' is not known on line 1 in source list /etc/apt/sources.list.d/additional-repositories.list
E: The list of sources could not be read.

When sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

PLEASE help :(

About the sources.list.d/additional-repositories.list file error you have to edit it and see the first line (as indicated in error message),  it cannot start by https directly but it has to have a deb before.

Please post your additional-repositories.list file in order to fix the error in line 1

---

### Post by sixsamuraisoldier on 2013-06-25
when: google-chrome
[11148:11148:0625/081305:ERROR:process_singleton_linux.cc(239)] readlink(/home/sixsamuraisoldier/.config/google-chrome/SingletonLock) failed: Invalid argument
[11148:11148:0625/081305:ERROR:process_singleton_linux.cc(239)] readlink(/home/sixsamuraisoldier/.config/google-chrome/SingletonLock) failed: Invalid argument
[11148:11148:0625/081305:ERROR:process_singleton_linux.cc(263)] Failed to create /home/sixsamuraisoldier/.config/google-chrome/SingletonLock: File exists
[11148:11148:0625/081305:ERROR:process_singleton_linux.cc(239)] readlink(/home/sixsamuraisoldier/.config/google-chrome/SingletonLock) failed: Invalid argument
[11148:11148:0625/081305:ERROR:chrome_browser_main.cc(1195)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

---

### Post by Cheesehead on 2013-06-25
> **sixsamuraisoldier said:**
> [11148:11148:0625/081305:ERROR:chrome_browser_main.cc(1195)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

That means chrome is already running.
Kill the chrome process, then try again.

Here is an example of how to kill a running process. Use it carefully and sparingly, only if you cannot find the chrome window.

```
me@mysystem:~$ ps -e | grep chrome
 4473 ?        01:33:36 google-chrome
me@mysystem:~$ kill 4473
me@mysystem:~$ 
```

---

### Post by sixsamuraisoldier on 2013-06-26
is it me@mysystem or sixsamuraisoldier@sixsamuraisoldier'ssystem?

---

### Post by newb85 on 2013-06-26
Only enter the commands after the $.

---

### Post by sixsamuraisoldier on 2013-06-26
wait, but 
do i type in EXACTLY me@mysystem 
and do they go ALL in one line or each line is an enter after it

---

### Post by sixsamuraisoldier on 2013-06-26
heres what i get:
sixsamuraisoldier@sixsamuraisoldier-HP-Pavilion-dv6-Notebook-PC ~ $ me@mysystem:~$ ps -e | grep chrome
WARNING:root:could not open file '/etc/apt/sources.list'

me@mysystem:~$: command not found
sixsamuraisoldier@sixsamuraisoldier-HP-Pavilion-dv6-Notebook-PC ~ $  4473 ?        01:33:36 google-chrome
WARNING:root:could not open file '/etc/apt/sources.list'

4473: command not found
sixsamuraisoldier@sixsamuraisoldier-HP-Pavilion-dv6-Notebook-PC ~ $ me@mysystem:~$ kill 4473
WARNING:root:could not open file '/etc/apt/sources.list'

me@mysystem:~$: command not found

---

### Post by newb85 on 2013-06-26
Do not enter the $. Do not enter me@mysystem or whatever your username and system names are. The terminal should display all that as part of the prompt. Enter the commands one line at a time.

Oh, and the second line of cheesehead's example is the output of the first line. It provides you with t the process number you need for the kill command

---

### Post by sixsamuraisoldier on 2013-06-27
somethings going on:
sixsamuraisoldier@sixsamuraisoldier-HP-Pavilion-dv6-Notebook-PC ~ $ ps -e | grep chrome
sixsamuraisoldier@sixsamuraisoldier-HP-Pavilion-dv6-Notebook-PC ~ $

---

### Post by sixsamuraisoldier on 2013-06-28
guys,please PLEASE HELP :((((((

---

### Post by newb85 on 2013-06-28
The fact that the ps command didn't return any entries containing "chrome" indicates that chrome is not running.

This is probably a dumb question, but you *are* trying to run chrome, not chromium, right?

---

### Post by sixsamuraisoldier on 2013-06-29
yes im trying to run CHROME , NOT chromium....

---

### Post by artur2 on 2013-07-31
Issues is simply to solve.

Propably you get previously some CHROMIUM crash and it inproperly exit.  Then some sym-links are incorrect (if you make listing in this  directory, you will get some bad sym-links). For example:
--------------
lrwxrwxrwx 1 *** ***      19 mar 10 10:56 SingletonCookie -> 2297198313226873933
-rw------- 1 *** ***   16890 mar 10 12:05 SingletonLock
lrwxrwxrwx 1 *** ***      50 mar 10 10:56 SingletonSocket -> /tmp/.org.chromium.Chromium.WXn8Io/SingletonSocket
--------------

In part of message, you has given path to directory.
Fallow it in terminal. 

Then remove SingleTone files which cause that issue.

/.config/chromium$ rm SingletonS*
/.config/chromium$ rm SingletonC*
/.config/chromium$ rm SingletonLock 

Have a nice usage of chromium ;)

---

### Post by newb85 on 2013-08-01
First, I don't know why this hasn't been mentioned earlier, but the issue at hand is separate from the one indicated in the thread title, and should have been given it's own thread.

artur2 may be on to something, but since the OP is trying to use Chrome, not Chromium, the commands would be

```
cd .config/google-chrome
rm SingletonS*
rm SingletonC*
rm SingletonLock
```

(And please use code tags, per the Code of Conduct.)

---

