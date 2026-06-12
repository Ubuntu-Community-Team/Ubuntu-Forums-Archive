---
title: "sed removing duplicate characters and certain characters in begining/end of string"
date: 2010-02-12
forum: Programming Talk
---

### Post by tolanri on 2010-02-12
Hello, I am asking for your help with sed. I need to remove duplicate underscores and underscores from beginning and end of string.

For example:

```
echo '[Lorem] ~ ipsum *dolor* sit metus !!!' | sed 's/[^ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789._()-]/_/g'
```Produces: _Lorem____ipsum__dolor__sit_metus____

And I need to further format this string to: Lorem_ipsum_dolor_sit_metus

In other words, remove any underscores from beginning and end of string, and reduce multiple consecutive underscore symbols into just one, preferably using another pipes.

Do you have any idea how to do that?

Thank you.

---

### Post by mobilediesel on 2010-02-12
> **tolanri said:**
> Hello, I am asking for your help with sed. I need to remove duplicate underscores and underscores from beginning and end of string.

For example:

```
echo '[Lorem] ~ ipsum *dolor* sit metus !!!' | sed 's/[^ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789._()-]/_/g'
```Produces: _Lorem____ipsum__dolor__sit_metus____

And I need to further format this string to: Lorem_ipsum_dolor_sit_metus

In other words, remove any underscores from beginning and end of string, and reduce multiple consecutive underscore symbols into just one, preferably using another pipes.

Do you have any idea how to do that?

Thank you.

Try this:
```
echo '[Lorem] ~ ipsum *dolor* sit metus !!!' | sed -e 's/[^A-Za-z0-9._()-]/_/g' -e 's/^_*//' -e 's/_*$//' -e 's/_\{2,\}/_/g'
```

**A-Z**, **a-z** and **0-9** handles the whole range instead of typing out all the characters. **'s/^_*//'** gets rid of the underscores at the beginning of a line. **'s/_*$//'** takes care of the underscores at the end of a line. **'s/_\{2,\}/_/g'** takes 2 or more consecutive underscores and replaces them with one underscore.

---

### Post by tolanri on 2010-02-12
Thanks, I had A-Za-z range, but oddly it would not work properly with one string:

```
echo 'Something â?? Something else' | sed -e 's/[^A-Za-z0-9._()-]/_/g' -e 's/^_*//' -e 's/_*$//' -e 's/_\{2,\}/_/g'
```would output **Something_â_Something_else** 

In windows, this string (filename) looks like this: **Something &#8211; Something else.mp4** but in Linux it's **Something â?? Something** else instead

If you know solution to this, I would rather use range as it seems also accepts letters from non-English alphabet.
But your solution worked great for removing those underscores! Thanks

---

### Post by mobilediesel on 2010-02-12
> **tolanri said:**
> Thanks, I had A-Za-z range, but oddly it would not work properly with one string:

```
echo 'Something â?? Something else' | sed -e 's/[^A-Za-z0-9._()-]/_/g' -e 's/^_*//' -e 's/_*$//' -e 's/_\{2,\}/_/g'
```would output **Something_â_Something_else** 

In windows, this string (filename) looks like this: **Something – Something else.mp4** but in Linux it's **Something â?? Something** else instead

If you know solution to this, I would rather use range as it seems also accepts letters from non-English alphabet.
But your solution worked great for removing those underscores! Thanks

Weird, it comes out **Something_Something_else** on my system. I don't know what would be different.

---

### Post by tolanri on 2010-02-12
> **mobilediesel said:**
> Weird, it comes out **Something_Something_else** on my system. I don't know what would be different.

I'm using Ubuntu Server 9.10, tried it also on Ubuntu Desktop 9.10, same:

```
tolanri@ubuntu:~$ echo 'Something â?? Something else' | sed -e 's/[^A-Za-z0-9._()-]/_/g' -e 's/^_*//' -e 's/_*$//' -e 's/_\{2,\}/_/g'
Something_â_Something_else
```

---

### Post by mobilediesel on 2010-02-12
> **tolanri said:**
> I'm using Ubuntu Server 9.10, tried it also on Ubuntu Desktop 9.10, same:

```
tolanri@ubuntu:~$ echo 'Something â?? Something else' | sed -e 's/[^A-Za-z0-9._()-]/_/g' -e 's/^_*//' -e 's/_*$//' -e 's/_\{2,\}/_/g'
Something_â_Something_else
```

I see why it worked on mine. the **â** didn't paste into my terminal. I normally use Terminator and I also tried in xfce4-terminal. Plain xterm doesn't seem to let me paste anything at all.

---

### Post by tolanri on 2010-02-12
Do you know why would em-dash in Linux transformed into *â??* ? I would rather use a-zA-Z ranges in sed, but because this "bug" I can't...

---

### Post by mobilediesel on 2010-02-12
> **tolanri said:**
> Do you know why would em-dash in Linux transformed into *â??* ? I would rather use a-zA-Z ranges in sed, but because this "bug" I can't...

That **â** has me stumped.

---

