---
title: "Difference between - and -- in commandline"
date: 2017-08-27
forum: New to Ubuntu
---

### Post by cocteau2x on 2017-08-27
I am VERY NEW at this.

Sometimes I see the command line entry ....   -l   ... for example .. with just one " - "

other times I see  ..       --command      with 2   " -- "

is " -- " a key on the keyboard?
or is it actually 2 " - "   ????

It just seems to not work if I just type 2 " - " in a row ...

Thank You for your patience ...

---

### Post by mc4man on 2017-08-27
is it actually 2 " - "

---

### Post by vasa1 on 2017-08-27
And the "-" or the "--" are often used to indicate that the string immediately following is an option or switch. There doesn't seem to be a rule: some developers write their applications to require "--", others use "-".

---

### Post by &amp;KyT$0P# on 2017-08-27
> **cocteau2x said:**
> It just seems to not work if I just type 2 " - " in a row ...
What command are you trying to run?

---

### Post by vasa1 on 2017-08-28
And if you want become an expert: [https://stackoverflow.com/questions/8045479/whats-the-magic-of-a-dash-in-command-line-parameters](https://stackoverflow.com/questions/8045479/whats-the-magic-of-a-dash-in-command-line-parameters) ;)

---

### Post by SeijiSensei on 2017-08-28
During the early years of Unix, developers used the "-[letter]" convention to denote options.  As time went on, it became clear that some programs have too many options to rely on single letters.  So the "--[word]" convention was adopted as well.

Some single-letter options have longer, equivalent versions as well.  "-v" and "--verbose" are common synonyms in some programs.

---

### Post by Yellow Pasque on 2017-08-28
It's not a stupid question, but a horrible thread title...

---

### Post by vasa1 on 2017-08-28
> **Temüjin said:**
> It's not a stupid question, but a horrible thread title...
+1

I tried to improve it. Any other suggestions are welcome!

---

### Post by &amp;KyT$0P# on 2017-08-28
> **vasa1 said:**
> I tried to improve it. Any other suggestions are welcome!
I suggest '*"--" in commandline just seems to not work*', as this appears to be the reason for this thread -
> **cocteau2x said:**
> It just seems to not work if I just type 2 " - " in a row ...

---

### Post by vasa1 on 2017-08-28
OP seems to be including spaces before and after - and so isn't dealing with what's actually being used. I'm inclined not to worry any further until OP reappears :)

---

### Post by 1clue on 2017-08-28
Dashes mean whatever the author of the script or command want them to mean. When the script or command runs, the arguments passed in are sent as a list of space-delimited strings.

That said, there are customary meanings concerning dashes.

- followed by a single character (no intervening space) or several characters means each of those characters is considered to be a command option. '-v' often means 'verbose' and '-f' often means 'file'. So '-vf' would combine 'verbose' with 'file'. In the case of the -f option, typically you pass a filename as the next parameter, so you would actually have '<command> -vf foo.txt'

-- followed by a word with no intervening space usually means the whole --<word> is a single option. Sometimes that word is just an easier-to-remember version of a single-character option, or sometimes there is no single-character equivalent.

-- appearing alone as an argument usually means that the rest of the command line is to be passed to the command as a single unit. The implied reason is that the command you run will run some other command, and that command needs arguments which will follow the --.

---

