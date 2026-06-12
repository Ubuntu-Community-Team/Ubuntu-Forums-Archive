---
title: "cmd to know the size of file,directory"
date: 2011-01-26
forum: Programming Talk
---

### Post by scott_tiger on 2011-01-26
wat is d cmd to know size of file/directory?

how could i see my beans i posted at a glance , as many times i forget to which community i posted my THREAD on ubuntuforum.?

---

### Post by khamil8686 on 2011-01-26
the bash command to show you the size of a directory would be ls -lh and it will show how how big the files and directories are in your current working directory, you can see your beans by clicking Quick Links, then Your Profile, then click the statistics tab and it will list how many posts you have

---

### Post by slavik on 2011-01-26
du will tell you the cumulative size of all files in a directory.

---

### Post by Arndt on 2011-01-26
> **scott_tiger said:**
> wat is d cmd to know size of file/directory?

how could i see my beans i posted at a glance , as many times i forget to which community i posted my THREAD on ubuntuforum.?

Under the Search menu at the top here, you have Find All Your Posts.

You can also choose to subscribe to threads that you start, and then you can easily see whether there are any new answers: In User CP (also at the top of the page here), you have Edit Options, and there you can set Default Thread Subscription Mode.

After that, when you go to User CP, new messages in your subscribed threads will be listed.


Unless "du" which was suggested does what you want: what do you mean by the size of a directory? The number of files? The actual size taken by the directory as a file?

You can see the size of a file with "ls -l", "ls -s" or "wc".

Note that files can have holes in them, so they take less actual space on disk than some measures of their size suggest.

---

