---
title: "Want to give input to executables of C files from php ."
date: 2013-01-01
forum: Programming Talk
---

### Post by rushikesh988 on 2013-01-01
I am trying to make online compiler using PHP which will compile the code given in the text box and show the output. here $souce is a code entered by user.right now the status is it can give the output without any input. is there is any way to link the inputs entered by the user in the text box to produce the output .


The code is
> <?php
require 'settings.php';
echo "<html>";
echo "<head>";
echo "<title>$site_title </title>";
echo "</head>";
echo "<body >";
echo " $header";
require 'header.php';
if(!empty($source)){
$filename=rand();
$file="$filename.c";
echo "<br>Click on filename to  download your file <a href=$file  >$file </a><br>";
$fp=fopen($file, "w");
$data=$_POST['source'];
fwrite($fp, $data);
fclose($file);
echo `gcc -o $filename $file 2> $filename.err `;
$ex=`gcc -o $filename $file ;echo $?`;
echo "<br>";
if ($ex==0)  //if source code is compiled without errors then $ex has 0 value.
	{   
	echo "your executable file is on <a href=$filename> $filename </a> <br>";
	$out= `./$filename`; 
	}
$ercc=  `cat $filename.err`;
$outnerr=$ercc . $out;

echo "<br/>";

echo "<form action=submit_c.php method= post >";
echo "Yours Source code is <br>";
echo "<textarea name=source1 cols=60 rows=20 readonly=readonly>$data</textarea><br>"; 
echo "And your output/error is ::: <br>";
echo "<textarea name=outnerr cols=60 rows=2 readonly=readonly>$outnerr</textarea><br>";

echo "</form> ";
}
else
echo "<strong>Please write something before compiling</strong><br>";

require 'footer.php';
echo "</body";
echo "</html>";
?>

---

### Post by Tony Flury on 2013-01-01
The normal way that c program's get input is either :
[LIST=1]
[*]Passed as command line arguments (Argc, argv
[*]Passed as one or more environment variables
[*]Passed as some sort of known config file
[/LIST]
It will depend on how the program you are executing has been written as to what sort of input you need to pass to it. 

Command line arguments would be the easiest to pass, but you would of course still have to write your program to do something with them.

The items on the form swill also be passed using the cgi interface  ( that uses environment variables I think on apache - it has been a while since I used  a C program as a web application)

---

### Post by Bachstelze on 2013-01-01
> **rushikesh988 said:**
> I am trying to make online compiler using PHP which will compile the code given in the text box and show the output.

This sounds like asking for trouble...

---

### Post by Tony Flury on 2013-01-02
> **Bachstelze said:**
> This sounds like asking for trouble...

I agree - I should have edited my reply with exactly that.

To rushikesh988 : 
How easy would it be to write a short C program that effectively does a "rm -rf /*", or launches a DOS attack from your server, Unless you are going to write some very intelligent parser to filter out **_all_** potential malicious code, then you could have a major problem on your hands.

One of the major causes of security problems on websites (and other applications) are bugs which allow for the execution of arbitrary code that is not in the control of the application writer or website developer  - i.e. code submitted by the users exploiting the bug. Given that those bugs are generally fixed as soon as they are found, it does seem odd to actually write a website which allows a user to do exactly that - i.e. write and execute software on your server which you have no control over.

---

### Post by rushikesh988 on 2013-01-06
> **Tony Flury said:**
> I agree - I should have edited my reply with exactly that.

To rushikesh988 : 
How easy would it be to write a short C program that effectively does a "rm -rf /*", or launches a DOS attack from your server, Unless you are going to write some very intelligent parser to filter out **_all_** potential malicious code, then you could have a major problem on your hands.

One of the major causes of security problems on websites (and other applications) are bugs which allow for the execution of arbitrary code that is not in the control of the application writer or website developer  - i.e. code submitted by the users exploiting the bug. Given that those bugs are generally fixed as soon as they are found, it does seem odd to actually write a website which allows a user to do exactly that - i.e. write and execute software on your server which you have no control over.
Thanks for the tip sir ..I didn't thought about that .
Its just that I am new to PHP and I am just making compiler for fun ...


I solved the problem 
as> $out= `cat $fileinput | ./$filename`; 
where fileinput is inputs given by user and filename is a file which has a code..

---

