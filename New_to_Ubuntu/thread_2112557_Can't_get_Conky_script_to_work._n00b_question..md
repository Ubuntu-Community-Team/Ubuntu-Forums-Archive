---
title: "Can't get Conky script to work. n00b question."
date: 2013-02-05
forum: New to Ubuntu
---

### Post by Mr. ViC on 2013-02-05
Hi guys.

I have Linux Voyager, a xubuntu version which already comes installed with Conky.

So I got a script which I love but can't get to work.

I included a copy in the dropbox link:

[https://www.dropbox.com/s/4pgz5g8jy3yyj4q/12-1-stylintile-1.tar.gz](https://www.dropbox.com/s/4pgz5g8jy3yyj4q/12-1-stylintile-1.tar.gz)

Also, already edited the locations in the script to fit mine. Then, tried to use this command:

```
sh -c "sleep 10; conky -c /home/vitality/Downloads/conky/.cal_rc;"
```

To get it to work, but nothing worked.

Thanks in advance.

---

### Post by 0N3 on 2013-02-05
Your trying to start the cal.rc file with a sleep delay of 10 secs?
Im pretty sure your autostart file should be a .sh extension? I could be wrong.

---

### Post by 0N3 on 2013-02-05
Have you made the startup script executable?

---

### Post by Mr. ViC on 2013-02-05
> **0N3 said:**
> Your trying to start the cal.rc file with a sleep delay of 10 secs?
Im pretty sure your autostart file should be a .sh extension? I could be wrong.

There is no .sh file available.

> **0N3 said:**
> Have you made the startup script executable?

No I have not, how would I do that?

Thanks for your reply!

---

### Post by 0N3 on 2013-02-05
I see you have your conky file in /home/vitality/Downloads/conky/.cal_rc directory

I think its easier to put them into your /home

You need a startup script something like 

#!/bin/sh
sleep 20
conky -d -c ~/.conkyrc
exit

Paste that into a text file and call it conky_start.sh

Right click that file and go to Properties > Permissions and make sure the tick box beside Execute is ticked

---

### Post by 0N3 on 2013-02-05
Could you also open a terminal and type in conky and hit enter and post the output?

---

### Post by Mr. ViC on 2013-02-05
> **0N3 said:**
> I see you have your conky file in /home/vitality/Downloads/conky/.cal_rc directory

I think its easier to put them into your /home

You need a startup script something like 

#!/bin/sh
sleep 20
conky -d -c ~/.conkyrc
exit

Paste that into a text file and call it conky_start.sh

Right click that file and go to Properties > Permissions and make sure the tick box beside Execute is ticked

Thank you, going to try that now.

By the way, is there any way to know which one is the autostart file?

---

### Post by Mr. ViC on 2013-02-05
Edit:

I just keep getting this when I start up:

[IMG]http://i.imgur.com/xYHIt0x.png[/IMG]

---

### Post by 0N3 on 2013-02-05
Are all of your configuration files in your home directory?

---

### Post by Mr. ViC on 2013-02-05
> **0N3 said:**
> Could you also open a terminal and type in conky and hit enter and post the output?

Here's the output:

```
Conky: desktop window (1200003) is subwindow of root window (14e)
Conky: window type - desktop
Conky: drawing to created window (0x4600001)
Conky: drawing to single buffer

```

And the screen I've posted above.

> **0N3 said:**
> Are all of your configuration files in your home directory?

Yes, they are.

Again, thanks for your reply.

---

### Post by 0N3 on 2013-02-05
> **Mr. ViC said:**
> Hi guys.

I have Linux Voyager, a xubuntu version which already comes installed with Conky.

So I got a script which I love but can't get to work.

I included a copy in the dropbox link:

[https://www.dropbox.com/s/4pgz5g8jy3yyj4q/12-1-stylintile-1.tar.gz](https://www.dropbox.com/s/4pgz5g8jy3yyj4q/12-1-stylintile-1.tar.gz)

Also, already edited the locations in the script to fit mine. Then, tried to use this command:

```
sh -c "sleep 10; conky -c /home/vitality/Downloads/conky/.cal_rc;"
```

To get it to work, but nothing worked.

Thanks in advance.

I see you said you edited the locations in your script to fit yours? Have you changed all those locations now that your conky configuration is in your /home? 
It seems like conky is working but doesn't know what files and images to display to mee i'm guessing there something wrong with your structure. Im no expert on conky but im pretty sure thats the problem.

---

