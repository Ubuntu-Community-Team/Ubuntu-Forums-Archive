---
title: "PHP: while loop to generate form"
date: 2009-05-25
forum: Programming Talk
---

### Post by scruff on 2009-05-25
Hello,

I am trying to set up a page to enter CD info that will then submit this info to a database. I am kind of stumbling through it with experimentation and I wondered if someone could help me get past this. Here's basically what I have:

[php]
<?php
$i=1;
echo "<tr><th>#</th>";
echo "<th>artist</th>";
echo "<th>track</th>";
echo "<th>sample</th>";

while($i<21) {
		echo "<tr>";
		echo "<td>$i</td>";		
		echo "<td><input type=\"text\" name=\"artist$i\" maxlength=\"30\" value=\"<? $form->value(\"artist$i\"); ?>\"> </td>";
		echo "<td><input type=\"text\" name=\"track$i\" maxlength=\"30\" value=\"<? $form->value(\"track$i\"); ?>\"> </td>";
		echo "</tr>";
		$i++;
		
}

?>
[/php]

But it winds up displaying some of the form info in my fields. Also, is that method of NAME$i an acceptable form of naming multiple items of the same name? 

Thanks!

---

### Post by kay-man on 2009-05-25
It doesn't seem to be a problem to name your fields like this. But i'm not quite sure what you're trying to do here. What is $form? I feel like I'm missing some bits here.

I tried these lines:

```
        $artist = "artist" . $i;
        echo "<td><input type=\"text\" name=\"$artist\" maxlength=\"30\" value=\"" . $form->value($artist) . "\"> </td>";

```

but they give me an error because there is no object named $form

---

### Post by kay-man on 2009-05-25
Also, your top table row (header row) doesn't get closed

---

### Post by scruff on 2009-05-25
Thanks for the response. I am trying to generate a page like this:

```

--------------------------
| track | title | artist |
|------------------------|
|<form> |<form> |<form>  |
|------------------------|
|<form> |<form> |<form>  |
|------------------------|
 etc etc

```
This is to fill a database of various artist cd's. So each row is one track on the album. One page per album. On submission it should populate the database accordingly.

---

### Post by kay-man on 2009-05-25
so do you have $form defined as an instance of a class somewhere?

---

### Post by scruff on 2009-05-25
For now $form isn't important. I just want to know the correct method to generate this page so that all those fields are ready to accept user input and submit them appropriately.

I left out other code since it doesn't actually pertain to my problem.

---

### Post by scruff on 2009-05-25
Here's a screenshot of what I currently see.

---

### Post by kay-man on 2009-05-25
Ok, try this:

[PHP]<?php
$i=1;
echo "<table>";
echo "<tr><th>#</th>";
echo "<th>artist</th>";
echo "<th>track</th>";
echo "<th>sample</th>";
echo "</tr>";

while($i<21) {
        echo "<tr>";
        echo "<td>$i</td>";        
        echo "<td><input type=\"text\" name=\"artist$i\" maxlength=\"30\" value=\"\"> </td>";
        echo "<td><input type=\"text\" name=\"track$i\" maxlength=\"30\" value=\"\"> </td>";
        echo "</tr>";
        $i++;
        
}

?> 


</table>[/PHP]

The difference is that the form fields don't get populated, i.e. value is empty. But the form shows allright. If you have previous values for artist and track you should be able to add that easily.

---

### Post by scruff on 2009-05-25
That works. Thanks!

---

### Post by kay-man on 2009-05-25
Cool! So when can we expect your nifty web based music collection management app to be open sourced? :D

---

