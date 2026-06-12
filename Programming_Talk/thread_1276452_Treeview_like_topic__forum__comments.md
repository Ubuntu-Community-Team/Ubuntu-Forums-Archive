---
title: "Treeview like topic / forum / comments"
date: 2009-09-27
forum: Programming Talk
---

### Post by micdhack on 2009-09-27
I search the web for this kind of thing and even though i ve seen in dozen of times in websites i cant find a source that i could use.
So before im going off to start programming one all by myself i thought about asking if there is something like that or if i am using the wrong keywords to search for it.
So what exactly i want is a system that will print all replies of a topic not in a serial manner (which is one reply under the other) but in an treeview like manner. An example:

Hello i would like to watch the movie district 9, is it good? - user1
-Yes man it is good - user2
-No dude its not - user3
--Dude what do you know, you suck - user2
---mind your own business - user3
--user3 i dont aggree with you - user5
-I heard its a good movie - user4

---

### Post by januzi on 2009-09-27
You could take  a look at the: Rails Cookbook page 113 (forum with acts_as_nested_set)

---

### Post by micdhack on 2009-09-27
> **januzi said:**
> You could take  a look at the: Rails Cookbook page 113 (forum with acts_as_nested_set)

Yes but this is based on ruby. My website is written in php so it will be more usefull if i would have something that could be based on php/javascript system.
Sorry i should had specified this.

---

### Post by KIAaze on 2009-09-27
> **micdhack said:**
> Hello i would like to watch the movie district 9, is it good? - user1

Yes. :)

---

### Post by januzi on 2009-09-27
Table posts:
id - int autoincrement primary 
parent - int default 0
post - text 
created_at - date

Php:
```

$query = 'select * from posts' ;
$result = mysql_query( $query ) ;
while( $row = mysql_fetch_assoc( $result )) {
 $tab[$row['parent']][] = $row ;
}

function recursion( $parent, $depth, &$tab ) {
 foreach( $tab[$parent] as $key => $value ) {
   echo 'depth: '.$depth.'<br/>' ;
   print_r( $value ) ;
   recursion( $value['id'], $depth+1, $tab ) ; 
 }
}

recursion( 0, 0, $tab ) ;

```

Check this one, it should show records as a "tree" (depth + record data). Remember to insert some records to the table.

---

### Post by micdhack on 2009-09-29
Amazing i believe that should work. And do you have any ideas about the printing of the tables?
should i do it like a table inside another table with an extra column at the beggining to differenciate the depth?

---

### Post by januzi on 2009-09-29
It may be something like that:
```

for( $i = 0 ; $i < $depth ; $i++ ) echo '-' ;

```You could also use $depth as sign:
```
[FONT=monospace]
[/FONT]echo $depth.' ' ;[FONT=monospace]
[/FONT]echo $value_as_text ;
recursion( $value['id'], $depth.'-', $tab ) ; 

//...//
recursion( 0, '', $tab ) ;

```You could use $depth as width/margin:
```

$width = $depth*10 ;
echo '<p style="margin-left: '.$width.'px">'.$value_as_text.'</p>' ;

```
With tables there are one big problem: the more tables, the slower page.

---

### Post by chrisjsmith on 2009-09-29
Use nested UL / LI and wrap the content in a div inside the LI.  That is semantically correct and renders very fast in all browsers as it doesn't involve calculating column sizes and table nesting.

---

