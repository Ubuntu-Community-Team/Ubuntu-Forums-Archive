---
title: "My First Programming Language [Please Help!]"
date: 2015-06-23
forum: Programming Talk
---

### Post by nick198 on 2015-06-23
Hello everyone,

So I decided to learn programming and after I've learned HTML & CSS i want to learn a real programming language [PHP].

Now, my problem is that I really don't have much experience with neither programming nor linux/ubuntu. So I have problems in writing functions (I've tried to do the course on PHP on Codecademy and got to about 60% and now I'm stuck, since I can't manage to write functioning functions like printing out a random letter from my name etc. I know the basic things like arrays, rand, substr, strtoupper etc. but I can't manage to put them together the way so they actually make sense. I also don't know how to write PHP on my Ubuntu PC (Now I kinda figured it out following some tutorials but I still have no idea about apache2 and MySQL and what they actually are and all of this stuff).

Can someone please push me a little bit to the right path? Like giving me some good resources, what and in what order to learn. 
It would also be totally amazing if someone would be able to mentor me a little. I really do have a short time frame to learn PHP (6 months to a year) and would highly appreciate any help. I do think it's doable since I'm willing to put in 4-6 hours of learning a day + about 15 hours over the weekends.

Thank you all so so much!:)
Best regards
 - Nick

---

### Post by flaymond on 2015-06-23
I don't know much about PHP, but I may give you the steps and short guide to programming PHP on Ubuntu. :D

# Step 1

Find information what is all about Apache2, PHP, and MySQL. You can Google for this, and you should get a tons of relevant answers.

# Step 2
Start installing the tools especially LAMP (Linux, Apache2, MySQL, PHP5) # Linux is the platform, and I believe you can guess after this, if it's WAMP or XAMP.

```
 sudo apt-get update # update your repository

sudo apt-get install apache2 # install apache2

sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql # install MySQL and dependencies

sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt # install PHP5 and dependencies

```

# Step 3 - Now, test your php file (info.php), - 

* Create the test file (in this file, it will display your php5 in the web browser)
```
 cd /var/html/www && sudo printf "<?php\n phpinfo();\n?>" >> phpinfo.php # cd to the directory and create a file name info.php with a few codes in it
```

* Restart your apache2 web server
```
 sudo service restart apache2
```

* Now run it in your web browser (with firefox)
```
firefox localhost/info.php #  if everything fine, it will run the file and will display the php5 info. 
```

# Further information - [https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)
#                             Linux/Unix beginner tutorial - [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

Tips 1 - It's very good to know about your platform, especially the file system, simple commands of Linux and your web server (Apache2).
Tips 2 - Colloborate with others, in FOSS project (Free Open Source Software), anything including in Github, Launchpad, Bitbucket.
Tips 3 - Find the project you interested with, in this case you might looking for php project.
Tips 4 - Try other technologies that fun, and amazing or full of 'magic' to you. Might be HTML5 with canvas, ActionScript (flash game) and more.

# I'm not a professional programmer, and I'm just a beginner, too. However, I'm not a web developer, I'm more to desktop application programmer and I'm still learning to be better! ;)
# Just do something fun for you to keep you stay motivated. In my case, 'build something'.



Thanks! :D

---

### Post by branau on 2015-06-23
[This article]("http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program") was given to me by one of the other members of the forum and I read it all the time whenever I need to get a sense of direction. Also, another thing that will get you to keep pushing forward and learn new things is to "scratch your itches" as the programmers like to say. Once you've got a decent foundation and you know more or less how the language works, start using it. Read sample code that you come across (and don't just wait to come across it, look it up and find some, and then try to really figure out what's going on), and then use some of the things that you come across to implement into your code. If you want to do something but you're not sure how, look it up, ask questions if you really can't find anything at all. Post your code to a forum and ask for tips on how to improve it, etc. The best thing is to just keep using it and keep challenging yourself to try new things, and most importantly, have fun with it.

I can't help you out with PHP either, as I've been learning Python and now C (I actually took my first steps with Python at Codeacademy too), but learning a programming language is pretty much the same no matter which language it is. Don't be afraid to ask stupid questions but just make sure you do research on your own first and consider asking for help from a forum as a last-ditch effort. Ideally you should just figure things out, since being a programmer is basically being a professional problem solver :P

---

### Post by flaymond on 2015-06-23
> **William_Brawner said:**
> [This article]("http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program") was given to me by one of the other members of the forum and I read it all the time whenever I need to get a sense of direction.

[SIZE=5][SIZE=4]+1[SIZE=2]

TheFu is a kind in this forum, for giving advice to others including me about programming stuff! ;)
[/SIZE][/SIZE][/SIZE]

---

### Post by branau on 2015-06-23
> **InterProg said:**
> [SIZE=5][SIZE=4]+1[SIZE=2]

TheFu is a very good guy in this forum, for giving advice to others including me about programming stuff!
[/SIZE][/SIZE][/SIZE]

Agreed. TheFu won't always give you a straight answer; sometimes he'll just point you in the right direction and say "go look it up" but that's honestly way better for your learning process. If TheFu answers you, you'll learn something new every time. Guaranteed.

---

