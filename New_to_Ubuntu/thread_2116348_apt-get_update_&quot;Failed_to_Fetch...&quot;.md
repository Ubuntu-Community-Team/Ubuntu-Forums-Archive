---
title: "apt-get update &quot;Failed to Fetch...&quot;"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by pwert00 on 2013-02-15
Hi all,

I have a problem with my "sudo apt-get update" command in ubuntu.  I know a few things about using the terminal in general, but I don't know how to use the terminal for updating.  For the record, when I use the software updater, it still gives the same problems.  I tried googling extensively and I cannot find out how to solve my problems, so if someone can help me that would be great.  Here is the end of the output after I type "sudo apt-get update" below.  

```
W: Failed to fetch http://ppa.launchpad.net/ikarosdev/unity-revamped/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ikarosdev/unity-revamped/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ikarosdev/unity-revamped/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I also noticed that when the code is running for updating, that there are a few error messages in the runnning lines of code.  Maybe this can help.  

```
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found

```

---

### Post by cariboo on 2013-02-15
You are getting the error, because there aren't any Qunatal packages available in the ppa you have enabled. The easiest way for you to disable those ppas, is to go to System Settings->Software Sources, then click the Other Software Tab, highlight the ppas you want to remove, and click the remove button.

Once you have removed the ppa, open a terminal and type:

```
sudo apt-get update
```

to make sure you don't get any more errors.

---

### Post by arpanaut on 2013-02-15
There are no packages for quantal in that repository.
You will need to remove those from "Software Sources"

You need to untick those entries for that PPA 
Example:

---

### Post by xaff90 on 2013-05-09
Hello,
I have the same problem but I can't disable or delete this ppa in the "Software Sources".
Any ideas to resolve this problem?
Thanks :cool:

---

### Post by todorakiggg on 2013-05-09
I had similar problem, which I solved by removing the troubled ppa:


sudo apt-add-repository --remove ppa:kernel-ppa/ppa
[COLOR=#333333][FONT=Ubuntu Beta]
Then update with:[/FONT][/COLOR]

sudo apt-get update

---

### Post by xaff90 on 2013-05-12
You have to remove or comment the lines relative to ikarosdev-unity-revamped-precise. To achive this try one of these solutions:
- remove or comment(add '#' in front of the line) the lines for this ppa 'sudo gedit /etc/apt/sources.list' or 'sudo gedit /etc/apt/sources.list.d/ikarosdev-unity-revamped-precise.list'
- 'sudo rm /etc/apt/sources.list.d/ikarosdev-unity-revamped-precise.list'
If you want more informations about this, you can read the manual page 'man sources.list'. 

ps: To solve problem, beginning by read man pages on the problematic command ;-)

---

