---
title: "batch modify svg files"
date: 2010-11-22
forum: Programming Talk
---

### Post by roccivic on 2010-11-22
I have about 400 svg files, in which a value for an attribute has been incorrectly set. Of course, I would like to avoid opening each file with inkscape and changing the offending value. So, I'm looking for some way of doing this from a batch script or similar. The problem is in the element that has value of "path3881" for the attribute "id". And I would like to change the value of the sttribute "style".

[HTML]
.....
    <path
       style="fill:none;stroke:#000000;stroke-width:5;stroke-linecap:round;stroke-linejoin:round;stroke-opacity:1;stroke-miterlimit:4;stroke-dasharray:none"
       d="m 67.194555,831.37694 -23.125,60.09375 27.09375,0.65625 -3.96875,-60.75 z"
       id="path3881"
       inkscape:connector-curvature="0" />
.....
[/HTML]

Any help at all would be much appreciated.

Many thanks in advance.

---

### Post by Arndt on 2010-11-22
> **roccivic said:**
> I have about 400 svg files, in which a value for an attribute has been incorrectly set. Of course, I would like to avoid opening each file with inkscape and changing the offending value. So, I'm looking for some way of doing this from a batch script or similar. The problem is in the element that has value of "path3881" for the attribute "id". And I would like to change the value of the sttribute "style".

[HTML]
.....
    <path
       style="fill:none;stroke:#000000;stroke-width:5;stroke-linecap:round;stroke-linejoin:round;stroke-opacity:1;stroke-miterlimit:4;stroke-dasharray:none"
       d="m 67.194555,831.37694 -23.125,60.09375 27.09375,0.65625 -3.96875,-60.75 z"
       id="path3881"
       inkscape:connector-curvature="0" />
.....
[/HTML]

Any help at all would be much appreciated.

Many thanks in advance.

Something like this:

```
find . -type f | xargs sed -i 's/path3881/path3882/'
```

Modify to taste.

---

### Post by roccivic on 2010-11-22
But I'm not trying to just rename the path. I'm looking for a way to modify the value of the "style" attribute. Something like:

 [HTML].....
    <path
       style="fill:none;stroke:#000000;stroke-width:5;stroke-linecap:round;stroke-linejoin:round;stroke-opacity:1;stroke-miterlimit:4;stroke-dasharray:none"
       d="m 67.194555,831.37694 -23.125,60.09375 27.09375,0.65625 -3.96875,-60.75 z"
       id="path3881"
       inkscape:connector-curvature="0" />
.....[/HTML]

to 

 [HTML].....
    <path
       style="new style goes here"
       d="m 67.194555,831.37694 -23.125,60.09375 27.09375,0.65625 -3.96875,-60.75 z"
       id="path3881"
       inkscape:connector-curvature="0" />
.....[/HTML]

Not sure, but I think that the files need to be parsed, as there is no guarantee that the attributes will be in that exact order in each file.

Thanks.

---

### Post by debsankha on 2010-11-24
These two lines of python code would do what you want, provided that the style attribute precedes the id attribute:
```

import re
re.sub("<path(?s)[^>]*style=\"([^\"]*)\"[^>]*?id=\"path3881\"[^>]*?>",new_string,oldstring)

```

---

### Post by debsankha on 2010-11-24
This one will work even if style is not before id:
```

re.sub("<path(?s)(?=[^>]*?id=\"path3881\"[^>]*?>)[^>]*?style=\"([^\"]*)\"[^>]*?>",old_string,new_string)

```

---

