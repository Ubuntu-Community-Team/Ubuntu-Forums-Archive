---
title: "Fill html table from txt or xml file really slow!!! Please help?"
date: 2008-02-09
forum: Programming Talk
---

### Post by lucas4ce on 2008-02-09
Hi there, I have a ubuntu desktop 7.10 as a server with Apache2 and php5 on an old desktop computer.

I'm trying to read a file (txt or xml) into a variable array/object, then create an html table row for each element, filling each table row with certain children of the current element.

I started with a text file which has a string on each line, I then read each line into a multiimensional array using fgets(filename) and some looping.  This works fine.  Then iterating through the array I use echo to create a table row, and table cells filled with the information I want.  This also does what it should.

Things it takes about 15s to create the table.  Its not a problem with internet connection speed, it seems to be all happening too slowly on the server.

So I though I'd try it with an xml file.  I used the code I'd written above and changed it to output the xml structure I wanted in an html page.  I can then save the page as a .xml file.  In comparison this works in no time at all, less than a second.  So I'm think that the part of the code that reads the file and creates the array is fine.

Using this xml file I've done something very similar to using the text file above, it still works and fills the html table just fine, but still takes about 15s.  The code for this is below.

<?php
if (file_exists('file.xml'))
{
  $xml = simplexml_load_file('file.xml');
}
else
{
  exit('Failed to open file.xml.');				
}
$count=$xml->Count; //this element carries an integer with the number of 2ndElement's
$x=0;
$r=$xml->MainElement->2ndElement;
While($x<$count)
{
  echo '<tr id="somerow' . $x . '" onclick="somefunction(id)">';
  echo '<td class="somecell" >' . $r[$x]->someinfo1 . "</td>";
  echo '<td class="somecell" >' . $r[$x]->someinfo2 . "</td>";
  echo '<td class="somecell" >' . $r[$x]->someinfo3 . "</td>";
  echo '<td class="somecell" >' . $r[$x]->someinfo4 . "</td>";
  echo '<td class="somecell" >' . $r[$x]->someinfo5 . "</td>";			
  echo '<td class="somecell" >' . $r[$x]->someinfo6 . "</td>";
  echo '<td class="somecell" >' . $r[$x]->someinfo7 . "</td>";
  echo '<td class="somecell" >' . $r[$x]->someinfo8 . "</td>";
  echo "</tr>";
  $x++;
}
?>

The txt file is 46KB with 8371 lines.
The xml file is 165KB with 278 elements, each with 31 children.
The information being stored and read is either an integer, a small float, or a string no more than 15 characters long.

I have deduced from the quick speed of the xml creation code that its the table creation that is slowing things down, do you think I'm right?

15s seems very slow for what is really quite a small amount of simple information.  could it be a hardware issue with my server, is my code too inefficient?

Any help would be great!!

---

### Post by LaRoza on 2008-02-09
> **lucas4ce said:**
> 
15s seems very slow for what is really quite a small amount of simple information.  could it be a hardware issue with my server, is my code too inefficient?

Any help would be great!!

What is your hardware like? It is likely your code is inefficient (most code is).

You could try using a for loop, or not echoing everything until the end.

It might be better to use a database for this.

---

### Post by lucas4ce on 2008-02-09
Its a PII 350MHz with 256MB of ram.

Would a for loop be quicker than the while loop I'm using?

Would a MySql database speed this up?

Thanks.

---

### Post by hod139 on 2008-02-09
As suggested by LaRoza, what's the performance gain if you comment out all those echos?

---

### Post by lucas4ce on 2008-02-09
Sorry about this but what do you mean by comment out?

---

### Post by hod139 on 2008-02-09
I mean don't do the echo commands, just increment the counter.  If it still takes a very long time, then you have a better idea what the slow down is, meaning it isn't this loop.

---

### Post by pmasiar on 2008-02-09
> **lucas4ce said:**
> Its a PII 350MHz with 256MB of ram.


You try to run most recent ubuntu desktop AND apache web server on 256MB or RAM and slow CPU? IMHO RAM will be the bottleneck.

You may want to use some other GUI desktop with lesser requirements, like xubuntu. Or in plain commandline without any GUI.

---

### Post by lucas4ce on 2008-02-09
Ok sorry I see what you mean now.

I just tried taking this piece of code out of the webpage I'm building and ran it seperately with <html> and <body> tags to create a simple table and it runs in an instant. All 278 elements with their own information appear in a table with no apparent delay.  So it's not this bit of code?

If I comment out the echo's that create table cells and open the web page it opens the page in an instant too.

So on it's own the table is created with no delay, and inside my webpage the loop runs with no delay but the table creation takes 15s.

Could it be CSS that's slowing it down?

I'll look into that next...

Any ideas will be very much appreicated, thanks for your help so far!

---

### Post by LaRoza on 2008-02-09
CSS is applied by the client, not on the server.

Try storing the output in an array, then print the array that the end.

[http://ubuntuforums.org/showthread.php?p=4287313](http://ubuntuforums.org/showthread.php?p=4287313)

---

### Post by lucas4ce on 2008-02-09
I really hope it doesn't come to changing the desktop etc as I just started using linux and managed to get it all running.  But good point well made!!  I hope you're wrong:)

---

### Post by popch on 2008-02-09
Your program is doing much work within the innermost loop (i.e. once per data item) wich should be done exactly once for each table row:

  echo '<td class="somecell" >' . $r[$x]->someinfo1 . "</td>";

Try and assign $r[$x] to an intermediate variable. That should speed things up a bit.

---

### Post by lucas4ce on 2008-02-09
Ok stored it in an array and echo'd form the array, same result, took a long time to load.

I'm starting to think it may not all be the server, I'm viewing the webpage from a windows laptop with dual 3.4GHz processors and 2GB of ram.  When I open the webpage, and for the 15s or so that it takes to load, the CPU usage is steady at 50%.

If the table creation code on its own runs with no delay, then does it make sense that the delay must be caused by the Client?

---

### Post by LaRoza on 2008-02-09
> **lucas4ce said:**
> Ok stored it in an array and echo'd form the array, same result, took a long time to load.

I'm starting to think it may not all be the server, I'm viewing the webpage from a windows laptop with dual 3.4GHz processors and 2GB of ram.  When I open the webpage, and for the 15s or so that it takes to load, the CPU usage is steady at 50%.

If the table creation code on its own runs with no delay, then does it make sense that the delay must be caused by the Client?

The client is only getting a static page so it isn't that, try the advice above.

---

### Post by lucas4ce on 2008-02-09
Any clues on the intermediate variable?

---

### Post by popch on 2008-02-09
> **lucas4ce said:**
> Any clues on the intermediate variable?

why not 

```

intermediate_variable = $r[$x]

```

and later

```

  echo '<td class="somecell" >' . intermediate_variable->someinfo1 . "</td>";

```

I am not all that familiar with PHP, but it should be something like that.

---

### Post by lucas4ce on 2008-02-09
Still no luck I'm afraid, even tried putting it all in one echo, but no change.

Just out of interest can anyone tell me why my table can be created in a flash on its own, but takes so long when included in my webpage?  If it took as long on its own I'd understand that I need to limit the size of the table or something, but this is just confusing me.

I turned off the CSS sheet and it still took over 15s.

If it helps to know the loading bar for the webpage fills really quickly then seems to hang there for 15s or so before the page aprears or refreshes.

---

### Post by aks44 on 2008-02-09
This behaviour is quite strange...

What happens if you wrap your whole code between ob_start() / ob_end_flush()?
```
<?php
ob_start();

// code that currently takes 15s

ob_end_flush();
?>
```

---

### Post by popch on 2008-02-09
I am beginning to suspect (most reluctantly) your client. Try and save the HTML page on your client. Close your browser, Open it again and load the saved page. Is there any difference in the time taken to display the page?

---

### Post by LaRoza on 2008-02-09
Your computer (with the server) is slow, you can't expect too much.

---

### Post by lucas4ce on 2008-02-09
Actually I think I just found it, thanks for all your help by the way!!

I have some javascript for the webpage that formats this table using CSS, so that when I click on a row that row alone is highlighted, or when I click on a heading that column alone is highlighted.  This javascript currently iterates through the whole table five times to reformat it each time something is pressed.

I had this script urn on the onload even of the webpage.  If take it out the page loads in just over a second.

I think maybe I should give the formatting script another try :confused:

Sorry for leading everyone in the wrong direction.

Anyone know of a quicker way to highlight rows or columns using CSS?:oops:

---

### Post by LaRoza on 2008-02-09
> **lucas4ce said:**
> Actually I think I just found it, thanks for all your help by the way!!

I have some javascript for the webpage that formats this table using CSS, so that when I click on a row that row alone is highlighted, or when I click on a heading that column alone is highlighted.  This javascript currently iterates through the whole table five times to reformat it each time something is pressed.

I had this script urn on the onload even of the webpage.  If take it out the page loads in just over a second.

I think maybe I should give the formatting script another try :confused:

Sorry for leading everyone in the wrong direction.

Anyone know of a quicker way to highlight rows or columns using CSS?:oops:

How do you want it highlighted? I need the source to write the function do do this.

---

### Post by popch on 2008-02-09
> **lucas4ce said:**
> 

Anyone know of a quicker way to highlight rows or columns using CSS?:oops:

You could start by assigning each row a unique ID and each column a unique class. Highlighting all members of a class is straightforward and does not in itself require a script. Hightlighting a row should not be all that difficult once you know its ID.

---

### Post by LaRoza on 2008-02-09
> **popch said:**
> You could start by assigning each row a unique ID and each column a unique class. Highlighting all members of a class is straightforward and does not in itself require a script. Hightlighting a row should not be all that difficult once you know its ID.

The way I would do it:

Define the CSS for what you said, and use a script to assign the class and id attributes so the style is applied dynamically.

---

### Post by lucas4ce on 2008-02-09
At the moment I'm switching between a standard style and a clicked style to distinguish the selection.

---

### Post by lucas4ce on 2008-02-09
This is good!!

I have an ID for each row.  How do I assign a class to each column?

---

### Post by LaRoza on 2008-02-09
> **lucas4ce said:**
> This is good!!

I have an ID for each row.  How do I assign a class to each column?

You will have to apply it to each <td> in that column.

---

### Post by lucas4ce on 2008-02-09
Excellent thanks!!!

---

