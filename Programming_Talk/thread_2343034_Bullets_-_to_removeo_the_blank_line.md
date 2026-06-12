---
title: "Bullets - to removeo the blank line"
date: 2016-11-12
forum: Programming Talk
---

### Post by satimis on 2016-11-12
Hi all,

Please advise how to remove the line between <ul> and <li>?

Please see attached photo.  I expect to remove the blank line between "Ingredients" and "Heating a frying pan"

Thanks

satimis

---

### Post by SeijiSensei on 2016-11-12
I take it you mean "Directions" rather than "Ingredients".

Try changing the default padding for <ul> with
```
<ul style='padding-bottom:0'>
```
Does that help?

---

### Post by satimis on 2016-11-12
> **SeijiSensei said:**
> I take it you mean "Directions" rather than "Ingredients".

Try changing the default padding for <ul> with
```
<ul style='padding-bottom:0'>
```
Does that help?
Hi,

Thanks for your advice.

No, it didn't work.  I tried it before.

satimis

---

### Post by SeijiSensei on 2016-11-12
Using a negative margin worked for me in Firefox:
```

<p>Heading</p>
<ul style='margin:-10px'>
<li>line 1
<li>line 2
</ul>

```
See [http://stackoverflow.com/questions/7759229/remove-space-between-paragraph-and-unordered-list](http://stackoverflow.com/questions/7759229/remove-space-between-paragraph-and-unordered-list)

I always have a hard time anticipating the effects of margin, spacing, and padding.

---

### Post by satimis on 2016-11-13
> **SeijiSensei said:**
> Using a negative margin worked for me in Firefox:
```

<p>Heading</p>
<ul style='margin:-10px'>
<li>line 1
<li>line 2
</ul>

```
See [http://stackoverflow.com/questions/7759229/remove-space-between-paragraph-and-unordered-list](http://stackoverflow.com/questions/7759229/remove-space-between-paragraph-and-unordered-list)

I always have a hard time anticipating the effects of margin, spacing, and padding.

Hi,

Thanks for your advice and link.

Sorry your code doesn't work for me.  I'm running Firefox 49.0.2

I have tried your link before posting.

Finally following coding works for me here.
```

<ul>
<p style="color: #3366ff; margin: -60px; margin-top: 20px; margin-bottom: 0"><strong>Directions:</strong></p>
<li><span style="color: #ff6600;">Heat a frying pan.</span></li>
........


```

Thanks

satimis

---

