---
title: "Exclude some matches with sed"
date: 2012-02-18
forum: Programming Talk
---

### Post by Intrepid Ibex on 2012-02-18
Hey,

The task is to edit [this](http://www.pastebin.com/Wqy9ebsi) file by changing all that **/sbin/** stuff to **/usr/bin/**, excluding **/sbin/modprobe** lines: 

I only know how to do this by changing them back afterwards:
```
# sed -i "s|/sbin/|/usr/bin/|g" asd
# sed -i "s|/usr/bin/modprobe|/sbin/modprobe|g" asd
```

---

### Post by StephenF on 2012-02-18
You want a negative lookahead assertion.

---

### Post by Intrepid Ibex on 2012-02-18
Yes, I know, but I don't know how to do that.

---

### Post by StephenF on 2012-02-18
Wanting to know < wanting to learn. Here is your know.

$ perl -pe 's|/sbin/(?!modprobe)|/usr/bin/|g' in.txt >out.txt

sed < perl

Here is the in-place version.

$ perl -pi'.bak' -e 's|/sbin/(?!modprobe)|/usr/bin/|g' file.txt

---

### Post by matt_symes on 2012-02-18
Hi

Use Perl as suggested.

sed and grep do not implement lookaheads or look behinds.

Kind regards

---

### Post by Intrepid Ibex on 2012-02-18
> **StephenF said:**
> Wanting to know < wanting to learn. Here is your know.

Yeah, well, I'd much rather have someone just tell me how to do the single thing I'm never gonna do again, instead of reading some docs and finding out myself. Thanks.

---

### Post by The Cog on 2012-02-20
You can do it in a single line with sed like this:
```
sed -i -e "s|/sbin/|/usr/bin/|g" -e "s|/usr/bin/modprobe|/sbin/modprobe|g" asd
```

---

