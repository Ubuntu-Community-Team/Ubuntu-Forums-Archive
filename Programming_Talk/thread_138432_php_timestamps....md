---
title: "php timestamps..."
date: 2006-03-01
forum: Programming Talk
---

### Post by grim918 on 2006-03-01
I have a problem. I can't figure out how to work with timestamps. I want to use timestamps to check if a user is online or not. How do you compare two different timestamps, for example:

//--start code--//
if( $timestamp  > ($timestamp2 + $x)){
                 //user offline
}
//--end code--//

$x is the amount of minutes that will be added to the second timestamp.
the statement will check if the user has been inactive for $x amount of minutes.
I don't know how to work with timestamps though. How do you compare them. I would appreciate any help.

---

### Post by ltmon on 2006-03-01
Timestamps are a measure of seconds since a certain date (1/1/1970?).  It's called 'Unix time', and is the internal representation of time on all Unix machines.

You can use functions to convert them to and from actual date/time representations (see: [http://php.net/manual/en/ref.datetime.php](http://php.net/manual/en/ref.datetime.php)) ... or just do the math manually.

For example, to check for 10 minutes:

```

if ($timestamp1 > $timestamp2 + (10 * 60)) { *do something* }

```

---

### Post by grim918 on 2006-03-02
Ok thank you, now i get it. Will this work if you enter a timestamp into a mysql table and then retrieve the timestamp and try to use it. I read that mysql stores timestamps as a string. If it does store them as a string then wouldn't that create a problem if you try perform mathematical equations on it.

---

### Post by ltmon on 2006-03-02
Hi,

Store timestamps in mysql as INTEGER type columns. 

I wouldn't bother with MySQL date type columns or anything like that.  It's just as easy to use INTEGER timestamp fields, it's more efficient and there are a whole lot of "GOTCHA's" in MySQL date fields that need watching out for.  All in all it's just simpler to use INTEGER columns and timestamps.

Cheers,

L.

P.S. On a side note this will actually fail sometime in 2034 or so, because a 32-bit integer will run out of room in which to store timestamps for that date and beyond.

If you have a 64-bit machine (and plan on keeping this app running until 2034 :)) you could use BIGINT instead to prevent this.

P.P.S. For an example of some of the issues with DATE columns in MySQL have a look at: [http://sql-info.de/mysql/gotchas.html#1_14](http://sql-info.de/mysql/gotchas.html#1_14)

---

### Post by grim918 on 2006-03-02
Ok, Thank you for the tip.

---

