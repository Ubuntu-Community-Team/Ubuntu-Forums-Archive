---
title: "Need advice on coding this in php"
date: 2009-05-12
forum: Programming Talk
---

### Post by ELD on 2009-05-12
Basically on my script i am coding an option to email inactive members.

I currently have this:
```

        $sql_find = "SELECT `username`, `email` FROM `members` WHERE `last_active` < $inactive_time AND `member_id` != 2";
        $query_find = $db->query($sql_find);
    
    while ($info = $db->fetch_array($query_find))
    {

    }

```I was thinking to add a email inside the while loop but then it will use the email function for every single member, it would be better on the systems resources to use one mail function and cc all the emails right?

But then if i do it that way it can only be a generic email as i won't be able to change the username displayed in the email as it will just be sending to all.

---

### Post by sonicb00m on 2009-05-12
you can email in the loop but it might be advisable to add a sleep function for a few seconds after every x emails to stop the mail server flooding the cpu.

---

### Post by ELD on 2009-05-12
That is exactly what i was thinking, but what would be a good way to do it "every x mails" ?

---

### Post by pitje on 2009-05-12
```

$sql = "SELECT `username`, `email` FROM `members` WHERE `last_active` < $inactive_time AND `member_id` != 2";
$result = $db -> query ( $sql );
   
$count = 0;
$max = 10;	//max amounts of mail to send per batch
$sleeptime = 5; //time to sleep in seconds
while ( $info = $db -> fetch_array ( $result ) )
{
	// do the things you do
	// to send the mail here

	if ( $count++ === $max )
	{
		$count = 0;
		sleep ( $sleeptime );
	}
}

```
?

---

### Post by ELD on 2009-05-12
Great stuff thanks.

---

### Post by sonicb00m on 2009-05-14
Depending on the server and what else is running there you might want a gap of 5-15  every 50 mails or so?

---

### Post by s.fox on 2009-05-14
Hi,

Don't forget to add the database connection details,  or your query will fail :)

-Ash R

---

### Post by ELD on 2009-05-14
> **Ash R said:**
> Hi,

Don't forget to add the database connection details,  or your query will fail :)

-Ash R

Lol i know that of course. That is just a snippet of code i was asking about not the whole script :P

---

### Post by rsuresh on 2009-05-15
hai  i need to know the  procedure  for  sending mails  through  a php  mail function  in linux.


and also  i need to know the changes to apply on the php.ini  file  .

please help me in this regards

---

### Post by ELD on 2009-05-15
Would be better to make your own thread really, keep each problem seperate.

---

