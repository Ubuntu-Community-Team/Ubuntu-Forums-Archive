---
title: "Making bash do something on a timer/schedule?"
date: 2009-10-03
forum: Programming Talk
---

### Post by rob86 on 2009-10-03
Can I make BASH perform some things on a timer? For example, downloading a file with wget every hour.

---

### Post by wojox on 2009-10-03
cron job would do the trick. [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by rob86 on 2009-10-03
Oh yeah I remember cron from when I used to run eggdrop bots, thanks.

---

### Post by rob86 on 2009-10-03
I seem to be having some trouble with cron. I read about it, and I thought I understood what I was doing but it isn't working.

For testing purposes, I made a sh script that does echo 'Hello world' and then set up a cron to run it every minute to see if it works, but it doesn't seem to do anything. Here's what I'm seeing: First I test the script, then I set up a cron, well technically there are two, but that's because the first one didn't work so I tried another.


```
rob@desktop:~$ ~/myscript.sh
Hello World
rob@desktop:~$ crontab -l
# m h  dom mon dow   command
* * * * * ~/myscript.sh
*/1 * * * * ~/myscript.sh


```

---

### Post by lswb on 2009-10-03
cron jobs are not aware of your display and can't just echo something to the screen. Your original example of downloading a file, however, would work.

There are various ways of getting a cron job to display a message on your running display e.g. notify-send or setting the DISPLAY variable in the cron job and having it open terminal or window to run your command. There are some complications with the latter method especially, you can search for threads on the forum with more information.

---

### Post by rob86 on 2009-10-04
I get what you're saying lswb, but I still seem to be having problems just getting cron to do anything. I re-did my test crontab to run gthumb so it looks like this:

# m h  dom mon dow   command
* * * * * /usr/bin/gthumb
*/1 * * * * /usr/bin/gthumb

I wait and wait for 10 minutes and gthumb doesn't pop up. It said it installed it, and when I type crontab -l, it shows them. What am I missing? I'm just trying to do some kind of a test to make sure I know how to use crontab, but I can't figure it out. It looks easy, but nothing works!

---

### Post by renkinjutsu on 2009-10-04
> **rob86 said:**
> I seem to be having some trouble with cron. I read about it, and I thought I understood what I was doing but it isn't working.

For testing purposes, I made a sh script that does echo 'Hello world' and then set up a cron to run it every minute to see if it works, but it doesn't seem to do anything. Here's what I'm seeing: First I test the script, then I set up a cron, well technically there are two, but that's because the first one didn't work so I tried another.


```
rob@desktop:~$ ~/myscript.sh
Hello World
rob@desktop:~$ crontab -l
# m h  dom mon dow   command
* * * * * ~/myscript.sh
*/1 * * * * ~/myscript.sh


```
try this..
```
* * * * * export DISPLAY=:1 && /usr/bin/gnome-terminal -e /home/user/myscript.sh
```
also.. if you script only does "echo" .. there's a good chance gnome-terminal will pop up, echo whatever you put in the script.. and then disappear.. you can add something like `sleep 3` at the end of your script to keep the script running (and the terminal open) long enough for you to know the cron's working.
> **rob86 said:**
> I get what you're saying lswb, but I still seem to be having problems just getting cron to do anything. I re-did my test crontab to run gthumb so it looks like this:

# m h  dom mon dow   command
* * * * * /usr/bin/gthumb
*/1 * * * * /usr/bin/gthumb

I wait and wait for 10 minutes and gthumb doesn't pop up. It said it installed it, and when I type crontab -l, it shows them. What am I missing? I'm just trying to do some kind of a test to make sure I know how to use crontab, but I can't figure it out. It looks easy, but nothing works!

and this..
```
* * * * * export DISPLAY=:1 && /usr/bin/gthumb
```
=]

---

### Post by rob86 on 2009-10-04
Hmm.. I copy/pasted that stuff and still nothing seems to be working, the myscript or the gthumb (and yes, it's installed and at that location!) Here's my script, and the crontab -l. Is it possible the cron daemon isn't running or something? 


```
rob@desktop:~$ cat /home/rob/myscript.sh
#!/bin/bash
echo 'Hello World'
sleep 5
rob@desktop:~$ crontab -l
* * * * * export DISPLAY=:1 && /usr/bin/gnome-terminal -e /home/rob/myscript.sh
* * * * * export DISPLAY=:1 && /usr/bin/gthumb

```

---

### Post by renkinjutsu on 2009-10-04
> **rob86 said:**
> Hmm.. I copy/pasted that stuff and still nothing seems to be working, the myscript or the gthumb (and yes, it's installed and at that location!) Here's my script, and the crontab -l. Is it possible the cron daemon isn't running or something? 


```
rob@desktop:~$ cat /home/rob/myscript.sh
#!/bin/bash
echo 'Hello World'
sleep 5
rob@desktop:~$ crontab -l
* * * * * export DISPLAY=:1 && /usr/bin/gnome-terminal -e /home/rob/myscript.sh
* * * * * export DISPLAY=:1 && /usr/bin/gthumb

```
waaahh!! blunder!
My mistake.. it should be ```
export DISPLAY=**:0**
```
my brain is shutting down...

---

### Post by rob86 on 2009-10-04
Wow it actually worked, what's the 0 mean in DISPLAY=:0 ? Active display? Default? :confused:

---

### Post by renkinjutsu on 2009-10-04
Yup .. that's the default active display..

If you want to start another X session, it must be in display 1 or after... so Not only do you have multiple workspaces, you can actually have multiple X sessions! .. i can't see any use other than to play fullscreen games

---

### Post by ermeyers on 2009-10-04
Also "at" for one-shot commands.

---

### Post by rob86 on 2009-10-04
Thanks for the help.

Could someone elaborate on "at" ? An example of how it's used, for example!

---

