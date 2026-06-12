---
title: "unblocking internet"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by joewas1 on 2008-07-17
Well I have a ubuntu laptop version 7.04. Lol my dad doenst like me thinks I am wasting my time playing this online game and using this IRC so he blocked in terminal anyone have any idea how he did it and how I can unblock it?

---

### Post by iaculallad on 2008-07-17
> **joewas1 said:**
> Well I have a ubuntu laptop version 7.04. Lol my dad doenst like me thinks I am wasting my time playing this online game and using this IRC so he blocked in terminal anyone have any idea how he did it and how I can unblock it?

On IPTables? Blocked a certain website/domain? We could help you with that but it seems you're father had a good purpose on doing that. You might as well stick on using you're laptop w/o net connection.

---

### Post by joewas1 on 2008-07-17
Naw he just is mad I wont mow the lawn (lawn mower broken claims it isnt) plus if I can get help on it there is other ways I can get info on how to do this. Also its blocking a domain I believe.

---

### Post by lisati on 2008-07-17
Go easy on your Dad, he means well.....and try to humour him with the lawns (be nice when asking for help getting the lawn mower fixed: you don't want to end up with a fireworks display that would see Dr Phil or Jerry Springer proud)

---

### Post by jamesrfla on 2008-07-17
My advice is to earn the internet back. I know it seems like a bad idea but if he finds out that you unblocked the internet he'll be more mad and you probably won't see that computer for a long time. About the lawn mower I am not sure what to do about that.

---

### Post by joewas1 on 2008-07-17
He probably does but I think I will only convinse him to get a new one by making a fireworks display out of our current one but anyways how can I unblock this domain I dont have super user access though only regular user other wise I would just check into terminal history of su using this code 
(history|awk '{a[$2]++ } END{for(i in a){print a[i] " " i}}'|sort -rn|head).

---

### Post by anewguy on 2008-07-17
You say you have other means of getting the information?  You might as well use them.  Nobody here SHOULD provide you with the answers as it would be going against your father's wishes, and obviously you are still under age.  Perhaps you should do what ever you can to satisfy your father in this matter and maybe he'll give you access back.  Trying to do whatever you want no matter what is not a good way to grow up.

---

### Post by zipperback on 2008-07-17
You mentioned that he blocked it because you didn't mow the lawn, so perhaps you should go get the lawn mowed, do a good job, and then ask him to please unblock your Internet access.

Since it's probably your dads internet connection you are using, it's probably a good idea to simply keep him happy and do as he asks about the lawn and such. It's really not that big of a deal to do it, is it?

Just my humble thoughts on the subject.

- zipperback
:popcorn:

---

### Post by joewas1 on 2008-07-17
No I do have internet access just 2 pages that he wont let me use my IRC chat and another page but can some one give me a hint so I can start looking plus I will mow the lawn just not now seeing as everybody is a asleep.

---

### Post by iaculallad on 2008-07-17
And, listing the commands used by using the command you posted will do you no good either. You still need the "privileged" user's password to re-run it. (since the password previously inputted had already expired by now)

---

### Post by joewas1 on 2008-07-17
What do you mean how can a password expire I dont think I would need super user to do what he did or because he did it as su I cant reverse with out having su access?

---

### Post by Zack McCool on 2008-07-17
Modifying the iptables firewall rules requires superuser access.  If you do not have sudo access, you do not have iptables access.

Now deal with your punishment, and tomorrow get the lawn cut, and perhaps dad will give you back the access you want.

---

### Post by joewas1 on 2008-07-17
what if I do it in a root shell? Apperantly I still have root privelages but not super user access is that possible?

---

### Post by Zack McCool on 2008-07-17
root shell and su are the same shell.  Just accessed from a different place.

Dad needs to secure the PC better.  I still won't be a party to you breaking the rules.  I have my own kids and would be furious if they did the same.

---

### Post by easybake on 2008-07-18
Maybe you should be asking for tips on how to fix a lawnmower instead.

---

### Post by joewas1 on 2008-07-18
Well so from a root shell you could access su or you wouldnt need to seeing as everything you can do in root you can do with a sudo command? By the way he should secured it better seeing I figured out the password to get in pathetic for a computer program that knows linux inside and out though I think he made it simple so doesnt forget it.

---

### Post by pi.boy.travis on 2008-07-18
Sorry bud, no password, no cigar.  ;)

That is what makes Linux so secure!


BTW I am the administrator on my parents machine! :lolflag:

It's because they are new to Linux and I don't want them to mess anything up and get discouraged.  Anything to keep them off Windows. . .

---

### Post by joewas1 on 2008-07-18
lol windows is bad but I have it figured in a root shell you can run sudo commands and I am trying to get rid of my IPTable using this page but I dont know how to get rid of them?
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by joewas1 on 2008-07-18
Thanks all for all the little tips I figured it out :lolflag:

---

### Post by thedevnull on 2008-07-18
> **joewas1 said:**
> Naw he just is mad I wont mow the lawn (lawn mower broken claims it isnt) plus if I can get help on it there is other ways I can get info on how to do this. Also its blocking a domain I believe.

Well I would mow the lawn then!!!  :)  After that I would:

Reboot the machine of the Live Ubuntu CD... Ahmennn no password issue then. :)  Or you can install Ubuntu to a USB key and then boot off of that if you need to...

Then I would look at your home router/firewall.  Its also probably blocking your access to certain sites.  

But then again I would just do the damn lawn.  For cripes sake its not that hard man!  Oh, and if you go get a job you can just by and old machine with wifi and then the whole issue is irrelevant.

:KS

---

### Post by pi.boy.travis on 2008-07-18
> **thedevnull said:**
> Well I would mow the lawn then!!!  :)  After that I would:

Reboot the machine of the Live Ubuntu CD... Ahmennn no password issue then. :)  Or you can install Ubuntu to a USB key and then boot off of that if you need to...

Then I would look at your home router/firewall.  Its also probably blocking your access to certain sites.  

But then again I would just do the damn lawn.  For cripes sake its not that hard man!  Oh, and if you go get a job you can just by and old machine with wifi and then the whole issue is irrelevant.

:KS

Good info, routers can be configured to block sites as well. (cough) that can modified by typing the routers ip address into Fx, or your browser of choice.  thedevnull is right about the lawn too. :lolflag:

---

