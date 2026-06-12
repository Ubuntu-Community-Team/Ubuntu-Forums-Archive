---
title: "Vala: text file needs to be UTF-8"
date: 2009-11-26
forum: Programming Talk
---

### Post by kumoshk on 2009-11-26
I get the following error,
```
(reader:8018): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
```
while running the following line of code:
```
string text;
FileUtils.get_contents (filename, out text, null);
```

It seems that I'm getting this because the file isn't UTF-8 and it has non-ascii characters (it's ISO-8859-1).

How do I convert it to UTF-8?

---

### Post by LKjell on 2009-11-26
Open the file in gedit and use save as to save. Set encoding to utf-8. You might have to edit the file afterwards so convert those character to utf-8

---

### Post by kumoshk on 2009-11-26
> **LKjell said:**
> Open the file in gedit and use save as to save. Set encoding to utf-8. You might have to edit the file afterwards so convert those character to utf-8

Thanks for the advice&#8212;but, I need to do it in the program (in a cross-platform manner). So this won't work. I want the program itself to be able to handle all files in iso-8859-1 encoding (by converting it to UTF-8, since Vala doesn't do anything but UTF-8 itself).

I know I can change it manually, is what I'm saying.

---

### Post by LKjell on 2009-11-26
If I remember correctly you need iconv then. It should convert from one encoding to another.

---

### Post by kumoshk on 2009-11-26
Thanks! That looks like it should work, as soon as I can figure out the documentation on the library for it (which does exist for Vala, thankfully).

---

### Post by kumoshk on 2009-12-03
How do I get the encoding of a .txt file?

To convert my file to UTF-8 properly, I need to know what its original encoding is. So, without that information, it looks like I have to choose one encoding for my program to convert, and forget about the rest (unless I allow the user to select the encoding manually).

---

### Post by Arndt on 2009-12-03
> **kumoshk said:**
> How do I get the encoding of a .txt file?

To convert my file to UTF-8 properly, I need to know what its original encoding is. So, without that information, it looks like I have to choose one encoding for my program to convert, and forget about the rest (unless I allow the user to select the encoding manually).

The program 'file' at least can distinguish between UTF-8, UTF-16 and Latin-1, probably many more.

Interactively, you can give the text file to Emacs or Firefox and they will try to select the correct encoding.

---

### Post by kumoshk on 2009-12-03
> **Arndt said:**
> The program 'file' at least can distinguish between UTF-8, UTF-16 and Latin-1, probably many more.

Interactively, you can give the text file to Emacs or Firefox and they will try to select the correct encoding.

I believe I need a solution that could be cross-platform more easily. It didn't recognize the charactersets I tried, though, but it could be cool if I need to distinguish between Unicode formats.

Until I have a solution, I'll just let my saved configuration file specify a secondary characterset&#8212;and tell people in the help that they can change it there (or I'll make a menu option); UTF-8 is the default, so that's why I say a secondary characterset (although that does require them to know what it is, unfortunately).

---

### Post by LKjell on 2009-12-03
You should be able to distinguish between utf-8 and utf-16 since there are some bytes that are illegal in utf-8 but legal in utf-16.

---

### Post by kumoshk on 2009-12-03
> **LKjell said:**
> You should be able to distinguish between utf-8 and utf-16 since there are some bytes that are illegal in utf-8 but legal in utf-16.

Yeah. For this particular project I don't need to convert between Unicode formats, since they can all display pretty much the same stuff anyway. I just need to convert non-Unicode formats to UTF-8 (Vala's default encoding).

At least, I think I don't need to worry about that. I actually haven't tried loading a utf-16 or 32 file yet.

EDIT: Yep, I need to worry about it. GLib.convert doesn't seem to work on it, either (although it's worked on all the non-Unicode stuff). I'll have to try Iconv.

---

