---
title: "Tcl Regexp problem"
date: 2009-03-17
forum: Programming Talk
---

### Post by oaul on 2009-03-17
lets say I have a variable foo set as paul

% set foo paul

I want to see if the string "$paul" is in the line "$paul is smelly"

% set line {$paul is smelly}

% puts "\$$foo"
$paul

Here is where I am messing up:
regexp "\$$foo" $line
0

Any suggestions?

---

### Post by oaul on 2009-03-17
Nevermind.  I am stupid. 

SHOULD be:
regexp "\\$$foo" $line

which works just fine.  My bad

---

