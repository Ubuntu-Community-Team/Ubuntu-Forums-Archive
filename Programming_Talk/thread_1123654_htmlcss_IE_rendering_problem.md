---
title: "html/css IE rendering problem"
date: 2009-04-12
forum: Programming Talk
---

### Post by jseiser on 2009-04-12
I am having trouble getting a table to render in a <div>.  I just want it to render like it does in firefox.  In IE the table over runs the <div> tag.  are there anyways to get this to stop?

[http://orion.terra.edu/orion85/final/](http://orion.terra.edu/orion85/final/)

---

### Post by tturrisi on 2009-04-13
Your existing problem is because you have not set the width of all the elements in the page.  Also, don't nest headings inside <p> tags.

Your doctype is HTML 4.01, thus no need for closing tags like < />.

However, why use a table for the menu?  Use an inline list or a <p>.

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html lang="en">
<head>
	<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">
	<title>Final Project</title>
	<link href="main.css" rel="stylesheet" type="text/css">
</head>
<body>

<div id="contents">

<img style="position:absolute; top:45px; left:0px; width:60px; height:468px" src="Banner.jpg">

<p style="width:auto; text-align:center; word-spacing:30px;">Home About Contact</p>
<hr width="90%" color="#453823">
<br>

	<h1>Welcome!</h1>
	
	<h2>April 1, 2009 </h2>
	
	<p>I was looking for a way to design a site without having to use tables as the main layout element.  Using the < div > tag I was able to create layers that I then set properties for.  Such as the background and text color.  I was also able to move the normal banner on a website to the left side of the page.  These elements will all scale with the website, to accomodate for users with different monitor resolutions.  
	</p>

	
	<p>	
		Definiciones significa todo el contenido de los archivos, disco, disco u otro medio con el cual este Contrato se adjunta, incluyendo, sin limitacion a informacion computacional o de programas de computo de  o de terceros; imagenes digitales, fotografas incorporadas, galera de imagenes, sonidos, u otros trabajos artsticos material escrito o archivos con informacion relacionada fonts; actualizaciones, versiones modificadas, ampliaciones, complementos y copias del , en caso de existir, que  le ha otorgado a Usted bajo licencia .  Los terminos significan acceder, instalar, descargar, copiar o de cualquier otra forma obtener beneficios de la utilizacion de las funciones del  de acuerdo con la document. Numero Permitido significaunoa a no ser que se indique lo contrario conforme a una licencia valida otorgada por . Significa un dispositivo electronico que acepta informacion en forma digital o en forma similar y que manipula dicha informacion para obtener un resultado especfico basado en una secuencia de instrucciones.
	</p>
	
</div>
</body>
</html>

```

---

### Post by hessiess on 2009-04-13
Why not use the XHTML strict/transitional DTD insted of HTML4. Menus should be marked-up as a horizontal/vertical list. tables exist for one perpose only, to display tabular data, a menu is *NOT* tabular data.

---

### Post by jseiser on 2009-04-13
alright, that makes sense.  I meant to use the xhtml doctype as well, thanks for reminding me.

---

