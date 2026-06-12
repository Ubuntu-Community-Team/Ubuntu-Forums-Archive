---
title: "BASH: Problem capturing output from cfv"
date: 2010-08-08
forum: Programming Talk
---

### Post by User4519 on 2010-08-08
Hey all :)

Just migrated from KDE to Gnome, and I wanted to make the most of of the awesome nautilus-commands app to integrate some SFV creation context menu entries to nautilus, using cfv as the workhorse underneath.

I've done this with Konqueror previously, but back then it just started a background bash script which opened a KDialog in the end with the results. This time I'd like for it to be a little more awesome, so I'm using zenity to first allow me to select the type of checksum I want (using --radiolist), then select the filename for the checksum file (--file-selection), and the next part is to capture the progress output from cfv and feed it to zenity's --progress dialog.

Enter pipe hell. I simply cannot figure out how to capture the progress output from cfv. I initially wanted to capture the filename being processed and the progress (which is represented, for those who don't know cfv, by twenty characters, like "####\..............." - the backslash here is a "spinner" made from -, \, |, and / alternating to give constant feedback to the user. The #s show the current progress and the .s show what's left to be processed.

Okay, so I assembled a (not very pretty, but functional) sed command that can convert these lines to lines that can be fed into zenity, e.g. "# /home/daniel/testfile.tar.bz2\n15\n", but the thing is that I cannot make the output make it to sed. I did a lot of attempts and a lot of Googling (which is pretty difficult, considering how many "false positive" results you get searching for stuff like this ;) ).

I finally gave up on this output, figuring that i was probably because of some cursor control codes screwing up the pipe, due to the way the progress is constantly being written out to the tty.

So I decided to skip that progress and just make cfv do a verbose output without progress bar, which means that after each file it has finished processing, it'll print out a line like this,
```
/Batch1/Batch1.sfv : OK (f83db1e8)
```

And now I'm really getting stomped, because this I cannot capture either. The output disappears from the visible shell, so obviously some sort of redirection is going on, but I've now found that I can't get at any of the lines until cfv finished or is killed.

Example. Triggering in terminal window #1:
```
$ touch pipe
```

Then, terminal window #2:
```
$ tail -f pipe
```

Back to #1:
```
$ cfv --progress no -v -rr -L -C -p ./ -t sfv -f tistest.sfv * 2>&1 > pipe
```

In #2, immediately:
```
tail: pipe: file truncated
```

In #1 there is no output to the shell, I then do ctrl-c to kill cfv, and after a while (once it has finished the file it was working on when I sent ^C, I assume):
```
^CTraceback (most recent call last):
  File "/usr/bin/cfv", line 3, in <module>
    cfv.main()
  File "/usr/lib/pymodules/python2.6/cfv.py", line 2465, in main
    make(cftypes[typename],a,args)
  File "/usr/lib/pymodules/python2.6/cfv.py", line 2196, in make
    (filecrc,filesize),dat = dof(f)
  File "/usr/lib/pymodules/python2.6/cfv.py", line 1698, in make_addfile
    crc=hexlify(getfilecrc(filename)[0])
  File "/usr/lib/pymodules/python2.6/cfv.py", line 355, in getfilecrc
    finfo['crc'],finfo['size'] = _getfilecrc(file)
  File "/usr/lib/pymodules/python2.6/cfv.py", line 726, in _getfilecrc
    return _getfilechecksum(file, CRC32)
  File "/usr/lib/pymodules/python2.6/cfv.py", line 664, in _getfilechecksum
    m = hasher(dommap(f.fileno(), mmapsize))
  File "/usr/lib/pymodules/python2.6/cfv.py", line 716, in __init__
    self.value = _crc32(s)
KeyboardInterrupt
```

And then, BANG, in shell #2, I get all the output at once:
```
./$RECYCLE.BIN/S-1-5-21-1154372438-3869228711-277597537-1001/$ID8RNSI.srt : OK (95afdca4)
./$RECYCLE.BIN/S-1-5-21-1154372438-3869228711-277597537-1001/$RD8RNSI.srt : OK (45960c1b)
./$RECYCLE.BIN/S-1-5-21-1154372438-3869228711-277597537-1001/desktop.ini : OK (b2f9f22e)
./$RECYCLE.BIN/S-1-5-21-1732984049-2036620335-315254517-1001/desktop.ini : OK (b2f9f22e)
./$RECYCLE.BIN/S-1-5-21-4277130658-3462654387-2601481779-1001/desktop.ini : OK (b2f9f22e)
./$RECYCLE.BIN/S-1-5-21-576843801-2688154282-3896425139-1000/desktop.ini : OK (b2f9f22e)
./$RECYCLE.BIN/S-1-5-21-576843801-2688154282-3896425139-500/desktop.ini : OK (b2f9f22e)
./Batch1/Batch1.sfv : OK (f83db1e8)
./Batch1/sda1.ddimg : OK (18135beb)
```

I'm really puzzled by this. It seems as if the piped output is buffered until cfv has finished, but I don't know why. I mean, clearly these are individual lines, so there must be some newline characters here, right? And isn't the nature of piping that you can usually pick up each line as it comes through? Am I missing something really fundamental here?

I hope someone has some insight, because I'd really like for this script to work :)

---

