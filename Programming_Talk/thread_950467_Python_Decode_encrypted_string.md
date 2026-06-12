---
title: "Python: Decode encrypted string"
date: 2008-10-17
forum: Programming Talk
---

### Post by lixeno on 2008-10-17
Hello,

I'm using python to grab data from a website and update a database.. The problem i have is that some of the data I'm grabbing seems encoded and was just wondering how to decode it?

The data looks something like this:

\x34\60\160\170\x20

---

### Post by eGlyph on 2008-10-17
> **lixeno said:**
> 

The data looks something like this:

\x34\60\160\170\x20

Look at .encode and .decode methods for strings in Python manual.
Basically you have a string in a certain encoding and you have to tell the Python which encoding to use.

---

### Post by lixeno on 2008-10-17
I'm afraid that didn't help me very much.. In php i used regex to extract the numeric value after \ and \x and then ran the results through a function looking something like

```

function convert_string($str, $type) {
	if($type == "oct") {
		if($str < 40) {
			return "";
		}
		return chr(octdec($str));
	} elseif($type == "hex") {
		return urldecode("%".$str);
	}
}

```

but not even this solution works as i have a hard time finding a similar function to **octdec** in python, so if someone could answer that, i could settle for that.

---

### Post by ghostdog74 on 2008-10-17
the oct2dec equivalent in python is :
```


>>> int("77",8)
63
>>>  

```

---

