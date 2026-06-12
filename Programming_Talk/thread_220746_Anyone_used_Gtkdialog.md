---
title: "Anyone used Gtkdialog?"
date: 2006-07-22
forum: Programming Talk
---

### Post by 3rdalbum on 2006-07-22
```
sudo apt-get install gtkdialog
```

GTKdialog is a kind of GUI toolkit which accepts an XML-based language (through a file or stdin) and outputs an interface. There are a number of examples included with it so you know what I mean by that.

I was wondering if anyone has used it before? Because it's XML and therefore uses nesting of tags, it seems a lot more intuitive than the other toolkits I've used before.

But exactly how flexible is it? For instance, could I create the kind of interface you would see in a Windows installer? Does it allow you to place graphics in the window? I'm very interested in using it in a Python project; I figure I could just redirect stdin and stdout so Python could talk to gtkdialog. How would I go about doing this?

---

### Post by jasonpline on 2007-08-21
I realize this an old post but if anyone's interested I've written alot of gtkdialog apps. I wrote them all for Puppy Linux. Mostly multimedia stuff (audio conversion, cd ripping, lossless audio file testing, etc...). I kind of got sick of using a minimalistic distro and started using Ubuntu instead. I figured my laptop is more than capable of running the latest stuff so there's no point in it. Anyways I've ported the apps I use over to my Ubuntu install and they seem to work fine (after some tweaking). I can post the programs if there's any interest.

---

### Post by glantucan on 2008-07-11
Almost a year later ... 

I'm interested :D

In fact I've got a problem because the event driven example coming with the package doesn't work on my ubuntu hardy.
When running:
```
#! /usr/bin/gtkdialog -e 

function print_this() {
  echo "print: $1"
}

export MAIN_DIALOG='
<vbox>
  <button>
    <label>function</label>
    <action>print_this button</action>
  </button>
  <button>
    <label>Exit</label>
  </button>
</vbox>
'

```

I get:
```

$ ./eventDriven.sh
sh: source: not found

** ERROR **: GtkDialog: Could not find the dialog description in the environment variable 'MAIN_DIALOG'.
aborting...
Aborted

```

Any ideas?

Many thanks

---

### Post by glantucan on 2008-07-11
By the way, it seems it is a bug:
[https://bugs.launchpad.net/ubuntu/+source/gtkdialog/+bug/177093](https://bugs.launchpad.net/ubuntu/+source/gtkdialog/+bug/177093)

And it seems it's fixed, but I don't understand how to fix it on my computer

:confused:

---

### Post by glantucan on 2008-08-13
> **glantucan said:**
> By the way, it seems it is a bug:
[https://bugs.launchpad.net/ubuntu/+source/gtkdialog/+bug/177093](https://bugs.launchpad.net/ubuntu/+source/gtkdialog/+bug/177093)

And it seems it's fixed, but I don't understand how to fix it on my computer

:confused:

TOC,TOC,TOC,...
Hello? :)

---

### Post by vincenma on 2008-12-13
Hi, I ran in the same problem.

my **temporary** solution to get gtkidesk working on ubuntu 8.10 "intrepid": 

as root :
```

# which bash
/bin/bash
# cd /bin
# ls -al *sh*
-rwxr-xr-x 1 root root 725136 2008-05-12 14:48 bash
-rwxr-xr-x 1 root root  87924 2008-06-20 12:07 dash
lrwxrwxrwx 1 root root      4 2008-12-13 20:16 rbash -> bash
lrwxrwxrwx 1 root root      4 2008-12-11 22:45 sh -> dash
lrwxrwxrwx 1 root root      4 2008-12-13 20:16 sh.distrib -> bash

# ln -sf bash sh
# ls -al *sh*
-rwxr-xr-x 1 root root 725136 2008-05-12 14:48 bash
-rwxr-xr-x 1 root root  87924 2008-06-20 12:07 dash
lrwxrwxrwx 1 root root      4 2008-12-13 20:16 rbash -> bash
lrwxrwxrwx 1 root root      4 2008-12-13 20:18 sh -> bash
lrwxrwxrwx 1 root root      4 2008-12-13 20:16 sh.distrib -> bash


```

this permits me to get gtkidesk working...but I really do not think its a good idea to leave sh pointing to bash instead of dash so I reverted the symbolic link to point to dash right after I finished doing what I wanted with gtkidesk...

really, its probably easier to simply edit idesk config file with emacs in this case but I wanted to test gtkidesk :)

hope it helps

---

### Post by glantucan on 2008-12-13
Hmm!
Log time to get some feedback... :D but always welcome to the forum vincenma.

I'll check this out as soon as I get my linux desktop. Thanks for the input!

I would also like to understand why this is needed... if that's remotely possible

Cheers!

---

### Post by mssever on 2008-12-13
> **glantucan said:**
> Hmm!
Log time to get some feedback... :D but always welcome to the forum vincenma.

I'll check this out as soon as I get my linux desktop. Thanks for the input!

I would also like to understand why this is needed... if that's remotely possible

Cheers!
I don't know anything about that specific software, but my guess is that some bash script(s) somewhere are erroneously called using /bin/sh. In many distros, /bin/sh is a symlink to bash. The effect is that people sometimes write buggy sh scripts by relying on bash-specific stuff. Ubuntu (since Edgy, I think) links /bin/sh to dash, which is a smaller shell and conforms much more closely to the standard. Thus, sh scripts that use bashisms (correctly) won't work on a default Ubuntu.

You can use checkbashisms to identify bashisms in sh scripts.

---

### Post by Harii on 2009-07-18
what  puppy linux gtkdialog apps.? 
sounds like they could be very useful to me.
i really like small apps -

---

### Post by simon_w on 2010-01-18
The problem, from reading the bug reports seems to be that gtkdialog is using the bashism `source` to read the functions, instead of simply `.`.

I'm come up with what I think is a rather elegant work-around for an event-driven dialog:

```

#! /bin/bash

export GTKD_FUNCS="$0"

function test_func () {
    echo 'test_func executed';
}

function launchDialog () {

    export DIALOG="
    <window>
        <vbox>
            <button>
                <label>Execute test_func()</label>
                <action>$GTKD_FUNCS test_func</action>
            </button>
            <button cancel></button>
        </vbox>
    </window>
    "

    gtkdialog --program=DIALOG
}


case "$1" in
    test_func)
        test_func;
    ;;
    *)
        launchDialog;
    ;;
esac

```

of course, there may even be situations when it makes sense to execute function individually, from the script, so i like this for that reason too :)

any comments?

uo&#623;&#7433;s

edit: typo

---

### Post by glantucan on 2010-01-18
Hi simon_w

I'm happy there is someone using gtkdialog. I found it really funny. But I'm not using it at the time being. I'll check your workaround if I get some time to refresh my memory on it. :D

Cheers!

---

