---
title: "Input text size"
date: 2013-10-10
forum: Programming Talk
---

### Post by alfirdaous on 2013-10-10
Hello everybody

I am using Ubuntu 12.10 LTS, Firefox browser, while doing the below code, the input text size is too large, eventhough I made it smaller:

[HTML]
<input type='text' name='title' size='15'>
[/HTML]

Any idea about this

Thx in advance

---

### Post by vasa1 on 2013-10-10
Could you provide some context? Where are you applying this code?

---

### Post by alfirdaous on 2013-10-11
it is only a simple form with the above code

---

### Post by r-senior on 2013-10-11
Are you styling it with CSS? If so, could you show your complete CSS file?

---

### Post by alfirdaous on 2013-10-11
no css applied:

[html]
<input type="text" name="test" size="15" maxlength="40" />
<br />
<input type="text" name="test" size="25" maxlength="40" />
<br />
<input type="text" name="test" size="35" maxlength="40" />
<br />
[/html]

Opera preview
[IMG]http://s22.postimg.org/qtteh3utd/Opera.png[/IMG]

Firefox preview;
[IMG]http://s21.postimg.org/66kxqrvd3/Fire_Fox.png[/IMG]

---

### Post by r-senior on 2013-10-12
The size attribute of an input element of type "text" controls the visible width of the text field. If you want to change the size of the font within the text field, you should style it with CSS. For example:

```

<html>

<head>
[color='red']<style>
input[type=text] {
    font-size: 14pt;
    font-weight: bold;
    color: red;
}
</style>[/color]
</head>

<body>

<form>
<input name="test" type="text" size="15" maxlength="40"/><br/>
</form>

</body>
</html>

```

This is for illustration only. In a real page, you would probably link to an external stylesheet so that you can use it across multiple pages.

[https://en.wikipedia.org/wiki/Cascading_Style_Sheets](https://en.wikipedia.org/wiki/Cascading_Style_Sheets)

---

### Post by alfirdaous on 2013-10-13
What I am looking for, is "size" within "input", not the font-size, the above code did not change anything

---

