---
title: "is unicode my problem?"
date: 2010-04-03
forum: Programming Talk
---

### Post by chris200x9 on 2010-04-03
I have started to write an ebarassingly easy function but it won't work. I have checked numorus tutorials and it should work, then I found some mention of it being for ASCII. So my question is, is there something wrong with this code or is it because geany uses unicode?

```
 string FixSentence( string sentance)
{
	int i = 0;
	string newstring;
	while (sentance[i])
	{
		newstring[i] =  tolower(sentance[i]);
		
	i++;
	}
	cout << newstring;
	return "";
} 
```

---

### Post by LKjell on 2010-04-03
Yea there is some problems with the code...
Have a read on arrays.

---

### Post by chris200x9 on 2010-04-03
got it sorry, question why when I reassemble a string can't I just output the string, why do I have to uptput each char?

---

### Post by LKjell on 2010-04-04
The string is a class while when you convert it to a char array to manipulate whatever it is an array now. However you can use the replace method.

[http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/)

---

