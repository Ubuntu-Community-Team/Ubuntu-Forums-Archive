---
title: "How to start terminal with script in ubuntu"
date: 2009-12-25
forum: Programming Talk
---

### Post by xZachtmx on 2009-12-25
I am looking to make a really easy to use gui from C++ in Qdevelop.  I have a little push button i want to open a terminal and automaticly run a shell script.  I know i have to use the system() function but what do i type after system("gnome-terminal    to make it run the script in the terminal.  i need to run the script IN the terminal because it needs the user's password to gain root acess.  any suggestions are welcomed.

Thanks,
Zach

---

### Post by ksa618 on 2009-12-25
gnome-terminal -e <command>
This will close the terminal when the command exits

---

