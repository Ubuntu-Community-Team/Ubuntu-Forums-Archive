---
title: "best way to develop a news site"
date: 2011-09-01
forum: Programming Talk
---

### Post by RobikShrestha on 2011-09-01
We are building a web app which collects news, does some analysis on the articles, groups them together and displays them in groups.

What would be the best way to build the site (we only know php)?
1. Start from scratch
2. Use CMS like drupal
3. Just use html template and do the php part ourselves
4. Other

?

---

### Post by aura7 on 2011-09-01
Try using more standard plugins from CMS you are using, or if you are a mature php developer you can write them yourself too.

The approach you described is quite right.

---

### Post by karlson on 2011-09-01
> **RobikShrestha said:**
> We are building a web app which collects news, does some analysis on the articles, groups them together and displays them in groups.

What would be the best way to build the site (we only know php)?
1. Start from scratch
2. Use CMS like drupal
3. Just use html template and do the php part ourselves
4. Other

?

I think you are in general asking the wrong question.  You need to start your analysis from the following:

Are there existing products that can do this?
If there are evaluate them first.
If there aren't then you might want you might need to look into writing one yourself.
If there is a product that does 70-80% of what you want to do it might be worthwhile to invest time and effort to build the other 20-30% that would do what you need.

---

### Post by RobikShrestha on 2011-09-01
Thanks for the reply. I am not aware of any open-source products as such. I know php but I do not know how to make the database I designed work with CMS (drupal).

---

### Post by dazman19 on 2011-09-01
you could write your own, I would look at using a framework like yii or zend.

---

### Post by tgalati4 on 2011-09-01
If this database is a no-SQL, hadoop, or key-value-store database, then you are on your own.  I did listen to a podcast that had some insights on database called membase.  

[http://twit.tv/show/floss-weekly/141](http://twit.tv/show/floss-weekly/141)

Getting membase to talk to Drupal would be a challenge.  I see that membase points to couchdb:

[http://www.couchbase.com/](http://www.couchbase.com/)

So now you need a CMS that works with couchdb.  My head hurts thinking about it.

---

### Post by RobikShrestha on 2011-09-01
We are using MySQL. We can code on our own but if there is a better way why not use that. The problem is we do not know how to map our own database with drupal.

---

### Post by karlson on 2011-09-02
> **RobikShrestha said:**
> We are using MySQL. We can code on our own but if there is a better way why not use that. The problem is we do not know how to map our own database with drupal.

Have you read installation documentation if you are going with Drupal?

---

### Post by sanderd17 on 2011-09-02
I believe it is pretty easy: [http://yoodey.com/how-create-and-access-multiple-database-drupal-7](http://yoodey.com/how-create-and-access-multiple-database-drupal-7)

---

### Post by RobikShrestha on 2011-09-02
what do i do after linking to database? how to display the data as drupal would without inserting the data into drupal database?

---

### Post by sanderd17 on 2011-09-02
That would probably require you to write a module.

---

### Post by tgalati4 on 2011-09-02
When you install Drupal with MySQL, you get a standard MySQL database running on your server with all of the specific fields established to support Drupal.  You can add fields and data to mysql either in a new database or an existing database using one of several mysql clients.  You can create new databases, users and privileges.  phpmyadmin is a web-based mysql panel.  

apt-cache search mysql

Personally, I would search the Drupal modules and ask in the Drupal forums for capability more specific to your application.  There may be existing modules that do something similar to what you want to do.

---

### Post by kevinharper on 2011-09-02
Are you trying to do something similar to [http://www.paper.li](http://www.paper.li) ?

Have you tried WordPress? It's very easy to configure and hack. And database interaction is a breeze. MANY plugins. A single search for "wordpress newspaper plugin" returned a few interesting results.

This is one: [http://wordpress.org/extend/plugins/newspaper/](http://wordpress.org/extend/plugins/newspaper/)

---

### Post by RobikShrestha on 2011-09-03
The database is as follows:

articleTable: Has articles

relatedArticlesTable: Tells which articles are related to one another
 
The web page should:

Show few lines of one article per group of related articles and allow users to click on a button to view articles related to that one article (per group).

Our main application is "Finding Relatedness Scores" and not "Displaying them on webpage". But we have to display them somewhere and building web app would be cool. 

I have used Wordpress and I have modified the database manually, it seems plausible. But I want to display the articles in the above mentioned format. i.e. I want custom designed HTML template to go with whatever Wordpress does. I need some examples.

---

### Post by tgalati4 on 2011-09-03
You can customize the Drupal "Views" module to show a webpage and have a side bar that has Related Pages based on keywords/tags and ranked by relevancy. 

This application sounds like a PDF document manager--of which there are several.  

[http://www.makeuseof.com/tag/3-pdf-document-management-tools-organizing-research/](http://www.makeuseof.com/tag/3-pdf-document-management-tools-organizing-research/)

---

### Post by RobikShrestha on 2011-09-04
Thanks.
I had read about views. I find drupal too complex to edit. Can you provide me very simple example of how to access custom DB and display the data using drupal? Which files do I need to edit? There are tons of them.

---

### Post by tgalati4 on 2011-09-05
There is no simple example.   You have to install Drupal and use it for several weeks.  Then you have to look at the PHP files and see how it works.  It's open source and generally well-documented in the PHP code.  Once you are comfortable using Drupal, then start adding some modules and look at the PHP code for those modules.  

It's a steep learning curve because you have several frameworks to cram into your brain:  PHP, MySQL, Drupal and CMS concepts.

So, there is no simple example without spending some time to learn the frameworks.

There are several CMS systems written by people who say "I wrote my own because Drupal was too complex for what I want to do."

That may be the case here, but you have to start somewhere and Drupal has been around long enough and has a proven track record of reliability, scaleability, and relative ease of installation and configuration.

---

### Post by RobikShrestha on 2011-09-07
Thanks... So, I will spend some time learning drupal then, seems like there is no easy way out.

---

### Post by RobikShrestha on 2011-09-09
Can anyone please list all the topics I need to learn to use external database with drupal.
I need to use the data from external database, post it on site (group them together) and allow users to comment on them.

---

### Post by WitchCraft on 2011-09-09
When you ask for the 'best' way to develop a news site, not the 'quickest' way, then the answer is to write the content management yourself. Otherwise, you might also be able to use WordPress for that instead of Drupal, it's less complicated.

---

### Post by RobikShrestha on 2011-09-09
Thanks, how do I map my database to that of wordpress? I just want the same result as I would get by posting articles manually except that now it should be automatically posted from another database.

---

### Post by RobikShrestha on 2011-09-09
I found this helpful: 

[http://wpbits.wordpress.com/2007/08/08/a-look-inside-the-wordpress-database/](http://wpbits.wordpress.com/2007/08/08/a-look-inside-the-wordpress-database/)

I still don't mind getting help from you guys. I don't want to screw this project as I still have 3 weeks to start the real coding. I want to get everything together before I code.

---

### Post by tgalati4 on 2011-09-09
Drupal has commenting built in.  Plus, you can define roles for different types of users (for example, beginners, medium users, advanced users) and give them different levels of access.  To reduce spam, you wouldn't want new people without history to comment on your articles.  Drupal also has built-in comment moderation--so you can review comments before allowing them to be posted.

For accessing the database, look at phpmyadmin--it's a web-based mysql handler and it's quite capable.  You can do a lot of admin tasks and database manipulation through phpmyadmin.  Send a command to rebuild the Drupal tables and your new content should be populated throughout the site.  Of course, you can do most data entry through Drupal itself--that is the purpose of a CMS.  Not sure why you need to modify the database outside of Drupal.  I'm not familiar with the Use Cases for your application.

---

### Post by RobikShrestha on 2011-09-10
@[tgalati4]("http://ubuntuforums.org/member.php?u=241895"): I need to post manually on drupal. I do not want that. My java program does text analysis and generates hundreds of news articles grouped together in mysql database. I just want to display them in a drupal site or wordpress site without posting those articles manually.

Wordpress database seems to be lot more simpler than that of drupal. But I still don't know how to hack it without causing errors. So I am asking for help. I would love a really good tutorial. I am willing to learn but have been unable to find a really good example in google.

---

### Post by WitchCraft on 2011-09-10
Just another thought:

When you're not a PHP person, you could check out the Orchard CMS.
The mono team boasted about half a year ago that it now works on mono/Linux. That would certainly be much nicer to tackle coming from a Java background than PHP.

Though I don't know how good it is, I haven't found an online demo, which is kind of telling.

---

### Post by RobikShrestha on 2011-09-10
I know PHP but just don't know how to modify a wordpress site for my purpose i.e. generate automatic contents from my db.

---

### Post by WitchCraft on 2011-09-11
> **RobikShrestha said:**
> I know PHP but just don't know how to modify a wordpress site for my purpose i.e. generate automatic contents from my db.

Well, whether you use Drupal or WordPress, you can switch a profiler into the database used, then add an article using the Drupal/WordPress interface. 
Then you switch to the profiler and see all the SQL insert/update statements that were executed to add that article/menu/whatever.

See here:
[http://stackoverflow.com/questions/365103/how-to-profile-postgresql-database](http://stackoverflow.com/questions/365103/how-to-profile-postgresql-database)
[http://stackoverflow.com/questions/430123/how-do-i-enable-the-postgresql-function-profiler](http://stackoverflow.com/questions/430123/how-do-i-enable-the-postgresql-function-profiler)
[http://pqa.projects.postgresql.org/](http://pqa.projects.postgresql.org/)

For MySQL:
[http://serverfault.com/questions/3120/how-do-i-profile-mysql](http://serverfault.com/questions/3120/how-do-i-profile-mysql)
[http://stackoverflow.com/questions/20263/is-there-a-profiler-equivalent-for-mysql](http://stackoverflow.com/questions/20263/is-there-a-profiler-equivalent-for-mysql)
[http://www.jetprofiler.com/](http://www.jetprofiler.com/)

---

### Post by RobikShrestha on 2011-09-11
Thanks but I have more features to add like: I want to display a group of posts together then I want to display another group then another and so on. I also need to use google map. 
I think using CMS is not such a good idea for me. May be I will hard code in php. 
If anyone has got really good examples please post them, but for now I think I won't choose CMS.

---

### Post by WitchCraft on 2011-09-11
> **RobikShrestha said:**
> Thanks but I have more features to add like: I want to display a group of posts together then I want to display another group then another and so on. I also need to use google map. 
I think using CMS is not such a good idea for me. May be I will hard code in php. 
If anyone has got really good examples please post them, but for now I think I won't choose CMS.

Well, as I said, the best (but not the quickest) way is to write one yourselfs.

A real function and feature richt CMS like Drupal or Joomla is quite a bit complex, so there is time required to master the learning curve ;-)

Maybe if you have specific requirements, you could choose rentacoder.com, to find someone who does the Drupal/Joomla work for you.
I'd guess there you find plenty of people with experience in Drupal or Joomla, which could do it for you, including explanation. 

Due to immense price pressure from people from India/Russia/Egypt, the prices there are usually as dumping cheap as it can get.

---

### Post by RobikShrestha on 2011-09-11
I am actually just a student trying to learn things. I am not looking to hire people because it's a college project work. So, my plan is to slowly learn the internal workings of CMS. But for now just going with hard coding.

---

### Post by WitchCraft on 2011-09-11
> **RobikShrestha said:**
> I am actually just a student trying to learn things. I am not looking to hire people because it's a college project work. So, my plan is to slowly learn the internal workings of CMS. But for now just going with hard coding.

Rentacoder is also a great place to get your homework done for a penny on the dollar.
No questions asked xD

---

### Post by RobikShrestha on 2011-09-12
I don't want my code done by someone else. I want to learn how to do it myself. I just wanted to know what was the best way to do it and I guess hard coding is the one for me.

---

### Post by medic2000 on 2011-09-12
> **RobikShrestha said:**
> I don't want my code done by someone else. I want to learn how to do it myself. I just wanted to know what was the best way to do it and I guess hard coding is the one for me.

+1 for hard coding.:KS Not every time best thing but for learning there is not a greater teacher than that.

---

### Post by RobikShrestha on 2011-09-12
Guess we need to get the basics into our minds and only then we can develop good applications.

---

### Post by RobikShrestha on 2011-09-12
Ohh hard coding means:

**Hard coding** (also, **hard-coding** or **hardcoding**)  refers to the software development practice of embedding what may,  perhaps only in retrospect, be regarded as input or configuration data  directly into the [source code]("http://en.wikipedia.org/wiki/Source_code") of a [program]("http://en.wikipedia.org/wiki/Computer_program")  or other executable object, or fixed formatting of the data, instead of  obtaining that data from external sources or generating data or  formatting in the program itself with the given input. (Wikipedia)

I thought hard coding was doing all the code ourselves. I was wrong.

---

### Post by lisati on 2011-09-12
> **RobikShrestha said:**
> Ohh hard coding means:

**Hard coding** (also, **hard-coding** or **hardcoding**)  refers to the software development practice of embedding what may,  perhaps only in retrospect, be regarded as input or configuration data  directly into the [source code]("http://en.wikipedia.org/wiki/Source_code") of a [program]("http://en.wikipedia.org/wiki/Computer_program")  or other executable object, or fixed formatting of the data, instead of  obtaining that data from external sources or generating data or  formatting in the program itself with the given input. (Wikipedia)

I thought hard coding was doing all the code ourselves. I was wrong.

Ah yes, that definition takes me back! I kinda figured *another* meaning was intended.

---

### Post by RobikShrestha on 2011-10-06
Well, if anyone is interested, this is how I built the site:
I used wordpress. I wrote a plugin to import news articles and insert them as posts into wordpress database. While inserting, category of news etc was also stored. So my solution was to develop a simple plugin in wordpress. I must say that wordpress is very powerful and very very easy to extend to do your specific work. Plus, templates are great and flexible. Finally on top of that, free plugins are really good and very useful.

Edit: I also used hooks : the_content and the_excerpt to display the "Related Articles" list.

---

