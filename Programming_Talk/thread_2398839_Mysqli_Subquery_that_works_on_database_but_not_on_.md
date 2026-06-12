---
title: "Mysqli Subquery that works on database but not on PHP"
date: 2018-08-17
forum: Programming Talk
---

### Post by santa-oscuro on 2018-08-17
[COLOR=#242729][FONT=Arial][CENTER]
[/CENTER]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]I have a subquery that search all the genres that have an specific book, and the query makes it find all the books that have those genres of the subquery and it is creates a count of the times that repeat the same books and creates a new column of the counter. The orderly query remaining is based on books that are repeated more to less.
[/FONT][/COLOR][COLOR=#242729][FONT=Arial] [FONT=inherit]
This query works but the problem comes when i tried to insert variable at server part with mysqli. I'm trying to do it for oriented objects but it does not return results. Well, i was looking for all post but nothing has worked. I tried REGEXP and similars but returns results that aren't correct.

[/FONT]
[/FONT][/COLOR]> [COLOR=#242729][FONT=Arial][COLOR=#303336][FONT=inherit]//[/FONT][/COLOR][COLOR=#303336][FONT=inherit]I used asigned letters because you can understand better

[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]book [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]get_id_book[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit] 
[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]book [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"%$book%"[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]result [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]link-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#303336][FONT=inherit]prepare [/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"SELECT b.name, COUNT(name) AS duplicated, c.arxive, t.type, t.name_type
FROM Books b, Covers c, Types t, Genres_book g
WHERE b.id_book = c.id_cover_book AND
b.id_book = g.id_genre_book AND
g.id_book_genre IN ( SELECT id_book_genre
FROM Book b1, Genres_book g1
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#242729][FONT=Arial][COLOR=#7D2727]WHERE b1.id_book = g1.id_genre_book AND
[/COLOR][/FONT][/COLOR][COLOR=#242729][FONT=Arial][COLOR=#7D2727][FONT=inherit]b1.id_book IN (?)) AND
NOT (b.id_book = ?)
GROUP BY b.name
ORDER BY duplicated DESC"[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]result-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#303336][FONT=inherit]bind_param[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]'i'[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]book[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

[/FONT][/COLOR][COLOR=#101094][FONT=inherit]if[/FONT][/COLOR][COLOR=#303336][FONT=inherit]($[/FONT][/COLOR][COLOR=#303336][FONT=inherit]result-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#101094][FONT=inherit]execute[/FONT][/COLOR][COLOR=#303336][FONT=inherit]()){[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]result-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#303336][FONT=inherit]bind_result[/FONT][/COLOR][COLOR=#303336][FONT=inherit]($[/FONT][/COLOR][COLOR=#303336][FONT=inherit]name[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]duplicated[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]arxive[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]type[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]name_type[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#101094][FONT=inherit]while[/FONT][/COLOR][COLOR=#303336][FONT=inherit]($[/FONT][/COLOR][COLOR=#303336][FONT=inherit]result-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#101094][FONT=inherit]fetch[/FONT][/COLOR][COLOR=#303336][FONT=inherit]())[/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
echo [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"...."[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#303336][FONT=inherit]}
[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]There I put the code that works. I know how use Like, but im saying that code works when i tried on database query but on php, on change:

[/FONT][/COLOR]> [COLOR=#101094][FONT=inherit]IN [/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#101094][FONT=inherit]SELECT[/FONT][/COLOR][COLOR=#303336][FONT=inherit] id_book_genre [/FONT][/COLOR][COLOR=#101094][FONT=inherit]FROM[/FONT][/COLOR][COLOR=#303336][FONT=inherit] Book b1[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit] Genres_book g1 [/FONT][/COLOR][COLOR=#101094][FONT=inherit]WHERE[/FONT][/COLOR][COLOR=#303336][FONT=inherit] b1[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]id_book [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] g1[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]id_genre_book [/FONT][/COLOR][COLOR=#101094][FONT=inherit]AND [/FONT][/COLOR][COLOR=#303336][FONT=inherit]b1[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]id_book [/FONT][/COLOR][COLOR=#101094][FONT=inherit]LIKE [/FONT][/COLOR][COLOR=#303336][FONT=inherit]?[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#101094][FONT=inherit]AND [/FONT][/COLOR][COLOR=#101094][FONT=inherit]NOT[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]b[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]id_book [/FONT][/COLOR][COLOR=#101094][FONT=inherit]Like [/FONT][/COLOR][COLOR=#303336][FONT=inherit]?[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#101094][FONT=inherit]GROUP [/FONT][/COLOR][COLOR=#101094][FONT=inherit]BY[/FONT][/COLOR][COLOR=#303336][FONT=inherit] b[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]name [/FONT][/COLOR][COLOR=#101094][FONT=inherit]ORDER [/FONT][/COLOR][COLOR=#101094][FONT=inherit]BY[/FONT][/COLOR][COLOR=#303336][FONT=inherit] duplicated [/FONT][/COLOR][COLOR=#101094][FONT=inherit]DESC[/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]result-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#303336][FONT=inherit]bind_param[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]'ii'[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]book[/FONT][/COLOR][COLOR=#303336][FONT=inherit],$[/FONT][/COLOR][COLOR=#303336][FONT=inherit]book[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);
[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]I tried without "**AND NOT (b.id_book Like ?)"** and only bind 1 parameter but both returns 0 results...[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Sorry for my english, I'm desperate I hope someone can help me out.[/FONT][/COLOR]

---

