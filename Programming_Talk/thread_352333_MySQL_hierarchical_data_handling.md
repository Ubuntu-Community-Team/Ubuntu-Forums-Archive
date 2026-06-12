---
title: "MySQL hierarchical data handling"
date: 2007-02-03
forum: Programming Talk
---

### Post by rem on 2007-02-03
Hello,

I'm interested in PHP developing and nowadays I'm studying all sorts of methods of handling hierarchical data in or out a MySQL database. I found a few methods but I would like to know which one is the best. Now, since I'm a huge Drupal and Wordpress fan and they for certain use one of this methods in their code to handle their infinite hierarchical complex navigational structures and because I'm not that good yet to understand that by myself, I am wondering: Do anyone actually knows what database handling method did they use to output their tree like navigations systems? 

Thank you!

---

### Post by kidders on 2007-02-03
Hi there,

This may be too simplistic, but let's see what you think. For the sake of argument, let's say you want to store element names from an XML document in a database. (Who knows why!)

I would create an "element" table like this:[LIST]
[*]id (INT AUTO_INCREMENT PRIMARY KEY)
[*]parentid (INT)
[*]tagname (TEXT)
[/LIST]
I would consider elements with (parentid<0) to have no parent.

```
<html>
       <head />
       <body>
              <img />
              <hr />
       </body>
</html>
```

So, the result of storing that would be:

```
id	parentid	tagname
1	-1		html
2	1		head
3	1		body
4	3		img
5	3		hr
```

Now, you could do things like ...

```
SELECT * FROM element WHERE parentid=1
```... to find all children of a given node in the tree, or ...
```
SELECT element.*, COUNT(child.id) AS childcount FROM element LEFT JOIN element AS child ON element.id=child.parentid GROUP BY element.id
```... to count the children of each node in the tree.

Is this anything like what you were looking for?

---

### Post by rem on 2007-02-03
This is great, thanks for your answer... My problem is that I'm tending to complicate things a lot... But still, just counting child nodes, will not get me a navigational system like WP or Drupal has... I need to store and out the data in and out a MySQL DB the same manner as the 2 OO applications does. I just need a infinite multilevel tree like menu. I was wondering what's the best / simplest method...

Thanks a mil, I will give your code a shot!

---

### Post by kidders on 2007-02-03
Hey again,> **rem said:**
> I just need a infinite multilevel tree like menu.Sorry... my last post was totally confined to the underlying data structure. The one thing that confuses me slightly is what you mean by "infinite". A tree will never be infinitely large unless at least one node is its own parent (either directly or indirectly). Is that likely to happen? In your o/p I took "infinite" to mean that you didn't want your data structure to impose a hard-coded cap on the number of leaves/levels your tree could have. Now I'm not so sure. :confused: 

In any case, let's imagine you wanted to display a large (but finite) tree structure in a web page. In XHTML terms, you would want to produce a collection of nested lists, that you could apply some CSS to, to make them look pretty.

```
<?php
dump_branch(-1);

function dump_branch($id) {
	$items=mysql_query("SELECT * FROM element WHERE parentid=$id");
	if (mysql_num_rows($items)>0) {
		echo "<ul>";
		while ($item=mysql_fetch_assoc($items)) {
			echo "<li>{$tem['tagname']}";
			dump_branch($item['id']);
			echo "</li>";
		}
		echo "</ul>";
	}
}
?>
```

Something like this (perhaps with some nice L-shaped background images, to make them look joined together) ought to do the trick. There are two problems with this approach though:

[LIST=1]
[*]As you can see, it would loop infinitely if your tree was infinite. You could stop that from happening by storing the primary keys of each tree node, as you "echo" it, and verifying that the same one isn't processed twice.
[*]There would potentially be quite a lot of SQL querying going on. How to optimise that aspect of the code depends very much on the shape of your tree, and the way you intend to present it.
[/LIST]

---

### Post by rem on 2007-02-03
Hey, thanks again ... you made me a great tutorial there :)
I saw some great navigational systems out there but most of them were not allowing you only a few links bellow, like two, three or maximum four. So, i would need some navigational system, like WP or Drupal. You can have as many nodes you want and assign as many sublinks to them and to those sublinks other sub-sublinks. The same concept can be applied to an online store where there's a main product category like "Electronics" and under that other secondary categories like "TVs", "Computers", "Portable" and to each of these secondary categories other like TV -> Tube, Flatscreens, Plasma, etc, etc... and to Computers Desktops, Laptops, PDAs, etc, etc and to Portables, CD players, MP3 players, etc, etc .. and we can go even deeper :)

I didn't had the chance to study your function yet, even though I studied all the stuff I could find on this matter on www :) I noticed though you used a *recursive* function which is not bad even though, as you stated too, I'm worried about the server load myself. The next one would be the [**_Modified Preorder Tree Traversal_**]("http://www.sitepoint.com/article/hierarchical-data-database/2") method, which honestly I have hard times to comprehend :( I was just wondering: if you'd have to build an application and you'd need some kind of hierarchical data structure, for what method you'd go for?

Thanks a lot, really appreciate it. The way you say it, sounds less complicated :)

---

### Post by rem on 2007-02-03
> Something like this (perhaps with some nice L-shaped background images, to make them look joined together) ought to do the trick. There are two problems with this approach though:

Your function works like a Swiss watch :) I'm impressed, very simple indeed!

---

### Post by kidders on 2007-02-03
*Apologies for the length of this post!!*

> **rem said:**
> You can have as many nodes you want and assign as many sublinks to them and to those sublinks other sub-sublinks. The same concept can be applied to an online store where there's a main product category like "Electronics" and under that other secondary categories like "TVs", "Computers", "Portable" and to each of these secondary categories other like TV -> Tube, Flatscreens, Plasma, etc, etc... and to Computers Desktops, Laptops, PDAs, etc, etc and to Portables, CD players, MP3 players, etc, etc .. and we can go even deeper :)Yep. That's the effect I imagined you were looking for. The approach I described doesn't limit the number of levels/etc. you can have.

Part of the trouble with systems like this is that you almost have to become an expert before you can even write a single line of code. If you're like me, you probably feel like you need to be in a position to anticipate every possible issue right from square one! Maybe this will help: Before you proceed, think about the sorts of things you're likely to want to do with your tree ...[LIST]
[*]Traversing it
[*]Finding the path to a node
[*]Reorganising it
[*]Etc.
[/LIST]By writing PHP functions that can perform these basic operations, and coding the rest of your application in terms of those functions, you should find it much easier to write a workable application. If, at some point, you discover a serious inefficiency, you will be able to address it by rewriting a single, self-contained function.

**Example:**

One major weakness in my suggested design is that it's hard to find the path to a node. This is always going to be a tough one! You could start by writing something like this:

```
/**
 * Returns false if the argument node is non-existent or an orphan.
 * Otherwise, returns the argument's path as an ordered list of tree nodes.
 */
function whereis($id) {
	$path=array();
	
	do {
		$node=mysql_fetch_assoc(mysql_query("SELECT * FROM element WHERE id=$id LIMIT 1"));
		if (!$node) return false;
		
		$parent=mysql_fetch_assoc(mysql_query("SELECT * FROM element WHERE id={$node['parentid']} LIMIT 1"));
		if (!$parent) return false;
		
		$path[]=$node;
		$node=$parent;
	} while ($parent['parentid']>=0);
	
	return $path;
}
```

As you can see, there is a mind-boggling number of SQL queries going on here. If it were  me, I would write it anyway, and trust that (provided my underlying design is sensible) I could figure out a more sensible alternative later. I could then replace this function, without impacting any of the rest of my code.

> **rem said:**
> I noticed though you used a *recursive* function which is not bad even though, as you stated too, I'm worried about the server load myself.Yep. Recursive functions are very easy to write, and can be very efficient.

> **rem said:**
> The next one would be the [**_Modified Preorder Tree Traversal_**]("http://www.sitepoint.com/article/hierarchical-data-database/2") method, which honestly I have hard times to comprehendTree traversal is always going to be heavy work :-( If I were writing this application myself, I think I would stick to the same basic DB structure, but after I'd gotten it working, I would set to work on making it more efficient.

**Example:**

Relational databases are never supposed to explicitly store information that can be inferred or calculated by another means. Given the *massive* pay-off, I would deliberately break this rule.

Imagine, for instance, if you could establish the full path to a tree node in a single query. For a node @ level 10, the snippet I concocted (above) would do it in about 20!! One solution would be to create a second, "optimised" element table, with an additional text field called "path". It would contain something like "17,32,1158,7" (ie the primary keys of the parent, it's parent, and so on). My "whereis" function could now be revised to calculate any path in two queries.

You would schedule a cron job that recalculated the optimised table every so often, to keep it up to date. The "whereis" function would fall back to the inefficient version of itself between updates.

```
function whereis($id) {
	$path=array();
	
	$node=mysql_fetch_assoc(mysql_query("SELECT * FROM element_optimised WHERE id=$id LIMIT 1"));
	
	// Efficient
	if ($node) {
		$sql="";
		$id_list=explode(',',$node['path']);
		foreach ($id_list as $i) $sql.=" OR id={$i}";
		$parents=mysql_query("SELECT * FROM element WHERE (".substr($sql,4).")");
		while ($parent=mysql_fetch_assoc($parents)) $path[]=$parent;
		
	// Inefficient
	} else {
		do {
			$node=mysql_fetch_assoc(mysql_query("SELECT * FROM element WHERE id=$id LIMIT 1"));
			if (!$node) return false;
			
			$parent=mysql_fetch_assoc(mysql_query("SELECT * FROM element WHERE id={$node['parentid']} LIMIT 1"));
			if (!$parent) return false;
			
			$path[]=$node;
			$node=$parent;
		} while ($parent['parentid']>=0);
	}
	
	return $path;
}
```

Unfortunately, I don't think it would be possible to implement pre/postorder traversal in the way the URL you posted describes. Its major failing seems to be that it assumes your tree will be static. In its "Food" diagram for example, you would have no way of adding a new item at "Yellow" or "Meat" without rewriting the entire database.

As a final example, it seems to me that this forum's database employs a techniques along the lines of what I just described ... deliberately redundant, cached data that goes stale, and gets refreshed at regular intervals.

---

### Post by kidders on 2007-02-03
> **rem said:**
> Your function works like a Swiss watch :) I'm impressed, very simple indeed!Haha! Well, thank you.

I've just noticed a flaw in my previous post's caching example. (Let's see if you spot it!)

I suppose the short version of that post is this:

If it were me, I would start by designing something simple & flexible. Then, I would reluctantly accept that some sort of caching is a necessary evil, and set about using it to make **big** efficiencies. Database tables that form part of your cache would contain redundant information designed to avoid having to look things up.

---

### Post by rem on 2007-02-03
Thanks a lot for your time,  I really appreciate it, these kind of posts are never too long! :)
After all, I think two tables is a decent solution to this and you may be right. Anyway, it sure worths to dig a bit into that too. Thanks a lot once again and have a good one! :)

And no... i didn't spot it :)

---

### Post by kidders on 2007-02-03
No problem. :-)

**Edit:** The flaw I mentioned is that my "efficient" path finder won't return node parents in the right order. It's easily solved though.

---

### Post by rem on 2007-02-03
> **kidders said:**
> No problem. :-)

**Edit:** The flaw I mentioned is that my "efficient" path finder won't return node parents in the right order. It's easily solved though.


Well, thanks a lot you didn't let me toil where the problem is. Anyway, now is my turn to get my hands dirty :)

---

### Post by kidders on 2007-02-03
I have one quick question:

How much data are we talking about here (ie how many tree nodes)? Less than 500? More than 10,000?

---

### Post by rem on 2007-02-03
This is for a custom CMS system I'm trying to develop. It'll be an OS project that I'm thinking about for the last few months. Don't want it to be big or anything it's just for having fun and gaining coding experience. I thought this is an opportunity to learn some cool stuff and maybe do something useful for others as well. I wanted to go beyond the 2 or 3 levels navigations I'm used with and provide a more flexible solution like Drupal does. Unfortunately this is a point where I got stuck big time but learning about it the hard way, hopefully it'll stick with me a while longer. The same solution might be implemented for a forum, online store, etc .. that's why I'm trying to get the best solution so to use it in my future codings as well.

---

