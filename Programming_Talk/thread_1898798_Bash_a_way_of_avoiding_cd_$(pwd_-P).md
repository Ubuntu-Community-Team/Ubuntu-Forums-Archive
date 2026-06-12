---
title: "Bash: a way of avoiding cd $(pwd -P)"
date: 2011-12-22
forum: Programming Talk
---

### Post by jhonan on 2011-12-22
I've created some soft linked directories to make CD-ing easier.

But when I CD to these dirs, I want to be located in the actual linked dir. So I always end up doing two steps. For example;

[FONT=Courier New]~$ cd my_dir (my_dir is a soft link)
~/my_dir$ cd $(pwd -P)
~/stuff/something/dir/long/name$[/FONT]

I want to avoid having to do [FONT=Courier New]cd $(pwd -P)[/FONT] each time - Is there any way of doing a 'cd' but telling it to go to the actual source dir, and not the soft link?

---

### Post by Lars Noodén on 2011-12-22
Wouldn't [font=Courier New]cd -P[/font] do the same thing?  You could make an alias for [font=Courier New]cd[/font] that does it for you.

```

alias cd='cd -P'

```

---

### Post by hakermania on 2011-12-22
**EDIT: hadn't seen Lars answer. OWNED :P It's funny how many things I don't know about simple commands like 'cd' which I think I rule :P**

Hello!
Put this in the end of your '.bashrc' file, located in your home directory:
```

function qw {
   cd $1;
   cd "$(pwd -P)"
}

```Name the function as you wish (I named it 'qw')
Close the terminal and open a new terminal window so as to read from the .bashrc file again.

Now type
```

qw symbolic_link

```and you will be guided to your actual dir instead.
Exapmle usage ('hello' is symbolic to '/')"
```

alex@MaD-pc:~$ file hello
hello: symbolic link to `/'
alex@MaD-pc:~$ cd hello
alex@MaD-pc:~/hello$ pwd -P
/
alex@MaD-pc:~/hello$ cd ~
alex@MaD-pc:~$ qw hello
alex@MaD-pc:/$ pwd
/

```

---

### Post by jhonan on 2011-12-22
> **Lars Noodén said:**
> Wouldn't [FONT=Courier New]cd -P[/FONT] do the same thing?  You could make an alias for [FONT=Courier New]cd[/FONT] that does it for you.

```

alias cd='cd -P'

```
Sweet, it works! I knew there'd be an easy answer.

Oh and thanks for the alternative solution hakermania anyway ;)

---

