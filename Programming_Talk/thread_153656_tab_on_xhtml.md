---
title: "tab on xhtml"
date: 2006-04-01
forum: Programming Talk
---

### Post by orlox on 2006-04-01
I'm trying to align something on a page using xhtml, and a tabulation tag would be pretty usefull. Is there any? Or is there another way of aligning them that's similar to using tab's?

---

### Post by engla on 2006-04-01
Well formatting and placement isn't really done with xhtml, except with tables.

You can insert literal tabs in a <pre> block though..

or you can use css to align text.

---

### Post by orlox on 2006-04-01
I thought it would be wiser with css, and the <pre> tag didn't work. To be more precise, this is my page source
```

		Nombre :
		<input type="text" name="nombre"></input><br />
		Apellido :
		<input type="text" name="apellido"></input><br />
		Rut (ej:14560234-1) :
		<input type="text" name="rut"></input><br />
		Email (a@a.com) :
		<input type="text" name="email"></input><br />
		Username :
		<input type="text" name="username"></input><br />
		Password :
		<input type="password" name="password1"></input><br />
		Verificar Password :
		<input type="password" name="password2"></input><br />

```

I'm trying to make a form here, and I'd like that the inputs appear at the side of the textual description, but aligned with respect to each other. How can I do that with css?

---

### Post by Corvillus on 2006-04-02
You could accomplish this with CSS in this way
[html]
<html>
<head>
<style>
.row {
	width: 500px;
}
.row .label {
	width: 30%;
	float: left;
}
.row .text {
	float: right;
	width: 70%;
}
</style>
</head>
<body>
<form>
<div class="row"><span class="label">First Name</span><input type="text" class="text" name="first_name"/></div>
<div class="row"><span class="label">Last Name</span><input type="text" class="text" name="last_name"/></div>
<div class="row"><span class="label">E-mail Address</span><input type="text" class="text" name="email"/></div>
</form>
</body>
</html>
[/html]

That said, forms are one of the few areas where tables actually make sense semantically, since a form is typically a tabular input structure.

---

