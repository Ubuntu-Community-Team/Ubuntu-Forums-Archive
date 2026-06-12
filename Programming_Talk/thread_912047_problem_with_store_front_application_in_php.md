---
title: "problem with store front application in php"
date: 2008-09-06
forum: Programming Talk
---

### Post by Mia_tech on 2008-09-06
I'm having problem with the second page of the store front.... I'm getting this errors
-------------------------------------------------------------------------
Notice: Undefined variable: cat_id in C:\Inetpub\wwwroot\store\showitem.php on line 24

Notice: Undefined variable: item_id in C:\Inetpub\wwwroot\store\showitem.php on line 32
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'order by item_color' at line 1
---------------------------------------------------------------------------
here's the code, this is the second page, I've already posted the code for the first page of this store front
[PHP]<?php
//connect to database
$conn = mysql_connect("localhost", "root", "password") or die(mysql_error());
mysql_select_db("test",$conn)  or die(mysql_error());

$display_block = "<h1>My Store - Item Detail</h1>";

//validate item
$get_item = "select c.cat_title, si.item_title, si.item_price, si.item_desc, si.item_image from store_items as si left join store_categories as c on c.id = si.cat_id where si.id = $_GET[item_id]";
$get_item_res = mysql_query($get_item) or die (mysql_error());

if (mysql_num_rows($get_item_res) < 1) {
   //invalid item
   $display_block .= "<P><em>Invalid item selection.</em></p>";
} else {
   //valid item, get info
   $cat_title = strtoupper(stripslashes(mysql_result($get_item_res,0,'cat_title')));
   $item_title = stripslashes(mysql_result($get_item_res,0,'item_title'));
   $item_price = mysql_result($get_item_res,0,'item_price');
   $item_desc = stripslashes(mysql_result($get_item_res,0,'item_desc'));
   $item_image = mysql_result($get_item_res,0,'item_image');

   //make breadcrumb trail
   $display_block .= "<P><strong><em>You are viewing:</em><br><a href=\"seestore.php?cat_id=$cat_id\">$cat_title</a> &gt; $item_title</strong></p>
   <table cellpadding=3 cellspacing=3>
   <tr>
   <td valign=middle align=center><img src=\"$item_image\"></td>
   <td valign=middle><P><strong>Description:</strong><br>$item_desc</p>
   <P><strong>Price:</strong> \$$item_price</p>";

   //get colors
   $get_colors = "select item_color from store_item_color where item_id = $item_id order by item_color";
   $get_colors_res = mysql_query($get_colors) or die(mysql_error());

   if (mysql_num_rows($get_colors_res) > 0) {
        $display_block .= "<P><strong>Available Colors:</strong><br>";
        while ($colors = mysql_fetch_array($get_colors_res)) {
           $item_color = $colors['item_color'];
           $display_block .= "$item_color<br>";
       }
   }

   //get sizes
   $get_sizes = "select item_size from store_item_size where item_id = $item_id order by item_size";
   $get_sizes_res = mysql_query($get_sizes) or die(mysql_error());

   if (mysql_num_rows($get_sizes_res) > 0) {
       $display_block .= "<P><strong>Available Sizes:</strong><br>";

       while ($sizes = mysql_fetch_array($get_sizes_res)) {
          $item_size = $sizes['item_size'];
          $display_block .= "$item_size<br>";
       }
   }

   $display_block .= "
   </td>
   </tr>
   </table>";
}
?>
<HTML>
<HEAD>
<TITLE>My Store</TITLE>
</HEAD>
<BODY>
<? print $display_block; ?>
</BODY>[/PHP]

and here's the first page... the first page works just fine is when a link calls the second page that I get the errors avobe
[PHP]<?php
//connect to database
$conn = mysql_connect("localhost", "root", "password") or die(mysql_error());
mysql_select_db("test",$conn)  or die(mysql_error());

$display_block = "<h1>My Categories</h1>
<P>Select a category to see its items.</p>";

//show categories first
$get_cats = "select id, cat_title, cat_desc from store_categories order by cat_title";
$get_cats_res = mysql_query($get_cats) or die(mysql_error());

if (mysql_num_rows($get_cats_res) < 1) {
   $display_block = "<P><em>Sorry, no categories to browse.</em></p>";
} else {
   while ($cats = mysql_fetch_array($get_cats_res)) {
        $cat_id  = $cats['id'];
        $cat_title = strtoupper(stripslashes($cats['cat_title']));
        $cat_desc = stripslashes($cats['cat_desc']);

        $display_block .= "<p><strong><a href=\"$_SERVER[PHP_SELF]?cat_id=$cat_id\">$cat_title</a></strong><br>$cat_desc</p>";

        if (isset($_GET['cat_id']) && ($_GET['cat_id'] == $cat_id)) {
           //get items
           $get_items = "select id, item_title, item_price from store_items where cat_id = $cat_id order by item_title";
           $get_items_res = mysql_query($get_items) or die(mysql_error());

           if (mysql_num_rows($get_items_res) < 1) {
                $display_block = "<P><em>Sorry, no items in this category.</em></p>";
           } else {
                $display_block .= "<ul>";

                while ($items = mysql_fetch_array($get_items_res)) {
                   $item_id  = $items['id'];
                   $item_title = stripslashes($items['item_title']);
                   $item_price = $items['item_price'];

                   $display_block .= "<li><a href=\"showitem.php?item_id=$item_id\">$item_title</a></strong> (\$$item_price)";
                }

                $display_block .= "</ul>";
           }
       }
   }
}
?>
<HTML>
<HEAD>
<TITLE>My Categories</TITLE>
</HEAD>
<BODY>
<?php print $display_block; ?>
</BODY>
</HTML>[/PHP]

---

