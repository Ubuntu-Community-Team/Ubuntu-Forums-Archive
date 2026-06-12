---
title: "Problem with Parameter Manipulation in Bash Script"
date: 2009-04-18
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-04-18
Ey guys I am making a simple script to tar files, the script takes two parameters a filename, and the files to be zipped. I currently have it working for taring a single file or folder but not multiple ones. I use this command in the script:

```

tar -czvf "$1".tar.gz "$@"

```

That works but it prints an ugly error message:
```

tar: test45: Cannot stat: No such file or directory
Small Test Folder/
Small Test Folder/Makefile
.
.
.
Small Test Folder2/lottery.c
tar: Error exit delayed from previous errors

```

When I echo $@ I get the filename in it as well as the files to be tarred, how do I go about removing the very first parameter from $@?

Thanks in advance!

---

### Post by ghostdog74 on 2009-04-18
you can try putting your files to tar in file
> 
       -T, --files-from=F
              get names to extract or create from file F



---

### Post by StunnerAlpha on 2009-04-18
> **ghostdog74 said:**
> you can try putting your files to tar in file
Eh? I would rather just be able to type bash zipper.h tarfile file1 file2 file3 and have them be tarred rather than putting them in a file. Thanks for the response.

---

### Post by ghostdog74 on 2009-04-18
show examples of the parameter you are passing in from the command line. did you quote them properly? are there white spaces in your file names?

---

### Post by StunnerAlpha on 2009-04-18
> **ghostdog74 said:**
> show examples of the parameter you are passing in from the command line. did you quote them properly? are there white spaces in your file names?
Yes there are white spaces, but I am making the script to be able to handle spaces in filenames. 

Here is the command:

```

bash zipper.sh test45 Small\ Test\ Folder Small\ Test\ Folder2

```

---

### Post by sarang on 2009-04-18
Try this:

```

#!/bin/bash
filename="$1"
shift
tar -czvf "$filename".tar.gz "$@"
exit 0

```

The key word here is 'shift'. Read more about it in the bash manual by running [FONT="Courier New"]man bash[/FONT] if you are not familiar with it.

---

### Post by StunnerAlpha on 2009-04-18
> **sarang said:**
> Try this:

```

#!/bin/bash
filename="$1"
shift
tar -czvf "$filename".tar.gz "$@"
exit 0

```

The key word here is 'shift'. Read more about it in the bash manual by running [FONT="Courier New"]man bash[/FONT] if you are not familiar with it.
Perfect! Just what I was looking for! Thanks!

---

### Post by sarang on 2009-04-18
And yes, you don't even have to type the whole 'bash zipper.sh' part. Edit your /home/USERNAME/.bashrc and at the very end add 

```

zipper ()
{
  filename="$1"
  shift
  tar -czvf "$filename".tar.gz "$@"
  return 0
}

```

This will result in a custom 'zipper' command being created.

Another useful function to add to ~/.bashrc is:

```

#Extract compressed files. Thanks to urukrama, Ubuntuforums.org	

myextract () 
{
     if [ -f $1 ] ; then
	echo "Working..."
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "Error: '$1' cannot be extracted via myextract()" ; return 1;
         esac
     else
         echo "Error: '$1' is not a valid file"
	return 99
    fi
}

```

---

