---
title: "[JAVA] reverse string split"
date: 2010-03-07
forum: Programming Talk
---

### Post by Fittersman on 2010-03-07
Hey, I'm trying to make an MP3 tagging program but I'm having trouble coming up with an efficient and clean way to code the following.

Basically what I want to do is if users have an MP3 file called something like "/home/fittersman/Music/Albums/U2/[2009] No Line On The Horizon/06 - Get On Your Boots.mp3" I want the user to be able to give me the structure of this file, so for this example it would be "/home/fittersman/Music/Albums/<artist>/[<year>] <album>/<track#> - <title>.mp3", then the program would be able to retrieve the artist, year, album, track#, and title from the filename.

I can do everything except the code that actually compares the two strings and gets the data from the filename.

Does anyone know of a good library or something that can help me with this?

Thanks for any help.

---

### Post by myrtle1908 on 2010-03-07
> **Fittersman said:**
> Does anyone know of a good library or something that can help me with this?

Take a look at Regular Expressions.

[http://java.sun.com/docs/books/tutorial/essential/regex/](http://java.sun.com/docs/books/tutorial/essential/regex/)

You could sub into the input string non-greedy match groups at relevant positions and grab what you need with $1, $2 etc.

---

### Post by Fittersman on 2010-03-08
Thank you for the response. I read through a couple java tutorials on regex but I'm not sure it's really what I'm looking for.

From what I've been reading about regular expressions they mostly seem to be useful when you know what you are looking for. In my case, I have no idea what I'm looking for. All I know is what will be separating the strings I want.

The way I'm understanding regular expressions, I would still need to have quite a large amount of if statements and possibly while loops so I would be able to tell which string I'm working with is for which MP3 property (because users are not always going to put the tags, enclosed in <>, in the same order).

What I was more looking for was a library that would allow me to do something like this...

```
  
String structure = //user input, something like "/home/fittersman/Music/Albums/<artist>/[<year>] <album>/<track#> - <title>.mp3"
structure = structure.replaceAll("<artist>", "$1");
structure = structure.replaceAll("<title>", "$2");
structure = structure.replaceAll("<year>", "$3");
structure = structure.replaceAll("<album>", "$4");
structure = structure.replaceAll("<track#>", "$5");
structure = structure.replaceAll("<number>", "$6");

```

This would result in a string such as "/home/fittersman/Music/Albums/$1/[$3] $4/$5 - $2.mp3" for structure.

Then I could call the function against the filename of the MP3. (GETVALUES is the made-up function I'm looking for.)

```

String filename = MP3file.getfilename();
VALUES = filename.GETVALUES(structure);

```

Then I could just get the tags using the retrieved values:

```

String songArtist = VALUES.get($1);
String songTitle = VALUES.get($2);
String songYear = VALUES.get($3);
//etc...

```

Anyone know anything like this? I just feel like there is already a function that does something like this.

---

