---
title: "[PHP] a simple bad word filter?"
date: 2009-02-09
forum: Programming Talk
---

### Post by ELD on 2009-02-09
Basically i have this:
```

		$sql_find_words = "SELECT `word`,`filter` FROM `bad_words`";
		$query_words = $db->query($sql_find_words, $page='class_post_parser.php');
		$bad_words = $db->fetch_array($query_words);

```

How would i then filter each "word" found with it's corresponding "filter" ?

---

### Post by drubin on 2009-02-09
> **ELD said:**
> Basically i have this:
```

		$sql_find_words = "SELECT `word`,`filter` FROM `bad_words`";
		$query_words = $db->query($sql_find_words, $page='class_post_parser.php');
		$bad_words = $db->fetch_array($query_words);

```

How would i then filter each "word" found with it's corresponding "filter" ?

Ok firstly I am stuggiling to try and understand what "$db->query($sql_find_words, $page='class_post_parser.php');" does. I understand the query part but what is  $page....

Secondly how big is this word list? How big is it expected to get? (VERY important to which method/algo you choose to use).

You need to think of solutions that are sutible to the load/data you will be working with. 

You could if the list wasn't to big get all the data like you have done here put it in an array and loop through the words in your $message and if found replace them with $filter.

The problem comes into play, is it each word on its own or part there of.
ie 

Take the bad word "boo"
> The big boy went boo boo when his baboon bit him.
would it be
> The big boy went *** *** when his ba***n bit him.
OR 
> The big boy went *** *** when his baboon bit him.

---

### Post by ELD on 2009-02-09
Okay firstly that "$db->" is my own database class function "$page" is just telling me what page the query is called from for debugging, very useful.

How big it is at the moment is 4 or 5 words, but i may keep adding, depends what words i deem naughty haha.

I don't know about the "boo" wording, whatever would be the best way.

---

