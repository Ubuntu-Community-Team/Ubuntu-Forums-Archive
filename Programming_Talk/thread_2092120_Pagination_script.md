---
title: "Pagination script?"
date: 2012-12-06
forum: Programming Talk
---

### Post by TheodoreP on 2012-12-06
Hey there everyone, for sometime I've been trying to find a tutorial on how to create a dynamic paging script that will allow for me to use it multiple times within the same page without cluttering up the address bar. After completing an online course on AJAX, I believe that is probably the best language to use for this problem. Unfortunately I am still a green when it comes to programming and was wondering if anyone knew of any tutorials on how to accomplish this. Please try and keep in mind that I want a the simplest tutorial one can either find or create. If you would like to see the paging script I'm using now just say the word and I'll attach a tar ball.

Thanks for all your help and advice.

OK, I've decided to add the tar ball now. This should give you a little better idea of what I'm trying to get accomplished.

---

### Post by Dimarchi on 2012-12-08
Things needed to take care of when doing pagination. Other people are invited to improve and comment on this. Keeping things general, without looking at that tar ball.

A simple table of data example...23 entries (rows), 5 entries (rows) displayed per page. Counting starts at 0 (zero) index.

1. ) Calculate the number of entries to be displayed (23 in this case).
2.) Determine the number of entries displayed per page (5 in this case).
3.) Calculate how many pages would be displayed ( 23 / 5, so five...simply put, Math.ceil(23 / 5) in case of Javascript).

Page 1 would display rows 0-4 (five entries).
Page 2 would display rows 5-9 (five entries).
Page 3 would display rows 10-14 (five entries).
Page 4 would display rows 15-19 (five entries).
Page 5 would display rows 20-23 (four entries).

The thing is that you need to have the pagination script supply the starting and ending point, while taking care that pagination never goes below 0 and above the maximum number of entries to be displayed (23 in this example, where the last page displays only four entries since there are no more). Javascript pagination, PHP pagination, even SQL pagination (LIMIT being the key word there)...both should provide plenty of hits when searching, with code. Not all that clear, I admit it, from my cursory peek at some of the search results... :)

You could try to simulate this by making a function that prints those numbers per page. If you succeed in that, you have a working pagination script. A more generalized version of that function would be something like

```
function paginate(elem, start, end)
{
 // pagination code stuff
}
```Where elem is the element to which the pagination links should be generated to. Still a very limited version, as such. To make it less so, you would need to add something that return more varied sources of query for the pagination, say...

```
function paginate(elem, query, start, end)
{
 // pagination code stuff and the query page called with ajax
}
```Where query is the page the variable that changes according to the desired query (thinking in terms of database queries here, and query being, say, a PHP page that does SQL query to a database and returning values in a json format...different PHP pages do different queries and return different results).

Does this help at all?

---

### Post by TheodoreP on 2012-12-08
So, are you saying that I need to take my php pagination script and copy it into a JavaScript function?

---

### Post by Dimarchi on 2012-12-09
No...whether it is in PHP, Javascript, or some other language does not matter. The principles are the same.

---

### Post by TheodoreP on 2012-12-09
Ok, I still am not quite understanding, however I am determined to learning programming so, if you could please point in the direction of some really great tutorial sites for programming I would greatly appreciate it.

I thank you very much for your time and I really appreciate it.

---

### Post by Dimarchi on 2012-12-09
Programming in general? Or in some specific language?

For pagination, a Google search for pagination tutorial yields some results that - for me, at least - seem simple and to the point

[http://www.google.com/search?q=pagination+tutorial&ie=UTF-8&sa=Search&channel=fe&client=browser-ubuntu&hl=en](http://www.google.com/search?q=pagination+tutorial&ie=UTF-8&sa=Search&channel=fe&client=browser-ubuntu&hl=en)

Most of the are in PHP, with some Javascript in the form of jQuery (the first jQuery example appears to be more form over function, and the second more to the point). These probably in all likelihood result in that cluttering of address bar that you mentioned you wanted to avoid (GET, like the link above), for which AJAX is a good canditate in order to avoid it (POST).

---

### Post by Some Penguin on 2012-12-09
Approach depends on whether the results are stable or not (pages in a book are stable, searches into a real-time feed of editable content are not; the latter introduces some complexity if you're attempting to paginate through multiple requests, because results may be added or deleted or conceivably reordered), latency requirements, how much you expect users to need...

The /simplest/ case is where the content is strictly stable (no additions, removals, or reordering), and the user doesn't mind pagination take some additional time, and where you can easily search based on an offset -- such as a static database of pages in a book -- you can easily refer to pages by number.  In such a case, you could simply have each request specify the minimum and maximum, and use AJAX to make individual calls per page or set of pages.

Harder cases are where content is dynamically generated and much more difficult to compute for arbitrary offsets.  For instance, trying to find the 43,000th most relevant post to "centipedes" in a real-time Twitter feed -- that might be difficult without also identifying the 1st-42,999th most relevant posts, which means that if you're doing it naively you may do massive redundant computation (many requests) with a risk of duplicates or missing values (as the set of results or ordering thereof changes between queries) or a stupidly slow initial query (doing a single query for a massive range would 'solve' consistency issues, but makes that request suffer even if the user never needs to see past result 10).

---

### Post by TheodoreP on 2012-12-10
Need help debugging my allrecipes.inc.php file. I for some reason can't seem to see why my script is not counting the pages right. To give a little history of this script it is basically just a modified version of the dashboard.inc.php script. I will paste the dashboard.inc.php and allrecipes.inc.php scripts.

dashboard.inc.php
[PHP]
<?php

if (!isset($_SESSION['recipeuser']))
{
    echo "<h1>Welcome to SociableCooking</h1>\n";
    echo "<h3><font color='#BE2625'>\n";
    echo "SociableCooking is dedicated to getting your creative \n";
    echo "jucies flowing in the kitchen. We are here to inspire \n";
    echo "your kitchen creativity.\n";
    echo "</font></h3>\n";

    include_once("allrecipes.inc.php");
} else
{
    $user = $_SESSION['recipeuser'];
    // Code for displaying only the recipes of the current users 
echo "<h1>My Recipes</h1>\n";


$query = "SELECT count(recipeid) from recipes WHERE poster = '$user'";
$result = mysql_query($query);
$row = mysql_fetch_array($result);

if ($row[0] == 0)
{
    echo "No Recipes Have Been Posted \n";
    echo "<a href=\"index.php?card=newrecipe\">Post A Recipe</a>\n";
} else
{
    $totrecipes = $row[0];
if (!isset($_GET['page']))
    $thispage = 1;
else
    $thispage = $_GET['page'];
$recipesperpage = 5;
$offset = ($thispage - 1) * $recipesperpage;
$totpages = ceil($totrecipes / $recipesperpage);
$query = "SELECT * FROM recipes WHERE poster = '$user' ORDER BY recipeid DESC LIMIT $offset, $recipesperpage";
$result = mysql_query($query) or die('Could not retrieve recipes: ' . mysql_error());
while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    $recipeid = $row['recipeid'];
    $title = $row['title'];
    $poster = $row['poster'];
    $shortdesc = $row['shortdesc'];
    echo "<table width=\"95%\" cellpadding=\"0\" cellspacing=\"5\" border=\"0\" align=\"center\">\n";
    echo "<tr><td rowspan=\"3\"><img src=\"showimage.php?id=$recipeid\" width=\"80\" height=\"60\"></td>\n";
    echo "<td><a href=\"index.php?card=showrecipe&id=$recipeid\">$title</a></td></tr>\n";
    echo "<tr><td><font size=\"1\" color=\"#ff9966\">posted by: <em>Chef " . $poster . "</em></font></td></tr>\n";
    echo "<tr><td><p>" . $shortdesc . "</p></td></tr>\n";
    echo "<tr><td colspan=\"2\"><hr></td></tr>\n";
    echo "</table>\n";
}

    //    Paging on main page

if ($thispage > 1)
{
    $page = $thispage - 1;
    $prevpage = "<a href=\"index.php?card=dashboard&page=$page\">Previous</a>";
} else
{
    $prevpage = "Previous";
}
    $bar = "Sorry, you don't have any need for a paging bar. ";
    
if ($totpages > 1)
{
    for ($page = 1; $page <= $totpages; $page++)
    {
        if ($page == $thispage)
        {
            $bar .= " $page ";
        } else
        {
            $bar .= "<a href=\"index.php?card=dashboard&page=$page\">$page</a>";
        }
    }
}
if ($thispage < $totpages)
{
    $page = $thispage + 1;
    $nextpage = "<a href=\"index.php?card=dashboard&page=$page\">Next</a>";
} else
{
    $nextpage = "Next";
}
    echo "<table width=\"80%\" align=\"center\" cellspacing=\"5\" cellpadding=\"3\"><tr><td colspan=\"3\" align=\"center\">Page: <page>$thispage</page> of <page>$totpages</page></td></tr>
    <tr><td align=\"left\"><page>$prevpage</page></td><td align=\"center\"> <page>$bar</page> </td><td align=\"right\"><page>$nextpage</page></td></tr></table>";
}
}
?>
[/PHP]allrecipes.inc.php
[PHP]
<?php
/** This included file will allow people to browse the current recipe catalog
    before signing-up. They will be able to view every recipe in the
    catalog on the internet, but must sign-up or login to the site before
    they can post their recipes, edit them, comment on a recipe. As well 
    printing will not be a standard function unitl they sign-up or login.
**/
$query = "SELECT count(recipeid) FROM recipes";
$result= mysql_query($query);
$row   = mysql_fetch_array($result);

if($row[0] == 0)
{
    echo "<h1>Recipe Catalog</h1>\n";
    echo "No one has posted any recipes. Please use the registration form ";
    echo "to the right to register your free account. If you already have ";
    echo "an account please use the login form within the header bar ";
    echo "to post a recipe to the public catalog.\n";
}else
{
    echo "<h1>Recipe Catalog</h1>\n";

    $totrecipes = $row[0];
    if(!isset($_GET['page']))
        $thispage = 1;
    else
        $thispage = $_GET['page'];
        $recipesperpage = 3;
        $offset = ($thispage - 1) * $recipesperpage;
        $totpages = ceil($totpages / $recipesperpage);
        $query = "SELECT * FROM recipes ORDER BY recipeid DESC LIMIT
                $offset, $recipesperpage";
        $result = mysql_query($query) or die('Could not retrieve recipes: ' .mysql_error());
        while($row = mysql_fetch_array($result, MYSQL_ASSOC))
        {
            $recipeid = $row['recipeid'];
            $title    = $row['title'];
            $poster   = $row['poster'];
            $shortdesc= $row['shortdesc'];

            echo "<table width=\"95%\" cellpadding=\"0\" \n";
            echo "cellspacing=\"5\" border=\"0\" align=\"center\">\n";
            echo "<tr><td rowspan=\"3\"><img src=\"showimage.php?id=$recipeid\" \n";
            echo "width=\"80\" height=\"60\"></td>\n";
            echo "<td><a href=\"index.php?card=showrecipe&id=$recipeid\">\n";
            echo "$title</a></td></tr>\n";
            echo "<tr><td><font size=\"1\" color=\"#ff9966\">posted by: \n";
            echo " <em>Chef $poster</em></font></td></tr>\n";
            echo "<tr><td><p>$shortdesc</p></td></tr>\n";
            echo "<tr><td colspan=\"2\"><hr></td></tr></table>\n";
        }
    /** the code after this point is used to count up the total recipes inthe catalogand display 
        only four at a time with a pagination bar at the bottom if it's required.
    **/
    if($thispage > 1)
    {
        $page = $thispage - 1;
        $prevpage = "Previous";
    }else
    {
        $prevpage = "Previous";
    }
    $bar = "Sorry there are not  enough recipes in the catalog.";
    if($totpages > 1)
    {
        for($page = 1; $page <= $totpages; $page++)
        {
            if($page == $thispage)
            {
                $bar .= " $page ";
            }else
            {
                $bar .= "<a href=\"index.php?card=dashboard&page=$page\">$page</a>";
            }
        }
    }
    if($thispage < $totpages)
    {
        $page = $thispage + 1;
        $nextpage = "<a href=\"index.php?card=dashboard&page=$page\">Next</a>";
    }else
    {
        $nextpage = "Next";
    }
    echo "<table width=\"80%\" align=\"center\" cellspacing=\"5\" cellpadding=\"3\">\n";
    echo "<tr><td colspan=\"3\" align=\"center\">Page: <page>$thispage</page> of <page>$totpages</pages>\n";
    echo "<tr><td align=\"center\"><page>$prevpage</page></td>\n";
    echo "<td align=\"center\"> <page>$bar</page> </td>\n";
    echo "<td align=\"right\"><page>$nextpage</page></td></tr></table>\n";
}
?>
[/PHP]If anyone finds any bugs in my scripts please let me know about them. First thing though I really need to get the page counting system working properly.

---

### Post by TheodoreP on 2012-12-11
bug found and eradicated. Thanks for the help though.

---

