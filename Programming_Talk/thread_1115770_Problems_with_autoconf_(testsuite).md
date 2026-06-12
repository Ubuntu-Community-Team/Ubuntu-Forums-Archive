---
title: "Problems with autoconf (testsuite)"
date: 2009-04-04
forum: Programming Talk
---

### Post by stcain on 2009-04-04
Hey guys, 1st time here ):P

Basically i'm running my own autotest suite and i'm writing my own tests using m4. Below is a sample of my testsuite.at

> 
AT_SETUP([Empty File Tests])
AT_KEYWORDS([empty])
AT_DATA([emptyInput],[[No file found]])
AT_CHECK([prog],[1],,emptyInput,[echo Failed],[echo Passed])
AT_CLEANUP


I checked against the autoconf documentation, seems correct. And it compiles with *make testsuite* too.
But when I run *./testsuite*..
> 
./testsuite: line 1289: syntax error near unexpected token `fi'
./testsuite: line 1289: `      fi'

Basically it blows up in my face. If i comment out the AT_DATA and AT_CHECK lines it goes through nicely since there isn't anything to check for. 

Does anyone see anything wrong with the testsuite.at? I did autoreconf and configure afew times to make sure that the makefiles and all were updated but it still gives me the same problem =\

Any help will be appreciated =)

Edit: Fixed a typo in the code

---

### Post by Arndt on 2009-04-04
> **stcain said:**
> Hey guys, 1st time here ):P

Basically i'm running my own autotest suite and i'm writing my own tests using m4. Below is a sample of my testsuite.at



I checked against the autoconf documentation, seems correct. And it compiles with *make testsuite* too.
But when I run *./testsuite*..

Basically it blows up in my face. If i comment out the AT_DATA and AT_CHECK lines it goes through nicely since there isn't anything to check for. 

Does anyone see anything wrong with the testsuite.at? I did autoreconf and configure afew times to make sure that the makefiles and all were updated but it still gives me the same problem =\

Any help will be appreciated =)

Do you really mean to have both emptyInput and emptyIntput?

---

### Post by stcain on 2009-04-04
Hey, what do you mean both emptyInput and emptyIntput?

..Ah..i see what you mean. Sorry it was a typo. I've corrected it..

Oh and that isn't the problem.. haha.

---

### Post by Arndt on 2009-04-04
> **stcain said:**
> Hey guys, 1st time here ):P

Basically i'm running my own autotest suite and i'm writing my own tests using m4. Below is a sample of my testsuite.at




This is what you have:

```
AT_SETUP([Empty File Tests])
AT_KEYWORDS([empty])
AT_DATA([emptyInput],[[No file found]])
AT_CHECK([prog],[1],,emptyInput,[echo Failed],[echo Passed])
AT_CLEANUP
```

I think this is what you want:

```
AT_SETUP([Empty File Tests])
AT_KEYWORDS([empty])
AT_DATA([emptyInput],[[No file found
]])
AT_CHECK([prog],[1],,emptyInput,[echo Failed],[echo Passed])
AT_CLEANUP
```

Your AT_DATA test turns into this in the shell code:

```
cat >emptyInput1 <<'_ATEOF'
No file found_ATEOF
```

and it then scans the rest of the script for the word _ATEOF and goes on from there, so the final newline in the error message is crucial.

---

### Post by stcain on 2009-04-04
ha! It worked! Thanks alot arndt, think i've got it now.

---

