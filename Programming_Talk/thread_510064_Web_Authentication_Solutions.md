---
title: "Web Authentication Solutions"
date: 2007-07-26
forum: Programming Talk
---

### Post by rock freak on 2007-07-26
Afternoon guys. Got a quick question after a couple of hours trawling the internet looking for it and I have had no joy.

Basically I am looking for a web based authentication system for our company website.  My MD is looking for a paid solution due to the support issues which doesn’t make my task any easier.

We need to have a secure area on the web site of which only authorized customers can view the spec sheets in that area.

If I can't find anything then ill convince him ill make it for him!!
Cheers in advanced guys!!

Ollie

---

### Post by smartbei on 2007-07-26
Wouldn't using a simple MySQL database for users with an 'allowed' field work? Then just use whatever your website runs on (PHP, Python, Ruby, whatever) and access the database to check if the user has access privleges.

---

### Post by rock freak on 2007-07-26
yup it would be but my MD wants a paid solution incase the thing breaks :S  might just say well ill build and u pay me :D lol

---

### Post by Limpan on 2007-07-26
You could use basic authentication and run it over ssl. That can be handled entirely by your server software; Apache, Lighttpd or IIS (I have done it with the two first).
[http://httpd.apache.org/docs/2.2/howto/auth.html]("http://httpd.apache.org/docs/2.2/howto/auth.html")

---

### Post by rock freak on 2007-07-26
haha its alright ive managed to convince him that i should do it :D chers for the help guys!!

---

### Post by Note360 on 2007-07-26
I would say the mysql is the best make sure to atleast md5 the passwords.

---

### Post by vcardona on 2007-07-27
> **Note360 said:**
> I would say the mysql is the best make sure to atleast md5 the passwords.

MD5 has been broken.  You should use one of the SHA family of hashes.  Also, the Java Servlet spec has some stuff for authentication and authorization if you're interested in going that route.

---

### Post by rock freak on 2007-07-27
> **vcardona said:**
> MD5 has been broken.  You should use one of the SHA family of hashes.  Also, the Java Servlet spec has some stuff for authentication and authorization if you're interested in going that route.

Indeed the MD5 has been.   I have been looking into other ways of securing the password.  I will be using PHP and MySql running over 128bit SSL.

Anybody got any suggestion as to which method will be the best??

---

### Post by Limpan on 2007-07-27
When I have to store passwords in a database I do like this:

1) Generate a random string, about 6-8 characters long. This is known as the salt.
2) Append the salt to the password (that you make your users make at least 8 characters) and hash the entire thing with SHA256. [PHP Manual pages on hash functions.]("http://se.php.net/manual/en/ref.hash.php")
3) Save the salt and the hashed password in the database.

This way, if hacker X manages to retrieve your database contents he won't know that user Y has the same password as he does based on a matching hash. For all he knows, every user could have identical passwords but it won't show in the database.

---

### Post by rock freak on 2007-07-27
Ahh clever the passwords will be randomly generated any way so that wont be a problem.  Will just generate two random strings!!

Ill have alook at that link later on!! 

Any reason for SHA-256 as aposed to any of the other SHA's??

Cheers
Ollie

---

### Post by Limpan on 2007-07-27
No particular reason for SHA-256 except that it's good. (They used it in Agile Web Development with Rails and I figure that if it's good enough for them it certainly is for me!)

---

### Post by Note360 on 2007-07-27
I said ATLEAST md5 it. I myself have been using a salt with a sha1, but my friend stupidly doesnt use the function that unincodes it he forces it into sha1 by stripping the salt from the end and thencomparing the sha1 when all you needed to do was plug both into a function and it would return a boolean

---

### Post by pmasiar on 2007-07-27
> **rock freak said:**
>  the passwords will be randomly generated any way so that wont be a problem.  

if user cannot remember password easily, she will write in on post-it and place on monitor. :-( here goes your safety.

[How to Pick a Safe Password](http://wolfram.org/writing/howto/password.html)

---

### Post by Limpan on 2007-07-27
> **pmasiar said:**
> if user cannot remember password easily, she will write in on post-it and place on monitor. :-( here goes your safety.

[How to Pick a Safe Password](http://wolfram.org/writing/howto/password.html)

I would have to disagree with you. It's definitely not that simple. I.e. at my home computer I sometimes write down my password on a note that I stick to the back of the monitor. Is that unsafe? No. How's that? Since I trust everyone that I let close to my monitor that's perfectly safe. This way I can use a very good password that I would normally not be able to remember. It would also allow me to choose different passwords every time a need one and all of them could be 16 chars long and be extremely good.

It could also be the other way around. Since users aren't allowed to write down their passwords and store them somewhere safe ('safe' depends on the situation, naturally) they tend to use the same password everywhere and it's usually an easy to remember combination. This often translates into a bad password being used everywhere instead of say, 5 or 6 different passwords written to a note that's in your wallet (or somewhere considered safe).

That's my 2 cents. I have a method I've used when I need a password. It's simple and it could make it a lot easier for you to create a good password AND remember it more than 30 seconds later. ;)

1) Write down a weird sentence but make it easy to remember. I.e. You adore the Matrix movies then it could be something like this:
```
Neo is the best but Trinity is the coolest and they both rock.
```
2) Take the first letter from each word.
```
NitbbTitcatbr
```
3) This is probably way better then all the real bad passwords. But to make it a little better change a few letters and add some numbers and signs. I would replace letters that occurs twice in a row with the total number of times that specific letter occurs. I would insert a #!. or some other character someplace where it makes sense to me. I would probably end up with this:
```
N!it3T!itcAt#br
```

In my opinion that's a kick *** password that I would be able to remember without putting it on a note.

---

### Post by rock freak on 2007-07-28
Random password won't be that much of a security issue with this implementation as we are just restricting the access to the spec sheets to certain clients and not our competitors.

So even if you did ask them to choose a password then they will just writer it down and share it with everyone else in the office! 

So id rather have a strong password that several people know as a posed to a easy password that some one else could crack or guess easily.

---

### Post by Limpan on 2007-07-28
That sounds lika a good decision.

---

### Post by smartbei on 2007-07-28
> **rock freak said:**
> Ahh clever the passwords will be randomly generated any way so that wont be a problem.  Will just generate two random strings!!
Ollie

You can't generate two random strings - you need the salt to be constant, otherwise you can't do comparisons. Just generate the salt once and save it somewhere.

---

### Post by Limpan on 2007-07-28
> **smartbei said:**
> You can't generate two random strings - you need the salt to be constant, otherwise you can't do comparisons. Just generate the salt once and save it somewhere.

I believe that's what he meant to do. He will generate the salt when he generates the initial random password. Of course both of them will be constant. That's the only way for his statement to make any sense at all. :) The point is that the salt should be randomly generated for it to be useful. If all users had the same password there wouldn't be any point in having it at all.

---

### Post by rock freak on 2007-07-28
They will both only need to be generated once anyway!!! so they will be static will have to start writing it this week!!!

---

### Post by smartbei on 2007-07-28
I guess I misunderstood then :D.

---

### Post by pmasiar on 2007-07-28
> **Limpan said:**
> I would have to disagree with you. 

Funny you disagree with me and then elaborate for half a page to describe safe password guide like the one I linked to :-D

---

### Post by Limpan on 2007-07-28
pmasiar: Sorry. I disagreed with the part where it sounded as 'you shouldn't even bother trying to pick a good password since they will write it down on a note'. Now when I read the linked page a little more carefully i realise there's a whole section about a similar/identical aproach. I guess I agree more or less with you.

---

### Post by pmasiar on 2007-07-28
> **Limpan said:**
> pmasiar: Sorry. I disagreed with the part where it sounded as 'you shouldn't even bother trying to pick a good password since they will write it down on a note'. Now when I read the linked page a little more carefully i realise there's a whole section about a similar/identical aproach. I guess I agree more or less with you.

No offense.

But I never said 'you shouldn't even bother trying to pick a good password since they will write it down on a note'. All I did was: I warned against "strong" random passwords (and yes, i have first person experience with those). Instead, I suggested strong non-random password based on a easy to remember sentence, like you did.

There was even serious experiment in a university, different methods for passwords were compared (but I lost link. I shoud've add it to wikipedia instead :-( )

Bonus suggestion for your password: Instead of "NitbbTitcatbr" you can have "N=t1bT=tc&t2r", just use = as 'is' and '&' as 'and'. Even stronger, eh?

---

### Post by Limpan on 2007-07-29
I made some calculations on it. These are only approximations, since words shouldn't be used it will be considerably weaker if a dictionary can be used to crack the password.

6 letters (aA) - **1.977 × 10^10** combinations  <-- this is too short
6 letters (aA1) - **5.6 80 × 10^10** combinations
6 letters (aA1#) - **4.04 6 × 10^11** combinations

8 letters (aA) - **5.346 × 10^13** combinations
8 letters (aA1) - **2.183 × 10^14** combinations
8 letters (aA1# - **2.992 × 10^15** combinations <-- usually considered a good password, if random

12 letters (aA) - **3.909 × 10^20** combinations
12 letters (aA1) - **3.226 × 10^21** combinations
12 letters (aA1#) - **1.637 × 10^23** combinations

(a = lower case, A = upper case, 1 = numbers 0-9, # = 24 symbols: !"#%&/|\()[]=?+-*.,;:@€$)

You can see that when using symbols in your password you really don't gain that much. So to say that a password get's a lot stronger by adding some symbols to the pool of available characters might be the case sometimes. But it's only about 10 to 100 times stronger. If you increase the length from say 8 to 12 characters you'll get a 1 000 000 times stronger password.

It's clear to me that length is way more important then the number of available characters (as long as you have sufficient, say lower and upper case).

---

### Post by pmasiar on 2007-07-29
> **Limpan said:**
> You can see that when using symbols in your password you really don't gain that much. ...  it's only about 10 to 100 times stronger. 

It's clear to me that length is way more important then the number of available characters (as long as you have sufficient, say lower and upper case).

It is funny to say that something 100 times stronger is about the same! Difference is, can be your password be cracked overnight (10 hours), or will it take 1000 hours == more than a month of runtime?

Obviously you want to have password which is both long and with wide variety characters. Adding special characters, which are as easy to type as normal, you add greatly to security of your password.

---

### Post by Limpan on 2007-07-29
I know it sounds a little weird but when you compare to what you can get if you choose a longer password. A 100 times is not really that much. It might save your day thou.

---

