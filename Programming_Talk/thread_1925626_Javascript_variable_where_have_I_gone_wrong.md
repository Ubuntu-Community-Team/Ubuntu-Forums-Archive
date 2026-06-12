---
title: "Javascript variable: where have I gone wrong?"
date: 2012-02-14
forum: Programming Talk
---

### Post by nikonian on 2012-02-14
Hi there. Here is some code which is (supposed to) change the paragraph, when the button is clicked. I want to compress my code into variables, but nothing works :(

```

<html>
<head>


<script type="text/javascript" >
var do = function () {document.getElementById("para").innerHTML=("SOME");};

function clicked(){
do();
}
</script>





</head>
<body>
<p id="para">This due to change</p>
<button type="button" id="butt1" onclick="clicked()">CLICK ME</button>
</body>
</html>

```

If you could help me? Thanks :)

---

### Post by myrtle1908 on 2012-02-14
A few observations ...

1. Why don't you just call "do" directly.  In your trivial example there is no need for a "clicked" handler.

2. innerHTML=("SOME"); ... this is invalid syntax.  Should be:- 

```
innerHTML="SOME";
```

3. Debug/Step-through your code with Firebug or Chrome Dev Tools.

---

### Post by nikonian on 2012-02-14
> **myrtle1908 said:**
> A few observations ...

1. Why don't you just call "do" directly.  In your trivial example there is no need for a "clicked" handler.

2. innerHTML=("SOME"); ... this is invalid syntax.  Should be:- 

```
innerHTML="SOME";
```3. Debug/Step-through your code with Firebug or Chrome Dev Tools.


Would you mind showing me the code that you would use, for my example? Having only shown me half the answer, as a newcomer, I am now *twice* as lost. You could as easily have *shown* me the suggested code, instead of explaining it... which is subject to interpretation, and in my case, erroneously so.

Thank you.

---

### Post by nikonian on 2012-02-15
Anyone? Hello? :)

---

### Post by k@e on 2012-02-15
"do" is a reserved keyword in JavaScript, you cannot name variables or functions the same as keywords. Change it to something else like "dosomething".

---

### Post by nikonian on 2012-02-15
> **k@e said:**
> "do" is a reserved keyword in JavaScript, you cannot name variables or functions the same as keywords. Change it to something else like "dosomething".

Thank you so much. You have sorted out my issue.

---

