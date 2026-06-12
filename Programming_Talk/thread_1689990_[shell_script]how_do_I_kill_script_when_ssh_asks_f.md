---
title: "[shell script]how do I kill script when ssh asks for a password"
date: 2011-02-17
forum: Programming Talk
---

### Post by RocketRanger on 2011-02-17
Hi

I'm trying to create a bash script that is supposed to run at boot. When the script tries to connect via ssh it will sometimes ask for the public key password. Is there a way to kill it when that happens?

---

### Post by hakermania on 2011-02-19
can you make somehow a check before trying to connect via ssh so as to guess that it will ask for passwd?

---

### Post by RocketRanger on 2011-02-19
The problem turned out to be a different one entirely. I was buildig a string to pass to rsync but bash doesnt treat strings as I expected.

The problem was that I was trying to pass arguments to rsync like this:
```

rsync "$OPTIONS_BASE $DOWNLOAD_OPTIONS $SOURCE/$i $LOCAL_DIR/$i";

```

which only partially worked. It tried to connect to the correct host but instead of using my normal ssh key it would just drop straight to a keyless login, which I was trying to avoid.

I made a similar mistake a while back where someone in here, actually, pointed me to the right solution, which was to build the parameter string on a different line.
```

PARAMS="$OPTIONS_BASE $DOWNLOAD_OPTIONS $SOURCE/$i $LOCAL_DIR/$i";
rsync $PARAMS >> $LOG_FILE;

```

After I did that everything was peachy.

---

### Post by slakkie on 2011-02-19
```

function check_ssh_needs_pass() {
    local host="$1"
    ssh $host -o BatchMode=yes ls &>/dev/null
    if [ $? -eq 0 ] ; then
        echo "keybased login OK"
        return 0
    else
        echo "password required"
        return 1
    fi
}

check_ssh_needs_pass somehost

```

Add additional checks, but that is what you need.

---

### Post by RocketRanger on 2011-02-19
Now that was a fantastic trick! I tip my hat :)

---

### Post by slakkie on 2011-02-19
ty, is use something like that to copy over certain files and setup keybased logins on machines where i still have password logins..

btw, in stead of ls, you could also use echo, could be quicker. 

Btw, i think eval would have fixed your problems:

```

eval rsync "$option1 $options2" 
# or just quote each option..
rsync "$option1" "$option2"

```

---

### Post by RocketRanger on 2011-02-19
eval works fine. Simply using quotes on each option does nothing. The odd thing is that it's different for different tools. echo, for instance, works just fine no matter which solution you use.

Given this:
```

echo "rsync $OPTIONS_BASE --dry-run $LOCAL_DIR/bin $TARGET/bin";
rsync "$OPTIONS_BASE --dry-run $LOCAL_DIR/bin $TARGET/bin";

```

echo will print the correct line but rsync will fail with an "unknown option" error. Looks like the solutions are
- build a parameter string and only pass that.
- use eval to run the rsync command

---

### Post by slakkie on 2011-02-20
> **RocketRanger said:**
> eval works fine. Simply using quotes on each option does nothing. The odd thing is that it's different for different tools. echo, for instance, works just fine no matter which solution you use.

Given this:
```

echo "rsync $OPTIONS_BASE --dry-run $LOCAL_DIR/bin $TARGET/bin";
rsync "$OPTIONS_BASE --dry-run $LOCAL_DIR/bin $TARGET/bin";

```

echo will print the correct line but rsync will fail with an "unknown option" error. Looks like the solutions are
- build a parameter string and only pass that.
- use eval to run the rsync command


I ment in the ssh_need_pass function, you could use echo "" instead of ls. It is quicker (me thinks).

because you use "$OPTIONS_BASE --dry-run ..." after rsync (without eval), rsync thinks you want to use the option "$OPTIONS_BASE .. etc", why you actually want "$option1" "$option2" "$optionX" to be used for rsync. So you need to use eval to make that work.

```

OPTIONS="option1"
rsync $OPTIONS --more-options "$option4" 
# OR
eval rsync "option1 --more-options $option4"

```

---

