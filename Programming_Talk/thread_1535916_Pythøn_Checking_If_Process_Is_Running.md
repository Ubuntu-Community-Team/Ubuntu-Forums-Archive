---
title: "Pythøn: Checking If Process Is Running"
date: 2010-07-21
forum: Programming Talk
---

### Post by Sailor5 on 2010-07-21
Ahoy Sailors!

I'm going to be compiling my Py to exe & I need to be able to check if there are multiple processes of the same thing are running, The following script does now work.
```
check = os.popen('tasklist').read()
if 'Self.exe' in check:
    print "We are running, Now exit."
    raise SystemExit
else:
    print "We're not running, Don't exit."
```But of course when we run this script, It will see itself and exit, How now can we say if we find two of 'Self.exe' then exit?

Thanks Bye!

** Figured it out,
```
sub = os.popen('tasklist').read()
if sub.count("Proc.exe") > 1:
  raise SystemExit
```

---

