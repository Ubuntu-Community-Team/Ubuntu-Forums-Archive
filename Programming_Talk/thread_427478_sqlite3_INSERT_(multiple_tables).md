---
title: "sqlite3 INSERT (multiple tables)"
date: 2007-04-29
forum: Programming Talk
---

### Post by gunksta on 2007-04-29
HI,

I am trying to insert some data into a sqlite3 database. I can't figure out how to do the insertion, because it's kinda weird, and I hope someone here can help me figure this out. I want to move my F-Spot tags from F-Spot to Digikam. 

I know I could do this with exiv2, but I have decided this "problem" gives me an excuse to learn more about SQL. Thus, my solution *must* be a SQL solution, for educational type reasons.

I have pulled my information out of F-Spot's database. Multiple table SQL queries are easy. I can use regular expressions magic to reformat the f-spot info into the type of info digikam needs. So, I'm almost ready to rock and roll.

Digikam has indexed all of my photos, and I reproduced my tag structure in Digikam. Now all I need to do is to re-associate photos with tags. Therein lies my problem. I can't figure out how to do this.

Digikam has 3 databases I have to work with. I have provided all of the relevant information on each database below.

**Tags**
```
CREATE TABLE Tags
 (id INTEGER PRIMARY KEY,
  pid INTEGER,
  name TEXT NOT NULL,
  icon INTEGER,
  iconkde TEXT,
  UNIQUE (name, pid));
CREATE TRIGGER delete_tag DELETE ON Tags
BEGIN
  DELETE FROM ImageTags WHERE tagid=OLD.id;
END;
CREATE TRIGGER delete_tagstree DELETE ON Tags
BEGIN
 DELETE FROM Tags
   WHERE id  IN (SELECT id FROM TagsTree WHERE pid=OLD.id);
 DELETE FROM TagsTree
   WHERE id IN (SELECT id FROM TagsTree WHERE pid=OLD.id);
 DELETE FROM TagsTree
    WHERE id=OLD.id;
END;
CREATE TRIGGER insert_tagstree AFTER INSERT ON Tags
BEGIN
  INSERT INTO TagsTree
    SELECT NEW.id, NEW.pid
    UNION
    SELECT NEW.id, pid FROM TagsTree WHERE id=NEW.pid;
END;
CREATE TRIGGER move_tagstree UPDATE OF pid ON Tags
BEGIN
  DELETE FROM TagsTree
    WHERE
      ((id = OLD.id)
        OR
        id IN (SELECT id FROM TagsTree WHERE pid=OLD.id))
      AND
      pid IN (SELECT pid FROM TagsTree WHERE id=OLD.id);
  INSERT INTO TagsTree
     SELECT NEW.id, NEW.pid
     UNION
     SELECT NEW.id, pid FROM TagsTree WHERE id=NEW.pid
     UNION
     SELECT id, NEW.pid FROM TagsTree WHERE pid=NEW.id
     UNION
     SELECT A.id, B.pid FROM TagsTree A, TagsTree B
        WHERE
        A.pid = NEW.id AND B.id = NEW.pid;
END;


```

**Images**
```
CREATE TABLE Images
 (id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  dirid INTEGER NOT NULL,
  caption TEXT,
  datetime DATETIME,
  UNIQUE (name, dirid));
CREATE INDEX dir_index ON Images    (dirid);
CREATE TRIGGER delete_image DELETE ON Images
BEGIN
  DELETE FROM ImageTags
    WHERE imageid=OLD.id;
  DELETE From ImageProperties
     WHERE imageid=OLD.id;
  UPDATE Albums SET icon=null
     WHERE icon=OLD.id;
  UPDATE Tags SET icon=null
     WHERE icon=OLD.id;
END;

```

**ImageTags**
```
CREATE TABLE ImageTags
 (imageid INTEGER NOT NULL,
  tagid INTEGER NOT NULL,
  UNIQUE (imageid, tagid));
CREATE INDEX tag_index ON ImageTags (tagid);

```

I need to insert the appropriate imageid and tag id into ImageTags. As I understand SQL that is as simple as:
```
INSERT INTO "ImageTags" VALUES(443,150); 
```

But, I need to be able to match the imageid in ImageTags to specific values of dirid and name. I would like to make a statement along the lines of.

INSERT INTO ImageTags VALUES(Images.id, 1)
WHERE Images.dirid = '2003/' AND Images.name='dscn1234.jpg';

But, I can't seem to make anything work. If anyone could help me out with this I would really appreciate it. I don't know how to use Triggers, and this is probably my problem, but I'm really still learning.

--andy

---

