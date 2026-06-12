---
title: "Look at my PHP"
date: 2006-02-18
forum: Programming Talk
---

### Post by cobbweb on 2006-02-18
the following code is saved as an HTML file called feedback.html

[HTML]
<html>
<body>
<form method="post" action="sendmail.php">
  Email: <input name="email" type="text" /><br />
  Message:<br />
  <textarea name="message" rows="15" cols="40">
  </textarea><br />
  <input type="submit" />
</form>
</body>
</html>

[/HTML]


Then I have this PHP file called sendmail.php that has this code. 
[PHP]

<?
  $email = $_REQUEST['email'] ;
  $message = $_REQUEST['message'] ;

  mail( "thenetduck@gmail.com", "Feedback Form Results",
    $message, "From: $email" );
  header( "Location: http://bilbob60.freecoolsite.com/thankyou.html" );
?>

[/PHP]

 You can view the page at [http://bilbob60.freecoolsite.com/feedback.html](http://bilbob60.freecoolsite.com/feedback.html)

 The Problem that im having is, when i fill out the information, i never recieve an email. Do i need some type of server or somthing? As you probably assumed, im learning PHP. Any ideas on why I dont recieve an email with the information filled out? Maby if you do a test and try using that form to email me it will work. Anyhelp is much needed
 Thanks, 
    Cobbweb

---

### Post by sapo on 2006-02-18
You are missing the headers i think.. this works for me:

[php]				$mensagem = '<html>
								<head>
								<title>BR IMPORT</title>
								</head>
								<body>
								<table>' .
								$msg . '
								</table>
								</body>
								</html>';

				$headers  = 'MIME-Version: 1.0' . "\n";
				$headers .= 'Content-type: text/html; charset=iso-8859-1' . "\n";
				/* headers adicionais */
				$headers .= 'To: ' . $cliente . ' <' . $destino . '>' . "\n";
				$headers .= 'From: Me <someemail@somedomain.com>' . "\n";
mail($destino,$assunto,$mensagem,$headers)[/php]

But you should read more about php mail, and more about headers, my code will send a html message.. for a text file it would be different.

---

### Post by vibes on 2006-02-18
sapo is right edit your headers, also i would change $_REQUEST to $_POST and maybe code in a few checks or someone will endup abusing your server

---

### Post by Enter on 2006-02-19
are you testing it on localhost? or on some hosting? a lot of hostings are disabling the mail(); function for security reasons

---

### Post by fakey1223 on 2006-04-26
To get the php mail() function working, I installed the sendmail package (doing so removed postfix).

---

### Post by LordHunter317 on 2006-04-26
[QUOTE=vibes]also i would change $_REQUEST to $_POST[/quote]Adds no security.

> and maybe code in a few checks or someone will endup abusing your serverThere's no way to abuse the server in this manner besides spam himself.

[quote=fakey1223]To get the php mail() function working, I installed the sendmail package (doing so removed postfix).[/quote]There's no reason to do this.  Postfix is sendmail-compatible.

---

