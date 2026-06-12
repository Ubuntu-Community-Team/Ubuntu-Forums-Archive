---
title: "Tab auto complete cause system hang for a few minutes"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by llewellynpienaar on 2014-04-02
Good day Ubuntu Community.

I have this annoying bug (not sure if it should happen or not). Regardless of the directory I am browsing. 
When I use the Tab completion on a file that has no more options or directories after it, the system hangs for a few minutes and then asks if it should display all 2000+ options.

Here is a example

/log/README
Display all 2413 possibilities? (y or n)

Any way I can clear those files? or change to only show in directory options?

Best Regards

---

### Post by TheFu on 2014-04-03
Directories that have thousands of files are bad.
Clean up the /log/ directory.

---

### Post by llewellynpienaar on 2014-04-03
Hi, 

It does not matter which directory I am browsing. its whenever I try to browse a directory or file that is not there or does not have any options to browse further it shows me the same message. Here is a different example of the same issue
/lib64/ld-linux-x86-64.so.2
Display all 3163 possibilities? (y or n)

---

### Post by TheFu on 2014-04-03
Exactly where in this are you pressing {tab}?  If you press it after the filename is completed, then it is offering to list every file inside the $PATH - that is kinda the point.

BTW, I'm not seeing this on a 13.10 system.

---

### Post by llewellynpienaar on 2014-04-03
Hi, 

I am using ubuntu server 12.10. Yeah it is odd. On our work servers using the same server this does not happen. Sometimes you press tab once to many times then it just hangs. I am not sure that this should be happening though. It should not list anything if you reached the end of the file and no more extentions are available. Or I might be missing something

---

### Post by Impavidus on 2014-04-03
If you reached the end of the file name the autocomplete assumes you want to give another file name as additional argument. It will then list all files/directories in the current directory. Still, even when there are thousands of them it shouldn't take minutes.

12.10 server edition? You have a few more weeks before it reaches end of life.

---

### Post by TheFu on 2014-04-03
> **llewellynpienaar said:**
> Hi, 

I am using ubuntu server 12.10. Yeah it is odd. On our work servers using the same server this does not happen. Sometimes you press tab once to many times then it just hangs. I am not sure that this should be happening though. It should not list anything if you reached the end of the file and no more extentions are available. Or I might be missing something

Which shell do you use? 
Is there any chance you've modified the completion settings?  Reinstalling the bash-completion module might help, if you use bash.

---

