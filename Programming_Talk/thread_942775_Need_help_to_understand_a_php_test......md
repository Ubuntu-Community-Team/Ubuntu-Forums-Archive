---
title: "Need help to understand a php test....."
date: 2008-10-09
forum: Programming Talk
---

### Post by hockey97 on 2008-10-09
CLOSED Post!!!!

---

### Post by themusicwave on 2008-10-09
Off the top of my head, what is the primary key of your database?

Remember you can't have duplicates of primary keys, that may be your problem.  Otherwise I am not too sure without seeing some code.

---

### Post by pp. on 2008-10-09
What you are saying is that you added a query to the program before inserting a new row, and that the database was already set to reject duplicate entries.

If the database rejects duplicate entries, then your query to detect possible duplicates is redundant.

Presumably you should have handled the error code for trying to insert a duplicate row.

---

### Post by CptPicard on 2008-10-09
Either you have a primary key or unique constraint on your data or you have to do a serializable transaction in your check to make sure that you keep things consistent across multiple sessions running concurrently.

---

### Post by drubin on 2008-10-09
> **hockey97 said:**
> HI ok, I already applied to one job, which is php developer job. The people rejected my test.

I bugged them asking why. They mainly said that I didn't allow for a duplicate manipulation.

The test was to make a html form to input the persons First Name and last name and their phone number into the database and then display this information.

This might help you out
[http://www.geekministry.com/blog_article.php?id=93](http://www.geekministry.com/blog_article.php?id=93)
[http://www.webmaster-talk.com/php-forum/31101-how-prevent-back-button-resubmitting-form.html](http://www.webmaster-talk.com/php-forum/31101-how-prevent-back-button-resubmitting-form.html)

---

### Post by drubin on 2008-10-09
> **CptPicard said:**
> Either you have a primary key or unique constraint on your data or you have to do a serializable transaction in your check to make sure that you keep things consistent across multiple sessions running concurrently.

I think the test wanted him to check if the user resubmitted for form ?

---

### Post by Sydius on 2008-10-09
> **drubin said:**
> I think the test wanted him to check if the user resubmitted for form ?

That was my guess.  A simple "prevent the user from clicking submit twice" kind of thing.  The test is otherwise too low-level to expect the person taking it to know about transactions serialization.

---

### Post by forger on 2008-10-09
If they didn't specifically ask you for that setting, I don't think you did anything wrong, they didn't specify their request :)

---

### Post by drubin on 2008-10-09
> **forger said:**
> If they didn't specifically ask you for that setting, I don't think you did anything wrong, they didn't specify their request :)

Job requests hardly specify what they excatly would like it to do.. Just that it should kinda look similar to this maybe not so much alike. (Say that english is shocking).

But most of the time they just would like it to work and be idiot prove. (Not that a simple header(location) solved any thing).

---

### Post by hockey97 on 2008-10-09
Closed post!!!!!!

---

### Post by LaRoza on 2008-10-09
> **hockey97 said:**
> 
I got an e-mail saying I was rejected and So I asked why they kept saying I don't know since it's the IT manager that handles the test. SO I bugged them until finally they got kinda annoyed by me so they ask the IT manager.

They then told me that my code wasn't able to be duplicate manipulative. 


Here is my opinion...

You said it yourself, you bugged them until they got annoyed. 

Not knowing you personally, I can't say for sure, but I would bet you annoyed them somehow before and they don't like you.

Since you know you bugged them, and they were annoyed, you probably know why they were. Now the question is, why did you do that?

This is the best book I know of for getting inside information on getting a job: [http://www.amazon.com/Confessions-Recruiting-Director-Insiders-Landing/dp/0735204047](http://www.amazon.com/Confessions-Recruiting-Director-Insiders-Landing/dp/0735204047)

"What Color Is Your Parachute?" is second.

Also, for interacting with humans, get: "How to Win Friends and Influence People" by Dale Carnegie

Based on what I see, I wouldn't hire you either, without even considering your coding ability or lack thereof.

---

