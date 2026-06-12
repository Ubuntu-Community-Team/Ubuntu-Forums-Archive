---
title: "Bash (Script) Help Please"
date: 2007-11-08
forum: Programming Talk
---

### Post by MasterXandrex on 2007-11-08
All, 

I need a bit of help. I need to write a bash script that will take in two (relative) directories and move files into a third directory in the following manner:

1) If and only if a command line switch is given, any file existing in one directory but not the other should be moved to the new directory.

2) When two files have identical names, the newer one should be moved to the new folder.

Come to think of it, there may be a command that does this i just don't know. Any help you can provide would be appreciated. 

Oh, also, here's one hitch, anything I write needs to work on Enterprise Solaris, but don't worry about that so much, I can test and tweak it to make it work. I just need to know where to start.


Thanks,

Xan

---

### Post by BoneKracker on 2007-11-08
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

### Post by gradedcheese on 2007-11-08
Here are a couple quick hints:

Assuming there aren't subdirectories, you can look at each file in a directory like this:

```

IFS="\n"
for f in `ls somedir/`; do 
echo $f; #do something here instead 
done

```

To see if a file $f exists in the other directory:

```

IFS="\n"
for f in `ls somedir/`; do 
  if [ -e otherdir/$f ]; then
     echo "$f exists in otherdir/"
  fi
done

```

...the ABS that BoneKracker pointed you to explains '-e' and other topics really well.

If your script needs to take command-line options, know that they're numbered $1, $2 and so on (also see info about this in the ABS).

---

### Post by geirha on 2007-11-09
It sounds like something rsync could do. Probably an idea to look at the man page for rsync and see.

---

### Post by MasterXandrex on 2007-11-09
Thanks for all the help so far, I'll probably start testing some scripts this afternoon. 

Also, I don't believe that I can use rsync, I did look at that before I decided to write the script. It is either restricted or not installed on the Solaris box I need to use this on. 


Like I said, Thanks,

Xan

---

