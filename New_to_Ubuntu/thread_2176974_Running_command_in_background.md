---
title: "Running command in background"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by klim2 on 2013-09-26
Hi Everybody,
could you please tell me why the following command doesn't release terminal:
find / filename > findout &

I expected the command to release my terminal and redirect output to file findout.
Instead the output was still displayed on the terminal and I didn't get the command prompt.

Thanks
Klim

---

### Post by 3246251196 on 2013-09-26
> **klim2 said:**
> Hi Everybody,
could you please tell me why the following command doesn't release terminal:
find / filename > findout &

I expected the command to release my terminal and redirect output to file findout.
Instead the output was still displayed on the terminal and I didn't get the command prompt.

Thanks
Klim

```
find / | grep filename &> findout &
```

&> redirects all to findout,
i personally use pipe grep for looking for filename but you can also use
```
find / -name "filename"
```

---

### Post by qamelian on 2013-09-26
To release the terminal, enclose the entire command in parentheses:
```
(find / filename > findout &)
```

---

### Post by klim2 on 2013-09-27
@[**[COLOR=#000000]qamelian[/COLOR]**]("http://ubuntuforums.org/member.php?u=8229"), not sure what I did wrong but the parentheses didn't help. I still got the output sent to the terminal, not findout file.

@[**[COLOR=#000000]3246251196[/COLOR]**]("http://ubuntuforums.org/member.php?u=1258334"), thanks! the following command did the trick:

find / -name "filename" &> findout &

What is interesting that only one background process was started. I still can't explain to myself why it works. 
Is it documented somewhere?

---

### Post by Lars Noodén on 2013-09-28
There is only one process running, it is "find".  The [**&>** redirects both stdout and stderr](http://www.tldp.org/LDP/abs/html/io-redirection.html) to the same file.  You can have more I/O streams than that if you set it up explicitly, but by default you have stdout and sterr for your programs' output.

---

