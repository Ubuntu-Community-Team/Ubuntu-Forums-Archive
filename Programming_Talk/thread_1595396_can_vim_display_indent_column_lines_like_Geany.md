---
title: "can vim display indent column lines like Geany?"
date: 2010-10-13
forum: Programming Talk
---

### Post by Ascenti0n on 2010-10-13
My standard text editor ATM is Geany, it's fast, compact and does most of what I need for web development.

I want to see if I can recreate a similar environment in Vim. Does anyone know how to display indent column lines as in Geany?

---

### Post by Ascenti0n on 2010-10-13
anyone?

---

### Post by spjackson on 2010-10-13
> **Ascenti0n said:**
> My standard text editor ATM is Geany, it's fast, compact and does most of what I need for web development.

I want to see if I can recreate a similar environment in Vim. Does anyone know how to display indent column lines as in Geany?
I don't follow why you want to emulate Geany in Vim. If you like Geany, why not use Geany?

I am not aware of a method in Vim that does what you are looking for. The closest thing that I can think of is
```

:set list

```which will by default show TAB as ^I and end of line as $. You can adjust the display of tabs using
```

:set listchars=tab:

```followed by some character sequence with esoteric syntax. However, this is no use if spaces are used to indent rather than TAB.

Maybe there's a way, but I haven't tried to over-customise Vim since I like its defaults by and large.

---

### Post by shawnhcorey on 2010-10-13
I don't use Geany so I don't know what you mean but ViM can automatically do indents.  It has two options: autoindent and smartindent.  Start ViM and type:

```
:help autoindent^M
```

```
:help smartindent^M
```

---

### Post by spjackson on 2010-10-14
> **shawnhcorey said:**
> I don't use Geany so I don't know what you mean but ViM can automatically do indents.  It has two options: autoindent and smartindent.

I could be mistaken, but I thought the OP was talking about the thin grey lines at the various indentation levels in the attached screenshot. This affect cannot be achieved using  autoindent or smartindent, as far as I am aware.

---

### Post by shawnhcorey on 2010-10-14
> **spjackson said:**
> I could be mistaken, but I thought the OP was talking about the thin grey lines at the various indentation levels in the attached screenshot. This affect cannot be achieved using  autoindent or smartindent, as far as I am aware.

In that case, ViM calls this folding.

```
:help folding
```

I don't think ViM puts lines down the side though.

---

### Post by Ascenti0n on 2010-10-14
spkjackson and the submitted image IS what I want to do in Vim. (I was not referring to code folding)

It seems there is a way to put a marker, or rather character of your choice at he point of indentation. This might be the best option thus far. ie use '>' or '|'.

---

### Post by ssam on 2010-10-14
i use cream-showinvisibles.vim (download and put in ~/vim/plugin/) and toggle on and off with F4

[http://www.vim.org/scripts/script.php?script_id=363](http://www.vim.org/scripts/script.php?script_id=363)

---

