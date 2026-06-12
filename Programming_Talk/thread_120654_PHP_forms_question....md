---
title: "PHP forms question..."
date: 2006-01-23
forum: Programming Talk
---

### Post by veraction on 2006-01-23
Currently, I have a form which consists of 2 steps:
[LIST=1]
[*]Fill out form & click submit
[*]Form's input is displayed & then it is processed
[/LIST]
I'd like to make it a 3 step process:
[LIST=1]
[*]Fill out form & click submit
[*]Output the user's input and have a verify button (so if they screwed up they can go back)
[*]process form input
[/LIST]


Say I have a form in *1.html*:
```
<form action="2.php" method="post">
    Name:  <input type="text" name="username" /><br />
    Email: <input type="text" name="email" /><br />
    <input type="submit" name="submit" value="Submit" />
</form>
```

then *2.php* looks like this:```

   <?
        $username = $_POST[ 'username' ];
        $email = $_POST[ 'email' ];

        echo "<h2>Verify: </h2>";
        echo "Username: $username<br>";
        echo "email: $email";

        echo "<form action = \"3.php\" method = \"post\" >
                     <input type = \"submit\" name = \"complete\" value=\"complete\" />
            </form>";
    ?>

```

Now, how would I go about getting the $username and $email variables in 3.php? -- not using 3.php?username=x&email=y  (cause form may have lots of text)

2.php & 3.php could be combined into one file if needed, but I still can't figure it out then. I can use isset( $_POST[ 'complete' ] ) to check if the 'complete' button was pressed, but can't access the email & username fields.

I'd prefer to remain compatible with different browsers & settings. So, no javascript or cookies

---

### Post by mostwanted on 2006-01-23
```
<input type="hidden" name="email" value="$email" />
```

---

### Post by veraction on 2006-01-23
Yeah, I considered that. Thought it may not be too elegant considering users will be filling out forms with maybe 5000 characters in total. But that may be the only way

---

### Post by mostwanted on 2006-01-23
It is if you won't do cookies or session cookies.

[QUOTE=veraction]Yeah, I considered that. Thought it may not be too elegant considering users will be filling out forms with maybe 5000 characters in total. But that may be the only way[/QUOTE]

Who cares? They're positively never going to see it anyway.

---

### Post by grim918 on 2006-01-23
using hidden fields is the only way that i can think of. i dont know if it would work  but you could try and use sessions.
in 2.php you could create a session and then use 

$_SESSION[email] = $_POST[email]; //this would store the users email address

if this is passed to 3.php then you can resume a session by using session_start() in 3.php. 3.php could access the input from 2.php using $_SESSION[email].

after 3.php is done processing input then you can just destroy the session using session_destroy();

i still think using hidden fields would be the best choice though. you could give sessions a try if your looking for something new though.

---

### Post by YopY on 2006-01-23
You could also just copy / paste the entire form and add the filled in stuff to the fields. Like this:

```

//2.php

    Name:  <input type="text" name="username" value="<?php echo $username; ?>" /><br />
    Email: <input type="text" name="email" value="<?php echo $email; ?>" /><br />
    <input type="submit" name="submit" value="Submit" />

```

That way, the user can simply edit the contents in the text fields without having to go back to 1.php. But then again, you might want to have them re-confirm their choices. You could then go and add some hidden form fields again and check wether the values of the hidden form fields are identical to the values inserted in the shown form fields, if they're not, you can give the user the form again, and if they are, then the selection has been confirmed.

---

### Post by veraction on 2006-01-23
Ok, got some ideas from this thread. I'll either use sessions or hidden fields.

sessions are completely server side right? so it doesn't matter what browser/settings someone has?

And,

[QUOTE=grim918]
i still think using hidden fields would be the best choice though. you could give sessions a try if your looking for something new though.[/QUOTE]
Why would you consider hidden form fields to be a better way of doing it rather than sessions?

---

### Post by mostwanted on 2006-01-23
[QUOTE=veraction]sessions are completely server side right? so it doesn't matter what browser/settings someone has?[/QUOTE]

Sessions are temporary cookies, they're client-side.

---

### Post by veraction on 2006-01-23
Ok, hidden forms then. Thanks

---

### Post by Corvillus on 2006-01-24
You could also include
[php]<?php ini_set('session.use_trans_sid', 1); ?>[/php]
at the beginning of each file. This will cause PHP to pass the session ID in a get string instead of a cookie, so things will work if cookies are disabled, and you won't have to use hidden form fields. The downside of this is that the session ID will appear in the query string (the part of the URL after the ? ) of all of your pages which use this directive.

---

