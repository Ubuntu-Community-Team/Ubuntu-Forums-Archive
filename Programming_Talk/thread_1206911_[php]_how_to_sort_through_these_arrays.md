---
title: "[php] how to sort through these arrays?"
date: 2009-07-07
forum: Programming Talk
---

### Post by ELD on 2009-07-07
Okay please do bear with me this is hard to explain.

Firstly say i have these two arrays
```

Array
(
    [15] => Array
        (
            [0] => 18
            [1] => 15
        )

    [16] => Array
        (
            [0] => 17
            [1] => 19
            [2] => 16
        )

)

Array
(
    [18] => Array
        (
            [topic_id] => 1
            [forum_id] => 18
            [title] => sdfdsf
        )

)

```

And say i am currently doing a loop where lets say $id has gotten to "15". As you can see the first array with "15" has "15" and "18" in it.

The second array has "18".

What i want is to be able to pick that up, so then i can use the information like "title" and "topic_id".

Any help on how to do that would be great!

---

### Post by Reiger on 2009-07-07
I don't understand your problem at all, much less why the array keys should have such nondescript values...

But am I right in thinking that you are probably given a ton of help alone in saying how you can query for the array keys in a given array? Hint: array_keys($array) results in an array of keys of $array.

Combine that with in_array() and you can find whether or not a key also exists as value inside some (other) array.

---

### Post by ELD on 2009-07-07
Like i said it is hard to explain. The values are perfectly descriptive for what they are needed for.

I will try to explain again.

The first arrays keys "15" and "16" are the id's of top level forums, inside are those are forums ids + their child forums, so "15" has a child forum of "18".

The second array is a load of topics found via sql from the forums.

While i am looping through the forums i am getting a last post information for each top level forum from their forums and their subforums (top levels being "15" and "16").

And so we can see the second array has a topic from forum "18" which is a subforum of "15".

When looping through the forums say it hits forum id "15" i want it to find any topics from the second array where the number is equal to any in the "15" array, which it will be since that has "15" and "18".

Very confusing i know.

Using the function you supplied above i have gotten near on where i need to be:
```

Array
(
    [18] => Array
        (
            [topic_id] => 1
            [forum_id] => 18
            [title] => sdfdsf
        )
)
Array (     [0] => 18     [1] => 15 ) 

```

I need to see if the second array numbers 18 or 15 are in the first one, which they are, i'm so close!

---

### Post by Reiger on 2009-07-07
OK. So all you have to do (now you have the output-that-is-nearly-there) is to check whether or not something isset() ?
[php]
/* $data =  the `first' array,
 * $forumIDs = the `second' array
 */
foreach($forumIDs as $forumID) {
  if(isset($data[$forumID])) {
    // do something?
  }
}
[/php]

---

