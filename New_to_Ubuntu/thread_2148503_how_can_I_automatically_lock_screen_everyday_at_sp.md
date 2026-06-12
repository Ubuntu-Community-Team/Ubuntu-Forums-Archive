---
title: "how can I automatically lock screen everyday at specific times?"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by TooFreppaT on 2013-05-25
how can I automatically lock my desktop at pre-specified specific times everyday?

---

### Post by newb85 on 2013-05-25
The command 
```
gnome-screensaver-command -l
```
locks the screen.

You could probably incorporate that into crontab.  (There's plenty of documentation on crontab, so do a little searching...)

---

### Post by papibe on 2013-05-25
Hi TooFreppaT.

This would be the command you need to run:
```
gnome-screensaver-command -l
```
IMHO, the easiest way to automate the process would be to use cron.

To edit your crontab run this:
```
crontab -e
```
This entry would lock your screen every minute (good for testing):
```
*/1 * * * * DISPLAY=:0 gnome-screensaver-command -l
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by lethall1 on 2013-05-25
[FONT=Ubuntu Mono]```
gnome-screensaver-command -l
``` + crontab -e

i forgot to refresh my page )[/FONT]

---

### Post by TooFreppaT on 2013-05-25
thankyou for your replies :D
> **papibe said:**
> This entry would lock your screen every minute (good for testing):
```
*/1 * * * * DISPLAY=:0 gnome-screensaver-command -l
```

I found this [help.ubuntu.com/community/CronHowto#GUI_Applications]("https://help.ubuntu.com/community/CronHowto#GUI_Applications")

I wanted to find out more about the commands but from the link the only thing I can't understand is [FONT=courier new]env DISPLAY=:0[/FONT] and why you didn't use [FONT=courier new]env[/FONT] in yours

---

### Post by papibe on 2013-05-25
A few thoughts:
[LIST]
[*]The cron environment is very efficient, but limited, so you need to include the variable DISPLAY in order to run GUI apps.
[*]**:0** is the reference to the default display and it will work on most cases.
[*]When you have 2 monitors the syntax changes. **:0.0** would reference the first one, and **:0.1** the second one.
[*]In the context of you want to do, either:
```
env DISPLAY=:0 cmd

DISPLAY=:0 cmd
```
produces the same result: modifiy the environment in which the command 'cmd' will run.


[*]The command 'env' is a much powerful way to do that. For instance, you can set several variables:
```
env  PATH=/path/to/special/library:$PATH  DISPLAY=:0.1  cmd
```
(that would modify the environment in which 'cmd' would run by adding an extra directory to the path, and set to run on the 2nd monitor).
[/LIST]
Does that help?
Regards.

---

### Post by TooFreppaT on 2013-05-25
Thank you very much. :D

If I could marke this as solved then I would but I can't find it anymore. ](*,)

---

### Post by papibe on 2013-05-25
> **TooFreppaT said:**
> Thank you very much. :D
Glad I could help :)
> **TooFreppaT said:**
> If I could marke this as solved then I would but I can't find it anymore. ](*,)
It hasn't been set yet. [Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it for now.

Regards.

---

### Post by newb85 on 2013-05-25
> **papibe said:**
> Glad I could help :)

It hasn't been set yet. [Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it for now.

Regards.

I get the impression that a lot of threads are going without being marked as solved because the only way to do it is a not-so-obvious workaround.  Seems like it should be more of a priority...  But then, I know nothing about managing the format of a forum site.

---

### Post by timjavins on 2013-05-26
Awesome. I love that it doesn't take much to do custom things like this in Ubuntu.

---

### Post by TooFreppaT on 2013-05-26
```
TooFreppaT@TooFreppaT:~$ crontab -e
no crontab for TooFreppaT - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/vim.tiny

Choose 1-3 [2]: 
```

I'm not sure if this is important. Should I select number 2 and [COLOR=#ff0000]how will I change this afterwards?[/COLOR]

Okay I have selected number 2 and noticed this
```
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
```
Since I haven't been asked for a email, what will it do otherwise? and how can I set the email? [COLOR=#008000]Okay I have found out to p[/COLOR][COLOR=#008000]ut [[FONT=courier new]MAILTO=""[/FONT]]("http://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/") at the [/COLOR][COLOR=#008000]top of my file.[/COLOR]

 [COLOR=#ff0000]Now I am looking for a way to redirect the unsent email into a file on my Desktop.
I am not sure[/COLOR][COLOR=#ff0000] what [/COLOR][COLOR=#ff0000][FONT=courier new]MAILTO=root[/FONT][/COLOR][COLOR=#ff0000] will do and unsure about if [FONT=courier new]MAILTO=Desktop[/FONT] would even work at all.[/COLOR]

---

### Post by Impavidus on 2013-05-27
The output send to the e-mail address is the standard output+standard error of the command. If you make sure the command doesn't produce any or if you redirect the output to a log file, no e-mail will be send. You can use normal shell redirects.

---

### Post by papibe on 2013-05-27
> **TooFreppaT said:**
> ```
how will I change this afterwards?
You can run the menu that allows you to select the default command line editor by running:
[CODE]select-editor
```
Regards.

---

