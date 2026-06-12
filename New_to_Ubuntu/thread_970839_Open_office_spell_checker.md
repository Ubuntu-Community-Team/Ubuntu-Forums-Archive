---
title: "Open office spell checker"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by SuperSix on 2008-11-04
Hi i am a pretty new user and i have just recently started using Open Office and i am trying to write a university report. The spell check doesn't seem to work. I have tried to install new dictionaries but it wont work. cant anyone help me please.

---

### Post by gandaran on 2008-11-04
> **SuperSix said:**
> Hi i am a pretty new user and i have just recently started using Open Office and i am trying to write a university report. The spell check doesn't seem to work. I have tried to install new dictionaries but it wont work. cant anyone help me please.
did you use synaptic to install? and was it *myspell* packages?

---

### Post by SuperSix on 2008-11-05
i went to wizzards and then went install new dictionary and tried to install english DicOOo

---

### Post by ad_267 on 2008-11-05
If you go to Tools - Options - Language Settings - Languages, you have to make sure the selected language has the tick/ABC icon next to it. This means you can use the spell checker. My default language was set to "English NZ" but I had to set it to "English UK" to get spell check to work.

---

### Post by gandaran on 2008-11-05
> **SuperSix said:**
> i went to wizzards and then went install new dictionary and tried to install english DicOOo
if you want to install any additional dictionary packages for open-office use synaptic package manager, just open it and scroll down to myspell, find the myspell-en-gb (english, if this is the one you want) mark for install and click the apply button, now you can find the english option in the open-office spell checker

---

### Post by SuperSix on 2008-11-05
i tried both of your suggestions and no luck. when i went to tools- options-language settings- language there were no languages even listed. then i went to synaptic and looked for the dictionaries and they were already installed. Funny thing is my spell checker works on the internet and in pidgin.

---

### Post by ad_267 on 2008-11-05
Here are the packages I have installed when I search for openoffice and spell:

language-pack-en-base
language-pack-gnome-en-base
language-support-en
libhunspell-1.2-0
myspell-en-au
myspell-en-gb
myspell-en-za
openoffice.org-l10n-common
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-thesaurus-en-au

I'm using OpenOffice 3 so it might be a bit different for you, but hopefully that helps.

---

### Post by gandaran on 2008-11-05
> i tried both of your suggestions and no luck. when i went to tools- options-language settings- language there were no languages even listed. then i went to synaptic and looked for the dictionaries and they were already installed. Funny thing is my spell checker works on the internet and in pidgin.
open-office and firefox use myspell dictionary's, pidgin and all ubuntu gnome apps use ispell (hardy 8.04) intrepid 8.10 uses wamericam or wbritish. 
just check the spell checker in open-office tools, not options-language settings, it must be there!

---

### Post by gandaran on 2008-11-05
if it really doesn't work install any other additional myspell dictionary, maybe this will force it work!

---

### Post by fballem on 2008-11-05
Two questions:

1/ What version of OpenOffice are you using?
2/ What language and variation are you trying to use?

For example, in my case, I use English (Canada), which is not installed by default and is not in the repositories.

When I was running OpenOffice 2.4, I followed the instructions that I received in this post on OpenOffice.org: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=9754&p=45931&hilit=canadian+english#p45931](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=9754&p=45931&hilit=canadian+english#p45931). Although the instructions are for Canadian English, there are a large number of dictionaries available in this tool.

Now that I'm running OpenOffice 3.0, the additional dictionaries are extensions. Do the following:

1/ Start Open Office Write.
- If you want the dictionary to be available to all users, then open a Terminal and execute ```
gksudo soffice
```. This will start Open Office as the root user and allow you to apply the extension to all users. Once started, select Text Document, which will open Write.
- If you want the dictionary only for yourself, then start OpenOffice Write as you normally do.
2/ Once Write is open, select Tools > Extension Manager. This will open a panel similar to the screenshot attached.
3/ Click the link to Get more Extensions here .. (it's shown on the screenshot).
4/ Follow the instructions, and then close Write. If you opened it as root, make sure that you exit from the terminal.
5/ When you restart Write, you should be good to go.

Hope this helps,

---

### Post by SuperSix on 2008-11-10
how do i get open office 3.0 i cant find it in synaptic

---

### Post by ad_267 on 2008-11-10
> **SuperSix said:**
> how do i get open office 3.0 i cant find it in synaptic

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by SuperSix on 2008-11-12
i did that and it didn't work i am on 8.04 Ubuntu not 8.10

---

### Post by ad_267 on 2008-11-13
Looks like there's a PPA for 8.04 now too, see [http://kshoster.net/node/56](http://kshoster.net/node/56) for instructions.

---

### Post by SuperSix on 2008-11-24
i dont know man none of this is working, spell check works when i open a file but now when i start one

---

