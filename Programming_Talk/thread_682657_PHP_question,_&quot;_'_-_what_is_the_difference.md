---
title: "PHP question, &quot; ' - what is the difference?"
date: 2008-01-30
forum: Programming Talk
---

### Post by ben22 on 2008-01-30
Hi,

I was wondering whether someone knows a good php forum to exchange with other developers.


Also one question. I read a tutorial and sometimes the author is using ' - sometimes ".

What is the difference?

Example:

if(isset($_GET['section']) AND (**"**admin**"** == $_GET['section'])) {
							session_start();										}    


if(isset($_GET['section']) AND (**'**admin**'** == $_GET['section'])) {
							session_start();										}

---

### Post by LaRoza on 2008-01-30
Strings in double quotes do variable substitution.

---

### Post by idn on 2008-01-30
just out of interest what does that mean? i didnt think there was a difference...

---

### Post by LaRoza on 2008-01-30
> **idn said:**
> just out of interest what does that mean? i didnt think there was a difference...

[php]
$bestforummember = "LaRoza";

echo "$bestforummember is the best\n";

echo '$bestforummember is the best';
[/php]

Output:
```

LaRoza is the best
$bestforummember is the best

```

---

### Post by ThinkBuntu on 2008-01-30
Also, the \n indicating a newline and similar characters only work with double quotes. I generally use double quotes unless there's a reason not to.

---

### Post by LaRoza on 2008-01-30
> **ThinkBuntu said:**
> Also, the \n indicating a newline and similar characters only work with double quotes. I generally use double quotes unless there's a reason not to.

404 still. Hows it going?

---

### Post by ThinkBuntu on 2008-01-30
So far, so good. Still due out by Feb. 14.

---

### Post by LaRoza on 2008-01-30
> **ThinkBuntu said:**
> So far, so good. Still due out by Feb. 14.

It better be. I keep getting requests for CSS issues and help.

---

