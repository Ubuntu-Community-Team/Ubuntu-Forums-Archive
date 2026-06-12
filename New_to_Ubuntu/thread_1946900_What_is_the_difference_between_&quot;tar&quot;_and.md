---
title: "What is the difference between &quot;tar&quot; and &quot;sig&quot; files"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by jps2012 on 2012-03-25
I was trying to install the package for makefile, and downloaded a tarball that uncompressed and built a folder with one file named "make-3.82.tar.gz.sig"

I haven't seen that file extension. For some reason the files uncompressed and landed in my bin/temp folder. "Properties" of the file show that it's locked. 

I looked up the file extension and read one user's comments to the effect that the "sig" extension might indicate the file "had been tampered with." 

That comment appears on this link: 

[http://www.linuxquestions.org/questions/linux-newbie-8/sig-files-with-tar-files-any-real-significance-804238/](http://www.linuxquestions.org/questions/linux-newbie-8/sig-files-with-tar-files-any-real-significance-804238/)

Are "sig" files 'dangerous'? I'm fairly sure I'd downloaded it from a GNU mirror. 

Assuming they're not dangerous, are they compiled/installed in the same way tarballs are? 

Many thanks.

---

### Post by lechien73 on 2012-03-25
Hi,

The .sig file is a signature file. It's generated so that you can verify the tar.gz file against it to make sure its not been tampered with.

So, you should have two files - a tar.gz and a tar.gz.sig file, you then verify the tarball using:

```
gpg --verify file.tar.gz.sig file.tar.gz
```

So, in answer to your question, it's not dangerous. Rather a way of verifying that an original file hasn't been tampered with.

---

### Post by jps2012 on 2012-03-25
That's good to hear, Matt. Thank you. I'll continue working to figure out how to install it.

---

### Post by jps2012 on 2012-03-27
Just wanted to thank you, Lechien. It's good to know that (in this case) I haven't downloaded a dangerous file.

---

