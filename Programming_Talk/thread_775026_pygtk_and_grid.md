---
title: "pygtk and grid"
date: 2008-04-29
forum: Programming Talk
---

### Post by wilkerlucio on 2008-04-29
Hi all!

I'm starting to program with python and pygtk for create windows.
I will create a program that needs to display data into a grid (like file explorer grid), the grid needs to contains labels and custom components inside (like progress bar).

Im searching for a widget to use for this case but i dont found anything... i know its possible seeing applications like bittorrent using into downloads list but i dont know how...

anyone can help me please...

thanks :)

---

### Post by Quikee on 2008-04-30
> **wilkerlucio said:**
> Hi all!

I'm starting to program with python and pygtk for create windows.
I will create a program that needs to display data into a grid (like file explorer grid), the grid needs to contains labels and custom components inside (like progress bar).

Im searching for a widget to use for this case but i dont found anything... i know its possible seeing applications like bittorrent using into downloads list but i dont know how...

anyone can help me please...

thanks :)

Use a TreeView with a ListStore.

---

