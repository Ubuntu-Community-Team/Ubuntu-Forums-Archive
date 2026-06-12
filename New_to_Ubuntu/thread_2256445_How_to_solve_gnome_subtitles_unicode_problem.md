---
title: "How to solve gnome subtitles unicode problem?"
date: 2014-12-12
forum: New to Ubuntu
---

### Post by remmas-sido on 2014-12-12
Hi guys 
I was today trying to synchronize a subtitle for my movie to watch it later and the letters of the subtitles were not shown correctly 
P.S 
it's an Arabic subtitle

---

### Post by Impavidus on 2014-12-13
Maybe it doesn't recognise the correct encoding? In Linux, everything has been standardised to Unicode/UTF-8, but other encodings are commonly found in the wild. Your file may be in Windows-1256 or iso 8859-6 encoding. When you open a subtitle file in the subtitle editor, you can select the used encoding. You can also try converting the encoding to UTF-8. A text editor like gedit may be able to do so. Select the current encoding when you open the file (use the "open" menu in the text editor, if your double click the file from the file browser it may not give you the option of selecting the encoding) and then select the UTF-8 encoding in the "save as" menu. Alternatively, use the iconv terminal program.```
iconv --from-code WINDOWS-1256 --to-code UTF-8 --output output-file-name input-file-name
```

There can be some more subtle errors too. If that is the case, please specify what you mean by not showing correctly. One of the few things I know about arabic script is that the conversion from logical character to glyph shape is not as straightforward as in the latin script.

---

