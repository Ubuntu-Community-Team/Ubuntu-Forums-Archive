---
title: "JavaScript Calculator"
date: 2007-12-07
forum: Programming Talk
---

### Post by MarkCrossley on 2007-12-07
I'm in the process of developing  a JavaScript scientific calculator for use by a visually impaired student that I teach.

I have currently made it so that it has all the functions he requires, and can be used in the same way as a normal calculator with normal operator precidence. However, I've got stuck implementing a power function - JavaScript doesn't recognise ^ as a power sign; instead it uses the power(a,b) function to raise a to the power of b. Ideally I'd like the calculator to be able to check for a ^ sign, and if it finds one to work out which part of the expression is the 'a' part in power(a,b), which part is the 'b' part, and then use that function. However, I've got no idea how to do that!

Any suggestions?

The code for the calculator is here:

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
        "http://www.w3.org/TR/html4/loose.dtd">
  <head>
    <meta http-equiv="Content-Type" content="text/html;charset=utf-8">
    <meta name="author" content="M Crossley">
    <meta name="description" content="A JavaScript scientific calculator designed for use by the visually impaired.">
    <meta name="keywords" content="scientific, calculator, visually, impaired, large">
    <title>Scientific Calculator</title>

    <style type="text/css">
      .btn {
        color: #0f0;
        background-color: #000;
        font-family: helvetica,sans-serif;
        width: 170px;
        height: 80px;
        font-size:50px;
        font-weight:bold;}

      .btn0 {
        color: #0f0;
        background-color: #000;
        font-family: helvetica,sans-serif;
        width: 343px;
        height: 80px;
        font-size:50px;
        font-weight:bold;}
          
      .btnequals {
        color: #f00;
        background-color: #000;
        font-family: helvetica,sans-serif;
        width: 170px;
        height: 162px;
        font-size:50px;
        font-weight:bold;
      }

      .btnAC {
        color: #f00;
        background-color: #000;
        font-family: helvetica,sans-serif;
        width: 170px;
        height: 162px;
        font-size:50px;
        font-weight:bold;
      }

      .btnplus {
        color: #0f0;
        background-color: #000;
        font-family: helvetica,sans-serif;
        width: 170px;
        height: 162px;
        font-size:50px;
        font-weight:bold;
      }

      .display {
        color: #000;
        padding-left: 10px;
        padding-top: 10px;
        background-color: #ccc;
        font-family: helvetica,sans-serif;
        width: 850px;
        height: 80px;
        font-size:50px;
        font-weight:bold;
      }
    </style>

    <script language="JavaScript" type="text/javascript">
      var Pi=Math.PI

      function addChar(input, character) {
        if(input.value == null || input.value == "0")
          input.value = character
        else
          input.value += character
      }

      function Sqrt(x) {
        return Math.sqrt(x)
      }

      function Sin(x) {
        return Math.sin(x/(180/Pi))
      }

      function Cos(x) {
        return Math.cos(x/(180/Pi))
      }

      function Tan(x) {
        return Math.tan(x/(180/Pi))
      }

      function deleteChar(input) {
        input.value = input.value.substring(0, input.value.length - 1)
      }

      function compute(form) {
        form.display.value = eval(form.display.value)
      }
    </script>
  </head>

  <body>
    <form name="sci-calc" action="">
      <table cellspacing="0" cellpadding="1">
        <tr>
          <td colspan="5">
            <input name="display" class="display" value="0" size="28" maxlength="25">
          </td>
        </tr>
        <tr>
          <td>
            <input type="button" class="btn" value="(" onclick="addChar(this.form.display, '(')">
          </td>
          <td>
            <input type="button" class="btn" value=")" onclick="addChar(this.form.display, ')')">
          </td>
          <td>
            <input type="button" class="btn" value="sin" onclick="addChar(this.form.display, 'Sin(')">
          </td>
          <td>
            <input type="button" class="btn" value="cos" onclick="addChar(this.form.display, 'Cos(')">
          </td>
          <td>
            <input type="button" class="btn" value="tan" onclick="addChar(this.form.display, 'Tan(')">
          </td>
        </tr>
        <tr>
          <td>
            <input type="button" class="btn" value="^" onclick="addChar(this.form.display, '^')">
          </td>
          <td>
            <input type="button" class="btn" value="sqrt" onclick="addChar(this.form.display, 'Sqrt(')">
          </td>
          <td>
            <input type="button" class="btn" value="/ " onclick="addChar(this.form.display, '/')">
          </td>
          <td>
            <input type="button" class="btn" value="x" onclick="addChar(this.form.display, '*')">
          </td>
          <td>
            <input type="button" class="btn" value="-" onclick="addChar(this.form.display, '-')">
          </td>
        </tr>
        <tr>
          <td>
            <input type="button" class="btn" value="Pi" onclick="addChar(this.form.display, 'Pi')">
          </td>
          <td>
            <input type="button" class="btn" value="7" onclick="addChar(this.form.display, '7')">
          </td>
          <td>
            <input type="button" class="btn" value="8" onclick="addChar(this.form.display, '8')">
          </td>
          <td>
            <input type="button" class="btn" value="9" onclick="addChar(this.form.display, '9')">
          </td>
          <td rowspan="2">
            <input type="button" class="btnplus" value="+" onclick="addChar(this.form.display, '+')">
          </td>
        </tr>
        <tr>
          <td>
            <input type="button" class="btn" value="del" onclick="deleteChar(this.form.display)">
          </td>
          <td>
            <input type="button" class="btn" value="4" onclick="addChar(this.form.display, '4')">
          </td>
          <td>
            <input type="button" class="btn" value="5" onclick="addChar(this.form.display, '5')">
          </td>
          <td>
            <input type="button" class="btn" value="6" onclick="addChar(this.form.display, '6')">
          </td>
        </tr>
        <tr>
          <td rowspan="2">
            <input type="button" class="btnAC" value="AC" onclick="this.form.display.value = 0 ">
          </td>
          <td>
            <input type="button" class="btn" value="1" onclick="addChar(this.form.display, '1')">
          </td>
          <td>
            <input type="button" class="btn" value="2" onclick="addChar(this.form.display, '2')">
          </td>
          <td>
            <input type="button" class="btn" value="3" onclick="addChar(this.form.display, '3')">
          </td>
          <td rowspan="2">
            <input type="button" class="btnequals" value="=" NAME="enter" onclick="compute(this.form)">
          </td>
        </tr>
        <tr>
          <td colspan="2">
            <input type="button" class="btn0" value="0" onclick="addChar(this.form.display, '0')">
          </td>
          <td>
            <input type="button" class="btn" value="." onclick="addChar(this.form.display, '.')">
          </td>
        </tr>
      </table>
    </form>
  </body>
</html>
```

---

### Post by smartbei on 2007-12-07
Hmmm...I cannot think of a way to do this without forcing you to write a parser for the calculator. The problems lies in the fact that with this implementation it is possible to have something like:
> 
Sqrt(75)^7

Which forces to you to parse the Sqrt before the ^7, which gets you into the whole mess of operator precedence which you are able to avoid entirely through the use of eval.

Maybe there is a simple way to do this and I am just not seeing it... Since you are already using Sqrt - why not do the same thing with Power?

---

### Post by MarkCrossley on 2007-12-07
Ideally this would be as close to using a 'real' calculator as possible - reason being that then he doesn't have to be taught to use it separately from the rest of the class.

Maybe I'd be better of creating a calculator in C, or Python and learn to create a GUI.

Or perhaps someone knows of a large screen scientific calculator already?

---

### Post by smartbei on 2007-12-07
Well, the language doesn't matter so much. With any of the languages you will probably run into problems with the ^ command - in C and Python it is XOR - and will be forced to write a parse tree (correct term?), which you could do in Javascript just like in any other language.

Just for fun, I wrote a scientific calculator a while ago in Python that does support ^ - I'll take a look at it and see if it can easily be adapted to a gui and if more functions (log functions, etc.) could easily be added. Will post back later :).

---

### Post by Billisnice on 2007-12-07
Here is a calander java thing i use at work at

[http://www.google.com/search?q=free+java+script+calendar&ie=UTF-8](http://www.google.com/search?q=free+java+script+calendar&ie=UTF-8)

---

### Post by Billisnice on 2007-12-07
Here is the link

[http://www.bmgamble.com/](http://www.bmgamble.com/)

---

