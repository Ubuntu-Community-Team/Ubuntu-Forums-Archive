---
title: "Enter a response demanded by a command that you are running (using a script)"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by bustard on 2012-10-25
I want to run a small python script that runs a command. This would be while I am not at the computer.

When the command runs, it prompts me to enter 'y' or 'n'. Is there some way I can build in to the script a way to have the script enter 'y' in response to the prompt, so that the command can continue to run?

---

### Post by maniandram on 2012-10-25
```

echo y|<command to run script>

```
-
You are receiving technical advice from an 11-year old.

---

### Post by Lars Noodén on 2012-10-25
Which program is to be run?  Some have an option to assume that the answer is yes if a prompt is needed.  e.g. "apt-get -y"

---

### Post by bustard on 2012-10-25
> **maniandram said:**
> ```

echo y|<command to run script>

```
-
You are receiving technical advice from an 11-year old.Thanks, that worked.

---

