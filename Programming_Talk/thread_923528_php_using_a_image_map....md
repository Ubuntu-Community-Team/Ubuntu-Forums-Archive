---
title: "php using a image map..."
date: 2008-09-18
forum: Programming Talk
---

### Post by hockey97 on 2008-09-18
I have a php script ready to go. I am using a html image map but I don't want to use links to pages since it's a image map of the U.S I can't afford to make 50 different pages.

So I want to use the image map to pass a name by  a post method to my php script so I can use $_POST["state"].

I want to be able to grab what the user has click and then with php do a mysql lookup and generete a list of items in a table this table then would replace the image map so it would only be a table of that list and I will have a button that when clicked It would send me back to the image map.

any idea how I can do this???

---

### Post by LaRoza on 2008-09-18
For URI's, you are best off using GET.
[html]
<a href="http://home.com/index.php?sate=confusion" title="State">Click here for your state</a>
[/html]

Then you just grap that like any other GET variable.

---

### Post by hockey97 on 2008-09-18
so I should put something like that in the image map???

---

### Post by Reiger on 2008-09-18
Well yes. Wherever you dump your links your image map refers to you write:
```

http://my_domain/my_file.php?my_var=my_value

```

Substitute with actual values as required.

Then your my_file.php tailors its output to the value of $_GET['my_var'].

---

### Post by drubin on 2008-09-18
> **LaRoza said:**
> For URI's, you are best off using GET.
[html]
<a href="http://home.com/index.php?sate=confusion" title="State">Click here for your state</a>
[/html]

Then you just grap that like any other GET variable.

I mostly use $_REQUEST solves the issue of if you need to include the var as a hidden varible in a form post. :)

$_REQUEST = $_POST +$_GET + $_SESSION +(1 or 2 others)

---

### Post by drubin on 2008-09-18
For the mods:
Can these threads be merged, they are by the same person, about the same issue. 
[http://ubuntuforums.org/showthread.php?t=920880](http://ubuntuforums.org/showthread.php?t=920880)

---

