---
title: "a PHP/MySQL wizardry question"
date: 2009-04-10
forum: Programming Talk
---

### Post by skullmunky on 2009-04-10
sorry for the vague subject, I'm not sure how to describe what I'm trying to do concisely.

I'm working on a PHP/MySQL system where each user has access to a subset of the set of files.  Some files can be accessed by multiple users, others might have no users able to access them at all.

I'm doing the admin part for editing a user's file access, showing a list of all the available files and a checkbox to grant or deny access.  My problem is that the way I'm doing it requires a filtering step in PHP, and I'm wondering if there's a sneaky way to do this all in SQL. 

More details: 
I have 3 tables involved: users, files, and fileaccess.  fileaccess has three columns: id, user_id, file_id.

so I can do things like 
```

SELECT files.title, fileaccess.user_id FROM files LEFT JOIN fileaccess ON files.id=fileaccess.fileid

```

unfortunately that gives me too many results - if two users both have access to a file, it shows up twice because there are two records in the fileaccess table.  

```

title           user_id
-----------------------
Videodrome  	5
Zombie Party 	5
Action Pants 	NULL
Spaceballs 	NULL
Cake Riot 	6
Iron Brew 	5
Iron Brew 	6

```

here, user 5 has access to Videodrome, Zombie Party, and Iron Brew.  user 6 has access to Iron Brew and Cake Riot.  Iron Brew shows up twice.

```

WHERE fileaccess.user_id=$user_id

```

only shows me the ones the user has access to; I need the others, too, so I can select them to grant access.

```

WHERE fileaccess.user_id=$user_id OR IFNULL(fileaccess.user_id,0)=0

```
is closer but only shows me files that I can access or nobody can access; e.g. for user 5, "Cake Riot" doesn't show up at all.

UNION doesn't seem to help because it only unifies rows which are totally identical.  

DISTINCT doesn't seem to do anything for me here either, I guess because it only applies within each table, not to the JOINed result.

I can fix this by then iterating through the results in PHP and removing duplicates, but I'm wondering if there's a better way to do it through SQL.  

btw: those filenames are just for testing purposes, I am not making some kind of movie pirating site.

---

### Post by soltanis on 2009-04-10
I don't understand. It seems like what you're describing is exactly the behavior you want. Why do you want to filter out "duplicate entries" which aren't duplicates anyway, since they describe 2 different things?

In your Iron Brew example, yes users 5 and 6 have access to the file hence it shows up twice. Why do you want that not to be true?

---

### Post by skullmunky on 2009-04-11
Hm, yeah, let me try and explain that better.  This is for the site admin to edit access options, on a per-user basis.  On the page for editing User #5, I should see a list of all the files, with a flag next to each showing whether User 5 can access it. In this context I don't care about whether -other- users can access a file, only User #5.  

so, the end result I want is like this (when editing user #5):

```

File            Accessible
-----------------------
Videodrome  	[X]
Zombie Party 	[X]
Action Pants 	[ ]
Spaceballs 	[ ]
Cake Riot 	[ ]
Iron Brew 	[X]

but, I get this instead:

File            Accessible
-----------------------
Videodrome  	[X]
Zombie Party 	[X]
Action Pants 	[ ]
Spaceballs 	[ ]
Cake Riot 	[ ]
Iron Brew 	[X]
Iron Brew      [ ]

```

Of course I may be thinking about this all wrong in some way...

---

### Post by Reiger on 2009-04-11
Am I an complete and utter idiot or do you just want a list of **all files in the system with a boolean flag indicating access rights**?

A CASE statement may help (YMMV because one SQL differs from DB to DB): [http://www.tizag.com/sqlTutorial/sqlcase.php](http://www.tizag.com/sqlTutorial/sqlcase.php)

---

### Post by simeon87 on 2009-04-11
What about:

```

SELECT id, title FROM files WHERE id IN (SELECT fileid FROM fileaccess WHERE user_id = 5)

```

The subquery selects all files the user is allowed to access, the outer query selects the ids and titles.

Edit: right, you want the other files too. In that case the above query isn't what you're looking for.

---

### Post by kpatz on 2009-04-11
(duplicate post, must have hit reply instead of edit)

---

### Post by kpatz on 2009-04-11
I'm a programmer, and have run into this sort of thing many times in my days.

The way I typically do it is: start with your join query in your post, but ORDER BY files.title.

Then, in the PHP, as you're going through the results, look and see if the title is the same as the previous title.  If it is, you have a repeat, and you can skip it.  If you see a user id that matches the one you're working with, set the checked flag for that title.

Something like this (this is quasi-PHP pseudo-code, I'm too lazy to look up the PHP commands):

[php]
  $lasttitle="";
  $checked = 0;
  while fetch($result)
  {
    if ($result['title'] != $lasttitle)
    {
      if ($lasttitle)
      {
       (write out info for last title)
      }
      $lasttitle = $result['title'];  // store last encountered title
      $checked = 0;  // reset checked flag
    }
    // if user has access, set checked flag
    if ($result['user_id'] == $user_id_being_edited) $checked = 1;
  }
  if ($lasttitle)
  {
    (write out info for last title that would have been missed in the loop)
  }
[/php]

---

### Post by skullmunky on 2009-04-11
@Reiger: Bingo, that's exactly what I need :)  I'll check out CASE and see if I can make that work.  In the meantime, here's the PHP solution I came up with ... 

```


$result = DBQuery ("SELECT videos.id AS video_id, videos.title AS title, IFNULL(videoaccess.user_id,0) AS user_id FROM videos 
LEFT JOIN videoaccess ON videos.id=videoaccess.video_id");

if ($result)
{
	$videos = array();
	
	$n=mysql_numrows($result);
	for ($i=0;$i<$n;$i++)
	{
		$video_id = mysql_result($result,$i,'video_id');
		
		$t=mysql_result($result,$i,'title');
		$u=mysql_result($result,$i,'user_id');
		
		$vidrec=array();
		$vidrec[0]=$video_id;
		$vidrec[1]=$t;
		$vidrec[2]=$u;	
		
		// this item already in the list
		if (isset($videos[$video_id]))
		{
			if ($u == $user_id)
				$videos [$video_id] = $vidrec;
		}
		else
		{
			$videos [$video_id] = $vidrec;
		}
	}
	foreach ($videos as $v)
	{
		if ($v[2]==$user_id)
			$acc="CHECKED";
		else 
			$acc="";
		print ("<tr><td>$v[0] $v[1]</td><td><input type='checkbox' name='access[]' value='$v[0]' $acc></td></tr>\n");
	}
}

```

---

