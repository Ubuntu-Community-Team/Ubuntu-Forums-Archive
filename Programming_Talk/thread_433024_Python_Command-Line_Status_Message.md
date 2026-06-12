---
title: "Python Command-Line Status Message"
date: 2007-05-04
forum: Programming Talk
---

### Post by pointone on 2007-05-04
Hi, all!

I've been working on a Python script which renames audio files in the current directory based on their ID3 tag information. I'd like this script to show some sort of progress indication.

At the moment, I have a for loop set up to complete the renaming tasks on each file in the specified directory, and have a basic progress indicator using sys.stdout.write:

```
        for f in fileList:
            count += 1
            
            do_work(f)
            
            message = "Renamed %d of %d" % (count, total)
            sys.stdout.write("\b" * 30)
            sys.stdout.write(message)
```

This code writes the message "Renamed 5 of 140", for example, and updates itself for each iteration, but I'm not happy with the method here: writing backspace characters.

By using backspace characters, the message is updated in-line, but this also causes the cursor to flash over the text each iteration (each rename takes about a tenth of a second, so this flashing is somewhat distracting). 

To cut a long story short, I was wondering if anyone could suggest a better method to accomplish this, or if there were some way to disable the cursor, perhaps?

Thanks in advance!

---

### Post by WW on 2007-05-04
I don't know if this will make a difference, but instead of printing a bunch of '\b' characters, you could print '\r'.  That is, replace these two lines
```

            sys.stdout.write("\b" * 30)
            sys.stdout.write(message)

```
with
```

            sys.stdout.write('\r' + message)

```

---

