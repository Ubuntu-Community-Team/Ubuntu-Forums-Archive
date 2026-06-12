---
title: "Memory leaks with QT"
date: 2008-08-21
forum: Programming Talk
---

### Post by alxlabs on 2008-08-21
I tried to run my app (written with QT4.X) thru valgrind and got some memory leaks from QT. Is this normal? 

```

=5683== LEAK SUMMARY:
==5683==    definitely lost: 660 bytes in 6 blocks.
==5683==    indirectly lost: 1,740 bytes in 91 blocks.
==5683==      possibly lost: 760 bytes in 4 blocks.
==5683==    still reachable: 493,978 bytes in 4,127 blocks.
==5683==         suppressed: 0 bytes in 0 blocks.
==5683== Reachable blocks (those to which a pointer was found) are not shown.
==5683== To see them, rerun with: --leak-check=full --show-reachable=yes

```

```

==5683== 1,856 (256 direct, 1,600 indirect) bytes in 1 blocks are definitely lost in loss record 180 of 219
==5683==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==5683==    by 0x4D62FD3: (within /usr/lib/libfontconfig.so.1.3.0)
==5683==    by 0x4D6392C: (within /usr/lib/libfontconfig.so.1.3.0)
==5683==    by 0x4D63F3B: (within /usr/lib/libfontconfig.so.1.3.0)
==5683==    by 0x4D6415F: (within /usr/lib/libfontconfig.so.1.3.0)
==5683==    by 0x4D59286: FcDefaultSubstitute (in /usr/lib/libfontconfig.so.1.3.0)
==5683==    by 0x42F66D8: QFontDatabase::load(QFontPrivate const*, int) (in /usr/lib/libQtGui.so.4.3.4)
==5683==    by 0x430EFD4: (within /usr/lib/libQtGui.so.4.3.4)
==5683==    by 0x4319349: QTextLine::layout_helper(int) (in /usr/lib/libQtGui.so.4.3.4)
==5683==    by 0x431A96C: QTextLine::setNumColumns(int) (in /usr/lib/libQtGui.so.4.3.4)
==5683==    by 0x431AD8E: QTextLayout::endLayout() (in /usr/lib/libQtGui.so.4.3.4)
==5683==    by 0x44A6188: (within /usr/lib/libQtGui.so.4.3.4)

```

---

### Post by kknd on 2008-08-21
Valgrind results are usually wrong when you are testing a program that uses QT (and GTK too), because the way that QT manages the memory.

---

### Post by alxlabs on 2008-08-21
> **kknd said:**
> Valgrind results are usually wrong when you are testing a program that uses QT (and GTK too), because the way that QT manages the memory.

What's the good tool for this?

---

### Post by yabbadabbadont on 2008-08-21
> **alxlabs said:**
> What's the good tool for this?

The one located directly between your ears...  :D

---

### Post by kknd on 2008-08-21
There's no perfect tool, but you can configure valgrind (massif helps) to better suit you.

For example, to analise the heap use with GTK (basically it passed to massif the memory allocator functions):

valgrind --tool=massif --depth=5  --alloc-fn=g_malloc --alloc-fn=g_realloc --alloc-fn=g_try_malloc --alloc-fn=g_malloc0 --alloc-fn=g_mem_chunk_alloc application.


I don't know how it would be done with QT, and this example don't show memory leaks explicit.

---

