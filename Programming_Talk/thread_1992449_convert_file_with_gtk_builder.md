---
title: "convert file with gtk builder"
date: 2012-05-31
forum: Programming Talk
---

### Post by jboy012000 on 2012-05-31
Hi All,

I am learning how to use glade3 GUI creation program, I have put my simple text editor user interface together, now using GTK I want to convert my glade file to an xml file.

Following the instructions in the glade3 tutorial it says to type in to the terminal command

gtk-builder-convert TextEditor.glade TextEditor.xml

However this does not work.

I get the following responce from terminal

Traceback (most recent call last):
  File "/usr/bin/gtk-builder-convert", line 799, in <module>
    sys.exit(main(sys.argv))
  File "/usr/bin/gtk-builder-convert", line 787, in main
    conv.parse_file(input_filename)
  File "/usr/bin/gtk-builder-convert", line 162, in parse_file
    self._parse()
  File "/usr/bin/gtk-builder-convert", line 234, in _parse
    assert glade_iface, ("Badly formed XML, there is "
AssertionError: Badly formed XML, there is no <glade-interface> tag.

Can anyone help me out with this, I installed the libgtk 2.0-dev as instructed, is there anything else I need to install???

Thanks very much

John

---

