---
title: "Apending A word to each line"
date: 2009-07-28
forum: Programming Talk
---

### Post by Chamillionaire2 on 2009-07-28
What's Up?

OK, So With my new project, I need to be able to add a particulate word onto each line, But each line i need to append a different word.
```
sed s/$/.jpg/ Output.txt
```

So far thats what i have got, it appends .jpg to the end of each line, but i need to be able to append a diffrent word to the end of each line.

Anyone know how to?

Thanks Bye.

---

### Post by Bucky Ball on 2009-07-28
Thunar is what you're after. It should be in the repositories.

[http://thunar.xfce.org/pwiki/documentation/bulk_renamer?rev=1145564135](http://thunar.xfce.org/pwiki/documentation/bulk_renamer?rev=1145564135)

---

### Post by stroyan on 2009-07-28
Your description is not clear.
What 'different word' do want append to each line?
If you have a fixed sequence of words that you will append, you can use the paste command to combine a file of beginnings with a file of endings.
```

$ cat names
one
two
three
four
$ cat endings
.jpg
.png
.mp3
.txt
$ paste -d '' names endings
one.jpg
two.png
three.mp3
four.txt

```

---

