---
title: "collective reference to javascript files"
date: 2016-02-03
forum: Programming Talk
---

### Post by maclenin on 2016-02-03
Is there a way to refer, collectively, to multiple javascript files?

For example, I have a.js, b.js ... z.js

Could I store them all in an *alphabet* directory and point to them from the header, in this way (or similar):
```
<!DOCTYPE html>

<html>

<head>

<script src = "alphabet/"></script>

</head>

<body>

</body>

</html>
```
Could I use a wildcard? For example: <script src = "alphabet/*.js"></script>

It would be nice to not have to list them all individually (or sutff them all into one giant *alphabet.js* file).

Thanks for any guidance!

---

