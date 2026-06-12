---
title: "BASH to create SQL Insert statements?"
date: 2009-02-16
forum: Programming Talk
---

### Post by brennydoogles on 2009-02-16
I am in the process of creating a music database as part of a class project, and I am looking for a way to cut the amount of time required for data entry. All of my music is organized in folders by Artist, and then album inside my Music folder. Using tree, I was able to generate a file that shows my music like this:
```
|-- Audioslave
|   |-- Audioslave
|   |   |-- 01 Cochise.mp3
|   |   |-- 02 Show Me How to Live.mp3
|   |   |-- 03 Gasoline.mp3
|   |   |-- 04 What You Are.mp3
|   |   |-- 05 Like a Stone.mp3
|   |   |-- 06 Set It Off.mp3
|   |   |-- 07 Shadow on the Sun.mp3
|   |   |-- 08 I Am the Highway.mp3
|   |   |-- 09 Exploder.mp3
|   |   |-- 10 Hypnotize.mp3
|   |   |-- 11 Bring Em Back Alive.mp3
|   |   |-- 12 Light My Way.mp3
|   |   |-- 13 Getaway Car.mp3
|   |   `-- 14 The Last Remaining Light.mp3
|   `-- Out of Exile
|       |-- 01 Your Time Has Come.mp3
|       |-- 02 Out of Exile.mp3
|       |-- 03 Be Yourself.mp3
```

and so on. The file is about 1500 lines long, and manually entering the first album resulted in about 115 lines of code, resulting in about 12,000 lines of code to be entered. 

I was thinking that a BASH script could generate the SQL for me by substituting the song names and album names in the statements. The problem is that I am super rusty on my BASH, and don't know where to begin. Any advice?

---

### Post by howlingmadhowie on 2009-02-16
i don't think this tree format is particularly parseable. i'd recommend going into the base directory for your music and trying something like:

```
find . -name "*.mp3" > mymusicfiles
```

the resulting file should be easier to parse.

---

### Post by Yuzem on 2009-02-17
This example is for sqlite (I didn't test it):

```
database=your-database
table=table

find . -name "*.mp3" | (

	echo "BEGIN TRANSACTION;"

	while read -r line ; do
		album=${line%/*} album=${album##*/}
		title=$(line##*/}

		echo "INSERT INTO \"$table\" VALUES('$album','$title');"
	done

	echo "COMMIT;"

) | sqlite3 $database
```

---

