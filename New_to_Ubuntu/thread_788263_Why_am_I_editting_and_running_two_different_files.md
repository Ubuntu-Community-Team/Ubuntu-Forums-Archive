---
title: "Why am I editting and running two different files?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by AncientPC on 2008-05-09
I have a test script in ~/bin/test.

I have an old test script that contains the lines:
#!/bin/bash
echo "test 0"
exit 0

When I type in "which test" it gives me:
/home/user/bin/test

I then type in "vim `which test`" and modify and save a single line:
#!/bin/bash
echo "test 1"
exit 0

The command: cat `which test` returns the output:
echo "test 1"

When I run test, this is the output:
test 0

The command: ~/./bin/test returns the output:
test 1

Why?!?

---

### Post by gsmanners on 2008-05-09
I think you may be running into the fact that Bash uses a hash rather than a path search for commands. Try:

hash

and see what turns up.

---

### Post by AncientPC on 2008-05-09
I ran the test file to make sure it was loaded into the hash table, and then ran hash but nothing shows up.

---

### Post by AncientPC on 2008-05-09
I feel retarded and have just found the problem, I've aliased test to something else. :(

---

### Post by gsmanners on 2008-05-10
Thanks for the explanation. I don't think that would have ever crossed my mind.

---

