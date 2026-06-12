---
title: "pidgin&gt;yahoo messenger&gt; can't connect"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by gychang on 2008-11-28
can't seem to connect yet the same computer on the XP side connects fine, get an error message "Error resolving scs.msg.yahoo.com"

How do I correct for this?

thanks,

gychang

---

### Post by n1wil on 2008-12-13
I am having the same problem.  Tried changing the server, port etc. but to no avail.  I also tried Kopete and that program failed to connect as well.  

Is it possible that Yahoo has changed something which disallows these 3rd party clients to connect?  To the people using YIM in XP are you using pidgin or the original YIM client from yahoo?

I wonder if yahoo is doing this to force people to see the ads upon connection, in order to secure additional revenues.

Please share your thoughts/suggestions.


Thanks,

John

---

### Post by x58 on 2008-12-13
Write only Yahoo ID like chack32, do not write like [email]chack32@yahoo.com[/email]

---

### Post by Izek on 2008-12-13
> **x58 said:**
> Write only Yahoo ID like chack32, do not write like [email]chack32@yahoo.com[/email]

inverse for MSN though; you MUST specify the domain name for connecting to MSN. I have many people who just give me their username and not the domain, it's awful, since I can't add MSN users without the domain either.

---

### Post by n1wil on 2008-12-13
> **x58 said:**
> Write only Yahoo ID like chack32, do not write like [email]chack32@yahoo.com[/email]

That's exactly what ive been doing all along.  Been working up until recently.

---

### Post by sneeks on 2008-12-13
> **x58 said:**
> Write only Yahoo ID like chack32, do not write like [email]chack32@yahoo.com[/email]

have just checked this myself,and by just putting yr id in seems to still work ok.
this is in gutsy by the way but i dont forsee that it would be any different for any other..

---

### Post by JKBurton on 2008-12-13
If Yahoo's changed it, it wouldn't be the first time. Twice before they've made changes to their protocol to keep 3rd party chat apps from working, the bums.

---

### Post by Izek on 2008-12-13
> **JKBurton said:**
> If Yahoo's changed it, it wouldn't be the first time. Twice before they've made changes to their protocol to keep 3rd party chat apps from working, the bums.

I think it's a certificate issue this time, not sure.

---

### Post by Rolcol on 2008-12-13
> **Izek said:**
> inverse for MSN though; you MUST specify the domain name for connecting to MSN. I have many people who just give me their username and not the domain, it's awful, since I can't add MSN users without the domain either.

There is a reason for that.  You can register any email address for a windows live passport.  I registered my comcast email for msn messenger.

---

### Post by x58 on 2008-12-13
First only yahoo ID not Yahoo E-MAIL. Then change Edit account, Modified account at Advance highlight scs.msg.yahoo.com and change to 66.163.181.173
and be sure to Save.Works after that like firework.

---

### Post by gychang on 2008-12-13
> **x58 said:**
> First only yahoo ID not Yahoo E-MAIL. Then change Edit account, Modified account at Advance highlight scs.msg.yahoo.com and change to 66.163.181.173
and be sure to Save.Works after that like firework.

thanks, this works fine.

gychang

---

### Post by ben2talk on 2009-04-15
> **gychang said:**
> thanks, this works fine.

gychang

Makes no difference to me - also it won't connect in MSN or Google or anything else - but XP
 in virtualbox is connected...

---

### Post by QCompson on 2009-04-18
> **ben2talk said:**
> Makes no difference to me - also it won't connect in MSN or Google or anything else - but XP
 in virtualbox is connected...

Same here.  That trick worked last time some months ago when I had a connection issue with pidgin and yahoo, but doesn't work for me now. :(

EDIT: but changing it back to scs.msg.yahoo.com did work.  Weird.

---

### Post by lsutiger on 2009-04-18
> EDIT: but changing it back to scs.msg.yahoo.com did work. Weird.

ditto here.

---

### Post by perceptus on 2009-06-18
not ment to res an old post, but i had the same issues described and i am using 66.163.181.173 and my id, i also had to restart pidgin. works fine now.

---

### Post by peripatetic on 2009-06-19
Detailed Explanation here:
[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)

---

### Post by leonardo_neo on 2009-06-19
> **peripatetic said:**
> Detailed Explanation here:
[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)


Thanks for the info. :)

---

### Post by Therion on 2009-06-19
Changing the server to read 

```
cn.scs.msg.yahoo.com
```

is also working for many.

---

### Post by phyrewall on 2009-06-20
> **Therion said:**
> Changing the server to read 

```
cn.scs.msg.yahoo.com
```is also working for many.

Thanks! This worked immediately for me.  

You get a gold star, lol. :KS

---

### Post by Yfrwlf on 2009-06-22
Now Pidgin just crashes when trying to connect to Yahoo.  Had to disable networking so I could disable Yahoo before it tried to log in.

C'mon Jabber clients, get Jingle support.

---

### Post by sandalgod on 2009-06-22
> **peripatetic said:**
> Detailed Explanation here:
[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)

thanks!! great info

---

### Post by rybaxs on 2009-06-23
how about aim?

---

### Post by warped6 on 2009-06-23
> **Yfrwlf said:**
> Now Pidgin just crashes when trying to connect to Yahoo.  Had to disable networking so I could disable Yahoo before it tried to log in.

C'mon Jabber clients, get Jingle support.

Yeah that's what it is doing for me too. I'll have to try the disable network and see if I can disable yahoo. Grrrr

---

### Post by warped6 on 2009-06-23
> **warped6 said:**
> Yeah that's what it is doing for me too. I'll have to try the disable network and see if I can disable yahoo. Grrrr

OK... disabled networking and was able to bring Pidgin up. Went into settings and changed the server back to the standard scs.msg.yahoo.com from cn.scs.msg.yahoo.com. Re-enabled networking and now Pidgin seems to be behaving itself. YMMV...

BTW... this is with 8.10.

---

### Post by xeticus on 2009-06-23
> **Therion said:**
> Changing the server to read 

```
cn.scs.msg.yahoo.com
```is also working for many.I tried that and it's working fine for me now.

---

### Post by mihaicj on 2009-06-23
> **xeticus said:**
> I tried that and it's working fine for me now.

This causes pidgin to connect and then crash after a second.

---

### Post by emeraldgirl08 on 2009-06-23
> First only yahoo ID not Yahoo E-MAIL. Then change Edit account, Modified account at Advance highlight scs.msg.yahoo.com and change to 66.163.181.173
and be sure to Save.Works after that like firework.
Thank you. This worked... hopefully it stays this way :)

btw where does the 66.163.181.173 originate?

---

### Post by undoIT on 2009-06-23
66.163.181.173

Not working anymore :(

---

### Post by QCompson on 2009-06-23
This is ridiculous... I have to change settings every few hours now.  :confused:

Now I don't know what works.

---

### Post by H2SO_four on 2009-06-23
Works like a charm!

---

### Post by jrusso2 on 2009-06-23
Why don't you all update to the new pidgin?

---

### Post by occams_beard on 2009-06-23
I am also having trouble.

[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)

This page says that pidgin 2.5.7 fixes this problem. The version included with Jaunty is 2.5.5.  So the question is will Ubuntu upgrade to this version, or will I have to install it directly from pidgin. 

This is a show stopper as many people rely on yahoo messenger. I wonder why they have NOT updated this version in the Ubuntu repo yet?

---

### Post by undoIT on 2009-06-23
> **occams_beard said:**
> I am also having trouble.

[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)

This page says that pidgin 2.5.7 fixes this problem. The version included with Jaunty is 2.5.5.  So the question is will Ubuntu upgrade to this version, or will I have to install it directly from pidgin. 

This is a show stopper as many people rely on yahoo messenger. I wonder why they have NOT updated this version in the Ubuntu repo yet?

Did you try this?

[http://ubuntuforums.org/showpost.php?p=7504859&postcount=10](http://ubuntuforums.org/showpost.php?p=7504859&postcount=10)

---

### Post by nynoah on 2009-06-24
Perm fix here [http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)

---

### Post by misswham on 2009-06-24
I just updated to the new pidgeon and it works fine once i switched everything back to cn.scs.msg.yahoo.com.  

When it updated it looks a little different.  Are there any different functions now with the new pidgin that werent there before like webcam?

---

### Post by mihaicj on 2009-06-24
> **misswham said:**
> I just updated to the new pidgeon and it works fine once i switched everything back to cn.scs.msg.yahoo.com.  

When it updated it looks a little different.  Are there any different functions now with the new pidgin that werent there before like webcam?

Still the same client that can't do anything. Not even delete a contact.
What clients do you guys use?

---

### Post by scrooge_74 on 2009-06-24
The final solution was posted in the other [thread]("http://ubuntuforums.org/showthread.php?t=1191686&page=3"). The pidgin team has already posted a solution.

[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

The admins should merge the threads

---

### Post by misswham on 2009-06-25
ok now, when I log onto pidgin it logs off immediately.  What is going on?  I have downloaded the new version and it worked like a charm all day and this just started happening a few mins ago.

---

### Post by scrooge_74 on 2009-06-25
Being working ok for me on two machines since I made the updates

---

### Post by Georgia boy on 2009-06-25
After trying various things previously I just put in the "
cn.scs.msg.yahoo.com". So far it's working. Guess I'll see how long it works before it gets changed again. I noticed that in the link to Sofpedia it talked about different versions of Ubuntu except for Hardy 8.04. I had also gone to the link that went to the Pidgin site where they gave the directions for terminal. Do you put both of those into the terminal at the same time or are they separate inputs? Never had the need to use terminal except for one time and it was almost a year ago. So please overlook the dumbness of the question.
Thanks
Tom

---

### Post by misswham on 2009-06-25
Can anyone tell me why pidgin wont stay connected.  I have already updated to the new version and it worked perfect but after one day it logs on and completely off.  I went to bed last night and when I woke up it worked fine for about 20 minutes and now it has started again.  Wont stay connected.  

Please can anyone help me.

---

### Post by Yfrwlf on 2009-07-02
I've not had any issues with the new version 2.5.7 as far as connecting and staying connected, except I'll always have Yahoo or some service require me to click reconnect every time I log in, like they are all trying at once so it times out or something.

The problem I am having on the newest version is my contacts aren't showing that they've logged off.  They all stay on-line until I disconnect and reconnect, then I can see who is actually on-line.  Not sure if it is just Y! that is doing this or all of them.

Off-topic I know but this problem of connecting to Yahoo seems to definitely be fixed in the newer versions of Pidgin...

---

### Post by Yfrwlf on 2009-07-02
> **misswham said:**
> Can anyone tell me why pidgin wont stay connected.  I have already updated to the new version and it worked perfect but after one day it logs on and completely off.  I went to bed last night and when I woke up it worked fine for about 20 minutes and now it has started again.  Wont stay connected.  

Please can anyone help me.

Are your Y! settings the same or did you change them to try to fix your connection issue?  If you changed them earlier, you might want to change them back.  I've had no problems connecting.

scs.msg.yahoo.com
cs.yahoo.co.jp
5050
etc

Maybe your Internet connection is to blame.

---

### Post by Georgia boy on 2009-07-02
YFRWLF, I didn't have any problems with contacts in the 2.5.7 but I did have problems receiving files like jpeg or wma from my niece. She was testing her IM out(don't know which one) and when she sent something to me I couldn't receive it. But I could send. They say that 2.5.8 has corrected that problem. Going to test that out with her this weekend. Hopefully the latest version has taken care of everything. You might want to get the 2.5.8 and see if that takes care of the contact problems for you. Like I said though, I don't remember having that kind of a problem.
Tom

---

### Post by Yfrwlf on 2009-07-03
> **Georgia boy said:**
> YFRWLF, I didn't have any problems with contacts in the 2.5.7 but I did have problems receiving files like jpeg or wma from my niece. She was testing her IM out(don't know which one) and when she sent something to me I couldn't receive it. But I could send. They say that 2.5.8 has corrected that problem. Going to test that out with her this weekend. Hopefully the latest version has taken care of everything. You might want to get the 2.5.8 and see if that takes care of the contact problems for you. Like I said though, I don't remember having that kind of a problem.
Tom

Thanks for the info/help, I am on 2.5.8 now and it seems to be working well so far.  Haven't had a problem with file transfers yet, but haven't tried them out much.  Good luck. ^^

---

### Post by brmc on 2009-07-31
yahoo people must have changed their server settings
 
 so just change advance settings
 replace scsa.msg.yahoo.com with  scs.msg.yahoo.com
 then it should be ok
 or u can install pidgin 2.5.8
 if u wana update your exciting pidgin,
 simply run these in terminal
 
 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 
  echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
     sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
    
 then run the update manager 
 
 if u need more assistance 
 go to : [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)
 
 chinthaka bandara

---

### Post by scrooge_74 on 2009-08-01
This thread should have being close like 3 weeks ago...

---

### Post by AlanRick on 2009-08-02
I tried this a few days ago but the pidgin and purple entries in the update manager don't have any effect.
```
The list of changes is not available yet.
Please try again later.
```
Thsi can't be true because some of you have updated already.

Any idea what is causing this?
Alan
[hardy]

---

### Post by jmszr on 2009-08-02
AlanRick,

You can get Pidgin 2.5.8.here: [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin) . You will need to remove your old Pidgin before you install this.

Hope this helps.

---

### Post by AlanRick on 2009-08-02
But why won't the launchpad repo work? I checked the binaries for hardy and it is for 2.5.8 so all's except for my upgrade manager.
The list-of-changes message makes no sense. :confused:
Do I have to de-install pidgin for launchpad too?
alan

---

### Post by scrooge_74 on 2009-08-03
Did you try using the pidgin version directly from the pidgin website? I had no issues after they got the upgrade out for Hardy version

---

### Post by AlanRick on 2009-08-07
Thank you scrooge_74 and jsmzr,

I swallowed my pride, deinstalled, and downloaded and installed the getdeb version. Works fully now.

I also read the documentation for synaptics package installer and found that there is an intelligent mechanism for determining which is the best version to install if several source libraries refer to the same application. This is not necessarily the newest version (makes sense - since I've opted for LTS rather than jaunty). Thanks to the documentation I now know how to select a different version if I disagree - and this is what I should have done to get the most recent version from a different source.

Wiser now,
Alanrick

---

### Post by colau on 2009-08-15
Page Server!
```

cn.scs.msg.yahoo.com

```

---

### Post by and3street on 2009-08-16
I had the same problem the code works super troper:


 				 				**Re: pidgin>yahoo messenger> can't connect** 			
 			 			 		   		 		 		Changing the server to read 

 	Code:
 	cn.scs.msg.yahoo.com 
is also working for many.

---

### Post by Teknyk on 2009-08-17
cn.scs.msg.yahoo.com was not working for me and neither did using IP's

I checked one of my old accounts I had setup and it DID connect just fine but was using this for a server  scsa.msg.yahoo.com

Using that I was able to get all my accounts connected just fine now.

(Excuse any typos. At work and posting in a hurry)

---

### Post by zerhacke on 2009-08-17
I have found that editing /etc/hosts and adding 

66.163.181.184 scs.msg.yahoo.com

to it solved all my problems.  I don't even have to manually determine a server in Pidging with this solution.

---

### Post by colau on 2009-08-17
> **Teknyk said:**
> cn.scs.msg.yahoo.com was not working for me and neither did using IP's

I checked one of my old accounts I had setup and it DID connect just fine but was using this for a server  scsa.msg.yahoo.com

Using that I was able to get all my accounts connected just fine now.

(Excuse any typos. At work and posting in a hurry)
Do you use Pidgin 2.5.8?

---

### Post by Cato2 on 2009-09-19
> **Teknyk said:**
> cn.scs.msg.yahoo.com was not working for me and neither did using IP's

I checked one of my old accounts I had setup and it DID connect just fine but was using this for a server  scsa.msg.yahoo.com

Using that I was able to get all my accounts connected just fine now.

(Excuse any typos. At work and posting in a hurry)

scsa.msg.yahoo.com is a server using Yahoo's new authentication mechanism - the latest version of Pidgin supports this but possibly the version bundled in Ubuntu doesn't, as the change to new authentication happened in about June 2009.  You can only use this server with a newer version of Pidgin, I believe.

cn.scs.msg.yahoo.com is a server that's still running the older authentication mechanism from Yahoo.  While this may work for some people, it's NOT a permanent solution - eventually Yahoo will upgrade all the old-authentication servers to the new version.

See [http://ubuntuforums.org/showthread.php?t=1264572](http://ubuntuforums.org/showthread.php?t=1264572) for a solution using Kopete from KDE 4.3.1 (however, I can't get the Yahoo emoticons working properly.)   The KDE bug report includes a link to a Pidgin bug report, so you should be able to find which Pidgin version fixes this.

---

### Post by misfitpierce on 2009-09-19
I got ver. 2.5.5 which I believe is the default version although I have had a update to it. Mine connects perfectly fine to Yahoo though.

---

### Post by scrooge_74 on 2009-09-19
I switched to Debian Lenny a few weeks ago, and a few days ago yahoo started giving piding problems again. So I went back to the system of changing the ip for the yahoo server, no more problems here, I'm using 202.43.216.6 for logging into yahoo

---

### Post by whoya on 2009-09-21
> **x58 said:**
> Write only Yahoo ID like chack32, do not write like [email]chack32@yahoo.com[/email]
x58 i just started to use pidgin and couldnt log into my yahoo acc, i did what you said and all is good now. 
Thanks x85

---

