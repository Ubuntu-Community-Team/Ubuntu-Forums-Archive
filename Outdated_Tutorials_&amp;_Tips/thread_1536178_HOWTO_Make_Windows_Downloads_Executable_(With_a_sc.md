---
title: "HOWTO: Make Windows Downloads Executable (With a script)"
date: 2010-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Quirkyjim on 2010-07-21
Hello there! I must introduce myself by saying that this is indeed my first post here, so hello!

The topic I will be covering is very basic, but it was probably my first useful thing I did on my new Ubuntu partition.

Before we get started, lemme get you acquainted with my system. I'm running Ubuntu on a 10 gb partition on my brand new 64-bit Toshiba Qosmio laptop with 4 gigs of ram and one of the new i7 processors. It shipped with Windows 7 and I recently installed Ubuntu 10.04 desktop onto a 10 gb partition. I was just planning on having it to mess around with it, but I'm starting to like it more and more. :) 

Anyways, let's get started.

I came across this problem while messing around with using various Windows stuff using Wine. I was downloading various exe's, but when I went to my Downloads folder, it said I couldn't run them! Now, I'm not a complete Unix nub, so I knew I had to fix the permissions. It was as simple as right-clicking the file, going into Properties -> Permissions and checking the box next to "Allow Executing File as Program." Simple, right? Yeah, it is. But I was thinking there was an easier an quicker way to do it, especially en masse.

So I created this nifty bash script. Check it out.

```
#!/bin/bash

chmod a+x *.exe
echo "All windows files made executable!"
```

Basically, all it does is changes the permissions of all your exe files in the current directory to be executable by all. I know, it's simple, but I figure it may be useful to put up here.

**BONUS**

Yes, there's a bonus! I figured that I should add this on as well. This script makes all the .desktop shortcuts in the current directory to be executable.

```

#!/bin/bash

chmod a+x *.desktop
echo "All windows files made executable!"
```

And there you go! Two nifty little scripts to help with Windows programs.

Thanks for reading!
Quirkyjim

P.S.
If you want to be able to access these scripts easily, you can do one of two things:

1) Copy your file to /bin

You'll have to have root access to do this, so you'll want to do:

```

sudo cp fix_shortcuts /bin

```

2) Add the directory of your script(s) to your PATH variable

Personally, this is what I use. That way, I can just make a new script and use it immediately (with permissions).

```

export PATH=$PATH:/data/myscripts

```

There you go!

Thanks for reading.

---

