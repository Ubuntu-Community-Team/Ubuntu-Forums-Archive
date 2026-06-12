---
title: "Couldn't initialize the &lt;update manger&gt; package"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by theone1111 on 2011-12-21
My system's Ubuntu 11.10  worked with no problems since installation a month ago . Now I am not able to utilize "Update Manager" application, possibly being a bug. The error message shown as: 'E:Malformed line 57 in source list /etc/apt/sources.list (URI parse)'
I tried report this bug (if this is really a bug) using terminal "ubuntu-bug update manager" command, I also notice that I am not able to open "Ubuntu Software Center" application afterwards, nothing happens when I click it's icon. All my other applications are working very nicely . I appreciate any help in advance.

---

### Post by heyandy889 on 2011-12-21
Hi, theone1111. I Googled "11.10 E:Malformed line 57 in source list /etc/apt/sources.list (URI parse)", sorted by "past year," and came up with the following forum thread:

[http://www.linuxquestions.org/questions/linux-software-2/serious-problem-with-sources-list-what-to-do-915948/](http://www.linuxquestions.org/questions/linux-software-2/serious-problem-with-sources-list-what-to-do-915948/) 

Take a look at that thread, and see if any of the posts address your problem. Welcome to the forums!

---

### Post by oldos2er on 2011-12-21
> **theone1111 said:**
> I appreciate any help in advance.

Can you run **cat /etc/apt/sources.list** in a terminal and post the output here?

---

### Post by theone1111 on 2011-12-21
Thank you all for your help, It is really great to be a member of this forum family.
I was able to solve the problem after many trials. The cause of the problem was in installation one of the application from third party. So, by opening and removing  System > Software Sources >Other Software> lucid partner, both the Update Manager and Ubuntu Software Center come to life.
With my best regard
-Fred

---

