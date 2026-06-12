---
title: "Recycle Bin / Trash Can Functionality for the Linux Shell"
date: 2007-10-06
forum: Programming Talk
---

### Post by irkengir on 2007-10-06
Since I've discovered that it is possible to have this kind of [functionality for Samba](http://ubuntuforums.org/showthread.php?t=155763) I've wanted to create a shell utility for moving files to a trash can rather than deleting them forever. I found [a simple implementation](http://www.cs.ecu.edu/~collins/rm/rm.html) but I wanted something a little more complete. So I've taken this as an opportunity to actually write something of generalised use in bash.

So I'm posting this for critique and advise, and possibly to see if anyone wants to help me write this, it's a pretty small project and an opportunity to learn a bit about shell scripting (I'm a pretty experienced programmer otherwise). I've read this article about [writing good Linux utilities](www.ibm.com/developerworks/linux/library/l-util.html) and this about the [GNU/POSIX utility guidelines](http://www.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap12.html). So I'm enclosing my design here in the hope that more experienced Linuxers :P may be able to offer some conceptual advice.

Note: I haven't written any actual code yet

_**can**_

the overall name for the utility is "can" which you can take to loosely mean "put in a trash can". Note 'a' and not 'the'. This is a easy to type, remember and say and is related to what it does. It isn't obvious what it does until you know of it but then not many Unix utilities are. I considered "trsh" but that sounds like a shell. I considered "bin" but that already means binary. "throwout" or "thrwt" or chuck are longer and no more obvious in meaning. 

I've tried to generalise my design to be: *a way of moving stuff to a place where it can be easily restored from for only a limited time*; so I like the way you can think of "can " to mean trash-can or "can" in the more general form as being a container. Of course "can" is a common english word so that's a bit annoying for this post but later on I can't see it as being a problem. The word also functions nicely as a verb: "I don't need that any more; can it"

_**Summary of Functionality**_

There are 3 scripts involved in this:[list][*]**can** - moves files to a trash can
[*]**ucan** - restores files from a trash can
[*]**pcan** - (purge can) this is usually executed daily, using cron, that permanently deletes files in the trash can if they have reached a certain age[/list]Each time a file is canned it goes to the trash can (usually this is a hidden directory under the user's home dir). When files are canned they are done so in such a way as to maintain the location of the deleted file. If you delete "/foo/bar/file.txt" whilst logged in as the user "zim" the file will be moved to "/home/zim/.trash/foo/bar/file.txt", with the sub-dirs automatically created as necessary. You can then "find ~/.trash" in order to view all the files you've canned and see exactly where they used to be. 

When you can files you may specify a --purge-after (-p) option to determine how long the file should hang around for. If this option is omitted the default value is used. You may specify a --purge-after of 0 or -1 to keep the file indefinitely. A new log file is created for each can operation containing the list of files that were canned, how long they should be kept for and when the can occurred. The log files will have the mode of 0400 and are stored in a dir ".canlogs" . A typical can log might look like this:
```
2007-10-06 16:46:12,20
/home/zim/foo.txt
/home/zim/bar.txt
```First is the date those files where deleted, then a colon, then how long they should stay around then on the new lines the deleted file paths.

If this should occur:```
$ touch foo
$ can foo
$ touch foo
$ can foo
```can will fail saying that foo is already in the trash. You may force it with -f to perform the can overwriting the old version of foo in the process.


**_Configuration and Hooks**_

can, ucan and pcan are all configured by a file ".can" in the user's home directory, if this isn't found a system-wide file "/etc/can.conf" is used. The configuration files looks very much like ini files and are sectioned into blocks that may inherit from each other. There are only a handful of directives. A commented example file is shown below:

```

####
# can.conf
#

    # the default configuration set
    [default]
    
        # where trashed files go
        trashcan=~/.trash
        
        # number of days trashed files remain in existance
        # set to 0 for no purge, this still permits user to use
        # purge in their invocation of can
        purge_after=45

        # the highest number a user can use when specifying 
        # their own --purge-after. 0 for no maximum
        max_purge_override=0

        # the lowest number a user can use when specifying 
        # their own --purge-after. 0 for no minimum
        min_purge_override=0
        
        # Hooks
        #
        # These are scripts that we executed either before (pre)
        # or after (post) can or ucan. These will be invoked once
        # for each file being moved by can or ucan unless otherwise stated
        
        
            # before can
                # $1 will be full filepath
                # $2 onwards are any --pre-args specified by the can invocation
                #
                # You may exit with a status number to communicate with can:
                #   0: continue with can - assumed
                #   1: abort the can and suppress execution of post_can_hook for this file
                #   2: abort the can and suppress execution of post_can_hook for this file
                #       and all others in this invocation of can
                #   3: do not can, purge right away
            pre_can_hook=''
                    
            # after can
                # $1 will be the full file path
                # $2 onwards are any --post-args specified by the can invocation
            post_can_hook=''

        
            # before ucan
                # $1 is the full file path where it was deleted from
                # $2 is the full destination file path (not necessarily the same as $1)
                # $3 onwards are any --pre-args specified
                #
                # You may exit with a status number to communicate with ucan:
                #   0: continue with ucan - assumed
                #   1: abort the ucan and suppress execution of post_ucan_hook for this file
                #   2: abort the ucan and suppress execution of post_ucan_hook 
                #      for this file and all others in this invocation of ucan
            pre_ucan_hook='' 
        
            # after ucan
                # $1 is the full file path where it was deleted from
                # $2 is the full destination file path (not necessarily the same as $1)
                # $3 onwards are any --post-args specified
            post_ucan_hook='' 
        
    # implements an alternate configuration set called 'foo' that 
    # inherits the options from upon default
    [foo : default]
    
        # deviation from default
        trashcan=/tmp/trash

    # another configuration not inheriting from anything
    [bar]

        # this will prevent this configuration set from being executed. You may wish 
        # to use this on default if you want to force your users to specify wish 
        # configuration to use
        disabled=1

```

As you can see in this configuration there are three blocks: default, foo and bar. You may specify which configuration you use in the -c option. Users can use this to direct their files to several trash cans if they wish.

Technical notes:[list][*]Because can create logs in ".canlogs" under the trash can dir you will be denied the ability to can anything called "/.canlogs" 
[*]If pcan encounters a file in a log that is not present in the trash can it will ignore it and carry on, assuming it has probably been restored[/list]

**_Usage**_

```
Usage: can [OPTION]... FILE...
Recursively moves files or directories to a trash can

  -c --config=CONFIG      specifies which set of configuration directive should apply
  -f --force              cans even if something with same name and path already exists in trash can
  -v --verbose            show the files being canned
  -p --purge-after=DAYS   set the number of day the files will remain
                          in the trash before being purged (rm'd)
  -r --pre-args=ARGS      args to send to the pre_hock_script
  -o --post-args=ARGS     args to send to the post_hock_script
  -h --help               display this help text
```

```
Usage: ucan [OPTION]... FILE... [DEST]
Restore files or directories from the trash can

FILEs and DEST are relative to . unless absolute

  -c --config=CONFIG      specifies which set of configuration directive should apply
  -r --pre-args=ARGS      args to send to the pre_hock_script
  -o --post-args=ARGS     args to send to the post_hock_script
```

```
Usage: pcan [-c config|-a] [-e]
Deletes the current user's canned files that are due to be purged.

  -c --config=CONFIG      specifies which set of configuration directive should apply
  -a --all                 purges all users canned files
  -e --empty               completely empties the trash of everything even regardless

```

---

### Post by slavik on 2007-10-06
you can instead write your own rm utility :)

---

### Post by Wybiral on 2007-10-06
> **irkengir said:**
> There are 3 scripts involved in this:[list][*]**can** - moves files to a trash can
[*]**ucan** - restores files from a trash can
[*]**pcan** - (purge can) this is usually executed daily, using cron, that permanently deletes files in the trash can if they have reached a certain age[/list]

Maybe instead of three separate programs you could just use one with parameters, like "can -u /some/file" and "can -p"?

Just a suggestion (users would probably prefer them all in one place).

---

### Post by irkengir on 2007-10-07
> Maybe instead of three separate programs you could just use one with parameters, like "can -u /some/file" and "can -p"?Thinking from an implementation point of view I think that will be harder to do. Besides you won't want to ucan or pcan very often.

Should I call them can, canu and canp instead perhaps? I was just thinking about how it's mount and umount.

---

### Post by bobbocanfly on 2007-10-07
can: can <file>
```
mv $1 ~/.Trash
```

ucan: ucan <file> <destination>
```
mv ~/.Trash/$1 $2
```

pcan:
```
rm -rf ~/.Trash/*
```

Dunno if itd work for directories but it works definately for files.

---

### Post by irkengir on 2007-10-07
What are you trying to say, bobbacanfly?

That is a simple solution but it hardly does everything that can would.

---

### Post by bobbocanfly on 2007-10-07
If someone came on here looking for a CLI trashcan but didnt want to compile a CPP program or whatever its just 3 simple lines you could even alias to something.

---

### Post by gnusci on 2007-10-07
can_dir:

```

> cp -R dir_name ~/.trash && rm -rfR dir_name/* && rmdir dir_name

```

---

### Post by slavik on 2007-10-07
> **bobbocanfly said:**
> can: can <file>
```
mv $1 ~/.Trash
```

ucan: ucan <file> <destination>
```
mv ~/.Trash/$1 $2
```

pcan:
```
rm -rf ~/.Trash/*
```

Dunno if itd work for directories but it works definately for files.
it would work for directories. :)

---

### Post by bobbocanfly on 2007-10-07
> **gnusci said:**
> can_dir:

```

> cp -R dir_name ./trash && rm -rfR dir_name/* && rmdir dir_name

```

Well thats can finished, which newbies good idea are we going to ruin next ? :)

---

### Post by aks44 on 2007-10-07
> **bobbocanfly said:**
> Well thats can finished, which newbies good idea are we going to ruin next ? :)

Now you just need to remember the restore (= original) path, and make it compatible with other trashcan systems (eg. KDE's, I know nothing about Gnome/XCFE/... but I assume they have one too, but is it the same?).

Oh my, I guess I just ruined your "brilliant" yet way too simple-minded approach of the problem... ;)

---

### Post by winch on 2007-10-07
You could implement the [freedesktop trash spec](http://www.freedesktop.org/wiki/Specifications/trash-spec).

That way it would tie in with the desktop.

---

### Post by irkengir on 2007-10-10
[quote="bobbocanfly"]Well thats can finished, which newbies good idea are we going to ruin next ?[/quote]I don't see how you've ruined my idea. That's just moving a file. It's error pone, not configurable, you can't add extra behaviour to it, and it's more typing.
> make it compatible with other trashcan systems (eg. KDE's, I know nothing about Gnome/XCFE/... but I assume they have one too, but is it the same?).Yeah that sounds like a good idea.> You could implement the freedesktop trash spec.

That way it would tie in with the desktop. Cool thanks for that link winch.

---

### Post by gerrywastaken on 2010-05-24
Great work on the spec irkengir. It's sad that this functionality hasn't already been included by default.

---

### Post by bitinerant on 2010-07-10
For those in search of this sort of functionality, see the Ubuntu package:

[INDENT][COLOR="Navy"]trash-cli[/COLOR][/INDENT]

and another tool discussed here:

[INDENT][COLOR="Navy"][http://ubuntuforums.org/archive/index.php/t-787535.html](http://ubuntuforums.org/archive/index.php/t-787535.html)[/COLOR][/INDENT]

---

