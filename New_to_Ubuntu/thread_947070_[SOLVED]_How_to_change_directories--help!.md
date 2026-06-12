---
title: "[SOLVED] How to change directories--help!"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by avalenc on 2008-10-13
Hi, there--

I need to md5sum a file, and _in theory_ I know how to do it. In reality, I try to change directories so that I can md5sum the file, and it tells me no such directory. I've tried putting the file in my home folder, and in a folder in the home folder, but I think I'm lacking some basic syntax or something to make it know the exact folder names.

for example, I write cd /desktop/ 
and it gives me the no such file or directory response.

What am I missing?

Thanks!

---

### Post by detroit/zero on 2008-10-13
> **avalenc said:**
> Hi, there--

I need to md5sum a file, and _in theory_ I know how to do it. In reality, I try to change directories so that I can md5sum the file, and it tells me no such directory. I've tried putting the file in my home folder, and in a folder in the home folder, but I think I'm lacking some basic syntax or something to make it know the exact folder names.

for example, I write cd /desktop/ 
and it gives me the no such file or directory response.

What am I missing?

Thanks!
You're missing a ~

[Here's a quick how-to for someone else with much the same question the other day.]("http://ubuntuforums.org/showthread.php?t=945310")

For extended reading, there's always [LinuxCommand.org]("http://linuxcommand.org/").

---

### Post by Muffinabus on 2008-10-13
You're also missing a capitol D, it's case sensitive.

cd ~/Desktop

---

### Post by b0b138 on 2008-10-13
too many /'s and everything is case sensitive.

when you first open a terminal, your prompt should look like user@computer:~$  The ~ indicates your home folder which is at /home/username. If you were to cd ..  that would go up one level to /home and look like user@computer:/home$ One more cd .. would go up another to / and be user@computer:/$ this would be the root of the drive (the equivalent of c: or d: in windows.

So your command cd /desktop/ is really looking for a folder named desktop on the root of the drive (like c:/desktop) which is not there unless you made it. 

From your home folder, user@computer:~$, you can cd Desktop (note the capitol D) and be where everything that is on your desktop is.

---

### Post by avalenc on 2008-10-13
Whew. I'm glad that it was something as minor as a ~ and a capital letter. Thank you!

---

### Post by schauerlich on 2008-10-14
Please mark this thread solved - the option is under Thread Tools. :)

---

