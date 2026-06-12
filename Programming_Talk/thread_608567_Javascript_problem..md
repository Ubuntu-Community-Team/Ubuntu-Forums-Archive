---
title: "Javascript problem."
date: 2007-11-10
forum: Programming Talk
---

### Post by Kadrus on 2007-11-10
```
<style type="text/css">
span
{
font:12px arial;
background:#CCCCCC;
position:absolute;
width:100;
height:500;
top:300;
clip:rect(0 100 100 0);

}
</style>
<script type="text/javascript">
var interval
startPosition=0
topPosition=100
endPosition=100
speed=50

function scrollit()
{
if (startPosition!=200)
	{
	startPosition=startPosition+1
	topPosition=topPosition-1
	document.getElementById('display').style.clip="rect(" + (startPosition + 1) + " 100 " + (startPosition + endPosition) + " 0)"
	document.getElementById('display').style.top=topPosition
	interval=setTimeout("scrollit()",speed)
	}
else
	{
	startPosition=0
	topPosition=100
	endPosition=100
	interval=setTimeout("scrollit()",speed)
	}
}

function stopinterval()
{
clearTimeout(interval)
}
</script>

<body onload="scrollit()" onunload="stopinterval()">
<span id="display" ><br /><br /><br /><br /><br /><br /><br />
A text here <br />
</span>
```
The problem that I am having here..is that i cannot figure a way how to align the span..
Anyone can help?

---

### Post by Kadrus on 2007-11-10
So..no one has a clue?!

---

### Post by eggdeng on 2007-11-10
Just slip in a left offset value in the first block of code, for example

```
width:100;
height:500;
[COLOR="Red"]left:400;[/COLOR]
top:300;
```

Easy.

---

### Post by supirman on 2007-11-10
What do you mean by align?  Are you trying to move the box (span), or the text within the span?  Give more info.

---

### Post by smartbei on 2007-11-10
Firstly, please cut out the "bummer"/"no one has a clue" posts. This forum is not that busy, so your post was still in the first couple. Most people who browse this forum don't do so constantly, and just check if there are any new posts every **several hours** at the least. Therefore, the fact that nobody responded within less than an hour does not mean that no one has a clue.

Could you explain what you are trying to do with this code? There might be a simpler way to do it and/or we might better understand your question.

---

### Post by Kadrus on 2007-11-10
> **eggdeng said:**
> Just slip in a left offset value in the first block of code, for example

```
width:100;
height:500;
[COLOR="Red"]left:400;[/COLOR]
top:300;
```

Easy.
Doh...how could I have missed that!?](*,)...thanks a lot anyway:)

---

### Post by Kadrus on 2007-11-10
> **supirman said:**
> What do you mean by align?  Are you trying to move the box (span), or the text within the span?  Give more info.
It's the box not the text in it..anyway..eggdeng solved it..thanks anyway..

---

### Post by Kadrus on 2007-11-10
> **smartbei said:**
> Firstly, please cut out the "bummer"/"no one has a clue" posts. This forum is not that busy, so your post was still in the first couple. Most people who browse this forum don't do so constantly, and just check if there are any new posts every **several hours** at the least. Therefore, the fact that nobody responded within less than an hour does not mean that no one has a clue.

Could you explain what you are trying to do with this code? There might be a simpler way to do it and/or we might better understand your question.
I wanted to move the box..it's alignment...anyway it got solved..thanks for the help and for your time..

---

