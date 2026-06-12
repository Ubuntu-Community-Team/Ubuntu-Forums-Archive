---
title: "THE SHELL, a proposal to the Linux administration inclined"
date: 2007-09-10
forum: Programming Talk
---

### Post by slavik on 2007-09-10
The idea is simple, pick a tool/command that you find very useful/neat and start a thread on it, describing it's usefulness and neatnet. I'll start. :)

I'll start with xargs.

basic xargs usage:
xargs <command>

explanation:
xargs reads from stdin and calls the command with what it read as the argument to the command.

simple usage:
echo filename | xargs rm

complex use:
if, for example, you need to find files that match a certain criteria (and there are a lot of them) and remove them, you could run find and then pipe the find output to xargs with rm being the command.

basically, xargs will call <command> on each arguement for <command> but not only that, it will try to fit as many argument to <command> as allowed by the shell. so, in example, rm could be run with 1000 files, if their names fit :)

---

### Post by the_unforgiven on 2007-09-10
> **slavik said:**
> The idea is simple, pick a tool/command that you find very useful/neat and start a thread on it, describing it's usefulness and neatnet. I'll start. :)

I'll start with xargs.

basic xargs usage:
xargs <command>

explanation:
xargs reads from stdin and calls the command with what it read as the argument to the command.

simple usage:
echo filename | xargs rm

complex use:
if, for example, you need to find files that match a certain criteria (and there are a lot of them) and remove them, you could run find and then pipe the find output to xargs with rm being the command.

basically, xargs will call <command> on each arguement for <command> but not only that, it will try to fit as many argument to <command> as allowed by the shell. so, in example, rm could be run with 1000 files, if their names fit :)
Not only that, but xargs is mainly used to overcome the various shell limits (like no. of chars in the command line or no. of command line arguments etc.) which can easily become a hindrance for an automated script.
For more details, check out the manpage of [xargs]("http://linux.die.net/man/1/xargs"). It's quite a versatile tool.

---

