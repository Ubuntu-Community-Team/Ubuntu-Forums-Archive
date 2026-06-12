---
title: "what is the password for UI LOCK to open qbittorrent ?"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by aaron9 on 2013-09-15
qbtorrent was working great until i got a message box stating i need to unlock ui password...i have no clue what this means...i have searched everywhere for info with no luck. HELP  :confused:

---

### Post by TheFu on 2013-09-15
Could this just be the screen saver? If so, then it is the login password for the user that logged into teh Ubuntu machine.

I must be misunderstanding something.

---

### Post by fireflower on 2013-09-15
Are you the one who installed linux on your box? If so, you should know the password. If not, call the one who installed it.

---

### Post by aaron9 on 2013-09-15
i tried the administrator password with no luck...uninstalled and re-installed it 2 times and now Qbittorrent is working and not asing for a UI password...a glitch i suppose...But I am happy with Ubuntu so Not complaining...Thanks Everyone...takes time and patience to learn a new OS...

---

### Post by fireflower on 2013-09-16
Glad to hear it. Your first line of defence should always be a restart or two. Luckily those take only a few seconds in Ubuntu even with an obsolete computer. That said, here's how to mark your thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Naveen_P_Suthar on 2014-02-23
Below are the step to reset the password:

Open up home directory and change the view to show hidden files (Ctrl + H) > now  go to .config > qBittorrent > open qBittorrent.conf with your  favorite text editor (i.e. gedit) and search the below shown lines :
[LEFT] [B]
password=xyzsomething
locked=true[/B]
[/LEFT]
 [LEFT] 
Change it to as below :
[B]password=
locked=false[/B]
[LEFT] [/LEFT]

delete whatever the password after is equal (=) sign, save and exit.
[/LEFT]
 [LEFT] 
[/LEFT]
 [LEFT] Make sure while doing this qBittorrent is closed or kill qBittorrent task before doing this, otherwise it'll just  recreate the same document automatically to overwrite your editing.

Now start the qBittorrent and you are done.
[/LEFT]

---

