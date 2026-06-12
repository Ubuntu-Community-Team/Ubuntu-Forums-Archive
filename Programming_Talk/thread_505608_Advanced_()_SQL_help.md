---
title: "Advanced (?) SQL help"
date: 2007-07-20
forum: Programming Talk
---

### Post by olejorgen on 2007-07-20
```

CREATE TABLE photo_tags (photo_id, tag_id);
CREATE TABLE photos (id, time, directory_path, name, description, default_version_id);
CREATE TABLE tags (id, name, category_id, is_category, sort_priority, icon);
```

I want to select all photos that's tagged with, say, **both** tag_id 6 and tag_id 13

This is what I've come up with:
```

select p.name from photos p where 
     6 in (select tag_id from photo_tags where photo_id = p.id)
and 13 in (select tag_id from photo_tags where photo_id = p.id);
```
1. Is this the correct way to do this? I couldn't really come up with many alternatives.
2. Is there any way to alias the inner query? ('(select tag_id from photo_tags where photo_id = p.id)')

This is f-spots database schema btw.

---

### Post by aks44 on 2007-07-20
```
SELECT p.name
FROM photos AS p INNER JOIN photo_tags AS pt ON (p.id=pt.photo_id)
WHERE pt.tag_id=6 OR pt.tag_id=13
```

Not sure it is anymore efficient though, only a query analysis can tell it for sure (on MySQL: EXPLAIN)

---

### Post by olejorgen on 2007-07-20
Thanks, but I think you missunderstood. I want the selected photos to be tagged with BOTH tags. (original post clearified)

---

### Post by aks44 on 2007-07-20
Sorry my bad, just replace the OR by a AND in the WHERE clause, then.

EDIT: please disregard that post :oops: I really misunderstood in the first place, and worsened my case by not thinking before posting the above comment. No way to get what you want using a INNER JOIN :oops:

---

### Post by tszanon on 2007-07-20
```
select p.*
from photos p, photo_tags pt
where p.id = pt.photo_id
and pt.tag_id = 6
and exists (select 'x' from photo_tags pt1 where pt1.photo_id = p.id and pt1.tag_id = 13);
```

Guess it works. :)

---

### Post by aks44 on 2007-07-20
What about

```
SELECT name FROM photos
WHERE id IN
  (SELECT photo_id
   FROM photo_tags
   WHERE tag_id=6 AND tag_id=13
  )
```

You could replace the inner WHERE ... AND ... clause by a WHERE tag_id IN(...) if needed.

---

### Post by tszanon on 2007-07-20
> **aks44 said:**
> What about

```
SELECT name FROM photos
WHERE id IN
  (SELECT photo_id
   FROM photo_tags
   WHERE tag_id=6 AND tag_id=13
  )
```

You could replace the inner WHERE ... AND ... clause by a WHERE tag_id IN(...) if needed.

The nested SELECT won't return any rows, because there isn't any row where tag_id is both 6 and 13.

You could also do it this way:
```
select p.*
from photos p, (select photo_id from photo_tags where tag_id = 6) pt1, (select photo_id from photo_tags where tag_id = 13) pt2
where p.id = pt1.photo_id
and pt1.photo_id = pt2.photo_id;
```

---

### Post by olejorgen on 2007-07-20
```
select p.*
from photos p, (select photo_id from photo_tags where tag_id = 6) pt1, (select photo_id from photo_tags where tag_id = 13) pt2
where p.id = pt1.photo_id
and pt1.photo_id = pt2.photo_id;
```
Yeah, that was how I did it first. Still very ugly when you add many tag requirements :-/

I also tried the impossible tag_id = 6 and tag_id = 13 ^^

If this worked it would be neat:
```

select p.name from photos where
(6, 13) subsetof (select tag_id from photo_tags where p.id = photo_id)
```

---

### Post by tszanon on 2007-07-20
> **olejorgen said:**
> If this worked it would be neat:
```

select p.name from photos where
(6, 13) subsetof (select tag_id from photo_tags where p.id = photo_id)
```
I have never heard of any SQL function that would do that. It would really save a lot of time.

---

### Post by olejorgen on 2007-07-21
I know. I tried this too (essensially the same), but no luck (on sqlite)
```

select p.name from photos where
(6, 13) = (select tag_id from photo_tags where p.id = photo_id intersection (6, 13))
```

---

### Post by winch on 2007-07-21
Perhaps,

```

select name from photos where id in (select photo_id from photo_tags where tag_id in (6, 13);

```

---

### Post by tszanon on 2007-07-21
> **winch said:**
> Perhaps,

```

select name from photos where id in (select photo_id from photo_tags where tag_id in (6, 13);

```
The nested SELECT will return all photos that have the tags 6 or 13, not those that have both tags.
At the moment, I don't see any other alternative to do what the original post wants.

Good luck!

---

### Post by olejorgen on 2007-07-21
Yeah, I guess I'll just use it. It seems kinda strange that it's not a better way. I'd assume this kind of problem pops up fairly often

---

### Post by winch on 2007-07-21
> **tszanon said:**
> The nested SELECT will return all photos that have the tags 6 or 13, not those that have both tags.

Opps.

You could also do this,

```

select name from photos where id in(select photo_id from (select photo_id, count(*) as count from photo_tags where tag_id in (6, 13) group by photo_id) where count = 2);

```

That will work as long as the photo_tags table doesn't have duplicate rows.

---

