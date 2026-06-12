---
title: "cannot run commands in Terminal"
date: 2017-06-05
forum: New to Ubuntu
---

### Post by pjstock on 2017-06-05
I am a pretty avid Ubuntu user. It's just that when I have to go beyond the GUI (I think it is called) and venture into Terminal, I am pretty helpless if things do not go exactly as the instructions describe.

I am trying to install a wifi Brother printer and that seems to require me "running" the Install Tool which I have downloaded and parked in a separate directory.
But I cannot seem to get TO that directory.

when I enter Terminal and try to CD to the subdirectory, I get an error (or reply):

"peter@CollierDesk:~$ cd downloads
bash: cd: downloads: No such file or directory"

and in fact no commands seem to work.

what am I doing wrong?

---

### Post by howefield on 2017-06-05
Linux needs the correct case for the commands, 

```
cd Downloads
```

is probably what you are looking for, if that doesn't work try

```
cd ~/Downloads
```

---

### Post by pjstock on 2017-06-05
ahhhah. That was pretty dumb of me. now I'll try to remember that.

If I can press on...
the printer install instructions say:
" Step3. Enter this command to extract the downloaded file:
Command: gunzip linux-brprinter-installer-*.*.*-*.gz"

But when I do I get an error.

"peter@CollierDesk:~/Downloads/tmp$ gunzip linux-brprinter-installer-*.*.*-*.gz
gzip: linux-brprinter-installer-*.*.*-*.gz: No such file or directory"

even though I think I have the required file correctly downloaded and in the right place.
"peter@CollierDesk:~/Downloads/tmp$ dir
linux-brprinter-installer-2.1.1-1"

---

### Post by oldrocker99 on 2017-06-05
Use a file mananger, open the directory where the .gz file is and right-click it and choose **Extract Here**. It will extract a text file, which you will run thus:
```
sudo sh brother-printer-installer[whatever].sh
```

You'll be asked for the model number of your printer, and it'll ask for an IP address, which you can get your Brother printer to print out. It works like a charm for my 3170-CDW.

---

### Post by pjstock on 2017-06-05
thank you.

so I think I have now extracted the file correctly.
it seems to be called: linux-brprinter-installer-2.1.1-1

but when I try your suggested command (modified as I think it has to be to match this actual file name) I get an error.

peter@CollierDesk:~/Downloads/tmp$ sudo sh linux-brprinter-installer-2.1.1-1.sh
sh: 0: Can't open linux-brprinter-installer-2.1.1-1.sh
peter@CollierDesk:~/Downloads/tmp$

I must be screwing something up.

Oppps. might have sorted it.
I tried

sudo bash linux-brprinter-installer-2.1.1-1 HL-3070CW 
and it seems to be doing something.

---

### Post by howefield on 2017-06-05
Why are you putting .sh at the end if the file name is linux-brprinter-installer-2.1.1-1 ? 

Try..

```
sudo sh linux-brprinter-installer-2.1.1-1
```

A little tip is to use autocomplete, type a few characters and then press the tab key and the filename should automcomplete.

Edit : ok, posted simultenously there.

---

### Post by pjstock on 2017-06-05
Hmmm, well I got most of the way through this. When I specify the URI it seems to print a test page but I think that is via Ethernet. I still cannot figure out the Wifi setup. I might throw this back over to my Printer Setup post.
but thank you for your help on all this.
Peter

someone above gave me a command to try that seemed to include the .sh
Like I said, I am so clueless that all I can do is follow instructions.

anyway, "sudo bash linux-brprinter-installer-2.1.1-1 HL-3070CW" seems to install something. and when I specific the IP Address 192.168.3.109 it allows me to print a test page with the Ethernet attached. but not when it is just on wifi 

I'll try your command. who knows?

---

