---
title: "Displaying .txt in webpage"
date: 2011-04-06
forum: Programming Talk
---

### Post by ki4jgt on 2011-04-06
Hey guys,

I have a really weird problem. I have a text file on Box.net, which I need to display on my site. It has information in it, so I'd rather the the user had an interesting view of that information and not just a bunch of text that they had to wade through. The information in this file will be constantly updated and probably be working like a live feed of information, b/c there's no telling how many times during the day, I will update it. All help is appriciated. Thanks.

---

### Post by deathadder on 2011-04-06
What language are you using? You can read the file in PHP and display it quite easily (see [PHP: file manual]("http://php.net/manual/en/function.file.php")).

Do you have full control over your own server? If so, you can setup a cron job to grab the file, using wget, once every X minutes and then parse the local file.

If you want any more in-depth help we'd need a bit more information about what you have available to do the job.

---

### Post by ki4jgt on 2011-04-06
> **deathadder said:**
> What language are you using? You can read the file in PHP and display it quite easily (see [PHP: file manual]("http://php.net/manual/en/function.file.php")).

Do you have full control over your own server? If so, you can setup a cron job to grab the file, using wget, once every X minutes and then parse the local file.

If you want any more in-depth help we'd need a bit more information about what you have available to do the job.

Unfortunately, I'm just using a Blogger account. from blogspot.com :-( I can't manage my own hosting. I have a computer program which needs funding.

I've had 20 downloads during the last 6 days (For it's particular purpose that's pretty good) I'm going to action off 100 advertising spaces within the program to fund the developement of this program (I want to convert it from BASIC to Python)

I've written another program, which will allow me to keep up with bids placed on the advertising slots. It generates a text file telling who the top bidders are. This way, if you lose your spot, you will know it. I've placed this file, in my Box.net account and when ever I add or remove things from the program, the file gets updated with who has the current highest bid. The program is free and open sourced, but I'm needing to fund it. Since Box.net is up 24/7. So this text file will be hosted constantly.

---

### Post by deathadder on 2011-04-07
Hmm, I've never used blogspot before so I don't know what options there are for you, short of doing it all manually...

---

