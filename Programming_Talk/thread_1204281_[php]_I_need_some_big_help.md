---
title: "[php] I need some big help"
date: 2009-07-04
forum: Programming Talk
---

### Post by ELD on 2009-07-04
Deleting topics.

The way it currently works:
Delete a topic, update the main forum stats, grab the next available topic from the same forum and then update all parent forums (even if it has a partner forum or even a subforum that has a newer topic) to that topics information for the last post info.

Which is totaly wrong it should work like below:

Check any subforums and then that subforums children to see if their last topic was made after the topic we tried to find from the forum we deleted the topic from (if we didnt find a topic before any topic in a subforum will be newer obviously).

It does that so it can correctly update the parent forum category correctly but only one problem, what if the parent forum category holds another forum apart from the one we are deleting a topic from, we need to check them now as well as their subforums to make sure they don't have a newer topic. for the parent forums last post info.

And then we need to repeat it for the next parent and so on, i'm so confused!

---

### Post by credobyte on 2009-07-04
```
**Programming**
     - C++
[COLOR=DimGray]          - Linux
          - Windows[/COLOR]
     - Python
     - Java
```Depending on how your database is organised, you may want to do it in this way :

[LIST=1]
[*]delete topic from Python ( child of Programming )
[*]check for the latest Programming topic ( including all sub-categories )
[/LIST]

No matter from where the topic was deleted, always check parent & child categories ( if you've 2 child categories with sub-categories, idea is still the same ).
Not sure about why you want to grab the next topic from the same category, but .. it's useless ( as you'll check it again while looping trough the child categories and checking for "latest" post ).

---

### Post by ELD on 2009-07-04
It's not as easy as that at all. Each subforum has it's own last topic information so i can't just check the main forum and update from there, since they all would have their own latest post.

Your way i would have to loop down to find each single forum, then loop back to update, which seems pointless and double the work?

---

### Post by credobyte on 2009-07-04
In that case .. which one will be the latest post and for which category ?

```
**Programming** ( latest post in Java sub-category : 02:24:51 )
    - Java ( latest post : 02:24:51 )
    - Python ( latest post in Windows sub-category : 02:07:54 )
         [COLOR=DimGray]- Linux ( latest post : 01:47:12 )[/COLOR]
         [COLOR=DimGray]- Windows ( latest post : 02:07:54 )[/COLOR]

```

Now, if you delete a topic from Python/Windows, check both Python sub-categories and compare both sub-category latest posts.
If Python appears to be a sub-category of something else ( you can check it ), update parent category by applying the same logic - check all sub-categories and compare their latest posts.

Ah, anyway .. good luck with this ;)

---

### Post by ELD on 2009-07-04
This is what i try to do, and fail miserably and it is ruining my project.

---

### Post by mike_g on 2009-07-06
How you gob about this kinda depends on your database schema. But these are the steps I would take:

1) get the root board id for the subforums.
2) use recursion to get all the subforum ids from the top level forum.
3) update the time using the ids you got.

In code, it may be some thing like:
```
function updateTimes($time, $forum_id){
        global $ids = "";
	$root_forum_id = getRootForum($forum_id);
	$ids = getUpdateIds($root_forum_id);
	$ids = substr($ids, 0, strlen($ids)-1); // chop off the last ,
	mysql_query("UPDATE forum SET last_post_time='$time' WHERE id IN('$ids')");
}

function getRootForum($forum_id){
	while(1){
		$result = mysql_query("SELECT id, parent FROM forum WHERE id = $forum_id");
		$row = mysql_fetch_object($result);
		if(! $row){
			return -1; 			//somethings broken
		}else if(! $row->parent){
			return $row->id;  	//got the parent forum
		}
	}
}


function getUpdateIds($forum_id){
        global $ids;
	$ids.=$forum_id.",";
	$result = mysql_query("SELECT id FROM forum WHERE parent = $forum_id");
	while($row = mysql_fetch_object($result)){
		getUpdateIds($row->id);
	}
	return $ids;
}

```
I havent tested it, so there may be errors in it, but hopefully it gives you an idea of how you could go about it. Have fun...

---

### Post by ELD on 2009-07-06
@mike_g i didnt look at the code but from you explanation i think it is similair to what im attempting to do but in a different way.

Basically all forums have a new field "children" so it will grab all the children forum ids from those fields and then find the last topic information that way (so instead of being a hardcoded last_post_id). So when i delete a topic i won't have to update anything at all.

If that doesn't work right i will try your coding.

Thanks!

---

### Post by mike_g on 2009-07-06
Ok, good luck with it :)

Perhaps it may be worth going through some existing forum software too to see how they do things VBullitin and PHPbb are my favorites.

I never wrote forum software myself, but have done several mods on some. Generally they tend to have have a parent field instead of a child field containing multiple values, in relational theory, database fields are intended to store a single value. It also makes things a bit messy when you delete entries referenced by multivalue fields as you have to explode the references then implode it without the deleted one. I dunno, it might make things a bit simpler in the long run...

---

### Post by ELD on 2009-07-06
I have a parent field, as well as a children field ;)

---

