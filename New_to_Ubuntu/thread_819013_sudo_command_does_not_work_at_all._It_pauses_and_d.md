---
title: "sudo command does not work at all. It pauses and doesn't do anything."
date: 2008-06-05
forum: New to Ubuntu
---

### Post by ClickerMonkey on 2008-06-05
I just installed Ubuntu Hardy on my old desktop tonight for the second time to fix problems with graphics performance. The graphics performance problem has been fix because of the reinstall but all of a sudden I can't do any root commands. After the install sudo commands worked perfectly fine and I don't recollect do anything that would of affected this. I can't do anything along the lines of 'sudo *' where * is any command.. it will just return to the next line in the terminal and blink while not doing anything. 

This is also causing several other problems I presume with administrative applications. I can't start them, it doesn't even prompt me on the screen for a password, It will show a tab on my task bar with 'Starting Administrative Application' and after a minute it will disappear. 

I'm also assuming since It won't grant me root privileges my update manager is not working correctly. Since its a new install it prompts for about 120mb of things. Ive trimmed it down to only the essentials but when I hit 'Install Updates' the update manager screen goes gray (not a 'Not Responding' gray) just a working gray.. then it tries to launch another admin app and it once again closes with the update manager still grayed. Nothing is responding to anything! I'm new to ubuntu and linux so don't be afraid to overly explain things to me..

Thanks, 

Phil

---

### Post by dppowell on 2008-06-05
Phil, take a look at this archived thread and see if the suggestion a few posts down is helpful:

[http://ubuntuforums.org/archive/index.php/t-146859.html](http://ubuntuforums.org/archive/index.php/t-146859.html)

Dave

---

### Post by ClickerMonkey on 2008-06-05
Thanks for the reply, however I've tried all of those routes...

The group admin for me does exist. However to add a user you need to have root privileges.

The problem for me is different, it doesn't even prompt for a password it doesn't respond to any command (not even ctrl+c) after I hit return after I type in any command using 'sudo'

I can't even view the sudoers file without root access.

Thanks, any other input would be greatly appreciated!

---

### Post by spiderbatdad on 2008-06-05
what does the command "id" return?

---

