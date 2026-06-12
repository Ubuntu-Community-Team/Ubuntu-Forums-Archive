---
title: "Freeze a Line on a shell script"
date: 2009-04-21
forum: Programming Talk
---

### Post by Mbengi Bongi on 2009-04-21
Is there a way of "freezing" a line of text in a shell script, i.e. like on a spreadsheet?

I though perhaps it may be **echo** with a switch but I checked the man page and there doesn't seem to be anything relevant.

Basically I want to write a script that parses and extracts data from a csv file line by line but the first line is my headings and I want that to be visible all the time rather than it disappearing off the screen.

Can anyone help? ;)

---

### Post by tgalati4 on 2009-04-21
Zenity could pop up a dialog box with the header info.

man zenity

---

### Post by ghostdog74 on 2009-04-21
are you parsing line automatically? or are you parsing the file, viewing each line as it goes? show some sample input and describe the output you want.

---

### Post by Arndt on 2009-04-22
> **Mbengi Bongi said:**
> Is there a way of "freezing" a line of text in a shell script, i.e. like on a spreadsheet?

I though perhaps it may be **echo** with a switch but I checked the man page and there doesn't seem to be anything relevant.

Basically I want to write a script that parses and extracts data from a csv file line by line but the first line is my headings and I want that to be visible all the time rather than it disappearing off the screen.

Can anyone help? ;)

If you know that the terminal or terminal emulator is ANSI-compatible (gnome-terminal, xterm, etc. are), you can use a control sequence to set the scroll region. See [http://www.shaels.net/index.php/propterm/7-documents/16-scroll-control](http://www.shaels.net/index.php/propterm/7-documents/16-scroll-control).

For example, try:

```
echo -e "\e[6;24r"
```

---

### Post by Mbengi Bongi on 2009-04-22
> **Arndt said:**
> If you know that the terminal or terminal emulator is ANSI-compatible (gnome-terminal, xterm, etc. are), you can use a control sequence to set the scroll region. See [http://www.shaels.net/index.php/propterm/7-documents/16-scroll-control](http://www.shaels.net/index.php/propterm/7-documents/16-scroll-control).

For example, try:

```
echo -e "\e[6;24r"
```

That's perfect Arndt, that's exactly what I needed!!!  

Thanks very much  :popcorn:

---

### Post by Arndt on 2009-04-22
> **Mbengi Bongi said:**
> That's perfect Arndt, that's exactly what I needed!!!  

Thanks very much  :popcorn:

I last used that feature of terminals 26 years ago, believe it or not; nice that some standards stay worth knowing.

---

