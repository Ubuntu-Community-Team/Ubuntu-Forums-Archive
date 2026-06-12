---
title: "best language to perform string operations"
date: 2013-04-27
forum: Programming Talk
---

### Post by IAMTubby on 2013-04-27
Hello,
I frequently run into problems where I have to get some input from a text file, do some string operations on it, and then write it back to the file.
As of now, I am doing this in C, but I feel this is consuming too much of my time since I have to implement everything from scratch.

While it makes for very good learning, it's sometimes difficult when I'm in a hurry.

Which language would you advise me for this purpose.
Thanks.

---

### Post by Vaphell on 2013-04-27
What kind of string operations?
perl is the king of everything string related, python is ok too. Easy tasks can be done with awk, sed.

---

### Post by IAMTubby on 2013-04-27
> **Vaphell said:**
> 
perl is the king of everything string related, python is ok too. Easy tasks can be done with awk, sed.
Ok shall keep that in mind.[/quote]

> What kind of string operations?
Mainly like, extracting a part of a string from a huge string.

---

### Post by trent.josephsen on 2013-04-27
Perl. It takes a bit of time to learn but it makes some things so easy.

*Learning Perl* is the best introductory programming text ever IMO, so if you get a book, make it that one.

---

### Post by Bachstelze on 2013-04-27
Perl is indeed the best language for text-related operations, but very often a one-liner shell script with the standard tools is enough.

---

### Post by shawnhcorey on 2013-04-27
Perl. Perl has the most advance regular expression engine. So advance that Python uses it too.

---

### Post by Mikeb85 on 2013-04-27
Ruby or Perl.  Ruby has all of Perl's regex features, many built-in methods you can perform on strings, and is quite user friendly too.  It also has pattern matching, blocks, and other useful functions.  I've heard Perl is very powerful for this kind of thing too, but I don't know it very well (just the Perl-inspired bits in Ruby).

---

### Post by shawnhcorey on 2013-04-27
> **Mikeb85 said:**
> Ruby or Perl.  Ruby has all of Perl's regex features, many built-in methods you can perform on strings, and is quite user friendly too.  It also has pattern matching, blocks, and other useful functions.  I've heard Perl is very powerful for this kind of thing too, but I don't know it very well (just the Perl-inspired bits in Ruby).

FYI: Ruby also uses Perl's regular expression engine.

---

### Post by machikakara on 2013-04-27
I would like to know how important speed is when it comes to these string operations, or is it about how easy it is to edit this code.

---

### Post by IAMTubby on 2013-04-28
Thanks a lot for the replies. The unanimous answer sounds like Perl, I shall get a book and start learning. It will be very helpful for me.

---

### Post by shawnhcorey on 2013-04-28
> **IAMTubby said:**
> Thanks a lot for the replies. The unanimous answer sounds like Perl, I shall get a book and start learning. It will be very helpful for me.

You would probably want to sign on to Perl [beginner mailing list]("http://learn.perl.org/faq/beginners.html").

---

### Post by Vaphell on 2013-04-28
i'd advise looking into sed and awk too. For many tasks pulling perl is imho an overkill, sed is perfect for simple jobs with a oneliner and awk is like a perl lite.

---

### Post by trent.josephsen on 2013-04-28
True, but from a utilitarian standpoint, you can pretty much skip sed and awk in favor of perl when it's available (and it is usually available on platforms with sed and awk). The reverse, i.e. replacing perl with the GNU tools, is much less easily done (after all, that's essentially why Perl exists in the first place). Unless you anticipate a platform where perl isn't available, it's not unreasonable to start with perl, rather than starting with bash+sed+awk to later discover you need more power.

This is why I never bothered to learn much bash; whenever I need more than simple invocation, I lapse into Perl. To be fair, I suppose a limited command of bash could be a liability, but I haven't seen that happen yet. On the other hand, I'm a hobbyist when it comes to Linux scripting, and my experience should not be considered authoritative.

---

### Post by shawnhcorey on 2013-04-28
I have written more than I care to remember in bash, sed, and awk, and I still prefer to use Perl. If it isn't on the machine, I install it. :)

---

### Post by IAMTubby on 2013-04-28
> **shawnhcorey said:**
> You would probably want to sign on to Perl [beginner mailing list]("http://learn.perl.org/faq/beginners.html").
Thanks a lot for that shawnhcorey :)
just subscribed by sending a mail to [email]beginners-subscribe@perl.org[/email]

---

### Post by ofnuts on 2013-04-29
I may be a bit late into the fray but if all you need to do is extract data with regular expressions, sed or awk might be even faster than perl.

---

