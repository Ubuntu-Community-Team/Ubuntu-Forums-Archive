---
title: "AJAX Typing Test"
date: 2012-10-19
forum: Programming Talk
---

### Post by TheodoreP on 2012-10-19
Hi everyone,

I have been having a little debugging my current lesson for my online course covering AJAX. The point of the application is to display 3 phrases when one clicks the Begin Test button which works. What I am having a little trouble getting to work is the grade quiz function. It is supposed to take the users input and if it all matches up alright it should increase a numberCorrect variable by one which it doesn't do. Below I will post my current code configuration:

<html>
<head>
<title>Ajax Typing Challenge</title>
</head>
<script language="javascript" type="text/javascript">
<!-- Start hiding JavaScript statements
var Request1 = false;
var Request2 = false;
var Request3 = false;

var sentence1 = "";
var sentence2 = "";
var sentence3 = "";
var numberCorrect;

if(window.XMLHttpRequest)
{
    Request1 = new XMLHttpRequest();
    Request2 = new XMLHttpRequest();
    Request3 = new XMLHttpRequest();
} else if(window.ActiveXObject)
{
    Request1 = new ActiveXObject("Microsoft.XMLHTTP");
    Request2 = new ActiveXObject("Mictosoft.XMLHTTP");
    Request3 = new ActiveXObject("Microsoft.XMLHTTP");
}
function startQuiz()
{
    document.getElementById("inputTXT1").value="";
    document.getElementById("inputTXT2").value="";
    document.getElementById("inputTXT3").value="";
    document.getElementById("trgtP").innerHTML="";
    if(Request1)
    {
        var RequestObj1 = document.getElementById("trgtDiv1");
        Request1.open("Get", "ChallengeTXT/challenge1.txt");
        Request1.onreadystatechange = function() {
            if (Request1.readyState == 4 && Request1.status == 200)
            {
                RequestObj1.innerHTML = Request1.responseText;
                sentence1 = Request1.responseText;
                window.alert(" " + sentence1 + " ");
            }
        }
        Request1.send(null);
    }
    if(Request2)
    {
        var RequestObj2 = document.getElementById("trgtDiv2");
        Request2.open("GET", "ChallengeTXT/challenge2.txt");
        Request2.onreadystatechange = function() {
            if(Request2.readyState == 4 && Request2.status == 200)
            {
                RequestObj2.innerHTML = Request2.responseText;
                sentence2 = Request2.responseText;
                window.alert(" " + sentence2 + " ");
            }
        }
        Request2.send(null);
    }
    if(Request3)
    {
        var RequestObj3 = document.getElementById("trgtDiv3");
        Request3.open("GET", "ChallengeTXT/challenge3.txt");
        Request3.onreadystatechange = function() {
            if(Request3.readyState == 4 && Request3.status == 200)
            {
                RequestObj3.innerHTML = Request3.responseText;
                sentence3 = Request3.responseText;
                window.alert(" " + sentence3 + " ");
            }
        }
        Request3.send(null);
    }
}
function GradeQuiz() 
{
    numberCorrect = 0;
    var result1 = document.getElementById("inputTXT1").value;
window.alert(" " + result1 + " ");
    var result2 = document.getElementById("inputTXT2").value;
window.alert(" " + result2 + " ");
    var result3 = document.getElementById("inputTXT3").value;
window.alert(" " + result3 + " ");
    var score = document.getElementById("trgtP");

    if(sentence1 == result1)
    {
         numberCorrect++
    }
    if(sentence2 == result2)
    {
         numberCorrect++
    }
    if(sentence3 == result3)
    {
         numberCorrect++
    }
    window.alert(" " + numberCorrect + " ");
    score.innerHTML = "To pass you must type at least 2 " +
        "out of 3 sentences correctly. You got " + numberCorrect +
        " correct.";
}
// End hiding JavaScript statements -->
</script>
<body>
<h1 style = "color:blue">Ajax Typing Challenge</h1>
<form>
<p>Click "Begin Test" when you are ready to begin, and then
type the sentences that are diplayed in the text fields
displayed below each sentence. When finished, click "Grade
Test."</p>
<input type="button" value="Begin Test" id="btnControl1"
  onclick=startQuiz()>
<input type="button" value="Grade Test" id="btnControl2"
  onclick=GradeQuiz()>
<p><div id="trgtDiv1"> </div></p>
<input type="textfield" size="100" id="inputTXT1"> 
<p><div id="trgtDiv2"> </div></p>
<input type="textfield" size="100" id="inputTXT2">
<p><div id="trgtDiv3"> </div></p> 
<input type="textfield" size="100" id="inputTXT3">
</form>
<p style="color:red; font-weight:Bold" id="trgtP"> </p>
</body>
</html>

---

### Post by TheodoreP on 2012-10-20
I think the problem resides in the fact that the if(sentenceN == resultN) statements are not being proven right and it's skipping over them. However according to my window.alert messages everthing should be working superbly. Please if anyone can give me any kind of help fixing this bug I would greatly appreciate it. I feel I may start to loss some sleep over this problem.

FYI

I have added semi-colons to the end of the numberCorrect++ statements and it still doesn't work.

**PLEASE HELP!**

---

### Post by spjackson on 2012-10-20
I haven't done any Ajax programming, but I wonder whether the sentenceN ends with a line-feed but resultN doesn't. Try displaying the lengths of each string.

---

### Post by TheodoreP on 2012-10-20
> **spjackson said:**
> I haven't done any Ajax programming, but I wonder whether the sentenceN ends with a line-feed but resultN doesn't. Try displaying the lengths of each string.

Just to make sure I understand you correctly, a line feed is when the applications gives you an automatic new line or something like that, without your knowledge. If that is correct then yes I believe that it is adding a new line to the sentenceN variables.

---

### Post by Dimarchi on 2012-10-21
It does indeed add a new linefeed, thereby invalidating the comparison. For example, sentenceN in the file is "123" and the user inputs "123". The responseText you get, however, is "123\n".  123\n is not 123.

I didn't get your code to work without modifications. If it works for you, that is fine. If it does not, I suggest you take a look at this page:

[https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)

You will notice some differences in the manner you have coded your ajax call and how it is presented on that page.

---

