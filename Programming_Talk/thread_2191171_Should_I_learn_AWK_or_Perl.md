---
title: "Should I learn AWK or Perl?"
date: 2013-12-01
forum: Programming Talk
---

### Post by sha1sum on 2013-12-01
Hello guys,

I'm trying to become a more tech-savvy Ubuntu user. I've recently finished [this book]("http://linuxcommand.org/tlcl.php") about the BASH shell, and I've read the chapters about sed in the book "sed & awk, 2nd edition" by O'Reilly Press. I've found that sed is an extremely useful tool for my purposes (mainly writing scientific articles, and writing scripts to make that easier), so I would like to increase my knowledge of stream editors. I've seen some useful awk commands being used, but I've also heard that it got replaced by Perl for a big part. I also have a book on learning Perl, so I can start studying either one. Which one would you guys recommend to me?


tl;dr: Should I learn AWK or Perl?

---

### Post by Lars Noodén on 2013-12-01
Learn both, but for AWK you don't need to get into programming it much.  It's good to know the basics and it's excellent for one-liners or otherwise very short one-offs.  You can learn the basics very quickly then move on.    

For detailed text processing, I would definitely say perl.  The pattern matching is more powerful, among other things.

---

### Post by drmrgd on 2013-12-01
I would say it all depends on what you'd like to be able to do.  That being said, though, I completely agree with Lars and say learn both.  If I recall correctly, Perl was born out of Larry Walls' need to do things for which he found AWK to be a little less robust and easy to use.  In my own experience, for really quick and simple command line text processing, AWK definitely gets the job done, and quick simply.  But, when the data gets a little more complex and I find myself piping awk, through sed, through whatever, Perl comes along and makes the job really simple.  So, having a good knowledge of both is pretty useful.  

Just as Lars says, for simple jobs, AWK seems to make the most sense.  For larger, more complex jobs, Perl - to me - makes the most sense.

---

### Post by r-senior on 2013-12-01
I think anyone who uses the command line a lot should know enough awk to know when it's useful. I don't use awk enough to be fluent but I can do the simple one liners and recognise situations where I need to go digging in the awk manual.

---

### Post by sha1sum on 2013-12-01
Okay I see. What would be the smartest thing to do... should I start with awk and when I'm familiar with that, move on to Perl? Or would it be better to start with Perl, and do awk after? I'm leaning toward learning awk first. I've also read that a lot of awk syntax is based on C. I don't know any C, could that be an obstacle? Or would it only be an advantage for if I ever decide to start learning C?

---

### Post by Lars Noodén on 2013-12-01
I'd do awk first.  You can cover the basics in a few hours spread over a few days.  The syntax is a little unclear at first, but it's really just stripped down if-then statements.    The things before the {..} are the ifs and the things inside the {..} are the thens.  There are special variables like $0 (the default) and $1, $2, $3 and so on.  There are others like NF, NR, FS and OFS.  Regular variables are just named, no $ or % in front.  The ~ operator can match a variable to a pattern.  Any 'if' expression can be negated with !  That's mostly it as far as what to look for.  If you go much beyond that, then you start to get out of awk's strengths and into perl's.

---

### Post by r-senior on 2013-12-01
The examples starting here and continuing on the subsequent pages give a good idea of what can be done.

[http://www.catonmat.net/blog/awk-one-liners-explained-part-one/](http://www.catonmat.net/blog/awk-one-liners-explained-part-one/)

---

### Post by sha1sum on 2013-12-01
Awesome, thanks guys. Out of curiosity I alread read a little, but now I've decided that I'm going to start learning awk. Wanna see my first script?

```
# first.awk -- my first awk script :-)

/^$/{ print "This line is empty" }
!/^$/{ print }

```

I love it when software does what you want it to do.

---

### Post by drmrgd on 2013-12-02
To help on your way, here's a couple AWK tutorials and sites with information that I've used to help get somewhat of a footing in the world of AWK:

[http://www.grymoire.com/Unix/Awk.html#uh-1](http://www.grymoire.com/Unix/Awk.html#uh-1)[URL="http://www.selectorweb.com/awk.html"]
http://www.selectorweb.com/awk.html[/URL]
[http://www.vectorsite.net/tsawk_3.html](http://www.vectorsite.net/tsawk_3.html)

Good luck learning this super handy useful tool! :)

---

### Post by sha1sum on 2013-12-02
Thanks! Good stuff.

---

### Post by Lars Noodén on 2013-12-02
For some non-technical background information, here is an interview with Brian Kernighan who is one of the co-authors of awk.  

[http://www.youtube.com/watch?v=8CalKJ5-w-U](http://www.youtube.com/watch?v=8CalKJ5-w-U)

Fast forward to 10:20 where he starts talking about awk until about 12:10 or so.

"for programs that are really only a few lines long, it's hard to beat"

---

### Post by sha1sum on 2013-12-02
Interesting clip :-) 

So yesterday and this morning I've done some more studying, and I'm already profiting from awk. A week or two ago I was trying to configure the nl (number line) command in such a way that it appends the line number at the end of the line, instead of the beginning. I couldn't get that to work, so I had to use a construction of nl pipelined into sed. Now I discovered that you can easily do it with awk:

```

cat doc.txt | awk '{ print $0 "\t" NR }'
```
Easy as pie!

---

