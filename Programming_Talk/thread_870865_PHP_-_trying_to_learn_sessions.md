---
title: "PHP - trying to learn sessions"
date: 2008-07-26
forum: Programming Talk
---

### Post by sp0nge on 2008-07-26
I am trying to learn PHP and have come to research sessions for user authentication. I am at the very beginning of understanding this, and my code is basic, but there is a syntax error (apparently) that I'm not able to identify:

```
<?php
session_start();
//Check to see if user has logged in with a valid password
	if ($_SESSION['auth user']!=1 {
	echo "Access Denied.";
	exit();
	}
?>
```

Upon calling the file in a browser, I get a parse error on line 4. I tried to diagnose this myself and made a simple change: 

```
<?php
session_start();
//Check to see if user has logged in with a valid password
	if ($_SESSION['auth user']!=1 
        {
	echo "Access Denied.";
	exit();
	}
?>
```

And then I got the error on line 5. Is the "{" not necessary to contain the instructions for "if"?](*,)

---

### Post by LaRoza on 2008-07-26
C'mon! A syntax error? A good editor should show you that! Close the () in the if statements!

---

### Post by sp0nge on 2008-07-26
I don't have a "good" editor on this window's machine. 

Thanks, I knew it was something stupid!

---

### Post by LaRoza on 2008-07-26
> **sp0nge said:**
> I don't have a "good" editor on this window's machine. 

Thanks, I knew it was something stupid!

If you can install editor: [http://www.crimsoneditor.com/](http://www.crimsoneditor.com/)

If you cannot install: [http://portableapps.com/apps/development/notepadpp_portable](http://portableapps.com/apps/development/notepadpp_portable)

---

### Post by drubin on 2008-07-26
> **LaRoza said:**
> 
If you cannot install: [http://portableapps.com/apps/development/notepadpp_portable](http://portableapps.com/apps/development/notepadpp_portable)

Great app REALLy :) 2nd that

---

