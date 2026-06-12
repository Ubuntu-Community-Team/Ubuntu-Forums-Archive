---
title: "Javascript Replace Problem"
date: 2013-02-22
forum: Programming Talk
---

### Post by _user on 2013-02-22
```
<script type="text/javascript">
  function replace1() {
    document.getElementById('number').innerHTML = "<b>2:</b>";
    document.getElementById('question').innerHTML = "<b>ABC </b>";
    document.getElementById('answer1').innerHTML = "<input type=\"radio\" name=\"radio\" id=\"radio\" value=\"radio\" /> Yes";
    document.getElementById('answer2').innerHTML = "<input type=\"radio\" name=\"radio\" id=\"radio\" value=\"radio\" /> No";
    document.getElementById('nextbutton').innerHTML = "<a href=\"javascript:replace2()\">Next Question &gt;</a>";
  }

  function replace2() {
    document.getElementById('number').innerHTML = "<b>3. </b>";
    document.getElementById('question').innerHTML = "<b>DEF </b>";
    document.getElementById('answer1').innerHTML = "<input type=\"radio\" name=\"radio\" id=\"radio\" value=\"radio\" /> Yes";
    document.getElementById('answer2').innerHTML = "<input type=\"radio\" name=\"radio\" id=\"radio\" value=\"radio\" /> No";
    document.getElementById('nextbutton').innerHTML = "<a href=\"javascript:replace3()\">Next Question &gt;</a>";
  }
</script>

<div class="questionnaire">
<span id="number"><strong>1.</strong></span>
<span id="question"><strong>123</strong></span>

<p><span id="answer1"><input name="radio" id="radio" value="radio" type="radio" />Yes</span><br />
   <span id="answer2"><input name="radio" id="radio" value="radio" type="radio" />No</span></p>
   
<div id="nextbutton"><a href="javascript:replace1()">Next</a></div></div>
```

Problem: I'm trying to use javascript replace to change the question on a webpage when the user hits 'Next'.  At the moment when the user hits 'Next' nothing happens.  Gedit syntax highlighting also suggests there is a problem with my javascript but I can't see where the issue is.  I'm aware "javascript:replace3()" won't actually do anything - I've just simplified the code whilst troubleshooting it.

---

### Post by greenpeace on 2013-02-22
Hi!

Firstly, (and sorry to not tackle your problem directly), I would consider rewriting your functions to make it easy to read, and extend... something like the following:

```
function updateQuestions(question_id) {
    
    //  just add new lines to this dictionary for each new question you 
    //  want to add, ending each line except for the last with a comma,

    var questions = {
      1: {"number": 2, "question": "ABC"},
      2: {"number": 3, "question": "DEF"}
    };

    var current_question = questions[question_id];

    document.getElementById("number").innerHTML = "<b>"+current_question["number"]+"</b>";
    document.getElementById('question').innerHTML = "<b>"+current_question["question"]+"</b>";

    //rethink these two lines, as we're not actually changing anything here!
[B]    document.getElementById('answer1').innerHTML = "<input type=\"radio\" name=\"radio\" id=\"radio\" value=\"radio\" /> Yes";
    document.getElementById('answer2').innerHTML = "<input type=\"radio\" name=\"radio\" id=\"radio\" value=\"radio\" /> No";[/B]
    
    document.getElementById('nextbutton').innerHTML = "<a href=\"javascript:updateQuestions("+current_question["number"]+")\">Next Question &gt;</a>";

  }
```

Note the use of a dictionary to store the various details of the questions in a structured way.  The function then simply looks up the values from this dictionary to populate the fields in the HTML.

I've highlighted two lines that need to be rethought, as we're not actually changing anything there.

Also, think about how the answers from the user are going to be returned to you, at the moment they don't go anywhere.

Hope that helps, the function is working here in the HTML, just update here as well to reference the new function:

[HTML]  <div id="nextbutton">
    <a href="javascript:updateQuestions(1)">Next</a>
  </div>[/HTML]


Cheers,
GP

---

### Post by _user on 2013-02-23
That worked- thanks!  Appreciate the tips too.

---

### Post by greenpeace on 2013-02-23
cool, no worries! :)  Don't forget to mark the thread as solved (I think it's in the thread tools options.)

Cheers!
gp

---

