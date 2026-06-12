---
title: "sudo install adblock for seamonkey doesn't work anymore"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by faif on 2008-07-15
Hello All. 
I recently rebuild my ubuntu machine 8.04.1. I apt-get installed seamonkey. and in terminal type: sudo seamonkey and installed adblock plus without problem. but when I start normal seamonkey, it seems the adblock plus had not been installed. I can only use adblock plus with seamonkey only when start seamonkey as root(sudo) strange! It worked before, I use above approach to solve this write permission problem. Anyone can give me some clue?

---

### Post by spiderbatdad on 2008-07-15
try also installing adblock by starting seamonkey normally. I know you get a meesage. Just ignore...install it, then restart seamonkey

---

### Post by mevets on 2008-07-15
If I am following your post correctly, then it is because you installed the extension thru the broswer w/ it had root privileges. Then you ran seamonkey w/o root priv and its not there. If this worked before I dont know how, but you should instead try to fix this write permission problem you are having. What happens when you run seamonkey w/o root priv and you navigate to the seamonkey addons page and try to install any random extension?

---

### Post by faif on 2008-07-15
> **mevets said:**
> If I am following your post correctly, then it is because you installed the extension thru the broswer w/ it had root privileges. Then you ran seamonkey w/o root priv and its not there. If this worked before I dont know how, but you should instead try to fix this write permission problem you are having. What happens when you run seamonkey w/o root priv and you navigate to the seamonkey addons page and try to install any random extension?

I tried flashgot, there is no problem no warning/error messages, It said flashgot had been successfully installed on my profile, and it does, when I restart seamonkey.

but when I try adblock plus, it gave me the message box as following warning:

**"This extension requires write access to the application directory to install properly. currently write access to some of the relevant subdirectories is forbidden, you probably have to log in as root before installing. after installation no elevated privileges will be necessary, read access is sufficient to use Adblock Plus."**

Because I saw this message, that is why I tired sudo seamonkey to install adblock plus. And switched to non-root normal user. It worked before. but now it can't, I must use "sudo seamonkey" to use adblock plus. 

I also tried ignore this alert message at non-root mode, but it still doesn't work. It seems I must use seamonkey at sudo mode?

---

### Post by faif on 2008-07-15
I solved it! It is the problem of adblock plus 0.7.5.5 and seamonkey 1.1.9 (current package in ubuntu repository).

Please the this thread for details:
[COLOR="DarkGreen"]*[http://adblockplus.org/forum/viewtopic.php?t=2550&start=0&postdays=0&postorder=asc&highlight=](http://adblockplus.org/forum/viewtopic.php?t=2550&start=0&postdays=0&postorder=asc&highlight=)*[/COLOR]

I installed adblock plus 0.7.5.4 and it works (by the approaches that use sudo seamonkey first and switch back to normal start). I will keep that for a while.

---

### Post by Quarterback3x on 2012-05-14
> **faif said:**
> 

I installed adblock plus 0.7.5.4 and it works (by the approaches that use sudo seamonkey first and switch back to normal start). I will keep that for a while.

Where would I find adblock plus 7.5.4? I am having problems finding that particular down load. It also seems that I am having difficulties finding Sudo Seamonkey as well. 

I take it you add Sudo Seamonkey, and then Adblock Plus .7.5.4? I am not very computer savvy. I am your average person who knows their way around well enough for college.

---

### Post by coffeecat on 2012-05-14
@Quarterback3x, this is an ancient thread about a now-obsolete version of Ubuntu and a very old, obsolete version of adblock. Please start a thread of your own describing what you are trying to achieve and someone will be able to help you. Do not forget to include the version of Ubuntu that you are using.

Thread closed.

---

