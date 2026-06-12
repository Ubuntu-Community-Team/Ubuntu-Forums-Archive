---
title: "HOW TO: Install FireFox 1.0 from the Backports Project"
date: 2005-01-16
forum: Outdated Tutorials &amp; Tips
---

### Post by clparker on 2005-01-16
After spending a good long week struggling on how to upgrade my Firefox browser to the new 1.0 in Warty Warthog, I finally found a solution that was both easy and did not crash my precious Ubuntu install. Using the Hoary Hedgehog repositories I ended up breaking my X-server setup. It was a mess. I hosed my install about three times in a row using Hoary repositories, and doing a manual install was confusing. So now, I offer my first how to here on the forums to anybody who wants a simple walk through on how to install Firefox 1.0 from the backports project.
 

[list=1]
[*]* > sudo gedit /etc/apt/sources.list *
[*]add at the bottom:  > *deb     [http://ubuntu-bp.sourceforge.net/ubuntu]("http://ubuntu-bp.sourceforge.net/ubuntu") warty-backports main     universe*
[*]save the file and get back to the     terminal and tell it to update by typing:  > *sudo apt-get update*
[*]* > sudo apt-get install     mozilla-firefox *
[/list] To the best of my knowledge, this is the simplest and easiest way to run Firefox 1.0 on Warty and not break anything. The backports project is run by some amazing people, and they also do a GAIM update as well.

---

### Post by cabu on 2005-01-16
And for those of us who don't like evolution...they have Thunderbird 1.0.

---

### Post by jdong on 2005-01-17
[QUOTE=clparker]The backports project is run by some amazing people, and they also do a GAIM update as well.[/QUOTE]


Thanks :). There are over 250 updated packages in the Backports repository. If you ever feel like just looking around: [http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/)

---

### Post by clparker on 2005-01-18
any word on posibly a nicotine backport?

---

### Post by clparker on 2005-01-19
And if ya want: Thunderbird too: > sudo apt-get install mozilla-thunderbird
 

---

### Post by Brikkah on 2005-01-19
Are there any other packages barkported? like xnews of gaim??

---

### Post by cabu on 2005-01-19
Take a look at this [thread](http://ubuntuforums.org/showthread.php?t=8486) . The links listed will take you to see what has been backported.

---

### Post by angrylittleman on 2005-01-19
Great Thread, thanks for the help  :)

---

### Post by Wubanga on 2005-01-20
[QUOTE=clparker]After spending a good long week struggling on how to upgrade my Firefox browser to the new 1.0 in Warty Warthog, I finally found a solution that was both easy and did not crash my precious Ubuntu install. Using the Hoary Hedgehog repositories I ended up breaking my X-server setup. It was a mess. I hosed my install about three times in a row using Hoary repositories, and doing a manual install was confusing. So now, I offer my first how to here on the forums to anybody who wants a simple walk through on how to install Firefox 1.0 from the backports project.
 

[list=1]
[*]*  *
[*]add at the bottom:  
[*]save the file and get back to the     terminal and tell it to update by typing:  
[*]*  *
[/list] To the best of my knowledge, this is the simplest and easiest way to run Firefox 1.0 on Warty and not break anything. The backports project is run by some amazing people, and they also do a GAIM update as well.[/QUOTE]
 Hi there, a newbie here

I observed that all the updates through this method ar for i386 kernel. I updated my ubuntu to i686 kernel,  can I do the update anyways?

Thxs

---

### Post by steffen on 2005-01-20
Yep - you can! You can use i386, i586 and i686 packages ;)

Usually, I go for the highest one - I have an i686 processor type

---

### Post by Eklöf on 2005-01-23
How do I get FF and TB 1.0 when using the AMD64 version of Ubuntu. I get errors when using this backport.

---

### Post by pseudonym on 2005-01-23
Thanks for the tip. Once you've added the backports repository and done an apt-get update, shouldn't it be sudo apt-get *upgrade* rather than *install*? (assuming you have both Firefox and Thunderbird already installed, of course) I did apt-get upgrade and found that 2 packages had holds on them - hotplug and mozilla-thunderbird. I have no idea why (I did apt-get check and they are both OK). Can you have problems if you override a hold?

---

### Post by clparker on 2005-01-23
In this walkthrough should I recomend to people they remove the line from the sources file once the update has been made?

---

### Post by pseudonym on 2005-01-23
Just found a German version of this howto that users in various non-English locales will find extra helpful. If you read German go to [http://www.ubuntuusers.de/wiki/internet:firefox_installieren](http://www.ubuntuusers.de/wiki/internet:firefox_installieren) . For those who don't, it's basically the same as this one only you add a different repository to /etc/apt/sources.list . You can obtain Firefox 1.0 and (at time of writing) 1.0-compatible localisation packs for German, French, Japanese, Catalan, Ukrainian,  Norwegian, Turkish, and Polish, plus some package which is supposed to integrate FF 1.0 better into Gnome (which I haven't tried yet).

Follow clparker's steps, but INSTEAD OF the backports repository, use this one -

deb [http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu/](http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu/) warty-updates main universe

Once you've installed FF I guess you could add the backports one, but I would say it's  definitely safer to not have them both in your sources.list at once when you do apt-get update (though this is not based on any technical know-how, just what seems like commonsense).

I installed FF 1.0 plus German localisation from here, and everything is running sweetly. I had problems upgrading FF 0.93 to 1.0 via backports repository-the German pack plus the language switcher for 1.0 which I got separately from Mozilla failed to work properly. So I uninstalled 0.93 and started over. However, had I known about the German repository I probably would not have had to do anything this drastic, instead just grab the German localisation from it. 

But it's all over now. I'm a happy camper again. :)

PS. clparker, maybe edit your original howto post with relevant details from my one here?

---

### Post by jdong on 2005-01-24
I'm sorry... I'll get locales in soon for Thunderbird and Firefox.

---

### Post by Eejay on 2005-02-15
Subcribes 2 thread

---

### Post by rufius on 2005-02-15
I'll look into a backport of nicotine for you. :-)

---

### Post by jdong on 2005-02-15
[QUOTE=jdong]I'm sorry... I'll get locales in soon for Thunderbird and Firefox.[/QUOTE]

All Firefox locales are compiled & marked STABLE...

Thunderbird locales are coming along.

---

