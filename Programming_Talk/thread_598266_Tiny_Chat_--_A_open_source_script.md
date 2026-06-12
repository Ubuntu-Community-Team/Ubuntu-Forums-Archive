---
title: "Tiny Chat -- A open source script"
date: 2007-10-31
forum: Programming Talk
---

### Post by 7Priest7 on 2007-10-31
No Code For Ubuntu Forums

---

### Post by smartbei on 2007-10-31
Just wondering...What do you have against 'for' loops?
[php]
@file_put_contents($sd . "10.txt", @file_get_contents($sd . "9.txt")); // Move the chat up
@file_put_contents($sd . "9.txt", @file_get_contents($sd . "8.txt")); // Move the chat up
@file_put_contents($sd . "8.txt", @file_get_contents($sd . "7.txt")); // Move the chat up
@file_put_contents($sd . "7.txt", @file_get_contents($sd . "6.txt")); // Move the chat up
@file_put_contents($sd . "6.txt", @file_get_contents($sd . "5.txt")); // Move the chat up
@file_put_contents($sd . "5.txt", @file_get_contents($sd . "4.txt")); // Move the chat up
@file_put_contents($sd . "4.txt", @file_get_contents($sd . "3.txt")); // Move the chat up
@file_put_contents($sd . "3.txt", @file_get_contents($sd . "2.txt")); // Move the chat up
@file_put_contents($sd . "2.txt", @file_get_contents($sd . "1.txt")); // Move the chat up
[/php]
=
[php]
for ($i = 10; $i >1; $i++)
{
     @file_put_contents($sd . "$i.txt", @file_get_contents($sd . $i-1.".txt")); // Move the chat up
}
[/php]
Same with the other one. Note - there may be some syntax errors - didn't check the code.

Also, why use 10 different files? You could have it use one file, but that is a change of architecture, so it's up to you.

Lastly, it is simpler to use sessions to remember that someone is logged on than to use a hidden form field.

---

### Post by 7Priest7 on 2007-10-31
> **smartbei said:**
> Just wondering...What do you have against 'for' loops?
[php]
@file_put_contents($sd . "10.txt", @file_get_contents($sd . "9.txt")); // Move the chat up
@file_put_contents($sd . "9.txt", @file_get_contents($sd . "8.txt")); // Move the chat up
@file_put_contents($sd . "8.txt", @file_get_contents($sd . "7.txt")); // Move the chat up
@file_put_contents($sd . "7.txt", @file_get_contents($sd . "6.txt")); // Move the chat up
@file_put_contents($sd . "6.txt", @file_get_contents($sd . "5.txt")); // Move the chat up
@file_put_contents($sd . "5.txt", @file_get_contents($sd . "4.txt")); // Move the chat up
@file_put_contents($sd . "4.txt", @file_get_contents($sd . "3.txt")); // Move the chat up
@file_put_contents($sd . "3.txt", @file_get_contents($sd . "2.txt")); // Move the chat up
@file_put_contents($sd . "2.txt", @file_get_contents($sd . "1.txt")); // Move the chat up
[/php]
=
[php]
for ($i = 10; $i >1; $i++)
{
     @file_put_contents($sd . "$i.txt", @file_get_contents($sd . $i-1.".txt")); // Move the chat up
}
[/php]
Same with the other one. Note - there may be some syntax errors - didn't check the code.

Also, why use 10 different files? You could have it use one file, but that is a change of architecture, so it's up to you.

Lastly, it is simpler to use sessions to remember that someone is logged on than to use a hidden form field.

Heh the for loop has a logic error...
You increased $i when it should  be decreased

Anyhow I made the mods...

I prefer 10 files (It is a matter of preferance)
I Could use sessions but that is less minimalist...

Anyhow Thanks :)

Alex

---

### Post by 7Priest7 on 2007-11-01
I added limits to amount of charcters...

I not only did it to the form (that can be hacked)

I did it to the PHP...


Enjoy :)

Alex

---

### Post by smartbei on 2007-11-02
Another thing:

In php, you shoudn't be doing things like:
[php]
if ($_POST['u'])
{
...
}
[/php]
Because if $_POST['u'] is set to '0' it will evaluate to false. What you should be using is:
[php]
if (isset($_POST['u']))
{
...
}
[/php]
That actually checks if the variable was set (is defined).

---

### Post by ankursethi on 2007-11-02
Heed smartbei. Something like that utterly killed a project of mine when several people were using it.

---

### Post by 7Priest7 on 2007-11-02
I added strip_tags

Some1 showed me how they could use some Javascript to screw up my site

So I fixed that...

Smartbei You may be right with the isset however if some1 cannot think of a more unique user name than 0 or false they do not deserve to chat with me or any1 around me...


Enjoy :)

Alex

---

### Post by smartbei on 2007-11-03
Well, for username you may be right, but you are doing the same check on the string sent as a chat message. It is quite possible that someone may send 0 as their message.

---

### Post by 7Priest7 on 2007-11-03
> **smartbei said:**
> Well, for username you may be right, but you are doing the same check on the string sent as a chat message. It is quite possible that someone may send 0 as their message.

Give a scenario?

Please and Thanks :)


Alex

EDIT: A scenario that would really happen... Nobody will ever ask a math question...

---

### Post by smartbei on 2007-11-03
Oh come on... You don't have to correct this if you don't want to, but this could definately be a small bug.

Person A: What is 5-5?

Person B: 0

Person A: Hello?

Person B: I said '0'

Person A: I didn't get anything

... :D

---

### Post by 7Priest7 on 2007-11-03
> **smartbei said:**
> Oh come on... You don't have to correct this if you don't want to, but this could definately be a small bug.

Person A: What is 5-5?

Person B: 0

Person A: Hello?

Person B: I said '0'

Person A: I didn't get anything

... :D

Not that I think people ask math questions while chatting...

I added it anyways 


Enjoy :)

Alex

---

### Post by 7Priest7 on 2007-11-03
I added some auto refresh javascript...
It waits 10 seconds and if there is nothing in the users chat input...
It refreshes

This feature is to try to give a live chat feeling...

Enjoy :)

Alex

---

### Post by Wybiral on 2007-11-03
> **7Priest7 said:**
> I added some auto refresh javascript...
It waits 10 seconds and if there is nothing in the users chat input...
It refreshes

This feature is to try to give a live chat feeling...

Enjoy :)

Alex

Where's the AJAX? Refreshing is so 90s...

---

### Post by 7Priest7 on 2007-11-03
> **Wybiral said:**
> Where's the AJAX? Refreshing is so 90s...

I didn't ask for moronic comments!
I will code however I want...
If you want to use bathtub cleaner to code go ahead!!!
Bathroom cleaner language is not for me(Mostly because I do not know it)!!!

Please only give helpfull comments...

Alex

---

### Post by CptPicard on 2007-11-03
> **7Priest7 said:**
> 
I will code however I want...


And this is actually a pretty bad argument, as it can be used to sidestep any and all criticism/commentary, essentially stopping discussion whenever it gets inconvenient. Emergency appeals to subjectivity are actually a rather common cop-out ;)

---

### Post by 7Priest7 on 2007-11-03
Also there are not enough free hosts with AJAX for me to get into it...

I am a minimalist...

I never pay for hosting/domain names/any software


Alex

---

### Post by smartbei on 2007-11-03
All AJAX is is javascript that calls a server-side script that can be coded in the language of your choice - php I would assume, so the web host does not care in the least.

Besides, I believe Wybiral was joking.

---

### Post by ankursethi on 2007-11-03
You might want to take a look into AJAX. Google would definitely be the best starting point :
[http://www.google.com/search?hl=en&client=opera&rls=en&hs=yCh&q=AJAX+tutorial&btnG=Search](http://www.google.com/search?hl=en&client=opera&rls=en&hs=yCh&q=AJAX+tutorial&btnG=Search)

I assume you're already familiar with AJAX apps, but if not, check out Google Suggest. Very nifty piece of work.

You already know PHP, and XHTML (you *did* look into that, right?) and JavaScript (I assume you do, correct me if I'm wrong). Adding AJAX (actually just fancy stuff with JavaScript and the XMLHTTP request object, no biggie but very useful) to your arsenal will make you a really great web programmer :).

EDIT :  I just read the above comment. AJAX is *not* something that you have to install on the server side. It's just a fancy way to interact with the PHP/Perl/Python/Ruby/BlahBlah script that resides on the server. You can send POST and GET requests to the script *without* having to reload the page. Better check out the Wikipedia article. I'm no web programmer, so I'm not qualified for this.

---

### Post by 7Priest7 on 2007-11-03
> **ankursethi said:**
> You might want to take a look into AJAX. Google would definitely be the best starting point :
[http://www.google.com/search?hl=en&client=opera&rls=en&hs=yCh&q=AJAX+tutorial&btnG=Search](http://www.google.com/search?hl=en&client=opera&rls=en&hs=yCh&q=AJAX+tutorial&btnG=Search)

I assume you're already familiar with AJAX apps, but if not, check out Google Suggest. Very nifty piece of work.

You already know PHP, and XHTML (you *did* look into that, right?) and JavaScript (I assume you do, correct me if I'm wrong). Adding AJAX (actually just fancy stuff with JavaScript and the XMLHTTP request object, no biggie but very useful) to your arsenal will make you a really great web programmer :).

Thanks...

I thought AJAX was a language all its own

Thank You :)

Alex

---

### Post by Wybiral on 2007-11-03
> **smartbei said:**
> ... Besides, I believe Wybiral was joking.

I was joking with the 90s comment, but I wasn't joking with the fact that no self-respecting chat application should be without AJAX these days.

---

### Post by 7Priest7 on 2007-11-03
I am now learning AJAX...
I may add the feature later...

Thanks all :)

Alex

---

