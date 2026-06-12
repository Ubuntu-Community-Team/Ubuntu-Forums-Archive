---
title: "Execute the command most safely"
date: 2020-09-24
forum: Programming Talk
---

### Post by secux-22 on 2020-09-24
[COLOR=#242729][FONT=Arial]I want to automatically export an mdb file so that the system can work with CSV but I don't want to use functions like shell_exec, exec, system and etc
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]the option I can think of: create a user with access to only one directory **/var/files** and one command **mdb-export** -- [U]if you think this is a good option. would you advise me how to do it

[/U][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]what would you recommend me to do and how to do it ?[/FONT][/COLOR]

---

### Post by TheFu on 2020-09-24
mdb files are more complex than you seem to realize. They can hold code, 50 tables, layouts, functions and they can be locked and encrypted.  So, the first step is to clearly decide what your requirements around each different mdb file is and see whether there is any Unix tool that can even access it in that manner.

Why not just use VBA on Windows? Obviously, the file comes from Windows. Use powershell.

---

### Post by secux-22 on 2020-09-25
I found I have a way to read the file, now my question is the safest to run the command automatically. 

ssh login machine with special user? but how to restrict user rights to only one command and directory?

---

### Post by TheFu on 2020-09-25
> **secux-22 said:**
> I found I have a way to read the file, now my question is the safest to run the command automatically. 

ssh login machine with special user? but how to restrict user rights to only one command and directory?

If you just want to run the command at a specific time, use **cron**.

If you want to run the command when a new file is copied over somewhere specific, use **inotify**.

When processing is finished, you can move the files to an "output" directory that provides read-only access. Allowing files to be dropped, processed and output to the same directory is a huge security failure.  Each of those steps need to happen in different directories almost always. This is a security thing well documented in texts.

If you insist on using ssh, you can look up how git servers are setup to only allow the 'git' command to be used over ssh. I think the ProGit book has half a page about that or any comprehensive ssh text would as well.

---

