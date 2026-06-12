---
title: "Python pyperclip copy/pasting error, possible gtk2/3 conflict."
date: 2016-01-07
forum: Programming Talk
---

### Post by TheCommissar on 2016-01-07
Hi folks, 

I'm not quite sure if this is the right forum to post this thread in, so my apologies if it isn't, and can you please let me know where best to post it. I'm a complete newbie with regard to programming and am currently on the "Automate the Boring Stuff with Python" course, which is for absolute beginners.

I have successfully installed and imported the "pyperclip" module into my Python 3.4.3+ Shell, however, when attempting to use "pyperclip.copy" or "pyperclip.paste", I get this error (copy/pasted from the shell):

```
pyperclip.copy('Hello world!')Traceback (most recent call last):
  File "<pyshell#21>", line 1, in <module>
    pyperclip.copy('Hello world!')
  File "/usr/local/lib/python3.4/dist-packages/pyperclip/clipboards.py", line 32, in copy_gtk
    cb = gtk.Clipboard()
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 62, in __getattr__
    raise AttributeError(_static_binding_error)
AttributeError: When using gi.repository you must not import static modules like "gobject". Please change all occurrences of "import gobject" to "from gi.repository import GObject". See: https://bugzilla.gnome.org/show_bug.cgi?id=709183
```

I copied something manually, and attempted to paste it using pyperclip. Same error.

Having had a look at the bug report pages, it looks like there is a conflict because I am attempting to import gtk2 and gtk3 into the same process. I don't really know what this means. The bug report pages, and the other similar bugs which have pages, may well offer instructions as to how to fix this, but I'm not sure how to go about it as I am very out of my depth. Can anyone help me with this?

Please let me know if you need any more information, and thanks in advance.

Currently running 15.10 64-bit.

---

### Post by ian-weisser on 2016-01-07
How, exactly, did you 'install and import' pyperclip?

---

### Post by TheCommissar on 2016-01-08
I think it was:

```
sudo pip3 install pyperclip
```

then, in the python shell:

```
import pyperclip
```

---

### Post by geekhush on 2016-08-28
hi, i have the same error. i went through the pyperclip docs on [https://pyperclip.readthedocs.io/en/latest/introduction.html#not-implemented-error](https://pyperclip.readthedocs.io/en/latest/introduction.html#not-implemented-error) and installed the xsel and xclip utilities and its still giving the same error. how do i solve this.any help appriciated. thanks :)

---

