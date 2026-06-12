---
title: "Javascript: function not being called"
date: 2012-01-14
forum: Programming Talk
---

### Post by debd on 2012-01-14
Am absolutely new to JS and DOM.. so a bit confused.
The problem in the following lines of code is I want it to display a  little greetings msg when the button in the form is clicked using the  innerHTML method in the empty div. But the function isnt being called at  all! and I can't get whats going wrong!
```

<html>
<head>
<style type="text/css">
.test{
    background:rgba(00,00,00,0.7);
    width:50%;
    margin-right:auto;
    margin-left:auto;
    text-align:center;
    }
#press{
    width:30%%;
    background:#00BCDD;
    box-shadow:2px 2px 1px 1px #000000;
    }

</style>
<script type="text/javascript">
//<![CDATA[
sayhi(){
    alert("damn");
    var nam = document.getElimentById("nam");
    var doutput = document.getElimentById("doutput");
    var name = nam.value;
    doutput.innerHTML= "Hi there, ";
    doutput.innerHTML += "<strong>" + name + "<\/strong>!";
}
//]]>
</script>
</head>

<body>
<form class="test" action="">
<fieldset>
    <label>Type in your name</label>
    <input type="text" value="your name here" id="nam"/>
    <p>
    </p>
    <button type="button" id="press" onclick="sayhi()">Click me!</button>
</fieldset>
</form>    
<div id="doutput" style="color:black">

</div>    
</body>

</html>

```

---

### Post by Dimarchi on 2012-01-15
Well, apparently solved already but no reason mentioned how, so...here's for the future. :)

Typos are the reason. Without testing your code  - and from memory - I would have written the function as follows:
```

<script type="text/javascript">
//<![CDATA[
function sayhi()
{
     alert("damn");
     var nam = document.getElementById("nam");
     var doutput = document.getElementById("doutput");
     var name = nam.value;
     doutput.innerHTML= "Hi there, ";
     doutput.innerHTML += "<strong>" + name + "<\/strong>!";
}
//]]>
</script>

```There you go. You are on the right track so don't let things like that confuse you. :)

---

### Post by shashanksingh on 2012-01-15
Also, my little experience tells me the firebug extension for firefox and the default console in chrome are helpful many times to point out the type or any other error.

---

