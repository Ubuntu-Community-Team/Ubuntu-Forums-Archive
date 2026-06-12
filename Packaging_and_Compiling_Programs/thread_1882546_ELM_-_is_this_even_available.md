---
title: "ELM - is this even available?"
date: 2011-11-17
forum: Packaging and Compiling Programs
---

### Post by zim2dive on 2011-11-17
Anyone gotten this to compile in 11.10?

I had several versions of source squirreled away.. some fail in Configure, others in make.

---

### Post by oldos2er on 2011-11-17
Post moved to its own thread.

---

### Post by gmargo on 2011-11-17
While I have not tried to compile **elm**, I just wanted to point out the **mutt** mail client, which by its own admission is very elm-like (and currently maintained.)  This is what I currently use (and I was an elm-user way back when.)

---

### Post by zim2dive on 2011-11-17
> **gmargo said:**
> While I have not tried to compile **elm**, I just wanted to point out the **mutt** mail client, which by its own admission is very elm-like (and currently maintained.)  This is what I currently use (and I was an elm-user way back when.)

Yep, I know mutt and have tried to convert.. and just can't :)

---

### Post by zim2dive on 2011-11-18
I got it to compile.. I had a makefile already from the configure on an earlier Ubuntu.. so I skipped configure.. and ran make... make was pointing to the wrong libcrypt, so I ran make until it failed, and then did a cd to the src dir, and ran ```
cc -o ../bin/elm addr_util.o alias.o aliaslib.o args.o a_edit.o a_screen.o a_sendmsg.o a_sort.o a_quit.o bouncebk.o builtin.o calendar.o chstatus.o curses.o date.o delete.o edit.o editmsg.o elm.o encode.o fbrowser.o file_ops.o file_util.o fileio.o find_alias.o forms.o hdrconfg.o help.o in_utils.o init.o leavembox.o lock.o limit.o mime.o newmbox.o options.o out_utils.o pattern.o quit.o read_rc.o reply.o returnadd.o save.o save_opts.o savecopy.o screen.o showmsg.o showmsg_c.o signals.o sndattach.o sndhdrs.o sndmsg.o sndpart_io.o sndpart_lib.o softkeys.o sort.o string2.o strings.o syscall.o utils.o wordwrap.o ../lib/libutil.a /usr/lib/x86_64-linux-gnu/libcrypt.a -lcurses
```

I have a working binary again.  Somewhere a dinosaur is smiling (but I am too)

---

### Post by gmargo on 2011-12-11
I just ran across this web site, via freecode.com:

"Elm Millennium Edition"
[http://freecode.com/projects/elmme](http://freecode.com/projects/elmme)
[http://www.elmme-mailer.org/](http://www.elmme-mailer.org/)

---

