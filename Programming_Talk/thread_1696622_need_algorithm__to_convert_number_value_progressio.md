---
title: "need algorithm  to convert number value progression"
date: 2011-02-27
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-27
looking for an algorithm

originally I thought this BUT
I need to take in a number from 
1 -> 20 and return 1
21 -> 40 and return 2
41 -> 60 and return 3
61 -> 80 and return 4

etc....

I really need it like this

1 -> 20 and return 1
21 -> 40 and return 21
41 -> 60 and return 41
61 -> 80 and return 61

---

### Post by sdowney717 on 2011-02-27
Any way this can be improved?

[PHP]this works
I can increment every 20, and there will never be more than 10,000 record count
  $count = 1;
  while ($count <= 10000)
     {   
     if (($rpos>=$count) and ($rpos<($count+20))){$dum = $count;break;}  
     $count =($count +20);
     }

  echo 'weirdcounter'.$dum.'<BR>';[/PHP]

---

### Post by NovaAesa on 2011-02-27
Unless I'm not understanding what the problem is, why don't you just divide the input by 20 (using integer division), then add 1 to the result of the division?

---

### Post by lisati on 2011-02-27
> **NovaAesa said:**
> Unless I'm not understanding what the problem is, why don't you just divide the input by 20 (using integer division), then add 1 to the result of the division?

That's similar to what I was thinking, i.e. divide by 20.0, add 0.9, and keep only the integer part of the result.

---

### Post by sdowney717 on 2011-02-28
Thanks for the help

On one page, I display a series of records in 20 record blocks, with pagination.
Basically, every next, previous, etc... shows another 20 record set.
I create a link displayed with each record based on the record number which is part of each record.
Click that it loads another page which displays just that one record.
On that page I move forward or back one record at a time.
SO, when I post back to the first page that displays the 20 record set, I needed to figure out which set of 20 records to display.

I modified what the algorithm  needs to this
I need to take in a number from
1 -> 20 and return 1
21 -> 40 and return 21
41 -> 60 and return 41
61 -> 80 and return 61

etc.... 

so if your displaying record number 15, it posts back to block of records starting at 1 running to 20

so if your displaying record number 25, it posts back to block of records starting at 21 running to 40

---

### Post by Tony Flury on 2011-02-28
> **sdowney717 said:**
> Thanks for the help

On one page, I display a series of records in 20 record blocks, with pagination.
Basically, every next, previous, etc... shows another 20 record set.
I create a link displayed with each record based on the record number which is part of each record.
Click that it loads another page which displays just that one record.
On that page I move forward or back one record at a time.
SO, when I post back to the first page that displays the 20 record set, I needed to figure out which set of 20 records to display.

I modified what the algorithm  needs to this
I need to take in a number from
1 -> 20 and return 1
21 -> 40 and return 21
41 -> 60 and return 41
61 -> 80 and return 61

etc.... 

so if your displaying record number 15, it posts back to block of records starting at 1 running to 20

so if your displaying record number 25, it posts back to block of records starting at 21 running to 40


Try : 
StartofPage = (INT(CurrentRecord/20) * 20) + 1

---

### Post by sdowney717 on 2011-03-01
Thanks, but it has a problem.

StartofPage = (INT(CurrentRecord/20) * 20) + 1 

If you try 20 with that, it returns 21 but should be 1

records 1 thru 20 need to return 1
records 21 thru 40 need to return 21

If you try 40 with that, it returns 41 but should be 21

I can see it is close.

this might work
StartofPage = (INT(CurrentRecord/21) * 20) + 1

oops, no fails on 101
101 should return 101 but gives 81

---

### Post by Tony Flury on 2011-03-01
> 
records 1 thru 20 need to return 1
records 21 thru 41 need to return 21

Um - shouldn't that be 21 thru 40 need to return 21 ?
and then 41 to 60 to return 41 ?

if so then : 
CurrentPage = ((CurrentRecord -1)/20)+1
StartPage = ((CurrentPage-1)*20)+1

Or to simplify : 
StartPage = (((CurrentRecord-1)/20)*20)+1

---

### Post by sdowney717 on 2011-03-01
thanks, I fixed my post.

OK, this does seem to be working:P
I broke it into 3 steps to see it working
> 
$dum = (($rpos-1)/20) ;
$dum = (int)($dum);
$dum = (($dum *20) +1);


---

