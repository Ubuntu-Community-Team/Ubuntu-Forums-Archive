---
title: "PHP search through array with in_array"
date: 2011-09-25
forum: Programming Talk
---

### Post by aktiwers on 2011-09-25
Could someone help me out with this.

I have a database  table called wp_users. In this table there is a row called user_login, which contains all the usernames.

Now I want to search through these usernames, to check if they exist or not.

I do it this way and it seams to work:

[php]
// db connection
$con = mysql_connect("localhost","user","password");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

mysql_select_db("databasename", $con);

//Get usernames from db to $usernames
$usernames = array();
$results = mysql_query("SELECT * FROM wp_users");
while ($row = mysql_fetch_array($results))
    {
      $usernames[] = $row['user_login'];
    }

        {
        if (in_array($name, $usernames, true))
            {
            $response="Username not in use!";
            }
        else
            {
            $response="Username in use!";
            }
        }[/php]The thing I dont understand is - when my "if (in_array($name, $usernames, true))" finds a match it prints the ELSE statement, and when it does not find a match it prints the IF statement.

Shouldn't it be the other way around? When "if (in_array($name, $usernames, true))" is true, it prints the first statement, and when false the last statement (the ELSE statement).

Or could someone explain this to me?

---

### Post by lisati on 2011-09-25
I've never used the "strict" option with [in_array()]("http://php.net/manual/en/function.in-array.php") - the option where you've specified "true" - and have found that in_array works as expected for me.

---

### Post by Bachstelze on 2011-09-25
You are making it far more complicated than it needs to be. Just run

```
SELECT * FROM wp_users WHERE user_login = $name
```

and check whether it returns zero or one row.

---

### Post by aktiwers on 2011-09-25
Thank you both for your answers.

And you are right Bachstelze, I didn't think about that.

Its a bit late here (again) - and now when I re-read my code, the behavior makes sense.
It is behaving correct. I simply switch the $response statements around, because Im tired :)

About the strict option, it does not really matter. I use it because it is CaSe SensiTive.

Again thanks for the replys.

---

