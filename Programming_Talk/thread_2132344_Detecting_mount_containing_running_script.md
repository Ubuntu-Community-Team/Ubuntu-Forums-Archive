---
title: "Detecting mount containing running script"
date: 2013-04-04
forum: Programming Talk
---

### Post by kiplingw on 2013-04-04
Hey forum,

Is there a recommended approach for a Bash script to find at runtime the device which contains the mount which contains the running script? I have a script which runs off of a removable optical media and I'd like it to eject the media when it is done, but the 'eject' command needs a device path.

~ Kip

---

### Post by schragge on 2013-04-04
Something like
```

mntpoint=`df "$0"|awk 'NR==2{print $NF}'`
exec eject "$mntpoint"

```

---

### Post by ofnuts on 2013-04-04
> **schragge said:**
> Something like
```

mntpoint=`df "$0"|awk 'NR==2{print $NF}'`
exec eject "$mntpoint"

```

Clever (and necessary) use of 'exec'....

---

### Post by kiplingw on 2013-04-04
Thanks folks. This is what I've come up with based on some of the feedback and researching a bit more BASH.

```

# Eject the media only if we are running off of removable media...
EjectRemovableMedia()
{
    # Get full directory name containing this script no matter where it is 
    #  called from...
    AUTORUN_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"

    # Find the mount point it is located on...
    MOUNT_POINT=`df "$AUTORUN_DIR" | awk 'NR==2{print $NF}'`

    # Alert user of our intentions...
    echo -n "Checking if" $MOUNT_POINT "is removable media..."

    # Eject if it is removable media. That is, under /media/* according to sect
    #  3.11.1 of the FHS...
    if [[ $MOUNT_POINT == /media/* ]]; then

        # Eject the media...
        echo -e $SYMBOL_STATUS_OK
        echo -n "Ejecting..."
        eject $MOUNT_POINT 2> /dev/null

        # Old approach: eject the disc by first trying CDROM eject method, then
        #  by SCSI method...
        # eject -r -s 2> /dev/null

        # Report whether it was successful or not...
        if [ $? == 0 ]; then
            echo -e $SYMBOL_STATUS_OK
        else
            echo -e $SYMBOL_STATUS_FAIL
        fi

    # Not running off of removable media, so don't try to eject...
    else
        echo -e $SYMBOL_STATUS_FAIL
    fi
}

```

I could prefix eject with exec, but I wasn't sure I understood fully why it was necessary and when I should be using it.

~ Kip

---

### Post by slavik on 2013-04-04
man exec

---

### Post by kiplingw on 2013-04-05
> **slavik said:**
> man exec

Thanks Slavik, but that's a given. It should have gone without saying that I wasn't satisfied with the man page.

---

### Post by ofnuts on 2013-04-05
Because the file with your script is open, so you can't unmount the filesystem that holds it. 'exec' replaces the script by another process, so the file is closed and the media can be unmounted.

---

### Post by schragge on 2013-04-05
+1 to what **slavic** and **ofnuts** said. Slavik's adivice was well-minded, but it might be misleading if you don't have package *manpages-posix* installed. The manual page he meant is [exec(1posix)]("http://manpages.ubuntu.com/manpages/precise/en/man1/exec.1posix.html"). Since *exec* is impemented as bash builtin, you may also want to look it up in the [bash info manual]("http://www.gnu.org/software/bash/manual/html_node/Bourne-Shell-Builtins.html#index-exec"), or in the [ABS]("http://tldp.org/LDP/abs/html/internal.html#EXECREF").

Concerning your code, I'd probably rewrite this ```
AUTORUN_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"
``` as
```
AUTORUN_DIR=$(readlink -f "$0")
``` Strictly speaking, even this is not needed as *df* is able to walk through symlinks, so ```
AUTORUN_DIR=$0
``` should be enough.

BTW, better not name your script variables in all-caps as it may interfere with environment variables.

Also, if the only purpose of finding the mount point is to check whether it's a removable media then better approach would be directly evaluating device name:
```

device=$(df "$0"|awk 'NR>1{print $1}')
removable=$(lsblk -r -n -o RM $device)
if ((removable))
then echo Running off of removable media
else echo Running off of fixed drive
fi

```
Just for fun, doing the above snippet in one pass:
```

((`lsblk -rnorm $(df "$0"|sed '1d;s/ .*//')`))&&media_type=removable||media_type=fixed
echo Running off of $media_type media

```

---

### Post by conradin on 2013-04-05
> **schragge said:**
> Something like
```

mntpoint=`df "$0"|awk 'NR==2{print $NF}'`
exec eject "$mntpoint"

```

I thought it was best to avoid use of exec. Would this work with ` qoutes?

```

mntpoint=`df "$0"|awk 'NR==2{print $NF}'`
 `eject "$mntpoint"`

```

---

### Post by schragge on 2013-04-05
No, it wouldn't. To begin with, if eject returned some output, the shell would interpret it as a command. Fortunately, *eject* normally outputs nothing, so in this particular case, bare command substitution would be equivalent to executing *eject* in a subshell:
```
(eject "$mntpoint")
``` The script would end up waiting for the *eject* command to end with consequences described by **ofnuts** [post=12589266]above[/post]. BTW what's wrong with using *exec*?

---

### Post by kiplingw on 2013-04-05
> **schragge said:**
> +1 to what **slavic** and **ofnuts** said. Slavik's adivice was well-minded, but it might be misleading if you don't have package *manpages-posix* installed. The manual page he meant is [exec(1posix)]("http://manpages.ubuntu.com/manpages/precise/en/man1/exec.1posix.html"). 


Hey schragge. Thanks for the heads up. I was actually missing that package.

> **schragge said:**
> 
Since *exec* is impemented as bash builtin, you may also want to look it up in the [bash info manual]("http://www.gnu.org/software/bash/manual/html_node/Bourne-Shell-Builtins.html#index-exec"), or in the [ABS]("http://tldp.org/LDP/abs/html/internal.html#EXECREF").


Got it, thanks =)

> **schragge said:**
> 
Concerning your code, I'd probably rewrite this ```
AUTORUN_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"
``` as
```
AUTORUN_DIR=$(readlink -f "$0")
``` Strictly speaking, even this is not needed as *df* is able to walk through symlinks, so ```
AUTORUN_DIR=$0
``` should be enough.


The problem with that is I need just the directory and not the directory and the file name. This could also work, I reckon:
```
AUTORUN_DIR="$(dirname -- "$(readlink -f -- "$0")")"
```

> **schragge said:**
> 
BTW, better not name your script variables in all-caps as it may interfere with environment variables.


Great piece of advice. Thanks a lot.

> **schragge said:**
> 
Also, if the only purpose of finding the mount point is to check whether it's a removable media then better approach would be directly evaluating device name:
```

device=$(df "$0"|awk 'NR>1{print $1}')
removable=$(lsblk -r -n -o RM $device)
if ((removable))
then echo Running off of removable media
else echo Running off of fixed drive
fi

```
Just for fun, doing the above snippet in one pass:
```

((`lsblk -rnorm $(df "$0"|sed -n '2s/ .*//p')`))&&media_type=removable||media_type=fixed
echo Running off of $media_type media

```

It's a good solution but one problem is if the filesystem is encrypted, say, e.g. /home/me/.Private, then that will show up as its device name even though it's not actually it. When you run lsblk on it, it will choke.

It would be great if there was a way to call a whole bash subroutine through exec. Is there a way to do that? Then I could put all the ejection code in one function and call that via exec which would be a lot cleaner.

---

### Post by ofnuts on 2013-04-06
> **kiplingw said:**
> It would be great if there was a way to call a whole bash subroutine through exec. Is there a way to do that? Then I could put all the ejection code in one function and call that via exec which would be a lot cleaner.
If you call exec over a subroutine of your script, you defeat its very purpose. The important point here is that eject should somehow be called from outside your script (which is what 'exec' does) so that the file containing the script is closed when "eject' is executed.

But nothing forbids your to have all that code in a funciton that retrieves the device/fileystem and calls 'exec'.

---

### Post by schragge on 2013-04-06
> **kiplingw said:**
> It's a good solution but one problem is if the filesystem is encrypted, say, e.g. /home/me/.Private, then that will show up as its device name even though it's not actually it. When you run lsblk on it, it will choke. I have no experience with encrypted filesystems, but I guess that one additional step may help here: find the real device name with [findmnt](http://manpages.ubuntu.com/manpages/precise/en/man8/findmnt.8.html):
```

mountpoint=$(df "$0"|awk 'NR>1{print $NF}')
device=$(findmnt -c -n -o SOURCE $mountpoint|cut -d[ -f1)
removable=$(lsblk -r -n -o RM $device)
((removable)) && exec eject $device

```
If you show how an encrypted filesystem shows up in the output of the following commands
```

findmnt -l -otarget,source,label,uuid
findmnt -sl -otarget,source,label,uuid
findmnt -ml -otarget,source,label,uuid
sudo blkid -o list -c /dev/null

``` then I believe we could come up with a way to extract the device name from one of them.

---

### Post by kiplingw on 2013-04-06
> **ofnuts said:**
> If you call exec over a subroutine of your script, you defeat its very purpose. The important point here is that eject should somehow be called from outside your script (which is what 'exec' does) so that the file containing the script is closed when "eject' is executed.

But nothing forbids your to have all that code in a funciton that retrieves the device/fileystem and calls 'exec'.

I guess what I'm confused about is how exec works. As I understand it, it takes over execution of the current process with nothing further of the original script being executed after it. The reason for that is the file handle to the script will be closed immediately before the eject command is executed next. Is that correct?

---

### Post by schragge on 2013-04-06
Exactly.

---

### Post by kiplingw on 2013-04-06
> **schragge said:**
> Exactly.

It would be nice if the script were not locking the device and control could return to the script after the eject command. But I guess that is not so straightforward.

---

### Post by schragge on 2013-04-06
Well, you probably could use [at](http://manpages.ubuntu.com/manpages/precise/en/man1/at.1.html) for this:
```

echo Scheduling eject to be run in one minute
echo eject $device|at now + 1 minute
echo Continue script execution

```

---

### Post by kiplingw on 2013-04-06
That's one approach, but I think a problem with it is it won't be very elegant if, say, the script doesn't need to wait that long, or the script ends up taking a little longer than that.

---

### Post by schragge on 2013-04-06
Sure, it is very inelegant. I'm just wondering why would you want control to be returned to the script after *eject*? To check whether *eject* failed? Then do it like this
```

echo Running eject
if eject -n $device 2>/dev/null
then exec eject $device
else echo eject failed
fi

```

---

### Post by kiplingw on 2013-04-07
> **schragge said:**
> Sure, it is very inelegant. I'm just wondering why would you want control to be returned to the script after *eject*? To check whether *eject* failed? Then do it like this
```

echo Running eject
if eject -n $device 2>/dev/null
then exec eject $device
else echo eject failed
fi

```

Hey Schragge. I had thought about that already and isn't the problem that control never "returns" from the conditional's evaluation in the *then* since the exec it calls replaces the process space?

---

### Post by schragge on 2013-04-08
No. Why should that be a problem? It's syntactically correct. The *else* branch just won't be reached in this case. Open a terminal and try something like:
```
(if true;then exit;else some garbage;fi)
```

---

### Post by kiplingw on 2013-04-08
> **schragge said:**
> No. Why should that be a problem? It's syntactically correct. The *else* branch just won't be reached in this case. Open a terminal and try something like:
```
(if true;then exit;else some garbage;fi)
```

Right, but how will you know if the "exec eject" command completed successfully? As soon as it's run, execution leaves the script and never returns again, so there is no way to check eject's exit code and to do something based on that.

---

### Post by ofnuts on 2013-04-08
> **kiplingw said:**
> It would be nice if the script were not locking the device and control could return to the script after the eject command. But I guess that is not so straightforward.
It's not the script that is locking the device... 

A different approach is to have your script self-copy to /var/tmp and then 'exec' the copy (maybe passing its original location as a parameter or environment variable). Then you are no longer using a file on the device.

---

### Post by schragge on 2013-04-08
+1 to what **ofnuts** said.
There may be a problem if */var/tmp* (or */tmp* if you choose to use it instead) is mounted *noexec*. In this case, invoke it like
```
exec bash /var/tmp/$scriptname
```

---

### Post by kiplingw on 2013-04-08
> **schragge said:**
> +1 to what **ofnuts** said.
There may be a problem if */var/tmp* (or */tmp* if you choose to use it instead) is mounted *noexec*. In this case, invoke it like
```
exec bash /var/tmp/$scriptname
```

It's definitely possible to copy itself to tmp and execute the copy with the idea that it would relieve the device it was hosted on from being locked. I had considered that route, but then I figured it might not be worth the trouble and probably easier to just find a way to run the exec eject as the last command. But thanks for everyone's help.

---

