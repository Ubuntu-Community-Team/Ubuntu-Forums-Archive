---
title: "Shell programmimg help (bash) - Please...."
date: 2007-03-22
forum: Programming Talk
---

### Post by sunshine803 on 2007-03-22
Hello everybody. This is my first post in your forums. My Ubuntu experience is 3 days old but my Unix experience goes back a few years. I look forward to learn from your experiences and contribute where I can :) 

I am trying to use some Unix shellscripts I used to use on Unix machines and most of them run fine under bash. One thing that niggles me though, is the inability of the shell to interprete special characters, like   \n  or \c

In Unix, with say:  echo "\n\nHello Ubuntu\n\n" 
I would get 2 blank lines, followed by "Hello Ubuntu" followed by another 2 blank lines.
Or, with "Please enter Name: \c" 
I would get the prompt "Please enter Name: " without new line at the end (waiting for user to enter Name).

These do not seem to work in Ubuntu. I get the \n and \c printed out, ie it takes them as literal characters.

I am sure there MUST be a way but I do not know how or where to find it. I tried "man shell" but I still can't get it to work the way I want it. Any advice PLEASE?.... :confused: 

Thanks and best regards

---

### Post by silas_irl on 2007-03-22
try 'man echo'

according to my version of echo the switch -e tells it to interpret backslash escape sequences.

So for example: > echo -e "Please enter Name: \c"

You can turn this off with echo -E, which must be the default behavour.

---

### Post by sunshine803 on 2007-03-22
Thanks Silas,
but I tried it and it makes no difference. Same result.
Is there a way I can switch to another shell by the way, like csh or preferebly Bourne shell (same as the Unix one I am used to)?

Regards

---

### Post by Mr. C. on 2007-03-22
Something you are doing is incorrect then. 

```
$ echo -e "hello"
hello
$ echo -e "\n\n\nhello\n\n\n"



hello



$ echo -e "hello\c"
hello$
```

Show your output if you believe this is not working.

You can change your shell via chsh or editing /etc/passwd.

```
man chsh
```

MrC

---

### Post by sunshine803 on 2007-03-23
Thank you Mr C,
your example helped me 'click'
I thought the -e was a mode that youset it and stays in it, ie

echo -e
echo "\n\n\nHELLO\n\n\n"
echo -E

I knew I was doing something wrong...
I wish the echo -E was not the default. Must add -e to all 'echo' lines of my scripts but it will be a one-off job...  

Thanks for the chsh tip too

Best regards

---

### Post by cwaldbieser on 2007-03-23
> **sunshine803 said:**
> Thank you Mr C,
your example helped me 'click'
I thought the -e was a mode that youset it and stays in it, ie

echo -e
echo "\n\n\nHELLO\n\n\n"
echo -E

I knew I was doing something wrong...
I wish the echo -E was not the default. Must add -e to all 'echo' lines of my scripts but it will be a one-off job...  

Thanks for the chsh tip too

Best regards

You could also try using "printf", which seems to respect some escape sequences by default.
```

$ printf "\n\n\nHELLO\n\n\n"



HELLO




```

---

### Post by Mars8082686 on 2007-03-23
> **sunshine803 said:**
> Thank you Mr C,
your example helped me 'click'
I thought the -e was a mode that youset it and stays in it, ie

echo -e
echo "\n\n\nHELLO\n\n\n"
echo -E

I knew I was doing something wrong...
I wish the echo -E was not the default. Must add -e to all 'echo' lines of my scripts but it will be a one-off job...  

Thanks for the chsh tip too

Best regards

why don't you just use:
alias echo="echo -e" then every time you use echo it will interpret the special characters without you having to constantly type the -e flag.

---

