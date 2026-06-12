---
title: "Problem Quoting Variable In a String"
date: 2009-05-26
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-05-26
Ey fellas, I am having some problems quoting a combined string with .join, here is my code:

```

elif TempList[nI] == "USER":
    user = ' '.join((TempList[nI+1],TempList[nI+2]))
    return ' '.join(('user',"Attempting To Connect")) #I am trying to quote user

```

It gives me this:
```

user Attempting To Connect

```

Instead of what I want, which is:
```

'John Smith' Attempting To Connect #note the single quotations

```

If anyone happens to also make it so that I can put 'John Smith' in double quotations, that would be great. Any help really appreciated thanks!

---

### Post by StunnerAlpha on 2009-05-26
Nevermind I actually ended up figuring it out. This is what I ended up doing:

```

return ' '.join((("'"+user+"'"),"Attempting To Connect"))

```

If there are any other easier ways to do it and you guys dont mind sharing that would be great. Thanks.

---

### Post by iiska on 2009-05-26
Assuming that you are coding in Python, you could do it this way also:

```
return "'%s' attempting to connect" % user
```

---

### Post by Jacks0n on 2009-05-27
```

elif TempList[nI] == "USER":
	return '"%s %s" Attempting to Connect' % (TempList[nI+1],
				  		  TempList[nI+2])

```

That *should* work.

Jackson

---

### Post by StunnerAlpha on 2009-05-27
Thanks fellas.

---

