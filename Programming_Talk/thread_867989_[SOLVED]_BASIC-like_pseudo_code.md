---
title: "[SOLVED] BASIC-like pseudo code"
date: 2008-07-23
forum: Programming Talk
---

### Post by Krupski on 2008-07-23
Hi all,

I want to make a little shell script that does something like this (BASIC-like pseudo code):

while inkey$ = "" ' wait until a keypress
 cat /proc/something >> /tmp/listing
 sleep 0.1
wend

In other words, I want to send the contents of a constantly changing file (cpu speed, actually) to a file so that I can import it into a graphing program and look at CPU usage vs process loading.

I tried using 'watch' to repeatedly run 'cat' and redirect the output to a file (which worked) but the resulting file was full of ANSI control codes that I didn't want.

How would I make a shell script to do this? I can either have the script accept a keystroke to end it, or just make it an endless loop that I kill with ctrl-c.

I tried 'man bash' and got all confused... :(

Thanks in advance!

-- Roger

---

### Post by phidia on 2008-07-23
I'll bet there are people at the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39") who could address this. Maybe you can have a mod relocate this?
I think that there already is a gnome applet that does this too-I can't remember the name though and I'm not in my ubuntu install right now.

---

### Post by Krupski on 2008-07-23
> **phidia said:**
> I'll bet there are people at the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39") who could address this. Maybe you can have a mod relocate this?
I think that there already is a gnome applet that does this too-I can't remember the name though and I'm not in my ubuntu install right now.

I guess I should have mentioned that I want to do this in Ubuntu 64 bit SERVER (i.e. no Gnome or any GUI). It's gotta be a command line thing.

Thanks!

---

### Post by overdrank on 2008-07-23
Thread moved as requested by op :)

---

### Post by mssever on 2008-07-23
You could check out inotify, which will tell you when a file changes, then simply run the code to grab the new version every time you get a notification. A brute force approach might to repeatedly tail the file and look for changes.

---

### Post by Krupski on 2008-07-25
> **mssever said:**
> You could check out inotify, which will tell you when a file changes, then simply run the code to grab the new version every time you get a notification. A brute force approach might to repeatedly tail the file and look for changes.

Thanks for the suggestion. I did finally find what I was looking for here: [http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/loops1.html](http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/loops1.html)

...and I adapted a code snippet (about 2/3 down the page) to do what I needed. It worked fine:

```

# run for 5 minutes (10 * 60 * 5) = 3000
LIMIT=3000

for ((a=1; a <= LIMIT ; a++))
do
# write cpu speed to a file...
   cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq >> /tmp/cpu0speed.dat
   cat /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq >> /tmp/cpu1speed.dat
# ...10 times a second
   sleep 0.1
done

```


By the way, I had to run this script with bash (i.e. bash script-name) because 'sh' gave me an error.

(edit to add): This is what I was collecting the data for. I wanted to see what "conservative" and "ondemand" CPU speed governors performed like. The task I ran to test it was to 'gzip' a 4 gig file into a resulting 700-some megabyte compressed file. I applied a "backbone" fit to the data and a 50 sample walking window to smooth out the data (to remove rapid up-down spikes). The difference between the two governors is interesting. Obviously, I didn't bother to graph "powersave" or "performance" since these are just flatline graphs!  :)

Here are links to the graph images:

[Conservative]("http://users.adelphia.net/~krupski/images/conservative.jpg") 

[Ondemand]("http://users.adelphia.net/~krupski/images/ondemand.jpg")



-- Roger

---

### Post by mssever on 2008-07-27
> **Krupski said:**
> ```
for ((a=1; a <= LIMIT ; a++))
# ...
```
By the way, I had to run this script with bash (i.e. bash script-name) because 'sh' gave me an error. I'm pretty sure that the double parentheses is a bashism. At any rate, on Debian-derived systems, sh is dash, not bash. There are a few areas where you have to use sh (mostly in certain boot scripts). With that exception, you should always use bash; it's installed on virtually every *nix system these days (and every Linux system), so the portability argument for using sh is moot these days. Since bash offers some additional features not in sh or dash, you might as well use bash.

> Here are links to the graph images:

[Conservative]("ftp://69.207.19.109/public/conservative.jpg") 

[Ondemand]("ftp://69.207.19.109/public/ondemand.jpg")
These links point to an FTP location which requires a password that I don't know.

---

### Post by Krupski on 2008-07-27
> **mssever said:**
> I'm pretty sure that the double parentheses is a bashism. At any rate, on Debian-derived systems, sh is dash, not bash. There are a few areas where you have to use sh (mostly in certain boot scripts). With that exception, you should always use bash; it's installed on virtually every *nix system these days (and every Linux system), so the portability argument for using sh is moot these days. Since bash offers some additional features not in sh or dash, you might as well use bash.


These links point to an FTP location which requires a password that I don't know.

Your browser's "anonymous" should work... although I've been working on the server and it may have been down when you tried. Sorry... :(

(edit to add): Moved the images to a different server - you should be able to see them now. Sorry for the grief.

-- Roger

---

