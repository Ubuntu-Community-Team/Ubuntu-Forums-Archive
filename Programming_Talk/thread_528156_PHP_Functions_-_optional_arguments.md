---
title: "PHP Functions - optional arguments"
date: 2007-08-17
forum: Programming Talk
---

### Post by yknivag on 2007-08-17
I'm trying to create a function along the following lines:

```

function formattext($text, $vers, $lang)
{
//some code
return $format_text;
}

```

I want $vers and $lang to be optional arguments (ie they will take on detault vaules if not expressly set in the call.  In otherwords I want the call to be validated on the following syntax:

```

formattext(string $text [, int $vers, string $lang])

```

The code for my function above works, only it throws a warning for every missing argument. Is there anyway I can set these argumets to be optional?

Thanks in advance.

---

### Post by strategicpause on 2007-08-17
Set the optional parameters to a default value such as 0 or "".  That way when nothing is passed to that parameter, it'll just use the default value and not throw up an error.

---

### Post by smartbei on 2007-08-17
Here is a code sample of how to do it:
```

function formattext($text, $vers=1, $lang="eng") {
	//Function code

}

```
You can change the parts after the equals sign to be whatever you want.

---

### Post by yknivag on 2007-08-17
Thanks smartbei, I have the default values as user-configurable variables in my script, I tried the following:

```

function formattext($text, $vers=$default_vers, $lang=$default_lang)
{
 //funtion code
}

```

but I get a parse error on the line where I define the arguments.  Is there aryway I can set defaults without using literals?

---

