---
title: "How to insert a variable into a variable name in PHP?"
date: 2017-01-20
forum: Programming Talk
---

### Post by m5rc on 2017-01-20
I'm trying to place a variable within another, and it doesn't seem work--PHP complains about an unexpected dollar sign in the array. What's the best way to do this? Thanks.

```

$i = 1;
while ($i < 5) {
  if (count(image_array_$i)) {
    foreach ($image_array_$i as $img) {
      // image operations
    }
  }
  $i++
}

```

---

### Post by SeijiSensei on 2017-01-20
Shouldn't 
```
if (count(image_array_$i))
```
be
```
if (count(**$**image_array_$i))
```

---

### Post by spjackson on 2017-01-21
If you really have four variables, $image_array_1, $image_array_2, $image_array_3, $image_array_4, then wouldn't it make sense for image_array to be a 2-dimensional array and then reference each array as $image_array[$i]?

---

### Post by Olav on 2017-01-21
This is how:
```

$i = 1;
while ($i < 5) {
  if (count(${"image_array_$i"})) {
    foreach (${"image_array_$i"} as $img) {
      // image operations
    }
  }
  $i++;
}

```
... but I agree that it is an ugly hack, I hate the fact that PHP even makes this possible and you should really use a twodimensional array.

---

### Post by m5rc on 2017-01-21
Thanks everybody. I see how it's a pretty ugly hack. I'm using a content management system API, where there are 3 image fields (the arrays) which can contain multiple image objects, each with their own methods and variables like $img->size(640,480) and $img->description. So I need to iterate on those individual images within these 3 discrete fields (arrays). The CMS already created the data structures for me and I need to use its API. I thought it might be easy to do something like this variable-within-variable so I don't have to duplicate my HTML markup in the render function I'm writing. If you see a better way to do this based on what I just said, let me know :-)

---

### Post by Olav on 2017-01-21
> **m5rc said:**
> If you see a better way to do this based on what I just said, let me know :-)
I am not sure I understand quite how to imagine your "image fields (the arrays)". Do you have some code that you can show?

---

### Post by SeijiSensei on 2017-01-22
So does each item have an array of key/value pairs so that this code makes sense
```

$thisimage=array("description"=>"some description","size"=>"640x480", etc.);
$image[$i]=$thisimage;

```
That creates a two-dimensional array $image indexed by $i where each value of $image is itself another array of image characteristics.  Then $image[$i]['description'] will return "some description" while $image[$i]['size'] returns "640x480".  Does that make any sense in the context of your application?

---

