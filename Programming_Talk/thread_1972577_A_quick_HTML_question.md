---
title: "A quick HTML question"
date: 2012-05-03
forum: Programming Talk
---

### Post by codingman on 2012-05-03
I was doing some stuff in html and then I thought "How can I set an input to that if the radio button is pressed, it will show a 'next page' button"

So, can anyone answer my quandary?

Thanks,
Codingman

---

### Post by PaulM1985 on 2012-05-03
You will need to use something like JavaScript for this.

I found this page which describes what you are after, but I haven't tested the code so I can't say how accurate it is:
[http://www.universalwebservices.net/web-programming-resources/javascript/show-hide-elements-with-javascript](http://www.universalwebservices.net/web-programming-resources/javascript/show-hide-elements-with-javascript)

Paul

---

### Post by |{urse on 2012-05-03
```
<html>
 <head>
  <script type="text/javascript">
    window.onload = function() {

        var ex1 = document.getElementById('example1');
        var ex2 = document.getElementById('example2');
        var ex3 = document.getElementById('example3');

        ex1.onclick = handler;
        ex2.onclick = handler;
        ex3.onclick = confirmation;

    }

        function confirmation() {
	var answer = confirm("Continue to next page?")
	if (answer){
		alert("Bye bye!")
		window.location = "http://www.google.com/";
	}
	else{
		alert("Thanks for sticking around!")
	}
   }

    function handler() {
        alert('clicked');
    }
  </script>
 </head>
 <body>
  <input type="radio" name="example1" id="example1" value="Example 1" />
  <label for="example1">Example 1</label>
  <input type="radio" name="example2" id="example2" value="Example 2" />
  <label for="example1">Example 2</label>
  <input type="radio" name="example3" id="example3" value="Example 3" />
  <label for="example3">Example 3</label>
 </body>
</html>


```

As you can see you can assign whatever action you wish to the confirm dialog in example 3. So far as making a non-popup button appear I guess you could create a css rule hidden{ display: none; } and set whatever image/button/div containing image etc to display whatever is in the tags containing the hidden attribute using onclick.

---

### Post by |{urse on 2012-05-05
So, just curious, what did you come up with?

---

### Post by AmbientOcclusion on 2012-05-05
Are you using html 5?

---

### Post by |{urse on 2012-05-10
If you mean me, no, thats html4, idk what codingman was wanting to use.

---

