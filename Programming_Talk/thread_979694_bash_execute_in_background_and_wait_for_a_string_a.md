---
title: "bash: execute in background and wait for a string at stdout?"
date: 2008-11-12
forum: Programming Talk
---

### Post by segalion on 2008-11-12
I would like to write a script that launch a program in background, and wait for this program to read some string at stdout. The program (i.e wminput) write some string at stdout (i.e Ready.) a variable time after it is launched.

Something like this...

```
program_at_background &
read from_stdout # wait until "Ready" appear
rest of script...

```

I was trying with "read" command (that wait for stdin instead of stdout) and changing redirections and file descriptors ( stdin, stdout, exec, etc.) but I couldnt get any success.


Thanks in advance...

---

### Post by dwhitney67 on 2008-11-12
Is there a requirement that you must run that script in the background?

If not, then perhaps the following would suffice:
```

#!/bin/sh

msg=`sh ./script1.sh`

echo message received: $msg

exit 0

```

---

### Post by segalion on 2008-11-12
> **dwhitney67 said:**
> Is there a requirement that you must run that script in the background?



Yes, its a requirement.

I want to run wminput in background. It activate the wiimote as a bluetooth joypad, and has to be running in paralell with the rest of script.

Thanks for the response.

---

### Post by geirha on 2008-11-12
```

# Start wminput in the background and send its output to file descriptor 3
exec 3< <(wminput)

# Read the output of wminput line by line until one line contains Ready
while read line; do
   case "$line" in
   *Ready*)
      echo "'$line' contains Ready. Exiting loop"
      break
      ;;
   *)
      echo "'$line' does not contain Ready."
      ;;
   esac
done <&3

# Close the file descriptor
exec 3<&-

echo continue the script ...

```

---

### Post by segalion on 2008-11-13
Thanks a lot, geirha. 

Thats exactly what I was searching for!!!

I am seen that you have a lot of thanked posts. My respect.

---

### Post by kartlee05 on 2012-05-11
> **geirha said:**
> ```

# Start wminput in the background and send its output to file descriptor 3
exec 3< <(wminput)

# Read the output of wminput line by line until one line contains Ready
while read line; do
   case "$line" in
   *Ready*)
      echo "'$line' contains Ready. Exiting loop"
      break
      ;;
   *)
      echo "'$line' does not contain Ready."
      ;;
   esac
done <&3

# Close the file descriptor
exec 3<&-

echo continue the script ...

```


I am looking for a similar solution where the script will be launched through ssh. The script set certain environment and call a perl script. The perl script print certain information say X and Y which is communicated through launch host ( from where ssh is run ) through stdout. I don't want ssh to hang forever till the perl script is run and wanted to close once X and Y is communicated. The script you suggested above would work for me but it need to work in bourne shell. Can you please suggest a technique for it?

The solution I am following now is -

A) The shell script would call underlying perl script as background process

exec_proc()
{
 exec <perl script>
}
exec_proc &

and perl script would print X and Y and close STDOUT.

At this point the ssh would terminate.

If you have a better solution, please let me know.

---

### Post by geirha on 2012-05-11
> **kartlee05 said:**
> I am looking for a similar solution where the script will be launched through ssh. The script set certain environment and call a perl script. The perl script print certain information say X and Y which is communicated through launch host ( from where ssh is run ) through stdout. I don't want ssh to hang forever till the perl script is run and wanted to close once X and Y is communicated. The script you suggested above would work for me but it need to work in bourne shell. Can you please suggest a technique for it?

Heh, you revived a 3.5 year old thread.

Anyway, everything in that script will work with bourne, except the process substitution. You can use a fifo instead.

```

#!/bin/sh

somecommand() {
    sleep 2
    echo X
    sleep 2
    echo Y
    sleep 2
    echo Z
}

mkfifo fifo || exit
trap 'rm -f fifo' 0

somecommand > fifo &

while read line; do
    case $line in
        Y) echo "Y found, breaking out."; break;;
        *) echo "<$line>";;
    esac
done < fifo

echo Outside^cat

```
And testing it:
```
$ TIMEFORMAT=%R
$ time ./testscript
<X>
Y found, breaking out.
Outside
4.084

```


> **kartlee05 said:**
> 
The solution I am following now is -

A) The shell script would call underlying perl script as background process

exec_proc()
{
 exec <perl script>
}
exec_proc &

and perl script would print X and Y and close STDOUT.

At this point the ssh would terminate.

If you have a better solution, please let me know.

I can't quite understand what you're trying to do, but it sounds like fifos might help.

---

