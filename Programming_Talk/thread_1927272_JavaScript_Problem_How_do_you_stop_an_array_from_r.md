---
title: "JavaScript Problem: How do you stop an array from resizing a div?"
date: 2012-02-17
forum: Programming Talk
---

### Post by vidwarren on 2012-02-17
I've been working on a project that tests juggling notation (siteswaps) for validity. Part of the script needs to take a form input, run it through some 'for loops' and display the output as a split array.

The problem I'm having is that, if the output is so long that the display is wider than it's containing div, it continues out off the right hand edge of the screen.

How do I set the split array to NOT resize the div?

Or, how can I set the split array to start a new line at 500px?

For the full context, the latest stable version is online at [http://www.vidwarren.com/siteswap](http://www.vidwarren.com/siteswap) (type a really long number into the input field to see the problem).

A simplified version of the code is here:

JavaScript:

```
<script type="text/javascript">

window.onload=validateForm;


function validateForm()
{


var inputContent=document.forms["myForm"]["fname"].value

    var splitInput=inputContent.split("");

document.getElementById("ci").innerHTML="<br><br>" + splitInput;


}

</script>

```HTML:

[HTML]<br><br>

<form name="myForm" onkeyup="validateForm()" method="POST" action="#">
<input onchange="validateForm()" type="text" id="firstn" name="fname">
</form>


<div style="width: 500px;">
<span id="ci" width="500px"></span>
</div>[/HTML]Thanks in advance!

---

### Post by r-senior on 2012-02-17
I suspect it's not wrapping because there is no whitespace where the browser will think it's OK to break the line. You could try adding spaces after your commas, or use a CSS style of 'word-wrap: break-word'.

---

### Post by vidwarren on 2012-02-17
Thank you! That looks to have done it.

New JavaScript:

```

<script type="text/javascript">

window.onload=validateForm;


function validateForm()
{


var inputContent=document.forms["myForm"]["fname"].value

    var splitInput=inputContent.split("");

    var joinInput=splitInput.join(" ");

document.getElementById("ci").innerHTML="<br><br>" + joinInput;


}

</script>
```

---

