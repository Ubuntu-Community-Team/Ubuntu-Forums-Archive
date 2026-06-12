---
title: "exec() PHP + apache - commands not being executed"
date: 2008-06-06
forum: Programming Talk
---

### Post by henryrhenryr on 2008-06-06
Hi

I'm quite new to Ubuntu (ie 1 week) so I might be making a glaring error... bare with me...

I have a PHP system to run commands (running a java programme) via the exec() PHP command.  Basically this executes a command as if you were in terminal.

My PHP scripts work fine.  When I echo the exact command it creates and input that directly into terminal, the command runs as expected.  When I run the command from the PHP script, it doesn't run at all.

Could this be something to do with priveleges that apache has?  Or would it be a restriction in PHP?

I think it's the apache priveleges.  How do I launch apache as a different user to try it out...  I've been launching with Sudo - that makes it root right?

Thanks for any tips/advice!

Henry

---

