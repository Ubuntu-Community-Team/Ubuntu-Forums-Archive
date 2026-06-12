---
title: "Ugraded to 8.04 and lost/can't install Firefox add -ons"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by ljbirns on 2008-05-20
I recently upgraded to 8.04.  I run Firefox 2.0.0.4
All my extensions fail to work in 8.04. When I try to install ( re-install ) I get this error

>Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938


Lew

---

### Post by bumanie on 2008-05-20
There are many FF extensions that don't work with FF3,5b. I assume the writers/developers are waiting for the final release of FF3 in June, before they update things. There are some that work, but obviously not the ones you want.

---

### Post by quelx on 2008-05-20
You can downgrade to FF2 and get your extensions back

[http://ubuntuforums.org/showpost.php?p=5000335&postcount=8](http://ubuntuforums.org/showpost.php?p=5000335&postcount=8)

---

### Post by ljbirns on 2008-05-20
Thanks guys but please note I am using FF  2.0.0.4   NOT  3.0 B

---

### Post by Bubba64 on 2008-05-20
> **ljbirns said:**
> I recently upgraded to 8.04.  I run Firefox 2.0.0.4
All my extensions fail to work in 8.04. When I try to install ( re-install ) I get this error

>Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938


Lew

Nightly tester tools in Mozilla add ons will enable them in FF 3. It could be that if you have any part of FF3 in there that is what is keeping FF2 add ons working in Hardy. I wouldn't remove FF 3 but see if this add on will enable FF 2 add ons in Hardy. If the only reason your running FF 2 is because the addons were not working this download will force them to work in FF 3. I have had no problems personally using this add on.
[https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools](https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools)

---

### Post by drs305 on 2008-05-20
Was FF 3.05b installed when you upgraded to hardy? There were many users that upgraded, didn't like 3.05b, went back to FF2.0 and had problems, especially with bookmarks and extensions.

I'm not using FF so I don't have an answer. There were several comprehensive threads on it. You can search the ubuntu forums and I'm sure you will come up with a solution. Hint: in your search, if you include 'SOLVED' it will probably produce results which you can use.

Good luck.

---

### Post by stchman on 2008-05-20
> **ljbirns said:**
> I recently upgraded to 8.04.  I run Firefox 2.0.0.4
All my extensions fail to work in 8.04. When I try to install ( re-install ) I get this error

>Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938


Lew

That is a really old version of Firefox.  FF2 is up to 2.0.0.14.  Also Hardy comes with FF3 Beta 5 which rocks.

A lot of the add ons I use work but a few don't.

---

### Post by Bubba64 on 2008-05-20
> **drs305 said:**
> Was FF 3.05b installed when you upgraded to hardy? There were many users that upgraded, didn't like 3.05b, went back to FF2.0 and had problems, especially with bookmarks and extensions.

I'm not using FF so I don't have an answer. There were several comprehensive threads on it. You can search the ubuntu forums and I'm sure you will come up with a solution. Hint: in your search, if you include 'SOLVED' it will probably produce results which you can use.

Good luck.

I would say that if you look at a forum where people go to fix problems it looks as though there are (lots) of people with problems, this is not true though. Personally I had FF3 installed on Gutsy before even upgrading and have never had a problem. The add ons not working without knowing about nightly tester tools can also be a little disconcerting. This is not to say that people haven't had problems but I think it's a very small %.

---

### Post by GOROSSI on 2008-05-20
you could try this to get the extesions to work might cause the browser to be unstable though [pc world firefox 3 extensions fix]("http://www.pcworld.com/article/id,146062/article.html") I don't use it as on Kubuntu and installed v2 from the repos until v3 is final

---

### Post by ljbirns on 2008-05-20
Ok  Solved.  Since I had no extensions using FF 2.0  I figured why not upgrade to 3.0 b5. Then I followed BUBBA64 's advice and installed Nightly Tester Tools.  That worked just fine !:)  I now have my extensions working -
particularly Easy Gestures -- without which I am lost.
Thank you all and particularly to BUBBA 64

Lew

---

### Post by Bubba64 on 2008-05-20
> **ljbirns said:**
> Ok  Solved.  Since I had no extensions using FF 2.0  I figured why not upgrade to 3.0 b5. Then I followed BUBBA64 's advice and installed Nightly Tester Tools.  That worked just fine !:)  I now have my extensions working -
particularly Easy Gestures -- without which I am lost.
Thank you all and particularly to BUBBA 64

Lew

Cool, I picked up this tidbit of info on the forums. So it sounds like you were able to preinstall nightly tester tools then get add ons that were not workable, if that is the case that is valuable info. I have only used it post upgrade to enable what was already there but not working, let us know if my understanding is correct

---

### Post by ljbirns on 2008-05-20
I first un-installed FF 2.0 and then installed FF 3.0 via the Synaptic Package Manager. My extensions from 2.0 were still there of course, just not working. Then I installed the Nightly Tester  Tools Extension and  had it force the install of all my extensions.  Very cool.

Thanks again 

 Lew 
 PS  Is there a way to mark the thread solved :) ?

---

### Post by vratnica on 2008-05-22
can anybody see something interresting on this link with FF3?

[http://www.menshealth.com/bellyoff2008/?cm_mmc=BellyOffNL-_-2008_05_22-_-Editors_Column-_-The_Belly_Off_Summer_Edition](http://www.menshealth.com/bellyoff2008/?cm_mmc=BellyOffNL-_-2008_05_22-_-Editors_Column-_-The_Belly_Off_Summer_Edition)

I can see it with konqueror but with FF3 -no way

---

