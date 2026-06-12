---
title: "positioning elements using css"
date: 2007-02-23
forum: Programming Talk
---

### Post by Greykrrr on 2007-02-23
hi

When working on a webpage yesterday I came across a curious problem. When I try to position a background image in Firefox I can only use absolute measures. I put this in my header

```

	<style type="text/css">
	body	{	background-image:url(bg.jpg);
                           background-position:100% 80%;
                            background-repeat:no-repeat;
			}
	</style>

```

However the image is displayed at the right horizontal placement, but seems stuck vertically. If I replace the % with px it works fine. What am I not seeing?

---

### Post by derby007 on 2007-02-23
Did you try :

top left
top center
top right
center left
center center
center right
bottom left
bottom center
bottom right

instead of :  x%  x%

---

### Post by Greykrrr on 2007-02-23
Yes and they work fine. However I don't want to place my image right near the edge of the page but would like to move it slightly up relative to the page size so I need the percentage values to work.

Is your signature a question or a joke that I don't get?

---

### Post by Mirrorball on 2007-02-23
Remember that it's 80% of the height of the body element, not the height of the browser window.

---

### Post by Greykrrr on 2007-02-23
> **Mirrorball said:**
> Remember that it's 80% of the height of the body element, not the height of the browser window.

Yes! That was it exactly! ... so no. I didn't know that...

And that asks another questions then... How to I make the body element automatically fill up the browser window? Or alternatively, place elements relative to the lower right corner instead of the upper right?

---

### Post by finer recliner on 2007-02-23
> **Greykrrr said:**
>  How to I make the body element automatically fill up the browser window? Or alternatively, place elements relative to the lower right corner instead of the upper right?

i dont think you can MAKE the body fill the browser window from the fact that when there is too much data too display, you must SCROLL to see the rest of the data being displayed. 

i know there are functions to find the user's browser window dimensions/screen resolution. stuff like that. i dont know them off hand, it may be in javascript. i remember its one of those tools that is NOT cross-browser compatible (you probably need 2 different variants of the function if the user is using IE6 or firefox)

---

### Post by Mirrorball on 2007-02-23
Yes, it's Javascript if you really must.

---

### Post by Greykrrr on 2007-02-23
> **Mirrorball said:**
> Yes, it's Javascript if you really must.

That sucks! Even implementing two different javascripts to do this poses the further problem that the java script I'm using to update two frames at once is blocked by default by IE7.

It's stuff like that this that just takes all the fun out of creating homepages.

---

### Post by Mirrorball on 2007-02-23
> **Greykrrr said:**
> Even implementing two different javascripts to do this poses the further problem that the java script I'm using to update two frames at once is blocked by default by IE7.
Frames?! :o Eliminate the frames and you won't need any Javascript. :)

> **Greykrrr said:**
> It's stuff like that this that just takes all the fun out of creating homepages.
If you just accept it as it is, you will have fun again. Your page doesn't have to look exacly like you imagined (and it won't in different browsers, that's guaranteed).

---

### Post by derby007 on 2007-02-23
>>> Is your signature a question or a joke that I don't get? >>>
??? google it : its the ultimate Q ???

---

### Post by Greykrrr on 2007-02-24
> **Mirrorball said:**
> Frames?! :o Eliminate the frames and you won't need any Javascript. :)

I was just about the write how else to do it.. but I suppose that this is a fair point. I just like the idea of having two seperate files for the menu and the text on the main page but it isn't strictly nescessary.

What I really need in HTML is the ability to use include files like I know you can in php.

Ah well... I should just stop complaining and get on with it. I got my answer I am kind of working around it, so it's not really all that bad :)

---

### Post by Mirrorball on 2007-02-24
> **Greykrrr said:**
> 
What I really need in HTML is the ability to use include files like I know you can in php.

Include the files with PHP in your computer, then save the output and upload it to your server (wget makes saving a whole site easy). Who needs Dreamweaver templates? ;)

---

### Post by Greykrrr on 2007-02-24
> **Mirrorball said:**
> Include the files with PHP in your computer, then save the output and upload it to your server (wget makes saving a whole site easy). Who needs Dreamweaver templates? ;)

You'll have to forgive me asking this but how? I don't know php and I'm not sure where to find a good resource for this kind of thing. Is it possible for you to direct me somewhere where I can learn more about that?

---

### Post by Mirrorball on 2007-02-24
The first thing is to install Apache and mod_php.
```
apt-get install apache2 libapache2-mod-php5
```
Then in your browser go to [http://localhost/](http://localhost/)
Does it work?

---

### Post by Greykrrr on 2007-02-26
> **Mirrorball said:**
> Does it work?

Yup. I get an index page with the folder apache2-default in it.

What next?

---

### Post by Mirrorball on 2007-02-26
Create a new file in a text editor and write:
```

<?php
phpinfo();

```
Then save it as /var/www/phpinfo.php and go to [http://localhost/phpinfo.php](http://localhost/phpinfo.php) . If you see a very long page of PHP information, everything is OK. If it doesn't work, go to /etc/apache2/mods-enabled/ and check if php5.load and php5.conf are there. If they are not, execute in a terminal:
```

cd /etc/apache2/mods-enabled/
sudo ln -s /etc/apache2/mods-available/php5.conf .
sudo ln -s /etc/apache2/mods-available/php5.load .
sudo /etc/init.d/apache2 restart

```
Then go to [http://localhost/phpinfo.php](http://localhost/phpinfo.php)

---

### Post by Greykrrr on 2007-03-05
Hi.

Don't know if this thread is still active. I have been crazy busy with other stuff so I hadn't had time to try this but yes. I got a long page of php information when I did that. Really nice actually.

Where to go from here?

---

### Post by Mirrorball on 2007-03-05
You can start playing with PHP now. Your server is working (make sure it's behind a firewall). You can put your pages in /var/www and they will show up when you go to [http://localhost/]("http://localhost/phpinfo.php")
To use PHP in a page, save it with the .php extension. Now if you want to include a navigation bar that is in a separate file nav.php, just insert this code:
```

<?php include 'nav.php' ?>

```
and it's going to be included. You won't need frames anymore.

---

### Post by Greykrrr on 2007-03-05
> **Mirrorball said:**
> You can start playing with PHP now. Your server is working (make sure it's behind a firewall). You can put your pages in /var/www and they will show up when you go to [http://localhost/]("http://localhost/phpinfo.php")
To use PHP in a page, save it with the .php extension. Now if you want to include a navigation bar that is in a separate file nav.php, just insert this code:
```

<?php include 'nav.php' ?>

```
and it's going to be included. You won't need frames anymore.

Now that is going to make my life so much easier :)

Thanks for all your help. All there is to do now is play with it! 

One last thing though. Since there isn't a php part in the the programming resources sticky, would you happen to know a place to start if I should want to go into php at some point?

---

### Post by Mirrorball on 2007-03-05
If you already know a programming language, start with the tutorial at [http://www.php.net/manual/en/](http://www.php.net/manual/en/)
If not, you'll have to ask Google...

---

### Post by farid_slc on 2008-03-02
About your question on making the webpage fit the users screen. You do not need javascript, you just use percentage unit for your elements widths. For example, if you have a header, you can set its width to 100% and it will fill the users screen no matter what screen resolution. You should use this on all your elements. Test it out with different resolutions. 

The point to get is to use percentages as your width unit. It doesnt have to 100%.

Thank you.

---

