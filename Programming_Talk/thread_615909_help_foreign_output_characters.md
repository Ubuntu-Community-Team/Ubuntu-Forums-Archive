---
title: "help foreign output characters"
date: 2007-11-17
forum: Programming Talk
---

### Post by opakedragon on 2007-11-17
ok so I am currently trying to brush up on my programming and I pretty much know how to use g++ but My computer got unplugged while I was working (I also happened to be using pdfcrack but only my programming seems be affected by the interruption...) and now I keep getting output (being written out to a file) that what looks like foreign characters [see attachment]. I tried to reinstall g++ next im going to try pdfcrack reinstall (it works otherwise).

thanks for your help

---

### Post by LaRoza on 2007-11-17
It looks like the file was corrupted.

---

### Post by opakedragon on 2007-11-17
the thing is I copied the text over to a new file and named it something different but when I ran it it was still giving this output. could one of the libraries be corrupted?

---

### Post by opakedragon on 2007-11-18
another note to add I just opened a brand new text file and wrote a totally different program (still writing out to a file but...)  and it produced what looks to be the right number of characters but they were all foreign....

---

### Post by Kadrus on 2007-11-18
Yeah like Laroza said..the file got corrupted..

---

### Post by smartbei on 2007-11-18
@Kadrus - Yes, Laroza did indeed say that. We saw it too. Also, it may be worth reading new replies to see if new information has arrived (it has).

From what I understand, the problem is not that the original source file is corrupted, as the OP has stated that he copied the source into a new file and it still doesn't work (and he even wrote a whole new program and the problem persists). Rather, the problem is that the output of the program is gibberish.

@OP - Can you provide us with a bit of source? Are you printing to a file using vanilla c/c++ standard library functions? When you print to stdout (printf, cout) does the same thing happen? I highly doubt a library or g++ could be corrupted, since they weren't being edited when the plug was pulled, just used.

It could also  be a problem of file encoding - This shouldn't be a proble for any English text, but other languages can cause what is shown in the screenshot if different encodings are used to write and read the file.

---

### Post by opakedragon on 2007-11-19
I was using #include <fstream> and the data type ofstream to output to the file. also when I use cout (even at the same time as ofstream) I get gibberish in the text file and good output on the screen.

---

### Post by smartbei on 2007-11-19
I really have no idea what the problem could be. Do you want to post a very short example program so that others can verify your results?

---

### Post by aks44 on 2007-11-19
@OP: Speaking of file encoding... what is the output of this bash command? It should be run the same way you're running your program.

```
echo $LANG
```

Granted, this is quite random but you never know...

---

### Post by opakedragon on 2007-11-19
figured it out sorry about all this it turns out I was going out of bounds of my array by one sorry about all this

---

