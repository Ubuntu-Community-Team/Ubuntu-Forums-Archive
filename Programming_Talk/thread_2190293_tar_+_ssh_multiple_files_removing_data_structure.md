---
title: "tar + ssh: multiple files removing data structure"
date: 2013-11-26
forum: Programming Talk
---

### Post by erotavlas on 2013-11-26
Hi,
 
I have the following problem. I want to compress many files that are located in different paths i.e. /path1/file1, /path1/file2, /path2/file3 and so on on single file and I want to remove the folder structure. After this I want to put all in pipe with ssh command and then to decompress the archive in the server.
I'm using the following command
```

tar -jcf - /path1/file1 /path1/file2 /path2/file3 | ssh user@ip 'tar -C /path/ -jxf -'

```
it works only in part since it maintains the structure of the origin folder in the server.
How can I do?
 
Thank you

---

### Post by Bachstelze on 2013-11-26
Try

```
tar -jcf - /path1/file1 /path1/file2 /path2/file3 | ssh user@ip 'tar --strip-components=1 -C /path/ -jxf -'
```

(The title is misleading, this has nothing to do with bash.)

---

### Post by erotavlas on 2013-12-01
Ok, it works. Now if I want to reverse the direction of the operation. In the above example I can tar files and send them to a server. If I want to launch the command from my pc in the server and I want to copy file in my pc, how can I do? Is it possible to execute a remote tar and then pipe it with ssh and tar in my pc?
I can use scp with compression flag -C to do it but I don't know if I can do tar+ssh that is faster.
```

scp user@ip:/path_file1 user@ip:/path_file2  /home_path

```
Thank you for your help.

---

### Post by Lars Noodén on 2013-12-01
You should be able to just reverse the situation.  Output from ssh can get piped into the local tar.

---

### Post by erotavlas on 2013-12-01
Ok, but how could I tar the files at origin in unique tar file and then send it via piping?

---

### Post by Lars Noodén on 2013-12-01
You write to stdout as your file and then on the client side read from stdin.

```

ssh tar zcf - /some/path/ | ( cd /another/path; tar zxf -)

```

I should have mentioned that above, it's not obvious until you've seen it used in a few ways.  Most programs will let you write to stdout or read from stdin using the shortcut **-**  You can also sometimes use /dev/stdout or /dev/stdin.  There are a few exceptions but most allow it.

---

### Post by erotavlas on 2013-12-01
Ok, but how could I tar the files at origin in unique tar file and then send it via ssh?
Something like this
```

tar -jcf - /path1/file1 /path1/file2 /path2/file3 | ssh user@ip 'tar --strip-components=1 -C /path/ -jxf -'

```
but launched from my pc.

---

### Post by Lars Noodén on 2013-12-01
In #6 above, you are tarring files on the remote machine and then extracting them on the local machine.  Is that what you are trying to do?  It's the opposite of what you have in #1.

---

### Post by erotavlas on 2013-12-02
Yes, I'm able to do it in one way as I specified in my first post and after the suggestion of Bachstelze I'm able to remove the data structure. Now I would like to know if it is possible to do this in the reverse way. That is by launching the command from a local machine to a remote server. The server should execute the tar of several file and pipes it via ssh to local machine that untar the output of ssh.

---

### Post by Lars Noodén on 2013-12-02
> **erotavlas said:**
> The server should execute the tar of several file and pipes it via ssh to local machine that untar the output of ssh.

That's what #6 above does.  

You just move ssh in the formula:

```

ssh user@ip 'tar -jcf - /path1/file1 /path1/file2 /path2/file3' | tar --strip-components=1 -C /path/ -jxf -

```

Then the first tar is run on the remote machine and the second tar is run locally.  The first makes the archive and sends it over stdout via the pipe to the second which reads it from stdin and extracts it.

---

### Post by erotavlas on 2013-12-03
Ok, it works. The --strip-components=n works well only if all the files have a path with the same deep. How can I do if the paths have different deep?

---

### Post by erotavlas on 2013-12-04
> **Lars Noodén said:**
> That's what #6 above does.  

You just move ssh in the formula:

```

ssh user@ip 'tar -jcf - /path1/file1 /path1/file2 /path2/file3' | tar --strip-components=1 -C /path/ -jxf -

```

Then the first tar is run on the remote machine and the second tar is run locally.  The first makes the archive and sends it over stdout via the pipe to the second which reads it from stdin and extracts it.

Ok, it works. The --strip-components=n works well only if all the files  have a path with the same deep. How can I do if the paths have different  deep?

---

### Post by Lars Noodén on 2013-12-04
I think for that you would need to run tar+ssh multiple times.  

tar doesn't have conditional choices for its parameters so if you're wanting to have --strip-components strip different depths you'll need a separate instance of tar.  And because the pipe is one dimensional, having only one target, you'll need another pipe to hit a different target.  So all that means running tar+ssh or ssh+tar multiple times, once for each depth.

---

### Post by erotavlas on 2013-12-08
Ok, thank you.

---

