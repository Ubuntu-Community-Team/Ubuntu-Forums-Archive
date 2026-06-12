---
title: "vim : copy paste columns between two different terminals"
date: 2008-06-17
forum: Programming Talk
---

### Post by Claus7 on 2008-06-17
Hello,

if someone wants to copy a column in vim editor, someone presses Ctrl+v and selets the columns someone wants. Then, by pressing p, pastes the columns where someone wants, yet in the **same** terminal.

What about another file that is in **another** terminal? The way above doesn't work. Is there any way?

Regards!

---

### Post by geirha on 2008-06-17
You can mark the same way as vim's Ctrl+v by holding down Ctrl while marking with the left mouse button, then paste with the middle mouse button.

---

### Post by Claus7 on 2008-06-18
Hello,

Thank you for your response. I can mark that way the columns I want. Yet, if I paste that way in the other file, the text is inserted instead of having the column format. So what I want is:

file 1:
text *column_we_want_pasted* 
text *column_we_want_pasted*
text *column_we_want_pasted*
text *column_we_want_pasted*

file 2:
text2 *column_we_want_pasted* 
text2 *column_we_want_pasted*
text2 *column_we_want_pasted*
text2 *column_we_want_pasted*

and NOT:
text2 *column_we_want_pasted* 
 *column_we_want_pasted*
 *column_we_want_pasted*
 *column_we_want_pasted*
text2
text2
text2

Regards!

---

### Post by geirha on 2008-06-18
Then you'll have to edit both files in the same vim instance. There's no way to retain the information needed to paste like that in the clipboard.

Typically, you would do:
```

vim file1 file2
mark with ctrl+v and hit y to yank.
:n or :next to switch to the next file
p to paste
:prev and :previous will switch to the previous file.
you can also use :first and :last

```

If you've already run «vim file1» you can add file2 with «:argadd file2»

---

### Post by Claus7 on 2008-06-18
Hello,

thank you for all the info!

> **geirha said:**
> There's no way to retain the information needed to paste like that in the clipboard.
Yet, this should be helpful, in case someone works remotely and wants to avoid downloading (both) files to someone's computer and then post process them.

Regards!

---

### Post by geirha on 2008-06-18
> **Claus7 said:**
> Hello,

thank you for all the info!


Yet, this should be helpful, in case someone works remotely and wants to avoid downloading (both) files to someone's computer and then post process them.

Regards!

Well, you can copy with Ctrl+left mouse button, then on the other host, paste on an empty line (or in a new file), then select it again in the other host's vim with ctrl+v, delete it and paste it at the right place. That would be a workaround at least.

---

### Post by chichilalescu on 2009-02-02
this page might be useful:

[http://vim.wikia.com/wiki/Copy_and_paste_between_sessions_using_a_temporary_file#Comments](http://vim.wikia.com/wiki/Copy_and_paste_between_sessions_using_a_temporary_file#Comments)

I replaced the script on that page with
```

"custom copy'n'paste
"copy the current visual selection to ~/.vbuf
vmap <S-y> :w! ~/.vbuf<CR>
"copy the current line to the buffer file if no visual selection
nmap <S-y> :.w! ~/.vbuf<CR>
"paste the contents of the buffer file
nmap <S-p> :r ~/.vbuf<CR>

```

(they were using Ctrl-c and Ctrl-v, and I thought conflicts should be avoided, so I used Shift-y and Shift-p)
I noticed however that in block mode it copies the entire lines. maybe replace vmap by bmap or something? I'm not really sure how this works.

---

### Post by estanzi on 2010-03-16
Hey if you are still interested in a vim way to copy and paste:

In normal mode press C-v to marc columnwise then press "+y, what yanks the marked stuff into the +-Buffer.

Then in the other instance in normal mode press "+gP, what pastes the stuff as you wish.

Happy vIMing

---

### Post by binopolackal on 2010-11-03
-open the 2 files in two viewports :/vsp or :/sp
-the go to Visual mode using the key v
-now select the text u want to copy
-Yank it using key y
-go the the other file where it need to be pasted
-paste using key p

cpoy paste also works in the traditional way between different viewports.

---

