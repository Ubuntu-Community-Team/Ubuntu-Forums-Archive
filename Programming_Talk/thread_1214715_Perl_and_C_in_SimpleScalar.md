---
title: "Perl and C in SimpleScalar"
date: 2009-07-16
forum: Programming Talk
---

### Post by green86 on 2009-07-16
Hello.. Can someone tell me if we can call perl scripts through C program in ubuntu 8.04? And also if a perl script can pass information to C pgm? 

Actually I'm trying to do this:
Modify SimProfile(C pgm) of SimpleScalar to extract certain pgm characteristics and provide it to a fuzzy inference system[FIS] (Perl) that'll guide the scheduling of a hypothetical quad-core processor in Wattch.

Are there other ways creating this FIS? I installed Freemat.. But I've no clue about how to go about it!  

I highly appreciate any help in this regard and also your ideas in going about this project of mine.. =D>  Thanks in advance..

---

### Post by soltanis on 2009-07-16
Not sure about the second part of your post, but here's a relevant section from the perldocs:

```

man 1 perlembed

       PREAMBLE

       Do you want to:

       Use C from Perl?
            Read perlxstut, perlxs, h2xs, perlguts, and perlapi.

       Use a Unix program from Perl?
            Read about back-quotes and about "system" and "exec" in perlfunc.

       Use Perl from Perl?
            Read about "do" in perlfunc and "eval" in perlfunc and "require"
            in perlfunc and "use" in perlfunc.

       Use C from C?
            Rethink your design.

       Use Perl from C?
            Read on...

```

EDIT.

And please see the manpages for the system(3) and exec(3) calls in the C programming language. They are probably the quickest solution to your problem. Also consider looking at popen(3).

---

