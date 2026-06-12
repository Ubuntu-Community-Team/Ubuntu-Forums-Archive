---
title: "run php locally"
date: 2011-11-19
forum: Programming Talk
---

### Post by irv on 2011-11-19
I know I am missing something. 
I haven't done any php programing for awhile now, and had to make some changes to some code and test them. I wanted to do this locally, so I followed the instruction on this page: [https://help.ubuntu.com/8.04/serverguide/C/php5.html]("https://help.ubuntu.com/8.04/serverguide/C/php5.html")
I have everything installed, but when I go to run a php file in a browser, it won't run. it just ask me if I want to open it in a text editor.
What am I missing?
Thanks for the help.

I can run the php file on my server but no locally.

---

### Post by CharlesA on 2011-11-19
You have to run it from the web server instead of as just opening the file.

Do you have php5 installed?

---

### Post by irv on 2011-11-19
> **CharlesA said:**
> You have to run it from the web server instead of as just opening the file.

Do you have php5 installed?

Yes I installed:
```
sudo apt-get install php5 libapache2-mod-php5
```
```
sudo apt-get install php5-cli
```
```
sudo apt-get install php5-cgi
```
```
sudo apt-get install php5-mysql
```
```
sudo apt-get install php5-pgsql
```
I also ran 
```
sudo a2enmod
```
and restarted mods
and then ran 
```
sudo /etc/init.d/apache2 restart 
```
To restart apache.

If I put .php files in the /var/www/ directory they still will not run. They also want to display code.

---

### Post by CharlesA on 2011-11-19
Does it run if you run it with php?

```
php /path/to/file
```

---

### Post by madoba on 2011-11-19
If I remember correctly I think I ran into this problem. Those files that you are trying to run are not web pages but are scripts designed to be run from the command line.

When I first started learning PHP, I wanted to learn it to create webpages, but If my memory serves me right,  I noticed some code examples i was learning and creating were scripts designed to be run at the console in order to introduce you to a php concept and not designed to be run in a browser.  

So Yes I've seen that, and that's the problem. The browser is trying to open the file because it's not a web page (no html) etc..

---

### Post by irv on 2011-11-19
They were web pages, and for some reason everything is working now. I don't know what made it start to work, but I have been trying so many things it is hard to say what did the trick.
I do appreciate all the help and the input on this. A bunch of heads are better then one. And mine was a little foggy. I will mark this solved even though I don't know what solved it.

---

### Post by madoba on 2011-11-19
> **irv said:**
> They were web pages, and for some reason everything is working now. I don't know what made it start to work, but I have been trying so many things it is hard to say what did the trick.
I do appreciate all the help and the input on this. A bunch of heads are better then one. And mine was a little foggy. I will mark this solved even though I don't know what solved it.

Ok what  I remembered was problems I had learning php on my windows system at work and I was not running a web server configuration on my desktop.

Anyway some final thoughts, like you I have a lamp (linux, apapche, mysql php) configuration. 
I just noticed if I pull up a php file in my home documents it comes up like you described, like it wants to open the document. However that same document copied over to /var/www and pulled up in the browser works properly. Even its just a small script like below.

<?PHP
print file_get_contents("/home/lsoutput.txt");
?>

---

### Post by irv on 2011-11-19
I have a web server which is live on the Internet with a static ip and a URL address and a web server on my laptop where I do all my design and editing. I keep all my files I am working on in the var/www directory so I can do a reload on the page in my browser ever time I edit a file. When I get it just the way I want I upload it to the live server and I am back in business.

By the way the site I was working on is all php file, no HTML. I have one menu that is displayed on 24 pages so if I need to change or add something to the menu I only have to do it once and they all change. This site work with audio files which are stored elsewhere else on the server.

Web design is something I like to do, but only as a hobby. I did it for money for awhile, but that took the fun out of it. Besides I am getting to old to worry about money, I can't take it with me anyway.

---

### Post by CharlesA on 2011-11-19
> **irv said:**
> 
By the way the site I was working on is all php file, no HTML. I have one menu that is displayed on 24 pages so if I need to change or add something to the menu I only have to do it once and they all change. This site work with audio files which are stored elsewhere else on the server.

Mine is set the same way. I use php templates for the <head> area of the page and for the navbar. So much easier then having to add them to each page on their own..

---

