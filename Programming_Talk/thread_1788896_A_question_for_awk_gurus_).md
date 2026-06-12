---
title: "A question for awk gurus :)"
date: 2011-06-23
forum: Programming Talk
---

### Post by prodigy_ on 2011-06-23
Let's suppose I have a file like this:
```

...
foo
...
bar
...

```
where "..." is any number of lines with some text. The following simple command outputs everything between "foo" and "bar":
```
awk '/^foo/{i++;next}/^bar/{exit}i' file
```
I even understand how it works. But what if I wanted to skip a couple of lines after "foo" as well? (Of course I can pipeline to **tail -n +3** but that's not interesting. ;)

---

### Post by dethorpe on 2011-06-23
I think you can use getline to read and throw away some lines after the foo. e.g.:
 
```
 
awk '/^foo/{i++;getline;getline;next}/^bar/{exit}i' file

```

---

### Post by prodigy_ on 2011-06-23
Yeah, it works. Thanks! :)

---

