---
title: "fatal bash script..."
date: 2007-06-29
forum: Programming Talk
---

### Post by danubius on 2007-06-29
hi everyone!
i just converted from os-x to ubuntu, learned hundreds of new things -- mounting usb-cameras, apple-hfs-cds and how to use my powerbook as alarm clock and lots more -- but finally failed with my first bash script. it already deleted fifty original images, and i don't want it to happen again. could please someone correct it?

```

#!/bin/bash

i=2165;
for file in PICT*.JPG; do
j=$(printf "%05d" $i)
mv $file D$j.JPG
i=[$i+1]
done
```

i want it to run inside my picture folder to rename all of them, starting with i.

thanks a lot,

danubius

---

### Post by HackingYodel on 2007-06-30
Sorry, I've had a long day and don't understand exactly what you are trying to do in your script.

How are the files named in your picture folder and what do you want to rename your files to?

I'm sure we can get a working script together, I just need to know the way your files are named.

---

### Post by cwaldbieser on 2007-06-30
> **danubius said:**
> hi everyone!
i just converted from os-x to ubuntu, learned hundreds of new things -- mounting usb-cameras, apple-hfs-cds and how to use my powerbook as alarm clock and lots more -- but finally failed with my first bash script. it already deleted fifty original images, and i don't want it to happen again. could please someone correct it?

```

#!/bin/bash

i=2165;
for file in PICT*.JPG; do
j=$(printf "%05d" $i)
mv $file D$j.JPG
i=[$i+1]
done
```

i want it to run inside my picture folder to rename all of them, starting with i.

thanks a lot,

danubius

You might be better off using something like "krename".
If want to write a shell script, you might want to echo the output rather than executing the command when you test it.  I expect you wanted to do something like:
```

#! /bin/bash

i=2165;
for file in PICT*.JPG; do
    j=$(printf "%05d" $i)
    #mv $file D${j}.JPG
    echo mv $file D${j}.JPG #Uncomment previous line to actually rename files.
    i=$(($i+1))
done

```
This should rename your PICT*.JPG files to D02165.JPG, D02166.JPG, ...

---

### Post by danubius on 2007-07-03
Thank you. I tried both krename and your modified script, the second not working for me. Krename does the job, that is ok for the moment.

Thanks a lot.

---

