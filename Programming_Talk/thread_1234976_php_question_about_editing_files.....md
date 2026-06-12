---
title: "php question about editing files...."
date: 2009-08-08
forum: Programming Talk
---

### Post by hockey97 on 2009-08-08
Hi, I am working on a edit layout system. So far I figure out what I want to do. 

I will create a default layout. each user will have their own html file and css file if they made any changes.

I will create a new html file and css file for the person when they make changes to their layout. 

The reason I will create each user their own html file. Is because I plan to allow users to delete elements and add in new elements into their layout. 

So now here is where my question comes into play. I need to edit the html file and css file. 

I will either add a line automatically or delete a line automatically meaning by code.

I know how to add lines and delete them in files. The problem is how can I use php to figure out the content of each line. 

For example lets say a user added a youtube video on their layout. They then decided they don't want this so they go into the editor and delete the yoututbe video yet this user has 5 youtube videos. 

How in terms of programming,can I figure out which line in the html file starts the youtube code.Yet the know which exact line/code is the one for that particular video. 

I am asking how can I create some sort of id system for each element? 

So I can delete the right line. Also how could I just delete half a line. 

Lets say in one line their was 2 codes one for youtube and one for a image. If I tell it to delete that line then both codes will get deleted.
How could I figure out all the code for one element to  delete when it's on a same line as another piece of code? :confused:

Thanks for your time. 
:D

---

### Post by jeffathehutt on 2009-08-08
I think you are approaching this the hard way. ;)

The system you described would be very complicated to implement, and would be prone to numerous potential errors.  PHP is rarely used to create static .html files.  Usually, you would use php to generate a dynamic html file that is rendered and delivered directly to the browser, with the help of a database.

One way of solving this problem is to use a database that stores the markup for each user's web page.  Each user would have their own markup file in the database that only your layout editor would change (by disallowing the user to directly edit the file, you eliminate several possible bugs).  You could easily create your own type of wiki-like language to accomplish this.  For example, a sample markup file (in the database only, not a physical file) could be:

```

Hey, welcome to my page!  Check out my youtube video here: {{USER:1}}
Here is one of my pictures: {{USER:2}}

```

Now, all you have to do is go through the markup file, replacing {{USER:1}} and {{USER:2}} with the appropriate element.  {{USER:1}} and {{USER:2}} would map to a row in the database, which might contain something like '<img src="mypic.jpg">' or whatever the actual html would be to display that element.  The same applies to youtube videos, songs, pictures, whatever you want your users to have access to.  All you store in the markup file is a link such as {{USER:#}} and increment the number each time the user adds something to their page.  This way, when the user wants to delete something from their page, all you have to do is delete {{USER:1}} from the markup file for that user and there is no confusion as to which item the user wants to remove.

Using this system, you only need to manage a small number of files, instead of seperate files for each user.  For example, instead of using 'http://www.site.com/user/index.html' as their page they would instead use something like 'http://www.site.com/index.php?user=USER'.  You would then retrieve the markup file for USER, swap the {{USER:#}} with the actual element also stored in the database, then display it to the visitor.

When the user wants to change their page, they will have to do so from your layout editor (written in javascript or whatever you want to write it in).  The advantage there is they won't be able to make as many mistakes.  Just make sure your layout editor works properly, and it will be harder for your users to break their pages.

Hope that helps. :)

---

### Post by hockey97 on 2009-08-11
> **jeffathehutt said:**
> I think you are approaching this the hard way. ;)

The system you described would be very complicated to implement, and would be prone to numerous potential errors.  PHP is rarely used to create static .html files.  Usually, you would use php to generate a dynamic html file that is rendered and delivered directly to the browser, with the help of a database.

One way of solving this problem is to use a database that stores the markup for each user's web page.  Each user would have their own markup file in the database that only your layout editor would change (by disallowing the user to directly edit the file, you eliminate several possible bugs).  You could easily create your own type of wiki-like language to accomplish this.  For example, a sample markup file (in the database only, not a physical file) could be:

```

Hey, welcome to my page!  Check out my youtube video here: {{USER:1}}
Here is one of my pictures: {{USER:2}}

```

Now, all you have to do is go through the markup file, replacing {{USER:1}} and {{USER:2}} with the appropriate element.  {{USER:1}} and {{USER:2}} would map to a row in the database, which might contain something like '<img src="mypic.jpg">' or whatever the actual html would be to display that element.  The same applies to youtube videos, songs, pictures, whatever you want your users to have access to.  All you store in the markup file is a link such as {{USER:#}} and increment the number each time the user adds something to their page.  This way, when the user wants to delete something from their page, all you have to do is delete {{USER:1}} from the markup file for that user and there is no confusion as to which item the user wants to remove.

Using this system, you only need to manage a small number of files, instead of seperate files for each user.  For example, instead of using 'http://www.site.com/user/index.html' as their page they would instead use something like 'http://www.site.com/index.php?user=USER'.  You would then retrieve the markup file for USER, swap the {{USER:#}} with the actual element also stored in the database, then display it to the visitor.

When the user wants to change their page, they will have to do so from your layout editor (written in javascript or whatever you want to write it in).  The advantage there is they won't be able to make as many mistakes.  Just make sure your layout editor works properly, and it will be harder for your users to break their pages.

Hope that helps. :)

I think I know what your saying. I can  create one html file. At the basic point meaning not put any elements on their. I can use a database to help generate the html file by storing the code and displaying them where ever.In the database the users elements like youtube video will be stored and can be deleted at anytime.

I am thinking to make a php css file and from what you said I decided to put the css values in the database which can change upon editing.

I think  I understood what you said.

Thanks for your reply.  :)

---

