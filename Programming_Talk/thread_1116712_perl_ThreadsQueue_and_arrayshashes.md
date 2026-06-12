---
title: "perl: Threads::Queue and arrays/hashes"
date: 2009-04-05
forum: Programming Talk
---

### Post by scragar on 2009-04-05
Long story short I want to insert a hash or array(doesn't matter which at this stage) into a Thread::Queue so that I can pull the whole array/hash out at a later time, I have tried a few things.
[php]my $temp = {
           'url'=>$1,
           'data'=>$2
     };
$mq->enqueue($temp);## Invalid value for shared scalar
##########################
my %temp = (
           'url'=>$1,
           'data'=>$2
     );
$mq->enqueue(%temp);## Adds 4 elements: 'url', $1, 'data', $2 
$mq->enqueue($temp);## Adds, but I can't work out how to get it back :(
##########################
my @temp = ($1, $2);
$mq->enqueue(@temp);## Adds each element independently 
[/php]
Anyone any clues? I need to keep the values I'm inserting together, keep locking $mq over and over again to keep the values together sounds like a really bad solution. Anyone got any better ideas or something I've missed?


EDIT: solved, I just need to pass by reference instead of attempting to pass the value.

---

