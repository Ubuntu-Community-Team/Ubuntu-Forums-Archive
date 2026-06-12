---
title: "help me in software developement in C !!!"
date: 2011-02-21
forum: Programming Talk
---

### Post by Praveen30 on 2011-02-21
i have knowledge of c language but i haven't made any software kind of thing...i am a student and i have done basic level of programming..now i want to go on next level where i can use my c knowledge to build something interesting...i have an idea..i want to make a software by which i can count how many times my files have been copied on lan by other users..but i don't know know how to start and from where to start..well if this idea seems something complicated then give me some suggestions...waiting for your suggestions because i know a lot of developers are here..so plz guide me....

thanks in advance!!!

---

### Post by Tony Flury on 2011-02-21
Not sure that would be a beginner type project, as you would need (i think) to intercerpt or some how count the number of times the file gets opened and closed, and identify then what is opening and closing the file - and of course not every file open is a copy. On the whole this sounds like a kernel module change.

My suggestion would be - think of something that you do regularly - and see if you can automate it. 

For me it was uploading pictures to flickr, and then having to go through the uploaded pictures adding Tags, sets etc - so I wrote a gui which enables me to drag/drop pictures, etc, and add Tags/sets in batches.

---

### Post by Praveen30 on 2011-02-21
> **Tony Flury said:**
> Not sure that would be a beginner type project, as you would need (i think) to intercerpt or some how count the number of times the file gets opened and closed, and identify then what is opening and closing the file - and of course not every file open is a copy. On the whole this sounds like a kernel module change.

My suggestion would be - think of something that you do regularly - and see if you can automate it. 

For me it was uploading pictures to flickr, and then having to go through the uploaded pictures adding Tags, sets etc - so I wrote a gui which enables me to drag/drop pictures, etc, and add Tags/sets in batches.

Nice idea, can you give me some details of it?? means how to start it and how to do this??

---

### Post by Tony Flury on 2011-02-21
> **Praveen30 said:**
> Nice idea, can you give me some details of it?? means how to start it and how to do this??

Well - I started with an API for flickr for use in python - and started playing with writing code for it and once i had an Image class written that i could add pictures to, and which would upload pics - i then wrote the GUI classes. Having said that, this was in python - so very easy to do this sort of rapid developing.
If i was doing it in C - i would have done a lot more design up front.

Besides - i needed the app becuase I am a keen amateur photographer and artist and was uploading a lot of pictures per week, and so it was worth the effort.

I have a number of improvements i want to make - but they would be a lot of work - and they would not actually help me that much - so they are not getting done - as yet.

What I have found that unless I am getting paid to do development, then i only develop stuff that i really need (as a hobbyist), and I stop once it works for me - I tend to even ignore the occassional bugs etc which only impact me occassionally. 

What I am trying to say is don't pick a random project that someone else has suggested - pick something that you need, and write that, since if you really need it, you will finish it and make it work.

---

### Post by nvteighen on 2011-02-21
> **Tony Flury said:**
> 
What I am trying to say is don't pick a random project that someone else has suggested - pick something that you need, and write that, since if you really need it, you will finish it and make it work.

Or write something that attracts you but you don't need :D

Bah, I'm kidding; Tony is right: if you just follow someone else's interests, the chances of that not being your interests are very high. Don't desperate if you don't get any inspiration, just keep practicing and it will come.

---

