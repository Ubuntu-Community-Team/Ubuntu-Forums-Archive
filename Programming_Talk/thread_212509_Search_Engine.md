---
title: "Search Engine"
date: 2006-07-10
forum: Programming Talk
---

### Post by Darkness3477 on 2006-07-10
Hello, just for a little fun I've decided to code a little search engine using PHP and MySQL. It's nothing too serious, it's actually more to just help me learn PHP a little better. 

I'm only up to the design part, and I'm wondering if anyone has made a Search Engine before and if so, what types of things do I need to pay careful attention too, and what do I need to make sure I have?

So far I've decided that I need a program to add the information to my Database, a program that searches the DB and a program to list all, and if needed delete, the data I have put into my DB.

I've decided I'm going to design my database with these collumns as a bar minimum: Title, Author/Founder, Link, ref num, keyword(s), Description. 

Now, when I or others use my search engine, I would like them to be given the chance to search all of those fields, or just one. I would also like the description to be partially searchable. 
For instance, if I wanted to put this site into my Search Engine, I could have "The ubuntu help forums contain many intelligent people who are always willing to help out the linux community in anyway they can." If someone comes along and types in "ubuntu" "Linuc community" or any other word or string, I would like it searched.

How hard would it be to do this, considering I've only ever changed small sections of PHP around befor? I do have a book that I'm using as a reference, but it doesn't actually tell how to make a Search Engine, just a catalogue and a members only section.


Any and all help is appreciated,
thankyou for your time.

---

### Post by ifokkema on 2006-07-10
Interesting project. I've once told myself I should do this, but never got around actually doing it.
Your setup looks OK. You need to think about this, though: hit scores. If you're getting more and more pages in the database, how are you determining which hit goes on top? Hit in the title means more points than a hit in the body of the page. If you really want to do it right: two hits in the body of the page should get more points than one hit in the body of the page. AND you'd want MySQL sorting the hits for you, not in PHP.

Here's a thought... haven't worked this out myself, but just a thought. Build a table, containing the page id, a keyword, and the score that this page has for this particular keyword. If each hit in the title means 5 points, and each hit in the body 1, a page (PageID 1) with the word "Linux" in the body twice and once in the title, then has 7 points. So...

```
PageID | Rank | Keyword
-------+------+--------
     1 |    7 | Linux
```
You need a separte table with PageID, Title, Description, URL etc for printing out the results. You can order by the SUM(Rank) and join that table with the ranking table to print out the results properly.

Searching for "Ubuntu Linux" may go like: (untested code)
SELECT Pages.Title, Pages.URL, Pages.Description, SUM(Rank.Rank) AS Total_Rank FROM Rank LEFT JOIN Pages USING (PageID) WHERE Rank.Keyword = "Ubuntu" OR Rank.Keyword = "Linux" GROUP BY Rank.PageID ORDER BY SUM(Rank.Rank) DESC;

Remember, I've never written a search engine myself. This is just a thought.

Tell me what you think and have fun playing around with it!

---

### Post by Darkness3477 on 2006-07-11
I hadn't actually thought about that. Thanks for pointing it out to me! 
Hopefully I will be coding this out over the next week or so (Tomorrow is my birthday so I doubt I'll be able to type properly, so coding is out of the question) and then I have a few other things to do with the reminder of my holidays. 

Anyway, I'm aiming to have everything done a week into next month. Including having a good number of stuff for people to search. 

So, thanks again for the Rank idea, and I hope that if anyone else has an idea or a suggestion, that they would tell me. 

Toodles.

---

### Post by kripkenstein on 2006-07-11
Ok, for a search engine, you need 10,000 servers in a redundant array, for starters ;) 

More seriously, though, this sounds like a nice little project. My suggestion would be to make sure that nearly all of the processing is done at the **database** level - not PHP. This will in all likelihood make things faster and simpler (if you set up the DB right). Another advantage is that altering SQL is usually much easier than altering PHP. (This goes a little against your goal to learn PHP better, I know...)

What I mean, is that the tables should be set up so that virtually every query can be done with a single SELECT command (possibly a complex one). And **not** by a SELECT, then some processing in PHP.

Moving the processing to the DB can be done by smart SQL, including UNION keywords, and so forth. If you have any specific questions, feel free to run them by us here.

One last thing: Happy Birthday (tomorrow).

---

### Post by hockey97 on 2007-07-27
Hi, I am also interested in making a search engine,  how complex is it I know php and C++ and c-script and python.

never made a program or made a full page with php had done projects just for pratice..

I have seen tutorials on php making a search engine but only for your website not like somthing like google.

also how could I intergrate spell check in e-mailing ect..???

---

