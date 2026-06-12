---
title: "Help adding button functionality to a table cell - HTML, CSS, JavaScript"
date: 2009-11-19
forum: Programming Talk
---

### Post by stooshbunutu on 2009-11-19
Hey all,

I am doing my computer science coursework in the "Programmig for the World Wide Web" module. Part of it involves making an on-screen keyboard in a webpage. generally this has been very successful for me. However I wanted to add some additional visual features. I am using css to make the border of each cell 'outset' to make it look more like a button. What I want to be able to do is make it so the as the cell is clicked the border temporarily changes to an 'inset' border so it looks like a button press. I know how to do this for a hyperline using the built-in 'on' class. How can I do this for my table cell please?

Here is the code for me page
```

<html>
	<head>
		<title>Keyboard</title>
		<style type="text/css">
			td.key:hover{
				cursor: pointer;
				background-color: #6688EE;
			}
			td.key{
				background-color: #6688EE;
				border-style: outset;
			}
			td.input{
				background-color: #6688EE;
				border-style: outset;
			}
			a{
				font-family: verdana;
				color: #003355;
				font-weight: bolder;
				font-size: 25px;
			}
			input{
				background-color: #C0CCED;
				font-weight: bold;
				font-size: 25px;
				color: white;
				border-style: inset;
			}
			#main {
				position: absolute;
				width: 900px;
				top: 10px;
				left: 50%;
				margin-left: -450;
			}
		</style>
		<script type="text/JavaScript">
			var key_type = "qwerty";
			function draw_qwerty_keys(){
				var keyboard;
				keyboard = "<table border='0' cellspacing='0'>"
				for(i=0;i<3;i++){
				keyboard += "<tr>"
					for(j=0;j<10;j++){
						if(i==0){
							switch(j){
								case 0: x = "q"; break;
								case 1: x = "w"; break;
								case 2: x = "e"; break;
								case 3: x = "r"; break;
								case 4: x = "t"; break;
								case 5: x = "y"; break;
								case 6: x = "u"; break;
								case 7: x = "i"; break;
								case 8: x = "o"; break;
								case 9: x = "p"; break;						
								default: x = "";
							}
						}else if(i==1){
							switch(j){
								case 0: x = "a"; break;
								case 1: x = "s"; break;
								case 2: x = "d"; break;
								case 3: x = "f"; break;
								case 4: x = "g"; break;
								case 5: x = "h"; break;
								case 6: x = "j"; break;
								case 7: x = "k"; break;
								case 8: x = "l"; break;
								case 9: x = "_"; break;
								default: x = "";
							}
						}else if(i==2){
							switch(j){
								case 0: x = "/"; break;
								case 1: x = "z"; break;
								case 2: x = "x"; break;
								case 3: x = "c"; break;
								case 4: x = "v"; break;
								case 5: x = "b"; break;
								case 6: x = "n"; break;
								case 7: x = "m"; break;
								case 8: x = "("; break;
								case 9: x = ")"; break;						
								default: x = "";
							}
						}
						keyboard += "<td width='40px' height='30px' align='center' valign='center' class='key' onclick='keyPress(this.firstChild.innerHTML.toLowerCase());' onmouseover='' id='row"+i+"col"+j+"'><a>"+x.toUpperCase()+"</a></td>";
					}
					if(i==0){
						keyboard += "<td colspan='10' class='input' align='center'><input type='text' size='30' id='search_box'></td>"
						keyboard += "</tr>";
					}else if(i==1){
						keyboard += "<td width='80' colspan='5' height='30px' align='center' valign='center' class='key' onclick='backspace()' id='backspace'><a>BackSpace</a></td>";
						keyboard += "<td colspan='5' align='center' valign='center' class='key' onclick='clear_search()'><a>Clear</a></td>";
						keyboard += "</tr>";
					}else if(i==2){
						keyboard += "<td width='160' colspan='3' height='30px' align='center' valign='center' class='key' onclick='change_qwerty_keys()' id='querty'><a>Qwerty</a></td>";
						keyboard += "<td width='160' colspan='3' height='30px' align='center' valign='center' class='key' onclick='change_alpha_keys()' id='alpha'><a>Alpha</a></td>";
						keyboard += "<td width='160' colspan='3' height='30px' align='center' valign='center' class='key' onclick='change_dvorak_keys()' id='dvorak'><a>Dvorak</a></td>";
						keyboard += "</tr>";
					}
				}
				
				keyboard += "</table>"
				return(keyboard);
			}
			function keyPress(x){
				document.getElementById("search_box").value += x;
			}
			function clear_search(){
				document.getElementById("search_box").value = "";
			}
			function backspace(){
				document.getElementById("search_box").value = document.getElementById("search_box").value.substring(0,document.getElementById("search_box").value.length-1);
			}
			function change_alpha_keys(){
				document.getElementById("row0col0").firstChild.innerHTML = "A";
				document.getElementById("row0col1").firstChild.innerHTML = "B";
				document.getElementById("row0col2").firstChild.innerHTML = "C";
				document.getElementById("row0col3").firstChild.innerHTML = "D";
				document.getElementById("row0col4").firstChild.innerHTML = "E";
				document.getElementById("row0col5").firstChild.innerHTML = "F";
				document.getElementById("row0col6").firstChild.innerHTML = "G";
				document.getElementById("row0col7").firstChild.innerHTML = "H";
				document.getElementById("row0col8").firstChild.innerHTML = "I";
				document.getElementById("row0col9").firstChild.innerHTML = "J";
				document.getElementById("row1col0").firstChild.innerHTML = "K";
				document.getElementById("row1col1").firstChild.innerHTML = "L";
				document.getElementById("row1col2").firstChild.innerHTML = "M";
				document.getElementById("row1col3").firstChild.innerHTML = "N";
				document.getElementById("row1col4").firstChild.innerHTML = "O";
				document.getElementById("row1col5").firstChild.innerHTML = "P";
				document.getElementById("row1col6").firstChild.innerHTML = "Q";
				document.getElementById("row1col7").firstChild.innerHTML = "R";
				document.getElementById("row1col8").firstChild.innerHTML = "S";
				document.getElementById("row1col9").firstChild.innerHTML = "T";
				document.getElementById("row2col0").firstChild.innerHTML = "U";
				document.getElementById("row2col1").firstChild.innerHTML = "V";
				document.getElementById("row2col2").firstChild.innerHTML = "W";
				document.getElementById("row2col3").firstChild.innerHTML = "X";
				document.getElementById("row2col4").firstChild.innerHTML = "Y";
				document.getElementById("row2col5").firstChild.innerHTML = "Z";
				document.getElementById("row2col6").firstChild.innerHTML = "_";
				document.getElementById("row2col7").firstChild.innerHTML = "/";
				document.getElementById("row2col8").firstChild.innerHTML = "(";
				document.getElementById("row2col9").firstChild.innerHTML = ")";
			}
			function change_dvorak_keys(){
				document.getElementById("row0col0").firstChild.innerHTML = "(";
				document.getElementById("row0col1").firstChild.innerHTML = ")";
				document.getElementById("row0col2").firstChild.innerHTML = "_";
				document.getElementById("row0col3").firstChild.innerHTML = "P";
				document.getElementById("row0col4").firstChild.innerHTML = "Y";
				document.getElementById("row0col5").firstChild.innerHTML = "F";
				document.getElementById("row0col6").firstChild.innerHTML = "G";
				document.getElementById("row0col7").firstChild.innerHTML = "C";
				document.getElementById("row0col8").firstChild.innerHTML = "R";
				document.getElementById("row0col9").firstChild.innerHTML = "L";
				document.getElementById("row1col0").firstChild.innerHTML = "A";
				document.getElementById("row1col1").firstChild.innerHTML = "O";
				document.getElementById("row1col2").firstChild.innerHTML = "E";
				document.getElementById("row1col3").firstChild.innerHTML = "U";
				document.getElementById("row1col4").firstChild.innerHTML = "I";
				document.getElementById("row1col5").firstChild.innerHTML = "D";
				document.getElementById("row1col6").firstChild.innerHTML = "H";
				document.getElementById("row1col7").firstChild.innerHTML = "T";
				document.getElementById("row1col8").firstChild.innerHTML = "N";
				document.getElementById("row1col9").firstChild.innerHTML = "S";
				document.getElementById("row2col0").firstChild.innerHTML = "/";
				document.getElementById("row2col1").firstChild.innerHTML = "Q";
				document.getElementById("row2col2").firstChild.innerHTML = "J";
				document.getElementById("row2col3").firstChild.innerHTML = "K";
				document.getElementById("row2col4").firstChild.innerHTML = "X";
				document.getElementById("row2col5").firstChild.innerHTML = "B";
				document.getElementById("row2col6").firstChild.innerHTML = "M";
				document.getElementById("row2col7").firstChild.innerHTML = "W";
				document.getElementById("row2col8").firstChild.innerHTML = "V";
				document.getElementById("row2col9").firstChild.innerHTML = "Z";
			}
			function change_qwerty_keys(){
				document.getElementById("row0col0").firstChild.innerHTML = "Q";
				document.getElementById("row0col1").firstChild.innerHTML = "W";
				document.getElementById("row0col2").firstChild.innerHTML = "E";
				document.getElementById("row0col3").firstChild.innerHTML = "R";
				document.getElementById("row0col4").firstChild.innerHTML = "T";
				document.getElementById("row0col5").firstChild.innerHTML = "Y";
				document.getElementById("row0col6").firstChild.innerHTML = "U";
				document.getElementById("row0col7").firstChild.innerHTML = "I";
				document.getElementById("row0col8").firstChild.innerHTML = "O";
				document.getElementById("row0col9").firstChild.innerHTML = "P";
				document.getElementById("row1col0").firstChild.innerHTML = "A";
				document.getElementById("row1col1").firstChild.innerHTML = "S";
				document.getElementById("row1col2").firstChild.innerHTML = "D";
				document.getElementById("row1col3").firstChild.innerHTML = "F";
				document.getElementById("row1col4").firstChild.innerHTML = "G";
				document.getElementById("row1col5").firstChild.innerHTML = "H";
				document.getElementById("row1col6").firstChild.innerHTML = "J";
				document.getElementById("row1col7").firstChild.innerHTML = "K";
				document.getElementById("row1col8").firstChild.innerHTML = "L";
				document.getElementById("row1col9").firstChild.innerHTML = "_";
				document.getElementById("row2col0").firstChild.innerHTML = "/";
				document.getElementById("row2col1").firstChild.innerHTML = "Z";
				document.getElementById("row2col2").firstChild.innerHTML = "X";
				document.getElementById("row2col3").firstChild.innerHTML = "C";
				document.getElementById("row2col4").firstChild.innerHTML = "V";
				document.getElementById("row2col5").firstChild.innerHTML = "B";
				document.getElementById("row2col6").firstChild.innerHTML = "N";
				document.getElementById("row2col7").firstChild.innerHTML = "M";
				document.getElementById("row2col8").firstChild.innerHTML = "(";
				document.getElementById("row2col9").firstChild.innerHTML = ")";
			}
		</script>
	</head>
	<body>
		<div id="main">
			<script id="key_area">
				document.write(draw_qwerty_keys());
			</script>
		</div>
	</body>
</html>

```

Many thanks for any help :)

---

### Post by korvirlol on 2009-11-19
i didnt look at your code, but this is something you could do.

for the td:```


<td onmousedown = 'changeborder(this)' omouseup='changeborder(this)'></td>
```in your script:
```

function changeborder(obj){
     obj.style.border-style = 'inset';
}
```for mousedown and andmouseup, you will need to write the code to change the border style.

this is just a quick and dirty example of what you could do, there is a lot of missing code here.

hope this helps

---

### Post by Can+~ on 2009-11-19
[HTML]			function draw_qwerty_keys(){
				var keyboard;
				keyboard = "<table border='0' cellspacing='0'>"
				for(i=0;i<3;i++){
				keyboard += "<tr>"
					for(j=0;j<10;j++){
						if(i==0){
							switch(j){
								case 0: x = "q"; break;
								case 1: x = "w"; break;
								case 2: x = "e"; break;
								case 3: x = "r"; break;
								case 4: x = "t"; break;
								case 5: x = "y"; break;
								case 6: x = "u"; break;
								case 7: x = "i"; break;
								case 8: x = "o"; break;
								case 9: x = "p"; break;						
								default: x = "";
							}
						}else if(i==1){
							switch(j){
								case 0: x = "a"; break;
								case 1: x = "s"; break;
								case 2: x = "d"; break;
								case 3: x = "f"; break;
								case 4: x = "g"; break;
								case 5: x = "h"; break;
								case 6: x = "j"; break;
								case 7: x = "k"; break;
								case 8: x = "l"; break;
								case 9: x = "_"; break;
								default: x = "";
							}
						}else if(i==2){
							switch(j){
								case 0: x = "/"; break;
								case 1: x = "z"; break;
								case 2: x = "x"; break;
								case 3: x = "c"; break;
								case 4: x = "v"; break;
								case 5: x = "b"; break;
								case 6: x = "n"; break;
								case 7: x = "m"; break;
								case 8: x = "("; break;
								case 9: x = ")"; break;						
								default: x = "";
							}
						}
						keyboard += "<td width='40px' height='30px' align='center' valign='center' class='key' onclick='keyPress(this.firstChild.innerHTML.toLowerCase());' onmouseover='' id='row"+i+"col"+j+"'><a>"+x.toUpperCase()+"</a></td>";
					}
					if(i==0){
						keyboard += "<td colspan='10' class='input' align='center'><input type='text' size='30' id='search_box'></td>"
						keyboard += "</tr>";
					}else if(i==1){
						keyboard += "<td width='80' colspan='5' height='30px' align='center' valign='center' class='key' onclick='backspace()' id='backspace'><a>BackSpace</a></td>";
						keyboard += "<td colspan='5' align='center' valign='center' class='key' onclick='clear_search()'><a>Clear</a></td>";
						keyboard += "</tr>";
					}else if(i==2){
						keyboard += "<td width='160' colspan='3' height='30px' align='center' valign='center' class='key' onclick='change_qwerty_keys()' id='querty'><a>Qwerty</a></td>";
						keyboard += "<td width='160' colspan='3' height='30px' align='center' valign='center' class='key' onclick='change_alpha_keys()' id='alpha'><a>Alpha</a></td>";
						keyboard += "<td width='160' colspan='3' height='30px' align='center' valign='center' class='key' onclick='change_dvorak_keys()' id='dvorak'><a>Dvorak</a></td>";
						keyboard += "</tr>";
					}
				}
				
				keyboard += "</table>"
				return(keyboard);
			}
			function keyPress(x){
				document.getElementById("search_box").value += x;
			}
			function clear_search(){
				document.getElementById("search_box").value = "";
			}
			function backspace(){
				document.getElementById("search_box").value = document.getElementById("search_box").value.substring(0,document.getElementById("search_box").value.length-1);
			}
			function change_alpha_keys(){
				document.getElementById("row0col0").firstChild.innerHTML = "A";
				document.getElementById("row0col1").firstChild.innerHTML = "B";
				document.getElementById("row0col2").firstChild.innerHTML = "C";
				document.getElementById("row0col3").firstChild.innerHTML = "D";
				document.getElementById("row0col4").firstChild.innerHTML = "E";
				document.getElementById("row0col5").firstChild.innerHTML = "F";
				document.getElementById("row0col6").firstChild.innerHTML = "G";
				document.getElementById("row0col7").firstChild.innerHTML = "H";
				document.getElementById("row0col8").firstChild.innerHTML = "I";
				document.getElementById("row0col9").firstChild.innerHTML = "J";
				document.getElementById("row1col0").firstChild.innerHTML = "K";
				document.getElementById("row1col1").firstChild.innerHTML = "L";
				document.getElementById("row1col2").firstChild.innerHTML = "M";
				document.getElementById("row1col3").firstChild.innerHTML = "N";
				document.getElementById("row1col4").firstChild.innerHTML = "O";
				document.getElementById("row1col5").firstChild.innerHTML = "P";
				document.getElementById("row1col6").firstChild.innerHTML = "Q";
				document.getElementById("row1col7").firstChild.innerHTML = "R";
				document.getElementById("row1col8").firstChild.innerHTML = "S";
				document.getElementById("row1col9").firstChild.innerHTML = "T";
				document.getElementById("row2col0").firstChild.innerHTML = "U";
				document.getElementById("row2col1").firstChild.innerHTML = "V";
				document.getElementById("row2col2").firstChild.innerHTML = "W";
				document.getElementById("row2col3").firstChild.innerHTML = "X";
				document.getElementById("row2col4").firstChild.innerHTML = "Y";
				document.getElementById("row2col5").firstChild.innerHTML = "Z";
				document.getElementById("row2col6").firstChild.innerHTML = "_";
				document.getElementById("row2col7").firstChild.innerHTML = "/";
				document.getElementById("row2col8").firstChild.innerHTML = "(";
				document.getElementById("row2col9").firstChild.innerHTML = ")";
			}
			function change_dvorak_keys(){
				document.getElementById("row0col0").firstChild.innerHTML = "(";
				document.getElementById("row0col1").firstChild.innerHTML = ")";
				document.getElementById("row0col2").firstChild.innerHTML = "_";
				document.getElementById("row0col3").firstChild.innerHTML = "P";
				document.getElementById("row0col4").firstChild.innerHTML = "Y";
				document.getElementById("row0col5").firstChild.innerHTML = "F";
				document.getElementById("row0col6").firstChild.innerHTML = "G";
				document.getElementById("row0col7").firstChild.innerHTML = "C";
				document.getElementById("row0col8").firstChild.innerHTML = "R";
				document.getElementById("row0col9").firstChild.innerHTML = "L";
				document.getElementById("row1col0").firstChild.innerHTML = "A";
				document.getElementById("row1col1").firstChild.innerHTML = "O";
				document.getElementById("row1col2").firstChild.innerHTML = "E";
				document.getElementById("row1col3").firstChild.innerHTML = "U";
				document.getElementById("row1col4").firstChild.innerHTML = "I";
				document.getElementById("row1col5").firstChild.innerHTML = "D";
				document.getElementById("row1col6").firstChild.innerHTML = "H";
				document.getElementById("row1col7").firstChild.innerHTML = "T";
				document.getElementById("row1col8").firstChild.innerHTML = "N";
				document.getElementById("row1col9").firstChild.innerHTML = "S";
				document.getElementById("row2col0").firstChild.innerHTML = "/";
				document.getElementById("row2col1").firstChild.innerHTML = "Q";
				document.getElementById("row2col2").firstChild.innerHTML = "J";
				document.getElementById("row2col3").firstChild.innerHTML = "K";
				document.getElementById("row2col4").firstChild.innerHTML = "X";
				document.getElementById("row2col5").firstChild.innerHTML = "B";
				document.getElementById("row2col6").firstChild.innerHTML = "M";
				document.getElementById("row2col7").firstChild.innerHTML = "W";
				document.getElementById("row2col8").firstChild.innerHTML = "V";
				document.getElementById("row2col9").firstChild.innerHTML = "Z";
			}
			function change_qwerty_keys(){
				document.getElementById("row0col0").firstChild.innerHTML = "Q";
				document.getElementById("row0col1").firstChild.innerHTML = "W";
				document.getElementById("row0col2").firstChild.innerHTML = "E";
				document.getElementById("row0col3").firstChild.innerHTML = "R";
				document.getElementById("row0col4").firstChild.innerHTML = "T";
				document.getElementById("row0col5").firstChild.innerHTML = "Y";
				document.getElementById("row0col6").firstChild.innerHTML = "U";
				document.getElementById("row0col7").firstChild.innerHTML = "I";
				document.getElementById("row0col8").firstChild.innerHTML = "O";
				document.getElementById("row0col9").firstChild.innerHTML = "P";
				document.getElementById("row1col0").firstChild.innerHTML = "A";
				document.getElementById("row1col1").firstChild.innerHTML = "S";
				document.getElementById("row1col2").firstChild.innerHTML = "D";
				document.getElementById("row1col3").firstChild.innerHTML = "F";
				document.getElementById("row1col4").firstChild.innerHTML = "G";
				document.getElementById("row1col5").firstChild.innerHTML = "H";
				document.getElementById("row1col6").firstChild.innerHTML = "J";
				document.getElementById("row1col7").firstChild.innerHTML = "K";
				document.getElementById("row1col8").firstChild.innerHTML = "L";
				document.getElementById("row1col9").firstChild.innerHTML = "_";
				document.getElementById("row2col0").firstChild.innerHTML = "/";
				document.getElementById("row2col1").firstChild.innerHTML = "Z";
				document.getElementById("row2col2").firstChild.innerHTML = "X";
				document.getElementById("row2col3").firstChild.innerHTML = "C";
				document.getElementById("row2col4").firstChild.innerHTML = "V";
				document.getElementById("row2col5").firstChild.innerHTML = "B";
				document.getElementById("row2col6").firstChild.innerHTML = "N";
				document.getElementById("row2col7").firstChild.innerHTML = "M";
				document.getElementById("row2col8").firstChild.innerHTML = "(";
				document.getElementById("row2col9").firstChild.innerHTML = ")";
			}[/HTML]

Uhh...

---

