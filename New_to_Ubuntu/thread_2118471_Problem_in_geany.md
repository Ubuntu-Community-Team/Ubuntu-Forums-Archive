---
title: "Problem in geany"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by Rashedul Riad on 2013-02-21
I am using version 12.04 and installed geany yesterday, the problem is, I can compile the program, but when I try to execute, a window is appeared with the following message:
"/usr/bin/xterm: Can't execvp -e : No such file or directory"

plz give me the solution of this.

---

### Post by Kopkins on 2013-02-21
If you're trying to execute a file make sure that the execute bit is there. If it isn't it will turn up as no such file. 

From the directory where your file is do```
ls -l | grep <your_file_name>
``` Just replace your file name.

The whole output will be ```

drwxrwxr-x     9                             kyle   kyle      4096  Feb 18 21:27   VirtualBox VMs
permissions    number of files or folders    user   group     size  Date           name

```the permissions will look something like 
```
-rw-rw-r-- 
```Or ```

-rwxrwxr--
```Anything like that. The first `-' is for if it is a directory. if it is the `-' will be a d. Ex: `drw-rw-r--'
The next three are for what root can do with the file. r = read, w = write, x = eXecute. The next three are the owner of the file. and the last three are any other users. 
root -rwx------
owner ----rwx---
other -------rwx
directory d---------

For a file with permissions -rwx-rw-r
Root permissions : read write execute
Owner : read write
and Other : read

If the execute bit isn't turned on for your user then it cant run. 

Try ```
sudo chmod a+x <your_file>
```a+x gives execute to all users. to give just to the owner user use u+a or for root r+a.

Best of luck, hope I could help.

Kopkins

---

