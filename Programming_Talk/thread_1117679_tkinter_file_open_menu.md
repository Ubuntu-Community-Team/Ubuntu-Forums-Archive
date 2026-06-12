---
title: "tkinter file open menu"
date: 2009-04-06
forum: Programming Talk
---

### Post by ulysses-31 on 2009-04-06
Hi there

I Have created a really simple GUI in tkinter so that when i press a button it increases the contrast of an image for which i used PIL.
What i wanna do is create a file open button to grab a bunch of images store them in a list, add my modification to all of them and then save them in a output directory

Could anyone explain if there is a simple way i can do this.

Cheers
Scott

---

### Post by stevescripts on 2009-04-07
Below is a simple example of using tkFileDialog to select multiple files - 

I am sorry for the delay in posting this, please try it out - the delay was due to the fact that is does not work properly on the machine where I was developing it, but, it does seem to run correctly on every other box I have tried ...

```

import Tkinter, tkFileDialog

root = Tkinter.Tk()

files = tkFileDialog.askopenfilename(parent = root, filetypes = [('JPEG', '*.jpg'), ('ICON', '*.ico'), ('GIF', '*.gif')], multiple = 1 )

for i in files:
    print i


```

Hope this helps a bit.

If anybody else sees problems with this snippet, please let me know.

Steve

---

