---
title: "Maximum string length in PHP4"
date: 2007-05-17
forum: Programming Talk
---

### Post by MadeR on 2007-05-17
PHP4 problem.
I have a string that should contain a list of comma separated numbers, obtained elaborating a XML file.
So far, in this string there are 1035 numbers and php seems to have problems handling the situation.

In fact  a var_dump of this string outputs:
string(865) 

instead of something like:
string(*nnn*) "123,2346,23465.... "

If the string contains 300-400 numbers, there are no problems.

what can I do?

---

### Post by heimo on 2007-05-17
Can you give us an example (code if possible)? I don't know if there's limit for string length in PHP, but it's more than couple kilobytes.

---

### Post by MadeR on 2007-05-17
> **heimo said:**
> Can you give us an example (code if possible)? I don't know if there's limit for string length in PHP, but it's more than couple kilobytes.

well... 1035 numbers... 
let's say the average is 3 digits plus the comma.

so 4*1035 = 4150 bytes... well it's 4KB.

a brief description of the code:
[www.boardgamegeek.com](www.boardgamegeek.com) is a world boardgame database.
It offers an XML interface to get game's informations, user's informations and game collections.

I made a small program that lets a user mix the collection of some users, retrieve the details about the games in this "mixed" collection and then search games by some parameters [http://www.massimilianodellarovere.eu/giochiamo/](http://www.massimilianodellarovere.eu/giochiamo/)
if you want to try the program:
users: masdero,balugoci,trilobit   :works
users:Gomez,Darthlord,Dracomjb  : error

the problem is that one user, Gomez, has 1029 games. This means that I retrive the list as an xml file, [http://www.boardgamegeek.com/xmlapi/collection/gomez](http://www.boardgamegeek.com/xmlapi/collection/gomez) , extract the game ids, and then I query again the xmlapi to receive details about the games. [http://www.boardgamegeek.com/xmlapi/game/1,3](http://www.boardgamegeek.com/xmlapi/game/1,3) in this example I retrieve the infos for games 1 and 3.

There are two ways to receive informations about n games:
```
foreach( $games as $g )
GET_GAME_INFO( "http://www.boardgamegeek.com/xmlapi/game/$g" ); 
```
but this means 1035 connection to the BGG site

OR

```
GET_GAME_INFO( "http://www.boardgamegeek.com/xmlapi/game/" . "gamea,gameb,gamec,gamed,...gamexyz" );
GET_GAME_INFO( "http://www.boardgamegeek.com/xmlapi/game/$list" ); 
```

the problem is that the game list is too long and a string can't contain it all.

Here is the thread on boardgamegeek: [http://www.boardgamegeek.com/article/1502448](http://www.boardgamegeek.com/article/1502448)

info on the XML api: [http://www.boardgamegeek.com/xmlapi/](http://www.boardgamegeek.com/xmlapi/)

---

### Post by Miademora on 2007-05-17
Its possible that the webserver doesnt allow urls this long.

[http://classicasp.aspfaq.com/forms/what-is-the-limit-on-querystring/get/url-parameters.html](http://classicasp.aspfaq.com/forms/what-is-the-limit-on-querystring/get/url-parameters.html)

---

### Post by heimo on 2007-05-17
> **MadeR said:**
> the problem is that the game list is too long and a string can't contain it all.

Then you already know what's wrong and the following fails?
[php]<script language="php">
$string=str_repeat("a",8096);
echo $string;
</script>
[/php]

---

### Post by MadeR on 2007-05-17
> **Miademora said:**
> Its possible that the webserver doesnt allow urls this long.

[http://classicasp.aspfaq.com/forms/what-is-the-limit-on-querystring/get/url-parameters.html](http://classicasp.aspfaq.com/forms/what-is-the-limit-on-querystring/get/url-parameters.html)

To pass info on the web server, I concatenate the URL address together with the string, so while this can be an additional problem, is a different one.

---

### Post by Miademora on 2007-05-17
Whats your php version?

Your provider maybe using the hardened patch wich limits variable length?
[http://www.hardened-php.net/](http://www.hardened-php.net/)

Wich function are you using to build the string? or simple $a=$a.$b / $a.=$b?

---

### Post by MadeR on 2007-05-17
> **Miademora said:**
> Whats your php version?

Your provider maybe using the hardened patch wich limits variable length?
[http://www.hardened-php.net/](http://www.hardened-php.net/)

Wich function are you using to build the string? or simple $a=$a.$b / $a.=$b?

I use the implode(',', array) function to generate the string

---

