---
title: "HTML dropdown update without reload"
date: 2011-02-26
forum: Programming Talk
---

### Post by alket on 2011-02-26
I have dropdown1 and I need it when it changes to change the list of dropdown2 without page reloading ? Thank you in advance.

---

### Post by bashologist on 2011-02-27
By dropdown I think you're talking about the option and select elements. In any case hiding the elements somewhere then replacing them with javascript should do it.
[PHP]<body>
	<select onchange="change(this)">
		<option value="a">aaaaaaaaaaa</option>
		<option value="b">bbbbbbbbbbb</option>
		<option value="c">ccccccccccc</option>
		<option value="d">ddddddddddd</option>
	</select>

	<select id="a">
		<option value="a">aaaaaaaaaaa</option>
		<option value="b">aaaaaaaaaaa</option>
		<option value="c">aaaaaaaaaaa</option>
		<option value="d">aaaaaaaaaaa</option>
	</select>

	<div id="hidden" style="display: none">
		<select id="b">
			<option value="a">bbbbbbbbbbb</option>
			<option value="b">bbbbbbbbbbb</option>
			<option value="c">bbbbbbbbbbb</option>
			<option value="d">bbbbbbbbbbb</option>
		</select>

		<select id="c">
			<option value="a">ccccccccccc</option>
			<option value="b">ccccccccccc</option>
			<option value="c">ccccccccccc</option>
			<option value="d">ccccccccccc</option>
		</select>

		<select id="d">
			<option value="a">ddddddddddd</option>
			<option value="b">ddddddddddd</option>
			<option value="c">ddddddddddd</option>
			<option value="d">ddddddddddd</option>
		</select>
	</div>

	<script>
		function change(element) {
			var oldelement = document.getElementsByTagName("select")[1];
			var newelement = document.getElementById(element.value);
			var hidden = document.getElementById("hidden");
			document.body.replaceChild(newelement, oldelement);
			hidden.appendChild(oldelement);
		}
	</script>
</body>[/PHP]

---

### Post by alket on 2011-02-27
Thank you very much, I think i google it wrong.

---

