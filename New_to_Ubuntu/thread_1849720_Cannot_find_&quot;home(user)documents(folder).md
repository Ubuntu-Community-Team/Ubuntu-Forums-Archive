---
title: "Cannot find &quot;/home/(user)/documents/(folder)/"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by mschooler93 on 2011-09-25
Awhile ago, I tried to install Grand Theft Auto 2, through a zipped installer (.exe). I think the folder my computer is referring to is the un-zipped folder that contains the installer.
I installed through Wine, and later un-installed it (but i didn't do the uninstaller, I just deleted the files because it wasn't working and I was tired) and since then when I start up, it shows this window that says it cannot find the file or something. I can find no trace of the program in Wine's fake "c:" drive, and it is not installed at all.

---

### Post by anewguy on 2011-09-25
If you are truely looking as per the path in your title, be aware the /documents/ is /Documents/ -> the "D" in documents should be capitalized.

If you are instead looking for some file such as the results of an unzip, and the zipped file was downloaded, then you need to look in /home/(user)/Downloads for the zipped file and the unzipped will probably be a subfolder.

If what you are talking about is neither of these things, then more details from you will be needed.

Dave ;)

---

### Post by mschooler93 on 2011-09-25
No, the window pops up as soon as I log in, saying it cannot find the directory. I am not looking for it, because I am smart and I know I already deleted it days ago. Unfortunately, my computer is not blessed with such knowledge, as it keeps trying to look for it at startup for some reason.

---

### Post by 3rdalbum on 2011-09-25
You haven't mentioned if you've looked in the Startup Applications program to see if it's listed to launch when you log in. If you haven't checked this already, you should check it first.

---

### Post by mschooler93 on 2011-09-25
Attachments:
first is the message
second is part of the startup applications menu. I don't know Ubuntu well enough to know which ones I should be looking for that will cause this message. Also, I haven't checked them off one by one yet, because I tried that once with Windows, and I crashed it. If I have to do that though, let me know.

---

### Post by ajgreeny on 2011-09-25
It's not the user/Documents that can't be found, but the GTAINSTALLER, whatever that is.

Does it mean anything to you?  All I can find is some games links, but I'm not a gamer.

---

### Post by roger_1960 on 2011-09-25
Hi

Not quite sure what you have done, but:

The "false C drive" is in a hidden folder called .wine which can be seen in your home folder ie home/user/.wine  Its fairly obvious once you find it.

One you have installed wine, you must run wineconfig in terminal (or the "Configure Wine" programme ) in order to create these hidden folders.  Then you should be able to successfully install .exe programs.

Hope that helps

Roger

---

### Post by Paqman on 2011-09-25
> **mschooler93 said:**
> it keeps trying to look for it at startup for some reason.

Have you checked Startup Applications to make sure it's not listed?

---

### Post by mschooler93 on 2011-09-25
It is not any of the startup applications. i took off all of them, and it still popped up. So, unless there are hidden startup applications, that is not the problem.

---

### Post by Mark Phelps on 2011-09-25
The GTAInstaller is the file used to install Grand Theft Auto.

---

