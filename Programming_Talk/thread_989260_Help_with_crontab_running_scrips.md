---
title: "Help with crontab running scrips"
date: 2008-11-21
forum: Programming Talk
---

### Post by alexismm on 2008-11-21
Hopefully I am posting this in the correct place. If not then please fell free to move it. 

I have recently, after years of threatening to, moved to Ubuntu as my primary OS. I am fairly happy with it so far, slight learning curve, but I think its worth it :-) 

Anyway, I have been playing with writing a crontab, for a cron to run automated on my system. Basically I am trying to have a cron run to record a radio show. The show is on at 4 AM eastern time, as its a show at home in Europe. 
So far I have constructed a script [1] that runs perfectly from a terminal to begin the recording
Also I have written another script to kill this recording [2], and allow the rest of the first script to run, which converts the wav file to mp3 and delivers it to an archive dir. 

Then I edited my crontab (crontab -e) and added an entry [3]. I have played with the different cron settings, and am happy that I can use the first five columns as documented. I also confirmed that the cron job was running by adding a simple entry to the crontab to run a “mkdir /tem/test” this command ran fine and the file appeard as expected. 

So here is my problem. The scripts that I have written [1],[2] will not run when I add them to the crontab. 
I think that my problem is an environmental one. I have discovered that the default env from a cron that I am trying to unsuccessfully to run [1],[2] from is very limited. Where as the env in a default terminal is quite detailed. My shell has “SHELL=/bin/bash” set where as I think these scripts are written for  “/bin/bash". 

I will hold my hands up and say that I don't fully understand the different scripting methods, tools and this is where I am falling down. 

So here is my question, is there some way of setting the env in the cron to mirror that of my system env befre the cron runs the script? This script runs fine from a default shell on m y system so If I can get the cron to run with that env then I believe that I can resolve this problem 

does any one have any idea how I can get around this? 

Thanks!

[1] : 


> #!/bin/bash
export SHELL=/bin/bash
NOW=$(date +"%b-%d-%y")
mplayer "http://streaming.todayfm.com:8000/listen.pls" -ao pcm:file=/tmp/mystream.wav -vc dummy -vo null ;
lame -m s /tmp/mystream.wav -o "/home/amittm/mp3streams/radio/rd_show - $NOW.mp3" ;
rm /tmp/mystream.wav ;


[2]

> #!/bin/sh
pkill mplayer

[3]

> * * * * * /home/amittm/scripts/streamrecord

---

### Post by geirha on 2008-11-21
Could you post the error messages you get when cron tries to run the scripts? cron will mail you any output the scripts produce. Read it with the command ```
mail
```

---

### Post by alexismm on 2008-11-21
> **geirha said:**
> Could you post the error messages you get when cron tries to run the scripts? cron will mail you any output the scripts produce. Read it with the command ```
mail
```

I am not sure how to get it to email to me. Do I need to update the crontab with my email address? or do I jsut need to add mail to the top of the crontab?

---

### Post by geirha on 2008-11-21
No, it just writes it to a file; /var/mail/*username* and you can read it with the mail command. It does not require any mail servers or email adresses. The mail command is part of the [apt://mailx](apt://mailx) package which I believe is installed by default.

---

### Post by alexismm on 2008-11-21
> **geirha said:**
> Could you post the error messages you get when cron tries to run the scripts? cron will mail you any output the scripts produce. Read it with the command ```
mail
```

I did not have any mail application installed. I have installed it and run the cron again but it does not seem to be sending anything to mail. 

amittm@brynderwyn:~$ mail
No mail for amittm

---

### Post by geirha on 2008-11-21
That's odd. That mplayer command should output alot of data. Are you perhaps running it in root's crontab? If so, try ```
sudo mail
``` to read root's mail.

---

### Post by alexismm on 2008-11-21
> **geirha said:**
> That's odd. That mplayer command should output alot of data. Are you perhaps running it in root's crontab? If so, try ```
sudo mail
``` to read root's mail.

Great, as soon as I started getting the cron messages through mail I was able to debug the issue based on the messages, now its working fine for me. 
Before I had access to the errors in the mail messages, I really did not know what the problem was! 

thanks!

---

### Post by Cracauer on 2008-11-21
mplayer is a wired program. It is actually using the tty - and in the cronjob you don't have one.

mplayer       -noconsolecontrols

gets around this particular issue, but in general you want to try hard to find a cleaner commandline program than mplayer for scripts.

%%

Another issue is $PATH and other environment variables that aren't imported from your dotfiles into cronjobs you run.

I have
1 2 3 4 5 . /home/cracauer/.lib ; sh blah fasel

in my crontabs.

---

