---
title: "Using JavaScipt to alter CSS properties"
date: 2011-11-18
forum: Programming Talk
---

### Post by bluedalmatian on 2011-11-18
Im using JavaScript to change the CSS background-color property of a div tag with a unique ID which surrounds a question on an HTML form.
Each question is surrounded by a div with its own unique ID (e.g <div id=Q1>) and also a div with a class of either A or B (div class=A>)

The purpose of the A & B div classes is to alternate the background colours of adjacent questions using a two tone blue colour scheme.  The use of a div with a unique question ID will allow the Java Script vaidation function to override the background-color and set it to red if the question hasnt been answered correctly.

The HTML code is like this:


<div class=A>
	<div id=Q1>
		Question 1 and its associated form fields go here
	</div>
</div>
<div class=B>
	<div id=Q2>
		Question 2 and its associated form fields go here
	</div>
</div>
<div class=A>
	<div id=Q3>
		Question 3 and its associated form fields go here
	</div>
</div>

CSS is:


*.A {
	background-color:#009999;
	font-family:Arial, Helvetica, sans-serif;
}
*.B{
	background-color:#006699;
	font-family:Arial, Helvetica, sans-serif;
}

The validation function sets the background-color of any invalid questions like this:
var questiondiv = document.getElementById("Q1");
questiondiv.style.backgroundColor="red";

This works fine, the problem is that it also pops up a message to the user by changing the visibility property (to visible) of another div with the id=errordialog.....

#errordialog{
	background-color:purple;
	font-family:Arial, Helvetica, sans-serif;
	background: url(semi-transparent-purple-bg.png) no-repeat 0 0 fixed;
        background-size: cover;
 	position: absolute;
 	left:20%;
	width: 60%;
	visibility: hidden;

<div id="errordialog">
	<center>
		<img src="dialog-warning.png" align=middle><font size="5"><b>ERROR - You missed something out!</font></b>
		<br><br><b>
		You must answer the questions highlighted in red
		</b>
		<br><br>
		<form>
			<button onclick="hideErrDialog();">
				<img src="spacer.png" width=150 height=1><h1>OK</h1><br>
			</button>
		</form>
		<br><br>
	</center>
</div> 

Again this works fine but when the button is clicked and the hideErrDialog() function is called, not only does it hide the dialog it also removes the red background-color of the questions back to the two-tone blue, and I have no idea why.  This is the function:


function hideErrDialog()
{
	var errdialogdiv = document.getElementById("errordialog");
	errdialogdiv.style.visibility="hidden";



}

Can anyone enlighten me please?

Thanks

---

### Post by juancarlospaco on 2011-11-19
First, use [ CODE ] [ /CODE ] tags, or its really hard to understand.

With HTML5 maybe you dont need such complex JS programming,
heres a line of my HTML5 form that does what you want (i think)

<input type="text" id="fullname" placeholder="Joe" autocomplete="off" pattern="^[A-Za-z0-9 _]{2,70}[A-Za-z0-9 _]{2,70}$" autofocus required>

So describing, id its an id, placeholder its a placeholder text,
autocomplete disables browser autocomplete, 
pattern is a RegEx that filter the user input automatically,
autofocus gives the focus on page load to this field (use once),
and required makes the completion of this field mandatory for the user.
Of course you can give CSS to this too...

---

