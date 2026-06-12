---
title: "Shell in Vim"
date: 2007-06-12
forum: Programming Talk
---

### Post by ankursethi on 2007-06-12
Is there any way to run the shell in a sort of buffer under Vim? (Like you can do in Emacs) I hate the :shell command because I can't switch between buffers while using it.

---

### Post by Modred on 2007-06-15
You could always do a temporary escape by prefixing your command with an exclamation point.  Like the following:

!ls

Lists your current directory, then waits for you to press enter to jump back into the buffer.  Need to keep the output from your command in the buffer?  Try combining the ! with a r command.

r!ls

This performs the command and then reads the standard output from the command into your current buffer.  It might not be exactly what you're looking for, especially if you're expecting to run something interactively while also editing files.  But for simple things like restarting a web server, or getting a list of files, or grepping something, this should be adequate.  You can also specify a line number to read into, such as 10!ls to put the results starting on line 10.

If you aren't afraid of compiling from source, you might want to check out [VIM-shell](http://www.wana.at/vimshell/).  I've compiled my own VIM before and it's not so bad, provided you remember to enable all the features you want (I forgot omni-completion support for a few languages the first time around...).  Of course, if you compile from source, you dont have the benefit of using Syntaptic or another package manager to check the dependencies and easily uninstall and all that.  But I really don't think it's such a trouble.

---

### Post by ankursethi on 2007-06-16
I think I'll just manage by using tabs in the GNOME terminal and screen when in CLI mode. Thanks all the same :-)

PS : The application I'm compiling is an Ncurses based one. Doesn't play well with Vim.

---

