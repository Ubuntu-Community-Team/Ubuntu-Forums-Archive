---
title: "xsession-errors and 'low graphics mode'?"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by premier.renz on 2014-08-13
im new to ubuntu and i encountered this xsession-errors file to eat most of the hard drive space. how do i get rid of this? and now i cant even log in because another error prompted "your system is running on low graphics mode". 

and another thing, what does the "mounting your hard drive from read to read-only"? ive seen this when ive tried the recovery but i didn't continue because im afraid it will mess up the data on the hard drive.

please help asap.


thanks

---

### Post by premier.renz on 2014-08-13
is it ridiculous? sorry i really have no idea what xsession-errors is, im new to ubuntu. can you help me?

---

### Post by grahammechanical on 2014-08-13
When the file system or hard disk partition is Read Only it means that the files on the partition can be read but not edited. OS system files are also read only to stop us editing them and breaking the OS.

To write changes to the hard disk we need the file system to be in Read/Write mode. Then we can install software and we can save any files we edit.

So, if we use Recovery mode to update Ubuntu or to edit system files to fix problems we need to put the file system into read/write mode. Some of the options in the recovery menu do that because those options would not be able to do their work if the file system was in Read Only mode.

Regards.

---

### Post by premier.renz on 2014-08-13
> **grahammechanical said:**
> When the file system or hard disk partition is Read Only it means that the files on the partition can be read but not edited. OS system files are also read only to stop us editing them and breaking the OS.

To write changes to the hard disk we need the file system to be in Read/Write mode. Then we can install software and we can save any files we edit.

So, if we use Recovery mode to update Ubuntu or to edit system files to fix problems we need to put the file system into read/write mode. Some of the options in the recovery menu do that because those options would not be able to do their work if the file system was in Read Only mode.

Regards.

thanks for the reply grahammechanical. enlightened me a bit. so, there's nothing will happen to the data on the hard drive if i mount it as read/write? im going to try the failsafeX options on the recovery menu.

---

### Post by deadflowr on 2014-08-13
You might get better help if you post the xsession-errors output.
If it is *really huge*, then try [pastebinit]("https://help.ubuntu.com/community/Pastebinit").

It is hard to decipher any one particular reason for it being so big.
Each instance of xsession-errors can be vastly different from another.

First though, you might want to clear out the old xession-errors.old file, so that you still have some space left.
(Each session starts a new file, the old one should be called xsession-errors.old.)

Or perhaps keep it and login via ctrl+alt+F2(tty2 this will log you in via a simple command line console, no gui. also means no xsession running)
and install pastebinit  and then run something like
```
cat $HOME/.xsession-errors | pastebinit
```
or
```
cat $HOME/.xsession-errors.old | pastebinit
```
copy the url(s) and post a link.

Only then can we tell what's what.

From that point maybe something can be found to fix the problem.

---

### Post by oldos2er on 2014-08-14
> **premier.renz said:**
> im new to ubuntu and i encountered this xsession-errors file to eat most of the hard drive space. how do i get rid of this? and now i cant even log in because another error prompted "your system is running on low graphics mode". 

.xsession-errors is an error log containing info on your current X session; think of X as GUI, it's the software that creates the GUI essentially. Since you seem to be having a related problem with low graphics mode, it would be useful to post your video card make/model, any proprietary video drivers in use, and your Ubuntu version.

I've changed your thread title to better reflect your question.

---

### Post by premier.renz on 2014-08-17
> **deadflowr said:**
> You might get better help if you post the xsession-errors output.
If it is *really huge*, then try [pastebinit]("https://help.ubuntu.com/community/Pastebinit").

It is hard to decipher any one particular reason for it being so big.
Each instance of xsession-errors can be vastly different from another.

First though, you might want to clear out the old xession-errors.old file, so that you still have some space left.
(Each session starts a new file, the old one should be called xsession-errors.old.)

Or perhaps keep it and login via ctrl+alt+F2(tty2 this will log you in via a simple command line console, no gui. also means no xsession running)
and install pastebinit  and then run something like
```
cat $HOME/.xsession-errors | pastebinit
```
or
```
cat $HOME/.xsession-errors.old | pastebinit
```
copy the url(s) and post a link.

Only then can we tell what's what.

From that point maybe something can be found to fix the problem.


ive managed to log in via tt2, but how do i install the pastebinit? and another thing, ive tried the failsafex on the recovery menu but nothing happens. the low on graphics mode still prompting. thanks


> **oldos2er said:**
> .xsession-errors is an error log containing info on your current X session; think of X as GUI, it's the software that creates the GUI essentially. Since you seem to be having a related problem with low graphics mode, it would be useful to post your video card make/model, any proprietary video drivers in use, and your Ubuntu version.

I've changed your thread title to better reflect your question.

thanks oldo. how do i find out the videocard make/model? i can only login via tt2. im not really familiar with the ubuntu server, hope u guys would help me. btw is there i can free-up/delete the xsession-errors file through the console? when i log in via the tt2, i saw that the hard drive space usage is at 100%. maybe if im able to free-up some space i could log in

---

### Post by steeldriver on 2014-08-17
You can install pastebinit from the CLI using

```

sudo apt-get update
sudo apt-get install pastebinit

```

Once it's installed,

```

sudo lshw -sanitize | pastebinit

```

and then copy the generated URL. Similarly for your .xsession-errors file

```

pastebinit -i ~/.xsession-errors

```

although **if it's GB big it would probably be polite to post just the most recent portion** e.g.

```

tail -n 1000 ~/.xsession-errors | pastebinit

```

You can free up the space by removing (using rm) or truncating the file e.g.

```

> ~/.xsession-errors

```

but let's not do that until we know what your xsession is complaining about.

---

### Post by premier.renz on 2014-08-17
> **steeldriver said:**
> You can install pastebinit from the CLI using

```

sudo apt-get update
sudo apt-get install pastebinit

```

Once it's installed,

```

sudo lshw -sanitize | pastebinit

```

and then copy the generated URL. Similarly for your .xsession-errors file

```

pastebinit -i ~/.xsession-errors

```

although **if it's GB big it would probably be polite to post just the most recent portion** e.g.

```

tail -n 1000 ~/.xsession-errors | pastebinit

```

You can free up the space by removing (using rm) or truncating the file e.g.

```

> ~/.xsession-errors

```

but let's not do that until we know what your xsession is complaining about.

Thanks steeldriver, ill try that tomorrow and will post here what will happen. thanks again

---

### Post by JKyleOKC on 2014-08-17
If your disk usage is sitting at 100% already, you won't be able to follow steeldriver's advice to install pastebinit. You'll need to make a little space first, and that can be a bit tricky to do without destroying clues that can help us solve the original problem.

Try this to get a listing of all the files that begin with ".x" and tell us what they are together with their sizes: ```
ls -la | grep \.x.*
``` Those are lower-case "L" characters, not numeral "1"s. The "ls -la" will list all the files in your current directory and the "grep" command will filter out all the results except those containing ".x" followed by anything else. This will, hopefully, let us suggest a file or two that you can delete to get enough space to then do as steeldriver suggests.

---

### Post by oldos2er on 2014-08-17
> **premier.renz said:**
> thanks oldo. how do i find out the videocard make/model? 

```
lspci | grep VGA
```

---

### Post by premier.renz on 2014-08-17
> **JKyleOKC said:**
> If your disk usage is sitting at 100% already, you won't be able to follow steeldriver's advice to install pastebinit. You'll need to make a little space first, and that can be a bit tricky to do without destroying clues that can help us solve the original problem.

Try this to get a listing of all the files that begin with ".x" and tell us what they are together with their sizes: ```
ls -la | grep \.x.*
``` Those are lower-case "L" characters, not numeral "1"s. The "ls -la" will list all the files in your current directory and the "grep" command will filter out all the results except those containing ".x" followed by anything else. This will, hopefully, let us suggest a file or two that you can delete to get enough space to then do as steeldriver suggests.

JkyleOKC, ive tried the ls -la | grep \.x.* command and i saw results; some of it is in red font color. how do i copy them? so i can post the results here. thanks

---

### Post by premier.renz on 2014-08-17
> **oldos2er said:**
> ```
lspci | grep VGA
```

Oldo, here's the videocard details ive found:

Matrox Graphics, Inc. MGA G200eW WPCM450 (rev 0a)


Thanks

---

### Post by JKyleOKC on 2014-08-17
> **premier.renz said:**
> JkyleOKC, ive tried the ls -la | grep \.x.* command and i saw results; some of it is in red font color. how do i copy them? so i can post the results here. thanksOne of the simplest ways is probably to take a photo of the screen and attach it to a message in this thread. I've seen that done fairly often when the problem makes it impractical or impossible to do a totally machine-readable capture.

Programs for doing screen captures are built into some versions of *buntu but I don't know whether there's one in yours, or whether there's any space left on your system to allow it. You can try using the Print-Screen key on your keyboard, when the result is displayed, and if the capability is there that will either put the capture into your clipboard, or bring up a dialog asking you what to do with it. You can get it into the clipboard from the dialog, and then paste it into a reply here.

The red characters, which are probably the ".x" at the start of each displayed line, are simply indicating that they were what you had grep searching for. They don't indicate problems as red often does...

EDIT-- I'm about to pull out for the evening but Ann (oldos2er) can certainly pick up my side of the conversation and keep feeding you suggestions!

---

### Post by premier.renz on 2014-08-17
> **JKyleOKC said:**
> One of the simplest ways is probably to take a photo of the screen and attach it to a message in this thread. I've seen that done fairly often when the problem makes it impractical or impossible to do a totally machine-readable capture.

Programs for doing screen captures are built into some versions of *buntu but I don't know whether there's one in yours, or whether there's any space left on your system to allow it. You can try using the Print-Screen key on your keyboard, when the result is displayed, and if the capability is there that will either put the capture into your clipboard, or bring up a dialog asking you what to do with it. You can get it into the clipboard from the dialog, and then paste it into a reply here.

The red characters, which are probably the ".x" at the start of each displayed line, are simply indicating that they were what you had grep searching for. They don't indicate problems as red often does...

EDIT-- I'm about to pull out for the evening but Ann (oldos2er) can certainly pick up my side of the conversation and keep feeding you suggestions!

here's the result:

[IMG]http://imagizer.imageshack.us/v2/280x200q90/539/WU9rZR.jpg[/IMG]

---

### Post by premier.renz on 2014-08-18
i saw these on the xserver log file

[IMG]http://imagizer.imageshack.us/v2/280x200q90/673/Ou7bZX.jpg[/IMG][IMG]http://imagizer.imageshack.us/v2/280x200q90/661/NltTSz.jpg[/IMG][IMG]http://imagizer.imageshack.us/v2/280x200q90/540/p95B43.jpg[/IMG][IMG]http://imagizer.imageshack.us/v2/280x200q90/661/7mGYJ8.jpg[/IMG][IMG]http://imagizer.imageshack.us/v2/280x200q90/538/dDyv9x.jpg[/IMG][IMG]http://imagizer.imageshack.us/v2/280x200q90/661/h5A7PL.jpg[/IMG][IMG]http://imagizer.imageshack.us/v2/280x200q90/661/LLTOnX.jpg[/IMG][IMG]http://imagizer.imageshack.us/v2/280x200q90/905/58IHhC.jpg[/IMG]

---

### Post by premier.renz on 2014-08-18
[IMG][[IMG]http://imagizer.imageshack.us/v2/280x200q90/537/PlFFMX.jpg[/IMG]]("http://imageshack.com/f/exPlFFMXj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/674/nrkbby.jpg[/IMG]]("http://imageshack.com/f/iqnrkbbyj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/745/p9VqPX.jpg[/IMG]]("http://imageshack.com/f/kpp9VqPXj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/912/woUVZ2.jpg[/IMG]]("http://imageshack.com/f/pcwoUVZ2j") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/674/mu9Dxi.jpg[/IMG]]("http://imageshack.com/f/iqmu9Dxij") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/673/pWjPU2.jpg[/IMG]]("http://imageshack.com/f/ippWjPU2j") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/673/hO7FWR.jpg[/IMG]]("http://imageshack.com/f/iphO7FWRj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/539/ibLWkw.jpg[/IMG]]("http://imageshack.com/f/ezibLWkwj") [/IMG]

---

### Post by premier.renz on 2014-08-18
[[IMG]http://imagizer.imageshack.us/v2/280x200q90/674/Dfd3GF.jpg[/IMG]]("http://imageshack.com/f/iqDfd3GFj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/539/gicu0O.jpg[/IMG]]("http://imageshack.com/f/ezgicu0Oj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/538/D8FtQQ.jpg[/IMG]]("http://imageshack.com/f/eyD8FtQQj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/539/uDSk5N.jpg[/IMG]]("http://imageshack.com/f/ezuDSk5Nj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/913/c8VTs7.jpg[/IMG]]("http://imageshack.com/f/pdc8VTs7j") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/742/ruADCk.jpg[/IMG]]("http://imageshack.com/f/kmruADCkj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/540/yxlRhc.jpg[/IMG]]("http://imageshack.com/f/f0yxlRhcj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/674/MwIb1k.jpg[/IMG]]("http://imageshack.com/f/iqMwIb1kj")

---

### Post by premier.renz on 2014-08-18
[[IMG]http://imagizer.imageshack.us/v2/280x200q90/538/FmGQMR.jpg[/IMG]]("http://imageshack.com/f/eyFmGQMRj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/540/hzQtRl.jpg[/IMG]]("http://imageshack.com/f/f0hzQtRlj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/902/cjY6sN.jpg[/IMG]]("http://imageshack.com/f/p2cjY6sNj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/902/MdK09a.jpg[/IMG]]("http://imageshack.com/f/p2MdK09aj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/538/l02QjI.jpg[/IMG]]("http://imageshack.com/f/eyl02QjIj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/905/58IHhC.jpg[/IMG]]("http://imageshack.com/f/p558IHhCj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/661/LLTOnX.jpg[/IMG]]("http://imageshack.com/f/idLLTOnXj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/661/h5A7PL.jpg[/IMG]]("http://imageshack.com/f/idh5A7PLj")

---

### Post by premier.renz on 2014-08-18
[[IMG]http://imagizer.imageshack.us/v2/280x200q90/538/dDyv9x.jpg[/IMG]]("http://imageshack.com/f/eydDyv9xj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/661/7mGYJ8.jpg[/IMG]]("http://imageshack.com/f/id7mGYJ8j") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/540/p95B43.jpg[/IMG]]("http://imageshack.com/f/f0p95B43j") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/661/NltTSz.jpg[/IMG]]("http://imageshack.com/f/idNltTSzj") [[IMG]http://imagizer.imageshack.us/v2/280x200q90/673/Ou7bZX.jpg[/IMG]]("http://imageshack.com/f/ipOu7bZXj")

btw, may i just reinstall the ubuntu os without affecting the data on the hdd?

---

### Post by premier.renz on 2014-08-18
another thing, is it safe to delete the lightdm.log.1 file? i saw it earlier when im connected to the server via ftp. it eats a lot of space (194GB).

---

### Post by JKyleOKC on 2014-08-18
> **premier.renz said:**
> another thing, is it safe to delete the lightdm.log.1 file? i saw it earlier when im connected to the server via ftp. it eats a lot of space (194GB).I believe that one would be safe to delete, and doing so would give you plenty of space to follow steeldriver's original suggestions afterward.

You may need to "empty trash" after doing the delete, but since you are working from the command prompt rather than a desktop the effect of "rm" should be immediate rather than simply moving the file to a "trash" area. Be very careful when you type the command. This is one where an accidental extra space in the wrong place can destroy your system with no recovery possible!

When using "rm" my preferred technique is to first uuse "cd" to get to the exact directory that holds the file I'm going to remove, then type "ls" followed by a space and the first few characters of the file's name, followed by the TAB key. The system then fills in the rest of the name, and I hit ENTER to launch the command. This will list all the files that would be removed, which should be only the one I want to get rid of. I then use the history feature by pressing the up-arrow key to recall the previous command, press HOME to get the cursor to the front of the line, and replace "ls" with "rm" before hitting ENTER to do the actual deletion.

Sounds like the very long way around, but it confirms that I've not made any fat-fingered mistake that would take out the wrong file or even my entire system.

I wasn't able to read the content of your log; couldn't enlarge the photos enough for my ancient eyesight. After you get rid of the lightdm log file and get almost 200 GB back you can install pastebinit as described earlier in the thread and we can get the full file in machine-readable form.

---

