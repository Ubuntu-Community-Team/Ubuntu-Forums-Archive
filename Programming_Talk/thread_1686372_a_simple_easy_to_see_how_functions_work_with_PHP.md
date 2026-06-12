---
title: "a simple easy to see how functions work with PHP"
date: 2011-02-12
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-12
a simple easy to see how functions work with PHP
run it in the browser.
I know this is simple stuff but it took me a while to catch on. You dont need to define a var as global, just pass them into a function.

```
<?PHP
echo 'time is '.time().'<BR>';

$fileline = "mytest";
echo $fileline.'<BR><BR>';

if ($fileline == "mytest"){
  $test1 = help($fileline);

}

echo 'output from help function is -- '.$test1.'<BR><BR>';

$test2 = number2($test1);

echo 'output from number2 function is -- '.$test2.'<BR><BR>';







function help($fileline){
$fileline = $fileline. " first step into the first function";

//echo $fileline.'<BR>';
$fileline = $fileline. ", now modified by the first function";
//echo $fileline.'<BR>';
return $fileline;
}


function number2($test){
$fileline = $test. " first step into the second function";

//echo $fileline.'<BR>';
$fileline = $fileline. ", now modified by the second function";
//echo $fileline.'<BR>';
return $fileline;
}


?>
```

---

