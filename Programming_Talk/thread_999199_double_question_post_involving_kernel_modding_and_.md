---
title: "double question post involving kernel modding and webpage making"
date: 2008-12-01
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-12-01
question one:

for what ever reason ive become interested in making my own OS...nothing special...just a CLI like unix or dos...so i though might as well check out the linux kernel and see how it ticks and maybe mod it a little (no idea how but ive heard of people doing it)

is this dangerous? also any good links or advice on what i might tweak if anything

question two:

whats the easiest way to make a webpage without a drag and drop WYSIWYG editor?

---

### Post by Idefix82 on 2008-12-01
> **jimi_hendrix said:**
> 
whats the easiest way to make a webpage without a drag and drop WYSIWYG editor?

Learn HTML (there are thousands of tutorials on the web), set up gedit to suit your needs (see for example this extremely useful blog post: [http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html]("http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html")) and you are ready to go.

---

### Post by jimi_hendrix on 2008-12-01
i already know html :)...but i suppose the next step is CSS which i dont know...can you make a webpage in PHP or is that more the background stuff?

---

### Post by Idefix82 on 2008-12-01
Yes, the next step is definitely css.

You use PHP to produce the HTML code dynamically on the server before it's passed on to the client. It's used for all sorts of logic that make the look of the page depend on the circumstances.

For example on my page I have a picture gallery. Normally, you would have to create a table by hand and in the cells you would have to enter the file names of the thumb nails with links to full size pictures. If you want to include a new picture, you have to include a new cell by hand and enter the file name of the thumbnail into this cell. Then you have to turn it into a link to the full size picture.
Instead, you can write a php page, that goes through your picture folder and creates the table dynamically. The browser only sees the generated html code but it was generated on the server using php.
There are thousands of other examples for when PHP would be useful.

---

### Post by jimi_hendrix on 2008-12-01
so basically html is the only way to handwrite a website...javascript and php just do the logic

---

### Post by jimi_hendrix on 2008-12-01
is there an html editor in linux that will show what the page looks like as im adding HTML

in windows, while i was learning...i used chami...anything like this

---

### Post by rtoot3 on 2008-12-01
you use html with php for example
```

<html>
<head>
<title>example</title>
</head>
<body>
<?php echo 'this is php'; ?>
<p>but you can also use html<p>
</body>
</html>

```
and then you could save that as something like example.php

---

### Post by rtoot3 on 2008-12-01
> **jimi_hendrix said:**
> is there an html editor in linux that will show what the page looks like as im adding HTML

in windows, while i was learning...i used chami...anything like this

this website can be helpfull
[http://w3schools.com/html/tryit.asp?filename=tryhtml_basic](http://w3schools.com/html/tryit.asp?filename=tryhtml_basic)
you enter html in the left box, then it displays what it will look like in the right box

---

### Post by jimi_hendrix on 2008-12-01
i prefer a program

---

### Post by jimi_hendrix on 2008-12-01
> **jimi_hendrix said:**
> i prefer a program

this sounds like something i might be able to do...if theres an easy API for rendering html, javascript, php, and such

---

### Post by drubin on 2008-12-01
This title is very descriptive thank you. 

These 2 topics how ever are completly unreleated and should be located in 2 different threads so that you/others will at least be able to follow the topic they can understand. 

I understand quite abit about html/web dev. But when it comes to Kernels it just flows over my head... 

Best bet would be to start learning html (see stickies)

MOD: 
Could these threads be separated?

---

### Post by jimi_hendrix on 2008-12-01
o and are there any risks with setting up my own server in my basement on an old computer?  i read the sticky about the XSS stuff...ill avoid scripting languages where i can

---

### Post by jimi_hendrix on 2008-12-02
bumpitude

---

### Post by Tomosaur on 2008-12-02
Writing your own OS is NOT an easy task - be prepared to spend a **lot** of time reading :P

As for web development, just keep a text editor and a browser open side by side - with the browser looking at the file on your hard drive. As you edit the html file, save it, then refresh the browser. Quick n easy!

---

### Post by jimi_hendrix on 2008-12-02
but if i host a website in my basement...will i get hacked?

---

### Post by brian77095 on 2008-12-02
I have my own web server up and running... But to prevent hacking I take it down most of the time and check log files religiously.

It also helped me to keep a journal for my server so that I had the commands written down...almost like a recipe book.

but to answer your question you can easily do it.  I am assuming you have a dynamic ISP?

---

### Post by s.fox on 2008-12-02
I believe their is a program called Kompozer.  It should be in the package manager.  It offers a preview of your HTML before you upload onto your server.

Hope this is helpful

---

### Post by jimi_hendrix on 2008-12-02
> **brian77095 said:**
> but to answer your question you can easily do it.  I am assuming you have a dynamic ISP?

i think so...am i still at threat if i had just html on the page...no javascript or php

---

### Post by rtoot3 on 2008-12-02
> **Ash R said:**
> I believe their is a program called Kompozer.  It should be in the package manager.  It offers a preview of your HTML before you upload onto your server.

Hope this is helpful

oh yeah! i used to use kompozer before i wrote my own code. i forgot all about it. its a really good program.

---

### Post by s.fox on 2008-12-02
You could also try quanta

```
sudo apt-get install quanta
```

glad i could help

---

### Post by brian77095 on 2008-12-02
Yes you are if you keep your server up 24/7 eventually you will be visited by someone looking to get in.  You just have to set your system up to do so early.  Read read read. Then monitor.  You can easily put all kinds of security features up. A little at a time.....as you learn.  You should be able to see if anyone has come to your server.....and if you feel worried just wipe and reload.... bring it back up more securely...  I have not had to wipe mine but like I said I only bring it up when I know I am going to be working with it....  and like I said I check the log files to see what IP addresses have been to my server.

---

### Post by jimi_hendrix on 2008-12-02
wait but isnt the point of a website to be open to the general public for viewing?

---

### Post by s.fox on 2008-12-02
> **jimi_hendrix said:**
> wait but isnt the point of a website to be open to the general public for viewing?

Not always.  I once setup a website that only has a login screen available to the public.  If you want to access then you must already have an account.  This account was setup PREVIOUS to them trying to access.  Think of it as an exclusive members only website.

Its kinda difficult to explain,  so if you need me to clarify please ask

---

### Post by brian77095 on 2008-12-02
Yes and No,

You can have a closed network and use html docs on it or in my case its sole purpose is for my learning and tweaking pleasure.  I also allow one other person access to the server and they SSH in.  This helps me test my monitoring skills and, he gets access to a working server.  When I say I only put it up when I am using it that might mean a week or two at a time.  Unfortunately I do not have a UPS and since hurricane Ike my power goes out for a few seconds once every couple of weeks.  My server is only 1mhz with 512 ram on one nic card.  It is my goal to upgrade it and have two nics one going to my cable modem/router and one going to a private network switch.  Were Ill have a printer and what have you..  

Also if you dont want to worry about security. You can just buy a domain name and have some company host it for you cheap.  Then you can run what you like on it and not have to worry about the security part as much.

I did not go that way because this way is totally free.

---

### Post by jimi_hendrix on 2008-12-02
wait...how do you get a domain then if you host it at home...and probably last question:

how much do adds pay on average on your site?

---

### Post by s.fox on 2008-12-02
Have you bought the domain yet?

If not I use this site.

[LINK]("http://www.123-reg.co.uk/")

---

### Post by brian77095 on 2008-12-02
I dont have my own registered domain name per say I use this service.  It is free and works great for me like I said I just use it for learning. 

not sure how to exactly explain it but, I sort of ride off of there domain.

so for example my web site is something like  brian77095.dyndns.com

If I wanted to pay and register a domain I could I am just not ready yet...

[https://www.dyndns.com/services/dns/dyndns/](https://www.dyndns.com/services/dns/dyndns/)



As for adds I dont know I do not have any...

---

