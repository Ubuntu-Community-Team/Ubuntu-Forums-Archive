---
title: "[SOLVED] Data CD &amp;amp; DVD compatibility between Windows and Linux"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-12-01
When I create a "mastered" data CD or DVD in Windows, then my Ubuntu Hardy can read it perfectly fine.

However, when I create a data CD or DVD in Linux, the file names appear in Windows as arbitrary short names all in capitals. Although the contents are readable,  the file names are wrong. This makes it very hard to find the correct content when using Windows.

What is the best way to create a data CD or DVD in Ubuntu so that Windows can read the file names?

---

### Post by jgoguen on 2008-12-01
If you're burning with Brassero, once you click the Burn button click the check box to increase compatibility with Windows systems.

---

### Post by Paddy Landau on 2008-12-01
> **jgoguen said:**
> If you're burning with Brassero, once you click the Burn button click the check box to increase compatibility with Windows systems.
When I do that, Brasero complains:
> Some files don't have a suitable name for a Windows-compatible CD: their names will be changed and truncated to 64 characters.But Windows doesn't seem to have had a problem with the names when I wrote the DVD from Windows. As I understand, it's only old versions of Windows that had a 64-character restriction. I don't want to reduce the name lengths, as the names contain important information about the content.

---

### Post by jgoguen on 2008-12-01
You could try installing k3b and using that to burn.
```
sudo aptitude install k3b
```
It's a KDE application, but it's got a lot more options around this sort of thing.  I haven't used it in a while, but it wasn't hard at all to find these options last time I looked.

---

### Post by Paddy Landau on 2008-12-01
> **jgoguen said:**
> You could try installing k3b and using that to burn.
Thank you, that worked perfectly!

---

