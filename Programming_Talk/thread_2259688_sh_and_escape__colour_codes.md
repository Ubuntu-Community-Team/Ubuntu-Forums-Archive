---
title: "sh and escape / colour codes"
date: 2015-01-06
forum: Programming Talk
---

### Post by frankerooney on 2015-01-06
Hi all,
  This is sh / bash related which is programming related, sort of, isn't it?
In newer versions of ubuntu, the below doesn't work in sh :

echo -e "\e[31m"
echo "I should be in RED"
echo -e "\e[0m"

In previous versions it does, and it continues to work in bash. I don't want to particularly use bash as it's part of the message of the day scripts which seem to always use sh, and it always used to work in previous versions.
Anyone know why / how I fix it?
Tried in 13.10/14.10, and it doesn't work in either, but did in 13.04 as far as I can gather.

Thanks
andy

---

### Post by Gustaf_Alhll on 2015-01-06
What is the output when you run it? When I do it, it says:
-e \e[42mText
or is there a syntax error?
Otherwise, we both might have the same issue.
If it doesn't, I have a simlar issue: The -e after echo is mostly ignored and shown in the output instead, making it impossible to make proper escape codes in the echo command.

This is strange, considering that it works at random. In most cases, though, it doesn't.

---

### Post by Lars Noodén on 2015-01-06
The built-in [echo](http://manpages.ubuntu.com/manpages/trusty/en/man1/bash.1.html) is different in bash than in [dash](http://manpages.ubuntu.com/manpages/trusty/en/man1/dash.1.html) (sh)  If you use the program [/bin/echo](http://manpages.ubuntu.com/manpages/trusty/en/man1/echo.1posix.html) instead then you will get the same results regardless of which shell you try.

```

/bin/echo -e "\e[31m"
/bin/echo "I should be in RED"
/bin/echo -e "\e[0m"

```

---

### Post by frankerooney on 2015-01-06
Hi,  

  @ Gustaf - it just ignores the -e flag and echoes what you put in back out again without actually doing the escape.
  @ Lars - the absolute path does seem to work, despite "which echo" pointing at that same executable. I guess echo is a build in interpreter function in this case or something. Weird that it used to work in earlier versions..
Thanks, that's sorted things I think.
Andy

---

### Post by schragge on 2015-01-06
Up to dapper (Ubuntu 6.06), /bin/sh was a symbolic link to /bin/bash, since Ubuntu 6.10 it points to /bin/dash, see [uwiki]DashAsBinSh[/uwiki], especially  [uwiki]DashAsBinSh#echo[/uwiki]. Where were you hiding all that time?

BTW,
```
sh -c 'echo "\33[31m red \33[0m"'
``` works in dash, but is not recommended to use. Instead, you should use *printf*, which is more portable:
```
sh -c 'printf "Show the next message in red: \33[31m%s\33[0m\n" "Mayday! Mayday!"'
```

---

### Post by Holger_Gehrke on 2015-01-07
Wouldn't it be slightly more readable and portable to use 'tput' with a terminfo capability name instead of escape-sequences ? For example 'tput setaf 1' for 'set a foregroundcolour red'.

---

