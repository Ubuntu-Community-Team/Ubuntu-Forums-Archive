---
title: "Building Shoes 3 problems."
date: 2011-01-27
forum: Programming Talk
---

### Post by chunky bacon! on 2011-01-27
[FONT=Georgia][SIZE=4]Hi.

I followed the instructions here:

[https://github.com/shoes/shoes/wiki/Building-Shoes-on-Linux](https://github.com/shoes/shoes/wiki/Building-Shoes-on-Linux)

And I don't get errors or anything, but typing "shoes -v" tells me that it is not installed.  I will admit that I don't even know what Rake does.

So, is there something missing from the instructions for Ubuntu?  Something else I should be doing?
[/SIZE]

[/FONT]

---

### Post by chunky bacon! on 2011-01-27
OK, well, turns out I just didn't understand that it was installed, but to a particular path.

It puts the file in a older called "Dist" that sits inside the "shoes" folder.  Had to email the mailing list to get the answer.

---

### Post by karatedog on 2011-02-12
I was also confused with Shoes, I haven't found a direct instruction on how to use it. But endurance pays off:
Shoes is client application you have to run (you will find an executable  named 'shoes' in your install folder). A window will pop up with 3 options, THEN you can load your Ruby script into Shoes, which then will execute your script.
So there is no such thing as:```
require 'shoes'
```

---

