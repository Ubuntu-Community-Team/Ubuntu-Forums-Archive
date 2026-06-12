---
title: "Annoying Firefox crashes"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by barneyjoseph on 2011-10-21
[SIZE=1]Hi,
  
This is for those who would like a quick fix for the annoying firefox crashes in Ubuntu/Linux. 
  
Firefox sometimes refuses to start saying that another firefox is  already open. Sometimes Ubuntu might create an error while shutting down  saying that "firefox-bin" is not responding. The problem lies with the  "lock" and ".parentlock" files that were not deleted by firefox when  closed. 
  
This is just a bunch of rudimentary commands that are to be put into a file. Click the file and the problem goes away.
  
First a bit of searching is required. Go to your home folder and make  sure hidden files are shown. Go to ".mozilla/firefox" and locate the  profile folder. I'm not sure what name it chooses. It will be the folder  which has the files "***lock***" and "***.parentlock***". Remember the profile name.
  
Secondly, (for lazy people like me) create an empty file on your desktop and paste these commands. Make sure you replace **your_profile_folder** with the correct name that you just found out. Make sure you save the file with "***.sh***" eg: "***diefirefoxdie_reload.sh***"
  
  *killall firefox-bin*
  *rm -f ~/.mozilla/firefox/**your_profile_folder**/lock*
  *rm -f ~/.mozilla/firefox/**your_profile_folder**/.parentlock*
  *firefox*
  
I would like to put in a little explanation for newbies like me.  "killall" is used to kill the processes in the "Process" tab of your  "System Monitor" a.k.a "Task Manager" for those from MSWindows.  "firefox-bin" is the process name. Killall will terminate all instances  of it. "rm" is like the "del" command in windows. "~" stands for your  home folder. The last line "firefox" is optional (only if you want to  open firefox again). For me it serves as a check to see if the problem  persists.
  
Now that the file is saved, you need to make it executable a.k.a. "click and run". Go to terminal and type:

  *cd ~/Desktop*
   *chmod a+x diefirefoxdie_reload.sh*
  
This makes it executable. To see if it worked, right click the file and go to the "Permissions" tab. The "*Allow executing file as program*" should be checked. If it doesn't work then add "*sudo*" before the "*chmod*" line.
  
Go to the file now and double click it and choose "Run". 
  
Enjoy!

___________________________

I hope this works on other distributions of Linux. I am a newbie :guitar:
[/SIZE]

---

