---
title: "Emacs + cscope (xcscope.el)"
date: 2007-10-11
forum: Programming Talk
---

### Post by iakie on 2007-10-11
Hi there:

Can anyone give me some tips on using cscope and emacs?

I was able to load xcscope.el from cscope package. However, whenever i tries to use it, it says it finds nothing.

I edited my .emacs like this:
```

(load-file "/usr/share/emacs/site-lisp/xcscope.el")
(require 'xcscope)
```

Then, I untar-ed linux kernel in my home folder, under which I ran cscope to generate search database. And I tried to edit some files

```

me@box:~/linux-source-2.6.22$ cscope -R -q -b
me@box:~/linux-source-2.6.22$ emacs kernel/time.c
```

When I tried to find symbol definition using C-c s d, it returns no matched result

```

Finding symbol: tv_nsec

Database directory: /home/me/linux-source-2.6.22/
-------------------------------------------------------------------------------
cscope: no source files found

-------------------------------------------------------------------------------

Search complete.  Search time = 0.01 seconds.
```

Can someone tell me what I did wrong?

---

### Post by tuxfan123 on 2007-12-06
Hi,

I am also facing the same problem mentioned by you in this post.  Please let me know if you were able to solve this.

Thanks
TuxFan

---

### Post by tuxfan123 on 2007-12-06
I was able to solve this problem by adding the following lines in the emacs startup file, .emacs. although I am not sure how it solved the problem.

(setq cscope-do-not-update-database t)
(load-file "/usr/share/emacs/site-lisp/xcscope.el")
(require 'xcscope)

Cheers
TuxFan

---

### Post by &#26446;&#23572;&#26480; on 2008-08-20
But I think it is because you didn't use abs path  s to make the cscope database. Then when you lingered to other directories it can't find appropriate definitions.

---

### Post by mkokotovich on 2009-01-16
I'm guessing no one cares anymore, but in case someone stumbles upon this while searching (like I did) here is what worked for me:

Like suggested, put
```
(load-file "/usr/share/emacs/site-lisp/xcscope.el")
(require 'xcscope)
```
in your .emacs file.

Then, if you have code in ~/mycode, cd to that directory and run 
```
myusernam@mycomputer:~/mycode$ cscope-indexer -r
```
That should generate the required files. Then you can just open any file in emacs and cscope should work.

---

### Post by mwatt on 2009-03-09
Well I care mkokotovich. Thanks for your post. That just solved the problem for me, specifically using the command cscope-indexer to generate the index rather than just running cscope itself.

---

### Post by aijazbaig1 on 2010-03-16
Having faced a similar ordeal, I tried the suggestions in this thread by changing my .emacs file to include 
```
(load-file "/usr/share/emacs/site-lisp/xcscope.el") 
```
After having done that, as mkokotovich suggested, I tried to run the cscope-indexer on the top level directory of my src tree.

It gave me:
```
/usr/bin/cscope-indexer: line 142: cscope.files: No such file or directory
```
Finally I opened a sample file and ran 
```
cscope-find-this-symbol
```
which gave me the list of all places that has that symbol (defined or declared or used). I chose a sample line and pressed return hoping cscope would take me to the relevant src file. But instead I got:
```
*path to file* is not readable or exists
```
Additionally, to be specific I am trying to create a database of the linux kernel src tree. As a test I opened the file */include/linux/skbuff.h* and then searched for the symbol ***sk_buff*** which is declared in the file. It gives me a long list of all the files containing that symbol. On clicking one of the entries in the list I get the following
```
/usr/src/linux/include/linux**/include/linux/**skbuff.h does not exist or is not readable
```
Closely examine the line above. The substring in bold face is something that seems to have come from nowhere. The actual path is */usr/src/linux/include/linux/skbuff.h* so there must be something wrong in the set up of cscope here. 

Kindly let me know what mistake am I doing.

Regards,
Aijaz

---

### Post by mkokotovich on 2010-03-16
Let's handle one problem at a time here. First, cscope-indexer. That shouldn't be spitting out any errors like that. Can you describe exactly how you ran it? (i.e. which directory you were in, who you were logged in as, what arguments you supplied, etc)

Then, if you want to open /usr/bin/cscope-indexer in a text editor (it is a script) and copy and paste lines 130-150 into your reply. Hopefully we can figure out why it is failing.

---

### Post by aijazbaig1 on 2010-03-17
Hello people,

@mkokotovich:
> Can you describe exactly how you ran it? (i.e. which directory you were in, who you were logged in as, what arguments you supplied, etc)
I was in the top level directory of my linux kernel source tree where I ran the cscope-indexer in a shell as a super user. The way I ran it was exactly like what you mentioned in your last post. Like so ```
/usr/bin/cscope-indexer -r
```

Well I didn't knew it is a script. Nonetheless, now my cscope seems to be working for some strange reason. Well I would try opening the script in an editor and see whats inside.
> 
Then, if you want to open /usr/bin/cscope-indexer in a text editor (it is a script) and copy and paste lines 130-150 into your reply.
Do you mean I should first run the indexer like before and then if it fails I should copy those lines (so you can see the arguments and other variables it might have been working on)?

Keen to hear from you,

---

### Post by yotam on 2010-03-17
I am using 'ascope.el' (627 lines) written by Staton Sun
that I got from him  sunnycamel-AT-gmail-DOT-com.
It works fine form me. I wish I could attach it here.

---

### Post by mkokotovich on 2010-03-17
> **aijazbaig1 said:**
> 
Do you mean I should first run the indexer like before and then if it fails I should copy those lines (so you can see the arguments and other variables it might have been working on)?

Yeah, I was trying to see where in the script it was failing. If you cscope is working now though, it isn't that important anymore :)

---

### Post by post4pavan on 2011-09-27
[FONT=Book Antiqua][SIZE=3]Hi, Can you guide me, how to configure cscope in emacs, right from the beginning.[/SIZE][/FONT][FONT=Book Antiqua]
[/FONT]

---

### Post by yotam on 2011-09-28
May I suggest trying ascope.el (attached gz-zipped)
by Staton Sun <sunnycamel AT gmail DOT com>.

---

### Post by post4pavan on 2011-12-07
[FONT=Comic Sans MS][SIZE=3][COLOR=Navy]Thank You Yotam!!!!

Yeah Yes!

You can try any lisp package.

It can be cscope, xcscope, and xcscope+ also can be used[/COLOR][/SIZE][/FONT]......:popcorn:

---

