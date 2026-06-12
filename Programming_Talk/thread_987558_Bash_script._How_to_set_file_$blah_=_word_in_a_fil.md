---
title: "Bash script. How to set file $blah = word in a file"
date: 2008-11-19
forum: Programming Talk
---

### Post by Vinno on 2008-11-19
This returns: *tripwire --update -r /var/lib/tripwire/report//tmp/tripwire.temp.update*

I want $twupdate = the content in the 'tripwire.temp.update' file not the path.

How would I go on about doing that?

Thanks in advance.
```

# writes the results of 'ls -lah' to a temp file
sudo ls -lah /var/lib/tripwire/report/ > /tmp/tripwire.temp.list.dir

# prints to next temp file, the last line of the result
tail -n 1 /tmp/tripwire.temp.list.dir > /tmp/tripwire.temp.last.update

# grabbing and printing the 8th word to temp file
awk '{print $8}' /tmp/tripwire.temp.last.update > /tmp/tripwire.temp.update

twupdate=/tmp/tripwire.temp.update # <----- help me here

# doing the last update with the latest check file
echo "tripwire --update -r /var/lib/tripwire/report/$twupdate"
```

---

### Post by Cracauer on 2008-11-19
> **Vinno said:**
> This returns: *tripwire --update -r /var/lib/tripwire/report//tmp/tripwire.temp.update*

I want $twupdate = the content in the 'tripwire.temp.update' file not the path.

How would I go on about doing that?

Thanks in advance.
```

# writes the results of 'ls -lah' to a temp file
sudo ls -lah /var/lib/tripwire/report/ > /tmp/tripwire.temp.list.dir

# prints to next temp file, the last line of the result
tail -n 1 /tmp/tripwire.temp.list.dir > /tmp/tripwire.temp.last.update

# grabbing and printing the 8th word to temp file
awk '{print $8}' /tmp/tripwire.temp.last.update > /tmp/tripwire.temp.update

twupdate=/tmp/tripwire.temp.update # <----- help me here

# doing the last update with the latest check file
echo "tripwire --update -r /var/lib/tripwire/report/$twupdate"
```


Untested:
```

set -- `ls -lah /var/lib/tripwire/report/ | tail -1`
twupdate="$8"

```

---

### Post by ghostdog74 on 2008-11-19
> **Vinno said:**
> This returns: *tripwire --update -r /var/lib/tripwire/report//tmp/tripwire.temp.update*

I want $twupdate = the content in the 'tripwire.temp.update' file not the path.

How would I go on about doing that?

Thanks in advance.
```

# writes the results of 'ls -lah' to a temp file
sudo ls -lah /var/lib/tripwire/report/ > /tmp/tripwire.temp.list.dir

# prints to next temp file, the last line of the result
tail -n 1 /tmp/tripwire.temp.list.dir > /tmp/tripwire.temp.last.update

# grabbing and printing the 8th word to temp file
awk '{print $8}' /tmp/tripwire.temp.last.update > /tmp/tripwire.temp.update

twupdate=/tmp/tripwire.temp.update # <----- help me here

# doing the last update with the latest check file
echo "tripwire --update -r /var/lib/tripwire/report/$twupdate"
```

```

twupdate=$(ls -ltr |awk 'END{print $8}')

```

---

### Post by Cracauer on 2008-11-19
The performance is interesting.

Splitting the fields with `set --` and using tail is almost identical to using awk END.

```


foo1 ()
{
        set -- `ls -ltr /etc/ | tail -1`
        twupdate="$8"
}

foo2 ()
{
        twupdate=$(ls -ltr /etc/ | awk 'END {print $8}')
}

for i in `shellsupport -c  $2` ; do
        $1
done
echo $twupdate

~(wavehh)50% ctime sh ~/l.sh foo1 100
09:08
0:00.66 0.66 real 0.21 user 0.48 sys 104% CPU 0/92638 faults
~(wavehh)51% ctime sh ~/l.sh foo2 100
09:08
0:00.70 0.70 real 0.24 user 0.49 sys 104% CPU 0/100109 faults


```

Just for fun, optimizing it more.

I thought this would be faster as it avoids forking and execing either tail or awk
```

foo3 ()
{
        twupdate=`ls -ltr /etc | (
                while read line ; do oldline=$line ; done
                set -- $oldline
                echo $8
        )`
}

```

But alas:
~(wavehh)61% ctime sh ~/l.sh foo3 100
09:08
0:02.47 2.47 real 0.57 user 1.88 sys 99% CPU 0/85578 faults

That thing obviously hated the pipe.  Using a fifio is only minimally better:
```

foo4 ()
{
        rm -f /tmp/l2
        mkfifo /tmp/l2 # unsafe
        ls -ltr /etc/ > /tmp/l2 &
        while read line ; do oldline=$line ; done < /tmp/l2
        set -- $oldline
        twupdate=$8
}

```

~(wavehh)67% ctime sh ~/l.sh foo4 100
09:08
0:02.28 2.28 real 0.62 user 1.67 sys 100% CPU 0/100671 faults

Interesting.  I wouldn't have thought that the piping into a shell read loop is so bad.

You get some of the speed back by using a temporary file instead of a fifo, but not as good as the two-stage pipe.

---

### Post by ghostdog74 on 2008-11-19
> **Cracauer said:**
> 
Interesting.  I wouldn't have thought that the piping into a shell read loop is so bad.

tools such as awk/grep/sed/cut etc that process files have their "while loop" compiled. Using a while loop read loop in bash is definitely slower.

---

### Post by Cracauer on 2008-11-19
It's not the loop as such:
```

foo5 ()
{
        rm -f /tmp/l2
        ls -ltr /etc/ > /tmp/l2
        while read line ; do oldline=$line ; done < /tmp/l2
        set -- $oldline
        twupdate=$8
}


```

~(wavehh)2% ctime sh l.sh foo5 100
21:39
0:01.06 1.06 real 0.48 user 0.56 sys 99% CPU 0/73128 faults

This is more than twice as fast as the same shell construct, but fed by a temporary file instead of a fifo.

This is surprising to me.

You can cut off a couple tens of seconds of the latter solutions by moving the "rm" and "mkfifo" out of the loop.

---

### Post by Cracauer on 2008-11-19
Yeah, so bash does a lseek and an ioctl in front of every read() in that loop and reads with a blocksize of 128 bytes.

awk reads without further system calls with 4096 blocksize. Reads the whole file in 3 system calls plus one for the zero/EOF. Bash needed 1671 system calls :)

On FreeBSD /bin/sh (not bash) things are closer together.

---

### Post by Vinno on 2008-11-20
Thanks for the help guys :D

I have put in a if statement but the problem now is if i accidentally just hit the 'enter' key without typing 'y' or 'n', It gives me a error. 

How to kill/halt if no answer is given.


```
#!/bin/bash

# To check/update tripwire;
# Without having to type the command,
# remembering where tripwire reports are held
# or the last tripwire check date/time

# Asking for a check
echo -n "Want to check before update? (y/n) "

# setting $wantcheck with answer
read wantcheck

# If statements
if [ $wantcheck = y ]
then
        {
                # Print status to screen and do check.
                echo "Doing Check"
                sudo tripwire --check
        }
else
        {
                # Print status and move on.
                echo "Not doing check, moving to update."
        }
fi

# getting the latest report file name
twupdate=$(sudo ls -lah /var/lib/tripwire/report/ |awk 'END{print $8}')

# Doing the tripwire database update with latest report file
sudo tripwire --update -r /var/lib/tripwire/report/$twupdate
```

---

### Post by Cracauer on 2008-11-20
Please don't say "an error" without giving the error message ;)

That's right back to Windoze where the only error message is "Didn't work!".

In any case:
```

if [ "$myvar" = y ] ; then
[...]
fi

```

You need the quotes around $myvar.

And you probably want a case statement there.

---

### Post by Vinno on 2008-11-20
Thanks Cracauer :)

---

### Post by geirha on 2008-11-20
You can also have read only read 1 character so you don't need to hit enter after typing y or n. And I second using case, as it is easier to check for both lower case and uppercase y.
```

read -n1 -p "Want to check before update? (y/n) " wantcheck
echo
case "$wantcheck" in
  y|Y) 
    echo "yes"
  ;;
  n|N)
    echo "no"
  ;;
  *) 
    echo "something else"
  ;;
esac

```

---

### Post by Cracauer on 2008-11-20
"read -n" brings you from /bin/sh to bash land.

I recommend using "yepp" and "nope". Keeps users from answering too casually.

---

