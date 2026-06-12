---
title: "long echo echo echo..."
date: 2012-04-03
forum: Programming Talk
---

### Post by conradin on 2012-04-03
hi all, 
I have a long stream for an echo command. for ease of reading, I would like to bust up this stream, but not have to recall echo numerous times. 
```

#!/bin/bash
OUTPUT="$(ddate)"
echo -e "<html><head><title>Demo</title></head><body>" "<br><h1>Hail Eris!! Hail Discord!</h1><br>"  "Today is $OUTPUT <br>" "<br>Some Useful links:<br>"\n"<br><a href=""http://www.w3schools.com/"" target=""_blank"">Visit W3Schools!</a> <br>""<br><a href=""http://www.google.com/"" target=""_blank"">Google</a> <br>""<br><a href=""http://www.w3schools.com/"" target=""_blank"">Visit W3Schools!</a> <br>""</body></html>"   > index.html


```

when all the echo bits are on the same line, this works fine. 
when I want to make a new line, I tried \n even with  the -e option, the script wont run. is there a way i can bust this string up for easy reading? all the actual code can be on the same line, i don't care about that, I just want it to be easier to read.

---

### Post by Barrucadu on 2012-04-03
```

#!/bin/bash
OUTPUT="$(ddate)"
echo -e "
<html>
  <head>
    <title>Demo</title>
  </head>
  <body>
    <br>
    <h1>Hail Eris!! Hail Discord!</h1>
    <br>
    Today is $OUTPUT <br>
    <br>Some Useful links:<br>
    <br><a href=""http://www.w3schools.com/"" target=""_blank"">Visit W3Schools!</a> <br>
    <br><a href=""http://www.google.com/"" target=""_blank"">Google</a> <br>
    <br><a href=""http://www.w3schools.com/"" target=""_blank"">Visit W3Schools!</a> <br>""
  </body>
</html>" > index.html

```

---

