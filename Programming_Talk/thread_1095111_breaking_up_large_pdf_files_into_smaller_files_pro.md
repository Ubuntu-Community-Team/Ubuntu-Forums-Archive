---
title: "breaking up large pdf files into smaller files programmatically"
date: 2009-03-13
forum: Programming Talk
---

### Post by badperson on 2009-03-13
anyone one know a good way to do this? I would like to do it in either java or perl. 

Did a quick search on cpan, messed around with the PDF package, but was wondering if any of you guys have worked on that task specifically.
bp

---

### Post by lapubell on 2009-03-13
i've always used pdftk and whatever scripting language i was able to use.  sorry if this isn't what you are looking for.

```

pdftk bigOne.pdf burst

```

this will fill the working dir with a new pdf file for each page all with file names like pg_0001.pdf, pg_0002.pdf, so on...

it's pretty predictiable, so you can probably script around it as you need to.

---

