---
title: "LAMP and non-English characters"
date: 2012-06-09
forum: Programming Talk
---

### Post by mörgæs on 2012-06-09
A classic PHP project: A script receives input data using POST from an HTML FORM. 

The problem is to get Icelandic characters shown correctly. 

I have experimented with 

```
meta http-equiv="Content-Type" content="text/html; charset=utf-8"
```

and

```
meta http-equiv="Content-Type" content="text/html; charset=iso-8859-15"
```

but they only solve the problem partly. Either I get the user input or rest of the HTML shown correctly, not both.

Are there any serverside settings which might interfere with the charset?

I know that escaping characters could solve the problem, but I prefer to use configuration as much as possible.

---

