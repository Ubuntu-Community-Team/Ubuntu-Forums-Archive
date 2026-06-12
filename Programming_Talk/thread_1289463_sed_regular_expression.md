---
title: "sed regular expression"
date: 2009-10-12
forum: Programming Talk
---

### Post by RussellEngland on 2009-10-12
I want to import a html table into OpenOffice calc, but there doesn't seem to be an option?

So, I'm attempting to convert all the <td> to a tab in Kate using search for "\n<td>" replace with "\t" which works one at a time but takes forever with a replace all.

So thought I would try sed -e 's/\n<td>/\t/g' -i file.html

Which doesn't change anything. Any idea what the correct expression should be?

Many thanks

Russ

---

### Post by tino27 on 2009-10-12
sed can't match newlines. See [http://www.linuxtopia.org/online_books/linux_tool_guides/the_sed_faq/sedfaq5_009.html]("http://www.linuxtopia.org/online_books/linux_tool_guides/the_sed_faq/sedfaq5_009.html"). Maybe a match on just <td>?

---

### Post by ibuclaw on 2009-10-12
> **RussellEngland said:**
> I want to import a html table into OpenOffice calc, but there doesn't seem to be an option?

So, I'm attempting to convert all the <td> to a tab in Kate using search for "\n<td>" replace with "\t" which works one at a time but takes forever with a replace all.

So thought I would try sed -e 's/\n<td>/\t/g' -i file.html

Which doesn't change anything. Any idea what the correct expression should be?

Many thanks

Russ

Sed operates on a "line-by-line" basis. ^ being the start of a line, $ being the end. Hence it doesn't match \n.

To work around this, you can use N which carries the line across.
```
sed -e '**N;**s/\n<td>/\t/g' file.html
```

Regards
Iain

---

