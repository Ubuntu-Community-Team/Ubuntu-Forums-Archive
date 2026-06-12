---
title: "php help"
date: 2006-02-09
forum: Programming Talk
---

### Post by grim918 on 2006-02-09
i need some help. how would you go about writing a script that will show if a user is online or not. I'm thinking about creating script that checks for a certain value in a database for a certain individual, if the value is 1, then it will display online, if the value is 0 then it will display offline. when the user logs in the script will change their status to online, my problem is how do i change their status back ot offline. I can create a logout button that will change their status back to offline, this will only work though if the user logs out by using the logout button, but what if the user clicks on the close button of the window. This will keep the users status on online. Can someone help me out with my problem.

---

### Post by LordHunter317 on 2006-02-09
A smarter idea is to define a window for which a user is considered 'online'.  All activity (page hits, whatever) causes an update to a last activity field, which is a date/time stamp.  When asked if a user is online, you compare the difference between the current time and the last activity field to the window.  If the difference exceeds the window, they are offline.

---

### Post by nemik on 2006-02-09
IMO the simplest way is to check the user's session. as long as the session is alive, user can be considered offline. if it expires or he/she closes the browser, they won't be online anymore.

---

### Post by sapo on 2006-02-09
I think that you can use something like this:

user_id|timestamp

When the user logs in you insert his user_id and a timestamp in this table, when he open a page you update the timestamp, you record his user_id and the current timestamp using NOW() in mysql of time() in php, then when another user logs in, you check the timestamps that are older then 15 minutes and delete them before inserting the new user_id.

I think that this is simple and should work, you can also check and delete the timestamps for each page that a user opens.. something like this:

[php]function users_online($user_id) {
  $time = time() - (60*15);
  $sql_delete = "DELETE FROM users_online WHERE timestamp < $time";
  @mysql_query($sql_delete); 
  $sql_check = "SELECT user_id FROM users_online WHERE user_id='$user_id'";
  @mysql_query($sql_check);
  if(mysql_affected_rows() == 0) {
    $sql = "INSERT INTO users_online (user_id, timestamp) VALUES ('$user_id', NOW())";
   } else {
     $sql = "UPDATE users_online SET timestamp=NOW() WHERE user_id='$user_id'";
   }
   @mysql_query($sql);
   return true;
}[/php]

---

### Post by grim918 on 2006-02-10
how do you check if a users session is still alive. im new to sessions. thats why im having trouble with this part of the code. and thanks for the help.

---

### Post by LordHunter317 on 2006-02-10
[QUOTE=sapo]When the user logs in you insert his user_id and a timestamp in this table, when he open a page you update the timestamp, you record his user_id and the current timestamp using NOW() in mysql of time() in php, then when another user logs in, you check the timestamps that are older then 15 minutes and delete them before inserting the new user_id.

I think that this is simple and should work, you can also check and delete the timestamps for each page that a user opens.. something like this:[/quote]This is exactly what I described except you shouldn't delete the records, you should just update them.  It's sensless to delete and recreate them, and the online time is unique to each user record.

---

### Post by sapo on 2006-02-10
You cant, sessions are client side, just the user can see if his session is still alive.

You cant check someone else session :p

---

### Post by grim918 on 2006-02-11
im having trouble understanding all of this. does someone know of an online site where i can do some reading about sessions.

---

### Post by sapo on 2006-02-11
[http://www.php.net/session](http://www.php.net/session)

---

### Post by grim918 on 2006-02-12
thank you

---

