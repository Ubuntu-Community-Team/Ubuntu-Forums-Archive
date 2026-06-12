---
title: "php: Can't get if/else to work right?"
date: 2007-06-23
forum: Programming Talk
---

### Post by jingo811 on 2007-06-23
I want to print out the name of the Organization evaluators whenever there's data in my database.  And I want to printout "Don't know" whenever there isn't any data.
But I can't make it work :(
Originally I used
if ( !empty($_REQUEST....)
But that made the code jump right to the 
else part thus making all printout "Don't know" even if there's data for selected products.

```
		if ( !isset($_REQUEST["**Evaluators**"]) ) {


			print	"<tr>" . 

					"<td>Organization evaluation by: </td>" . 

					"<td><b>" . 

					$one_whole_row["**Evaluators**"] . 

					"</b></td>" . 

					"</tr>";

		} else {


			print	"<tr>" . 

					"<td>Organization evaluation by: </td>" . 

					"<td><b>" . 

					"**Don't know!**" . 

					"</b></td>" . 

					"</tr>";

		}
```
Can you see what's wrong or how I should back track all my codes?

---

### Post by jpeddicord on 2007-06-25
Try taking out the ! from isset.

```
		if ( isset($_REQUEST["Evaluators"]) ) {


			print	"<tr>" . 

					"<td>Organization evaluation by: </td>" . 

					"<td><b>" . 

					$one_whole_row["Evaluators"] . 

					"</b></td>" . 

					"</tr>";

		} else {


			print	"<tr>" . 

					"<td>Organization evaluation by: </td>" . 

					"<td><b>" . 

					"Don't know!" . 

					"</b></td>" . 

					"</tr>";

		}
```isset is pretty much the opposite of empty in the context you were using it.

---

### Post by jingo811 on 2007-06-26
I managed to sort things out now, it was the $_REQUEST part that was causing troubles
I should have accessed the variable from **mysqli_fetch_assoc** instead.
```
		if ( isset($one_whole_row["Evalutators"]) ) {
...
...
```

Now Firefox is happy and when Firefox is happy I'm happy :)

---

