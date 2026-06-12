---
title: "help connecting to server"
date: 2008-10-12
forum: Programming Talk
---

### Post by tima1 on 2008-10-12
Hi, I was wondering if this is somehow possible in ubuntu:

connect to my university's server and be able to edit and run my c programming files that are stored there.

I think Im looking for something like putty but I don't know how to install it.

Thank You

---

### Post by sillv0r on 2008-10-12
Hi,

* Is your question that you usually use PuTTy to connect to your school and you would like to know the ubuntu/linux equivalent of PuTTy?

I'm using Ubuntu 8.04.

I simply SSH in to my university's server.  I figure your school ought to have a server to which you can remote into.

---

### Post by tima1 on 2008-10-12
> **sillv0r said:**
> Hi,

* Is your question that you usually use PuTTy to connect to your school and you would like to know the ubuntu/linux equivalent of PuTTy?

I'm using Ubuntu 8.04.

I simply SSH in to my university's server.  I figure your school ought to have a server to which you can remote into.

Yes I use putty when i log in to windows (dual-boot) but I would much rather do it from ubuntu using the equivalent.

And how do I start/use SSH?

---

### Post by sillv0r on 2008-10-12
Using a variant of my usual login procedure:

```
ssh universitylogin@127.0.0.1
```

Where the 127.0.0.1 is the ip address of your university's server.

Note: You don't have to use the ip address.  If you know the server's host name/domain you can simply use that.

For example:

```
ssh user@remotemachine.example.com
```

Does this help?

---

### Post by tima1 on 2008-10-12
> **sillv0r said:**
> Using a variant of my usual login procedure:

```
ssh universitylogin@127.0.0.1
```

Where the 127.0.0.1 is the ip address of your university's server.

Note: You don't have to use the ip address.  If you know the server's host name/domain you can simply use that.

For example:

```
ssh user@remotemachine.example.com
```

Does this help?

Yes thanks! I've been able to login successfully. But now I have another problem :(

when i connect and navigate toward my c files, i type in emacs filename.c and what happens is the code is shown in my terminal even though i installed emacs on ubuntu. Is there any way I can modify it so that when i connect to my university server and type in emacs filename.c and it pops up into the emacs window? 

I've been able to do it in windows by using Xming + Putty + Emacs (windows version) but its realllly slow

---

### Post by Zugzwang on 2008-10-12
> **tima1 said:**
> Yes thanks! I've been able to login successfully. But now I have another problem :(

when i connect and navigate toward my c files, i type in emacs filename.c and what happens is the code is shown in my terminal even though i installed emacs on ubuntu. Is there any way I can modify it so that when i connect to my university server and type in emacs filename.c and it pops up into the emacs window? 

I've been able to do it in windows by using Xming + Putty + Emacs (windows version) but its realllly slow

It will be as slow here - Try adding the "-X" parameter to the ssh command "ssh -X [email]me@myserver.com[/email]". I would strongly suggest to copy your C files to your local machine and work on them there. There are also "advanced" tools for version control which help you in automatically synchronising your code, such as CVS, SVN, Mercurial, and so on. Use google for tutorials on these (if you have enough time to look into them).

---

### Post by sillv0r on 2008-10-12
* It sounds like you want to open a remote file using your local emacs installation.

mmm.  Now you're getting into territory that I'm not sure about.

For what it's worth, this is what I usually do when working on projects and testing on my university's computers:

1) I work on code locally in my favorite editor.
2) Test locally.
3) Upload to server using sftp.
4) ssh in and verify test results are the same.

Note: You can also use sftp to download the file for editing.

If you want to do something else, hopefully someone else will jump in and be of further assistance.

---

### Post by tima1 on 2008-10-12
Allright thanks sillv0r & Zugzwang! I tried adding -X and you were right Zugzwang its just as slow :) so I think i'll just work locally and then upload the files like sillv0r says

---

