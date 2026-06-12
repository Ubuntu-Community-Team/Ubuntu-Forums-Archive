---
title: "#! symbol"
date: 2010-04-26
forum: Programming Talk
---

### Post by blakep2 on 2010-04-26
#! or shift 3 then shift 1 if this dosent show up. i notice this in the address bar from time to time and i do not know what this means.  I tried to google it and it showed it as blank. What is up.

---

### Post by Dayofswords on 2010-04-26
its used to go to anchor tags in a web page like this
```
<html>
    <a href="#helloworld">anchor link</a>
blah blah blah
blah blah blah
    <a name="helloworld">where it directs you</a>
blah blah blah
</html>
```
clicking "anchor link" will direct the page to where the  'helloworld' anchor is declared at the "where it directs you". if it says 'example.html#anchor' it would got to a different page and move the oage to the position where 'anchor' is declared

more info:
[http://www.htmlcodetutorial.com/linking/_A_NAME.html](http://www.htmlcodetutorial.com/linking/_A_NAME.html)

**EDIT:** i think i read that wrong lol , i havent really seen #!, could just direct you to the '!' named one. can you give an example?

EDIT2: its the logo for [Crunchbang linux]("http://crunchbanglinux.org/")

---

### Post by oldfred on 2010-04-26
#! is the shebang (or sharp & bang).

Most scripts start with this and the type of shell to use.

python
#!/usr/bin/env python

Bash:
#!/usr/bin/env bash

---

### Post by Lux Perpetua on 2010-04-27
If the first line of an executable text file begins with **#!**, then the remainder of that line names the program that will interpret the file. In other words, if the first line of the file, say program.rb, is ```
#!/usr/bin/env ruby
``` then when you run the program by typing ```
> program.rb
``` in the shell, what will actually be executed is ```
/usr/bin/env ruby program.rb
```

---

### Post by nvteighen on 2010-04-27
> **blakep2 said:**
> #! or shift 3 then shift 1 if this dosent show up. i notice this in the address bar from time to time and i do not know what this means.  I tried to google it and it showed it as blank. What is up.

Which address bar??

#! (shebang) isn't used in webpages as far as I know, as it is a UNIX/Unix-like specific thing for simulating a binary file's magic number on a ASCII text file, so it gets recognized as an "executable" of some sort (interpreted by the interpreter stated on that very same line).

Could you please elaborate a bit more?

---

### Post by blakep2 on 2010-04-28
web browser address bar on facebook and stuff going between user profiles and photo albums it will normally do something like this when i click view my profile.  facbook.com/home.php#!/my_username   it is like it is just skipping the home.php part and going to the facebook.com/my_username.

---

