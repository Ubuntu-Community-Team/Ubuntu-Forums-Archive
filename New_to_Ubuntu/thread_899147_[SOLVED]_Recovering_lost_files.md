---
title: "[SOLVED] Recovering lost files"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by dinostabOMG on 2008-08-24
Recently I tried to upgrade from Gutsy to Hardy. I knew that upgrading isn't as safe as a new install, so I backed up first. Sure enough, the upgrade failed and I had to install from scratch.

Unfortunately, my backup didn't work properly. It output an archive, which I wanted, but later file-roller couldn't read it. Crap!

So, there is one .odt I would like to get back in particular. I heard you can use the grep command to get lost files back? 

I have an ext3 file system, installed over the same partition as the botched upgrade. Based on some advice I found while searching on how to recover files, I came up with this command:

```
sudo grep -i -a -B10 -A10 'upcoming project ideas:'
```

The advice I found followed that with > file.txt - but I don't have a particular file, I am hoping it can find the text floating around on the partition somewhere. Or hm, it just occurred to me that maybe that takes the output and puts it in a new file?

I also realize that this is not a plain text file, it's an .odt file. Still, I think the text should be in there relatively unmolested, right?

In any case, is this likely to work? Thanks.

---

### Post by talsemgeest on 2008-08-24
I had the same problem a few months ago. I backed up to a tar.gz, but when it was time to uncompress, none of the archive programs would uncompress it because it was that little bit corrupted. I lost everything...

---

### Post by aysiu on 2008-08-24
That *grep* command might work - I don't know.

I do know that if you boot a live CD, install the *testdisk* package and then run Photorec, you'll probably be able to recover the .odt file and just about everything else: ```
sudo nano /etc/apt/sources.list
``` Remove the *#* signs from the web address lines with the word *universe* in them. Save (Control-X, Y, Enter). ```
sudo apt-get update
sudo apt-get install testdisk
sudo photorec
```

---

### Post by dinostabOMG on 2008-08-24
Thanks for the recommendation, I discovered photorec researching this problem too! Now I have tons of files to wade through, but looks like this will do.

---

### Post by talsemgeest on 2008-08-24
Good luck, I hope you get your stuff back!

---

