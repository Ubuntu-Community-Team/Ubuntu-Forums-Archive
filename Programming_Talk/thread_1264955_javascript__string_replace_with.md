---
title: "javascript  string replace with \"
date: 2009-09-12
forum: Programming Talk
---

### Post by tc101 on 2009-09-12
In a string in javascript, how do I replace all instances of \ with \\

I tried this and it didn't work:

NewString = OldString.replace("\","\\")

---

### Post by falconindy on 2009-09-12
It's been a while since I've touched all that much Javascript, but I suspect that \ is the escape character in JS, as it is in many languages. Therefore, your statement aims to find nothing at all and replace it with a single \. Long story short, you need to escape your backslashes:
```
NewString = OldString.replace("\\","\\\\")
```

---

### Post by myrtle1908 on 2009-09-12
Learn about about escaping characters.

```
<script language="javascript">
var s = 'abc\\def\\ghi';
alert('before=' + s + '\nafter=' + s.replace(/\\/g, '\\\\'));
</script>
```

---

