---
title: "BASH: if [ variable 'contains'..."
date: 2007-09-28
forum: Programming Talk
---

### Post by ryanVickers on 2007-09-28
ok, if the title wasn't descriptive enough, I'll elaborate...

I am in need of a kind of if statement that will allow me to check for if the variable **contains** a certain string rather than if it's **equal** to it.

so, what would I put in place of the "==" in the following code:

```

if [ $variable == "string" ]
then...

```
:confused:

---

### Post by mssever on 2007-09-28
Untested code:
```
if [[ $var =~ regexp ]]; then
  #do something
fi
```

---

### Post by ryanVickers on 2007-09-28
ok, I tell you how it works :)

---

### Post by ryanVickers on 2007-09-28
Thanks a lot!  You've saves a **lot** of time and diskspace (well, no too much diskspace :))

---

### Post by Kakalle on 2011-10-07
Hi,

what would be the opposite of tis statement?
I mean: IF var/string contains not

This is not working:
if [[ $var !~ regexp ]]; then
Thank you very much for your help !!!

---

### Post by nothingspecial on 2011-10-07
Hi, this thread is very old.

Please create a new one with as much detail of your problem as possible.

Closed.

---

