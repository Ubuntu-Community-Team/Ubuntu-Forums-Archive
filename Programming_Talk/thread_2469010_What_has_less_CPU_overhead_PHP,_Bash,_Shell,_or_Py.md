---
title: "What has less CPU overhead? PHP, Bash, Shell, or Python"
date: 2021-11-16
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2021-11-16
Going to be make some scripts that does some string modification and a little basic math can calls a couple shell commands (sensors and qdbus calls) and another that will be reading a pile of files, basic math, and string modifications

these scrips will be running a inf loop with a sleep delay in them

---

### Post by TheFu on 2021-11-17
If the script is running in an endless loop, then it doesn't matter.  Php is seldom used for non-webapps, however.  The question to ask is will the system need to install the interpreter or not?  If the scripts are part of a webapp that is based on php, then you can assume php is already loaded on the system. Otherwise, php isn't there and I would never use the script.

What's the difference, in your mind, between bash and shell?  Shell is a generic term for any of the typical shells on Unix - so bash is shell, but so are zsh, fish, psh, ksh, sh.  If the script needs to run on non-linux servers/desktops, then I wouldn't assume bash is available (similar to php).  Sticking with Borne shell (sh) would be smart, unless the script is very complex and really need functions, which sh doesn't support.

Python is a dependency for most Linux servers and desktops, so it is reasonably safe to assume, but then you need to be worried about older distros having only python2 and newer installs only having python3.  If there is any IPC between systems, now you have to deal with incompatibilities in python2 and 3 communications.  

In general, if that won't be any issue for the next 5 yrs, then I'd choose python3 as my base language from the choices provided. It provides a nice language with every feature needed for simple and complex needs, will likely be pre-installed on any Linux except a uLinux, just went through a major version upgrade in 2020, so that won't happen again for many years.  But if the entire script is under 1 page in length, I'd do it in either bash (linux only) or sh (Unix compatible).  Any shell script over 1 page in length is my cutoff for when I switch to perl.

Is there a reason perl wasn't in your list?

---

### Post by pqwoerituytrueiwoq on 2021-11-17
"Is there a reason perl wasn't in your list?"
was only including languages i know how to use

these script is mainly for personal use so i am not worried about supporting old distros or old kernels that lack support to get the data i am processing

here is a example of one i already started (the generic version i made to share):
[https://github.com/wsdfhjxc/do-it-yourself-bar/files/7556659/kde.diybar.amdgpu.monitor.sh.txt](https://github.com/wsdfhjxc/do-it-yourself-bar/files/7556659/kde.diybar.amdgpu.monitor.sh.txt)
my personal version will have built in overclocking features, probably hard coded in

in the old version of this i was using cat, but i found out read is dramatically faster today

i figured bash would have a little more overhead than shell and have used the policy of does it need bash or does it work in shell

i have a lot of exp with php, so it can be faster for me to get a script done as opposed to using python where i have less exp
example of one of my client side scripts that is used php to generate a bash script: [https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

since this is going to be running at all times i waned to make it as optimized as i can and when you are reading sensor data by the time you can read it the reading has long since changed

---

### Post by TheFu on 2021-11-17
If you want real optimization, use C.  Perl routinely is within a few % of C performance for stuff like this, but obviously would have a higher memory use due to all the interpreter overhead.  Developer-time vs CPU time  is the issue.  When I was a new commercial developer, I remember spending a few hours thinking about optimizing a subroutine and did a slightly more complex solution which was hard to follow and maintain.  A few weeks later, that program was having performance issues, so we hooked up a profiler to see where all the delays were happening.  Turned out the routine I'd optimized was hit maybe once an hour, while there were other routines hit 50x  a second.  

First step was to reduce the number of times the routine was called.
Then doing any optimization wasn't actually needed for the routine.  The next highest delay wasn't called too often, but was just inefficient.  Was able to reduce the time 90% there.
Rinse and repeat for the highest time using routines.

What I learned was to think a little about optimization, but not to actually do anything about it until the profiler proved it was an issue.  Working, safe code, is much more important.  Optimize later, when necessary ... but obviously don't do dumb implementations that waste CPU or RAM. ;)

---

