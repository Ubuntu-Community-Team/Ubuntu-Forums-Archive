---
title: "add actual date to begin of every saved line"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by gam01hr on 2013-02-08
Hello ,

I'm trying make small and dirty datalogger.
My Arduino board sends every second ASCII string like this:
"001,002,003,004\n"  The numbers are decimal values from AD channels 1 to 4.
On the PC runs simple command which saves data to a file. This one works fine for me:
[COLOR=Green]
$ cat /dev/ttyacm0 | tee logfile.txt[/COLOR]

 
Now I would like to add actual date to begin of every saved line. Like this:
[COLOR=Green]
$ date +%H:%M:%S[/COLOR]

Please is there a simple way how to do it on command line?
Or do I need write python script?
Thank you...

---

### Post by Hadaka on 2013-02-08
Hi this might work.

```
 [COLOR=Green]cat /dev/ttyacm0 | sed "s/^/ ` date ` / " >> logfile.txt[/COLOR]
```

---

### Post by steeldriver on 2013-02-08
Hmm... I wonder if the date will only get expanded one time (when the command is first run) rather than each time a substitution is made? Maybe a bash 'read' would work though?

I don't have a special file / device that I can test this with, so this reads from a process using 'sleep' to delay the lines of input:-

```
$ sed "s/^/$(date '+%H:%m:%S') /" < <(for i in {1..6}; do echo line ${i}; sleep 2; done)
22:02:26 line 1
22:02:26 line 2
22:02:26 line 3
22:02:26 line 4
22:02:26 line 5
22:02:26 line 6

```whereas```
$ while read -r line; do echo $(date '+%H:%m:%S') "$line"; done < <(for i in {1..6}; do echo line ${i}; sleep 2; done)
22:02:56 line 1
22:02:58 line 2
22:02:00 line 3
22:02:02 line 4
22:02:04 line 5
22:02:06 line 6

```

---

### Post by sgy on 2013-02-09
Have you tried something simpler like this?

```

[COLOR=Green]date >> logfile.txt && cat /dev/ttyacm0 | tee -a logfile.txt[/COLOR]

```The date will be on a different line than the data, but it's close.

It's probably not hard to remove the new line character after the date.

---

### Post by gam01hr on 2013-02-19
Hello,
Thank you for your advices. I have got good result with this:
```

pi@raspberrypi ~ $ while read line; do echo -e "$line $(date '+%H:%m:%S')"; done < /dev/ttyUSB0
111,0,0,0,0,0,0 23:02:13
111,0,0,0,0,0,0 23:02:14
111,0,0,0,0,0,0 23:02:15
^C

```but if I exchange the position of $(date) and $line, the date is printed only one time
```

pi@raspberrypi ~ $ while read line; do echo -e "$(date '+%H:%m:%S') $line"; done < /dev/ttyUSB0
23:02:25 111,0,0,0,0,0,0
111,0,0,0,0,0,0
111,0,0,0,0,0,0
111,0,0,0,0,0,0
^C

```here is the know-how source: [http://en.kioskea.net/faq/1757-how-to-read-a-file-line-by-line](http://en.kioskea.net/faq/1757-how-to-read-a-file-line-by-line)

---

