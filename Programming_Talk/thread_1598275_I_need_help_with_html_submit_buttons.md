---
title: "I need help with html submit buttons"
date: 2010-10-16
forum: Programming Talk
---

### Post by hoboy on 2010-10-16
I have a an html form with 1 input fields,and an upload and delete buttons.
The form calls a java Servlet, I want to react depending witch button is is click on.
If it is delete then I want to delete some files, if it is upload I want to upload some file.
How can I distinguish in my servlet code with button is been click ?
I don't want to use javaScript as I don't know how to code in javaScript.
tks

---

### Post by James78 on 2010-10-16
Here's how I would do it in Python Werkzeug.

```
<form action="./" method="post">
<input type="submit" name="submit1" value="Submit1!">
<input type="submit" name="submit2" value="Submit2!">
</form>

req = local.request
getform = req.form.get
if req.method == 'POST':
    submit1 = getform('submit1')
    submit2 = getform('submit2')
    print submit1 # submit1 = "Submit1!"
```
As you can see, I use the name field in HTML to specify what field it is, and I use it in the code to get the value.

[W3Schools]("http://www.w3schools.com/html/html_forms.asp") in depth examples

---

### Post by spjackson on 2010-10-16
Yes it is possible to have two different Submit buttons and to detect which one has been used, without javascript.

```

<form method=post action="show.php">
<input type=submit name=submit value="Delete">
<input type=submit name=submit value="Upload">
</form>

```I don't know how you access the posted data in a Java Servlet, but in php, you can do

```

if ($_POST['submit'] == "Delete")
{
    print "Delete";
}
else if ($_POST['submit'] == "Upload")
{
    print "Upload";
}

```

---

### Post by hoboy on 2010-10-17
Thanks guys

---

