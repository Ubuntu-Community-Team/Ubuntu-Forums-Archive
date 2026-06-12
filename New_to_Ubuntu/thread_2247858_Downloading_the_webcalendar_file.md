---
title: "Downloading the webcalendar file"
date: 2014-10-10
forum: New to Ubuntu
---

### Post by hugh6 on 2014-10-10
I am trying to download and install "webcalendar" from sourceforge. I have read and tried wget http://sourceforge.net/projects/webcalendar/files/webcalendar%201.2/1.2.7/WebCalendar-1.2.7.tar.gz". It appears to try to download but then I get permissions denied. What am I doing wrong? Thanks for the help!!

---

### Post by yancek on 2014-10-10
I just downloaded it without problems.  Where are you trying to save it.  If you are online as a normal user, download it to your /home/user/Downloads directory.  When you click Save, you should have the option of where to Download to.

---

### Post by hugh6 on 2014-10-10
I am trying to download from a virtual ubuntu server at work.

---

### Post by yancek on 2014-10-10
> I am trying to download from a virtual ubuntu server at work. 		

You'll have to explain that in a little more detail.  You originally said you were trying to to download it from sourceforge.   Are you trying to download it to a machine at your work which you don't have permissions for?  Your post isn't clear on what you are trying to do.

---

### Post by hugh6 on 2014-10-11
Sorry..... I have a virtual server with ubuntu server installed. I am trying to download webcalendar from the sourceforge website from the command line since ubuntu server does not have a web browser.  I get file permission errors. How do I resolve this? Thanks

---

### Post by Vladlenin5000 on 2014-10-12
I also download it just fine with wget. I copied/pasted as is from your post.
Perhaps you should tell exact error message... If it doesn't let you download to your current location then most likely you don't have write permission in that folder.

---

### Post by hugh6 on 2014-10-15
I got it. I tried Sudo.. and it downloaded. I am a windows guy trying to learn linux. Thanks a bunch!

---

### Post by hugh6 on 2014-10-15
one more thing.. It is downloading but I want the .tar file and I am getting the zip file. How do I force to download the tar

---

### Post by yancek on 2014-10-15
On the page linked in your first post, there are options to download either a tar.gz or a zip file, select the tar.gz.

---

### Post by ian-weisser on 2014-10-15
Er, you do realize that what you are trying to do requires non-trivial skills? Not something I recommend to beginners.

I would recommend trying one of the many fine calendar applications already in the Ubuntu Software Center.

---

### Post by hugh6 on 2014-10-17
Got it downloaded and installed..... have another problem, when I run the program I get this message " [COLOR=#000000][FONT=Arial]The file permissions of the [/FONT][/COLOR]includes directory are set so that the installer does not have permission to create a new file. Please change the permissions of the following directory to continue.:[INDENT][B]/var/www/html/WebCalendar/includes"

How do I change the permissions on the includes directory?

[/B] 
[/INDENT]

---

### Post by yancek on 2014-10-17
Usually when you are outside your /home/user directory, you need root privileges.  You should preface any command with sudo, the command to change permissions is chmod.  Open a terminal and type:  man chmod which is the manual for that command.   You could also just google changing permissions in Linux.  Don't know what you want to change to or what the permissions currently are so can't be any more speceific.

---

