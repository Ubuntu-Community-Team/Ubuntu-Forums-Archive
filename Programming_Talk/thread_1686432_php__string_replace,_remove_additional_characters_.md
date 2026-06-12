---
title: "php  string replace, remove additional characters after a match is found"
date: 2011-02-12
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-12
say I have this line of text
> =540 $aYes this is the text$bSome more text here

what I want back is this for output
Yes this is the text: Some more text here

what I want to do is to strip out the $ plus a single char afterwards
solved with this, can it be improved?

> <?
//use a backslash to escape the $ sign in PHP
echo time().'<BR>';
$fileline = "=450\\rrr \$aSun also {dollar}rises \$bSubtitle hemmingway";

$fileline = preg_quote($fileline , '/');

echo $fileline.'<BR><BR><BR>';


$stripp = Stripper($fileline);
//$stripp = STitle($fileline);

echo '<BR>function stripped<BR>'.$stripp.'<BR><BR>';
echo '<BR><BR><BR>';

function Stripper($fileline){          
    //'take it off of fileline, leave fileline1 intact
    //'get rid of =xxx type of number in front of string, leave $a etc... =700__$aSometext becomes $aSometext  
    $pos = strpos($fileline, "$");
    if ($pos == 0){return $fileline;}
    $fileline = substr($fileline,$pos); 
    //echo 'line'.$fileline.'<BR><BR><BR>';
    //'get rid of $a $b $c etc..., replace with  space " "    
    
    do {
    $pos = strpos($fileline, "$");
    If ($pos > -1) { 
       $Firstpart = substr($fileline, 0, ($pos + 0) );
       $Lastpart = substr($fileline, ($pos + 2));
       $fileline = $Firstpart. " " . $Lastpart;    
       }
    Else  {break;}
     }while ($pos !== FALSE); //not identical [http://www.php.net/manual/en/language.operators.comparison.php](http://www.php.net/manual/en/language.operators.comparison.php)
  
    //'look for {dollar} replace with '$', we dont want to see {dollar} in a field except for marcdata
    $fileline = str_replace ("{dollar\}","$",$fileline );

    //'stripslashes?
    $fileLine = stripslashes($fileLine);

    //'trim it up
    $fileLine = trim($fileLine);

    return $fileline;  
} // end of stripper

---

### Post by s.fox on 2011-02-13
Hello,

I had a little play and came up with a function, it might give you some ideas :)

```
<?php
function formatString($inputString){
//create array of $
$stage1 = explode('$',$inputString);
//don't need first array value
unset($stage1[0]);
foreach ($stage1 as $value){
    //create new array with values after 1st character
    $processedArray[] =  substr($value, 1);
}
//clear original array as no longer needed
unset($stage1);
//return array, correct formatting
return $processedArray;
}
//input string
$inputString = '=540 $aYes this is the text$bSome more text here';
//make function call
$result = formatString($inputString);
print_r($result);
?>
```I am not sure if it is efficient or not, but it is functionalised and can handle just about any string if it follows the input rules :)

-s.fox

---

### Post by sdowney717 on 2011-02-15
thanks, pretty cool to see the explode create the array.
every field and subfield uses the $ sign as a field designator.
this is actually what is called a MARC record field which is used in library automation.
A MARC file can be a compressed communications format or an expanded human readable file. 
Some of these schemes came about years prior before storage space was no longer an issue.

I wrote an automation program in VB6 for my wife's school and now am looking to webify it. PHP came to mind.

I have a programmer friend who suggested RUBY on RAILS.
But PHP seems to work for me so far.

---

### Post by sdowney717 on 2011-02-15
[http://www.loc.gov/marc/bibliographic/ecbdcntf.html](http://www.loc.gov/marc/bibliographic/ecbdcntf.html)

I never saw the practical need for all the subfield code definitions.
And they are extensive. For each MARC field = 500, =080 run from 001 to 999, etc... can contain many multiple subfield codes.
I also pondered how to make all the subfield coding relevant to a normal library user and it escapes me.
Is there any reasonable approach to organizing the data which could include subfield code designations? Which would be of any practical  benefit? If you could think of any, or a scheme to incorporate that into the db, let me know.

What I do is normalize the data into the primary numbered fields and strip out the subfield coding.
And then store the various striped data into various distinct fields in a MySql db. 

I made a first attempt at a searchable db using some of her data and put it here. I have some duplication in that db because I ran the same load script a couple of times.
[http://www.sdowney717.byethost16.com/mysearch2first.php](http://www.sdowney717.byethost16.com/mysearch2first.php)

I had to figure out how to use PHP to create the tables and then use PHP to read data out of a file and write it into a mysql db.


[http://discuss.joelonsoftware.com/default.asp?design.4.188811.5](http://discuss.joelonsoftware.com/default.asp?design.4.188811.5)
a little discussion on that was here and I find it funny but true what this fellow states.

> Stay away from MARC. Really. Import it, maybe store it in tables that mirror your actual, useful tables so that you can export it, but for the love of god don't try to work with it. MARC is a stinking morass of arbitrary data structures (and I use the term loosely) munged together and stomped on.
Eli Naeher Send private email
Wednesday, August 24, 2005
 


---

