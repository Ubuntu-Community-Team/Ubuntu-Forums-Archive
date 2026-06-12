---
title: "PHP Help"
date: 2007-04-20
forum: Programming Talk
---

### Post by dyous87 on 2007-04-20
Ok everyone I'm pretty much new to php programming but my university has asked me to create and online test type thing for incomming freshmen to take next year. I have two sides to this project, an admin side and a student side. The admin side allows you to add chapters, questions and answers to a mysql database. Then on the student side, the student is to login and connect to the database. I have accomplished this up until now. 

Now what I need to do is make it so that the student side can import the question data from the database and display it. The database is set up so that each question has 4 answers one of which is right. The student has 3 chances to get it right, on the last try he will just be transferred to the next page which is the next question. 

I have been trying to figure out how to do this and I have searched around the web but I have been unable to. Is there anyone here he would be kind enough to explain this to me or maybe walk me through it. I would really appreciate it. Thank you

David

---

### Post by finer recliner on 2007-04-21
> **dyous87 said:**
> 
Now what I need to do is make it so that the student side can import the question data from the database and display it. The database is set up so that each question has 4 answers one of which is right. The student has 3 chances to get it right, on the last try he will just be transferred to the next page which is the next question. 
David

instantiate a counter variable (number of guesses), and use case statements depending on what the value of the counter is.

---

### Post by dyous87 on 2007-04-21
The thing is in my mysql database I have the quiz question, answers and number of chances allowed. I also have set what page it should go to if the question is wrong or right. I need to know how to get this information to appear in a website using php.

It's supposed to be dynamic so that the quiz is working right off the database and i don't need to write and html or php page for every question. I read something about outer join in order to get this done but I'm not exactly sure what that is.

---

### Post by Mirrorball on 2007-04-21
The first step is to setup Apache, mod_php and the MySQL module for php. Then create a text document student.php and save it to the /var/www/ folder, because it is where Apache serves files from. Then write PHP code in student.php to connect to the MySQL database, fetch the quiz question and answers. Here is something to get you started:
```

<?php
$link = mysql_connect('localhost', 'root', ''); // creates a database connection
mysql_select_db('quiz', $link); // select a database
$result = mysql_query('SELECT * FROM question', $link); // fetch the questions
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>Quiz</title>
</head>
<body>
<h1>Quiz</h1>
<?php while ($row = mysql_fetch_array($result)) { /* iterates through the query results */ ?>
<p><?php echo $row['question'] /* prints a question */ ?></p>
<?php } ?>
</body>
</html>

```This is just to get you started. Everything you need to know is here: [http://www.php.net/manual/en/](http://www.php.net/manual/en/)
Excellent manual. Learn what a session is, it's going to be useful. ;)

---

### Post by Mirrorball on 2007-04-21
I wrote the PHP guide for the sticky thread on how to start programming, here it is:
[http://ubuntuforums.org/showpost.php?p=2327843&postcount=25](http://ubuntuforums.org/showpost.php?p=2327843&postcount=25)

---

### Post by dyous87 on 2007-04-21
> **Mirrorball said:**
> The first step is to setup Apache, mod_php and the MySQL module for php. Then create a text document student.php and save it to the /var/www/ folder, because it is where Apache serves files from. Then write PHP code in student.php to connect to the MySQL database, fetch the quiz question and answers. Here is something to get you started:
This is just to get you started. Everything you need to know is here: [http://www.php.net/manual/en/](http://www.php.net/manual/en/)
Excellent manual. Learn what a session is, it's going to be useful. ;)

Thank you very much for all your help. I followed your example and I put this code in:

```
<?php
$link = mysql_connect('localhost', 'root', 'pw'); // creates a database connection
mysql_select_db('fordham', $link); // select a database
$result = mysql_query('SELECT * FROM questions', $link); // fetch the questions
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>Quiz</title>
</head>
<body>
<h1>Quiz</h1>
<?php while ($row = mysql_fetch_array($result)) { /* iterates through the query results */ ?>
<p><?php echo $row['question'] /* prints a question */ ?></p>
<?php } ?>
</body>
</html>
```

and it displays all my question data on a single web page. I need to be able to somehow have each question on a different page followed by the answer choices. when  you select the right answers is should go to the next page which the next question would be on. Any idea how this can be done?

---

### Post by Mirrorball on 2007-04-21
GET/POST variables. I think you should read this tutorial:
[http://www.php.net/manual/en/tutorial.php](http://www.php.net/manual/en/tutorial.php)
With a GET variable, the url to your page will be [http://localhost/student.php?id=1](http://localhost/student.php?id=1), id is the question's ID in the database. Then you know what question to show (obs: always validate the id, that it's an integer to a valid question, for security). To display the answer choices:
```

<?php $result = mysql_query('SELECT * FROM answers WHERE question_id = ' . $question_id, $link); ?>
<form method="post" action="student.php?id=<?php echo $id_to_the_next_question ?>">
<p>Question: <?php echo $question ?></p>
<select name="answer">
<?php while ($answer = mysql_fetch_array($answers)) { ?>
    <option value="<?php echo $answer['id'] ?>"><?php echo $answer['answer'] ?></option>
<?php } ?>
</select>
<p><input type="submit" value="Submit" /></p>
</form>

```
To track students and record their answers, use sessions:
[http://www.php.net/manual/en/ref.session.php](http://www.php.net/manual/en/ref.session.php) (keep this page open all the time)
[http://www.tizag.com/phpT/phpsessions.php](http://www.tizag.com/phpT/phpsessions.php) (short tutorial)
[http://www.oreilly.com/catalog/webdbapps/chapter/ch08.html](http://www.oreilly.com/catalog/webdbapps/chapter/ch08.html) (longer explanation)

---

### Post by milton1 on 2007-04-21
Not to seem overly simple, but would Moodle do all of this for you? I have tinkered with it a bit, and it seems like it has all the capabilities that you are seeking. It also happens to be free:

[http://moodle.org/](http://moodle.org/)

---

### Post by barmazal on 2007-04-21
> **milton1 said:**
> Not to seem overly simple, but would Moodle do all of this for you? I have tinkered with it a bit, and it seems like it has all the capabilities that you are seeking. It also happens to be free:

[http://moodle.org/](http://moodle.org/)

Many or those free cmses are very hard to configure sometimes it's easier to write code alone when it comes to some simple questioning.

---

### Post by dyous87 on 2007-04-21
ok bare with me i definitely butchered this code, thanks for all the help though, i have been reading through tutorials and i am trying to get the hang of this. anyway here is what i have:

```
<?php
$link = mysql_connect('localhost', 'root', 'pw'); 
mysql_select_db('fordham', $link);

$result = mysql_query('SELECT * FROM pages WHERE page_number = 1' . $page_number, $link); ?>

mysql_query('SELECT * FROM pages WHERE page_number=1', $link);
if $page_type_id=1 {
mysql_query('SELECT * FROM pages_data', $link);
echo $row pages_data;
}
if $page_type_id=2 {
mysql_query('SELECT * FROM questions', $link);

<form method="post" action="begin.php?id=<?php echo $page_type_id ?>">
<p>Question: <?php echo $question ?></p>
<select name="answer">
<?php while ($answer = mysql_fetch_array($answers)) { ?>
    <option value="<?php echo $answer['id'] ?>"><?php echo $answer['answer'] ?></option>
<?php } ?>

<?php 
</select>
<p><input type="submit" value="Submit" /></p>
</form>
```I know it isn't complete yet and when i run it on my server nothing happens so there's stuff wrong it it. basically what i want to happen is i want to select from my pages table where the page_number=1. that's to begin. then if page_type_id = 1 i want it to select from pages_data. if page_type_id=2 i want it to select from questions.

then i want it to print the question for the page and i want it to list the answers from question_response table in radio boxes. i want it to then check against the database for the correct answer. 1=wrong 2=right. if it's right i want it to go to the next question if it's wrong i want them to have another chance. three chances in all. i'm not sure if this is all supposed to be simpler then i'm making it out to be but i'm very new with php and just trying to figure this stuff out. i really appreciate all your help.

also thanks for the moodle link but this is something that i must code on my own :)

---

### Post by Mirrorball on 2007-04-21
It should be:
```
if ($page_type_id==1) {
```
Notice the parentheses and == for comparison instead of = (for assignment).

More code to help you:

```

<?php
session_start(); // Start a session to "remember" what the student has already done.
$link = mysql_connect('localhost', 'root', '');
mysql_select_db('quiz', $link);
if (_SERVER['REQUEST_METHOD'] == 'POST') { // Check if the student has submitted a form by POST.
  $question = $_POST['question']; // The question, it's here because of the hidden input field in the form below.
  $answer = $_POST['answer']; // The answer
  $result = mysql_query('A query to fetch the right answer to the question', $link);
  // etc
  if ($answer == $right_answer) {
    // Calculate the next question
    $_SESSION['chances'] = 1; // This is the first chance for the question
  }
  else {
    if ($_SESSION['chances'] == 3) {
      // I don't know what you want to do when the student has had his three chances.
    }
    else {
      $_SESSION['chances'] += 1;
    }
  }
}
else {
  $question = 1; // First question
}

// Fetch the question and alternatives...
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>Quiz</title>
</head>
<body>
<h1>Quiz</h1>
<form method="POST" action="student.php">
<p><?php echo $question ?></p>
<p>
<?php while ($row = mysql_fetch_array($answers)) { ?>
<label><input type="radio" name="answer" value="<?php echo $answer['id'] ?>" /> <?php echo $answer['answer'] ?></label><br />
<?php } ?>
<input type="hidden" name="question" value="<?php echo $question_id; ?>" /> <!-- Important so that you know what question the student is answering when he submits the form. -->
</p>
<p><input type="submit" value="Submit" /></p>
</form>
</body>
</html>

```

---

### Post by dyous87 on 2007-04-21
when three chances are up i'd want it to just register in the db as incorrect and go to the next question. i'm trying to see if i could get that code to work now, i will let you know. thank you.

also i'm a little confused about that code you posted. should i have that after the code I already had or should that be all new from scratch. also in this line: >   $result = mysql_query('A query to fetch the right answer to the question', $link); should it be: > $result = mysql_query(SELECT * FROM question_data WHERE question_data_correct = 2 ', $link);?

---

### Post by pmasiar on 2007-04-22
> **dyous87 said:**
> my university has asked me to create and online test  

I bet there is free/oss implementation of this.

Just in 5 minutes, searching for "student assessment" in freshmeat, I found [http://freshmeat.net/projects/loncapa/:](http://freshmeat.net/projects/loncapa/:) with online and bubblesheet exams

Email archive suggest it is still alive: users supported, new versions announced.

Just FYI, you are free to create new one if you wish so.

---

### Post by dyous87 on 2007-04-22
> **pmasiar said:**
> I bet there is free/oss implementation of this.

Just in 5 minutes, searching for "student assessment" in freshmeat, I found [http://freshmeat.net/projects/loncapa/:](http://freshmeat.net/projects/loncapa/:) with online and bubblesheet exams

Email archive suggest it is still alive: users supported, new versions announced.

Just FYI, you are free to create new one if you wish so.

thanks, I need to create this on my own though, it is kind of like an intern where i am supposed to learn from and get experience.

---

### Post by Mirrorball on 2007-04-22
> **dyous87 said:**
> should i have that after the code I already had or should that be all new from scratch.
All new from scratch. But I didn't post that code for you to cut and paste. You have to understand what you are doing if you want it to work. Did you read the tutorials? Do you know what POST variables are? Sessions? PHP is an easy language, but you have to understand web programming.
> **dyous87 said:**
> also in this line:  should it be: ?
Of course, I didn't want to write the query.

---

### Post by dyous87 on 2007-04-22
yes i read the tutorials, i understand them somewhat. i'm going to try to mess with that code some more, i really do appreciate your help btw.

---

### Post by Mirrorball on 2007-04-22
You are welcome. :D

---

### Post by dyous87 on 2007-04-22
in this section over here:

```

  $question = $_POST['question']; // The question, it's here because of the hidden input field in the form below.
  $answer = $_POST['answer']; // The answer

```

can i make it pull the question and answer right from mysql by declaring their tables right in between the [ ]?

sorry if these questions are obvious i'm just very new to php once again. i've never used anything but html in the past. :)

---

### Post by Mirrorball on 2007-04-22
No, $_POST is associative array that contains data from a form the user has submitted by POST. For instance, $_POST['answer'] is the answer the user has selected. 'answer' is the name of the input field (the radio fields).

Suppose that you have this form in a page:
```

<form action="submit.php" method="POST">
<p>Your Linux distribution: <input type="text" name="distro" /></p>
<p><input type="submit" value="Submit /></p>
</form>

```
It has a form, which sends data to a script called submit.php by POST. There is a field named "distro", where the user will write the name of his Linux distribution. To process this form in submit.php, we could do:
```

<?php
echo 'Your Linux distribution is ' . $_POST['distro'];

```
If the user wrote "Ubuntu" in that field, the output will be "Your Linux distribution is Ubuntu."

---

### Post by dyous87 on 2007-04-22
oh ok i see that. but then i don't understand why i would wan't to use post for the question. wouldn't i just want the question to show up from the database.

---

### Post by Mirrorball on 2007-04-22
Yes, but you also want to know what question the user has just answered when he submits the form and the script is checking the answer. Everytime the page is loaded, you don't know what the student has already done.

---

### Post by dyous87 on 2007-04-22
yes all right that does make sense. i think i am closer to getting it to work. this is what i have now:

```
<?php
session_start();
$link = mysql_connect('localhost', 'root', 'pw');
mysql_select_db('fordham', $link);

$result = mysql_query('SELECT * FROM pages WHERE page_number = 1', $link);
  if (page_type_id == 1) {
    $result = mysql_query('SELECT * FROM pages_data WHERE page_id = page_id FROM pages', $link);
    while ($row = mysql_fetch_array($result));
    echo $row['page_data'];
        
}
else {
  if (page_type_id == 2) {
    $result = mysql_query('SELECT * FROM questions WHERE page_id = page_id FROM pages and SELECT * FROM question_data_answer WHERE question_id = question_id FROM questions', $link);
    while ($row = mysql_fetch_array($result));
    (_SERVER['REQUEST_METHOD'] == 'POST')
    $question = $_POST['question'];
    $answer = $_POST['question_data_answer'];
    $result = mysql_query('SELECT * FROM question_data WHERE question_data_correct = 2', $link);
  }
  if ($answer == $result) {
        $_SESSION['chances'] = 1;
    mysql_query("INSERT into questions_response (question_id, question_response_answer, user_id')");
    header("location:begin_test.php?next_page = page_next");
  }
  else {
    if ($_SESSION['chances'] == 3) {
    mysql_query("INSERT into questions_response (question_id, question_response_answer, user_id')");
    header("location:begin_test.php?next_page = page_next");
    }
    else {
      $_SESSION['chances'] += 1;
    }
  }
}
else {
  $question = 1; 
}

?>
<html>
<head>
<title>Student Test</title>
</head>
<body>
<h1>Integrity Test</h1>
<form method="POST" action="begin.php">
<p><?php echo $question ?></p>
<p>
<?php while ($row = mysql_fetch_array($answers)) { ?>
<label><input type="radio" name="answer" value="<?php echo $answer['question_data_answer'] ?>" /> <?php echo $answer['question_data_answer'] ?></label><br />
<?php } ?>
<input type="hidden" name="question" value="<?php echo $question_id; ?>" />
</p>
<p><input type="submit" value="Submit" /></p>
</form>
</body>
</html>
```It still does nothing but show a blank page when loaded however. there has to be something wrong. i am not sure what it is though. :confused:

---

### Post by dyous87 on 2007-04-22
ok i've been playing around with this code all morning now. I think i'm getting closer to figuring it out. Now when i load the php page i get these errors:

```
**Notice**:  Use of undefined constant page_type_id - assumed 'page_type_id' in **/var/www/html/fordham/student/begin_code.php** on line **7**

**Notice**:  Use of undefined constant page_type_id - assumed 'page_type_id' in **/var/www/html/fordham/student/begin_code.php** on line **14**

**Notice**:  Undefined variable: answer in **/var/www/html/fordham/student/begin_code.php** on line **22**

**Notice**:  Undefined index:  chances in **/var/www/html/fordham/student/begin_code.php** on line **28**

**Notice**:  Undefined index:  chances in **/var/www/html/fordham/student/begin_code.php** on line **33**
    

**Notice**:  Undefined variable: question in **/var/www/html/fordham/student/begin_code.php** on line **47**

  
**Notice**:  Undefined variable: answers in **/var/www/html/fordham/student/begin_code.php** on line **49**

**Warning**:  mysql_fetch_array(): supplied argument is not a valid MySQL result resource in **/var/www/html/fordham/student/begin_code.php** on line **49**
```

Apparently I'm supposed to be defining something somehow. This is the code I have now:

```
<?php
session_start();
$link = mysql_connect('localhost', 'root', 'usa4552');
mysql_select_db('fordham', $link);

$result = mysql_query('SELECT * FROM pages WHERE page_number = 1', $link);
  if (page_type_id == 1) {
    $result = mysql_query('SELECT * FROM pages_data WHERE page_id = page_id FROM pages', $link);
    while ($row = mysql_fetch_array($result));
    echo $row['page_data'];
        
}
else {
  if (page_type_id == 2) {
    $result = mysql_query('SELECT * FROM questions WHERE page_id = page_id FROM pages and SELECT * FROM question_data WHERE question_id = question_id FROM questions', $link);
    while ($row = mysql_fetch_array($result));
    ($_SERVER['REQUEST_METHOD'] == 'POST');
    $question = $_POST['question'];
    $answer = $_POST['question_data_answer'];
    $result = mysql_query('SELECT * FROM question_data WHERE question_data_correct = 2', $link);
  }
  if ($answer == $result) {
        $_SESSION['chances'] = 1;
    mysql_query("INSERT into questions_response (question_id, question_response_answer, user_id')");
    header("location:begin.php?next_page = page_next");
  }
  else {
    if ($_SESSION['chances'] == 3) {
    mysql_query("INSERT into questions_response (question_id, question_response_answer, user_id')");
    header("location:begin.php?next_page = page_next");
    }
    else {
      $_SESSION['chances'] += 1;
    }
  }
}


?>
<html>
<head>
<title>Student Test</title>
</head>
<body>
<h1>Integrity Test</h1>
<form method="POST" action="begin.php">
<p><?php echo $question ?></p>
<p>
<?php while ($row = mysql_fetch_array($answers)) { ?>
<label><input type="radio" name="answer" value="<?php echo $answer['question_data_answer'] ?>" /> <?php echo $answer['question_data_answer'] ?></label><br />
<?php } ?>
<input type="hidden" name="question" value="<?php echo $question_id; ?>" />
</p>
<p><input type="submit" value="Submit" /></p>
</form>
</body>
</html>
```

I'll be playing with it some more but hopefully someone can point me in the right direction.

Thanks!

---

### Post by Mirrorball on 2007-04-22
Only two of your SQL queries are valid. I don't know what you are trying to select/insert, but have a look at the MySQL manual.
[http://dev.mysql.com/doc/refman/5.0/en/data-manipulation.html](http://dev.mysql.com/doc/refman/5.0/en/data-manipulation.html)

---

### Post by dyous87 on 2007-04-22
ok i am looking at that right now. thanks

is there any chance you could tell me what is invalid about those ones though.

---

### Post by Mirrorball on 2007-04-22
'... WHERE page_id = page_id FROM pages' is invalid. Are you trying to do an inner join?
'... FROM pages and SELECT ...' should be two different queries.
INSERT syntax: "INSERT INTO table (x, y, z) VALUES('x', 'y', 'z')"

---

### Post by dyous87 on 2007-04-22
$result = mysql_query('SELECT * FROM pages_data WHERE page_id = page_id FROM pages',

hmm so this is wrong now? because i've been playing with the code and now i get on these errors:

```
**Notice**:  Undefined index:  chances in **/var/www/html/fordham/student/begin_code.php** on line **31**

**Notice**:  Undefined index:  chances in **/var/www/html/fordham/student/begin_code.php** on line **36**
```

however the page only displays one radio button with a submit button so obviously there are lots of things wrong with this. I think i am trying to do an inner join, or would it be an outer join. i wish my teacjer didn't give me this project at this point, it's way above my skill level. oh well though thanks for your patience.

---

