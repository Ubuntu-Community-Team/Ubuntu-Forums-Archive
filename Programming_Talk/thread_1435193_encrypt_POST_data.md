---
title: "encrypt POST data?"
date: 2010-03-21
forum: Programming Talk
---

### Post by ja660k on 2010-03-21
hey guys,

as the title says, how do i encrypt post data... this needs to be done on the client side, ie js. 

so how do i get js to send variables to php?

---

### Post by jflaker on 2010-03-21
> **ja660k said:**
> hey guys,

as the title says, how do i encrypt post data... this needs to be done on the client side, ie js. 

so how do i get js to send variables to php?

JS wouldn't be the way...

Use SSL to transmit the post/data and once your PHP app has the data, use the encryption available on the server side to encrypt, then store the data...

JS encryption, while plausible, isn't reliable as not all clients have javascript enabled and I don't think there are functions available with JavaScript to do encryption......the most you can do is alphanumeric substitution to obscure the data

---

### Post by ja660k on 2010-03-21
yeah sorry, i probably should of said that.
its for an example. 

i would be using SSL but i need to use js that sets post data.
(silly i know)

so my question now becomes, can i set POST data from js? to another page
(not ajax)

---

### Post by raffaele181188 on 2010-03-21
Without using AJAX I think it will be quite "complicated" and "dirty"
The only thing I can think of is to dynamically create a <form>, method post, then adding <input> (all in your javascript) and then call form.submit(), but I don't know if it will work and will be portable, you shoul try on your own

[FarFarFar.com]("http://farfarfar.com/scripts/encrypt/") is a GPLv3 encryption library, but there could be more

---

### Post by Hellkeepa on 2010-03-21
HELLo!

You could try to use the JS to intercept the submit action, overwrite the contents of the inputs with their encrypted content,  and then permit the form to submit normally. However, I give you no guarantees that this'll work.

Happy codin'!

---

### Post by soltanis on 2010-03-21
You should really use SSL for this. Your site is open to vulnerabilities (weak encryption, javascript injection) if you rely of JS to do this for you.

Not to mention that JS is slow.

---

### Post by ja660k on 2010-03-22
hellkeepa: yes exactly!
how do i do that?

soltanis: look at post #3, im not using this for actual use on the web. its just an example for school.

---

### Post by Hellkeepa on 2010-03-22
HELLo!

Half-pseudo code:
```
function Encrypt (formElement) {
    var inputFields = formElement.getFields();
    foreach (inputFields as Elm) {
        Elm.value = encryptData (Elm.value);
    }

    return true;
}

<form method="post" action="" onsubmit="return Encrypt (this)">
```
Try something like that, and see if it works. Might be a lot easier to accomplish using jQuery, but if you're going to demonstrate the method I'm not sure if I'd rely on any third party libraries.

Happy codin'!

---

### Post by myrtle1908 on 2010-03-22
> **raffaele181188 said:**
> [FarFarFar.com]("http://farfarfar.com/scripts/encrypt/") is a GPLv3 encryption library, but there could be more

[http://code.google.com/p/crypto-js/](http://code.google.com/p/crypto-js/)

---

### Post by ja660k on 2010-03-22
errr its not working :(
i cant figure out how to send changed value.

i have 
[PHP]
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>SEC part 1</title>
<script type="text/javascript">
// the ceaser value, hard coded.
var shift = 3;
function encrypt(fe){
    var d = fe.elements[0].value+"hello"
    //d = d+"hello";     

    return true; 
}
</script>
</head>

<body>

    <!-- <form id="form1" name="form1" method="post" onsubmit ="return encrypt(this)"> -->
    <form id="form1" name="form1" method="post" action="recvCode.php" onsubmit ="return encrypt(this)">
  <p>Enter some data to encrypt.</p>
  <p>
    <textarea id="text" cols="45" name="text" rows="8"></textarea>
</p>
  <p>
    <input type="submit" name="send" id="send" value="Send Data"  />
  </p>
</form>
</body>
</html>

[/PHP]

and in the recvCode php all it has is
[PHP]<pre>
<? print_r($_POST); ?>
</pre>
[/PHP]

i need that to be what i put in the txtarea+hello
but it doesnt, all it does it send the textarea msg?

:(

---

### Post by Zayfox on 2010-03-22
$_POST in itself doesn't print anything. You need to give it values, eg: $_POST['valuename'];
On this note, add a "name" attribute to each element in your form, this attribute corresponds to the value in $_POST['valuename'];

**Edit:**
On that note, from my limited experience with javascript (I'm more of a backend - PHP guy ;)), if it's anything like PHP you need to use "." instead of "+", as "+" implies your two values are integers.

---

### Post by ja660k on 2010-03-22
yes it does,
thats why i use print_r...
[http://au2.php.net/manual/en/function.print-r.php](http://au2.php.net/manual/en/function.print-r.php)

EDIT
I'm pretty sure to do string concatenation is + in js( but i may be wrong)

---

### Post by Zayfox on 2010-03-22
> **ja660k said:**
> yes it does,
thats why i use print_r...
[http://au2.php.net/manual/en/function.print-r.php](http://au2.php.net/manual/en/function.print-r.php)
> The connection was reset

      

The connection to the server was reset while the page was loading.Badass.
**Edit:**
I didn't pick up you were using print_r.
Try my second comment.

---

### Post by ja660k on 2010-03-22
im trying to concatenate my the data, im sure thats done with a + in js
"hello"+"world"

but i cant manage to return that to send to the php :(

---

### Post by myrtle1908 on 2010-03-22
In your example, you were not actually altering the underlying form value.  You were merely assigning it to a variable named 'd'.

```
function encrypt(fe){
  fe.elements[0].value += 'hello';  // append 'hello' to zeroeth form element
  return true; 
}
```

Also, you should use firebug so that you can inspect the DOM, see whats being posted etc.

[http://www.getfirebug.com](http://www.getfirebug.com)

---

### Post by Zayfox on 2010-03-22
> **myrtle1908 said:**
> In your example, you were not actually altering the underlying form value.  You were merely assigning it to a variable named 'd'.

```
function encrypt(fe){
  fe.elements[0].value += 'hello';  // append 'hello' to zeroeth form element
  return true; 
}
```Also, you should use firebug so that you can inspect the DOM, see whats being posted etc.

[http://www.getfirebug.com](http://www.getfirebug.com)
I missed that.
I am disappoint.

---

