---
title: "'if' statement logic"
date: 2021-02-20
forum: Programming Talk
---

### Post by jcdenton1995 on 2021-02-20
Edit 2: Found this in the Bash info page after some reading> expression1 && expression2
                     True if both expression1 and expression2 are true.
              expression1 || expression2
                     True if either expression1 or expression2 is true.

              The  &&  and || operators do not evaluate expression2 if the value of expression1 is sufficient to determine the return value of
              the entire conditional expression.So that pretty much solves it.

Hello all,

I've been spending a few hours playing around with this and working out how to express my question as clearly as possible. Basically it's a question about the logic of Bash 'if' statements and how they evaluate the conditional expressions which follow them.

**Question: does an 'if' statement evaluate the return value of every command which follows it, or just the last one executed by the shell?**

Now as far as I can tell, the two alternative possibilities are actually practically the same (at least as far as I can tell based on my five minutes of bash scripting) but I'm not sure whether  there is a distinction between them when dealing with some more advanced scenarios that I haven't encountered yet. I'll explain why I think this and then someone might be able to point me in the right direction.

So as far as I am aware, there are two logical operators which can be used to chain commands; 'AND' and 'OR'. When evaluating a list of commands chained together using 'AND', practically only the return value of the final command executed by the shell is important, because it is either the final command in the chain, or it is not the final command in the chain but it has failed and that *makes it *the final command as any subsequent commands are disregarded.

Similarly, in a chain of commands linked using OR, the shell executes each command in turn until one of the commands succeeds. This means that practically the first successful command, which also makes it the last command executed, is the only command that 'if' needs to evaluate

I hope that makes sense, I suppose its a question more about the underlying logic of 'if' as opposed to anything else.

I'd love to hear some other peoples thoughts.

Edit: The following is all that I could find in the Bash info pages, and I don't feel like it really answers my question:> if list; then list; [ elif list; then list; ] ... [ else list; ] fi
              The if list is executed.  If its exit status is zero, the then list is executed.  Otherwise, each elif list is executed in turn,
              and if its exit status is zero, the corresponding then list is executed and the command completes.  Otherwise, the else list  is
              executed, if present.  The exit status is the exit status of the last command executed, or zero if no condition tested true.

---

### Post by TheFu on 2021-02-20
Websearch   "absg bash"

These questions can be tested. Try it and see.

---

### Post by jcdenton1995 on 2021-02-23
> **TheFu said:**
> Websearch   "absg bash"

These questions can be tested. Try it and see.

Thanks, the course you linked to looks pretty good, it' something I can move onto after the one I'm doing right now.

---

### Post by TheFu on 2021-02-23
> **jcdenton1995 said:**
> Thanks, the course you linked to looks pretty good, it' something I can move onto after the one I'm doing right now.

I use it for reference - to learn exactly what I need to know "now", as it relates to bash.  But as soon as any bash script gets over 1 page (25 lines, including comments), I'll switch to a better scripting language that supports arrays and associated arrays (hashes) much easier.  Yes, bash does support those things, but the grammar is next to impossible to actually type and read. Give me perl over that, any day. It is fairly common to have arrays inside hashes to keep entire related data together. That's where bash really gets too hard to deal with for me.

But I will admit that bash is much more capable than I've ever given it a chance to prove in my scripting.

---

