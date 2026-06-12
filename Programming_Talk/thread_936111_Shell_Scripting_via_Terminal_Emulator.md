---
title: "Shell Scripting via Terminal Emulator"
date: 2008-10-02
forum: Programming Talk
---

### Post by Rich78 on 2008-10-02
Hi,

I know this is a very newbie question but I've been looking at some shell scripting and came across the following example:

$ echo -e "\033[34m   Hello Colorful  World!"
Hello Colorful  World!

The above example doesn't work for me. I'm using RedHat 9 via Reflections terminal emulator at work.

If I run the above I get the following output:  "bash: !": event not found".

I've found that it blows up when I echo "!".  But I don't know why bash treats "!" as a non string character I assume it must act as an escape sequence.  But then why is it included in an example and why would it not work for me?

I've also found that echo -e "\033[34m Hello Colorful World"
Just responds with "Hello Colorful World" with no color difference applied to the text.  Is this because it's through a terminal emulator?  

Thanks

---

### Post by Rich78 on 2008-10-02
Sorry further reading suggests it needs to be based on an ANSI terminal to understand the escape sequences which is obviously why the colour didn't apply.

Is there any other escape sequences I could use for my terminal instead?

Also is doesn't answer why echo "!" blows up?

Thanks again.

---

