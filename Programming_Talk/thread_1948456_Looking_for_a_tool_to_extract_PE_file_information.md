---
title: "Looking for a tool to extract PE file information"
date: 2012-03-28
forum: Programming Talk
---

### Post by twegele on 2012-03-28
Hi all,

I'm new to this forum and using ubuntu since some time. I was looking for a tool (or trying to develop it myself) to extract some information from Microsoft PE files (such as *.dll, *.exe). Do you know if something is already integrated in ubuntu which can be used for this? The information which are interesting are something like file information, sections, entry point and so on.

Best regards,
Thomas

---

### Post by CynicRus on 2012-03-28
objdump -x -D pe-exe-file.exe | less

---

