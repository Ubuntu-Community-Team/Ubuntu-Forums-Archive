---
title: "dell v515w printer not detected during install on 11.10"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by lukyedy on 2012-01-23
I know that there have been other threads regarding this printer install, but being relatively new to all this, I think my issue is slightly different, I appologise in advance if I should have just added this to one of the existing threads, but was unsure whether that would be seen as hijacking, and did not want to break forum ettiquette with my first post.
I am trying to install a dell v515w aio printer under 11.10, I found the linux drivers on the dell website, downloaded them, extracted and ran (even getting past the root password issue) the install seems to run just fine, up to the point where it asks for the printer to be connected to the usb port, but then it just sits waiting as if it has not detected the printer. after a reasonable wait (10mins) I cancelled the install and retried, with the same results, although this time I got a pop-up saying that the printer had been added, and the printer now appears in the printer list (despite the install hanging at the same point as before)
even though the printer is now shown in the printer list, it will not print, the first attempts gave a failed to print error message, and after a reboot any prints just go into the print queue and show pending, but do not generate any error message, but never print.
 
any assistance with this would be greatly appreciated, my responses may be a bit slow in coming as the printer and pc are at my father in laws house, so I cannot instantly access them for any tests or technical info

---

### Post by rbc on 2012-01-24
Is the name of the driver installer dell-inkjet-09-driver-1.0-1.i386.deb.sh? If so, there’s a typo in there somewhere. Open terminal and cd to the directory where that deb.sh is, then issue this command:
./dell-inkjet-09-driver-1.0-1.i386.deb.sh --noexec --keep

This will create a tmp folder under this same directory. Now open nautilus and go to that tmp directory, then find the config directory, then use whatever text editor to open the run.lua file. Use the Find capability to look for the word “ownhership” (yes, that’s the misspelling). Change that word to “ownership”, and save the file. Now, go back to your terminal and run*sudo sh startupinstaller.sh*in the tmp folder.
This fixed the problem I had with a Dell v313w. I got this off the web based on a fix that  someone name Dylan Taylor wrote for a Lexmark printer. I cannot guarantee this will solve your issue, but it’s worth looking into

---

### Post by lukyedy on 2012-01-25
> **rbc said:**
> Is the name of the driver installer dell-inkjet-09-driver-1.0-1.i386.deb.sh? If so, there’s a typo in there somewhere. Open terminal and cd to the directory where that deb.sh is, then issue this command:
./dell-inkjet-09-driver-1.0-1.i386.deb.sh --noexec --keep

This will create a tmp folder under this same directory. Now open nautilus and go to that tmp directory, then find the config directory, then use whatever text editor to open the run.lua file. Use the Find capability to look for the word “ownhership” (yes, that’s the misspelling). Change that word to “ownership”, and save the file. Now, go back to your terminal and run*sudo sh startupinstaller.sh*in the tmp folder.
This fixed the problem I had with a Dell v313w. I got this off the web based on a fix that  someone name Dylan Taylor wrote for a Lexmark printer. I cannot guarantee this will solve your issue, but it’s worth looking into
 thanks for the suggestion, I will try that when I get to the father in laws on the weekend, will post results when I have tried

---

### Post by bigpapapump on 2012-02-01
make sure usblp is loaded

```
lsmod | grep usblp
```

If it isn't... load it

```
modprobe usblp
```

You might have to add usblp to your /etc/modprobe.conf to ensure it reloads on reboot.

---

### Post by halitech on 2012-02-01
basically the printer is a rebadged Lexmark Interpret S405 so knowing how Lexmark is with supporting other then windows OS's, I wouldn't count on getting it to work properly with all features. If you have trouble with the dell driver, you can try the Lexmark drivers located here: [http://tinyurl.com/3eg77f4](http://tinyurl.com/3eg77f4)

---

### Post by bigpapapump on 2012-02-05
I had one computer that worked just fine (as long as the usblp kernel module was loaded).  However, when I went to a second computer that had a fresh install of 11.10 it didn't!  

I spent way too much time trying to track down what was wrong.  I found that the cups error_log was reporting printdriver with permission denied (113).  Also the localhost:631 cups manager simply reported printdriver failed.  

I messed with permissions, sticky bits, the works, and even tried replacing printdriver with script that would prelaunch it with strace.  However, I found that the script wasn't even getting launched!   Long story short, the solution was found in the syslog:

.```
..apparmor="DENIED" operation="exec" ... name="/usr/local/dell/dell09/bin/printdriver" ...
```

stinkin apparmor!!!  I hate you! apparmor was blocking printdriver from executing.

So the solution: Edit /etc/apparmor.d/usr.sbin.cupsd

change:
```
/usr/sbin/cupsd {
```

to:
```
/usr/sbin/cupsd flags=(complain) { 
```

Of course restart apparmor (I did /etc/init.d/apparmor reload and restart)

Hopes this helps someone.  I don't want to say how long I spent figuring this one out...

---

### Post by AngelMasters on 2012-02-06
NONE of these work.

Check out my post as it may be able to help you.

[http://ubuntuforums.org/showthread.php?p=11669500#post11669500](http://ubuntuforums.org/showthread.php?p=11669500#post11669500)

---

