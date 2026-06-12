---
title: "Terminal Issue"
date: 2022-08-18
forum: New to Ubuntu
---

### Post by dmacpeak on 2022-08-18
I am trying to give sudo privileges to a new user and when I am asked for my password it won't let me enter it.  It's a white colored blinking small square &#11036;, but I can't type anything.....
Any thoughts on why it won't let me enter my password?

---

### Post by &amp;KyT$0P# on 2022-08-18
It is supposed to look like nothing is happening even when it actually does register.  Did you try just typing your password and hitting Enter anyway?

---

### Post by ActionParsnip on 2022-08-19
When you type your password to use sudo you will not get any feedback. It is being accepted. Just keep typing and hit ENTER

---

### Post by dmacpeak on 2022-08-19
When I try to add sudo privileges for another user in the terminal it won't let me enter a password after it request one. There's a white blinking line that won't let me type anything.
Anyone know what I'm doing wrong?

---

### Post by dmacpeak on 2022-08-19
That makes more sense. Will it give me an indication that the command was executed successfully or do I need to test for it somehow?

---

### Post by oldfred on 2022-08-19
Duplicate threads merged.
Please do not post same question more than once.

Either command works or you get an error message to try again.

---

### Post by The Cog on 2022-08-19
As a general rule in both Unix and Linux command line, if a command is successful it says nothing and just returns. If it fails for any reason then it will print an error message.
The absence of a message proclaiming "I did it OK" message can be disconcerting to users coming from DOS/Windows, but it's pretty-much universal, and something you will get used to.

---

### Post by dmacpeak on 2022-08-19
Thank you Cog. It's all new to me so I default to assuming I'm doing something wrong. Thanks for the schooling...

---

### Post by TheFu on 2022-08-19
> **dmacpeak said:**
> Thank you Cog. It's all new to me so I default to assuming I'm doing something wrong. Thanks for the schooling...

Here's a beginner book that can be downloaded without any hassles:  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Lots of basic questions are answered.

---

