---
title: "Basic Javascript Problem"
date: 2013-01-03
forum: Programming Talk
---

### Post by Merrattic on 2013-01-03
There is hopefully a simple answer to this syntax problem.

I have found an image changing function in several places:
```
<script language="javascript">
    
    function changeImage() 
    {

        if (document.getElementById("imgClickAndChange").src == "snacks.png")
        {
            document.getElementById("imgClickAndChange").src="snack1.png";
        }
        else 
        {
            document.getElementById("imgClickAndChange").src="snacks.png";
        }
    }
</script>

<img id="imgClickAndChange" onclick="changeImage()" src="snacks.png" height="500" width="400"/>

```

It doesn't work, and the problem seem to be with the "==" syntax here:
```
if (document.getElementById("imgClickAndChange").src == "snacks.png")
```

I can work around it by using src.match(), but I don't understand why the "==" isn't working?

---

### Post by ofnuts on 2013-01-03
> **Merrattic said:**
> I can work around it by using src.match(), but I don't understand why the "==" isn't working?
Because the value of 
```

document.getElementById("imgClickAndChange").src

```is not "Snacks.png" but "http://path/to/your/server/Snacks.png" (or "file://path/to/your/local/Snacks.png")

---

### Post by Merrattic on 2013-01-03
Thanks for the response. The original tutorial didn't show an absolute reference, and as I say if I use match, the alternative conditions work OK with relative references. I'll give it a go and see what happens.

[EDIT] Just tried that out and it works! :) Many thanks

---

### Post by ofnuts on 2013-01-03
> **Merrattic said:**
> Thanks for the response. The original tutorial didn't show an absolute reference, and as I say if I use match, the alternative conditions work OK with relative references. I'll give it a go and see what happens.

[EDIT] Just tried that out and it works! :) Many thanks
I'm not a JS/DOM expert, but looking at posts on the web, most code seems to expect a relative URL (the one set) to be returned. This retrieved value which is not the one set is disturbing (but Firefox and Chrome behave the same). Different HTML versions adhered to? My test HTML, like yours, was fairly minimal so it didn't define a specific version.

---

