---
title: "HowTo make cron run GUI applications"
date: 2005-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by henriquemaia on 2005-12-18
First of all, please refer to this [howto]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron") to learn more about crontab.


My motivation to find this out was because there are several radio shows I really like and I was always missing them. As such, I needed something to make amarok play the chosen radio station at specific times. Probably this could be achieved through a more elegant solution, but what is explained here works great. Also, I knew that by learning how to do this, I could use it for many other things.

To accomplish this, you have to edit your crontab:

```
crontab -e
```

you can also use a nicer GUI tool to edit crontab, like **Gnome Schedule** (not in the repositories) or **KCron** (available on the repositories).

If you use a GUI tool, please adapt the instructions accordingly. I will explain this using as basis the default crontab editor.

To run a GUI command on cron, you'll have to tell cron what display the program should use. For that you use:

```
export DISPLAY=:0 
```

The '**:0**' is the default. If you like the program to run on other display, please change the number accordingly (e.g. **:1**, **:2**, etc).

So, you add to what is explained [here]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron"):  

```
01 04 * * * /usr/bin/somedirectory/somecommand
```

the **export** variable, like this: 

```
01 04 * * * export DISPLAY=:0 && /usr/bin/somedirectory/somecommand
```

You can omit the full path to the application bin. For **amarok**, you just need to use the 'amarok' command. Works fine both ways.

So, in my case, as I want **amarok** to play Antena2 (Portuguese classical radio station) at a specific time, I use:

```
30 16 * * 7     export DISPLAY=:0 && amarok mms://rdp.oninet.pt/antena2 
```

This will make amarok start the Antena2 url every Sunday, at 16:30. But I want also to shut up amarok after the show is finished. So, I use:

```
0 17 * * 7     export DISPLAY=:0 && amarok -s

```

This will shut up amarok at 17:00 every Sunday.

[SIZE="1"](Just a side note - to make amarok play mms urls, you have to set it to use xine engine)[/SIZE]

You can use this export trick to the limits of your imagination with every kind of application you want. 

Another example that occurs to me is when you neet to use an application for a certain period of time, from 3AM to 9AM, for exemple.

```
0 3 * * * export DISPLAY=:0 && your_favorite_application
```

that will start **your_favorite_application** (change this to the command that runs the application you desire) everyday at 3AM. To shut it down, I use:

```
0 9 * * * killall your_favorite_application
```

This will shut it down at 9AM.

Hope this helps some of you.

If you have more ideas how to use this trick (or how to improve this HowTo), please share with us in the thread.

---

### Post by henriquemaia on 2006-01-21
This howto was updated. Have a good time!

---

### Post by HJThis on 2006-01-21
Hi,henriquemaia

Nice work  just like to ask is this somthing
that may work with any prog????

Thank you

---

### Post by henriquemaia on 2006-01-21
I suppose so. I have tested this with lots of apps and always managed to get them working. As long as you put on you crontab the correct command line caller* to the application you want, there should be no problem at all. It is a good practice to test the command line before introducing it in crontab. Under a terminal, run: 

```
export DISPLAY=:0 && your_favorite_application
```

and see if does what you expect it to do. If it does, than you can introduce it to crontab that you know for sure it will work.

Hope this helps you.

*remember that the command line to call an application is not always the application name. For example, calculator's command caller is 'gcalctool' if you use Gnome or 'kcalc' if you use KDE. Just a reminder.

---

### Post by pgmario on 2006-04-02
Great how-to! Thanks a lot.
Also a good way to start an X-application from tty1.

---

### Post by henriquemaia on 2006-04-03
[QUOTE=pgmario]Great how-to! Thanks a lot.
Also a good way to start an X-application from tty1.[/QUOTE]

That's true. Now and then I use it. I really like this.

---

### Post by outofnicks on 2006-04-10
Thanks for the tutorial. I did a neat thing with it, scheduling voice announcements of the time every half-hour. Don't ask me why, just thought it was neat. I like to hear them in the morning starting about sunrise, it can help if I have to get up at a certain time.

I went to the AT&T Labs Text-to-Speech demo page at:

[http://public.research.att.com/~ttsweb/tts/demo.php](http://public.research.att.com/~ttsweb/tts/demo.php)

Picking my favorite voice (Lauren), I phonetically spelled out the time like so:

Seven, thirty, ay em.

This sounded better than typing:
7:30 am
The "am" was spoken as am, the word, so AM and PM needed to be spelled phonetically.

I put all the sound files in a folder under my home directory, and added in crontab a line for each of them according to the tutorial here, like so:

```
30      07      *       *       *       export DISPLAY=:0 && totem /home/ken/Documents/Sounds/Time/7-30am.wav
```

That Text-to-speech demo is fun to play around with, very good quality voices :)

---

### Post by henriquemaia on 2006-05-20
[QUOTE=outofnicks]Thanks for the tutorial. I did a neat thing with it, scheduling voice announcements of the time every half-hour. Don't ask me why, just thought it was neat. I like to hear them in the morning starting about sunrise, it can help if I have to get up at a certain time.

I went to the AT&T Labs Text-to-Speech demo page at:

[http://public.research.att.com/~ttsweb/tts/demo.php](http://public.research.att.com/~ttsweb/tts/demo.php)

Picking my favorite voice (Lauren), I phonetically spelled out the time like so:

Seven, thirty, ay em.

This sounded better than typing:
7:30 am
The "am" was spoken as am, the word, so AM and PM needed to be spelled phonetically.

I put all the sound files in a folder under my home directory, and added in crontab a line for each of them according to the tutorial here, like so:

```
30      07      *       *       *       export DISPLAY=:0 && totem /home/ken/Documents/Sounds/Time/7-30am.wav
```

That Text-to-speech demo is fun to play around with, very good quality voices :)[/QUOTE]

This is nice. Thanks for sharing this idea.

I also set up a reminder using images that pop up every 3 hours. The cool thing is that the possibilities are endless. Cron is a very useful tool.

---

### Post by kashms on 2006-05-20
This is not working for me! For example I put the following entry in crontab:

```
10 * * * * export DISPLAY=:0 && zenity --notification --text "This is a test."
```

Nothing happens and I get a mail from cron:

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Syntax error

Of course the command works from the terminal.

---

### Post by henriquemaia on 2006-05-20
[quote=kashms]This is not working for me! For example I put the following entry in crontab:

```
10 * * * * export DISPLAY=:0 && zenity --notification --text "This is a test."
``` 
Nothing happens and I get a mail from cron:



Of course the command works from the terminal.[/quote] 
Two questions:[INDENT][LIST]
[*]What is the number of the X you're running? To find out, use:[/LIST][INDENT]```
ls /tmp/.X11-unix/
``` [/INDENT][LIST]
[*] Did you try running the command from a terminal emulator like GNOME Terminal or from a tty (console)?[/LIST][/INDENT]I have tried the same command you shown and worked as expected. Even from the console (tty1).

---

### Post by kashms on 2006-05-21
```
$ ls /tmp/.X11-unix/
X0
```

You are on to something with the console/terminal. If I type: 

```
$ export DISPLAY=:0 && zenity --notification --text "This is a test."
```

in Gnome-Terminal it works. However, if I log into tty1 and try the same command I get the error:

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Syntax error

---

### Post by henriquemaia on 2006-05-21
[quote=kashms]```
$ ls /tmp/.X11-unix/
X0
``` 
You are on to something with the console/terminal. If I type: 

```
$ export DISPLAY=:0 && zenity --notification --text "This is a test."
``` 
in Gnome-Terminal it works. However, if I log into tty1 and try the same command I get the error:[/quote]

Are you logged in with your normal user (the one running X) on the console? Are you running crontab as normal user or system wide?

---

### Post by kashms on 2006-05-21
[QUOTE=henriquemaia]Are you logged in with your normal user (the one running X) on the console? Are you running crontab as normal user or system wide?[/QUOTE]

I log in as normal user both in X and in console. I think the root account has not even been activated.

If in the console I do "sudo -s" and then try the same command I get the following error:

> 
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
Syntax error


Apparently my cookies are no good

---

### Post by henriquemaia on 2006-05-21
[quote=kashms][...]

Apparently my cookies are no good[/quote] 
No, that's normal, since Xauthority file is locked for your user only. 

Try this on a terminal:

```
xhost +
``` 
and then try the   
```
export DISPLAY=:0 && zenity --notification --text "This is a test."
```command from the tty.

---

### Post by kashms on 2006-05-21
```
$ xhost +
access control disabled, clients can connect from any host
```

And sure enough the command now works from tty. Thanks!

How would I use this in the crontab file?
What are the security implications of using "xhost +"?

---

### Post by henriquemaia on 2006-05-21
[quote=kashms]```
$ xhost +
access control disabled, clients can connect from any host
``` 
And sure enough the command now works from tty. Thanks!

How would I use this in the crontab file?
What are the security implications of using "xhost +"?[/quote]

About the security implications, I found this on the internet:

«The xhost command opens a huge security hole because it gives to any user of the remote computer rights to control the behavior and to monitor the display, the keyboard, and the mouse of the local computer. The only secure setting of xhost is "xhost -" which denies any access, except for the local user.»

The thing is that with that you have found that you have an issue with the way your xserver is dealing with the hosts. 

try resetting the xhost to 

```
xhost -
```

and then use the command again from the tty, to see if you get the same previous error.

If yes, do:

```
xhost local:name_of_your_user
```

and then run the command (from the tty).

Let's see if this helps.

---

### Post by kashms on 2006-05-21
```
$ xhost -
access control enabled, only authorized clients can connect
```

From tty I then get the same error as before.

```
$ xhost local:my_user
non-network local connections being added to access control list
```

The command works again from tty. Excellent!

---

### Post by henriquemaia on 2006-05-21
[quote=kashms]```
$ xhost -
access control enabled, only authorized clients can connect
``` 
From tty I then get the same error as before.

```
$ xhost local:my_user
non-network local connections being added to access control list
``` 
The command works again from tty. Excellent![/quote] 
If that gets things right, put that

```

xhost local:your_user
``` 

on the .bashrc, so it will be run everytime you login. Now you can have your cron thing working everytime.

---

### Post by kashms on 2006-05-21
That worked! Thanks for your help.

---

### Post by henriquemaia on 2006-05-21
[quote=kashms]That worked! Thanks for your help.[/quote]

You're welcome. I'm glad to help.

---

### Post by geco on 2010-10-09
> **henriquemaia said:**
> 
So, you add to what is explained [here]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron"):  

```
01 04 * * * /usr/bin/somedirectory/somecommand
```

the **export** variable, like this: 

```
01 04 * * * export DISPLAY=:0 && /usr/bin/somedirectory/somecommand
```


Actually, you don't need to export the variable:

```
01 04 * * * DISPLAY=:0 /usr/bin/somedirectory/somecommand
```

is enough for the program to work.

Also, you are assuming that you will run the application on display :0

---

