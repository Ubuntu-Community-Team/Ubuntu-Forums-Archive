---
title: "Script to pause torrent downloads while browsing."
date: 2012-02-19
forum: New to Ubuntu
---

### Post by mayur.shetye on 2012-02-19
I was wondering if there is any script by which the torrent downloads will pause while I start browsing the web (because it decreases my browsing speed).I have ubuntu 11.10 and use Deluge. 
One of the ways I thought this could be  done is as follows:
When firefox or chrome is opened deluge will pause the torrent downloads and will resume them when they are closed.   
I have absolutely no idea how to implement this.So,I request the pros to help! :)

---

### Post by TeoBigusGeekus on 2012-02-19
Try with this:
```
#!/bin/bash
kill -STOP $(pidof deluge)
command_to_launch_your_browser
kill -CONT $(pidof deluge)
```
It pauses deluge, launches your browser and resumes deluge after you quit.

---

### Post by mayur.shetye on 2012-02-19
I tried this script.It opens my browser but does not have any effect on deluge.Deluge continues to download.
Also,when I run it in terminal I get this:
 **kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]**

---

### Post by TeoBigusGeekus on 2012-02-19
Open deluge and post the output of
```
ps aux|grep deluge
```

---

### Post by mayur.shetye on 2012-02-19
```
mayur    11527  1.0  3.3 178176 43016 ?        Sl   21:59   0:38 /usr/bin/python /usr/bin/deluge-gtk
mayur    11542  1.5  1.4  62688 19236 ?        Tl   22:00   0:54 /usr/bin/python /usr/bin/deluged --port=58846 --config=/home/mayur/.config/deluge
mayur    14000  0.0  0.0   4448   792 pts/0    S+   22:59   0:00 grep --color=auto deluge

```
That's the output.
By the way,I replaced 'pidof deluge' with 'pgrep deluged' in the script you gave.Then it seems to work fine.
However,I used system monitor-->Resources-->Network and found that deluged continues to receive data for about 30 secs(approx).But then evrything works smoothly after some time.

---

### Post by TeoBigusGeekus on 2012-02-19
> **mayur.shetye said:**
> ```
mayur    11527  1.0  3.3 178176 43016 ?        Sl   21:59   0:38 /usr/bin/python /usr/bin/deluge-gtk
mayur    11542  1.5  1.4  62688 19236 ?        Tl   22:00   0:54 /usr/bin/python /usr/bin/deluged --port=58846 --config=/home/mayur/.config/deluge
mayur    14000  0.0  0.0   4448   792 pts/0    S+   22:59   0:00 grep --color=auto deluge

```
That's the output.
By the way,I replaced 'pidof deluge' with 'pgrep deluged' in the script you gave.Then it seems to work fine.
However,I used system monitor-->Resources-->Network and found that deluged continues to receive data for about 30 secs(approx).But then evrything works smoothly after some time.

You stop the deluge demon - you could have used deluge-gtk as well.

---

### Post by mayur.shetye on 2012-02-19
Now the final script is :
```
#!/bin/bash
kill -STOP 11542
google-chrome
kill -CONT 11542
```
There are two minor problems though,
i)Now,I have made arrangements to run the script when I click the chrome launcher.But everytime it gives a dialog box showing the options 'run in terminal,display,cancel,run'.Is it possible to 'run' the script directly without the dialog box showing?
ii)It takes deluged some time to completely stop downloading.

---

### Post by TeoBigusGeekus on 2012-02-19
> **mayur.shetye said:**
> Now the final script is :
```
#!/bin/bash
kill -STOP 11542
google-chrome
kill -CONT 11542
```
There are two minor problems though,
i)Now,I have made arrangements to run the script when I click the chrome launcher.But everytime it gives a dialog box showing the options 'run in terminal,display,cancel,run'.Is it possible to 'run' the script directly without the dialog box showing?
ii)It takes deluged some time to completely stop downloading.

No, don't use that.
The pid of deluge will change every time you use it - use $(pidof deluge-gtk) instead.

---

### Post by mayur.shetye on 2012-02-19
Ok. And how do I disable the dialog box from showing everytime? :p

---

### Post by TeoBigusGeekus on 2012-02-19
I don't know about that - must be an ubuntu thing (I use a different distro).
Isn't there a something like "Remember choice" tickbox?

---

### Post by mayur.shetye on 2012-02-19
There is 'open with other application' option.But I dont know which application to use.

---

### Post by TeoBigusGeekus on 2012-02-19
> **mayur.shetye said:**
> There is 'open with other application' option.But I dont know which application to use.

A text editor for editing it - don't worry about that.

---

### Post by mayur.shetye on 2012-02-19
Ok.Thanks a lot for your help. :)
I'll mark the thread as solved.

---

### Post by mayur.shetye on 2012-02-20
Update:
I use this script now.. Instead of pausing the daemon it just pauses the torrents and resumes them on exiting chrome.
```
#!/bin/bash
deluge-console "pause *";
google-chrome
deluge-console "resume *";
```

---

