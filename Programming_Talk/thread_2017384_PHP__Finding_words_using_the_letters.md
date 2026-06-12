---
title: "PHP : Finding words using the letters"
date: 2012-07-05
forum: Programming Talk
---

### Post by djuran89 on 2012-07-05
<input name="letter1" type="text" maxlength="1">
<input name="letter2" type="text" maxlength="1">
<input name="letter3" type="text" maxlength="1">
<input name="letter4" type="text" maxlength="1">


$words = array('best','cake','test','taxi');

I want if i type e,t,b,s fine me word "best".

Somting like this [http://www.thewordfinder.com/scrabble.php]("http://www.thewordfinder.com/scrabble.php").

---

### Post by trent.josephsen on 2012-07-05
It's not 100% clear what you want.

* To generate dictionary words composed only of a short list of letters?
* To select one word from a short list of words based on knowing which letters it contains?
* To reorder scrambled letters into dictionary words?

You won't find any answers if you don't understand the problem...

---

### Post by djuran89 on 2012-07-05
check the [link]("http://www.thewordfinder.com/scrabble.php"). I need same thing, but i want to type letters in separate <input> one <input> one letter.

I want to find all words that contain the selected letters.
I need only words from 12 to 9 letters, but i here give exemple just for 4 letter. after i will try create same thing for 12 letter.

pls help. i kill my self because i can't find solution :D

---

### Post by trent.josephsen on 2012-07-05
Sigh. [Clicky]("http://ubuntuforums.org/showthread.php?t=1006666"). (Especially the links about posting homework and asking smart questions.)

Try to solve the problem yourself and post your code when you get stuck.

(Hint: First, generate all possible combinations of your four-letter "alphabet" and then worry about which ones are real dictionary words.)

---

### Post by djuran89 on 2012-07-05
OK. 
Probelm is here for example when I type "g","o","l","d" he just find the word gold, and not to find a gol.
I don't know how to write correctly if function, to find me the words with three and four letters 


HTML:
```

<form action="" method="post">
<input id="box" name="letter1" type="text">
<input id="box" name="letter2" type="text">
<input id="box" name="letter3" type="text">
<input id="box" name="letter4" type="text">
<input type="submit">
</form>
```
PHP:
```

$letter1 = $_POST['letter1'];
$letter2 = $_POST['letter2'];
$letter3 = $_POST['letter3'];
$letter4 = $_POST['letter4'];


$array = array('cut','put','work','gol','gold');


for ($x=0; $x<sizeof($array); $x++)	
	
$pos1 = strpos($array[$x], $letter1);
$pos2 = strpos($array[$x], $letter2);
$pos3 = strpos($array[$x], $letter3);
$pos4 = strpos($array[$x], $letter4);


if ($pos1!== false and $pos2!== false and $pos3!== false and $pos4!== false){
	echo $array[$x]."<BR>";

}


```

---

### Post by SeijiSensei on 2012-07-05
If the search space is limited to three or four letters, then just have the script generate all possible combinations of the input and see which matches.  With four letters, there are only 4! = 24 combinations to generate.

---

### Post by djuran89 on 2012-07-05
can be something simpler ? because I after  need make script for 12 letter and then it would be many combinations.

---

### Post by trent.josephsen on 2012-07-05
I think SeijiSensei and myself were assuming you had something of a much larger dictionary in mind than just a few words. If you only have a handful of words to check against, then yes it's going to be quicker to *check each word individually to see whether it contains (only) the letters in your alphabet* than to generate all the possible combinations.

If you're actually looking for all 9 to 12 letter words in the English language (or some other natural language), then, umm, yeah, you're going to find a lot of words no matter how you do it.

Anyway, so you've got the basic algorithm down: for each word in the dictionary, see whether it meets the criteria; if so, print it. It's the criteria itself that you haven't worked out yet. Checking *whether the word contains every letter in your alphabet* isn't working; you need to determine *whether the word contains **only** letters found in your alphabet*. (I imagine you want to count duplicates as distinct letters, too, but I'll leave that out for now.)

So get a sheet of paper, and write the letters D G L O across the top. Now write down the word "dog" and ask yourself: "How could I tell whether the word "dog" contains **only** letters from the four-letter alphabet at the top of the page?" You're going to have to compare one letter at a time and it's going to involve a lot of repetition. (When you implement it in code, it'll probably involve a nested loop.)

Now do the same thing with the alphabet A B C D E G H I L N O P R T U Y and the word "copyrighted". You should be seeing patterns that you can use to write code.

(Real solutions to similar problems often make use of a technique whose name I can't recall, but it amounts to checking prefixes and not just whole words. E.g. if the input letters are ['e', 'g', 'l', 'm', 'o', 'o', 't', 'y', 'y'], you can pretty quickly rule out any combination that starts with "eglm-" regardless of the order of the other five characters, because there is no word (in the dictionary I'm using) that begins with that prefix.)

---

