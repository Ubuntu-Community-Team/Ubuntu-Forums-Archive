---
title: "shell script to change permissions of all images file name has spaces what to do"
date: 2010-10-17
forum: Programming Talk
---

### Post by jamesbon on 2010-10-17
I created a shell script the images in some of the folders were not having proper permissions
so this script 
```

#!/bin/sh
i=1
for j in `ls *.png`
do
   chmod ugo-x $j
done

```works but if the file name contains blank then it is not working.
What do I need to improve.

---

### Post by sisco311 on 2010-10-17
Use quotes:

```

#!/bin/sh
for file in *.png
do
   chmod -x "$file"
done

```

See: ```
man sh | less +/Quoting
```

---

### Post by jamesbon on 2010-10-17
Ya before posting I had tried that and it had not worked.

---

### Post by spjackson on 2010-10-17
> **jamesbon said:**
> Ya before posting I had tried that and it had not worked.
If you had tried the code as posted by sisco311 you would find that it does work. There are two faults with your code and both of these are addressed by sisco311's posting.

1. Don't use ls and back-ticks when a simple wildcard will do.
2. Do place your variable in double-quotes.

---

### Post by sisco311 on 2010-10-17
BTW, you don't need a loop, you could simply run:
```
chmod -x *.png
```

---

### Post by geirha on 2010-10-17
See [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs) for a discussion on why your ls-approach fails.

---

### Post by jamesbon on 2010-10-17
Actually you are right no need  of while loop the original loop which I had written was to rename a bunch of pics.
In one of the image there was a problem of permission and blank space this file was having problem which I had mentioned above in.
The "" method is working I had forgotten the original script and was checking the permissions of file.So in utter confusion I felt that "" are not working.Which is not the case.

---

### Post by worksofcraft on 2010-10-17
Here is another [link for ideas to deal with spaces in filenames]("http://unixjunkie.blogspot.com/2007/01/handling-filenames-with-spaces_15.htmlinclusion of spaces"). But you make a very good point about it being a bit of a problem that messes up lots of scripts and causes all sorts of mayhem with url's on the internet.

Some people simply change separators that shell parser applies to allow only tabs and new lines but even that isn't fool proof because you can create file names with them in apparently :shock:

p.s. BTW you can also create file names with " in and ultimately I think the best solution is just to rename them.

---

