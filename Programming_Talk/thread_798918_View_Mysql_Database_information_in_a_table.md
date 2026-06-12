---
title: "View Mysql Database information in a table"
date: 2008-05-18
forum: Programming Talk
---

### Post by saj0577 on 2008-05-18
Hey,

I have a mysql database with a table that has the info:
id
Caption
Url

And basically what I want to do is for it to load all the Urls(images) wth a caption below them, now I know how to do this. But how would I do it so it shows them in rows so for example the first 5 results on the top row then the next 5 on the next row etc etc.

Thanks in advance
Saj

---

### Post by dwhitney67 on 2008-05-18
There's probably some cute way to do this in MySQL, however in PHP, one could simply do something like:
[PHP]
...
$sql = "SELECT * FROM someDBTable;";
$res = mysql_query( $sql );

$dispResults = 0;

while ( $newArray = mysql_fetch_array( $res, MYSQL_ASSOC ) )
{
  $id      = $newArray[ 'id' ];
  $caption = $newArray[ 'caption' ];
  $url     = $newArray[ 'url' ];

  $buffer = sprintf( "%d, %s, %s", $id, $caption, $url );

  printf( "%s -- ", $buffer );

  $dispResults += 1;

  if ( $dispResults % 5 == 0 )
  {
    printf( "<br/>" );
  }
}
...[/PHP]

---

