---
title: "Shell Script to get data from CSV file"
date: 2008-10-15
forum: Programming Talk
---

### Post by Mbengi Bongi on 2008-10-15
Hi again guys,

How do I go about getting a shell script to read and display data from a *.csv file?

From my script I basically want to type the first entry of one of the rows and I want the script to display the rest of the row on differnt lines on the script e.g.

Line from file:
[COLOR="Blue"]01,Steven Smith,33,Midfield,12,2005 [/COLOR]

I type in **01** in my script and the display is:

[COLOR="Blue"]Newtown United Squad List

**Shirt Number** 01 [COLOR="DarkOrange"]//The 01 is the '01' I inputted//[/COLOR]

**Player Name: **     Steven Smith
**Age:  **                   33
**Position:**              Midfield
**Goals Scored:**     12
**Joined: **                2005
[/COLOR]

Any help would be appreciated! :(

---

### Post by stevescripts on 2008-10-15
Duh ... why not just go ahead and make a simple (sqlite, eg) database?

That said, google is your friend:

[http://www.savvyadmin.com/tag/shell-scripting/](http://www.savvyadmin.com/tag/shell-scripting/)

might be a good place to start.

Also, scripting languages such as Python, Tcl, and others have methods available to parse csv files.

Hope this helps a bit.

Steve

---

### Post by Reiger on 2008-10-15
Not in 'shell script' but in PHP:

to give you an idea:

[php]
<?php
/*
Quick hack to get the job done:
Usage:
php <script_name> <flags> <args>

Flags:
-t, -team, --team, --t:, etc. next argument is the name of the team, unless it's a flag;
-c, -csv, --csv:, --c:, etc. next argument is the name of the csv file to use, unless it's a flag.

If no csv argument is given, the script will prompt for one.
Use 'exit' or 'quit' to exit the script (gracefully - it should also work at a csv prompt);
Use 'clear' to get the screen cleared;
Type a number (number of the line of the csv file) to output the corresponding line in format;

*/
$key=0; 
$args=array();
if($_SERVER['argc']>1)
foreach($_SERVER['argv'] as $v) {
   if(preg_match('/--?c(sv)?:?/',$v))
    $key='csv';
   elseif(preg_match('/--?t(eam)?:?/',$v))
    $key='team';
   else
    $args[$key]=$v;
}

if(!isset($args['csv'])) { 
echo "Please enter the CSV file to use.".PHP_EOL; 
$number=trim(fgets(STDIN)); 
$csv=$number;
}
else
   $csv=$args['csv'];

$team= isset($args['team']) ? $args['team'] : $csv;

$lines= @ file($csv) or die("Unable to open file: '$csv'!".PHP_EOL); 
$number='';
while($number != 'exit' && $number != 'quit') { 
echo "Please enter a number to look up a player by his shirt number, or type 'quit' or 'exit' to quit. Use 'clear' to clear the screen.".PHP_EOL; 
$number=trim(fgets(STDIN)); 
if($number=='clear') 
   system('clear'); 
elseif(preg_match('/\d+/',$number)) { 
      foreach($lines as $line)
        if(preg_match("/^$number/",$line)) {
         $data=explode(',',$line);
         break; 
      }
      $header= isset($team) ? $team: $csv; 
      echo "From $header:".PHP_EOL, 
           "Shirt number: {$data[0]}".PHP_EOL.PHP_EOL, 
           "Player name:  {$data[1]}".PHP_EOL, 
           "Age:          {$data[2]}".PHP_EOL, 
           "Position:     {$data[3]}".PHP_EOL, 
           "Goals scored: {$data[4]}".PHP_EOL, 
           "Joined:       {$data[5]}".PHP_EOL; 
  } 
elseif(preg_match('/(qu|ex)it/',$number))
  echo "Done!".PHP_EOL;
else 
  echo "I don't understand this (it's not a number): $number".PHP_EOL; 
} 
?>
[/php]

---

### Post by Mbengi Bongi on 2008-10-15
I must admit I never contemplated using PHP Reiger, that looks pretty much what I'm needing.

How do I change the colour of the text on a php script?  I want the data to be a different colour from the headings.

Regards

---

### Post by mike_g on 2008-10-15
> I must admit I never contemplated using PHP Reiger, that looks pretty much what I'm needing.
[Sure.](http://ubuntuforums.org/showthread.php?t=947631):roll:

---

### Post by Reiger on 2008-10-15
Yes that's possible. It involves some trial & error to get it right (naturally), but basically you must substitute regular echo-statements with:
[php]
system("echo \"\033[33;44mThis text got fancy colours!\033[0m\"");
[/php]

Be aware that echo "something", "something_else" (which I use a few times in the script) will require a bit more work: either you can have a variable accumulate multiple strings:
[php]
$str="command";
$str="$str; command_two"; /* or use string concatentation like so:
$str= "command; "."command_two"; */
/* some more of the above */
system($str); // finally echo everything.
[/php]

Or issue a system() call for each of the "something"/"something_else" bits.

For reference: [http://www.faqs.org/docs/abs/HTML/colorizing.html](http://www.faqs.org/docs/abs/HTML/colorizing.html)
Note that the trick works slightly different in Ubuntu, for the difference: look to my example statement.

---

### Post by becatlibra on 2008-10-15
if you still want to use a shell script let me know - it would be EASY.

-Benjamin

---

### Post by ghostdog74 on 2008-10-15
> **Mbengi Bongi said:**
> Hi again guys,

How do I go about getting a shell script to read and display data from a *.csv file?

From my script I basically want to type the first entry of one of the rows and I want the script to display the rest of the row on differnt lines on the script e.g.

Line from file:
[COLOR="Blue"]01,Steven Smith,33,Midfield,12,2005 [/COLOR]

I type in **01** in my script and the display is:

[COLOR="Blue"]Newtown United Squad List

**Shirt Number** 01 [COLOR="DarkOrange"]//The 01 is the '01' I inputted//[/COLOR]

**Player Name: **     Steven Smith
**Age:  **                   33
**Position:**              Midfield
**Goals Scored:**     12
**Joined: **                2005
[/COLOR]

Any help would be appreciated! :(

if you want a shell script
```

IFS=","
while read shirtnum name age pos goals joined
do
  echo "Shirt num: $shirtnum"
  echo "Name: $name"
  
done<file

```
you can also use awk, which is most suitable for processing text files in the shell
```

awk -F"," '
{
 echo "Shirt num:" $1
 echo "Name: "$2
}
' file

```

In PHP, you can use fgetcsv function
```

<?php
$file = $argv[1];
$fh=fopen($file,"r");
while( $data = fgetcsv($fh,4096)) {
    echo "Shirt num: {$data[0]}\n";
    echo "Name: {$data[1]}\n";
}
fclose($fh);
?>

```

---

### Post by Mbengi Bongi on 2008-10-16
> **mike_g said:**
> [Sure.](http://ubuntuforums.org/showthread.php?t=947631):roll:

Not for use in the Command Line, I do want to use the same method on my web site for a different project, I didn't realise php could be run in the Terminal. :guitar:

---

### Post by Mbengi Bongi on 2008-10-16
> **ghostdog74 said:**
> if you want a shell script
```

IFS=","
while read shirtnum name age pos goals joined
do
  echo "Shirt num: $shirtnum"
  echo "Name: $name"
  
done<file

```
you can also use awk, which is most suitable for processing text files in the shell
```

awk -F"," '
{
 echo "Shirt num:" $1
 echo "Name: "$2
}
' file

```

In PHP, you can use fgetcsv function
```

<?php
$file = $argv[1];
$fh=fopen($file,"r");
while( $data = fgetcsv($fh,4096)) {
    echo "Shirt num: {$data[0]}\n";
    echo "Name: {$data[1]}\n";
}
fclose($fh);
?>

```

Wow, thanks for all your help so far guys, 
I am still looking to use Shell Script as well to give me more options, couple of questions to ask you:

**Reiger:**  How do I change the php script so it loads the *.csv file automatically instead of asking for it?

**Benjamin/Ghostdog**: Looks like** IFS** or probably **awk** is they key for the Shell Script method, as per my question to Reiger, how do I load the file?  Do I replace **'file** with the filename?

---

### Post by Reiger on 2008-10-16
Well currently, you just have to pass a commandline argument:

php script_name -c my_csv.csv

Example:
```

prometheus@Bartix:~$ php ttt.php **-c my_csv** -t foo
Unable to open file: 'my_csv'!
Done!
prometheus@Bartix:~$ 

```

Alternatively you may change the following code:
[php]
if(!isset($args['csv'])) { 
echo "Please enter the CSV file to use.".PHP_EOL; 
$number=trim(fgets(STDIN)); 
$csv=$number;
}
else
   $csv=$args['csv'];
[/php]

to:
[php]
if(!isset($args['csv'])) 
   $csv = 'path/to/some_file.csv'; // the (now) hardcoded csv file to use when no argument is given.
else
   $csv=$args['csv'];
[/php]

---

### Post by mssever on 2008-10-16
Be aware that not all of the examples posted in this thread parse CSV correctly. For example, many fail to account for records which include /,/, /\n/, and/or /"/.

---

### Post by Mbengi Bongi on 2008-10-16
> **Reiger said:**
> Well currently, you just have to pass a commandline argument:

php script_name -c my_csv.csv

Example:
```

prometheus@Bartix:~$ php ttt.php **-c my_csv** -t foo
Unable to open file: 'my_csv'!
Done!
prometheus@Bartix:~$ 

```

Alternatively you may change the following code:
[php]
if(!isset($args['csv'])) { 
echo "Please enter the CSV file to use.".PHP_EOL; 
$number=trim(fgets(STDIN)); 
$csv=$number;
}
else
   $csv=$args['csv'];
[/php]

to:
[php]
if(!isset($args['csv'])) 
   $csv = 'path/to/some_file.csv'; // the (now) hardcoded csv file to use when no argument is given.
else
   $csv=$args['csv'];
[/php]

Brilliant! Thanks very much Reiger, I've just tested it on my csv file and it works a treat, as does the info on color.

Just one last thing (assuming it's possible), how can, after a query,  can I add a dos-like pause function or press enter for example and ten the program exits to a shell script? 

I know how to do a 'pause' function in a shell script:

```

function pause(){ 
   read -n 1 -p "$*" 
   echo 

```

Is there anything similar in php? :confused:

---

### Post by Reiger on 2008-10-16
Well, as you can see: all you need to do is to add (one) line of code which listens (and waits) for user-input:

e.g.:

[php]
fgets(STDIN);
[/php]

So wherever you want the script to pause you can add the following code (it notifies the user to enter something as well)

[php]
echo "Press enter to continue".PHP_EOL;
fgets(STDIN);
[/php]

Since it makes no sense to do this anywhere but in the 'main' case, you'd change your (colour-ized equivalent) of:
[php]
elseif(preg_match('/\d+/',$number)) { 
      foreach($lines as $line)
        if(preg_match("/^$number/",$line)) {
         $data=explode(',',$line);
         break; 
      }
      $header= isset($team) ? $team: $csv; 
      echo "From $header:".PHP_EOL, 
           "Shirt number: {$data[0]}".PHP_EOL.PHP_EOL, 
           "Player name:  {$data[1]}".PHP_EOL, 
           "Age:          {$data[2]}".PHP_EOL, 
           "Position:     {$data[3]}".PHP_EOL, 
           "Goals scored: {$data[4]}".PHP_EOL, 
           "Joined:       {$data[5]}".PHP_EOL; 
  } [/php]

to:
[php]
elseif(preg_match('/\d+/',$number)) { 
      foreach($lines as $line)
        if(preg_match("/^$number/",$line)) {
         $data=explode(',',$line);
         break; 
      }
      $header= isset($team) ? $team: $csv; 
      echo "From $header:".PHP_EOL, 
           "Shirt number: {$data[0]}".PHP_EOL.PHP_EOL, 
           "Player name:  {$data[1]}".PHP_EOL, 
           "Age:          {$data[2]}".PHP_EOL, 
           "Position:     {$data[3]}".PHP_EOL, 
           "Goals scored: {$data[4]}".PHP_EOL, 
           "Joined:       {$data[5]}".PHP_EOL;
      echo "Press enter to continue".PHP_EOL; /* notify user; alternatively omit the echo statement. */
      fgets(STDIN); /* discard user-input; we just want to suspend the thread till the user wakes up. */
  } [/php]

---

### Post by Reiger on 2008-10-16
> **mssever said:**
> Be aware that not all of the examples posted in this thread parse CSV correctly. For example, many fail to account for records which include /,/, /\n/, and/or /"/.

Yeah, but they all correctly parse the example (which is representative for all input?) line given, right? ;)

---

### Post by Mbengi Bongi on 2008-10-16
It certainly manges to parse my csv file :)

Reiger, one last thing (sorry to be a pain!) your last advice was helpful again but how can I expand it to get the user to a) Press <Enter> to clear the screen and start again, or press <x> to exit (preferably to a shell script (menu.sh).

Again many thanks for your help!

---

### Post by Reiger on 2008-10-16
Try this instead (you still got to modify it to work with colours, but that's largely a copy/paste job):
[php]
<?php
/*
Quick hack to get the job done:
Usage:
php <script_name> <flags> <args>

Flags:
-t, -team, --team, --t:, etc. next argument is the name of the team, unless it's a flag;
-c, -csv, --csv:, --c:, etc. next argument is the name of the csv file to use, unless it's a flag.

If no csv argument is given, the script will prompt for one.
Use 'exit' or 'quit' to exit the script (gracefully - it should also work at a csv prompt);
Use 'clear' to get the screen cleared;
Type a number (number of the line of the csv file) to output the corresponding line in format;

*/
$key=0; 
$args=array();
if($_SERVER['argc']>1)
foreach($_SERVER['argv'] as $v) {
   if(preg_match('/--?c(sv)?:?/',$v))
    $key='csv';
   elseif(preg_match('/--?t(eam)?:?/',$v))
    $key='team';
   else
    $args[$key]=$v;
}

if(!isset($args['csv'])) { 
echo "Please enter the CSV file to use.".PHP_EOL; 
$number=trim(fgets(STDIN)); 
$csv=$number;
}
else
   $csv=$args['csv'];

$team= isset($args['team']) ? $args['team'] : $csv;

$lines= @ file($csv) or die ("Unable to open file: '$csv'!".PHP_EOL."Done!".PHP_EOL);
$number='';
$header= isset($team) ? $team: $csv;
while($number != 'exit' && $number != 'quit') { 
if($number=='clear') {
   system('clear;'); 
   $number='';
}
else {
echo "Please enter a number to look up a player by his shirt number, or type 'quit' or 'exit' to quit. Use 'clear' to clear the screen.".PHP_EOL; 
$number=trim(fgets(STDIN)); 
}
if(preg_match('/\d+/',$number)) { 
      foreach($lines as $line)
        if(preg_match("/^$number/",$line)) {
         $data=explode(',',$line);
         break; 
      }
      if(isset($data)) { 
      echo "From $header:".PHP_EOL, 
           "Shirt number: {$data[0]}".PHP_EOL.PHP_EOL, 
           "Player name:  {$data[1]}".PHP_EOL, 
           "Age:          {$data[2]}".PHP_EOL, 
           "Position:     {$data[3]}".PHP_EOL, 
           "Goals scored: {$data[4]}".PHP_EOL, 
           "Joined:       {$data[5]}".PHP_EOL; 
      }
      else
           echo "No match found for: '$number' in: '$csv'!".PHP_EOL;
      echo "Type anything but 'q', 'Q', 'X', 'x', 'exit' or 'quit' to continue after you hit enter. The aformentioned 'commands' allow you to exit this script instead.".PHP_EOL;
      $number=fgets(STDIN);
      $number= preg_match('/((qu|ex)it)|(x|q|Q|X)/',$number)>0 ? 'exit' : 'clear';
  } 
elseif($number !='quit' && $number!='exit')
  echo "I don't understand this (it's not a number): $number".PHP_EOL; 
}
echo "Done!".PHP_EOL; 
?>
[/php]
The key change is that only a prompt is given if $number != 'clear'; hence you could make the script have clear you the screen first (by changing the first occurence of $number=''; into $number='clear';).

To make it 'exit to' a shell script:
(a) Add a system() call to the end of the script which executes your script, or 
(b) have this script be executed from within your shell script. 
Either way should work (just fine).

---

### Post by Mbengi Bongi on 2008-10-17
Tried method (b) there Reiger and it works fine!

Thank you so very much, this is what I've been trying to achieve.

Cheers

:lolflag:

---

### Post by Mbengi Bongi on 2008-10-18
> **Reiger said:**
> Try this instead (you still got to modify it to work with colours, but that's largely a copy/paste job):
[php]
<?php
/*
Quick hack to get the job done:
Usage:
php <script_name> <flags> <args>

Flags:
-t, -team, --team, --t:, etc. next argument is the name of the team, unless it's a flag;
-c, -csv, --csv:, --c:, etc. next argument is the name of the csv file to use, unless it's a flag.

If no csv argument is given, the script will prompt for one.
Use 'exit' or 'quit' to exit the script (gracefully - it should also work at a csv prompt);
Use 'clear' to get the screen cleared;
Type a number (number of the line of the csv file) to output the corresponding line in format;

*/
$key=0; 
$args=array();
if($_SERVER['argc']>1)
foreach($_SERVER['argv'] as $v) {
   if(preg_match('/--?c(sv)?:?/',$v))
    $key='csv';
   elseif(preg_match('/--?t(eam)?:?/',$v))
    $key='team';
   else
    $args[$key]=$v;
}

if(!isset($args['csv'])) { 
echo "Please enter the CSV file to use.".PHP_EOL; 
$number=trim(fgets(STDIN)); 
$csv=$number;
}
else
   $csv=$args['csv'];

$team= isset($args['team']) ? $args['team'] : $csv;

$lines= @ file($csv) or die ("Unable to open file: '$csv'!".PHP_EOL."Done!".PHP_EOL);
$number='';
$header= isset($team) ? $team: $csv;
while($number != 'exit' && $number != 'quit') { 
if($number=='clear') {
   system('clear;'); 
   $number='';
}
else {
echo "Please enter a number to look up a player by his shirt number, or type 'quit' or 'exit' to quit. Use 'clear' to clear the screen.".PHP_EOL; 
$number=trim(fgets(STDIN)); 
}
if(preg_match('/\d+/',$number)) { 
      foreach($lines as $line)
        if(preg_match("/^$number/",$line)) {
         $data=explode(',',$line);
         break; 
      }
      if(isset($data)) { 
      echo "From $header:".PHP_EOL, 
           "Shirt number: {$data[0]}".PHP_EOL.PHP_EOL, 
           "Player name:  {$data[1]}".PHP_EOL, 
           "Age:          {$data[2]}".PHP_EOL, 
           "Position:     {$data[3]}".PHP_EOL, 
           "Goals scored: {$data[4]}".PHP_EOL, 
           "Joined:       {$data[5]}".PHP_EOL; 
      }
      else
           echo "No match found for: '$number' in: '$csv'!".PHP_EOL;
      echo "Type anything but 'q', 'Q', 'X', 'x', 'exit' or 'quit' to continue after you hit enter. The aformentioned 'commands' allow you to exit this script instead.".PHP_EOL;
      $number=fgets(STDIN);
      $number= preg_match('/((qu|ex)it)|(x|q|Q|X)/',$number)>0 ? 'exit' : 'clear';
  } 
elseif($number !='quit' && $number!='exit')
  echo "I don't understand this (it's not a number): $number".PHP_EOL; 
}
echo "Done!".PHP_EOL; 
?>
[/php]
The key change is that only a prompt is given if $number != 'clear'; hence you could make the script have clear you the screen first (by changing the first occurence of $number=''; into $number='clear';).

To make it 'exit to' a shell script:
(a) Add a system() call to the end of the script which executes your script, or 
(b) have this script be executed from within your shell script. 
Either way should work (just fine).


Reiger, how can I modify the script so it accepts text or numerical input?

Is it a case of changing **$number** to something like **$string** or **$text**?

Just to give me more options.

---

### Post by Reiger on 2008-10-18
$number is a string value -- at all times. I've called it $number because in the main case it will be a number used to look up the relevant CSV entry.

Where exactly/what do you need to make this distinction for? If I know how you intend to use various types of input/commands I may be able to give you a better idea of what & how it is possible.

---

### Post by Mbengi Bongi on 2008-10-18
I have a friend who wants to use the same script for his UK Railway station database.

Only he tells me every station has a 3 letter code and this is what he wants to enter in the same way I'm entering a shirt number.

A sample from his csv file is:

ABD, Aberdeen,First ScotRail, SR etc  

I can figure out changing the fields to more suitable headings for him, but inputting text didn't seem to work.

---

### Post by Reiger on 2008-10-18
That's because of:
[php]
if(preg_match('/\d+/',$number))
[/php]

This says: 'if $number contains a digit' (and actually, to be on the safe side it should've read 
[php]
if(preg_match('/^\d+$/',$number))
[/php]

Which means 'if $number consists of multiple digits, only'... I recommend applying this fix to your own script, btw....

But in the case of your friend you'd want something different there: if his 'codes' only permit the use of the characters A-Za-z, you just write:

[php]
if(preg_match('/^[A-Za-z]+$/',$number))
[/php]

If his codes may include numbers also, you can write:

[php]
if(preg_match('/^[A-Za-z0-9]+$/',$number))
[/php]

and if his case also should/may allow for underscores (_), you can shorten it to:

[php]
if(preg_match('/^\w+$/',$number))
[/php]

So that's a quick (one second job) solution there. ;) However, so you may better understand what all this does, I suggest you read up on [Regular Expression Patterns]("http://en.wikipedia.org/wiki/Regular_expression"), also known as Regular Expressions, or Regexes for short. These offer some really powerful, abstract text-manipulation tools. For their uses in PHP, google 'preg PHP', or 'Regular Expressions PHP'.

---

### Post by Mbengi Bongi on 2008-10-18
Sorted!

I had a feeling it was something to do with that Reiger, I just couldn't put my finger on it!

Thanks also for the link, I'm going to do some reading up on that.

Many thanks again :)

---

### Post by Mbengi Bongi on 2008-10-19
Reiger,

One thing I've discovered, how can I get PHP to display accented characters?

Is is a case of doing something like **charset=UTF-8**?

I've tried Googling it but there doesn't seem to be straight answer?

Thanks

---

### Post by mssever on 2008-10-19
> **Mbengi Bongi said:**
> Reiger,

One thing I've discovered, how can I get PHP to display accented characters?

Is is a case of doing something like **charset=UTF-8**?

I've tried Googling it but there doesn't seem to be straight answer?

Thanks
You need to know what the character set of your input is, then set PHP to handle that.

---

### Post by Mbengi Bongi on 2008-10-19
> **mssever said:**
> You need to know what the character set of your input is, then set PHP to handle that.

Don't mean to sound totally stupid, but how do I want to do that?

I need the Latin-Extended A Charset (as I need grave accents - à, è, ì, ò and ù) and UK locale.

Anyone?? :confused:

---

### Post by mssever on 2008-10-19
> **Mbengi Bongi said:**
> Don't mean to sound totally stupid, but how do I want to do that?

I need the Latin-Extended A Charset (as I need grave accents - à, è, ì, ò and ù) and UK locale.

Anyone?? :confused:
You need to know what character set your input is in. There's no way to determine this programmatically. Then you can use PHP's iconv functions to convert the strings to your output character set. If you use UTF-8, you'll have to check the various functions to make sure they're multibyte-character-safe. PHP has a series of functions with names beginning with mb_ but some non-mb_ functions might also work. PHP is a mess that way.

(If your input was generated in Ubuntu, there's a good chance that it's UTF-8, since that's Ubuntu's default.)

---

### Post by Mbengi Bongi on 2008-10-19
It is indeed UTF-8, and I am using Ubuntu (Hardy).

I just had a look at the PHP manual for **iconv** and am totally confused!

Do I have to "encode" each string individually or is there a way I can encode the whole script in one go?

---

### Post by mssever on 2008-10-19
If your input and output are both UTF-8, then make sure you're using multibyte-capable string functions throughout.

If you have to convert character sets, you have to convert each string, but you could convert it before doing anything else to you so you have only one string. You can also write a function to do your conversion for you, if appropriate.

I've never used PHP's iconv stuff myself, so I have no direct experience with how to use it.

---

### Post by Mbengi Bongi on 2008-10-19
OK, looks like I'm going to have to really look into this!

Thanks for the advice msserver!

---

### Post by Mbengi Bongi on 2008-10-19
> **becatlibra said:**
> if you still want to use a shell script let me know - it would be EASY.

-Benjamin

What would the Shell Script way be?  I gather **awk** or **IFS** would be used.

Regards

---

### Post by jjalocha on 2009-08-14
This [Wiki page]("https://help.ubuntu.com/community/Converting%20CSV%20to%20XML") might help. The [Python example,]("https://help.ubuntu.com/community/Converting%20CSV%20to%20XML#Python") for example, could easily be adapted for different purposes.

---

