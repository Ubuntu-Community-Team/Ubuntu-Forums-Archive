---
title: "Terminal command &quot;cd&quot; returns &quot;file or directory not found&quot; every time"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by iluminameluna on 2011-10-06
I'm using an Asus eeePc & have Netbook 10.10 installed.

I wanted to do a LiveUSB w/ 10.04.3 but when I run the Live Installer it tells me at the end that there is a problem w/ my installation & it aborts.

That I can figure out later but what I want to do in the immediacy is ck to make sure my .iso file's integrity by using md5sum in a terminal window ... & here I'm stuck ...

I've spent over 4 hours running down all possible suggestions on how to get to my .iso file in my Downloads folder to ck it. All say to use cd to get to the file & then run the md5sum script on it in a Terminal window. Reason for not just downloading another copy of the file is that I'm on a USB modem (no landline where I live) AND I have 3G worth of broadband to "spend" a month ...

However, every time, w/out fail, I get "No such file or directory".

I feel like an idiot but I also think I've had this problem before. Lupus fog, however, does a number on my cognitive ability so I might be doing something wrong or misinterpreting an instruction (or 2, or all).

PLEASE help! I'm trying to make this netbook as streamlined as possible, performance-wise, 'cause I have to spend much of my time in an almost prone position. It's my sanity lifeline ...

If I can get some detailed instructions or suggestions, I'll REALLY appreciate it!

---

### Post by nothingspecial on 2011-10-06
Where is the iso?

---

### Post by iluminameluna on 2011-10-06
> **nothingspecial said:**
> Where is the iso?
In /home/jessie/downloads

---

### Post by iluminameluna on 2011-10-06
> **iluminameluna said:**
> In /home/jessie/downloads
This is a copy/paste from my Terminal window, & THANKS!

jessie@MumsieNetbook:~$ md5sum file:///home/jessie/Downloads/ubuntu-10.04-netbook-i386.iso 
md5sum: file:///home/jessie/Downloads/ubuntu-10.04-netbook-i386.iso: No such file or directory
jessie@MumsieNetbook:~$ cd /home/$jessie
jessie@MumsieNetbook:/home$ cd /downloads
bash: cd: /downloads: No such file or directory
jessie@MumsieNetbook:/home$ cd
jessie@MumsieNetbook:~$ cd /home/user
bash: cd: /home/user: No such file or directory
jessie@MumsieNetbook:~$ cd ~
jessie@MumsieNetbook:~$ cd /downloads
bash: cd: /downloads: No such file or directory
jessie@MumsieNetbook:~$

---

### Post by nothingspecial on 2011-10-06
Your problem might be that linux is case sensitive.

If you type ```
cd /home/jessie/downloads
```

with a lowercase D, when in fact your Downloads directory starts with an upper case D, the command will fail.

Try

```
cd /home/jessie/[COLOR="Red"]D[/COLOR]ownloads
```

---

### Post by iluminameluna on 2011-10-06
> **nothingspecial said:**
> Your problem might be that linux is case sensitive.

If you type ```
cd /home/jessie/downloads
```

with a lowercase D, when in fact your Downloads directory starts with an upper case D, the command will fail.

Try

```
cd /home/jessie/[COLOR="Red"]D[/COLOR]ownloads
```
Copy/pasted:

jessie@MumsieNetbook:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory
jessie@MumsieNetbook:~$

---

### Post by nothingspecial on 2011-10-06
```
cd ~/Downloads
```

---

### Post by iluminameluna on 2011-10-06
> **iluminameluna said:**
> Copy/pasted:

jessie@MumsieNetbook:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory
jessie@MumsieNetbook:~$
Gah .. did it wrong the first time then copy/pasted YOUR code & I'm good .. so far ... pls gimme a min more?

PERFECTOMUNDO!!!!! If you were here, I'd KISS you!!! THANKS!!!

---

### Post by audiomick on 2011-10-06
I get confused where I am with cd too. I use 
```
ls
```to see where I am, and the exact name of the directory I want to go into.

If you do ls from you home directory, you should see /home/jessie in the list that shows up somewhere. Pay attention to whether it is "jessie" or "Jessie", because file and directory names are case sensitive.

do

```
cd jessie
```assuming it is a small "j" in the name, then
```
ls
```you should see /home/jessie/downloads in the list. Have another look. The folder "Downloads" has a capital "D" on my system.

From there do 
```
cd Downloads
```assuming that it is a capital "D". Then do ls again. You should see your iso, and be able to do the md5sum.

I expect nothingspecial will be back any minute now with commands to do it all at once, because he's good like that. ;)

Pay attention to the capitals, though. I suspect that is your problem.

edit: beat me to it by miles,  didn't he. ;)

---

### Post by s.fox on 2011-10-06
Are you still stuggling with navigating the file system?  Have you got into the Downloads directory?

If you have not run this command in terminal to see a list of all folders you can cd into:

> ls -d */

edit: Glad you were able to get into the folder :)

---

### Post by audiomick on 2011-10-06
That's nice. Much better than just a straight "ls". :popcorn:

---

### Post by iluminameluna on 2011-10-06
Michael & S.Fox, yeah, he beat you to it but your jumping in to help was AWESOME! Now I can sleep 'cause I can see the sd5sum hash is right ... The rest will be a breeze .. It's a SanDisk ssd microcard so I know how to fix THAT prob. Even thru the FOG! Good night (it's dawn here but it's the end of a BAD day that ended WELL!)

<3 to all of you!

---

### Post by audiomick on 2011-10-06
Glad you're sorted. Sleep well. You might like to mark the thread as solved. That's in the thread tools at the top of the thread.

---

### Post by Lars Noodén on 2011-10-06
> **s.fox said:**
> 

If you have not run this command in terminal to see a list of all folders you can cd into:



There is also [pwd](http://manpages.ubuntu.com/manpages/oneiric/en/man1/pwd.1posix.html), which will show you exactly which directory you are in at the moment.

---

### Post by Vaphell on 2011-10-06
also use autocompletion (tab key)
let's say you type
```
cd D
```
now if you press tab it will fill as much as it can: full name if there is only one thing matching, common part if there are more possibilities, eg Down for **Down**load and **Down**grade. Typing l[tab] will complete Download, on the other hand typing g[tab] would choose Downgrade.
Double tab will show you all possibilities so you don't have to guess what the names are.

---

