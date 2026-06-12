---
title: "How to write into the Terminal?"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by harbimilan on 2012-02-06
Hi,
I'm trying to do a very simple thing but I couldn't find it in google.
I have a launcher that executes some commands in the terminal, and I want to add something like " write("operation complete.\n") " so that it writes "operation complete." in the terminal.

what is the command for that? 
Thanks for help.

---

### Post by sisco311 on 2012-02-06
You can use **echo** or **printf**:

```

echo "-----------------------------------------------------------"
printf '%s\n' "POSIX® recommends to use printf rather than echo"
printf '%s\n' "See: http://wiki.bash-hackers.org/commands/builtin/printf"
printf '%s\n' "and" "help echo" "help printf"
echo "-----------------------------------------------------------"
```

---

### Post by cortman on 2012-02-06
```
echo operation complete.
```

---

### Post by harbimilan on 2012-02-14
Thanks guys!

---

