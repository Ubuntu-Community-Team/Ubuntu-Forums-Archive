---
title: "GDB --batch &gt;file.log. I need display of output."
date: 2009-03-11
forum: Programming Talk
---

### Post by panaut0lordv on 2009-03-11
This is my mini autorestarter for server's core.

```
#!/bin/bash
echo "run -c test.conf" > test.gdb
echo "bt" >> test.gdb
echo "bt full" >> test.gdb
echo "info thread" >> test.gdb
echo "thread apply all backtrace full" >> test.gdb
until gdb ./core -x test.gdb --batch >test.log 2>test.err
do date && echo "test server died with exit code $?. Restarting..."
grep -B 10 -A 1800 "SIGSEGV" "test.log" > "testtrace.log"
cat "testtrace.log" | ./paster | grep "http" >> "test.link"
cat "test.err" > "testerror.log"
sleep 31;
done;
```

Issue is, that I need display in console but of course ">test.log 2>test.err" are redirecting it to file.
Is there a way I can multicast output to both terminal & file?

Thanks in advance.

---

### Post by geirha on 2009-03-11
With the tee command.

```
some-command 2>&1 | tee test.log
```

---

