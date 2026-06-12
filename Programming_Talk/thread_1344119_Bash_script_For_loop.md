---
title: "Bash script For loop"
date: 2009-12-02
forum: Programming Talk
---

### Post by steviefordi on 2009-12-02
I've been writing a reasonably complex bash script for housekeeping. It reads a config file and based upon what it finds builds a number of calls to the find command.

One of the settings in the config file is a space delimited list of file masks, which I want to build into find command like so:

```
\ ( -iname 'mask1*.txt' -o 'mask2.???' -o '[0-9]mask3.old' \ )
```

As the for loop works through a space delimited list I thought it would be perfect, however bash understandably wants to glob all my masks before running through them. Quoting just breaks the output, so I've fixed it by turning off globbing:

```
set -f
For mask in $masklist; do
   cmmands
done
set +f
```

This just seems like a bit of a bodge, I mean there must be a more elegant way of doing it? If not I would at least like to check if globbing is on or off first, then do what I need to do before returning it to its original setting.

Any suggestions most appreciated.

---

### Post by DaithiF on 2009-12-02
to check for current status of globbing, you could do:
```
save_glob=$(set -o | grep noglob | cut -c5)

```and at the end of your script, reset (if needs be) by doing:
```
[[ $save_glob == + ]] && set +o noglob
```

---

### Post by steviefordi on 2009-12-03
Thanks for the tips DaithiF, that's helped me out a lot.

---

### Post by DaithiF on 2009-12-03
you're welcome.  Just to say also, in case its not clear, that even if you turn off globbing in your script, once that script exits and control returns to your shell, the state of globbing in that shell is unaffected by whatever the script did.  Your script will run as a child process and settings it changes will NOT affect the environment of its parent.  

So while you might want to restore the original state of globbing for the remainder of your script, you don't need to worry about restoring it for the benefit of the calling process.

---

### Post by steviefordi on 2009-12-08
> Just to say also, in case its not clear, that even if you turn off globbing in your script, once that script exits and control returns to your shell, the state of globbing in that shell is unaffected by whatever the script did.

Thanks, that wasn't clear. I guess it makes sense though that if running a script is equivalent of opening a subshell, the calling shell instance remains unaffected from environment changes.

---

