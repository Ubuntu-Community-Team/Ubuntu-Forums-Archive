---
title: "Can't run a *.sh file that's in my home folder from terminal."
date: 2014-01-29
forum: New to Ubuntu
---

### Post by bengy103 on 2014-01-29
Hi there, hope you are all in a good mood.

I'm using Ubuntu 12.04 LTS 64 bit.

I've been trying to get rid of that damned AMD Unsupported hardware watermark and to that end copied a file called unsupported.sh from online which I saved to my home folder. Then I made it executable. Then opened Terminal checked that unsupported.sh was there and typed in 'sudo unsupported.sh.

Terminal came back with: unsupported.sh: command not found

But it's there, I can see it when I 'dir' my home folder.

I think it may be a path problem but I can't find a path command or where it may be hidden.

On the other hand it may be refusing because it's not a 64 bit file.

Any help gratefully appreciated.

regards,

brawd.

---

### Post by Habitual on 2014-01-29
try ```
bash /home/<user>unsupported.sh 
```and see what happens.
If it runs, it just may need a "shebang" inside the .sh script.

```
#!/bin/bash < - while this is a shebang and NOT a comment
# my script stuff <-- this is a comment.
...
```

have a gander at [https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by Impavidus on 2014-01-29
By default the current directory is not in the PATH. If you use sudo, only some standard directories are in your path (/usr/bin etc., but nothing in your home directory). So you need to give the path to your script, so that the system doesn't search the PATH:```
sudo ~/unsupported.sh
```Shell scripts don't care about 32 or 64 bits.

---

### Post by bengy103 on 2014-01-29
Thank you both.

The problem needed the little squiggly bit and slash.

That page link you posted looks useful, I've put it in my bookmarks.

---

