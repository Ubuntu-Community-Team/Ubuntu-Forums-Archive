---
title: "[SOLVED] [java]Conditional Splitting"
date: 2008-10-02
forum: Programming Talk
---

### Post by Pyro.699 on 2008-10-02
Hello,

I was wondering the best method to go about splitting a string aslong as the character preceding is not one that is specified. To put it in simplier terms, i would like a string containig **.** to be split into groups, as long as its not preceeded by a **\** so this string:
**Hello\. World. My\. Name. Is\. Cody** would be broken into these groups: [**Hello\. World**], [**My\. Name**], [**Is\. Cody**]. I hope that makes sense, its sort of like an escape character.

Thanks
~Cody Woolaver

---

### Post by mlind on 2008-10-02
Hiya,

One way to do this is to use regular expressions (and so called 'negative lookbehind').

```

String foo = "Hello\\. World. My\\. Name. Is\\. Cody";	
for (String s : foo.split("(?<!\\\\)\\.")) {
	System.out.println(s);
}

```

Expression will match for ".", except when it's preceded by a "\". Not sure if this covers all the cases, but should give an idea how to do this.

---

### Post by Pyro.699 on 2008-10-02
do i have to use** \\.** what would i have to change to make it **\.**

thanks
~cody woolaver

---

### Post by CptPicard on 2008-10-02
> **Pyro.699 said:**
> do i have to use** \\.** what would i have to change to make it **\.**


In your string literal "\\." *is* "\.". You have to escape the escape character itself so that it's interpreted as a literal \, not escaping the . :)

---

### Post by Pyro.699 on 2008-10-03
Right -.- i realized that later in the night while i was laying in bed thinking about it xD Thanks alot for both your help :)

---

