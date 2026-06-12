---
title: "Geany question"
date: 2012-05-26
forum: Programming Talk
---

### Post by bobman321123 on 2012-05-26
Geany is distributed under the GNU public license, so does that mean anything I write using it is also under said license?

---

### Post by Zugzwang on 2012-05-26
Short answer: no.

For a longer answer: Your question is covered in the GNU GPL FAQ: [http://www.gnu.org/licenses/gpl-faq.html](http://www.gnu.org/licenses/gpl-faq.html) - There is a section "Using programs released under the GNU licenses when writing other programs" in the index that covers your question in detail.

---

### Post by bobman321123 on 2012-05-29
Ah perfect, that's exactly what I was looking for :)
You're the best.

---

### Post by bobman321123 on 2012-05-31
So just to confirm, anything written under a program with GPL license is my property unless it explicitly requires GPL components to run?

---

### Post by PeterP24 on 2012-05-31
My guess was that if you write something with Geany, you don't have to release it under a GPL license. To be on the safe side, I've read the link Zugzwang gave you. Here is a quote:
> **Can I use GPL-covered editors such as GNU Emacs to develop non-free programs? Can I use GPL-covered tools such as GCC to compile them? **(#CanIUseGPLToolsForNF)

    _Yes, because the copyright on the editors and tools does not cover the code you write_. Using them does not place any restrictions, legally, on the license you use for your code.

    Some programs copy parts of themselves into the output for technical reasons—for example, Bison copies a standard parser program into its output file. In such cases, the copied text in the output is covered by the same license that covers it in the source code. Meanwhile, the part of the output which is derived from the program's input inherits the copyright status of the input.

    As it happens, Bison can also be used to develop non-free programs. This is because we decided to explicitly permit the use of the Bison standard parser program in Bison output files without restriction. We made the decision because there were other tools comparable to Bison which already permitted use for non-free programs.

So, I guess you replace emacs with geany in your query and you got your answer straight from the horse mouth.

---

### Post by bobman321123 on 2012-05-31
Ah, ok.
So the short answer is that I own the code I write. 

Thanks :)

---

