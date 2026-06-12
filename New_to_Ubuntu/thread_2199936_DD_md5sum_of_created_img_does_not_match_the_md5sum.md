---
title: "DD md5sum of created img does not match the md5sum run on created img file post DD"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by suetonius2 on 2014-01-16
I'm a relative beginner at Linux and I am using a 12.04 Live USB boot disk to create a forensic image of one partition on the unmounted local hard drive. This image is being written to an external hard drive that is larger than the partition I am imaging. I'm trying to get the hash that is created when I run DD to match the the md5sum that I calculate after the image has been created but I have not been able to accomplish this yet. The hashes do not match. If anyone can help me I would really appreciate it. 

These are the commands I am using;

```
sudo dd if=/dev/sda2 of=/media/Forensic/Forensik2.img bs=4096 conv=noerror,notrunc,sync | md5sum > /media/Forensic/initialhash.md5 
```

I am checking the hash of the created Forensik2.img using;

```
md5sum /media/Forensic/Forensik2.img > /media/Forensic/posthash.md5 
```

Is there anything wrong with the commands I am using?

Thanks for any help you can provide.

---

### Post by spencer the great on 2014-01-16
The pipe character ("|") takes the output of the first command and dumps it into the input of the second command.  dd does not output the contents of your drive (in fact, it dumps nothing into output besides the finish message, which is dumped into stderr and thus is not piped, as far as I remember).  Basically, you're taking the md5sum of a blank string.
Your md5sum matched this, correct?
```
[COLOR=#000000]d41d8cd98f00b204e9800998ecf8427e[/COLOR]
```

Because that's what I got when I:
```
$ touch newfile
$ md5sum newfile
```

EDIT:
However, it is possible to md5sum the block device file, but I don't think those conversion options you specified will leave the image untouched, meaning, it will most likely have a different md5sum even if it was copied correctly.

EDIT2: Well, maybe not.  But then, I tested using a 16mb partition, so your results might be different, given the size of your thing.

---

### Post by suetonius2 on 2014-01-17
Yeah, that's the hash that I got. 

So, there is no way to create a hash for the image while its being created without changing the file in some way? 

Thanks for your help!

---

### Post by Dave_L on 2014-01-17
> **suetonius2 said:**
> So, there is no way to create a hash for the image while its being created without changing the file in some way?

This might work:

```
sudo dd if=/dev/sda2 | tee /media/Forensic/Forensik2.img | md5sum > /media/Forensic/initialhash.md5
```

I tested a similar command on a small amount of data (using dd parameters "bs=1 count=1024"), and it worked correctly. I don't know exactly how "piping" is implemented. I don't know whether doing it with a huge amount of data could be problematic. 


References:
[http://manpages.ubuntu.com/manpages/precise/en/man1/dd.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/dd.1.html)
[http://manpages.ubuntu.com/manpages/precise/en/man1/tee.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/tee.1.html)

---

