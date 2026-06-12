---
title: "Problem with PHP Arrays"
date: 2009-01-22
forum: Programming Talk
---

### Post by PartickThistle on 2009-01-22
The answer to this is staring me in the face - I know it - I've done it many times before.  I must have coders-block today. 

I have an array like this;

```

[0] => stdClass Object
   (
       [GroupName] => Benchmarking
       [GroupType] => Advisory Group
       [numGroups] => 1
   )

[1] => stdClass Object
   (
       [GroupName] => Communities Scotland Procurement Strategy Advisory Group
       [GroupType] => Advisory Group
       [numGroups] => 1
   )

[2] => stdClass Object
   (
       [GroupName] => Consultation on the National Strategy
       [GroupType] => Consultative Group
       [numGroups] => 2
   )

```

The database I'm pulling from is in a complete mess and there's no time to normalize it so it has to be PHP data manipulation;

Ideally I'm wanting the data to go into another array, pre-Smarty output that will output the data like so;

```

GroupType 
   GroupName (numGroups)
   GroupName (numGroups)

GroupType
   GroupName (numGroups)
   GroupName (numGroups)

etc
   etc
   etc

```

Any hints?

---

### Post by Tibuda on 2009-01-22
Try this. I'm assuming your current data is stored in $data[PHP]$types = array();
foreach ($data as $row) {
    if (!isset($types[$row->GroupType]))
        $types[$row->GroupType] = array();
    $text = $row->GroupName.' ('.$row->numGroups.')';
    $types[$row->GroupType][] = $text;
}[/PHP]EDIT: I just see your rows are objects, but my first code was using assoc arrays.

---

### Post by PartickThistle on 2009-01-22
Thanks very much, Daniel.

Got pretty much what I want now.

---

