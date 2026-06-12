---
title: "need some help on PHP file manipulation."
date: 2009-11-08
forum: Programming Talk
---

### Post by hockey97 on 2009-11-08
Hi, I know how to open,close a file using php and make it read only or read and write  and know how to change permissions of that file. 

I just don't know how to logically make changes to a file and know whats what where it's located.

For example lets say I used php to generate or create a html file for each user that registered on my site. 

Now I make a editor for the user to edit the layout of that html page without knowing html coding meaning they will be using a gui type interface. Then they saved the layout they want  and the code gets saved to that html file. 

Now I know I can have that html file filled with default layout values. I can then erase the code in that file and put in the changes with the previous default values but with the changes made. 

I don't want to go that route. What I want to do is have some way to know each line of code is what. So the gui editor can add new items or delete old items.

So for example we add in lets say 5 youtube videos. how can php differ each youtube element? 

I tought maybe put the id tags as 1,2,3,4,5.  so that way you can easily tell which is which and the gui editor could just say delete youtube element 3 from layout. 

now lets say  the user just wanted to change youtube  element 3 and not delete it but just update the video src (source). 

how would php be able to find youtube element 3 and find exactly where the src is located and be able to delete the old src and put in the new src link.

So what I am asking is how using php can you manipulate the files in a smart way instead of just re-writing the file. Just to make the changes necessary for a certain action. 

I googled around and haven't found anything about what I am asking just tutorials and other stuff about how to open and close txt files and save data in the file. I already know this but don't know how I can get php to search the file for only the code that is needed to be modified or deleted.

---

### Post by Reiger on 2009-11-08
Think about your data. Adopt some kind of format. Then think again, and adopt a standard format. ;)

So your WYSIWYG (JavaScript) client must edit a pre-supplied document data model, and spit back out an updated document of another or same data model which is sent to your backend (PHP).

If you use standard data models such as XML (DOM) or JSON it should not be too hard if you stick to the essentials in the data. (I.e. if you adopt XML as model, then don't try to rephrase your data as an XHTML snippet; rather use a custom XML definition and use XSLT to convert it to XHMTL -- this way your XML can cut to the essentials without too much code which translates in less code on client and server and less data in the storage backend).

---

### Post by RTrev on 2009-11-08
> **hockey97 said:**
> So what I am asking is how using php can you manipulate the files in a smart way instead of just re-writing the file. Just to make the changes necessary for a certain action. 


I'm not exactly sure what you're trying to do, but here's a couple ideas which may help.

1) In these situations, you could read the file line by line, while writing the output file, and have full control of each line.

2) You could use include files.  The user edits the include file, and the main body of your php page is never changed at all.

Are we warm?

---

### Post by hockey97 on 2009-11-10
well, I want to directly modify the files.  I think your warm. 

I am making a layout editor. The user will have their own page. 

I will have a default file. If the user wants their own customized version then  my code will generate them their own html file and css file. 

I will make javascript to be the GUI so the users can on the page add in tables and vidoes and music etc to their layout and drag and drop it anywhere and even resize. They will be able to make the tables or links or images have functions attach for example if a table is a dispaly of people who posted messages then they can make a empty table and with a drop down menu assign a message function dispaly. Then the table will display messages they got. 

So then javascript will record all the values and generate the html code neede to make that layout. 

I then want to transfer that data to a php file which will open that users html and css file and then use that javascript data to make the changes. I don't want to rewrite the html file and css. I just want to make changes to it. 

So my question is how can I figure out  whats on each line. 

like for example if the user has 2 youtube videos  how can I find where those 2 youtube video code is located in the html file?

I know if I open the file and see like line 28 having the code. Yet couldn't their be some offsets when I open the file with php where line 28 could be line 29 meaning that I would edit line 28 thinking it's the line that has youtube video code and make changes but in reality it's line 29 and so I change some other code that will now mess up the layout.

Like how could I find specific parts of a file that has particular code. 

like if line 28 is a long line that contained a image code, 2 youtube videos and a link. 

How can php know whats what on line 28. Is their any way I can tell php to delete line 28 at youtube video 1 ? 

I know how to make the javascript and transfer the data to php.

I am just stumped at using php to modify html and css code that are particular  meaning I just want to changes parts when requested. 

like lets say I don't know what line number in th html file  where the code I want to delete or modify is located at. 

Is their any way php can search for particular ids? So when it finds a match it will edit that area of the code.

---

### Post by RTrev on 2009-11-10
> **hockey97 said:**
> like lets say I don't know what line number in th html file  where the code I want to delete or modify is located at. 

Is their any way php can search for particular ids? So when it finds a match it will edit that area of the code.

Well, this is kind of crude.. and maybe someone knows a better way.. but..

What I was getting at before was that the PHP routine would read each line, one at a time, of the file in question.  It could either store these lines in an array, or write them immediately to the output file.

For each line, a string search can be done looking for whatever you are interested in.  At that point, the routine begins making the modifications and writing different lines to the output file.  When it's done, it finishes up by simply going back to copying each line from the input file to the output file again.

Maybe you could put comment flags in the files to be modified, so that your routine had something specific to search for.  Implementation details like that could vary a lot.  But the basic idea is the line-by-line approach until you find the area(s) you are interested in changing.

Does that help any?

---

### Post by Can+~ on 2009-11-10
Simplest approach: with unique users id as filename:

```
usercss/<user_id>.css
```

Then, if you know your user id on the database, you can pull their css file (why would you use an html file?).

Edit: Also, notice I didn't read your whole replies, I'm just replying the original question. I know you usually commit some aberration that taint any attempt of making a usable program with shallow logic and ill-conceived ideas that make me doubt about my belief in human kind, so I just skipped that part.

---

