---
title: "Good Cobol Editors?"
date: 2011-07-18
forum: Programming Talk
---

### Post by xmanmonk on 2011-07-18
Probably not a common request, but I am looking for a good cobol editor. I have gVim, which highlights context in the code, but I would also like at least line numbering insertion (or renumbering), and it would be nice to also have syntax lookup, but that's not a necessity.

I also have gxe, which is very mainframe-like, but there doesn't seem to be any kind of highlighting, and the line number insertion uses the wrong number of fields and only seems to number by 1.

Oh, and the budget is about $1, so free would be good (cuz then I get to keep the buck). Any info will be greatly appreciated. Thanks!

---

### Post by Mordred on 2011-07-18
Hi,

in gvim you can turn on line numbering using command

[PHP]:set nu[/PHP]

You can also put this in your .vimrc so you do not have to type it every time.

---

### Post by xmanmonk on 2011-07-18
Thanks for the reply. That turns on the *display* of line numbers, but I'm looking for something that actually *inserts* line numbers into the text. In cobol, the first six spaces on each line are reserved for line numbers. Most modern compilers don't require them, but some older ones seem to expect them. Thus, I thought it would be nice to automatically add them when I'm finished. At present, I'm using a spreadsheet to do this (inelegant, but pragmatic). I'd prefer to have an editor or something like an IDE to it for me (lazy bum that I am!). Thanks for that, though.

---

### Post by cgroza on 2011-07-18
> **xmanmonk said:**
> Thanks for the reply. That turns on the *display* of line numbers, but I'm looking for something that actually *inserts* line numbers into the text. In cobol, the first six spaces on each line are reserved for line numbers. Most modern compilers don't require them, but some older ones seem to expect them. Thus, I thought it would be nice to automatically add them when I'm finished. At present, I'm using a spreadsheet to do this (inelegant, but pragmatic). I'd prefer to have an editor or something like an IDE to it for me (lazy bum that I am!). Thanks for that, though.
Why don't you write a macro for that? I don't know about vim, but in emacs you can write a elisp function that will number the whole buffer at the expense of a keystroke.

---

### Post by xmanmonk on 2011-07-18
Yeah, (*sigh*) I know. But you see, I am so incredibly lazy that I was hoping there was a tool out there that had done all this for me already :)

And I really prefer to use EMACS, so I may just do that. Thanks.

---

### Post by xmanmonk on 2011-07-21
OK, in case hell freezes over and someone else actually wants to do what I'm doing (edit mainframe cobol code on a linux PC), here's how to do what I needed.

One of the editors I have is gxe, which is an emulation of a mainframe editor. I wanted to be able to either number the lines, or renumber the lines if they were already there. gxe can do both. Vim (or gvim) can do cobol highlighting.

To get gxe to renumber, use the ren command. However, by default it uses the first 7 columns for the line numbers, which is not really standard for cobol (most cobols use 6). Additionally, it renumbers by 1, which is not typical (10 is more typical). So, to get it to count by ten, you renumber 1 fewer columns than you need, and specify a separation character of '0'. Thus, for six columns numbered by tens, the command would be:

   ren setr 1-5'0'

If you don't have line numbers and want to add them, replace the setr with seti. And... convoluted though it may be, that is my solution (for now).

Thanks to all who helped!

---

