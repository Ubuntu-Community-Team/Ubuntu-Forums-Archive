---
title: "Test if shell script is called from a GUI session?"
date: 2013-02-06
forum: Programming Talk
---

### Post by Ranko Kohime on 2013-02-06
Is there a way to test if a shell script is being called from a GUI session?

---

### Post by nvteighen on 2013-02-06
> **Ranko Kohime said:**
> Is there a way to test if a shell script is being called from a GUI session?

What do you mean by "being called from a GUI session"? Whether the script has been called from a terminal emulator (as opposed to the console)? Or whether a script has been called from a GUI program in general (e.g. via system(), popen(), etc.).?

In any case, I don't really get why the importance of this. If you're the shell script, you shouldn't really care where you are run from, but just do what you are supposed to do. Care to elaborate?

---

### Post by jwbrase on 2013-02-06
> **nvteighen said:**
> In any case, I don't really get why the importance of this. If you're the shell script, you shouldn't really care where you are run from, but just do what you are supposed to do.

Sometimes what you're supposed to do may depend on where you're run from. For example, you may want to use zenity dialogs as your interface if you're running under X, but fall back to a text interface if not.


@OP:
You can test to see if your program is running under X by testing to see if the "display" environment variable is defined.

```
if[ -n $DISPLAY ]
then
#Stuff to do if running under X
else
#stuff to do if not running under X
fi
```

This won't work if your OS uses something other than X for its GUI, but that's not an issue *yet* on most Unix-like systems (but MacOS/iOS and Android are prominent exceptions, and Wayland may eventually replace X on other Unix-likes).

---

### Post by sisco311 on 2013-02-07
> **jwbrase said:**
> Sometimes what you're supposed to do may depend on where you're run from. For example, you may want to use zenity dialogs as your interface if you're running under X, but fall back to a text interface if not.


@OP:
You can test to see if your program is running under X by testing to see if the "display" environment variable is defined.

```
if[ -n $DISPLAY ]
then
#Stuff to do if running under X
else
#stuff to do if not running under X
fi
```

This won't work if your OS uses something other than X for its GUI, but that's not an issue *yet* on most Unix-like systems (but MacOS/iOS and Android are prominent exceptions, and Wayland may eventually replace X on other Unix-likes).

Then, I'd use the good old `trial and error' method:

```

if zenity "$z_options"
then
    printf '%s\n' "zenity is it" >&2
elif dialog "$d_options"
then
    printf '%s\n' "hurray, we are using dialog" >&2
else
    printf '%s\n' "err" >&2  
fi 

```

---

### Post by Ranko Kohime on 2013-02-07
> **nvteighen said:**
> What do you mean by "being called from a GUI session"? Whether the script has been called from a terminal emulator (as opposed to the console)? Or whether a script has been called from a GUI program in general (e.g. via system(), popen(), etc.).?

In any case, I don't really get why the importance of this. If you're the shell script, you shouldn't really care where you are run from, but just do what you are supposed to do. Care to elaborate?
Oh, right.  Forgot the purpose.  :oops:

My script is long running, and its going to be putting out status messages.  If I'm in a CLI session, I want to echo those directly to the screen.  If I'm in a terminal emulator, though, (and it probably won't be called from another program than an emulator) I want to route it through notify-send.

---

