---
title: "Howto spam filtering in Evolution with bogofilter and spamassassin"
date: 2005-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by samiaji on 2005-12-05
After some research and adaptation I came up with personal spam filter using bogofilter and spamassassin with Evolution.

Disclaimer:
I just compiled and adapted what others have written about filtering spam, I included the reference web site at the endo of this post.
I assumed you use standard installation so every directory will be as standard. Customise to your own situation
Make backup -- I can't strees this enough, proper backup have saved me many times.

Background:
I used Faculty of IT at UTS procmail spam filtering at server side. However since I will leaving soon I better "train" my laptop some spam filtering

Ok here is my spec
Dell Inspiron 5100 laptop wiht P4 2.8 GHz, 512 Mb RAM, 32 MB ATI 7500, 30 GB HDD
Ubuntu Breezy 5.10, Evolution 2.4.1, Spamassassin 3.0.4-2, Bogofilter 0.95-2
I used everything standard in Breezy (either cd or repo)

First install spamassassin and bogofilter if you have not done so with whatever methods you like. This is what I did

sudo apt-get install spamassassin bogofilter

After installation
First step enable Junk mail filter in Evolution
Edit->Preferences->Mail Preferences->Junk->Check incoming mail for junk and remote test

Second create two message filters in Evolution to utilise bogofilter
The first filter is to teach bogofilter to recognise spam email (either from marked automatically or manually by user).

Give the rule any name mine is **Bogofilter teach spam**
Set Status is Junk ThenPipe to program /usr/bin/bogofilter -s + Stop Processing
It looks like this

[IMG]http://www.fe.uajy.ac.id/~ss/bogoteach.png[/IMG]


The second filter is the actual bogofilter action which (hopefully) remove spam

Give the rule any name mine is **Bogofilter check spam**
Set Pipe to program /usr/bin/bogofilter -u Then Set Status Junk + Stop Processing
It looks like this

[IMG]http://www.fe.uajy.ac.id/~ss/bogospam.png[/IMG]

You can stop here if you satisfied with bogofilter alone.

Then you have to train bogofilter using the first message filter (that is why the bogofilter teach is in the first position).

I have a collection of spam (700+) in spam folder (under evolution) and I used this for training both spamassassin and bogofilter.

Every spam email will be marked Junk and moved to Evolution Junk folder. You can marked every spam email you received and then it will be moved to Junk folder. I marked all the email in my Spam folder as junk.
Then I moved to Junk folder and select all message. To train bogofilter you just need to apply filter

Message -> Apply Filters or Ctrl+Y

It took about 5 minutes for bogofilter to learn 700+ spam email

You also can train bogofilter to identify spam and non spam (ham) using this command in CLI

bogofilter -s < /home/user/.evolution/mail/local/spam for spam message

bogofilter -n </home/user/.evolution/mail/local/Inbox for nonspam message and replace Inbox with whatever non spam folder you have in evolution

REMEMBER your non spam folder have to be free from spam. (thx dcstar for your comment).

If you want to add another layer to that (using spamassassin) then here it is

First generate the spamassassin configuration using this website if you like me (a.k.a.lazy)

[http://www.yrex.com/spam/spamconfig.php](http://www.yrex.com/spam/spamconfig.php)

Then create a third message filter (after the first two for bogofilter above)

Give the rule any name mine is Spamassassin 1
Set Pipe to program spamassassin -e Does not return 0 Then Move to Folder Junk/Spam + Set Status Read + Stop Processing
It looks like this

[IMG]http://www.fe.uajy.ac.id/~ss/sa.png[/IMG]

Again you have to train your spamassassin. I used (again) the spam folder I collected.

To train spamassassin use this command in CLI

sa-learn --spam --mbox /home/user/.evolution/mail/local/spam


The other feature of spamassassin is you could also teach them to recognise non spam (ham) as in bogofilter. I use this command in CLI

sa-learn --ham --mbox /home/user/.evolution/mail/local/Inbox

Replace Inbox with whatever non spam mail folder in Evolution.

After the three filters then you can create any filter to sort your email to any folder you like.
All incoming mail will be filtered by those 3 filters before any other filters.

I still train both my bogofilter and spamassassin, but the number of spam I received and appeared in Inbox have been reduced considerably. For illustration I received about 500-750 emails per day.

Regards
Samiaji
Reference
Bogofilter
[http://bogofilter.sourceforge.net/](http://bogofilter.sourceforge.net/)
SpamAssassin
[http://spamassassin.apache.org/](http://spamassassin.apache.org/)
Using bogofilter in evolution
[http://johnleach.co.uk/words/archives/2005/09/15/180/](http://johnleach.co.uk/words/archives/2005/09/15/180/)
Spamassassin in evolution
[http://software.newsforge.com/softwa....shtml?tid=130](http://software.newsforge.com/softwa....shtml?tid=130)
Spamassassin configuration generator
[http://www.yrex.com/spam/spamconfig.php](http://www.yrex.com/spam/spamconfig.php)

---

### Post by dcstar on 2006-02-17
And to add in a few more handy hints from the other thread on this useful HOWTO:

[I](More useful stuff from samiaji):
If you use spamassassin as your second layer spam filter (after the bogofilter) you can utilise dcc and razor network. follow the instruction on this URL 
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_p4](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_p4)[/I]

One thing to add to it for all of us not using IPv6 is:

sudo cdcc 'ipv6 off'

To prevent it from trying to use the stuff........

Another hint for all the Evolution users using this solution is to regularly "clean out" your Junk folder.

I am in the habit now of checking it every couple of days to ensure that there aren't any messages that have been mistakenly identified as Spam (and I did find some bulk e-mails from an airline that I actually wanted - so I them marked those as "Not Junk").

Once you are sure that the contents of the Junk folder are junk, delete them and do a "Empty Trash" to purge them from your files.

Setting up my Evolution with Spamassassin (with the extra dcc and Razor rules) has cut ~99% of my spam out with only a few "false positives" (from one airline site only).

Once you have your Evolution set up and working with spam filtering, you may then want to try incoming mail virus scanning with something like ClamAV:

[http://ubuntuforums.org/showthread.php?t=84423](http://ubuntuforums.org/showthread.php?t=84423)

---

### Post by pinguinus on 2006-04-05
>  Set Pipe to program spamassassin -e Does not return 0 Then Move to Folder Junk/Spam + Set Status Read + Stop Processing

It is not necessary to choose a folder where SpamAssassin filters spam in Evolution. Actually just using: 
*  Set Pipe to program spamassassin -e Does not return 0*
and:
*  Stop Processing *
(maybe with: 
*  Set status: Junk *
before the last Stop processing rule if you want but even that is not necessary)
is enough because SpamAssassin then knows automatically to move spam to Evolution's default Junk folder. 

More information about this and other Evolution spam filtering techniques (like finetuning spamfilters) in this Newsforge article: [http://software.newsforge.com/software/05/07/01/1521254.shtml?tid=130](http://software.newsforge.com/software/05/07/01/1521254.shtml?tid=130)

---

### Post by dcstar on 2006-04-06
[QUOTE=pinguinus]It is not necessary to choose a folder where SpamAssassin filters spam in Evolution. Actually just using: 
.......[/QUOTE]
Just ticking the "Check incoming mail for junk" option in the Breezy version of Evolution will automatically use Spamassassin, so no rule is needed at all!

---

### Post by btdown on 2006-04-06
> Just ticking the "Check incoming mail for junk" option in the Breezy version of Evolution will automatically use Spamassassin, so no rule is needed at all!
 
I dont think that is correct. Ticking the "Check incoming mail for junk" does absolutely nothing without the rules piping it to spamassassin or bogofilter. I trained/deleted for 2 weeks and Evolution never filtered a single spam.

---

### Post by kaplanmyrth on 2006-05-25
[QUOTE=btdown]I dont think that is correct. Ticking the "Check incoming mail for junk" does absolutely nothing without the rules piping it to spamassassin or bogofilter. I trained/deleted for 2 weeks and Evolution never filtered a single spam.[/QUOTE]

I can only say what my own experience has been with respect to this, and a filter is definitely not required in order to get Evolution to learn and filter junk mail.

I have had Evolution installed for months and wondered why the junk mail filtering didn't catch anything. Finally read these forums and installed Spamassassin (and not bogofilter). I also installed razor, dcc and pyzor, and customised the /etc/default/spamassassin file to turn on spamd and use razor, dcc and pyzor. Made sure Evolution had the junk mail filtering check boxes checked, and restarted it.

Training was easy -- since I've been marking mail as Junk all along, I had a Junk folder full of mail. I just moved it all to my Inbox, selected it, and marked it as junk. Now, for the first time, the status bar indicated it was "Learning junk".

And finally, without adding any filters, it is checking incoming mail for junk.

---

### Post by ubuntubrian on 2006-05-27
This is great but to me is useless. A "How To" that actually includes the steps and commands to get filtering to work would be very helpful. I can check filtering in Evolution but getting it to work means I need toknow how to pipe, etc. Can anyone make this sensible to a newbie?
Thanks

---

### Post by magnetism on 2006-05-30
> Give the rule any name mine is Bogofilter check spam
Set Pipe to program /usr/bin/bogofilter -u Then Set Status Junk + Stop Processing
It looks like this

The pictures are missing :(
What should the return value be?

---

### Post by ubuntubrian on 2006-05-31
I went to a couple of the links supplied in this thread and got the filters installed. I don't get that much spam, 10-20 a day, but am using the training method and anxiously waiting for bogofilter to take over.
Interestingly, before I upgraded to Dapper Evolution had a small icon below the mail list that had SpamAssassin's perception of the likelyhood that a particular message was spam. As I marked spam as junk, spamassassin seemed to be getting the messages more and more correct. Then I upgraded and spamassassin disappeared. I had never done anything other than check the boxes in mail preferences-as it should be.

---

### Post by ubuntubrian on 2006-06-21
I don't know if this thread died yet but.. I have tried Samiaji's method to no avail at all. I checked out a couple of sites re: this issue and one of them uses the same method but says to NOT check the "check incoming mail for junk" boxes in preferences. Could this be the reason my filter set up doesn't filter? I've stored up to 500 junk messages in junk and then applied the filters and deleted, as in the how to.
Any help before I switch to Thunderbird?

Thanks

---

### Post by Dubbayoo on 2006-06-21
i'm not sure this worked for me at all. I just followed the instructions and connected to my isp account. It has about 1,000 msgs in it, at least 995 of which are spam. About half of them made it to the Inbox.

What is the criteria for the second rule? Same as the first or should it be blank?
> 

The second filter is the actual bogofilter action which (hopefully) remove spam

Give the rule any name mine is Bogofilter check spam
Set Pipe to program /usr/bin/bogofilter -u Then Set Status Junk + Stop Processing
It looks like this


---

### Post by NZ-Wanderer on 2006-07-26
Veyr interesting read this guys, thanks :)

Only problem is, I got bogged down real quick... (especially when stuff about "pipe" etc was mentioned...)](*,) 

Can anyone very quickly type out step by step instructions on how to get a spam filter working in Evolution please??

---

### Post by sjv on 2006-07-29
I have had evolution running since breezy(on dapper now), and always had the junk filtering options checked. Never had spam assassin though. Just installed SA, and had it learn my spam(2500), and ham(1000). When I mark new mail as junk I get an indicator for the first time ever that it is "Learning junk". No extra configuration, just the config checkboxes set. Nothing ever seems to be filtered though. I also have razor, dcc, and pyzor installed. It comes in, and just sits in my inbox until I specify that it's junk. I would think with all of that, that at least some of this spam should be getting filtered properly. Am I missing some other setting?

Thanks,
Steve

---

### Post by Avian00 on 2006-08-07
Actually, Evolution works fine with Bogofilter installed.  It is not necessary to create any special Filters.  Just make sure the following packages are installed:

1) Evolution
2) Evolution-Plugins
3) Bogofilter

After that, uncheck Spamassassin in Edit -> Plugins in Evolution.

From there, it just takes a LOT of mail for Bogofilter to start working.  I supplied it with nearly 2000 HAM messages and almost 200 SPAM messages.  It works pretty well now.

---

### Post by NZ-Wanderer on 2006-08-07
Hokay, I did as you said, now tell me, how exactly do I know it is working??
You also mention about supplying Ham and Spam messages, did you just go through msgs on Evolution and mark them as Spam or Not Spam???

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

> **Avian00 said:**
> Actually, Evolution works fine with Bogofilter installed.  It is not necessary to create any special Filters.  Just make sure the following packages are installed:
1) Evolution
2) Evolution-Plugins
3) Bogofilter
After that, uncheck Spamassassin in Edit -> Plugins in Evolution.
From there, it just takes a LOT of mail for Bogofilter to start working.  I supplied it with nearly 2000 HAM messages and almost 200 SPAM messages.  It works pretty well now.

---

### Post by kevinbsmith on 2006-08-31
I have had evolution installed for a while, with the spamassassin and bogofilter plugins enabled. I have very diligently marked all spam (and no ham) as "junk" before deleting it.

It has deteriorated to where no spam at all is detected.

I just tried disabling the spamassassin plugin, but nothing changed.

Maybe there needs to be a HOWTO tell evolution/spamassassin/bogofilter to forget everything it knows so you can start from scratch. At least at the beginning it caught SOME of the spam, even though it never did as well as Thunderbird.

---

### Post by gmc on 2006-09-07
Hi Folks,

Is there anyone trying to implement this howto using version 2.8.0 of Evolution (aka Edgy) and noticed that creating the filters is impossible (without manually editing the filters.xml file). If so, I've filled a bug report [here]("http://bugzilla.gnome.org/show_bug.cgi?id=354797"). Confirmation or additional reports would help solving this problem.

G.

---

### Post by bhowell on 2006-09-19
Can somebody post a filters.xml file that works with bogofilter on 2.8.x?  My filters are not working since upgrading to Edgy.  The odd thing is, my .bogofilter/wordlist.db file gets updated every time I mark a spam but enabling, disabling or even reinstalling bogofilter doesn't make evolution detect spam.  I'm really drowning in amazing morgage offers here.

---

### Post by Phlosten on 2006-11-10
OK, it seems that the Evolution version that comes with Edgy does not allow you to define what extra options to pass to a program when calling it with 'Pipe To Program'. There is a work around which seems to be working for me and that is to create a shell script to do it for you.

create bogonospam.sh and call it from your filter setup. I have three scripts setup. One to tell bogofilter a message is spam when marked as junk, one to tell bogofilter a message is NOT spam when marked as NOT junk and one to check all incoming messages for spam and mark as junk if bogofilter thinks they are indeed junk. Once the filter marks them as Junk evolution automatically moves them to the junk directory.

---

### Post by Spin Doctor on 2006-11-14
> create bogonospam.sh and call it from your filter setup. I have three scripts setup. One to tell bogofilter a message is spam when marked as junk, one to tell bogofilter a message is NOT spam when marked as NOT junk and one to check all incoming messages for spam and mark as junk if bogofilter thinks they are indeed junk. Once the filter marks them as Junk evolution automatically moves them to the junk directory.Does anyone have the time to explain how to do what is said in the quote mentioned above?

I have found an alternative solution myself. It is posted on the following forum:
[http://www.ubuntuforums.org/showthread.php?t=293693](http://www.ubuntuforums.org/showthread.php?t=293693)

---

### Post by moeFinley on 2006-12-04
I'm trying to switch from Opera to Evolution.  Opera had brilliant spam detection and Evolution's is just confussing :confused: 

I've been told bogofilter is better than spamassassin so it seems I just disable one and enable the other in the plugins options?  

Why is everyone talking about shell scripts, isn't that just trying to force it to work in an outdated fashion?  Doesn't the checkbox do it all?

:???:

---

### Post by Spin Doctor on 2006-12-05
> Doesn't the checkbox do it all?I wish this was the case. Did you get it to work? Well, the key is to mark some non-spam emails as spam, and then from the junkmail folder, mark them as non-spam. This for me made the spamfilters start working. The concept is that u need to tell the filters what is not spam. This is a simple fix for a complicated problem...

I am running both SpamAssissin and Bobofilter. Why take one when u can have them all =)

---

### Post by eudemus on 2007-04-11
> **magnetism said:**
> Pipe to program /usr/bin/bogofilter -u
What should the return value be?

Does not return 0 (zero).

Now what's foxing me is how, using this method, the filter can ever learn.
The way you want it to learn continuously (once it's had its initial learning batch of emails put through it manually from the command line) is from manual corrections - marking an email as junk that the filter had missed, and marking an email as not-junk that had been tagged junk by the filter.

The answer at the beginning of this thread makes no sense to me.
A filter on incoming mail surely only filters mail as it arrives.
Once it's there, it won't be filtered. So, even if I mark emails manually as junk or not-junk, they will never pass through the "Bogofilter teach" filter to help fine-tune bogofilter's junk detection.

can anyone shed any light?

I'm suspecting that the best and smoothest way of having a filter that learns in the right kind of way is to get the bogofilter plugin working. But I just can't get it working on my system. I don't know if there is a file of settings somewhere that I need to look at, or something else I need to do. But although I have the bogofilter plugin installed and the relevant boxes checked, it simply doesn't work!

---

### Post by Spin Doctor on 2007-04-13
Actually I read on my above post that I recommend using both filters...That is incorrect. I now only use Bogofilter.

In Edgy and Fiesty the setup for great spamdetection differs somewhat. In Fiesty it is much easier.

But what really is important is the following:
[LIST]
[*]Mark a few of your "good" emails as junk. Lets say 10 of them
[*]Then go to your spamfolder and mark them as "non-junk" emails.[/LIST][LIST]
[*]This will start the filter to start learning. As you go on, you might have to continue mark some emails spam to be able to teach the filter. But as you go on, the filter will be better and better.
[*]Dont delete your junkmail. Keep em in the folder junk.[/LIST]Also make sure you have all settings activated for spammail. In edgy I include an incomming "junk mail test", and forwards them to my junkmail folder. In fiesty, you dont have to do that either. In dapper, I am not sure how the setting look like.

Hope this help!

---

### Post by westdaleworks on 2007-04-21
I've had good luck with [SpamBully]("http://www.spambully.com") and spambayes. I've been using both a few years at home and work. SpamBully also lets you report spammers to their providers which can be fun. Both are pretty easy to use.

---

