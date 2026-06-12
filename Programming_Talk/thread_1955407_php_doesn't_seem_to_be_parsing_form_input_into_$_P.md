---
title: "php doesn't seem to be parsing form input into $_POST"
date: 2012-04-09
forum: Programming Talk
---

### Post by GodsMadClown on 2012-04-09
I'm having trouble with form data getting into multidimensional data structures on the latest 12.4 beta.  I also observe the same behavior on Suse Linux Enterprise, but not on CentOS.  What am I missing?

I can define one explicitly, demonstrated with $test_array in the code examples below, however I can't get the post data to populate a similar structure.

The following basic form works as expected, with the input text data getting put into the variables text1 ... text4 in the $_POST array.

```
<?php 

print_r($_POST);

$test_array = array ( 'test1' => array( 'test11' => 'test','test12' => 'test','test13' =>  array( 'test131' => 'test') ) );

print_r($test_array);
?>

<html>
<body>
<form action="samplepost.php" method="post">

First Name: <input type="text" id="fname" name="text1"></input>
<br/><br/>
Last name: <input type="text" id="lname" name="text2"></input>
<br/><br/>

text3: <input type="text" id="fname" name="text3"></input>
<br/><br/>
text4: <input type="text" id="lname" name="text4"></input>
<br/>

<br/>
<input name="submit1" type="submit" value="submit"></input>

</form>

</body>
</html>
```

but this doens't seem to work properly.  After I submit a filled form, the first piece of form data gets populated into the $_POST araray, but all the other ones are always missing.  I know the data is getting submitted, because the variable $inputdata gets populated in the example below.  Why isn't that input getting parsed into $_POST?

```
<?php 

$inputdata = file_get_contents( 'php://input' );
print_r($inputdata);
print_r($_POST);

$test_array = array ( 'test1' => array( 'test11' => 'test','test12' => 'test','test13' =>  array( 'test131' => 'test') ) );

print_r($test_array);
?>

<html>
<body>
<form action="samplepost.php" method="post">

First Name: <input type="text" id="fname" name="text1[fname]"></input>
<br/><br/>
Last name: <input type="text" id="lname" name="text1[lname]"></input>
<br/><br/>

text3: <input type="text" id="fname" name="text1[text3][text]"></input>
<br/><br/>
text4: <input type="text" id="lname" name="text1[text4][text]"></input>
<br/>

<br/>
<input name="submit1" type="submit" value="submit"></input>

</form>

</body>
</html>
```

---

### Post by generic41209 on 2012-04-15
Using your first set of code, and naming the file samplepost.php, so that it posts information to its-self the $_POST data is displayed nicely.

Maybe I need more information to understand your problem. Php version maybe too.

---

### Post by SeijiSensei on 2012-04-15
In the form, the text1 array has one dimension in the name part, but two dimensions in the "text" part.  Why is that?  I suspect the array needs to have the same dimensionality throughout.  

I've used both one- and two-dimensional arrays in forms, but never tried to mix them as you do here.

---

### Post by GodsMadClown on 2012-04-15
> **SeijiSensei said:**
> In the form, the text1 array has one dimension in the name part, but two dimensions in the "text" part.  Why is that?  I suspect the array needs to have the same dimensionality throughout.  

I've used both one- and two-dimensional arrays in forms, but never tried to mix them as you do here.
I can confirm that the code works in Centos and that it works in a patched version of Suse Linux Enterprise Server 11 SP2, using the php53 packages.  It actually fails in in a clean install of SLES 11 sp2 but, about a week ago, some updated PHP packages were published to the repo and upgrading to them resolved my issue.  Now the code examples above both work as expected.  

It's very possible that there have been some recent updates to PHP in 12.04 that have fixed this problem.  Our production servers run SLES, but I'd like to switch to Ubuntu for package selection and general responsiveness to bugs.

---

### Post by SeijiSensei on 2012-04-15
Frankly, I find it hard to believe the CentOS isn't responsive to bugs.  It's just recompiled RedHat, and they are certainly responsive to bugs, at least security bugs.  All my servers run CentOS; I only use Ubuntu on the desktop.

---

### Post by GodsMadClown on 2012-04-15
No, it's SLES that's not responsive to bugs.  Due to past political baloney, Centos is out.

---

