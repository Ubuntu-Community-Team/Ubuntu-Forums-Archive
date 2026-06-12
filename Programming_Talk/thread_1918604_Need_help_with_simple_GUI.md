---
title: "Need help with simple GUI"
date: 2012-02-01
forum: Programming Talk
---

### Post by Marlonsm on 2012-02-01
I've been trying to create a GUI to enter some data and store it in a text file, then run a Python program that uses the numbers in that file as parameters.

Does anyone know a simple way of doing so?

The program I'm making needs 23 parameters to run. The GUI would generate a text file like this:

1 2 3
4 5
6 7 8 9 10

and so on, where each number is one of those parameters.

I would also like the GUI to read an existing text file and fill the entry fields with it.

As of which language/toolkit to use, I'm open to suggestions. There is not need of a fancy interface, it could even be run inside a web browser, if needed.

(If what I wrote here isn't clear, I'll try to explain it better.)

Thank you in advance.

---

### Post by cknu on 2012-02-01
Write an HTML page with N input fields and a button.
On button click, trigger a Javascript function to write stuff to a file.

```
function WriteFile()
{

var fh = fopen("file.txt", 3); // Open the file for writing

if(fh!=-1) // If the file has been successfully opened
{
    var str = getElementById("textfield1").value()+" "+getElementById("textfield2").value()+ ... +" " ;
    fwrite(fh, str); // Write the string to a file
    fclose(fh); // Close the file 
}

}
```

I still don't get the poin of calling a program with 23 parameters. You can use QT to make a GUI in python, but i think html and JS would be easier.

---

### Post by Marlonsm on 2012-02-01
Thanks, it's just what I need, but I couldn't get it to work, I don't know much about Javascript.

Here is what I tried:

```

<html>
<head>
  <title>test</title>
  <script language="javascript" type="text/javascript" defer="defer">
function WriteFile()
{
var fh = fopen("file.txt", 3); // Open the file for writing
if(fh!=-1) // If the file has been successfully opened
{
var str = getElementById("var1").value()+" "+getElementById("var2").value();
fwrite(fh, str); // Write the string to a file
fclose(fh); // Close the file }
}
  </script>
</head>
<body>
Var1: <input name="var1" type="text"><br>
Var2: <input name="var2" type="text"><br>
<a href="#" onclick="jsFunction()>Save</a>
</body>
</html>
```

---

### Post by memilanuk on 2012-02-01
Might also take a look @ easyGUI...

[http://easygui.sourceforge.net/](http://easygui.sourceforge.net/)

---

### Post by Marlonsm on 2012-02-01
> **memilanuk said:**
> Might also take a look @ easyGUI...

[http://easygui.sourceforge.net/](http://easygui.sourceforge.net/)

Thanks, it seems to be just what I needed!

---

