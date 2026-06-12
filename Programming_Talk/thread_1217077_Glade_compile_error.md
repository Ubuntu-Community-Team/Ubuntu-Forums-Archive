---
title: "Glade compile error"
date: 2009-07-19
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-19
I am new to Glade and Gtk+
Picked up a tuorial from net on Glade.
But i am not able to compile my code.
i get an error at the preliminary stage.What is the solution?

Error:

nipun@ubuntu:~$ gtk-builder-convert tutorial.glade tutorial.xml
Traceback (most recent call last):
  File "/usr/bin/gtk-builder-convert", line 756, in <module>
    sys.exit(main(sys.argv))
  File "/usr/bin/gtk-builder-convert", line 744, in main
    conv.parse_file(input_filename)
  File "/usr/bin/gtk-builder-convert", line 161, in parse_file
    self._parse()
  File "/usr/bin/gtk-builder-convert", line 233, in _parse
    assert glade_iface, ("Badly formed XML, there is "
AssertionError: Badly formed XML, there is no <glade-interface> tag.

---

