---
title: "firefox userstyle css help"
date: 2009-07-20
forum: Programming Talk
---

### Post by lunaz on 2009-07-20
I'm making a userstyle for an invision board for a specific gaming forum I visit. This will be used with firefox's stylish addon. I do not have access to any code on the server; only stuff on my end.

Using firebug I copied these snippets out of the html to see the order of things:

```

body
#ipbwrapper
<div class="activeusers">
<div class="row2">
<table class="ipbtable" cellspacing="0">
<tbody>
<tr>

body
#ipbwrapper
<div class="borderwrap">
<table class="ipbtable" cellspacing="0">
<tbody>
<tr>

```

The problem is that I want to style the tr's from each section differently but don't know how to be specific since they didn't name the tables differently.

I tried stuff like body>#ipwrapper>div.borderwrap>table.ipbtable tr{code} and .activeusers row1+row2{code} and it didn't seem to have any effect.

Am I screwed? :( There's these little red borders everywhere, and I only want them on the view topic page and view post page but not at footers just where the forum posts are. If there's more code needed let me know & I'll post it :)

---

### Post by cdiem on 2009-07-20
I think you could probably use something like this in order to access the tables (and change it with your custom CSS accordingly):

[PHP]<html>
  <head>
	<style type="text/css">
	.activeusers .ipbtable tr {
	color: blue;
	}	
	.borderwrap .ipbtable tr{
	color: green;
	}
	</style>
  </head>
  <body>
	<div class="activeusers">
	<div class="row2">
 	  <table class="ipbtable" cellspacing="0">
		<tr>
			<td>One</td>
			<td>Two</td>
		</tr>
		<tr>
			<td>Three</td>
			<td>Four</td>
		</tr>
	  </table>
	<div class="borderwrap">
	<p>
	  <table class="ipbtable" cellspacing="0">
		<tr>
			<td>One</td>
			<td>Two</td>
		</tr>
		<tr>
			<td>Three</td>
			<td>Four</td>
		</tr>
	  </table>
  </body>
</html>[/PHP]

Output is:
-------------------------------------------
[COLOR="Blue"]One  	Two
Three 	Four[/COLOR]

[COLOR="DarkGreen"]One  	Two
Three 	Four[/COLOR]
-------------------------------------------

For me it works also without mentioning the "tr" in the style definition - I guess the "tr" inherits some stuff from the upper class.
Just my 0.05.

---

