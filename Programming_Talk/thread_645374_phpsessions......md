---
title: "php:sessions....."
date: 2007-12-20
forum: Programming Talk
---

### Post by hockey97 on 2007-12-20
HI I am having problems with my sessions.

I have a login system where I want to have a session being able to be passed.

WHen the users uploads pictures or files I want the link to be saved in the database with also the username. I want to do this using a session that holds the username that is logged in.

however I made the script alread but when I try it I only get the image or file link everything else like the username dosen't show. I done test by echo ing the part where I call the session and nothing spits out.

seems somthing is wrong on passing the session along the to the pages.

I am using this  $_SESSION["username"] = $username; on the first page the login page and want to pass this along to the other pages.

---

### Post by aks44 on 2007-12-20
Did you use [session_start()]("http://fr2.php.net/manual/en/function.session-start.php") in your scripts?

---

### Post by apakatt on 2007-12-20
A bit off-topic but using usernames as login-sessions is very bad from a security point of view.

Scenario:
Let's say I log in at your site. I view the content of my cookies / sessions and notices that my session contains my username. Because of that I change the value of my session to another username - like your username.
All of a sudden I'm signed in as you.

---

### Post by hockey97 on 2007-12-20
yes I used  session_start()  but I put that on all pages right at the top.

apakatt thanks for the finding I know that, but  I  am also stuck on how I can make a secure system yet use the sessions  to spit out the username becuse the uers could upload files and the script I made has  their own page where they can display their images. I want when they upload a file to grab the session info about the username that is currently loged in and then input the link of that image and also the username in that database so that on that users profile I can display all his photo's or files on his page.

If I  can't  figure out who uploaded the pics or files then their is no way I can display the users photo's on his page, becuse I won't know who uploaded what.

is their any way where I can securely send a session or somthing that I can pass a variable like the username or a key that would point to the person name something in a secure fashion so that I can still know who uploaded the stuff so I can display it on the right user's page.

I have session_start();  and also  $_SESSION['username'] = $username;

I was also suggested to pass the username through headers.  I  really want a secure way on doing just passing something on each page to I  can verify who is login and  who uploaded stuff  bascily their activites  so no one would get other users pics or so.

---

### Post by hockey97 on 2007-12-20
I read up on php sessions and  what I understood it that you just need to have sessions_start() function then create your own $sessions values.

Then during any page that links off of  your login page  you should be able to just call the $session like what ever you name it .

so for example
  login script thing :

sessions_start();
$_SESSION["username"] = $username;
and so on........

______________________________---
Now the users page after he is logged in.
session_start();
$_SESSION["username"] 

if(isset($_SESSION["username"] ))
{ the user is good};
else{ the user stinks lock the session hahahah];


Mainly I was to pass the session around meaning all my pages.
and each pages will first check if the user is logged in  by using the sessions info stuff.

Is this right on how to pass the sessions? That's how I understood it. I have it working until  a page where you can unpload files and photos ect.

I wanted to grab the seesion info  meaning the username and save that with the photo or so in the database.

the database has a row for username storage and the link to where the image or file is at.

---

### Post by guilly on 2007-12-20
I'm no PHP expert however I believe the session_start() needs to be called before any other php code? can anyone else back me up on this?

---

### Post by LaRoza on 2007-12-20
> **guilly said:**
> I'm no PHP expert however I believe the session_start() needs to be called before any other php code? can anyone else back me up on this?

That is true. Just stick it at the top whenever you use sessions.

---

### Post by hockey97 on 2007-12-20
ok, well  I just figured out what was wrong I didn't have something turned on in php.ini 

the ob was off. 

it's working now. but thanks for the replies though.

---

### Post by hockey97 on 2007-12-21
Well since someone brought it up.  I  really would like to know  how to make it secure.

so  if the users can instead type their uername they put another username then those people get into other peoples account.

What should I do to stop them from during such a thing.

Is their a way I can grab the user's ip address when registering?

---

