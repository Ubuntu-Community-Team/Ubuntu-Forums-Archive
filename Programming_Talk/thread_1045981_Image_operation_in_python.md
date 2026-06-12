---
title: "Image operation in python"
date: 2009-01-21
forum: Programming Talk
---

### Post by adamsnative on 2009-01-21
Is there any method by which i can scale down 8 bit image to 4 bit image in python
This is required to speed up my work as it wont affect the output

Is there any code in python which can do this

Plz help or suggest some method to do it

---

### Post by Wybiral on 2009-01-21
I'm pretty sure [PIL]("http://www.pythonware.com/products/pil/") has various options when saving in different formats.

---

### Post by eightmillion on 2009-01-21
> **adamsnative said:**
> Is there any method by which i can scale down 8 bit image to 4 bit image in python
This is required to speed up my work as it wont affect the output

Is there any code in python which can do this

Plz help or suggest some method to do it

You might also look at pythonmagick. For example:

```

import PythonMagick
image = PythonMagick.Image('image.jpg')
image.depth(4)
image.write('image.jpg')

```

---

### Post by Gina on 2010-02-14
I'm creating a python app and wish to use ImageMagick to produce some graphics for web page use.  PythonMagick is mentioned in the IM docs as an API to use with Python but I can't seem to find any more info.  Do you know where I can find basic documentation on using the PythonMagic API, please?

---

### Post by Gina on 2010-02-16
Isn't anyone using Python Magick nowadays?  I guess the lack of documentation puts people off.  I'm now creating a bash script in Python and then running that as a system call.  PythonMagick is supposed to be more flexible and powerful...  oh well...

---

