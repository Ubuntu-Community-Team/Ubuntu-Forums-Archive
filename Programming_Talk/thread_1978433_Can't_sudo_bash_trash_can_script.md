---
title: "Can't sudo bash trash can script"
date: 2012-05-11
forum: Programming Talk
---

### Post by jcllings on 2012-05-11
I have a very nice trash can script that I use to reduce the use of rm -rf. It handles names with spaces and also puts things in the trash can correctly so that other programs can still work with them. Problem was that I couldn't figure out how to execute it from sudo which is exactly where you would want to execute it from. 

Imagine: sudo rm -rf a_really_bad_place 
KAPOW!!! We've all done that at least once. ;-)

Turns out the problem was this: You have to add both the /opt/bin directory where the PATH'ed link to the script lives, AND the /opt/scripts directory where the actual script file is to the secure_path in the sudoers file. 

So the line ends up looking like this:

Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt/bin:/opt/scripts"

Like so many things, it makes perfect sense after you've got it sorted. ;-)

---

