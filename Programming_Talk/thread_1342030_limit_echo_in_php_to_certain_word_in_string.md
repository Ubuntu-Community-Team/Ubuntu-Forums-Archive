---
title: "limit echo in php to certain word in string"
date: 2009-11-30
forum: Programming Talk
---

### Post by esteeven on 2009-11-30
Hello

I am a bit stuck with a php problem. I have a string of text that can be of a variable length eg

" Large and luxurious 5th floor 2 bed furnished apartment in a fantastic historic building close to the City Centre and Waterfront.

More details and 8 photos
Save property
Contact agent "

The text in the first 2 lines can be variable in length. The "More details... etc" is standard text. I want to display my string up to, but not including, the word "More."

I am looking (I think) for something like :

echo $mystring (up to the word "More") << this is the bit I can't work out.

Thanks

---

### Post by 0cton on 2009-11-30
[http://php.net/manual/en/function.strpos.php](http://php.net/manual/en/function.strpos.php)
[http://php.net/manual/en/function.substr.php](http://php.net/manual/en/function.substr.php)
Should be enough for you.

---

### Post by esteeven on 2009-11-30
I should have been clearer. I am taking the text string from another page using :

$content = file_get_contents('http://www.......);

I have then (somehow :) ) managed to get the text string I want using :

$start_pointer = strpos($content, '<ol id="summaries"');
$end_pointer = strpos($content, '</ol>', $start_pointer);
$properties_content_length  = $end_pointer - $start_pointer;
$properties = substr($content, $start_pointer, $properties_content_length);



$property_list = explode('<li class="regular',$properties);


$property_nbr = count($property_list);
echo '<li class="';

echo strip_tags($property_list[ rand(1, $property_nbr)-1], '<p><img><li><span><div><h2>');

This works fine, except that I want to limit the "echo $property_list" to a certain word eg the "More" in my string below.



" Large and luxurious 5th floor 2 bed furnished apartment in a fantastic historic building close to the City Centre and Waterfront.

More details and 8 photos
Save property
Contact agent "

Where do I insert the strpos and substr ?

---

### Post by cdenley on 2009-11-30
You want to print everything up until the word "More" appears?
[PHP]
$mystr=strip_tags($property_list[ rand(1, $property_nbr)-1], '<p><img><li><span><div><h2>');
$index=strpos($mystr,"\nMore");
if($index===false)
   echo "\"More\" is not in the string at the beginning of a line";
else
   echo substr($mystr,0,$index);
[/PHP]

Or do you simply want the first line?
[PHP]
$mystr=strip_tags($property_list[ rand(1, $property_nbr)-1], '<p><img><li><span><div><h2>');
$lines=explode("\n",$mystr);
echo $lines[0];
[/PHP]

---

### Post by esteeven on 2009-11-30
$home_properties=strip_tags($property_list[ rand(1, $property_nbr)-1], '<p><img><li><span><div><h2>');
$lines=explode("More details",$home_properties);
echo $lines[0]; 

EXCELLENT! Many thanks!! And it's a solution that I actually understand.

---

