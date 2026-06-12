---
title: "Shopping Cart - PHP/MySQL"
date: 2007-12-22
forum: Programming Talk
---

### Post by Jawahir on 2007-12-22
I'm working on a shopping cart at the moment and I'm stuck! My problem in a nutshell is this:

1. User clicks add_to_cart button from catalog page:>  "<a href=\"carttest.php?id=".$row['resource_id']."\">Add to cart</a><br><br>";

THIS part works FINE.

BUT once it directs to the carttest.php page I get this error:

> Parse error: parse error in c:\program files\easyphp1-8\www\farmsuperstores\carttest.php on line 9

The code for carttest.php page is this:

> <?

include ("mysqlconnect.inc.php");


$resource_id = $_POST['resource_id'];

// Check if a resource ID exists.
if (is_numeric [$resource_id]) {
// Set the page title and include the HTML header.
$pageTitle = 'Add items to the cart';
// Check if the shopping cart already contains 1 of the selected items.
if (isset ($_SESSION['resource_cart'][$resource_id])) {
$qty = $_SESSION['resource_cart'][$resource_id] + 1;
} else {
$qty = 1;
}
// Add the selected item to the shopping cart session variable.
$_SESSION['resource_cart'][$resource_id] = $qty;

} else { // Redirect
print "self.location='index.htm';" //Automatically redirects the user to the home page
exit();
}

// Check if the shopping cart is empty.
$empty = TRUE;
if (isset ($_SESSION['resource_cart'])) {
foreach ($_SESSION['resource_cart'] as $key => $value) {
if (isset($value)) {
$empty = FALSE;
}
}
}

?>


2. And the code to show the cart gives me the following error: 

> Notice: Undefined variable: empty in c:\program files\easyphp1-8\www\farmsuperstores\tmpdl7fltfvyg.php on line 3

Warning: Invalid argument supplied for foreach() in c:\program files\easyphp1-8\www\farmsuperstores\tmpdl7fltfvyg.php on line 8

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in c:\program files\easyphp1-8\www\farmsuperstores\tmpdl7fltfvyg.php on line 32


The code for this page is this:

> <?
// Display the shopping cart if it's not empty.
if (!$empty) {
include ("mysqlconnect.inc.php");

// Retrieve all the data for the items that exist in the shopping cart from the database.
$query = 'SELECT resource_id, name, purchase_price FROM resource WHERE resource_id IN (';
foreach ($_SESSION['resource_cart'] as $key => $value) {
$query .= $key . ',';
}
$query = substr ($query, 0, -1) . ')';
$result = mysql_query ($query);
// Put in some spaces.
echo '<br /><center><h1><em>Your Shopping Cart</em></h1></center><br />';
echo '<center><font face="Trebuchet MS">To remove an item from cart select the radio button and click \'Update
shopping cart\'</font></center><br />';

// Create a table and a form.
echo '<table border="1" bordercolor="#666666" width="80%" cellspacing="3" cellpadding="3" align="center">
<tr><td align="left" width="40%" bgcolor="#333333"><b><font color="#FFFFFF">Product Name</font></b></td>
<td align="center" width="10%" bgcolor="#333333"><b><font color="#FFFFFF">Purchase price</font></b></td>
<td align="center" width="10%" bgcolor="#333333"><b><font color="#FFFFFF">Qty</font></b></td>
<td align="center" width="10%" bgcolor="#333333"><b><font color="#FFFFFF">Total Price</font></b></td>
<td align="center" width="10%" bgcolor="#333333"><b><font color="#FFFFFF">Remove</font></b></td>
</tr><form action="showcarttest.php" method="post">';


// Print each item.

$total = 0; // Total cost of the order.

while ($row = mysql_fetch_array ($result, MYSQL_ASSOC)) {

echo "<input type=\"hidden\" name=\"resource_id\" value=\"{$row['resource_id']}\" />";

// Calculate the total and sub-totals.

$subtotal = $_SESSION['resource_cart'][$row['resource_id']] * $row['purchase_price'];

$total += $subtotal;

// Print the row.
echo " <tr>
<td align=\"left\" bgcolor=\"#CCCCCC\">{$row['name']}</td>
<td align=\"center\" bgcolor=\"#CCCCCC\">£{$row['purchase_price']}</td>
<td align=\"center\" bgcolor=\"#CCCCCC\"><input type=\"text\" size=\"3\"
name=\"qty[{$row['resource_id']}]\" value=\"{$_SESSION['resource_cart'][$row['resource_id']]}\" /></td>
<td align=\"center\" bgcolor=\"#CCCCCC\">£" . number_format($subtotal, 2) . "</td>
<td align=\"center\" bgcolor=\"#CCCCCC\"><input type=\"radio\" name=\"delete\"
value=\"{$row['resource_id']}\"></td>
</tr>\n";
} // End of the WHILE loop.

// Print the footer, close the table, and the form.
echo '<tr><td colspan="3" align="right" bgcolor="#999999"><b>Total:<b></td>
<td align="center" bgcolor="#999999">$' . number_format($total, 2) . '</td>
<td bgcolor="#999999">&nbsp;</td></tr></table><br />';

echo '<p align="center"><input type="submit" name="submit"
value="Update shopping cart" /></form></p><br />';
echo '<p align="center"><a href="confirm_order.php"><font face="Trebuchet MS"
size="+1"><b>Checkout</b></font></a></p>
<p align="center"><a href=catalog.htm><font face="Trebuchet MS" size="+1"><b>back to product
catalogue</b></font></a></p>';

// Put in some spaces.
echo '<p>&nbsp;</p>';
echo '<p>&nbsp;</p>';
echo '<p>&nbsp;</p>';
mysql_close(); // Close the database connection.

}

?>


PLEASE HELP ME! :(

---

### Post by Compyx on 2007-12-22
The first error message is about is_numeric(), is_numeric is a function so you need to put parenthesis(?) around the argument to is_numeric:
[php]
if (is_numeric($resource_id)) {
    /* do something */
}
[/php]

Repost your question using [ php ] tags around the php-code (without the spaces), that will make it less painfull to read. That way you'll probably get more responses.

PHP doesn't carry variables between scripts, so you need to pass $empty on the URL or store it in a session variable.

Another note: your html is horrible, use CSS and a proper DOCTYPE. At least provide an alternative to the "Ms Trebuchet" font, many people don't have this font installed. The code looks like it was generated by Frontpage, Dreamweaver or some other piece of crap.

Another serious mistake is using Fisher-Price OS ;)
> 
c:\program files\....


---

### Post by Majorix on 2007-12-22
Your code looks horribly pasted. Please see my sig for an explanation of this problem.

---

### Post by sunset_studies on 2007-12-22
> **Compyx said:**
> ...
Another serious mistake is using Fisher-Price OS ;)

I agree, if you're going to solicit help from an Ubuntu programming forum, at least have the decency to _pretend_ you're using Linux... :popcorn:

---

