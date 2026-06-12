---
title: "Basic python help pls.."
date: 2012-06-20
forum: Programming Talk
---

### Post by hopelessone on 2012-06-20
Hi,

```
    def get_inpath(self):
        inpath = tkFileDialog.askopenfilename(
            parent=None, 'title='Select ADEPT or FileOpen-encrypted PDF file to decrypt',
            defaultextension='.pdf', filetypes=[('PDF files', '.pdf'),
                                                 ('All files', '.*')])
        if inpath:
            inpath = os.path.normpath(os.path.realpath(inpath))
            self.inpath.delete(0, Tkconstants.END)
            self.inpath.insert(0, inpath)
        return
```

I'm trying to set a path dir..

```
    def get_inpath(self):
        inpath = tkFileDialog.askopenfilename(
            [COLOR="Magenta"]parent=root, initialdir='C:\\'[/COLOR] ,'title='Select ADEPT or FileOpen-encrypted PDF file to decrypt',
            defaultextension='.pdf', filetypes=[('PDF files', '.pdf'),
                                                 ('All files', '.*')])
        if inpath:
            inpath = os.path.normpath(os.path.realpath(inpath))
            self.inpath.delete(0, Tkconstants.END)
            self.inpath.insert(0, inpath)
        return
```

I've changed the above code, but no go..any ideas? I've googled tkFileDialog and thought the above code was ok...but apparently not..

---

### Post by GWBouge on 2012-06-21
What's the error you're getting?  It may be as simple as that stray ' before title=

---

