---
title: "Accessing data from an OpenOffice calc file using PHP"
date: 2012-05-13
forum: Programming Talk
---

### Post by Rusty au Lait on 2012-05-13
Hello all. I would like to write a program in PHP that reads data from an OpenOffice .ods file. I have found PEAR but have not installed it. Am I on the right path? Is there another package that handles ods files better? I may want to work on LibreOffice as well. Is there someplace else I should be looking?
Thanks for your comments.

---

### Post by lisati on 2012-05-13
If the file is saved in CSV format, then you can use PHP's "[explode]("http://php.net/manual/en/function.explode.php")" function to separate the elements on each line.

---

### Post by Rusty au Lait on 2012-05-14
Thanks Ilsati.
I don't want to add the manual steps of exporting data from OpenOffice. I need to be able to read the file directly.
Ciao

---

