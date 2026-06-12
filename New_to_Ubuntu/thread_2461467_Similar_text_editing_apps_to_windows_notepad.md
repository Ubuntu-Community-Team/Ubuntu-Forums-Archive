---
title: "Similar text editing apps to windows notepad"
date: 2021-05-01
forum: New to Ubuntu
---

### Post by unitedmetalheads on 2021-05-01
Hello. I have recently installed ubuntu 21.04 and I'm a newbie. I was trying to edit the txt file that I had written in windows notepad. I had made some kind of a table in that file using dashes and the vertical bar symbol. It was all fine in notepad but now when i open it in ubuntu text editor, the table is messy, the vertical bars have moved but its still fine in notepad. What is the cause of this? is there an app for ubuntu that would open txt files in a format just like notepad itself without messing up that table? both of them are on 100 percent zoom. Thanks in advance.

---

### Post by tea for one on 2021-05-01
Here is a selection to consider [https://alternativeto.net/software/notepad/?license=free&platform=linux](https://alternativeto.net/software/notepad/?license=free&platform=linux)

I'm sure that there are more choices and other forum members will offer their suggestions.

---

### Post by ajgreeny on 2021-05-01
Is your file really a .txt from notepad or was it saved as an .rtf file which notepad can both read and write, if I remember correctly, but which many Linux text editors can not.

Try abiword, a much faster and simpler word processor than LO Writer which will certainly open any .rtf files i have. There may be other applications as well but I'm not sure of how many or which they are.

---

### Post by coffeecat on 2021-05-01
Welcome to the forum, @unitedmetalheads.

I have tried simulating what you describe and cannot reproduce your problem. I created and saved a test text file in Notepad in Windows 10. This included pipe symbols (vertical bars) and hyphens separated by spaces and aligned on different lines. The file was displayed correctly and properly aligned when opened in the default text editor (gedit) in Ubuntu.

Question: are you using the default font in Notepad? It defaults to a monospace font, just as gedit does, but have you changed this to another font?

It would be easier for members to help diagnose the problem if you were to attach an example file to your next post. Prepare a file in Notepad that doesn't display correctly in Gedit, and upload it to your post using the attachment utility. You can access the attachment utility from the paperclip icon in the advanced message editor when replying.

---

### Post by ActionParsnip on 2021-05-01
If you use notepad++ in both you'll probably be OK.

---

### Post by Impavidus on 2021-05-01
There are many text editors for Ubuntu, but your problem is probably not with the editor, but with the font. The characters have different width on your Windows Notepad than on the text editor you use in Ubuntu (and not all by the same ratio). It would be best to use a monospaced font. A plain text file doesn't save any font info, so it opens in whatever font you set as the default in your text editor.

Another possible cause for the problem is tabs. If you use tabs for alignment, but use different tab settings in your text editors, alignment fails. Normally tabs align to multiples of 4 or 8 characters, if using a monospaced font.

---

### Post by ActionParsnip on 2021-05-01
Also, if its a tabled bit of information then use a spreadsheet.. Surely

---

### Post by Impavidus on 2021-05-02
It depends. When you write your own software to process the table, plain text is much easier to parse than whatever spreadsheet format you may decide to use. And once you have more than a few thousand rows or want some more advanced calculations, spreadsheets are a bit of a kludge anyway.

Or this is already a format that can be parsed by some other software, like a wikitext table.

BTW, when moving plain text files back and forth between Ubuntu and Windows, keep in mind that both systems have different conventions for line endings or line separators. Most text editors know how to handle this automatically, but if you want to learn more, read [this](https://en.wikipedia.org/wiki/Newline).

---

### Post by TheFu on 2021-05-03
**Geany** is cross platform. There are other editors which are too.

Of course, everyone knows that **vim** is the only editor anyone should ever need on any platform, but that could start a religious war.  My router has vim, but no other editor.  Vim in the hands of an expert is freakin' amazing.

There are 2 commands to deal with the line ending stuff.  **dos2unix** and **unix2dos**, but if you just use any of the Unix editors on Windows, this problem goes away. There must be at least 20 of them that are cross platform.  Geany is light and handles all sorts of languages, supports plugins, and will allow compilers, linkers and debuggers to be hooked in, if you must.

---

