---
title: "HTML: Keeping Text on One Side and the Text on the Other Side on the Same Line"
date: 2010-11-11
forum: Programming Talk
---

### Post by corrytonapple on 2010-11-11
Hello all, I am a upcoming developer for HTML and CSS and some JavaScript. Today's question for me is:
How do I make text on one side, then text on the other both centering to the each side **and **stay on the same line? I like to play around with building computers, and I need a page where I can have the same part used in a different build without having to save it to two folders at once, which is not possible. I need to have a section one and a section two. My code is this:
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
<title>Name of Build</title>
<style type="text/css">
h1 {text-align:center;}
p.op1 {text-align:left; line-height:90%;}
p.op2 {text-align:right; line-height:90%;}
a:link {color:#000000;}    /* unvisited link */
a:visited {color:#FF6600;} /* visited link */
a:hover {color:#FFCC00;}   /* mouse over link */
a:active {color:#000099;}  /* selected link */
/*p.space {line-height:135%;}*/
</style>
</head>
<body>
<body style="background:#554000">
<h2 style="text-align:center">Name of Build</h2>
<p>
If needed, you can specify any specific piping sizes, color, or how it works.<br />
This is the parts and their prices for this build:<br />
<p class="op1"><b>Total Price for Parts on Option #1: $000;</b> </p><p class="op2"><b>Total Price for Parts on Option #2: $000;</b> </p>
-------------------------------------------------------------------------------------------------------------------------Main Parts-------------------------------------------------------------------------------------------------------------------------<br />
<p class="op1"><a href="">Computer Cases</a>- $00</p>             <p class="op2"><a href="">Computer Cases</a>- $00</p><br />
<p class="op1"><a href="">Power Supplies</a>- $00</p>             <p class="op2"><a href="">Power Supplies</a>- $00</p><br />
<p class="op1"><a href="">Motherboards</a>- $00</p>               <p class="op2"><a href="">Motherboards</a>- $00</p><br />
<p class="op1"><a href="">Processors</a>- $00</p>                 <p class="op2"><a href="">Processors</a>- $00</p><br />
<p class="op1"><a href="">Memory</a>- $00</p>                     <p class="op2"><a href="">Memory</a>- $00</p><br />
<p class="op1"><a href="">SSD</a>- $00</p>                        <p class="op2"><a href="">SSD</a>- $00</p><br />
<p class="op1"><a href="">Hard Drives</a>- $00</p>                <p class="op2"><a href="">Hard Drives</a>- $00</p><br />
<p class="op1"><a href="">Blue-Ray</a>- $00</p>                   <p class="op2"><a href="">Blue-Ray</a>- $00</p><br />
<p class="op1"><a href="">CD/DVD Burners</a>- $00</p>             <p class="op2"><a href="">CD/DVD Burners</a>- $00</p><br />
-------------------------------------------------------------------------------------------------------------------------Accessories------------------------------------------------------------------------------------------------------------------------------<br />
<p class="op1"><a href="">Video Cards</a>- $00</p>                <p class="op2"><a href="">Video Cards</a>- $00</p><br />
<p class="op1"><a href="">Sound Cards</a>- $00</p>                <p class="op2"><a href="">Sound Cards</a>- $00</p><br />
<p class="op1"><a href="">TV-Tuners</a>- $00</p>                  <p class="op2"><a href="">TV-Tuners</a>- $00</p><br />
<p class="op1"><a href="">Keyboards</a>- $00</p>                  <p class="op2"><a href="">Keyboards</a>- $00</p><br />
<p class="op1"><a href="">Mice</a>- $00</p>                       <p class="op2"><a href="">Mice</a>- $00</p><br />
<p class="op1"><a href="">LCD Monitors</a>- $00</p>               <p class="op2"><a href="">LCD Monitors</a>- $00</p><br />
<p class="op1"><a href="">Headphones</a>- $00</p>                 <p class="op2"><a href="">Headphones</a>- $00</p><br />
<p class="op1"><a href="">Speakers</a>- $00</p>                   <p class="op2"><a href="">Speakers</a>- $00</p><br />
<p class="op1"><a href="">Microphone</a>- $00</p>                 <p class="op2"><a href="">Microphone</a>- $00</p><br />
<p class="op1"><a href="">Web Camera</a>- $00</p>                 <p class="op2"><a href="">Web Camera</a>- $00</p><br />
<p class="op1"><a href="">Wireless Card</a>- $00</p>              <p class="op2"><a href="">Wireless Card</a>- $00</p><br />
<p class="op1"><a href="">Bluetooth</a>- $00</p>                  <p class="op2"><a href="">Bluetooth</a>- $00</p><br />
<p class="op1"><a href="">Mouse Pad</a>- $00</p>                  <p class="op2"><a href="">Mouse Pad</a>- $00</p><br />
-------------------------------------------------------------------------------------------------------------------------Liquid/Air Cooling-------------------------------------------------------------------------------------------------------------------------<br />
<p class="op1"><a href="">Pumps</a>- $00</p>                      <p class="op2"><a href="">Pumps</a>- $00</p><br />
<p class="op1"><a href="">CPU Cooling</a>- $00</p>                <p class="op2"><a href="">CPU Cooling</a>- $00</p><br />
<p class="op1"><a href="">Radiators</a>- $00</p>                  <p class="op2"><a href="">Radiators</a>- $00</p><br />
<p class="op1"><a href="">Graphics Cooling</a>- $00</p>           <p class="op2"><a href="">Graphics Cooling</a>- $00</p><br />
<p class="op1"><a href="">Fittings</a>- $00</p>                   <p class="op2"><a href="">Fittings</a>- $00</p><br />
<p class="op1"><a href="">Tubing</a>- $00</p>                     <p class="op2"><a href="">Tubing</a>- $00</p><br />
<p class="op1"><a href="">Liquid</a>- $00</p>                     <p class="op2"><a href="">Liquid</a>- $00</p><br />
<p class="op1"><a href="">Pads for Pumps</a>- $00</p>             <p class="op2"><a href="">Pads for Pumps</a>- $00</p><br />
<a href="http://www.wedontsupportie.com"><img src="http://www.wedontsupportie.com/buttons/88x15/7.gif" border="0" /></a><br />
<!--
To display this page go to where it is located, and right click and click "Rename". Then, change ".txt" to ".html". Double click that file and you can see your page you made.
To edit this page, go to where it is located, and right click and click "Rename". Then, change ".html" to ".txt" and edit. Do what is above this to see the results.
-->
</p>
</body>
</html>

```
It has HTML and CSS. Half of it is links, so please just jump through that.
Thanks!

---

### Post by myrtle1908 on 2010-11-11
If I understand you correctly ...

Use a table, perfect for what you are trying to display.

```
<table width="100%">
  <tr>
    <td>Item A1</td>
    <td style="text-align:right">Item A2</td>
  </tr>
</table>
```

---

### Post by corrytonapple on 2010-11-11
OK Thanks. Let me try. I have never worked with a table before. Will the table show up in the same color as the background color or do I need to do some more work to get that?

---

### Post by myrtle1908 on 2010-11-11
> **corrytonapple said:**
> OK Thanks. Let me try. I have never worked with a table before. Will the table show up in the same color as the background color or do I need to do some more work to get that?

The table will be be "invisible" ie. transparent until you start applying style to its elements (the same way you would any other HTML element).

---

### Post by corrytonapple on 2010-11-12
Am now working on it. As you see in the above code, I have it where it separates the different categories of parts. EX: ---------------------Accessories---------------------------
How can I make it do that more efficiently and have it work with different screen sizes? I need to learn to make sites, not just build for me. :)

---

