---
title: "Make my own Geany color scheme?"
date: 2012-04-20
forum: Programming Talk
---

### Post by TheGuyWithTheFace on 2012-04-20
Despite the fact that I'm only learning how to program, I still have already developed preferences towards syntax highlighting. Does anyone know how I can make my own color scheme for Geany?

---

### Post by r-senior on 2012-04-20
Go to Tools -> Configuration Files -> filetypes.common and play with the colours. You can also edit the files in ~/.config/geany/filedefs, copying from /usr/share/geany where necessary.

More info: [http://www.geany.org/manual/current/index.html#special-file-filetypes-common](http://www.geany.org/manual/current/index.html#special-file-filetypes-common)

As the name suggests, filetypes.common is common styles across languages. The other filetypes.* files are for specific languages.

---

### Post by TheGuyWithTheFace on 2012-04-21
Thank You soo much!

---

### Post by TheGuyWithTheFace on 2012-04-21
> **r-senior said:**
> 
As the name suggests, filetypes.common is common styles across languages. The other filetypes.* files are for specific languages.

so, how would I make a specific file for, say, python?

---

### Post by r-senior on 2012-04-22
You'd edit the files in ~/.config/geany/filedefs, copying from /usr/share/geany where necessary.

For example, I like """ and ''' to be styled as strings, even though they are used a lot for documentation comments. So I copied /usr/share/geany/filetypes.python to ~/.config/geany/filedefs/filetypes.python and changed:

```
triple=string
tripledouble=commentdoc

to 

triple=string
tripledouble=string

```

So both triple-quotes are now styled as strings. Then I change the style with filetypes.common:

```
string=0x995c00
```

So the standard approach is to use the definitions in filetypes.common to create named styles and associate colours and text attributes with those. Then refer to those named styles in the filetypes.python file to style specific aspects of Python code. I've used existing named styles but you can create additional ones -- with the risk of creating a confusing colour scheme if you create too many.

You can also break from this standard approach and style directly in the filetypes.python file.

Beyond that, you'll have to read the documentation and experiment.

---

