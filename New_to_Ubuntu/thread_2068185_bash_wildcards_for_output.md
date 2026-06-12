---
title: "bash wildcards for output"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by nickpick on 2012-10-08
Hi guys,

I apologise in advance if this is the entirely wrong section, but I've got a question about using bash wildscards. Here's the situation:

[LIST]
[*]I have X files with identical names, except for the number at the end, e.g. Test001.txt, Test002.txt, Test003.txt, etc.
[*]I want to send every file to a Perl script with the following syntax: "script_lalala Test001.txt > Test001.ready"
[/LIST]

How I know that I can use the asterisk (*) to read every file with something like cat, i.e. "cat Test*.txt". How would I go about doing the same thing with the script above?

Thanks in advance!

---

### Post by Lars Noodén on 2012-10-08
Would this do the trick?

```

 for i in test{001..005};do script_lalala $i.txt > $i.ready;done

```

---

### Post by nickpick on 2012-10-08
> **Lars Noodén said:**
> Would this do the trick?

```

 for i in test{001..005};do script_lalala $i.txt > $i.ready;done

```

Works for me. Many thanks.

---

